# .github

<div align="center">
<br />

<img src="https://img.shields.io/badge/-NavyOS-0A1628?style=for-the-badge&logoColor=white" height="32" />

<br />
<br />

**Android, refined.**

A custom Android operating system built on LineageOS and AOSP,
designed to bring the visual clarity and fluidity of iOS 26 to open-source Android.

<br />

![Android](https://img.shields.io/badge/Android-AOSP-0A1628?style=flat-square&logo=android&logoColor=white)
![Base](https://img.shields.io/badge/Base-LineageOS-0A1628?style=flat-square)
![Status](https://img.shields.io/badge/Status-In%20Development-0A1628?style=flat-square)
![License](https://img.shields.io/badge/License-Apache%202.0-0A1628?style=flat-square)

</div>

---

<br />

NavyOS is not a reskin. It is a deliberate rethinking of how Android looks and feels — borrowing the design language of iOS 26, and rebuilding it from the ground up on a stable AOSP and LineageOS foundation.

Every detail is intentional. From the way sheets slide into view, to how notifications stack, to the weight of the typography — NavyOS is built for people who care about the experience, not just the specs.

<br />

## Design

NavyOS is guided by three principles:

**Clarity.** The interface gets out of the way. Clean layouts, consistent spacing, and purposeful use of color ensure that content — not chrome — takes focus.

**Continuity.** Transitions feel physical. Interactions have weight. Elements respond the way you expect them to, every time.

**Restraint.** Nothing is added without reason. Every component earns its place.

<br />

## Features

- iOS 26-inspired UI system — rebuilt natively on Android
- Physics-based animations and fluid transitions throughout the OS
- Frosted glass (blur) effects on sheets, notifications, and overlays
- Redesigned system apps — dialer, settings, launcher, and more
- Dynamic theming with true light, dark, and adaptive modes
- Privacy controls and permission management from LineageOS
- Regular Android security patch updates
- OTA (over-the-air) update support
- Zero bloatware

<br />

## Supported Devices

| Device | Codename | Status |
|--------|----------|--------|
| — | — | Coming soon |

Device support is expanding. If you want to bring NavyOS to your device, see [Contributing](#contributing).

<br />

## Building

**Requirements:** Ubuntu 22.04+, 16GB RAM minimum, 300GB free disk space, Python 3.x

```bash
# Initialize the manifest
repo init -u https://github.com/NavyOS/android_manifest.git -b main

# Sync sources
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags

# Set up the build environment
source build/envsetup.sh

# Select your device
breakfast <codename>

# Build
brunch <codename>
```

A full build guide, including driver setup and common troubleshooting, is available in the [Wiki](https://github.com/NavyOS/.github/wiki).

<br />

## Repository Structure

```
NavyOS/
├── android_manifest            # Repo manifest — start here
├── vendor_navy                 # NavyOS-specific overlays and configs
├── packages_apps_NavyLauncher  # Home screen and launcher
├── packages_apps_NavyUI        # System UI components
├── device_*                    # Device trees
├── kernel_*                    # Kernel sources
└── OTA                         # OTA update configuration
```

<br />

## Contributing

NavyOS is open to contributions of all kinds.

- **Bug reports** — Open an issue with a logcat and steps to reproduce
- **Device ports** — Submit a working device tree with build instructions
- **UI/UX** — Open a discussion before submitting design-related PRs
- **Translations** — Help localize NavyOS for your language

Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.

<br />

## Community

Discussions, build updates, and support happen on Telegram.

- **Group** — [t.me/navyos](https://t.me/navyos)
- **Updates** — [t.me/navyos_updates](https://t.me/navyos_updates)
- **XDA Thread** — Coming soon

<br />

## License

NavyOS is distributed under the Apache License 2.0, consistent with AOSP and LineageOS licensing terms.

```
Copyright (C) 2025 NavyOS Project

Licensed under the Apache License, Version 2.0.
You may not use this file except in compliance with the License.
http://www.apache.org/licenses/LICENSE-2.0
```

<br />

---

<div align="center">
<br />

*NavyOS — Clean. Fluid. Open.*

</div>
