# Remote Machines

One of Linux's superpowers: the terminal works the same whether the
computer is under your desk or across the planet. **SSH** (Secure
Shell) gives you an encrypted terminal on another machine.

## Logging in

```bash
ssh paul@192.168.1.50
```

This connects as user `paul` to the machine at `192.168.1.50`. You'll
be asked for paul's password *on that machine*, then your prompt
changes — you're typing on the remote computer now. `exit` (or
`Ctrl+D`) logs out and returns you home.

**Check:** After logging in, the prompt shows the remote machine's
name, and `pwd`/`whoami` answer for *that* machine.

The first connection asks you to confirm the host's fingerprint:

```text
The authenticity of host '192.168.1.50' can't be established.
Are you sure you want to continue connecting (yes/no)?
```

Type `yes`. SSH remembers the fingerprint; if it ever *changes*,
SSH warns you loudly — that can mean an attack, or just a
reinstalled machine. Don't ignore the warning; do verify which it
is before proceeding.

## Copying files

```bash
scp notes.txt paul@192.168.1.50:/home/paul/   # copy TO the remote
scp paul@192.168.1.50:/home/paul/notes.txt .   # copy FROM the remote
scp -r projects/ paul@192.168.1.50:~/          # -r for directories
```

`scp` reads like `cp`, but either side can be `user@host:path`.
Think of it as `cp` with a network.

## Passwordless login with keys

Typing passwords gets old, and passwords can be guessed. The better
way: a **key pair**. You keep the private key; the server gets the
public key.

```bash
ssh-keygen -t ed25519        # create a key pair (accept the defaults)
ssh-copy-id paul@192.168.1.50  # install your public key on the server
```

**Check:** `ssh paul@192.168.1.50` now logs you in without asking for
a password.

**Careful:** Your private key (`~/.ssh/id_ed25519`) *is* your
identity. Anyone holding it can log in as you everywhere it's
installed. Never email it, never paste it into a chat, never copy it
to a machine you don't trust. The public key (`id_ed25519.pub`) is
safe to share — that's the whole point of the pair.

## Users and groups (the 2-minute version)

```bash
whoami            # who am I here?
who               # who's logged in right now?
id                # my user id, group id, and all my groups
sudo usermod -aG sudo paul   # add paul to the sudo group (-aG = append!)
```

That last one deserves respect: `-aG` **appends** paul to the `sudo`
group. Without `-a`, `usermod -G sudo paul` *replaces* his groups —
locking him out of everything else. The `-a` is the difference
between "also" and "only."

**Next:** [Disks and Services](disks-and-services.md)
