# Offensive + Defensive Security ⚡️

## My Brain — Notes on Hex, Symbols, and Web Attack Surface

But that was a normal thing back in the 2000s. Back in the day there was no real antivirus—everything was just a hoax that made storage over-buffer. Modern ones are the same: antivirus only detects user-agent, not hex patterns. And it's weird—why do antiviruses have external ads instead of internal ones? Or why not build a dedicated userland for ads instead of merging them into the backend? No matter how sophisticated it is, if everything is merged together and the web architecture has ads in the frontend, it'll never be safe. A link is a header, a URL key, and at the same time the door handle to open the house—that's the analogy. So logically, if there's no antivirus, then just build an anti-payload register at the same time.

My homemade tarpit has anti-symbol abuse: too many `+++++` values, how many times `>>+-->+++`—every `+` is an anomaly inside the algorithm, not a minus (`-`). A space (` `) is an empty column, okay, that's the setting. But a space is also hex `0x20`, could be `0x00`, `0xFF`, could also be replaced with `f0 0f` where `f` = zero. For example like nested brackets `((((((...))))))` or array overflow `([][][][][])`.
0x00 = 0000 0000
0xFF = 1111 1111
0xF0 = 1111 0000
0x0F = 0000 1111

- `%` (Percent): this is `0x25`. In URL encoding, this is the start of `%00` (Null Byte). If you shoot `%00`, the C/C++ parser will stop reading (treated as end of string).
- `&` (Ampersand): `0x26`. Parameter separator in URLs. If you spam `&&&`, the parser can get confused and trigger a buffer overflow in the backend.
- `^` (Caret): `0x5E`. In regex or shell scripts, this is the XOR operator or negation. Can bypass logic filters.

## ASCII Symbols

| Symbol | Name | Hex | Binary |
| :--- | :--- | :--- | :--- |
| `@` | At | `0x40` | `0100 0000` |
| `#` | Hash | `0x23` | `0010 0011` |
| `$` | Dollar | `0x24` | `0010 0100` |
| `_` | Underscore | `0x5F` | `0101 1111` |
| `&` | Ampersand | `0x26` | `0010 0110` |
| `-` | Minus | `0x2D` | `0010 1101` |
| `+` | Plus | `0x2B` | `0010 1011` |
| `(` | Open Parenthesis | `0x28` | `0010 1000` |
| `)` | Close Parenthesis | `0x29` | `0010 1001` |
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
| `{` | Open Curly Brace | `0x7B` | `0111 1011` |
| `}` | Close Curly Brace | `0x7D` | `0111 1101` |
| `\` | Backslash | `0x5C` | `0101 1100` |
| `%` | Percent | `0x25` | `0010 0101` |
| `[` | Open Square Bracket | `0x5B` | `0101 1011` |
| `]` | Close Square Bracket | `0x5D` | `0101 1101` |
| `<` | Less Than | `0x3C` | `0011 1100` |
| `>` | Greater Than | `0x3E` | `0011 1110` |

So that's 2 to 3 bytes (16–24 bit). This is what makes WAFs often get bypassed, because they only scan 8-bit ASCII.

## Non-ASCII Symbols (Multi-Byte / Unicode)

| Symbol | Name | Hex | Binary |
| :--- | :--- | :--- | :--- |
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

```text
Offset 0x00: 50 4F 53 54 20 2F 61 70 69 2F 76 31 2F 69 6E  P O S T   / a p i / v 1 / i n
Offset 0x10: 76 6F 69 63 65 20 48 54 54 50 2F 31 2E 31 0D  v o i c e   H T T P / 1 . 1 .
Offset 0x20: 0A 48 6F 73 74 3A 20 73 65 72 76 65 72 2E 63  . H o s t :   s e r v e r . c
Offset 0x30: 6F 6D 0D 0A 43 6F 6E 74 65 6E 74 2D 4C 65 6E  o m . . C o n t e n t - L e n
Offset 0x40: 67 74 68 3A 20 32 35 0D 0A 0D 0A 7B 22 61 6D  g t h :   2 5 . . . . { " a m
Offset 0x50: 6F 75 6E 74 22 3A 31 30 30 30 30 30 7D           o u n t " : 1 0 0 0 0 0 }

That one, say, the key "amount". In hex, amount is:
61 6D 6F 75 6E 74

If you break it down to binary (8-bit per character):
Char Hex Binary
a 0x61 0110 0001
m 0x6D 0110 1101
o 0x6F 0110 1111
u 0x75 0111 0101
n 0x6E 0110 1110
t 0x74 0111 0100

Look at the letter a (0110 0001). Lowercase a is 0x61. If you flip just one bit at the far right (from 1 to 0), it becomes 0110 0000 (0x60). In ASCII, 0x60 is the Backtick symbol ( ` ).

Look at the letter m (0110 1101). If you change 1 bit (say to 0100 1101 / 0x4D), it becomes the letter M (uppercase).

Closing Questions

Every bit can be combined—so why is an attack different from an exploit? Why are basic-level attacks dangerous? Why is showing off an invoice or portfolio on social media a boomerang for yourself? Just treat this as yapping from someone who thinks he knows everything, like me.


If you don't understand what I wrote, then this isn't for you. 🗿🔪

## 👀🧟🐦✨🐒🐢

✨ An experiment that genuinely can't be explained—because once it can be explained, it's no longer an experiment, it's already a plan. An experiment is lived through, not presented. If I could explain it from start to finish, it means I already knew the outcome—and that's no longer an experiment, that's execution. Every tool and app and next software, including experiments—rather than letting experiments become cache and %temp%, better to push them to GitHub and GitLab ✨🐦

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)

![Profile Views](https://komarev.com/ghpvc/?username=aleksandergrambelik-png&color=blue)

[![Termux](https://img.shields.io/badge/Termux-Compatible-cyan?style=for-the-badge&logo=termux)](https://github.com/termux/termux-app)

[![Android](https://img.shields.io/badge/Platform-Android-green?style=for-the-badge&logo=android)](https://github.com/aleksandergrambelik-png/SanderShield//releases/tag/v38.0)

[![Java](https://img.shields.io/badge/Language-Java-red?style=for-the-badge&logo=openjdk)](https://adoptium.net/)


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
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

Made on a phone. Made to work. ⚙️
