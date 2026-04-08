NavyOS is an Open Source Android Platform, based on LineageOS, an iOS 26-inspired UI

## Features

- iOS 26-inspired UI system, rebuilt natively on Android
- Redesigned system apps, settings, launcher, and more
- Privacy controls and permission management from LineageOS
- Regular Android security patch updates
- Zero bloatware

<br>

## Supported Devices

| Device | Codename | Status |
|w|----ww------|-----ww---|
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
