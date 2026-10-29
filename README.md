# Offensive + Defensive Security ⚡️

This is a 2000s Undernet-style lab, proudly stuffed with polyglots — making everything more efficient, with simple tools. Back then we built stuff on Windows XP. Now we're on phones with potato-power and Java in the pocket.

![Profile Views](https://komarev.com/ghpvc/?username=aleksandergrambelik-png&color=blue)

[![SanderShield](https://github.com/aleksandergrambelik-png/SanderShield/actions/workflows/audit.yml/badge.svg)](https://github.com/aleksandergrambelik-png/SanderShield/actions/workflows/audit.yml)

## Overview

I build compact, high-performance network utilities for reconnaissance, hardening, and defensive automation. My work focuses on practical security tooling that runs efficiently in constrained environments.

I often work from a phone, build in Java, and keep the tooling lean enough to be useful in real conditions. The goal is simple: fast signal, practical defense, and systems that remain useful under pressure.

Built for CLI-first engineering, battery-aware automation, and tooling that still performs well when the hardware is constrained.

## DragonFly BSD — Architectural Inspiration

I often draw architectural inspiration from DragonFly BSD when designing SanderShield and the rest of my defensive tooling. Below is a concise mapping of core DragonFly concepts to the corresponding design.

1. DragonFly BSD = Core Java
   - DragonFly acts as the "engine" that manages system resources. I mirror that role with a compact Core architecture and CLI in Java (ConfigManager, OutputManager). Minimal layers, maximum efficiency.

2. HAMMER2 = StealthDefense
   - HAMMER2 is known for resilience (snapshots, deduplication, crash tolerance). StealthDefense follows the same philosophy: resilient honeypot behavior with tarpit engagement, fake banners, and robust defensive logic.

3. HAMMER1 = SanderScan
   - HAMMER1 is the older, high-performance filesystem—fast and aggressive. SanderScan embraces that spirit with aggressive scanning mode, optimized for speed and direct results.

4. LWKT (Lightweight Kernel Threads) = Modular Task System
   - LWKT provides lightweight threading to run many tasks with low overhead. I apply that idea to a modular task system under com.sander.modules and a help/module system so features run independently and efficiently.

(Placed here so visitors can quickly understand the architectural philosophy behind the tooling.)

## What I do

- 🔭 I build powerful network utilities: scanners, recon suites, and lightweight defensive tools.
- 🌱 Learning: deepening my skills in network security and Java.
- 💬 Ask me about Termux, fast port scanning, or OSINT workflows.
- ⚡ Pro tip: I once scanned my own router — it ran a 2005 web server. I laughed, then patched it.

---

## Featured Project — SanderShield

### 🛡️ SanderShield — Defensive Hardening & Exposure Control

![version](https://img.shields.io/badge/version-1.0-blue)
![license](https://img.shields.io/badge/license-GPL--3.0-green)
![platform](https://img.shields.io/badge/platform-Termux%20%7C%20Linux%20%7C%20Windows-orange)

Minimal but effective defensive shield for hostile environments: request filtering, hardening checks, and low-overhead monitoring built for mobile-first security tooling.

- Fast traffic filtering and anomaly detection
- Lightweight defensive automation for exposed services
- Hardening guidance and service exposure scoring
- Built to complement recon and honeypot workflows
- Designed for constrained devices and production-style triage

<p align="center">
  <img src="https://github.com/aleksandergrambelik-png/SanderShield/blob/main/screenshots/Screenshot-CVE%20Check.jpg?raw=1" width="420" alt="CVE Check" />
  <img src="https://github.com/aleksandergrambelik-png/SanderShield/blob/main/screenshots/Screenshot-GPS-Sensor.jpg?raw=1" width="420" alt="GPS Sensor" />
</p>

<p align="center">
  <img src="https://github.com/aleksandergrambelik-png/SanderShield/blob/main/screenshots/Screenshot-Privacy.jpg?raw=1" width="420" alt="Privacy" />
  <img src="https://github.com/aleksandergrambelik-png/SanderShield/blob/main/screenshots/Screenshot-command-help.jpg?raw=1" width="420" alt="Command Help" />
</p>

<p align="center">
  <img src="https://github.com/aleksandergrambelik-png/SanderShield/blob/main/screenshots/Screenshot-ping.jpg?raw=1" width="420" alt="Ping" />
  <img src="https://github.com/aleksandergrambelik-png/SanderShield/blob/main/screenshots/owasp.jpg?raw=1" width="420" alt="OWASP" />
</p>

<p align="center">
  <img src="https://github.com/aleksandergrambelik-png/SanderShield/blob/main/screenshots/Screenshot-Test-Vuln-demo.owasp-juice.shop.jpg?raw=1" width="840" alt="Demo Vuln" />
</p>

[→ Explore SanderShield](https://github.com/aleksandergrambelik-png/SanderShield)

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

Made on a phone. Made to work. ⚙️
