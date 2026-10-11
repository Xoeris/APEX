# APEX

**A cross-platform Android firmware toolkit** — unpack, browse, modify, rebuild and flash Android firmware from one desktop app, without WSL or a pile of command-line tools.

Built with **.NET 10**. Runs on **Windows, Linux and macOS**.

> Status: `1.0.0` — active development. Closed source.

---

## Table of contents

1. [Features](#features)
2. [How it works](#how-it-works)
3. [Typical RBK workflow](#typical-rbk-workflow)
4. [Performance and resource settings](#performance-and-resource-settings)
5. [Platform support](#platform-support)
6. [Known limitations](#known-limitations)

---

## Features

APEX is a **desktop toolkit** with a companion **Android app** (Xoeris APEX for Android).

### Desktop app — pages

| Page | What it does |
|---|---|
| **Dashboard (Overview)** | Device status, recent devices, recent commands and activity at a glance. |
| **RBK** | The ROM workshop — see below. |
| **Commands** | ADB and fastboot command runner with presets (`adb devices`, reboot to bootloader/recovery, `getprop`, `fastboot` commands), output log. |
| **Logs** | Full CLI session output, copy / save / clear, ANSI-colour stripping, auto-scroll. |
| **Analytics** | Commands run, success rate vs last session, average execution time, failed commands, flash operations by partition, CSV export. |
| **Settings** | Preferences, performance and hardware, developer options, license — see [Settings](#settings). |
| **About** | Credits and open-source acknowledgements. |

The menu bar also gives you project management (New / Rename / Duplicate / Delete / Clean Output, Open Workspace, Save As / Save a Copy), *Run Selected Tasks*, *Cancel Running Tasks*, *Clear Build Log*, and a **RBK Mode** switch.

### RBK (ROM workshop)

**Projects and import**
- Create projects, open them from a workspace, keep a per-project `Source/`, `Config/`, `Backup/` and output layout.
- Import ZIP, `payload.bin` or raw images. The package is **hard-linked** into `Source/` when on the same volume (instant for multi-GB files) and copied otherwise.

**ROM Extractor**
- *Extract ROM* in one run: package → `super.img` → logical partitions → file trees, with per-stage and per-partition timings in the log.
- *Extract payload.bin* (payload-dumper-go) for A/B OTA packages.
- *Extract firmware from Source* for projects already imported.
- Symlinks are recorded in `Config/<partition>_symlinks` so extraction works on filesystems without symlink rights.

**Super Image Packer / single-image packing**
- *Pack Super Image* (lpmake) and *Pack Single IMG Partitions*.
- Odin-style packaging: `.tar` with optional **LZ4** (`.img.lz4`) and **`.md5`**.
- Batch partition builds, *Repack to Build*, *Clean Output*.

**Browse**
- Open a partition image (or folder) read-only, search the whole image or by path, navigate folders, *Extract selected…* / *Extract this folder…*.

**Compare**
- Tree compare of two images/folders (LEFT e.g. stock vs RIGHT e.g. built): filter by *Identical / Added / Removed / Content differs / Metadata differs / Kind changed*, "Changed only".

**Apps (debloater)**
- Lists APKs with name, package, partition, type, size and a **risk verdict** (Safe / Caution / Risky / Critical), filter by risk or search by name/package.
- Remove to `Backup/Apps` and restore.

**Lab**
- Unpack / repack `boot`, `init_boot`, `vendor_boot`, `recovery` (magiskboot), edit the ramdisk, fstab and DTB, mount table view, *Save to ramdisk*.
- Verity / force-encrypt stripping and AVB flags, RKP and DEFEX hex patches, `vbmeta` patching.
- **Magisk patching** with the bundled Magisk libraries (`magisk32/64`, `magiskinit`).

**APK Workshop** (decompile · recompile · sign · merge)
- **Apktool** and **APKEditor** decompile/recompile/merge, **baksmali / smali** disassemble and assemble (*Smali Tools*), **zipalign**, **apksigner** signing (`*_signed.apk`), framework install/list (`Install fw` / `List fw`), `ApkManifest` package info.

**Workspace**
- Project details panel (model, manufacturer, codename, SoC/board, Android version, security patch), bundled-tools status (7-Zip, aapt/zipalign, apksigner, baksmali/smali, magiskboot, mke2fs, payload-dumper, simg2img, Java JRE) and file-format detection.

### Format support

| Format | Support |
|---|---|
| **ext4** | read, walk, extract (managed) |
| **EROFS** | plain, inline, chunk-based and **LZ4-compressed** (legacy + compact index), managed |
| **Android sparse** | seekable read-only view (RAW / FILL / DONT_CARE) and unsparse, managed |
| **super.img (LP)** | geometry + metadata v10.x, primary/backup slots, per-partition extraction, managed |
| **NEW.DAT / `.br` / transfer.list** | `Sdat2Img` conversion |
| **Detection** (`FormatDetector`) | sparse, ext4, f2fs, erofs, super, boot / init_boot / vendor_boot / recovery, vbmeta, dtbo, dtb, SELinux policy, `file_contexts.bin`, zip, 7z, rar, tar, Odin tar.md5, gzip, xz, lzma, lz4, brotli, bzip2, zstd, lzo, payload, new.dat(.br), update.zip, Amlogic, Allwinner, apk, jar, dex, vdex, odex, resources.arsc, binary XML |

Because the readers are C#, Windows needs no `simg2img`, `lpunpack` or WSL to extract a ROM. Output was verified against CRB's own extraction (14,000+ files, no content differences).

### Settings
Auto-scroll log, strip ANSI codes, Python executable path, **Maximize CPU Threads**, **Dedicated RAM Allocation**, **GPU hardware acceleration**, Developer Mode, **license & activation** (FREE vs PRO with hardware ID).

### Android app (Xoeris APEX for Android)
Package `com.xoeris.android.app.apex` · minSdk 24 · targetSdk 36 · ABIs `armeabi-v7a`, `arm64-v8a`, `x86`, `x86_64` · 14 translations. Python (Chaquopy) core plus a native terminal.

- **RBK on the phone:** unpack / pack **super.img** (lpunpack / lpmake), single-partition repack (packing method, access, size, compression level), sparse conversion, brotli/zstd decompression, **vbmeta patching**, **Magisk boot-image patching**, **APK decompile / build & sign** (standard or silent root install), DEX ↔ smali, format conversion and ROM menus.
- **Editors and viewers:** boot & recovery scene, **hex editor** (offset / hex / ASCII), **smali editor**, **text editor**, **archive viewer**, **APK editor**.
- **Root:** root shell and silent root install.
- **File manager (Xoeris):** storage overview, folders, recent files, properties (permissions, owner, group, counts), file operations.
- **Terminal:** built-in terminal emulator (native `apex-terminal`).
- **Media:** image/video viewer, PDF viewer, music player with mini-player and service.
- Light/dark theming.

### Built-in AOSP tools
`simg2img`, `img2simg`, `append2simg`, `lpmake`, `lpadd`, `lpflash` and `lpunpack` run inside APEX itself, so there are no separate processes to locate or install.

---

## How it works

```
 firmware zip ──hard-link──▶ Source/
                                │
              ┌─────────────────┴─────────────────┐
              ▼                                   ▼
     super.img (raw or sparse)             other images (boot, vbmeta, …)
              │  built-in sparse + LP readers
              ▼
   system / vendor / product / odm …  (ext4 or EROFS)
              │  built-in EROFS / ext4 readers
              ▼
   parallel extractor  ──▶  parallel streaming writes ──▶ project tree
```

- Partitions are processed **one at a time**, with parallelism *inside* each partition. Benchmarks showed whole-partition parallelism thrashes the disk and is slower.

---

## Typical RBK workflow
1. Open **RBK** → **New Project** and pick a firmware package.
2. Let APEX import it and run **Extract ROM**.
3. Browse or edit the extracted trees in the project folder.
4. Use **Build** to repack, then flash with the device tools.

---

## Performance and resource settings

Extraction speed is bound by disk writes, not decompression. APEX measures and plans accordingly:

- **Maximize CPU Threads** (Settings): workers = `clamp(logical CPUs / 2, 2, 4)`; otherwise 1.
- **Dedicated RAM Allocation** (Settings): the memory budget is the smaller of your setting and **75 % of physical RAM**, so the rest of the system always keeps headroom. Buffers are 8 / 4 / 1 MB depending on the budget, and workers are reduced when the budget is small.
- The plan is logged at the start of every extraction, e.g. `4 workers, 8 MB buffers, 16.0 GB budget of 23.7 GB RAM`.

Reference run on NVMe (47 partitions): **≈ 3 min 41 s** end to end, against ≈ 3 min 30 s for CRB's Linux-tool pipeline. The streaming extractor is 4–7× faster than the earlier whole-file version while using ~120 MB instead of gigabytes.

Tip: adding the projects folder to your antivirus exclusions can reduce write time noticeably.

---

## Platform support

| Capability | Windows | Linux | macOS |
|---|---|---|---|
| Desktop app | ✅ | ✅ | ✅ |
| ext4 / EROFS / sparse / super reading | ✅ managed | ✅ managed | ✅ managed |
| Hard-link import | ✅ `CreateHardLinkW` | ✅ `link` | ✅ `link` |
| EROFS repack | ✅ | ✅ | ❌ |
| `magiskboot` | ✅ | ✅ | ✅ |

---

## Known limitations

- **EROFS reader** rejects big pclusters, non-LZ4 algorithms, HEAD2, and inline/fragment compression.
- `lpdump` is not built (needs protobuf).
- Build and pack flows, and some RBK screens, are less tested than extraction.
- EROFS repacking has no lzma compression and is not available on macOS.

---

## Acknowledgements

AOSP (`liblp`, `libsparse`, `libbase`, `erofs-utils`), CRB (reference behaviour), and the platform-tools, payload-dumper-go, APKEditor and apktool projects.
