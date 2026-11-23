# Offensive + Defensive Security ⚡️

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=aleksandergrambelik-png&color=blue" alt="Profile views" />
</p>

## 👋 About Me

I am an Android-first security enthusiast focused on:

- 🛡️ Defensive security and practical threat analysis
- 🔍 Network scanning and OSINT workflows
- 🧩 Hex, binary, encoding, and web protocol fundamentals
- ☕ Java and lightweight tools for Termux/Linux environments

I build and test only on systems I own or have explicit authorization to assess.

## 🔬 Technical Notes

### Hexadecimal and Binary

Hexadecimal represents bytes using values from `0x00` to `0xFF`:

```text
0x00 = 00000000
0x0F = 00001111
0xF0 = 11110000
0xFF = 11111111
```

A byte is eight bits. Understanding binary representation helps when debugging network protocols, encoded payloads, file formats, and low-level application behavior.

### Common ASCII Characters

| Character | Name | Hex | Binary |
|:---:|:---|:---:|:---:|
| `@` | At | `0x40` | `01000000` |
| `#` | Hash | `0x23` | `00100011` |
| `$` | Dollar | `0x24` | `00100100` |
| `_` | Underscore | `0x5F` | `01011111` |
| `&` | Ampersand | `0x26` | `00100110` |
| `-` | Minus | `0x2D` | `00101101` |
| `+` | Plus | `0x2B` | `00101011` |
| `/` | Slash | `0x2F` | `00101111` |
| `*` | Star | `0x2A` | `00101010` |
| `:` | Colon | `0x3A` | `00111010` |
| `;` | Semicolon | `0x3B` | `00111011` |
| `?` | Question mark | `0x3F` | `00111111` |
| `~` | Tilde | `0x7E` | `01111110` |
| `` ` `` | Backtick | `0x60` | `01100000` |
| `|` | Pipe | `0x7C` | `01111100` |
| `^` | Caret | `0x5E` | `01011110` |
| `%` | Percent | `0x25` | `00100101` |
| `[` | Open bracket | `0x5B` | `01011011` |
| `]` | Close bracket | `0x5D` | `01011101` |
| `<` | Less than | `0x3C` | `00111100` |
| `>` | Greater than | `0x3E` | `00111110` |

### Unicode Encoding

Unicode symbols are often encoded as multiple UTF-8 bytes:

| Character | UTF-8 hexadecimal |
|:---:|:---:|
| `√` | `E2 88 9A` |
| `π` | `CF 80` |
| `÷` | `C3 B7` |
| `×` | `C3 97` |
| `€` | `E2 82 AC` |
| `✓` | `E2 9C 93` |

Correct parsing and normalization are important because differently encoded input can expose validation bugs. They should be tested defensively and fixed at the application boundary, not used against systems without authorization.

### Example: Reading an HTTP/JSON Payload

```text
POST /api/v1/invoice HTTP/1.1
Host: example.com
Content-Type: application/json

{"amount":100000}
```

The JSON key `amount` is encoded in ASCII as:

```text
61 6D 6F 75 6E 74
```

| Character | ASCII hex | 8-bit binary |
|:---:|:---:|:---:|
| `a` | `0x61` | `01100001` |
| `m` | `0x6D` | `01101101` |
| `o` | `0x6F` | `01101111` |
| `u` | `0x75` | `01110101` |
| `n` | `0x6E` | `01101110` |
| `t` | `0x74` | `01110100` |

A single bit can change one character's representation. This is a useful reminder to validate data at every system boundary and to avoid relying on one simple string check as a complete security control.

## 🧰 Tech & Tools

<p>
  <a href="https://github.com/termux/termux-app"><img src="https://img.shields.io/badge/Termux-000000?style=for-the-badge&logo=termux&logoColor=white" alt="Termux" /></a>
  <a href="https://www.adoptium.net/"><img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java" /></a>
  <img src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black" alt="Linux" />
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git" />
  <img src="https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Android" />
</p>

- 🌱 Currently learning network security and Java
- 💬 Ask me about Termux, defensive scanning, or OSINT workflows
- 📱 Built primarily from a phone
- ⚡ Pro tip: test and secure your own network—never someone else's

## 🚀 Projects

- [SanderShield](https://github.com/aleksandergrambelik-png/SanderShield) — security-oriented Android project

## 📊 GitHub Stats

<p>
  <img src="https://github-readme-stats.vercel.app/api?username=aleksandergrambelik-png&show_icons=true&theme=dark" alt="GitHub stats" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=aleksandergrambelik-png&layout=compact&theme=dark" alt="Top languages" />
</p>

## ☕ Support Development

If you would like to support the project:

[![Ko-fi](https://img.shields.io/badge/Ko--fi-Support-orange?style=for-the-badge&logo=ko-fi)](https://ko-fi.com/sander_0x04)
[![Saweria](https://img.shields.io/badge/Saweria-Support-orange?style=for-the-badge&logo=coffee)](https://saweria.co/aleksandergrambelik)

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)

---

<p align="center">Made on a phone. Made to work. ⚙️</p>
