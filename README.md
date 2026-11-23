# Offensive + Defensive Security ⚡️

## Decompiling, Low-Level Optimization, and Why I Love Java NIO

Decompiling a library is legal if the license permits it. Find the dead code, download the library, put it into raw code with an import to the syntax, check which part of the compiler method is set in each module of the library you want to use, then change its parameters according to your own logic.

Regular programmer:

import library; 
library.run(); 

(If it's slow, blame the library). Just build your own, it's a shame to blame the creator. 😄

Me: Decompile the .class or .jar, look at the AST (Abstract Syntax Tree), find hidden allocations, throw away unused bloatware, and rewrite its critical path. Don't piggyback on other people's libraries; I colonize their code to adapt it to the metal.

To make it efficient for a Ruby or PHP backend—or whatever—personally I like backend, but there's none I like more than Java compared to modern interpreters. 😄 It does 3x hidden memory allocations & unwritten O(n²) loops in the docs. And I love it. Java isn't just a language. The JVM has a JIT compiler, generational garbage collector, and transparent yet powerful memory management. I can see what happens in the heap & stack. I can manage thread pools, buffer pools, & socket channels explicitly.

Socket channel or NIO, I love it. Non-Blocking I/O to handle thousands of simultaneous connections with few threads, and buffer pool is the art of managing Direct Memory for I/O, avoiding unnecessary data copies between the Java Heap and OS Kernel.

THIS IS THE HOLY GRAIL.

Many Java developers don't know that ByteBuffer.allocateDirect() actually calls malloc() or mmap() at the OS level (C/C++).

· Heap Memory (Normal): Data from network → OS Kernel Buffer → JVM Heap → Application. (2x copy, hits Garbage Collector).
· Direct Memory (NIO): Data from network → OS Kernel Buffer → Direct Memory → Application. (Zero-copy, bypass GC).

Thread pool—I like memory cores. What can be used without bloatware? I determine how many cores are used, how many queues Windows runs in the background process. THAT IS THE ART OF CUSTOM OS AND OSS.

I love this part:

1. Autoboxing Map<Integer, Long> (Cache -128..127)

Code:

```java
map.put(1000, 5000L);
```

Raw Bytecode:

```text
invokestatic java/lang/Integer.valueOf(I)Ljava/lang/Integer;
```

C equivalent:

```c
typedef struct { int key; long value; } Pair;
Pair data[1000]; 
```

2. list.contains() inside a loop → O(n²)

Code:

```java
for (x : listA) { if (listB.contains(x)) ... }
```

Raw Bytecode:

```text
invokeinterface java/util/List.contains(Ljava/lang/Object;)Z
```

C equivalent:

```c
// Hash map look-up O(1)
long *val = find_in_hashmap(map, key);
if (val) { /* lock at you bastard */ }
```

3. ArrayList.remove(0) in a loop → System.arraycopy

Code:

```java
list.remove(0);
```

Raw Bytecode:

```text
invokevirtual java/util/ArrayList.remove(I)Ljava/lang/Object;
```

C equivalent:

```c
Node *temp = head;
head = head->next;
free(temp);
```

Because ASM: 
Raw x86: Just 2-3 lines of instruction:

```assembly
MOV RAX, [RBX] ; Take the head->next address
MOV [head], RAX ; Update head
CALL free      ; Delete old memory
```

Done. No arraycopy that eats up memory bandwidth. I like this. Thousands of lines are enough with logic and understanding, you don't need to overthink it.

4. Stream + Lambda Capturing

Code:

```java
list.stream().filter(x -> x > limit).collect(...)
```

Raw Bytecode:

```text
invokedynamic (or invokeinterface if the lambda is already compiled)
```

C equivalent:

```c
for (int i = 0; i < len; i++) {
    if (data[i] > limit) { result[count++] = data[i]; }
}
```

5. String.getBytes(), Defensive Copy, Iterator

String.getBytes():

· Raw Bytecode: invokevirtual java/lang/String.getBytes()[B

Defensive Copy (e.g., in constructor new ArrayList<>(existingList)):
This calls System.arraycopy or Arrays.copyOf, which at the native level copies a block of memory.

Iterator (for-each):

· Raw Bytecode: invokeinterface java/util/Iterator.hasNext()Z and invokeinterface java/util/Iterator.next()Ljava/lang/Object;

What I like about modifying Java's for-each is that it secretly calls iterator(). This creates a new Iterator object (allocation). That's why in game engines or low-latency applications, they prefer indexed for-loops (for (int i=0; i<size; i++)) so there's no iterator object allocation.

C equivalent:

```c
char *str = "Hello";
// No new allocation, just a pointer to read-only memory
```

Raw x86: LEA RAX, [RIP + str] (Load effective address of str). Zero copy.

Java Tax vs C/ASM Truth

Autoboxing (Map<Integer, Long>):

· Java Tax: Creates an Integer object in the Heap just to store the number 1000. Memory bloats, GC works hard.
· C/ASM Truth: typedef struct { int key; long value; } Pair;. Contiguous memory, cache-friendly, zero overhead. I understand that under the hood, Java is wasteful if not handled carefully.

O(n²) Trap (list.contains):

· Java Tax: Lazy programmers use List for lookups, making the server hang when data is large.
· C/ASM Truth: Hashmap lookup O(1) using pointer arithmetic. You understand that Big O notation has a real impact on CPU cycles.

ArrayList.remove(0) vs Pointer Manipulation:

· Java Tax: System.arraycopy (which is originally memmove in C). Shifts 1 million elements in memory just to delete index 0. Memory bandwidth is drained.
· ASM Truth: MOV RAX, [RBX]. 2 instructions. Update pointer, free old node. But as an elegant physical memory address manipulation.

Stream & Lambda (invokedynamic):

· Java Tax: Looks cool and functional, but behind the scenes it creates bootstrap methods, object allocations, and virtual method calls that cause CPU cache misses.
· C Truth: for (int i=0...). CPU branch prediction is happy, SIMD vectorization runs smoothly. I prefer raw loops because I care about L1/L2 Cache hit rates.

String & Iterator Allocation (The Silent Killers):

· Java Tax: for (String s : list) secretly calls iterator() → creates a new Iterator object in the Heap. In game engines or high-frequency trading, this causes GC pauses (lag spikes).
· ASM Truth: LEA RAX, [RIP + str]. Zero allocation. Just shift the pointer to read-only memory. Understand that "convenience" in Java is paid for dearly with garbage collection pauses.

## 👀🧟🐦✨🐒🐢

✨ An experiment that genuinely can't be explained—because once it can be explained, it's no longer an experiment, it's already a plan. An experiment is lived through, not presented. If I could explain it from start to finish, it means I already knew the outcome—and that's no longer an experiment, that's execution. Every tool and app and next software, including experiments—rather than letting experiments become cache and %temp%, better to push them to GitHub and GitLab 🧐

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)

![Profile Views](https://komarev.com/ghpvc/?username=aleksandergrambelik-png&color=blue)

[![Termux](https://img.shields.io/badge/Termux-Compatible-cyan?style=for-the-badge&logo=termux)](https://github.com/termux/termux-app)

[![Android](https://img.shields.io/badge/Platform-Android-green?style=for-the-badge&logo=android)](https://github.com/aleksandergrambelik-png/SanderShield//releases/tag/v38.0)

[![Java](https://img.shields.io/badge/Language-Java-red?style=for-the-badge&logo=openjdk)](https://adoptium.net/)

## My Brain — Notes on Hex, Symbols, and Web Attack Surface

But that was a normal thing back in the 2000s. Back in the day there was no real antivirus—everything was just a hoax that made storage over-buffer. Modern ones are the same: antivirus only detects user-agent, not hex patterns. And it's weird—why do antiviruses have external ads instead of internal ones? Or why not build a dedicated userland for ads instead of merging them into the backend? No matter how sophisticated it is, if everything is merged together and the web architecture has ads in the frontend, it'll never be safe. A link is a header, a URL key, and at the same time the door handle to open the house—that's the analogy. So logically, if there's no antivirus, then just build an anti-payload register at the same time.

My homemade tarpit has anti-symbol abuse: too many ++++++ values, how many times >>+-->+++—every + is an anomaly inside the algorithm, not a minus (-). A space ( ) is an empty column, okay, that's the setting. But a space is also hex 0x20, could be 0x00, 0xFF, could also be replaced with f0 0f where f = zero. For example like nested brackets ((((((((...)))))))) or array overflow ([]][][[]][][).

| Hex | Binary |
|:---:|:---:|
| `0x00` | `0000 0000` |
| `0xFF` | `1111 1111` |
| `0xF0` | `1111 0000` |
| `0x0F` | `0000 1111` |

- **% (Percent)**: this is `0x25`. In URL encoding, this is the start of `%00` (Null Byte). If you shoot `%00`, the C/C++ parser will stop reading (treated as end of string).
- **& (Ampersand)**: `0x26`. Parameter separator in URLs. If you spam `&&&`, the parser can get confused and trigger a buffer overflow in the backend.
- **^ (Caret)**: `0x5E`. In regex or shell scripts, this is the XOR operator or negation. Can bypass logic filters.

| Symbol | Name | Hex | Binary |
|:---:|:---|:---:|:---:|
| `@` | At | `0x40` | `0100 0000` |
| `#` | Hash | `0x23` | `0010 0011` |
| `$` | Dollar | `0x24` | `0010 0100` |
| `_` | Underscore | `0x5F` | `0101 1111` |
| `&` | Ampersand | `0x26` | `0010 0110` |
| `-` | Minus | `0x2D` | `0010 1101` |
| `+` | Plus | `0x2B` | `0010 1011` |
| `(` | Open Paren | `0x28` | `0010 1000` |
| `)` | Close Paren | `0x29` | `0010 1001` |
| `/` | Slash | `0x2F` | `0010 1111` |
| `*` | Star | `0x2A` | `0010 1010` |
| `"` | Double Quote | `0x22` | `0010 0010` |
| `'` | Single Quote | `0x27` | `0010 0111` |
| `:` | Colon | `0x3A` | `0011 1010` |
| `;` | Semicolon | `0x3B` | `0011 1011` |
| `!` | Exclamation | `0x21` | `0010 0001` |
| `?` | Question Mark | `0x3F` | `0011 1111` |
| `~` | Tilde | `0x7E` | `0111 1110` |
| `` ` `` | Backtick | `0x60` | `0110 0000` |
| `\|` | Pipe | `0x7C` | `0111 1100` |
| `^` | Caret | `0x5E` | `0101 1110` |
| `°` | Degree | `0xB0` | `1011 0000` |
| `=` | Equals | `0x3D` | `0011 1101` |
| `{` | Open Curly | `0x7B` | `0111 1011` |
| `}` | Close Curly | `0x7D` | `0111 1101` |
| `\` | Backslash | `0x5C` | `0101 1100` |
| `%` | Percent | `0x25` | `0010 0101` |
| `[` | Open Bracket | `0x5B` | `0101 1011` |
| `]` | Close Bracket | `0x5D` | `0101 1101` |
| `<` | Less Than | `0x3C` | `0011 1100` |
| `>` | Greater Than | `0x3E` | `0011 1110` |

So that's 2 to 3 bytes (16–24 bit). This is what makes WAFs often get bypassed, because they only scan 8-bit ASCII.

## Non-ASCII Symbols Multi-Byte / Unicode

| Symbol | Name | Hex | Binary |
|:---:|:---|:---:|:---:|
| `√` | Root | `0xE2 0x88 0x9A` | `11100010 10001000 10011010` |
| `π` | Pi | `0xCF 0x80` | `11001111 10000000` |
| `÷` | Divide | `0xC3 0xB7` | `11000011 10110111` |
| `×` | Multiply | `0xC3 0x97` | `11000011 10010111` |
| `¶` | Pilcrow | `0xC2 0xB6` | `11000010 10110110` |
| `∆` | Delta | `0xE2 0x88 0x86` | `11100010 10001000 10000110` |
| `£` | Pound | `0xC2 0xA3` | `11000010 10100011` |
| `¢` | Cent | `0xC2 0xA2` | `11000010 10100010` |
| `€` | Euro | `0xE2 0x82 0xAC` | `11100010 10000010 10101100` |
| `¥` | Yen | `0xC2 0xA5` | `11000010 10100101` |
| `©` | Copyright | `0xC2 0xA9` | `11000010 10101001` |
| `®` | Registered | `0xC2 0xAE` | `11000010 10101110` |
| `™` | Trademark | `0xE2 0x84 0xA2` | `11100010 10000100 10100010` |
| `✓` | Checkmark | `0xE2 0x9C 0x93` | `11100010 10011100 10010011` |

## Example: Invoice Payload Simulation

Example invoice—why can it be stacked? This is the simulation result, my own simulation, from searching hex patterns online, the scanner scans the amount.

| Offset | Hex | ASCII |
|:---:|:---|:---|
| `0x00` | `50 4F 53 54 20 2F 61 70 69 2F 76 31 2F 69 6E` | `P O S T   / a p i / v 1 / i n` |
| `0x10` | `76 6F 69 63 65 20 48 54 54 50 2F 31 2E 31 0D` | `v o i c e   H T T P / 1 . 1 .` |
| `0x20` | `0A 48 6F 73 74 3A 20 73 65 72 76 65 72 2E 63` | `. H o s t :   s e r v e r . c` |
| `0x30` | `6F 6D 0D 0A 43 6F 6E 74 65 6E 74 2D 4C 65 6E` | `o m . . C o n t e n t - L e n` |
| `0x40` | `67 74 68 3A 20 32 35 0D 0A 0D 0A 7B 22 61 6D` | `g t h :   2 5 . . . . { " a m` |
| `0x50` | `6F 75 6E 74 22 3A 31 30 30 30 30 30 7D` | `o u n t " : 1 0 0 0 0 0 }` |

### The key `amount` in hex:

```text
61 6D 6F 75 6E 74
```

### Binary breakdown (8-bit per character)

| Character | Hex | Binary |
|:---:|:---:|:---:|
| `a` | `0x61` | `0110 0001` |
| `m` | `0x6D` | `0110 1101` |
| `o` | `0x6F` | `0110 1111` |
| `u` | `0x75` | `0111 0101` |
| `n` | `0x6E` | `0110 1110` |
| `t` | `0x74` | `0111 0100` |

Look at the letter a (`0110 0001`). Lowercase a is `0x61`. If you flip just one bit at the far right (from 1 to 0), it becomes `0110 0000` (`0x60`). In ASCII, `0x60` is the Backtick symbol ( ` ).

Look at the letter m (`0110 1101`). If you change 1 bit (say to `0100 1101` / `0x4D`), it becomes the letter M (uppercase).

## Closing Questions

Every bit can be combined—so why is an attack different from an exploit? Why are basic-level attacks dangerous? Why is showing off an invoice or portfolio on social media a boomerang for yourself? Just treat this as yapping from someone who thinks he knows everything, like me.



uites, and lightweight defensive tools.
- 🌱 Learning: deepening my skills in network security and Java.
- 💬 Ask me about Termux, fast port scanning, or OSINT workflows.
- ⚡ Pro tip: I once scanned my own router — it ran a 2005 web server. I laughed, then patched it.

---

## Support Development

If you want to support the project and keep the tools growing, you can buy me a coffee:

[![Ko-fi](https://img.shields.io/badge/Ko--fi-Support-orange?style=for-the-badge&logo=ko-fi)](https://ko-fi.com/sander_0x04)
[![Saweria](https://img.shields.io/badge/Saweria-Beli%20kopi-orange?style=for-the-badge&logo=coffee)](https://saweria.co/aleksandergrambelik)

## GitHub Stats

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=aleksandergrambelik-png&show_icons=true&theme=dark)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=aleksandergrambelik-png&layout=compact&theme=dark)

---

## Tech & Tools

![Termux](https://img.shields.io/badge/Termux-000000?style=for-the-badge&logo=termux&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05050?style=for-the-badge&logo=git&logoColor=white)

Made on a phone. Made to work. ⚙️
