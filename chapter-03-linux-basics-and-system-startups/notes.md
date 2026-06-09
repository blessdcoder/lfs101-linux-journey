# Chapter 03: Linux Basics and System Startup
> Course: LFS101 — Introduction to Linux | Linux Foundation
> Date completed: June 2026

---

## What This Chapter Is About

This chapter explains what happens when you turn on a Linux computer. 
It also covers how the Linux filesystem is laid out and how Linux 
gets installed on a machine.

---

## The Boot Process

When you press the power button something called the boot process 
starts. It is a sequence of steps that happen one after another 
before you see the login screen.

Here is how it goes:

**BIOS or UEFI**
The first thing that runs when you power on is either BIOS or UEFI. 
This is built into the motherboard. It checks that the hardware is 
working and then looks for something to boot from.

BIOS is the older version. UEFI is the newer one. Most modern 
computers use UEFI.

**MBR**
Once BIOS or UEFI finds the hard drive it looks at a small section 
at the very start of the disk called the Master Boot Record. This 
points to the next step.

**Boot Loader — GRUB**
GRUB is the program that loads Linux. If you have ever seen a menu 
appear when starting a Linux machine asking which system to boot — 
that is GRUB. It loads the Linux kernel into memory.

**The Kernel**
The kernel is the core of Linux. After GRUB loads it, the kernel 
sets up the hardware and mounts the filesystem so the system can 
start reading files.

**Initial RAM Disk — initramfs**
This is a small temporary filesystem that helps the kernel get fully 
set up before the real system takes over.

**init and systemd**
After the kernel is ready it starts the very first process on the 
system. On modern Linux this is called systemd. It becomes process 
number 1 and is responsible for starting all the other services 
the system needs to run.

**Login Prompt**
After everything is started you finally see the login screen.

The full sequence looks like this: Power On → BIOS/UEFI → MBR → GRUB → Kernel → initramfs → systemd → Login

---

## The Linux Filesystem

The Linux filesystem is different from Windows. On Windows you have 
drives like C:\ and D:\. On Linux everything lives under one single 
starting point called root, written as `/`.

Here are the main folders and what they are used for:

| Folder | What It Is For |
|--------|---------------|
| `/` | Root — the top of the whole filesystem |
| `/home` | Where each user's personal files are kept |
| `/etc` | System and application config files |
| `/var` | Files that change regularly like logs |
| `/bin` | Basic commands that all users can run |
| `/sbin` | Commands used for system administration |
| `/tmp` | Temporary files that get cleared on reboot |
| `/boot` | The kernel and bootloader files |
| `/dev` | Device files for hardware like hard drives |

---

## Installing Linux

Linux can be installed in a few different ways:
- Directly on your computer (called bare metal)
- Inside a virtual machine
- On a cloud server

My setup is a virtual machine using VMware Workstation Pro with 
Ubuntu 24.04 LTS.

The basic installation steps are: choose your language, set up 
your disk, create a user account, and reboot.

---

## What I Found Interesting

I never thought about what happens between pressing power and seeing 
the screen. Now I know there are actually 7 steps happening and each 
one is a separate program passing control to the next. That is 
actually a smart way to build a system.

The filesystem being one tree starting at `/` also makes more sense 
to me now. Everything has a clear place.

---

## What Confused Me

I kept mixing up BIOS and UEFI. The simple version is:
BIOS is old, UEFI is new. Most computers today use UEFI.

I also did not fully understand what initramfs was at first. 
The way I think about it now is that it is a temporary helper 
that loads just enough for the kernel to get going before 
handing over to the real system.

---

## Chapter Complete: ✅ Yes
