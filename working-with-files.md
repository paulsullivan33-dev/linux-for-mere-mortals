# Working with Files

## Reading files

```bash
cat notes.txt          # print the whole file (fine for small files)
less notes.txt         # page through a big file (arrows/space to move, q to quit)
head notes.txt         # first 10 lines
head -n 3 notes.txt    # first 3 lines
tail notes.txt         # last 10 lines
tail -n 3 notes.txt    # last 3 lines
tail -f /var/log/syslog  # follow a file as it grows (Ctrl+C to stop)
```

`cat` on a 10,000-line log file will blast it all past your screen —
that's what `less` is for. `tail -f` ("follow") is how you watch a
log file live while something happens.

```bash
wc notes.txt           # word count: lines, words, bytes
```

**Check:** On a file containing `hello linux`, `wc` prints
`1  2 12` — 1 line, 2 words, 12 bytes (the newline counts as a byte).

## Editing files

The terminal's classic editor is **nano** — it shows its commands at
the bottom (`^X` means Ctrl+X). It's simple and always available:

```bash
nano notes.txt
```

Edit, then `Ctrl+O` to save, `Ctrl+X` to exit. (You'll meet `vim`
eventually — it has a learning cliff, not a curve. Nano first.)

On a desktop Linux, you can also use the graphical editor. No shame
in it.

## Redirection: files from commands

These two symbols are worth more than they look:

```bash
echo "hello" > greeting.txt     # > writes output INTO a file (overwrites!)
echo "again" >> greeting.txt     # >> APPENDS to a file
cat < greeting.txt               # < feeds a file in as input
```

**Careful:** `>` overwrites silently. `echo oops > notes.txt`
replaces your file with "oops" — no warning, no undo. When in doubt,
use `>>` (append), or back the file up first with `cp`.

## Wildcards

```bash
ls *.txt        # every file ending in .txt
ls photo-*.jpg # photo-1.jpg, photo-2.jpg, ...
ls ?.txt       # a.txt, b.txt — ? matches exactly one character
```

The *shell* expands wildcards before the command runs — `ls` never
sees the `*`, it sees the list of matching files. If nothing matches,
the pattern is passed through literally, which confuses beginners:
`ls *.xyz` with no matches tries to list a file literally named
`*.xyz`.

## Compressing and archiving

```bash
tar -czf backup.tar.gz projects/   # pack projects/ into backup.tar.gz
tar -tzf backup.tar.gz              # list what's inside (without unpacking)
tar -xzf backup.tar.gz              # unpack it
```

`tar` packs many files into one (originally for **t**ape **ar**chives);
the `z` adds gzip compression. You'll mostly *unpack* other people's
tarballs — `-tzf` to peek first is a good habit, so nothing sprays
files across your current directory unexpectedly.

**Next:** [Permissions](permissions.md)
