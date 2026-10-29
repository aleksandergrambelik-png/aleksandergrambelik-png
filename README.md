# Offensive + Defensive Security ⚡️

This is a 2000s Undernet-style lab, proudly stuffed with polyglots — making everything 'more efficient.' With simple tools. Back then we built stuff on Windows XP. Now we're on phones with potato specs, and we still make it work.

![Profile Views](https://komarev.com/ghpvc/?username=aleksandergrambelik-png&color=blue)

[![SanderMultiVector](https://github.com/aleksandergrambelik-png/SanderMultiVector/actions/workflows/audit.yml/badge.svg)](https://github.com/aleksandergrambelik-png/SanderMultiVector/actions/workflows/audit.yml)
[![SanderSuite](https://github.com/aleksandergrambelik-png/SanderSuite/actions/workflows/audit.yml/badge.svg)](https://github.com/aleksandergrambelik-png/SanderSuite/actions/workflows/audit.yml)
[![SanderScan](https://github.com/aleksandergrambelik-png/SanderScan/actions/workflows/audit.yml/badge.svg)](https://github.com/aleksandergrambelik-png/SanderScan/actions/workflows/audit.yml)
[![StealthDefense](https://github.com/aleksandergrambelik-png/StealthDefense/actions/workflows/audit.yml/badge.svg)](https://github.com/aleksandergrambelik-png/StealthDefense/actions/workflows/audit.yml)
[![SanderShield](https://github.com/aleksandergrambelik-png/SanderShield/actions/workflows/audit.yml/badge.svg)](https://github.com/aleksandergrambelik-png/SanderShield/actions/workflows/audit.yml)

## Overview

I build compact, high-performance network utilities for reconnaissance, hardening, and defensive automation. My work focuses on practical security tooling that runs efficiently in constrained environments.

I often work from a phone, build in Java, and keep the tooling lean enough to be useful in real conditions. The goal is simple: fast signal, practical defense, and systems that remain useful under pressure.

Built for CLI-first engineering, battery-aware automation, and tooling that still performs well when the hardware is constrained.

## DragonFly BSD — Architectural Inspiration (reference for my tools)

I often draw architectural inspiration from DragonFly BSD when designing SanderSuite, SanderScan, and StealthDefense. Below is a concise mapping of core DragonFly concepts to the corresponding design.

1. DragonFly BSD = Core Java (SanderSuite)
   - DragonFly acts as the "engine" that manages system resources. I mirror that role with a compact Core architecture and CLI in Java (ConfigManager, OutputManager). Minimal layers, maximum efficiency.

2. HAMMER2 = StealthDefense
   - HAMMER2 is known for resilience (snapshots, deduplication, crash tolerance). StealthDefense follows the same philosophy: resilient honeypot behavior with tarpit engagement, fake banners, and robust detection.

3. HAMMER1 = SanderScan
   - HAMMER1 is the older, high-performance filesystem—fast and aggressive. SanderScan embraces that spirit with aggressive scanning mode, optimized for speed and direct results.

4. LWKT (Lightweight Kernel Threads) = Modular Task System
   - LWKT provides lightweight threading to run many tasks with low overhead. I apply that idea to a modular task system under com.sander.modules and a help/module system so features run as independently as possible.

(Placed here so visitors can quickly understand the architectural philosophy that influenced SanderSuite, SanderScan, and StealthDefense.)

## What I do

- 🔭 I build powerful network utilities: scanners, recon suites, and lightweight defensive tools.
- 🌱 Learning: deepening my skills in network security and Java.
- 💬 Ask me about Termux, fast port scanning, or OSINT workflows.
- ⚡ Pro tip: I once scanned my own router — it ran a 2005 web server. I laughed, then patched it.

---

## Featured Projects — Ready to Run

### 🛡️ SanderMultiVector

> Hybrid Multi-Vector Bug Bounty Arsenal (Java + Perl + C++) for Termux/Linux.

![Java](https://img.shields.io/badge/Java-11+-orange)
![Perl](https://img.shields.io/badge/Perl-5.0+-blue)
![C++](https://img.shields.io/badge/C++-11+-purple)
![License](https://img.shields.io/badge/License-GPL--3.0-green)
![Platform](https://img.shields.io/badge/Platform-Termux%20%7C%20Linux%20%7C%20Windows%20%7C%20macOS-brightgreen)

**Features:**
- **6 Attack Modes:** SQLi, XSS, RCE, LFI, API Injection, Typo Mapping.
- **Hybrid Engine:** Java (Orchestrator) + Perl (Obfuscator) + C++ (Fast HTTP).
- **Double Output:** Real-time Terminal + JSONL Audit Log.
- **Interactive & CLI Mode:** Colored Menu + Command Line Support.
- **Cross-Platform:** Termux, Linux, Windows, macOS.
- **AI-Powered:** Built with Qwen 3.7 Plus & DeepSeek V4.1 Pro.

[→ View Repository](https://github.com/aleksandergrambelik-png/SanderMultiVector)

### SanderSuite — Beacon-Oriented Security Suite
![version](https://img.shields.io/badge/version-1.0-blue)
![license](https://img.shields.io/badge/license-GPL--3.0-green)
![platform](https://img.shields.io/badge/platform-Linux-orange)

A compact but ruthless security toolkit for beacon-driven intelligence, exposure mapping, and defensive action on Linux.

- Fast beaconing and service discovery
- Pseudo-AI risk triage for prioritizing exposed targets
- Exposure mapping under active threat pressure
- Banner and service fingerprinting
- Defensive hardening, lockdown guidance, and reporting
- Built for rapid decision-making in noisy, high-risk environments

SanderSuite is not just a recon tool. It behaves like a beacon engine: it emits signals, captures service intelligence, identifies exposed assets, and ranks the most dangerous targets before action is taken.

#### Core Features

##### 1. WAF Engine
Built-in payload filtering layer that blocks malicious requests before they reach the core logic.

- SQL Injection (SQLi)
  - UNION-based payloads
  - classic boolean bypasses
  - time-based injection patterns
- XSS
  - script tags
  - javascript: payloads
  - event handlers such as onerror=
- LFI
  - traversal attempts such as ../../etc/passwd
  - Windows path traversal patterns
- CMD Injection
  - command chaining via ;, |, &&, $()
- Sensitive Path Blocking
  - /.env
  - /.git/
  - /wp-config.php
  - /actuator
- Java Injection
  - Runtime.getRuntime()
  - ProcessBuilder
  - System.exit
- Nuclei Scanner Detection
  - common nuclei user-agent and request patterns

##### 2. Anti-Esoteric Language Filter
Catches payloads generated from unusual or obfuscated languages often seen in CTF and hostile scanning contexts.

- Brainfuck payload signatures
- JSFuck payload signatures
- obfuscated language markers such as fuck, kcuf, feck, and related variations

##### 3. Anti-Scan & Anti-Bot
Detection layer for noisy scanners and bot activity that behaves aggressively without normal application traffic.

- Anti-port scan tracking
  - repeated connection attempts across multiple ports from a single source
- Silent scan detection
  - scanners that probe without sending meaningful payloads
- Bot and abnormal behavior detection

##### 4. AI Threat Scoring
A lightweight scoring engine that turns activity into action.

- Monitor
  - score 1–29
  - logged and gently challenged
- Tarpit
  - score 30–69
  - delayed and throttled responses
- Block
  - score 70+
  - permanent blacklist trigger

[→ Explore SanderSuite](https://github.com/aleksandergrambelik-png/SanderSuite)

---



### SanderShield — Defensive Security Layer
![version](https://img.shields.io/badge/version-1.0-blue)
![license](https://img.shields.io/badge/license-GPL--3.0-green)
![platform](https://img.shields.io/badge/platform-Termux%20%7C%20Linux%20%7C%20PC-orange)

Minimal but effective defensive shield for hostile environments: request filtering, hardening checks, and low-overhead monitoring built for mobile-first security tooling.

![SanderShield PoC](https://raw.githubusercontent.com/aleksandergrambelik-png/SanderShield/main/screenshots/Screenshot-CVE%20Check.jpg)

- Fast traffic filtering and anomaly detection
- Lightweight defensive automation for exposed services
- Hardening guidance and service exposure scoring
- Built to complement recon and honeypot workflows
- Designed for constrained devices and production-style triage

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
