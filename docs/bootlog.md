# Generating Boot Logs

You can generate logcat and dmesg log using BiTGApps itself. Boot log functionality is not enabled by default. For that you need **boot-config.prop** file.
When this config file not present in device, at the time of installation you will be notified with following texts.

```! Boot config not found```

```! Skip installing boot log patch```

This can be used, when you ended up in bootloop after installing BiTGApps for whatever reasons. Logcat and dmesg log can be found in cache partition.

* boot_lc_main.txt
* boot_dmesg.txt

## System-As-Root

The root file system is no longer included in ramdisk image and is instead merged into system image.
Kernel init.rc that resides in either **system root** or **system/etc/init/hw** will be patched.

## A-only

Non-A/B devices that does not follow system-as-root scheme, boot image will be patched and required script will be installed in ramdisk.

## Usage

When device bootlooping, reboot to recovery, place config file and re-install BiTGApps. After installing, reboot to system and let it bootlooping,
after few seconds device will reboot back to recovery itself. You can grab log files from cache partition.

## Installation Conflicts

Installation of boot log patch entirely depends on boot image editing. For any reason, BiTGApps installer failed to extract/unpack/edit boot image, boot log patch will not be installed.
No changes will made in **system** regarding boot log patch.

## SELinux Conflicts

Selinux with enforce status prevents execution of logcat script. Due to lack of required selinux denials.

To fix this issue, BiTGApps will patch kernel commandline and make it permissive.

## Launch Bootanim Early
If your ROM built with this [commit](https://github.com/sm6150-dev/android_device_xiaomi_sm6150-common/commit/d64878a85353175b3fe9a14effded9408abeb5a1), then it is more likely that
boot animation will trigger even if your device is completely broken, not in a state of generating boot logs. The boot log functionality will not work in this case.
It maybe caused by a broken ROM or kernel itself.
