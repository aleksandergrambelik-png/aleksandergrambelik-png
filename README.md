# Offensive + Defensive Security ⚡️

This is a 2000s underground-style lab, packed with polyglots and practical tools — making everything more efficient, with simple systems. Back then we built things on Windows XP. Now we do it from a modern Android-first workflow.

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)

![Profile Views](https://komarev.com/ghpvc/?username=aleksandergrambelik-png&color=blue)

[![Termux](https://img.shields.io/badge/Termux-Compatible-cyan?style=for-the-badge&logo=termux)](https://github.com/termux/termux-app)

[![Ethical Hacking](https://img.shields.io/badge/Ethical-Hacking-maroon?style=for-the-badge&logo=hackthebox)](https://www.hackthebox.com/)

[![Android](https://img.shields.io/badge/Platform-Android-green?style=for-the-badge&logo=android)](https://github.com/aleksandergrambelik-png/SanderShield//releases/tag/v38.0)

[![Bug Bounty](https://img.shields.io/badge/Bug-Bounty-gold?style=for-the-badge&logo=bugcrowd)](https://www.bugcrowd.com/bug-bounty-university/)

[![Java](https://img.shields.io/badge/Language-Java-red?style=for-the-badge&logo=openjdk)](https://adoptium.net/)

### What's New : [![Release v38.0](https://img.shields.io/badge/Release-v38.0-2ea44f?style=for-the-badge)](https://github.com/aleksandergrambelik-png/SanderShield/releases/tag/v38.0)

- **Splash Screen:** Boot animation with ASCII loading sequence.
- **ASCII Banner:** New hacker-style banner on startup.
- **Hardware Monitor:** Real-time battery percentage and signal strength (dBm) monitor.
- **Clean Manifest:** Removed duplicated permissions, optimized for Android 12+.

### Apk. New Native Hex Editor & Reverse Tool On Mobile  No Root

[![Release v1.0](https://img.shields.io/badge/Release-v1.0-2ea44f?style=for-the-badge)](https://github.com/aleksandergrambelik-png/SanderHexDump/releases/tag/v1.0)

0.Classic Hex View: 12-byte per line with Offset, Hex, and ASCII representation side-by-side.

1.Color Highlighting: Blue for Offset, White for Hex, and Gray for non-printable ASCII. Optimized for readability.

2.Bold Monospace Font: Tuned for 720p mobile screens to prevent text wrapping.

3.Copy Log: Easily copy the entire hex dump to your clipboard for reporting.

4.BackTrack-Style UI: Pure black background with a terminal-like interface. No bloated UI elements.

## Next Feature Upgrade. File Picker, Pattern Search, Hash

### SCRENSHOOT
<img width="1080" height="2015" alt="Image" src="https://github.com/user-attachments/assets/438efa97-a837-40b5-bd7e-d8da93efc58a" />


## 🔍 Hex Viewer: What Can You Inspect?

The Hex Viewer is a built-in native tool to read the raw binary data (Magic Bytes) of almost any file. It's perfect for quick digital forensics and malware analysis without needing a PC.

### Supported File Types & Use Cases:

1. **Images (JPG, PNG, WEBP)**
   * **What you'll see:** Magic Bytes (e.g., JPEG starts with `FF D8 FF`, PNG with `89 50 4E 47`).
   * **Use Case:** Verify if a file received via WhatsApp is actually an image or a disguised malware (e.g., an `.apk` renamed to `.jpg`).

2. **Android APKs**
   * **What you'll see:** APKs are ZIP archives. You'll see the `50 4B 03 04` (PK) header and strings like `AndroidManifest.xml` or `classes.dex`.
   * **Use Case:** Quick recon to identify package names or libraries inside an APK without decompiling it with heavy tools.

3. **Text / Scripts (HTML, XML, JS, SH)**
   * **What you'll see:** Readable text in the hex dump (e.g., `3C 68 74 6D 6C 3E` translates to `<html>`).
   * **Use Case:** Inspect hidden scripts or read config files that contain weird characters not supported by standard text editors.

4. **Databases (.db / .sqlite)**
   * **What you'll see:** The `53 51 4C 69 74 65 20 66 6F 72 6D 61 74 20 33` header (SQLite format 3).
   * **Use Case:** Verify if a database is authentic or scan for hidden strings inside it.

5. **System / Linux Binaries (.dex, ELF, .so)**
   * **What you'll see:** The `7F 45 4C 46` header (ELF), indicating a Linux executable.
   * **Use Case:** Basic malware analysis or file system integrity checks.

6. **Archives (ZIP, RAR, 7z)**
   * **What you'll see:** Magic bytes like `50 4B` (ZIP) or `52 61 72 21` (Rar!).
   * **Use Case:** Check for corrupted archives or detect hidden files embedded inside an archive (like a ZIP bomb).

### 📖 How to Use (Cara Pakai)
1. Open the SanderShield Terminal.
2. Type the following command:
   ```bash
   hex /sdcard/Download/yourfile.jpg


## Overview

I build compact, high-performance network utilities for reconnaissance, hardening, and defensive automation. My work focuses on practical security tooling that runs efficiently in constrained environments.

I build in Java, and keep the tooling lean enough to remain useful in real conditions. The goal is simple: fast signal, practical defense, and systems that stay useful under pressure.

Built for CLI-first engineering, battery-aware automation, and tooling that still performs well even on limited hardware.

I don't beg for Stars or Forks. I build because I want to. If you use it, great. If you donate, thank you. If you don't, I don't care."
Modern devs are obsessed with licenses and copyrights. Back in 2009, we just shared the code and said 'here, don't be a skid'. 🥸

## Stealth & Portable Philosophy

SanderShield is designed to be Stealth & Portable. It does not require root access because it uses pure Java Sockets (TCP Connect scan), which is highly accurate for checking ports.

We believe that if you use root, your phone is already "dirty" and its integrity cannot be guaranteed. We want you to focus on the target and audit your actual work, not on messing with your own device.

1. Safety Guard Detect Root:
As seen in the screenshot, the output shows "device_rooted": false and "status": "SECURE". This means the app hooks into the system to check if the phone is rooted. If it is, the Safety Guard will trigger protective actions.

## Why SanderShield?

- **No Termux Required:** Unlike other tools that are just wrapper scripts, SanderShield is a 100% Native Java APK. You don't need to install Termux, Python, or any other environment. Download the APK and use it directly.
- **Anti-Tamper Protection:** Built-in "Safety Guard" verifies the APK's digital signature and SHA256 hash. If someone tries to repack the APK or inject malicious code, the app will detect it and refuse to run.
- **Zero Dependencies:** No external libraries. No Gradle. No bloatware.

## Full Features

### 1. Reconnaissance (RECON)
- **Port Scanner:** 100-thread concurrent scanner to detect open ports (21, 22, 23, 25, 53, 80, 110, 111, 135, 139, 143, 443, 445, 3306, 3389, 8080, 5555).
- **Ping:** Test network connectivity to any host or IP address (e.g., 8.8.8.8, 1.1.1.1).
- **IP Geolocation:** Look up the physical location and ISP of any public IP address using the IP-API service.

### 2. Web Vulnerability Scanner (WEB-VULN)
- **12-Header Evidence Scanner:** Audits security headers (HSTS, CSP, X-Frame-Options, CORS, etc.) and outputs evidence in JSON format.
- **NVD CVE Checker:** Connects directly to the National Vulnerability Database API to check for known CVEs (e.g., Log4Shell, Apache Path Traversal).

### 3. Active Defense (DEFENSE)
- **Anti-Phishing Clipboard Bot:** Monitors the clipboard in the background for phishing URLs (detects keywords like "login", "hadiah", ".xyz").
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
## Legacy

![version](https://img.shields.io/badge/version-v34.0-blue)

## NEW

[![Release v38.0](https://img.shields.io/badge/Release-v38.0-2ea44f?style=for-the-badge)](https://github.com/aleksandergrambelik-png/SanderShield/releases/tag/v38.0)


[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)

[![Termux](https://img.shields.io/badge/Termux-Compatible-cyan?style=for-the-badge&logo=termux)](https://github.com/termux/termux-app)

[![Ethical Hacking](https://img.shields.io/badge/Ethical-Hacking-maroon?style=for-the-badge&logo=hackthebox)](https://www.hackthebox.com/)

[![Android](https://img.shields.io/badge/Platform-Android-green?style=for-the-badge&logo=android)](https://github.com/aleksandergrambelik-png/SanderShield)

[![Bug Bounty](https://img.shields.io/badge/Bug-Bounty-gold?style=for-the-badge&logo=bugcrowd)](https://www.bugcrowd.com/bug-bounty-university/)

[![Java](https://img.shields.io/badge/Language-Java-red?style=for-the-badge&logo=openjdk)](https://adoptium.net/)


[![Official SHA256](https://img.shields.io/badge/Official%20SHA256-4616e445b16199154a3885c4c69da936e4e08785c758b15257d7c3f54703cc3f-blue?style=for-the-badge)](https://github.com/aleksandergrambelik-png/SanderShield/releases/tag/v38.0)

[![APK Hash](https://img.shields.io/badge/APK%20Hash-98F229735D9C0ECF40262C826400237678020CB8F4E7350833DDB61E43DE2AA1-orange?style=for-the-badge)](https://github.com/aleksandergrambelik-png/SanderShield/releases/tag/v38.0)

> Warning: This tool is intended for authorized testing only. Not for beginners. Minimum requirement: basic IT knowledge, understanding of web technologies, a cybersecurity mindset, and a bug-hunting mindset.

Minimal but effective defensive shield for hostile environments: request filtering, hardening checks, and low-overhead monitoring built for mobile-first security tooling.

- Fast traffic filtering and anomaly detection
- Lightweight defensive automation for exposed services
- Hardening guidance and service exposure scoring
- Built to complement recon and honeypot workflows
- Designed for constrained devices and production-style triage

## Screenshots

| Main Terminal | Command Help |
| :---: | :---: |
| <img src="screenshots/Screenshot-command-help.jpg" width="400"> | <img src="screenshots/Screenshot-ping.jpg" width="400"> |

| Vulnerability Scan (OWASP) | CVE Checker |
| :---: | :---: |
| <img src="screenshots/owasp.jpg" width="400"> | <img src="screenshots/Screenshot-CVE Check.jpg" width="400"> |

| Privacy & Anti-Tracker | GPS & Sensor Data |
| :---: | :---: |
| <img src="screenshots/Screenshot-Privacy.jpg" width="400"> | <img src="screenshots/Screenshot-GPS-Sensor.jpg" width="400"> |


[→ Explore SanderShield](https://github.com/aleksandergrambelik-png/SanderShield)

---

## Philosophy

I prefer tools that work in the wild: compact, fast, and useful. If it warms my phone, it still gets the job done.

## Support Development

If you want to support the project and keep the tools growing, you can buy me a coffee:

[![Ko-fi](https://img.shields.io/badge/Ko--fi-Support-orange?style=for-the-badge&logo=ko-fi)](https://ko-fi.com/sander_0x04)

## GitHub Stats

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=aleksandergrambelik-png&show_icons=true&theme=dark)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=aleksandergrambelik-png&layout=compact&theme=dark)

---

## Tech & Tools

![Termux](https://img.shields.io/badge/Termux-000000?style=for-the-badge&logo=termux&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

Made on a phone. Made to work. ⚙️
