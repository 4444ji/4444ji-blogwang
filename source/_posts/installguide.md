---
title: install guide(WIP)
date: 2026-06-13 19:00:00
tags: guide WIP
---

# **install guide**

welcome! o7 this install guide tells you how to install marlinux 

## You **need** to know what's required for some computer hardware.

- Memory : 4GB

- CPU X86_64 arch @ 500+

- Disk size 8GB+

## 1. enter the LiveCD
Download the LiveCD iso file and use the tools to enter the marlinux LiveCD

## 2. Boot into LiveCD 

Use usb device plug in your computer and press F12
choose your usb device and enter the marlinux LiveCD

## 3.partition the disk

run `lsblk` to check your disk(e.g. /dev/sda /dev/nvme0nx)

Run `cfdisk /dev/xxx`(replace xxx to real disk name)

**Double-check with lsblk and blkid before formatting. All data on selected partitions will be erased.**

create EFI partition Recommend size:**800M**

create Linux filesystem and press Write

then run one of these **commands** to format **WARNING! MAKE SURE YOU KNOW WHAT ARE YOU DO!!!!**

- `mkfs.fat -F32 /dev/xxx1`(replace xxx1 to real partition) this is to format the partition to EFI

- `mkfs.ext4 /dev/xxx2`(replace xxx2 to real partition) this is to format the partition to ext4 

- `mkfs.btrfs /dev/xxx2`(replace xxx2 to real partition) this is to format the partition to btrfs

btrfs follow this step:

- 1. **`mount /dev/xxx2 /mnt`**(**replace xxx2 to real partition**)

- 2. **`btrfs subvolume create /mnt/@`**

- 3. **`btrfs subvolume create /mnt/@home`**

- 4. **`umount /mnt`** 

- 5. **`mount -t btrfs -o compress=zstd,subvol=@ /dev/xxx2`** (**replace xxx2 to real partition**)

