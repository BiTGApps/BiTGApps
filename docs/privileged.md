# Privileged Permissions Patch

Privileged apps are system apps that are located in a `priv-app` directory on one of the system image partitions. The partitions used for Android releases are

* Android 8.1 and lower - /system

* Android 9 and higher - /system, /product, /vendor

Starting in Android 8.0, manufacturers must explicitly grant privileged permissions in the system configuration XML files in the `etc/permissions` directory.
As of Android 9, implementors must explicitly grant or deny all privileged permissions or the device won’t boot.

## Installation

BiTGApps disable privileged permissions allowlisting functionality itself during installation.

## System-As-Root

The root file system is no longer included in ramdisk image and is instead merged into system image.
Kernel default property that resides in **system/etc** will be patched.

## A-only

Non-A/B devices that does not follow system-as-root scheme, boot image will be patched.

## Boot Conflicts

All violations must be addressed by adding the missing permissions to the appropriate allowlists. Violations (of privileged permissions) mean the device doesn’t boot.
By disabling privileged permissions allowlisting functionality, device will boot even if required permissions are missing.

## Restore Conflicts

OTA survival script can't restore privileged permissions patch. The way function executes will override the modified boot image.

Below is an example of function from updater-script:

* `run_program("backuptool.sh", "restore", "/dev/block/system", "ext4");`

* `package_extract_file("boot.img", "/dev/block/boot");`

Restore function from OTA script triggers before installation of stock boot image. So anything done at **restore stage** will be override by next function.

if we switch functions (Should be implemented in ROM):

* `package_extract_file("boot.img", "/dev/block/boot");`

* `run_program("backuptool.sh", "restore", "/dev/block/system", "ext4");`

Then we will able to restore full privileged permissions patch. Since this type of functionality is not available, Non-AB devices need to re-install BiTGApps after installing OTA update.

_**Note:** This is the only exception with Non-AB devices. SAR/AB/Dynamic Partition devices has no effect. Also it does not affect rest of the OTA survival script functionality. OTA survival script can restore anything but not full  privileged permissions patch for Non-AB devices._

_**Exception:** Non-AB devices may have build property for enforcing privileged permissions in boot image._
