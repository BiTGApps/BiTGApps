# Safetynet Patch Installation Instructions

BiTGApps does contain safetynet patches for passing CTS profile. Installation of Safetynet Patch is not enabled by default. For that you need **cts-config.prop** file.
When this config file not present in device, at the time of installation you will be notified with following texts.

```! CTS config not found```

```! Skip installing CTS patch```

Build property from `system` and `vendor` patched for passing **basic integrity**.

Patched keystore used for passing **CTS profile**.

## Android Version Support

* 8.0.0 and above

## OS Patch Level

* Security Patch Level

Some devices need same SPL in `system`, `vendor` and `boot`. If found mismatching then device refuse to boot into system.
On technical side, **Keymaster HAL** crashing becuase of different SPL in `boot` then `system` and `vendor`.
The Keymaster trusted app in TrustZone refuses to work if `system`, `vendor` and `boot` SPLs don't match. It's part of anti-rollback protection.

To fix this issue, BiTGApps will update boot image SPL at the time of installation.

## Boot Conflicts

Failure of patched keystore can cause bootloop.

## Installation Conflicts

Installation of safetynet patch entirely depends on boot image editing. For any reason, BiTGApps installer failed to extract/unpack/edit boot image, safetynet patch will not be installed.
No changes will made in **system/vendor** regarding safetynet patch.

## Restore Conflicts

OTA survival script can't restore safetynet patch. The way function executes will override the modified boot image.

Below is an example of function from updater-script:

* `run_program("backuptool.sh", "restore", "/dev/block/system", "ext4");`

* `package_extract_file("boot.img", "/dev/block/boot");`

Restore function from OTA script triggers before installation of stock boot image. So anything done at **restore stage** will be override by next function.

if we switch functions (Should be implemented in ROM):

* `package_extract_file("boot.img", "/dev/block/boot");`

* `run_program("backuptool.sh", "restore", "/dev/block/system", "ext4");`

Then we will able to restore full safetynet patch. Since this type of functionality is not available, you will need to re-install BiTGApps after installing OTA update.

_**Note:** This is the only exception with safetynet patch and does not affect rest of the OTA survival script functionality. OTA survival script can restore anything but not full safetynet patch._
