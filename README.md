# APEX ,  Android Platform Entity Extension

![Platform](https://img.shields.io/badge/platform-Windows-blue)

![Architecture](https://img.shields.io/badge/architecture-x64%20%7C%20arm64-success)

![Status](https://img.shields.io/badge/status-Active%20Development-green)

![License](https://img.shields.io/badge/license-Mixed%20Open--Source-yellow)

---

## Overview

**APEX (Android Platform Entity Extension)** is an advanced, desktop-native Android engineering suite designed to streamline and modernize complex Android platform workflows.

APEX aggregates essential Android development, reverse-engineering, and firmware-level tools into a single, structured, and intuitive graphical environment, eliminating fragmented toolchains and excessive command-line overhead.

It is designed for **Android developers, power users, reverse engineers, security researchers, and custom ROM builders**.

---

## Key Capabilities

- Unified ADB & Fastboot control center  
- ROM cooking and firmware rebuilding  
- Boot / DTBO / AVB image manipulation  
- APK analysis, decompilation, and rebuilding  
- Real-time device screen mirroring  
- Modular, task-oriented workflow navigation  
- Desktop-grade performance and stability  

---

## Technology Stack

| Layer | Technology |
|------|-----------|
| Desktop Runtime | Electron |
| UI Framework | React |
| Build Tooling | Vite |
| Language | TypeScript |
| Styling | Tailwind CSS |
| Binary Orchestration | Node.js |

---

## Integrated Binaries & Tooling

| Tool | Purpose | Source |
|-----|--------|--------|
| 7z | Archive handling | https://www.7-zip.org |
| aapt2 | APK packaging | https://developer.android.com/tools/aapt2 |
| Android Image Kitchen | Boot image tools | https://github.com/osm0sis/Android-Image-Kitchen |
| apktool | APK reverse engineering | https://github.com/iBotPeaches/Apktool |
| avbtool | Android Verified Boot | https://github.com/jcrutchvt10/AVBTOOL |
| jadx | DEX → Java decompiler | https://github.com/skylot/jadx |
| OpenJDK | Java runtime | https://openjdk.org |
| lz4 | Compression | https://github.com/lz4/lz4 |
| magiskboot | Boot patching | https://topjohnwu.github.io/Magisk |
| mkdtboimg | DTBO tool | AOSP |
| platform-tools | adb / fastboot | https://developer.android.com/tools/releases/platform-tools |
| resize2fs | Filesystem resize | e2fsprogs |
| scrcpy | Screen mirroring | https://github.com/Genymobile/scrcpy |
| smali | DEX assembler | https://github.com/JesusFreke/smali |
| sqlite | Database tool | https://sqlite.org |
| tar | Archive tool | GNU Project |
| zipalign | APK optimization | Android SDK |
| zlib | Compression | https://zlib.net |
| zstd | High-speed compression | https://facebook.github.io/zstd |

---

## First-Run Notes

- USB debugging must be enabled on the device
- Device authorization via ADB is required
- Some operations require unlocked bootloader
- EDL mode usage is device-specific

---

## Open-Source Philosophy

APEX does not replace existing tools.

It aggregates, standardizes, and orchestrates open-source Android tooling into a unified desktop experience, while preserving attribution, licensing, and transparency.

---

## Installation

### Windows
Run `APEX-Setup.exe` as Administrator and follow the installer instructions.

---

## Disclaimer

APEX is an advanced system-level toolkit.  
Improper usage may permanently damage devices.

**Use at your own risk.**

---

## License

APEX itself is distributed under a custom license.
Integrated third-party tools remain under their original licenses.

Refer to /licenses for detailed information.

Copyright © 2020-2026 Xoeris

---

## Directory Structure

<details>
<summary><strong>Directory Structure</strong></summary>

```text
APEX
├── app
│   ├── modules
│   │   ├── adb
│   │   ├── fastboot
│   │   ├── rom-kitchen
│   │   └── edl
│   └── ui
│
├── binaries
│   ├── platform-tools
│   ├── boot-tools
│   ├── apk-tools
│   └── compression
│
├── logs
├── temp
└── config
```
