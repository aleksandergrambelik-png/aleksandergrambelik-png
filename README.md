# Offensive + Defensive Security ⚡️

## My Brain — Notes on Hex, Symbols, and Web Attack Surface

But that was a normal thing back in the 2000s. Back in the day there was no real antivirus—everything was just a hoax that made storage over-buffer. Modern ones are the same: antivirus only detects user-agent, not hex patterns. And it's weird—why do antiviruses have external ads instead of internal ones? Or why not build a dedicated userland for ads instead of merging them into the backend? No matter how sophisticated it is, if everything is merged together and the web architecture has ads in the frontend, it'll never be safe. A link is a header, a URL key, and at the same time the door handle to open the house—that's the analogy. So logically, if there's no antivirus, then just build an anti-payload register at the same time.

My homemade tarpit has anti-symbol abuse: too many ++++++ values, how many times >>+-->+++—every + is an anomaly inside the algorithm, not a minus (-). A space ( ) is an empty column, okay, that's the setting. But a space is also hex 0x20, could be 0x00, 0xFF, could also be replaced with f0 0f where f = zero. For example like nested brackets ((((((((...)))))))) or array overflow ([]][][[]][][).

```
0x00 = 0000 0000
0xFF = 1111 1111
0xF0 = 1111 0000
0x0F = 0000 1111
```

· % (Percent): this is 0x25. In URL encoding, this is the start of %00 (Null Byte). If you shoot %00, the C/C++ parser will stop reading (treated as end of string).
· & (Ampersand): 0x26. Parameter separator in URLs. If you spam &&&, the parser can get confused and trigger a buffer overflow in the backend.
· ^ (Caret): 0x5E. In regex or shell scripts, this is the XOR operator or negation. Can bypass logic filters.

@ (At)               | Hex: 0x40 | Binary: 0100 0000
# (Hash)             | Hex: 0x23 | Binary: 0010 0011
$ (Dollar)           | Hex: 0x24 | Binary: 0010 0100
_ (Underscore)       | Hex: 0x5F | Binary: 0101 1111
& (Ampersand)        | Hex: 0x26 | Binary: 0010 0110
- (Minus)            | Hex: 0x2D | Binary: 0010 1101
+ (Plus)             | Hex: 0x2B | Binary: 0010 1011
( (Open Paren)       | Hex: 0x28 | Binary: 0010 1000
) (Close Paren)      | Hex: 0x29 | Binary: 0010 1001
/ (Slash)            | Hex: 0x2F | Binary: 0010 1111
* (Star)             | Hex: 0x2A | Binary: 0010 1010
" (Double Quote)     | Hex: 0x22 | Binary: 0010 0010
' (Single Quote)     | Hex: 0x27 | Binary: 0010 0111
: (Colon)            | Hex: 0x3A | Binary: 0011 1010
; (Semicolon)        | Hex: 0x3B | Binary: 0011 1011
! (Exclamation)      | Hex: 0x21 | Binary: 0010 0001
? (Question Mark)    | Hex: 0x3F | Binary: 0011 1111
~ (Tilde)            | Hex: 0x7E | Binary: 0111 1110
` (Backtick)         | Hex: 0x60 | Binary: 0110 0000
| (Pipe)             | Hex: 0x7C | Binary: 0111 1100
^ (Caret)            | Hex: 0x5E | Binary: 0101 1110
° (Degree)           | Hex: 0xB0 | Binary: 1011 0000
= (Equals)           | Hex: 0x3D | Binary: 0011 1101
{ (Open Curly)       | Hex: 0x7B | Binary: 0111 1011
} (Close Curly)      | Hex: 0x7D | Binary: 0111 1101
\ (Backslash)        | Hex: 0x5C | Binary: 0101 1100
% (Percent)          | Hex: 0x25 | Binary: 0010 0101
[ (Open Bracket)     | Hex: 0x5B | Binary: 0101 1011
] (Close Bracket)    | Hex: 0x5D | Binary: 0101 1101
< (Less Than)        | Hex: 0x3C | Binary: 0011 1100
> (Greater Than)     | Hex: 0x3E | Binary: 0011 1110

So that's 2 to 3 bytes (16–24 bit). This is what makes WAFs often get bypassed, because they only scan 8-bit ASCII.

## Non-ASCII Symbols Multi-Byte / Unicode

√ (Root)             | Hex: 0xE2 0x88 0x9A | Binary: 11100010 10001000 10011010
π (Pi)               | Hex: 0xCF 0x80      | Binary: 11001111 10000000
÷ (Divide)           | Hex: 0xC3 0xB7      | Binary: 11000011 10110111
× (Multiply)         | Hex: 0xC3 0x97      | Binary: 11000011 10010111
¶ (Pilcrow)          | Hex: 0xC2 0xB6      | Binary: 11000010 10110110
∆ (Delta)            | Hex: 0xE2 0x88 0x86 | Binary: 11100010 10001000 10000110
£ (Pound)            | Hex: 0xC2 0xA3      | Binary: 11000010 10100011
¢ (Cent)             | Hex: 0xC2 0xA2      | Binary: 11000010 10100010
€ (Euro)             | Hex: 0xE2 0x82 0xAC | Binary: 11100010 10000010 10101100
¥ (Yen)              | Hex: 0xC2 0xA5      | Binary: 11000010 10100101
© (Copyright)        | Hex: 0xC2 0xA9      | Binary: 11000010 10101001
® (Registered)       | Hex: 0xC2 0xAE      | Binary: 11000010 10101110
™ (Trademark)        | Hex: 0xE2 0x84 0xA2 | Binary: 11100010 10000100 10100010
✓ (Checkmark)        | Hex: 0xE2 0x9C 0x93 | Binary: 11100010 10011100 10010011

## Example: Invoice Payload Simulation

Example invoice—why can it be stacked? This is the simulation result, my own simulation, from searching hex patterns online, the scanner scans the amount.

Offset 0x00: 50 4F 53 54 20 2F 61 70 69 2F 76 31 2F 69 6E  P O S T   / a p i / v 1 / i n
Offset 0x10: 76 6F 69 63 65 20 48 54 54 50 2F 31 2E 31 0D  v o i c e   H T T P / 1 . 1 .
Offset 0x20: 0A 48 6F 73 74 3A 20 73 65 72 76 65 72 2E 63  . H o s t :   s e r v e r . c
Offset 0x30: 6F 6D 0D 0A 43 6F 6E 74 65 6E 74 2D 4C 65 6E  o m . . C o n t e n t - L e n
Offset 0x40: 67 74 68 3A 20 32 35 0D 0A 0D 0A 7B 22 61 6D  g t h :   2 5 . . . . { " a m
Offset 0x50: 6F 75 6E 74 22 3A 31 30 30 30 30 30 7D           o u n t " : 1 0 0 0 0 0 }

# That one, say, the key "amount". In hex, amount is:
61 6D 6F 75 6E 74

# If you break it down to binary (8-bit per character):
a = 0x61 = 0110 0001
m = 0x6D = 0110 1101
o = 0x6F = 0110 1111
u = 0x75 = 0111 0101
n = 0x6E = 0110 1110
t = 0x74 = 0111 0100

Look at the letter a (0110 0001). Lowercase a is 0x61. If you flip just one bit at the far right (from 1 to 0), it becomes 0110 0000 (0x60). In ASCII, 0x60 is the Backtick symbol ( ` ).

Look at the letter m (0110 1101). If you change 1 bit (say to 0100 1101 / 0x4D), it becomes the letter M (uppercase).

## Closing Questions

Every bit can be combined—so why is an attack different from an exploit? Why are basic-level attacks dangerous? Why is showing off an invoice or portfolio on social media a boomerang for yourself? Just treat this as yapping from someone who thinks he knows everything, like me.


## 👀🧟🐦✨🐒🐢

✨ An experiment that genuinely can't be explained—because once it can be explained, it's no longer an experiment, it's already a plan. An experiment is lived through, not presented. If I could explain it from start to finish, it means I already knew the outcome—and that's no longer an experiment, that's execution. Every tool and app and next software, including experiments—rather than letting experiments become cache and %temp%, better to push them to GitHub and GitLab 🧐

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
![Git](https://img.shields.io/badge/Git-F05050?style=for-the-badge&logo=git&logoColor=white)

Made on a phone. Made to work. ⚙️
