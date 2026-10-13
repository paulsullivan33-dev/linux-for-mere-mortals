# Finding Things

## Finding files

```bash
find . -name "*.txt"            # files ending .txt, here and below
find /etc -name "*.conf"        # ...under /etc (may show "Permission denied" — normal)
find ~ -name "notes*" -type f   # files (not dirs) starting with "notes" in home
```

`find` walks the tree for real. It's thorough and slow on huge
trees. For "where is this program," there's a faster tool:

```bash
which python3     # where is the python3 program?
```

**Check:** `which ls` prints `/usr/bin/ls` — the actual file that
runs when you type `ls`.

## Searching inside files

```bash
grep "error" app.log            # lines containing "error"
grep -r "hello" .               # -r: search every file under here
grep -i "error" app.log         # -i: ignore case
grep -n "error" app.log         # -n: show line numbers
```

`grep` is the single most useful text tool on Linux. Learn it before
anything fancy.

**Check:** `echo "hello linux" > t.txt && grep "hello" t.txt`
prints the matching line.

## Asking for help

Three levels, in order:

```bash
ls --help        # quick summary of options (works for most commands)
man ls           # the full manual (arrows to scroll, q to quit)
```

`man` pages are complete but dense — written as reference, not
tutorials. Read `--help` first; graduate to `man` when you need the
full story. (The name is short for "manual," and yes, the joke about
needing a manual for the manual is older than you.)

Not every command has `--help` spelled the same way (`-h`, `-?`),
but most do.

## A note on "Permission denied" from find

Searching under `/etc` or `/` will print `Permission denied` for
directories you can't read. That's not an error in *your* command —
it means those files aren't yours to see. Add `2>/dev/null` to hide
the noise:

```bash
find / -name "myfile.txt" 2>/dev/null
```

(The `2>` sends error messages elsewhere; `/dev/null` is the void.
More in [Bash for Mere
Mortals](https://paulsullivan33-dev.github.io/bash-for-mere-mortals/).)

**Next:** [Processes](processes.md)
