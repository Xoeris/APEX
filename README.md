<p align="left">
  <img width="550" alt="Xoeris - APEX Mockup (Rounded)" src="https://github.com/user-attachments/assets/1d518622-6eef-4f57-b441-e80a0fd8aa8a" />
</p>

# APEX (Android Platform Entity Extension)

![Platform](https://img.shields.io/badge/platform-Windows-blue)
![Architecture](https://img.shields.io/badge/architecture-x64%20%7C%20arm64-success)
![Status](https://img.shields.io/badge/status-Active%20Development-green)
![License](https://img.shields.io/badge/license-Mixed%20Licensing-yellow)

---

## Overview

**APEX (Android Platform Entity Extension)** is a desktop-grade Android engineering control system designed to manage, analyze, and manipulate Android devices at a system level with precision, safety, and clarity.

APEX provides a unified environment where complex Android platform operations—traditionally performed through fragmented utilities and manual command execution—are transformed into structured, deterministic workflows. Every operation is executed through a controlled pipeline that prioritizes transparency, reliability, and full user awareness.

APEX is built for **Android engineers, power users, reverse engineers, security researchers, and custom ROM developers** who require professional-grade control over Android system internals.

---

## Design Philosophy

APEX is not a loose collection of scripts or utilities.

It is engineered as a **centralized orchestration layer** that:
- Maintains full visibility over device state and operations
- Eliminates ambiguity in system-level workflows
- Reduces operational risk during low-level modifications
- Enables repeatable and traceable engineering actions

The platform emphasizes deterministic execution, modular workflows, and desktop-class performance under sustained workloads.

---

## Key Capabilities

- Unified device communication and state management  
- Centralized ADB & Fastboot control interface  
- ROM cooking and firmware reconstruction  
- Boot / DTBO / AVB image analysis and modification  
- APK inspection, rebuilding, and structure analysis  
- Real-time device screen mirroring  
- Modular, task-oriented workflow navigation  
- Stable performance during high-intensity operations  

---

## Integrated Binaries & Tooling

APEX internally orchestrates a curated set of Android platform utilities to deliver a seamless engineering experience.

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
| magiskboot | Boot image patching | https://topjohnwu.github.io/Magisk |
| mkdtboimg | DTBO tooling | AOSP |
| platform-tools | adb / fastboot | https://developer.android.com/tools/releases/platform-tools |
| resize2fs | Filesystem resizing | e2fsprogs |
| scrcpy | Screen mirroring | https://github.com/Genymobile/scrcpy |
| smali | DEX assembler | https://github.com/JesusFreke/smali |
| sqlite | Embedded database | https://sqlite.org |
| tar | Archive tool | GNU Project |
| zipalign | APK optimization | Android SDK |
| zlib | Compression | https://zlib.net |
| zstd | High-speed compression | https://facebook.github.io/zstd |

---

## First-Run Notes

- USB debugging must be enabled on the device  
- Device authorization via ADB is required  
- Some operations require an unlocked bootloader  
- EDL mode support is device-specific  

---

## Installation

### Windows

Run `APEX-Setup.exe` as Administrator and follow the installer instructions.

---

## Disclaimer

APEX is an advanced system-level engineering platform.  
Improper usage may permanently damage devices, partitions, or data.

**Use at your own risk.**

---

## License

APEX itself is distributed under a custom license.  
Integrated third-party components remain under their respective licenses.

Refer to `/licenses` for detailed legal information.

Copyright © 2020–2026 Xoeris

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
