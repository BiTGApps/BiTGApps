## BiTGApps — Google Apps Package (Official Repository)

[![Official Website](https://img.shields.io/badge/Official-Website-brightgreen?style=for-the-badge)](https://bitgapps.io)
[![Telegram Group](https://img.shields.io/badge/Telegram-Group-blue?style=for-the-badge)](https://t.me/BiTGAppsChat)

Welcome to the official documentation repository for **BiTGApps**, a custom **Google Apps Package** designed for Android enthusiasts, developers, and custom ROM users. 

Established in **2018**, the BiTGApps project has spent nearly a decade providing streamlined, optimized, and rock-solid **GApps** solution to the Android modding community.

**Official Downloads & Documentation:** [https://bitgapps.io](https://bitgapps.io)

---

## What is BiTGApps?

**BiTGApps** is a customized, open-source **GApps package** used to sideload Google Play Services, frameworks, and essential applications onto Custom Android operating systems.

If you are flashing a custom ROM (like LineageOS or independent AOSP builds) that does not include Google services out of the box, you must flash a reliable **GApps** package immediately afterward to gain access to the Google Play Store.

### Why Choose BiTGApps?
- **Project Longevity (Since 2018):** Active development since 2018. The installation scripts and package layouts have been continuously updated and maintained across multiple Android generations.
- **Broad Android Version Support:** Maintained compatibility tracking for modern Android releases, with packages tailored for Android 17.0 all the way down to legacy Android 7.1.x.
- **Dual-Installation Method:** Can be flashed traditionally via custom recoveries (TWRP, OrangeFox, Lineage Recovery) or mounted seamlessly as a systemless **Magisk/KernelSU module**.
- **Smart Space Engine:** Advanced installation scripts that allow you to re-flash your preferred **GApps** variant even when your system partition runs critically low on space.

## Tailored GApps Variants & Packages

We understand that different users have different device limitations and performance preferences. That is why BiTGApps is distributed in a wide variety of custom-tailored **GApps packages**, ranging from minimal setups to full application suites:

- **Core:** The single minimal layout. Contains only essential Google Play Services (GMS), Google Services Framework (GSF), the Google Play Store, and necessary base synchronization backends.
- **Mini / Omni / Roar:** Intermediate distributions. These include additional Google applications beyond the base tier but maintain a lightweight profile by excluding the broader apps found in heavier tiers.
- **Nano / Atom / Pico / Tint:** Extended distributions containing a wider selection of Google user applications and additional framework dependencies.
- **Full:** The comprehensive package which safely replaces stock AOSP utilities with their Google alternatives for a complete Pixel-like environment.

> [!NOTE]
> *All packages are built using untouched upstream APK payloads sourced directly from the latest monthly Google Pixel OTA images to ensure maximum security and stability.*

## How to Install BiTGApps

To avoid system crashes, bootloops, or Google Play Services framework errors, please follow the strict installation order outlined below.

### Option A: Custom Recovery Installation (Highly Recommended)
1. Boot into your custom recovery environment (TWRP, Lineage Recovery, etc.).
2. Wipe your device partitions as required by your custom ROM.
3. Flash your preferred Custom ROM ZIP file.
4. **Immediately flash the BiTGApps ZIP package** before booting into the Android system.
5. *(Optional)* Flash any supplemental freeware addon.
6. Reboot system and complete the **SetupWizard configuration**.

> [!IMPORTANT]
> *If you reboot into the system before installing your GApps package, you must factory reset your device and flash the packages in the correct order, otherwise Google Play Services will continuously crash.*

### Option B: Systemless Module Installation (Optional)
Our unique unified installation stack detects your root environment automatically. The exact same ZIP package can be flashed directly in **Magisk** or **KernelSU** to bypass recovery restrictions entirely.

> [!NOTE]
> *KernelSU (and forks) Users: Ensure you have a compatible **metamodule** installed and initialized before applying the GApps module to guarantee system files load properly upon reboot.*

## Seamless OTA Survival

BiTGApps comes pre-bundled with version 3 of **addon.d survival script**.

If your custom ROM supports native backup functionalities (the vast majority of modern AOSP-based ROMs do), you enjoy a true **"flash and forget"** experience. When you update or dirty-flash your custom ROM, our script automatically backs up your entire GApps framework configuration and restores it cleanly post-update. You do not need to manually re-flash BiTGApps during monthly system updates.

---

## Contributing, Support & Help

We welcome the community to actively help improve the BiTGApps project. If you encounter any bugs, need assistance with configuration files, or want to contribute:

- **Open an Issue:** If you find a bug in our installation scripts, setup processes, or need general project help, please feel free to **[open a GitHub Issue](https://github.com/BiTGApps/BiTGApps/issues)** in this repository. Provide as much detail as possible so our community can assist you swiftly.
- **Submit a Pull Request (PR):** If you want to submit a bug fix, or improve installation logic, please **[submit a Pull Request](https://github.com/BiTGApps/BiTGApps/pulls)**. We actively review community contributions!

---

## Get the Latest GApps Downloads

Do not trust unverified mirrors or outdated third-party source listings that compromise your security. Always fetch your packages directly from our secure, official channels. Since the downloads are now strictly served through the official BiTGApps website only:

- **Download GApps:** [Visit Official BiTGApps Website](https://bitgapps.io)
- **Support Forums:** [Check the XDA Developers Thread](https://forum.xda-developers.com/t/custom-gapps-bitgapps-for-android.4012165)
- **Announcements:** [Join our Official Telegram Channel](https://t.me/BiTGAppsOfficial)

> [!NOTE]
> *Android is a registered trademark of Google LLC. This project is a community-driven, independent modification and is not legally affiliated with or endorsed by Google Inc.*
