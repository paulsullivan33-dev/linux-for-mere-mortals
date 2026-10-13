# Files and Directories

Everything lives in one big tree. There are no drive letters — no
`C:` — just `/` (the *root*) at the top, with everything else below
it.

## The lay of the land

| Directory | What's in it |
|-----------|--------------|
| `/` | The root — the very top |
| `/home/paul` | Your personal files (your *home directory*) |
| `/etc` | System configuration files |
| `/var` | Files that change a lot (logs, mail) |
| `/tmp` | Scratch space — may be wiped on reboot |
| `/usr` | Programs and their supporting files |
| `/bin`, `/sbin` | Essential programs (often links into `/usr` now) |

You mostly live in `/home/paul`. The rest you visit, carefully.

## Moving around

```bash
pwd        # where am I?
ls         # what's here?
cd Documents   # go into Documents (relative to here)
cd /etc        # go to /etc (absolute — starts from the root)
cd ~           # go home (~ is shorthand for your home directory)
cd ..          # go up one level
cd -           # go back to where you just were
```

**Check:** After `cd ~`, `pwd` prints `/home/<your-username>`.

### Absolute vs. relative paths

- `/etc/hosts` — **absolute**: starts at the root, works from anywhere.
- `Documents/notes.txt` — **relative**: starts from where you are now.

If a path starts with `/`, it's absolute. Otherwise it's relative.
Mixing these up is the #1 cause of "file not found."

### Shortcuts worth knowing

| Shortcut | Meaning |
|----------|---------|
| `~` | Your home directory |
| `.` | The current directory |
| `..` | The parent directory |
| `-` | The previous directory (with `cd`) |

## Seeing what's there

```bash
ls          # names, in columns
ls -l       # long format: permissions, owner, size, date
ls -la      # long format including hidden files (names starting with .)
ls -lh      # human-readable sizes (4.0K instead of 4096)
```

Hidden files start with a dot (`.bashrc`, `.config`). They're hidden
from plain `ls` to reduce clutter, not for security — `ls -a` shows
them. Your shell's configuration lives in these.

## Making and removing

```bash
mkdir projects        # make a directory
mkdir -p a/b/c        # make nested directories all at once
touch notes.txt       # create an empty file (or update its timestamp)
rm notes.txt          # delete a file
rmdir projects        # delete an EMPTY directory
rm -r projects        # delete a directory AND everything in it
```

**Careful:** `rm` does not have an undo. Deleted files don't go to a
trash can — they're gone. And `rm -r` on the wrong directory is the
classic disaster. Two rules:

1. Never type `rm -rf` with a path you haven't double-checked.
   (The `-f` means "don't ask me, just do it.")
2. Never run `rm -rf /` or `rm -rf ~` — the first tries to delete the
   whole system, the second your entire home directory. Modern `rm`
   refuses `/` without extra flags, but don't rely on that.

**Check:** After `mkdir testdir && ls`, you see `testdir` in the
listing. After `rmdir testdir`, it's gone.

## Copying and moving

```bash
cp notes.txt notes-backup.txt      # copy a file
cp -r projects projects-backup     # copy a directory (-r = recursive)
mv notes.txt Documents/            # move a file into Documents/
mv old.txt new.txt                 # rename a file (move within a folder)
```

`mv` is both "move" and "rename" — renaming is just moving to a new
name in the same place. There is no separate rename command.

**Next:** [Working with Files](working-with-files.md)
