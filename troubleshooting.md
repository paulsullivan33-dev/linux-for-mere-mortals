# Troubleshooting

Linux problems feel cryptic until you learn the method. The method
is unglamorous: read the error, reproduce it, change one thing.

## Read the error message. All of it.

Beginners (everyone, at first) see an error and panic-scroll past
it. Don't. Error messages are written by programmers *for*
programmers, but they usually contain the answer:

```text
cp: cannot stat 'notes.txt': No such file or directory
```

Translation: `cp` tried to read `notes.txt`, and it doesn't exist
(here). The fix isn't mysterious — you're in the wrong directory, or
the name is misspelled. Check with `pwd` and `ls`.

Common translations:

| Error | Usually means |
|-------|---------------|
| `No such file or directory` | Wrong path, typo, or wrong current directory |
| `Permission denied` | You need `sudo`, or the file isn't yours |
| `command not found` | Typo, or the program isn't installed |
| `Is a directory` | You gave a directory where a file was expected (add `-r`) |
| `No space left on device` | Disk full — see [Disks and Services](disks-and-services.md) |

## The checklist

1. **What did you actually type?** Up-arrow and re-read it.
   Half of all errors are typos.
2. **Where are you?** `pwd`. Half of the other half is the wrong
   directory.
3. **What are the permissions?** `ls -l`. "Permission denied" is
   almost always this.
4. **What do the logs say?** `journalctl -u <service>`, `dmesg |
   tail`. (See [Disks and Services](disks-and-services.md).)
5. **Did it ever work?** What changed since? New updates, new
   config, new hardware — the culprit is usually the most recent
   change.

## Searching the web effectively

Copy the distinctive part of the error — not your username or paths:

```text
"cp: cannot stat" ubuntu        # good
"cp: cannot stat 'notes.txt'"   # too specific, fewer hits
```

Add your distro (`ubuntu`, `mint`, `debian`) to the query. Someone
has almost certainly hit your exact error; the answer is usually a
forum post from 2019 that's still correct.

## When to ask for help

Ask a person (or forum) when you've done the checklist and searched.
Include: what you typed, the *full* error, your distro and version
(`cat /etc/os-release`), and what you already tried. "It doesn't
work" gets shrugs; the full error gets answers.

## The nuclear options, ranked

1. `sudo systemctl restart <service>` — restarts one thing.
2. Reboot — fixes a surprising amount, clears stuck state.
3. Reinstall the package — `sudo apt install --reinstall <pkg>`.
4. Reinstall the OS — the final answer, and why backups and a
   separate `/home` exist. Rarely needed.

**Next:** [Glossary](glossary.md)
