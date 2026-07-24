### PBRP device tree for moto g24/g24 power (fogorow)

=========================================

The moto g24 (codenamed _"fogorow"_) is a low-range / mid-range smartphone from Motorola.

It was released in February 6, 2024.

## Device specifications

Basic   		| Spec Sheet
-----------------------:|:-------------------------
CPU     		| Octa-core (2× ARM Cortex-A75 @ 2.0 GHz + 6× ARM Cortex-A55 @ 1.8 GHz)
Chipset 		| MediaTek Helio G85 (MT6769Z)
GPU     		| ARM Mali-G52 MC2 (MP2)
Memory  		| 8/4 GB RAM
Shipped Android Version | 14
Storage 		| 128 GB / 256 GB eMMC 5.1
Battery 		| 5000 mAh / 6000 mAh
Display 		| 720 × 1612 pixels, 6.56 IPS LCD, 90 hz

## Features

Works:

- [X] ADB
- [X] Decryption
- [X] Display
- [X] Fasbootd
- [X] Flashing
- [X] MTP
- [X] Sideload
- [X] USB OTG

Not implemented:

- Vibrator
- Flashlight

## Compile

First checkout minimal twrp with aosp tree:

```
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
repo sync -j$(nproc --all)
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/motorola/fogorow" name="fuckyoumotorola/recovery_android_device_motorola_fogorow-PBRP" remote="github" revision="android-12.1" />
```

Finally execute these:

```
source build/envsetup.sh
repopick <needed patch>
breakfast fogorow
mka vendorbootimage -j$(nproc --all)
```
## To use it:

```
fastboot flash vendor_boot out/target/product/fogorow/vendor_boot.img
```
