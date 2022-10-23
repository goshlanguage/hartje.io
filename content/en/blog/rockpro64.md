---
title: "Rockpro64"
date: 2022-05-01T14:48:54-05:00
draft: true
---

![Rockpro64](https://wiki.pine64.org/images/e/ec/ROCKPro64_annotated.jpg)

# Resources

|Name|Description|
|-|-|
|[Pine64 Wiki - Rockpro64](https://wiki.pine64.org/index.php/ROCKPro64)|The official pine64 wiki|
|[Pine64 Wiki - Rockpro64 Software Release](https://wiki.pine64.org/wiki/ROCKPro64_Software_Release)|Blessed Operating Systems|
|[Pine64 Forums](https://forum.pine64.org/forumdisplay.php?fid=98)|pine64 rockpro64 forum|
|[Pine64 Reddit](https://www.reddit.com/r/PINE64official/)|Official reddit sub|
|[Pi2 GPIO Pinout](https://www.jameco.com/Jameco/workshop/circuitnotes/raspberry_pi_circuit_note_fig2.jpg)|Diagram showing Raspi, but same pinout exists on the Rockpro64|
|[PXE Guide](https://forum.pine64.org/showthread.php?tid=6814)|PXE boot with U-boot|
|[U-Boot Guide](http://opensource.rock-chips.com/wiki_U-Boot)|For rockchip|
|[Ayufan U-Boot Releases](https://github.com/ayufan-rock64/linux-u-boot/releases/tag/2017.09-rockchip-ayufan-1065-g95f6152134)|For SPI flash images|
|[Ayufan Linux Releases](https://github.com/ayufan-rock64/linux-build/releases/tag/0.9.14)|For pine64 devices|
|[Rockchip Linux Kernel](https://github.com/rockchip-linux)||

# Provisioning

Flash [Ayufan linux](https://github.com/ayufan-rock64/linux-build/releases/latest) to an SD to write the SPI flash. On boot, run:

```sh
sudo ./rock64_write_spi_flash.sh
```

If for some reason something goes wrong, see:
https://github.com/ayufan-rock64/linux-build/blob/master/recipes/flash-spi.md#4-fix-for-spi-flashing-failures

Next, flash [Armbian](https://www.armbian.com/rockpro64/) to an SD card.

Next, setup user/pw, add user to ALL:NOPASSWD:

```sh
sudo visudo

# add this line replaced username with the system user of choice
username  ALL=(ALL) NOPASSWD:ALL

```

# Building images

> The best way to meet all these requirements is to take a standard Raspbian image, add u-boot.bin and u-boot.env (if any) to the FAT partition, add the "kernel=u-boot.bin" line in config.txt and see how it goes.

https://forums.raspberrypi.com/viewtopic.php?t=229445
