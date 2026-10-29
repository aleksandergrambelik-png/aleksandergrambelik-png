# Offensive + Defensive Security ⚡️

This is a 2000s Undernet-style lab, proudly stuffed with polyglots — making everything more efficient, with simple tools. Back then we built stuff on Windows XP. Now we're on phones with potato-power and Java in the pocket.
2000s undernet mindset. 2026 native Java. I write tools your antivirus can't detect. Don't ask me to fix your npm dependencies.

![Profile Views](https://komarev.com/ghpvc/?username=aleksandergrambelik-png&color=blue)

[![SanderShield](https://github.com/aleksandergrambelik-png/SanderShield/actions/workflows/audit.yml/badge.svg)](https://github.com/aleksandergrambelik-png/SanderShield/actions/workflows/audit.yml)

## Overview

I build compact, high-performance network utilities for reconnaissance, hardening, and defensive automation. My work focuses on practical security tooling that runs efficiently in constrained environments.

I often work from a phone, build in Java, and keep the tooling lean enough to be useful in real conditions. The goal is simple: fast signal, practical defense, and systems that remain useful under pressure.

Built for CLI-first engineering, battery-aware automation, and tooling that still performs well when the hardware is constrained.

## Full Features

### 1. Reconnaissance (RECON)
- **Port Scanner:** 100-thread concurrent scanner to detect open ports (21, 22, 23, 25, 53, 80, 110, 111, 135, 139, 143, 443, 445, 3306, 3389, 8080, 5555).
- **Ping:** Test network connectivity to any host or IP address (e.g., 8.8.8.8, 1.1.1.1).
- **IP Geolocation:** Look up the physical location and ISP of any public IP address using the IP-API service.

### 2. Web Vulnerability Scanner (WEB-VULN)
- **12-Header Evidence Scanner:** Audits security headers (HSTS, CSP, X-Frame-Options, CORS, etc.) and outputs evidence in JSON format.
- **NVD CVE Checker:** Connects directly to the National Vulnerability Database API to check for known CVEs (e.g., Log4Shell, Apache Path Traversal).

### 3. Active Defense (DEFENSE)
- **Anti-Phising Clipboard Bot:** Monitors the clipboard in the background for phishing URLs (detects keywords like "login", "hadiah", ".xyz").
- **Stealth Tarpit Honeypot:** Opens fake ports (2121, 2222, 3306, 8080, 33890) to trap and delay port scanners.
- **Safety Guard:** Verifies the APK signature and SHA256 hash to prevent repackaging. Includes AGPLv3 license information.

### 4. Privacy & Anti-Tracking (PRIVACY)
- **Anti-Tracker Auditor:** Scans installed applications for suspicious permissions (Background Location + Microphone + SMS).
- **WiFi Scanner:** Lists nearby WiFi networks (SSID, BSSID, Signal Strength). Requires Location permission.
- **GPS Guard:** Detects if the device is using mock locations and checks network roaming status.

### 5. Hardware & Sensors (SENSORS)
- **GPS Tracker:** Polls the device's GPS location every 5 seconds.
- **Accelerometer:** Reads X, Y, Z axis data from the device's sensor.

### 6. System Information (INFO)
- **Phone Info:** Retrieves the phone number and network operator (if permitted).
- **WiFi Info:** Displays the current WiFi SSID and local IP address.
- **Camera:** Opens the device's camera intent.

### 7. Mini Terminal
- Built-in manual command shell. Type `help` to see all available commands (e.g., `scan <ip>`, `vuln <url>`, `cve <ID>`, `gps on/off`).

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

## Screenshots

| Main Terminal | Command Help |
| :---: | :---: |
| <img src="https://github.com/aleksandergrambelik-png/SanderShield/blob/main/screenshots/Screenshot-command-help.jpg?raw=1" width="400" alt="Main Terminal"> | <img src="https://github.com/aleksandergrambelik-png/SanderShield/blob/main/screenshots/Screenshot-ping.jpg?raw=1" width="400" alt="Command Help"> |

| Vulnerability Scan (OWASP) | CVE Checker |
| :---: | :---: |
| <img src="https://github.com/aleksandergrambelik-png/SanderShield/blob/main/screenshots/owasp.jpg?raw=1" width="400" alt="Vulnerability Scan (OWASP)"> | <img src="https://github.com/aleksandergrambelik-png/SanderShield/blob/main/screenshots/Screenshot-CVE%20Check.jpg?raw=1" width="400" alt="CVE Checker"> |

| Privacy & Anti-Tracker | GPS & Sensor Data |
| :---: | :---: |
| <img src="https://github.com/aleksandergrambelik-png/SanderShield/blob/main/screenshots/Screenshot-Privacy.jpg?raw=1" width="400" alt="Privacy & Anti-Tracker"> | <img src="https://github.com/aleksandergrambelik-png/SanderShield/blob/main/screenshots/Screenshot-GPS-Sensor.jpg?raw=1" width="400" alt="GPS & Sensor Data"> |

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
