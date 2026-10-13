# What Linux Is

**The one-sentence version:** Linux is a free operating system kernel,
and people build complete operating systems around it.

**The slightly longer version:** An operating system is the software
that sits between your programs and your hardware. It decides which
program gets the CPU next, where files live on disk, and how programs
talk to the network. The *kernel* is the core of that — the part with
the most power and the least forgiveness. Linux is a kernel. It was
written by Linus Torvalds starting in 1991, and thousands of people
have contributed since.

## Kernel vs. distribution

This distinction confuses everyone at first, so let's nail it:

| Term | What it is | Analogy |
|------|-----------|---------|
| Kernel | The core that manages hardware | An engine |
| Distribution ("distro") | Kernel + tools + desktop + installer, packaged together | A complete car |

When someone says "I run Ubuntu" or "I run Mint," they mean a
distribution. Ubuntu, Debian, Fedora, Mint, Arch, Raspberry Pi OS —
all different cars built around the same engine family.

**Which distro should you pick?** For learning: Ubuntu or Linux Mint.
They're the most documented, which means when you search an error
message, someone has already answered it. This guide uses Ubuntu
examples; nearly everything works on Mint and Debian too, since Mint
is based on Ubuntu and Ubuntu is based on Debian.

## Why Linux runs the world (and your phone)

- **It's free.** No license fees, so a company can run 10,000 servers
  without paying per machine.
- **It's open.** Anyone can read the source code. Bugs get found by
  thousands of eyes instead of one company's QA team.
- **It runs anywhere.** Supercomputers, routers, thermostats,
  phones — the same kernel family scales from a thermostat to a
  supercomputer.
- **It's scriptable.** Everything can be driven from the command
  line, which means everything can be automated. That's the rest of
  this guide.

## What Linux is not

- **Not a company.** Nobody "owns" Linux. Companies (Canonical,
  Red Hat) sell support and build distros around it.
- **Not one thing.** "Linux" on a phone looks nothing like "Linux"
  on a server. The ideas transfer; the furniture moves.
- **Not only for experts.** The reputation comes from the 1990s. A
  modern Mint desktop is as approachable as Windows for daily use —
  the command line underneath is a *choice*, and it's the choice this
  guide teaches.

## The big idea to carry forward

Linux treats **everything as a file** — or close enough that the
metaphor holds. Your hard drive, your keyboard, a running process:
all show up as entries you can list, read, and (carefully) write.
Once that clicks, the rest of the guide is just details.

---

**Check:** Run this to confirm you're on Linux:

```bash
uname -s
```

Expected output:

```text
Linux
```

`uname` asks the kernel its name. If it answers `Linux`, you're in
the right place. (On a Mac it says `Darwin`; the commands in this
guide mostly work there too, but package managers and system tools
differ.)

**Next:** [Installing Linux (safely)](installing-linux.md)
