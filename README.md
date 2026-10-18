# ALEKSANDER — Offensive + Defensive Security ⚡️

![Profile Views](https://komarev.com/ghpvc/?username=aleksandergrambelik-png&color=blue)

## Java Manifesto & Challenge

People say Java is heavy, bloated, and full of garbage libraries. They say modern security tools must be written in Rust or Go.

I'm here to say otherwise. I built my entire suite—network scanner, firewall manager, bot detection—under 50KB, running on a potato phone in Termux. Pure Java. No bloatware.

Back in the 2000s, Java was the absolute king. Now everyone wants to throw it away. I'm here to remind you what Java can still do in the modern era when you actually know how to use it.

I used Qwen 3.7/3.8 and DeepSeek v4.1 Pro as my AI-assisted syntax partners — I wrote the logic, they helped polish and speed up iteration while I debugged 500+ lines on a 5-inch screen.

So, here is my challenge to you:
If you think your 'modern language' (or your generic AI prompt) can do better, rewrite my code in your language, keep the features, and make it under 50KB.

I'll wait. 🃏

I build sharp, fast network tools — often from my phone. I don't apologize for noisy scans.


## 📸 Proof of Concept (Live Test)

Here is a real output from `stealth_log.csv` and `stealth_log.json` captured during a live test on a local network (Telkomsel Hotspot). The tool successfully detected a bot, engaged the tarpit, and blocked multiple ports.

### CSV Output (`stealth_log.csv`)

```csv
timestamp,event,ip,port,details
2026-10-18 21:17:39,CONN,10.52.***.***,8080,"New connection"
2026-10-18 21:17:39,BOT,10.52.***.***,8080,"Bot signature detected"
2026-10-18 21:17:39,TARPIT,10.52.***.***,8080,"Tarpit engaged"
2026-10-18 21:22:27,CONN,10.52.***.***,3306,"New connection"
2026-10-18 21:22:27,TARPIT,10.52.***.***,3306,"Tarpit engaged"
```

### JSON Output (stealth_log.json)

```json
[
  {"timestamp":"2026-10-18 21:17:39","event":"BOT","ip":"10.52.***.***","port":8080,"details":"Bot signature detected"},
  {"timestamp":"2026-10-18 21:17:39","event":"TARPIT","ip":"10.52.***.***","port":8080,"details":"Tarpit engaged"}
]
```

Note: IP addresses are partially redacted for privacy and ethical disclosure.

## What I do

- 🔭 I build powerful network utilities: scanners, recon suites, and lightweight defensive tools.
- 🌱 Learning: deepening my skills in network security and Java.
- 💬 Ask me about Termux, fast port scanning, or OSINT workflows.
- ⚡ Pro tip: I once scanned my own router — it ran a 2005 web server. I laughed, then patched it.

---

## Featured Projects — Ready to Run

### SanderSuite-Linux — All-in-one Security Suite
![version](https://img.shields.io/badge/version-1.0-blue)
![license](https://img.shields.io/badge/license-GPL--3.0-green)
![platform](https://img.shields.io/badge/platform-Linux-orange)

An aggressive but responsible toolbox for offensive and defensive ops on Linux.
- Recon & high-speed scanning
- Compact offensive utilities (scripts & binaries)
- Defensive hardening steps and automation
- Easy install & CLI-first workflows

[→ Explore SanderSuite-Linux](https://github.com/aleksandergrambelik-png/SanderSuite-Linux)

---

### SanderScan — LAN & Port Scanner (Phone-friendly)
![Version](https://img.shields.io/badge/version-1.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-Termux%20%7C%20PC-orange)

Fast, threaded scanner built for Termux and PC. Made on a phone, optimized for speed.
- Auto network discovery
- 250-thread scanning mode
- Banner grabbing & MAC vendor lookup
- OS detection
- Export results to CSV/JSON

[→ Explore SanderScan](https://github.com/aleksandergrambelik-png/SanderScan)

---

### StealthDefense — Minimalist Honeypot & Tarpit
![version](https://img.shields.io/badge/version-2.6-blue)
![license](https://img.shields.io/badge/license-GPL--3.0-green)
![platform](https://img.shields.io/badge/platform-Termux%20%7C%20PC-orange)

Honeypot + Anti-bot + Tarpit defense with built-in filters (Clickjacking, SQLi/XSS/LFI). Zero dependencies.

[→ Explore StealthDefense](https://github.com/aleksandergrambelik-png/StealthDefense)

---

## Philosophy

I prefer tools that work in the wild: compact, fast, and useful. If it warms my phone, it still gets the job done.

## GitHub Stats

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=aleksandergrambelik-png&show_icons=true&theme=dark)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=aleksandergrambelik-png&layout=compact&theme=dark)

---

## Tech & Tools

![Termux](https://img.shields.io/badge/Termux-000000?style=for-the-badge&logo=termux&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

## Get in touch

- GitHub: https://github.com/aleksandergrambelik-png
- Want a demo or collab? Open an issue in any repo or DM me on GitHub.

---

Made on a phone. Made to work. ⚙️
