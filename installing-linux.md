# Installing Linux (safely)

You need a Linux to practice on. You do **not** need to wipe your
computer. Here are your options, safest first.

## Option 1: Windows Subsystem for Linux (Windows only)

If you're on Windows 10 or 11, this is the easiest path. WSL runs a
real Linux (usually Ubuntu) inside Windows — no rebooting, no risk to
your files.

```powershell
wsl --install
```

(Reboot when it asks, then open "Ubuntu" from the Start menu.)

**Check:** Inside the Ubuntu window, run `uname -s` — you should see
`Linux`.

**Limits:** It's real Linux, but it's a guest inside Windows. Hardware
access (like USB devices) is limited, and it's slower at some disk
operations. Fine for learning; not identical to a dedicated machine.

## Option 2: A virtual machine

VirtualBox (free) or similar lets you run Linux in a window on
Windows or Mac. Download an Ubuntu or Mint ISO, create a new VM, point
it at the ISO, and install. Your real system is untouched — the worst
case is deleting the VM and starting over.

**Good for:** trying the full desktop experience safely.

## Option 3: A Raspberry Pi or old computer

A Raspberry Pi (Raspberry Pi OS is Linux) or any old laptop makes a
great always-on practice box. This is also how home servers start.

**Good for:** learning the "remote machine" chapter for real, since
you'll SSH into it.

## Option 4: Dual boot / replace your OS

Installing Linux as your main OS. Totally viable — millions do it —
but back up first, and don't start here. Learn on a safe option,
*then* decide.

## What this guide assumes

From here on, you have a terminal open on a Debian-family Linux
(Ubuntu, Mint, Debian, Raspberry Pi OS). Commands that differ on
Fedora/Arch are noted where it matters.

**Next:** [The Terminal](the-terminal.md)
