# Permissions

Every file has an owner, a group, and three sets of permissions. This
is Linux's security model, and it's simpler than it looks.

## Reading `ls -l`

```bash
ls -l notes.txt
```

```text
-rw-r--r-- 1 paul paul 12 Oct 12 22:57 notes.txt
```

Breaking down `-rw-r--r--`:

| Part | Meaning |
|------|---------|
| `-` | File type (`-` file, `d` directory, `l` link) |
| `rw-` | Owner (paul) can **r**ead and **w**rite |
| `r--` | Group (paul) can only **r**ead |
| `r--` | Everyone else can only **r**ead |

The `1 paul paul` after it: link count, owner, group. Then size,
date, name.

For a directory, `x` means "allowed to enter / list":

```text
drwxr-xr-x 2 paul paul 4096 Oct 12 22:57 docs
```

## Changing permissions

Permissions are also written as numbers — each of read/write/execute
is worth 4/2/1:

| Number | Letters | Meaning |
|--------|---------|---------|
| 7 | `rwx` | read + write + execute |
| 6 | `rw-` | read + write |
| 5 | `r-x` | read + execute |
| 4 | `r--` | read only |
| 0 | `---` | nothing |

```bash
chmod 600 notes.txt   # owner read/write, nobody else anything (private)
chmod 644 notes.txt   # owner read/write, everyone else read (normal file)
chmod 755 script.sh   # owner everything, everyone else read+execute (programs)
chmod +x script.sh    # add execute permission (same as the x in 755)
```

**Check:** `chmod 600 notes.txt && ls -l notes.txt` shows
`-rw-------` as the permission string.

**The 90% rule:** files are `644`, directories and programs are
`755`, secrets are `600`. If you learn nothing else, learn that.

## Changing ownership

```bash
chown paul:paul notes.txt   # change owner and group
chgrp staff notes.txt        # change just the group
```

You generally only need these when files were created by someone
(or something) else — like files unpacked as root.

## sudo: borrowing superpowers

Some things need the superuser (root): installing software, editing
system files, managing services. Instead of logging in as root
(dangerous — no guardrails), you borrow root's power for one command:

```bash
sudo apt update
```

`sudo` asks for *your* password (not root's), runs the one command as
root, then drops the power. It remembers for a few minutes, so you
won't be asked every time in a burst of admin work.

**Careful:** With `sudo`, the guardrails come off. `sudo rm -rf /`
would genuinely try to erase the system. Pause before every `sudo`
command and read it once more. If a tutorial tells you to
`curl something | sudo bash` (download a script and run it as root),
understand what the script does first — you're handing a stranger
the keys.

**Check:** `sudo whoami` prints `root` — proof you borrowed the
power — while plain `whoami` still prints your name.

**Next:** [Finding Things](finding-things.md)
