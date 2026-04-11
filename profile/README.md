<p align="center">
  <img src="https://raw.githubusercontent.com/NavyOS/.github/main/profile/logo.png" width="120" alt="NavyOS Logo"/>
</p>

<h1 align="center">NavyOS</h1>
<p align="center">An Open Source Android Platform, based on LineageOS with iOS 26-inspired UI</p>

<p align="center">
  <img src="https://img.shields.io/badge/Android-15-green?style=flat-square&logo=android"/>
  <img src="https://img.shields.io/badge/Based%20on-LineageOS-orange?style=flat-square"/>
  <img src="https://img.shields.io/badge/License-Apache%202.0-blue?style=flat-square"/>
</p>

---

## Features
- iOS 26-inspired UI system, rebuilt natively on Android
- Redesigned system apps, settings, launcher, and more
- Privacy controls and permission management from LineageOS
- Regular Android security patch updates
- Zero bloatware

---

## Building

**Requirements:**
- Ubuntu 22.04+
- 16GB RAM minimum
- 300GB free disk space
- Python 3.x

```bash
# Initialize the manifest
repo init -u https://github.com/NavyOS-Project/android.git -b main

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

---

## Required Sources

Before building, make sure you have all the required sources for your device.

### Mandatory
| Source | Branch | Description |
|--------|--------|-------------|
| [android_device_\<vendor\>_\<codename\>](https://github.com/NavyOS) | `navy-23.2` | Device Tree |
| [android_kernel_\<vendor\>_\<platform\>](https://github.com/NavyOS) | `navy-23.2` | Kernel |
| [android_vendor_\<vendor\>_\<codename\>](https://github.com/NavyOS) | `navy-23.2` | Proprietary Vendor Blobs |

### Optional but Recommended
| Source | Branch | Description |
|--------|--------|-------------|
| android_vendor_\<vendor\>_\<codename\>-firmware | `navy-23.2` | Firmware blobs |
| hardware/\<vendor\> | `navy-23.2` | Hardware HAL |

---

## Porting NavyOS to a New Device

### 1. Device Tree Setup

Clone your device tree and make the following changes:

**`AndroidProducts.mk`** — Register your device product:
```makefile
PRODUCT_MAKEFILES := \
    $(LOCAL_DIR)/navy_<codename>.mk

COMMON_LUNCH_CHOICES := \
    navy_<codename>-userdebug \
    navy_<codename>-user
```

**`navy_<codename>.mk`** — Main product makefile (rename from `lineage_<codename>.mk`):
```makefile
# Inherit NavyOS common config
$(call inherit-product, vendor/navyos/config/common_full_phone.mk)

# Device identifier
PRODUCT_NAME := navy_<codename>
PRODUCT_DEVICE := <codename>
PRODUCT_BRAND := <brand>
PRODUCT_MODEL := <model>
PRODUCT_MANUFACTURER := <manufacturer>
```

**`BoardConfig.mk`** — Update vendor path:
```makefile
# Change this
-include vendor/lineage/config/BoardConfigReservedSize.mk
# To this
-include vendor/navyos/config/BoardConfigReservedSize.mk
```

### 2. Verify No Leftover LineageOS References

After setting up your device tree, run the following to check for any remaining LineageOS references that could cause issues:

```bash
# Check build props
grep -ri "ro\.lineage\." out/target/product/<codename>/system/build.prop
grep -ri "ro\.lineage\." out/target/product/<codename>/vendor/build.prop
grep -ri "ro\.lineage\." out/target/product/<codename>/product/etc/build.prop

# Check device tree
grep -ri "lineage" device/<vendor>/<codename>/ | \
  grep -v "Copyright\|SPDX\|hardware/lineage\|android.hardware.*lineage"
```

The following references are **safe to keep** and do not need to be changed:
- `android.hardware.light-service.lineage` — HAL binary name
- `android.hardware.power-service.lineage-libperfmgr` — HAL binary name
- `hardware/lineage/interfaces` — HAL interface path
- `ro.lineagelegal.url` — Legal URL, no effect on boot
- Copyright headers mentioning LineageOS

### 3. Key Files Summary

| File | What to Change |
|------|---------------|
| `AndroidProducts.mk` | Register `navy_<codename>.mk`, add lunch choices |
| `navy_<codename>.mk` | `PRODUCT_NAME`, inherit from `vendor/navyos` |
| `BoardConfig.mk` | Change `vendor/lineage` → `vendor/navyos` |
| `device.mk` | Remove unsupported packages if any |

---

## Community

Discussions, build updates, and support happen on Telegram.

| Platform | Link |
|----------|------|
| 💬 Group | [t.me/navyos](https://t.me/navyos) |
| 📢 Updates | [t.me/navyos_updates](https://t.me/navyos_updates) |
| 🧵 XDA Thread | Coming soon |

---

## License

NavyOS is distributed under the Apache License 2.0, consistent with AOSP and LineageOS licensing terms.

```
Copyright (C) 2025 NavyOS Project

Licensed under the Apache License, Version 2.0.
You may not use this file except in compliance with the License.
http://www.apache.org/licenses/LICENSE-2.0
```
