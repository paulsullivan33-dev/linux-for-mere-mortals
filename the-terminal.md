# The Terminal

The terminal is the black window where you type commands. People who
could use a mouse choose the terminal because typing is *precise*:
one command can rename 500 files, and you can save that command and
run it again tomorrow.

## The pieces

| Piece | What it is |
|-------|-----------|
| Terminal (emulator) | The window itself — it just displays text and sends your keystrokes |
| Shell | The program inside the window that reads your commands (usually **bash**) |
| Prompt | The bit of text waiting for input, like `paul@laptop:~$` |

Don't confuse the terminal with the shell. The terminal is the
window; the shell is the conversation partner. You can swap shells
without changing terminals.

## Reading the prompt

```text
paul@laptop:~$
```

- `paul` — who you're logged in as
- `laptop` — which machine this is
- `~` — where you are right now (`~` means your home directory)
- `$` — "I'm ready for a command" (a `#` here means you're root —
  the superuser — be extra careful)

## Your first commands

Type these exactly, pressing Enter after each:

```bash
whoami
```

**Check:** It prints your username — the same name as the start of
your prompt.

```bash
pwd
```

`pwd` = "print working directory." It answers "where am I?"

**Check:** It prints something like `/home/paul`. That's your home
directory — your personal space on the machine.

```bash
date
```

**Check:** It prints the current date and time. Congratulations, you
just asked the computer a question and got an answer.

## When a command runs long

- `Ctrl+C` — stop the current command (the universal "never mind")
- `Ctrl+D` — close the terminal / log out (sends "end of input")
- Up arrow — bring back the last command so you can edit and re-run it

Memorize `Ctrl+C` now. You'll need it exactly when you're flustered,
which is when you're least likely to remember something you only
read once.

## Case matters

`Documents` and `documents` are different things. Linux filenames are
case-sensitive, unlike Windows. `LS` is not a command; `ls` is.

**Next:** [Files and Directories](files-and-directories.md)
