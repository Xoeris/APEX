# APEX Third-Party Notices

APEX is proprietary software of Xoeris (see `LICENSE.md` and `EULA.md`). It uses, bundles or runs the third-party components listed below. Each component remains under its own license; nothing in the APEX license changes those terms. Where a license requires it, the copyright notice and permission text are reproduced in the section "License texts" below.

## Libraries compiled into the APEX apps

| Component | Version | License | Source |
|---|---|---|---|
| Avalonia (Avalonia, Avalonia.Desktop, Avalonia.Themes.Fluent) | 12.1.2 | MIT | https://github.com/AvaloniaUI/Avalonia |
| Avalonia.Fonts.Inter / Inter typeface | 12.1.2 | SIL Open Font License 1.1 | https://github.com/rsms/inter |
| CommunityToolkit.Mvvm | 8.4.2 | MIT | https://github.com/CommunityToolkit/dotnet |
| Microsoft.Extensions.DependencyInjection | 8.0.1 | MIT | https://github.com/dotnet/runtime |
| AdvancedSharpAdbClient | 3.6.16 | Apache License 2.0 | https://github.com/SharpAdb/AdvancedSharpAdbClient |
| .NET runtime and base class libraries | 10 | MIT | https://github.com/dotnet/runtime |

## Native code built into `apexnative`

The shared library `apexnative` (`apexnative.dll`, `libapexnative.so`, `libapexnative.dylib`) is built from the following Android Open Source Project (AOSP) sources and their dependencies.

| Component | License | Source |
|---|---|---|
| libsparse, liblp, simg2img, img2simg, append2simg, lpmake, lpadd, lpflash, lpunpack (AOSP `system/core`, `system/extras`) | Apache License 2.0 | https://android.googlesource.com/platform/system/core |
| libbase, liblog (AOSP `system/libbase`, `system/logging`) | Apache License 2.0 | https://android.googlesource.com/platform/system/libbase |
| fmt (AOSP `external/fmtlib`) | MIT | https://github.com/fmtlib/fmt |
| e2fsprogs / ext4_utils parts (AOSP `external/e2fsprogs`) | GPL-2.0, LGPL-2.0 and BSD-style, depending on the file | https://android.googlesource.com/platform/external/e2fsprogs |
| lz4 library (AOSP `external/lz4`) | BSD 2-Clause | https://github.com/lz4/lz4 |
| SQLite (AOSP `external/sqlite`) | Public domain | https://www.sqlite.org |
| erofs-utils (`mkfs.erofs`, `dump.erofs`, `fsck.erofs`) | Apache License 2.0 or GPL-2.0-or-later | https://android.googlesource.com/platform/external/erofs-utils |
| smali / baksmali | BSD 3-Clause | https://github.com/google/smali |

The Windows builds of these tools are compiled with MinGW-w64.

## Tools bundled with or downloaded by APEX

APEX runs these as separate programs. They are fetched unmodified from their official upstream releases.

| Component | License | Source |
|---|---|---|
| Android SDK Platform-Tools (adb, fastboot, mke2fs and related tools) and Build-Tools (aapt, aapt2, zipalign, apksigner) | Apache License 2.0 and the Android Software Development Kit License Agreement | https://developer.android.com/tools |
| 7-Zip | GNU LGPL 2.1 with the unRAR restriction; BSD-licensed parts | https://www.7-zip.org |
| lz4 command-line program (Windows) | GPL-2.0 | https://github.com/lz4/lz4 |
| Eclipse Temurin JRE 21 | GPL-2.0 with the Classpath Exception | https://adoptium.net |
| payload-dumper-go | Apache License 2.0 | https://github.com/ssut/payload-dumper-go |
| APKEditor | Apache License 2.0 | https://github.com/REAndroid/APKEditor |
| Apktool | Apache License 2.0 | https://github.com/iBotPeaches/Apktool |
| Magisk (`magiskboot`, `magisk32`, `magisk64`, `magiskinit`) | GPL-3.0-or-later | https://github.com/topjohnwu/Magisk |
| brotli support | .NET built-in `System.IO.Compression` (MIT) | https://github.com/dotnet/runtime |

### Source code for GPL and LGPL components

For components licensed under the GPL or LGPL (lz4 command-line program, Magisk, 7-Zip, e2fsprogs parts, Temurin), the complete corresponding source code is available from the upstream locations given above. Xoeris will also provide it on request for as long as the law requires; write to xoeris.official@gmail.com. APEX does not modify these programs and runs them as separate programs.

## License texts

### MIT License (Avalonia, CommunityToolkit.Mvvm, Microsoft.Extensions.DependencyInjection, .NET, fmt)

Copyright (c) the respective authors and contributors of each component named above.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

### Apache License 2.0

Licensed under the Apache License, Version 2.0. You may obtain a copy of the license at https://www.apache.org/licenses/LICENSE-2.0. Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

### SIL Open Font License 1.1 (Inter)

The Inter typeface is licensed under the SIL Open Font License, Version 1.1, available at https://openfontlicense.org. The font is bundled unmodified and is not sold by itself.

### BSD licenses (lz4 library, smali / baksmali)

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the copyright notice, the list of conditions and the disclaimer of the respective license are retained, and that the names of the copyright holders are not used to endorse derived products without permission (BSD 3-Clause). THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES ARE DISCLAIMED. The full texts are in the upstream repositories listed above.

### GNU licenses (GPL-2.0, GPL-3.0, LGPL-2.1)

The full texts are available at https://www.gnu.org/licenses/ and in the upstream repositories listed above.
