# Processes

A **process** is a running program. Your terminal is a process, the
thing you launched from it is a process, and there are a hundred you
didn't start. Linux gives each one a number — the **PID** (process
ID) — and lets you inspect and stop them.

## Seeing what's running

```bash
ps                # your processes in this terminal
ps aux            # EVERYTHING running (a = all users, u = details, x = no terminal)
top               # live updating table (q to quit)
htop              # top, but friendlier (may need installing)
```

**Check:** `ps aux | head -5` shows a header plus a few processes,
with columns like `USER`, `PID`, `%CPU`, `%MEM`, `COMMAND`.

Reading `ps aux` output:

```text
USER   PID %CPU %MEM COMMAND
root     1  0.0  0.1 /sbin/init
```

- `PID 1` is special: it's the first process the kernel starts
  (usually `systemd`), and everything else descends from it.
- `%CPU`/`%MEM` tell you who's hogging the machine — your first stop
  when the computer feels slow.

## Foreground and background

When you run a command, the terminal waits — that's the
**foreground**. You can also launch things into the **background**:

```bash
sleep 300 &        # & = run in background; terminal stays usable
jobs               # list your background jobs
fg                 # bring the job back to the foreground
```

Most of the time you'll just open another terminal instead. But
`&` is handy for launching something quick without losing your
prompt.

## Stopping a process

Escalation order — start gentle:

```bash
kill 1234        # ask PID 1234 to stop politely (it can clean up)
kill -9 1234     # force it dead NOW (no cleanup — data loss possible)
pkill firefox    # kill by name instead of PID
```

`kill` without a signal sends TERM ("please stop"). `-9` sends KILL
("stop whether you like it or not"). The polite version lets the
program save its work; `-9` doesn't. Reach for `-9` only when the
polite version fails.

**Careful:** `kill -9 1` would try to kill the init process — don't.
And double-check PIDs before killing; there's no undo.

## A frozen graphical program

If a GUI app freezes, you don't need to reboot. Find it and kill it:

```bash
ps aux | grep firefox
kill <the-PID>
```

Or open a terminal and run `xkill`, then click the frozen window.
(Your desktop environment may vary; the `kill` approach always
works.)

**Next:** [Installing Software](installing-software.md)
