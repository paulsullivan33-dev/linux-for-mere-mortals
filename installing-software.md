# Installing Software

On Linux you don't hunt down installer executables on websites. You
ask the **package manager**, which fetches software from curated
repositories, checks it's genuine, and handles updates for
everything at once. It's the app store that came before app stores —
and unlike app stores, it's not a walled garden.

## The main package managers

| Distro family | Command | Example |
|---------------|---------|---------|
| Debian/Ubuntu/Mint | `apt` | `sudo apt install htop` |
| Fedora/RHEL | `dnf` | `sudo dnf install htop` |
| Arch | `pacman` | `sudo pacman -S htop` |

This guide uses `apt` (Ubuntu/Mint/Debian/Raspberry Pi OS). The ideas
are identical elsewhere; only the command name changes.

## The daily workflow

```bash
sudo apt update            # refresh the LIST of available software
sudo apt upgrade           # install newer versions of what you have
sudo apt install htop      # install a package
sudo apt remove htop       # remove it (keeps its settings)
sudo apt search "editor"   # search for packages
```

**`update` vs. `upgrade` confuses everyone:** `update` downloads the
*catalog* ("here's what's available now"); `upgrade` installs the
newer *versions*. You almost always run `update` first, then
`upgrade`. Think: check the menu, then order.

**Check:** `sudo apt update` ends with lines like `Reading package
lists... Done` and no error lines. (It needs `sudo` because it writes
system files.)

## What "repository" means

A repository is a server full of packages that your distro's
maintainers have vetted. When you `apt install` something, it comes
from there — which is why Linux users worry less about malware than
people downloading random `.exe` files. The trade-off: versions can
lag behind the developer's website.

## Beyond apt: flatpak and snap

Some apps come as **flatpak** or **snap** packages — self-contained
bundles that work across distros and update independently:

```bash
flatpak install flathub org.gimp.GIMP   # example
snap install vlc                        # example
```

These are newer, bigger, and slightly controversial among purists.
For a beginner, the practical advice is simple: use `apt` first; if
the app you want isn't there or is ancient, try flatpak/snap.

## What not to do

- Don't `curl <url> | sudo bash` unless you trust the source and
  understand the script — you're running a stranger's code as root.
- Don't add random third-party repositories (PPAs) casually. Each
  one is a new stranger you're trusting with system software.
- Don't download `.deb` files from forums when `apt` has the package.
  The repository version is vetted; the forum file is not.

**Next:** [Remote Machines](remote-machines.md)
