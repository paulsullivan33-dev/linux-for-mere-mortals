# Disks and Services

## Where did my space go?

Two commands answer 90% of disk questions:

```bash
df -h        # how full is each filesystem? (-h = human-readable)
du -sh *      # how big is each thing HERE? (-s = summary)
```

**Check:** `df -h /` shows a line with the size, used space, and a
`Use%` column for your root filesystem.

When a disk fills up, drill down: `du -sh *` in the suspect
directory, `cd` into the biggest one, repeat. The culprit is usually
a log file that grew forever or a forgotten download folder.

```bash
du -sh ~/.cache/* | sort -h | tail -5   # five biggest things in your cache
```

### Mounting

Linux doesn't have drive letters. Extra disks get **mounted** —
attached at some directory:

```bash
lsblk                  # list block devices (disks and partitions)
mount | grep /myData   # where is /myData mounted?
```

You'll mostly encounter mounting when adding a USB drive or a second
disk. The details (fstab entries, mount options) can wait — know that
"a disk appears at a directory" is the model, and `lsblk` shows you
the disks.

## Services: what starts at boot

A **service** (or *daemon*) is a program that runs in the background
providing something — networking, printing, a web server. On modern
Linux, **`systemd`** manages them, and **`systemctl`** is how you
talk to systemd:

```bash
systemctl status ssh          # is the SSH service running?
sudo systemctl start ssh      # start it now
sudo systemctl stop ssh       # stop it now
sudo systemctl restart ssh    # stop, then start (the classic fix)
sudo systemctl enable ssh     # start it automatically at boot
sudo systemctl disable ssh    # don't start it at boot
```

**start vs. enable** trips everyone up: `start` affects *right now*;
`enable` affects *next boot*. You usually want both when setting
something up permanently.

**Check:** `systemctl is-active ssh` prints `active` or `inactive`.

### Reading logs

When a service misbehaves, its logs are the first place to look:

```bash
journalctl -u ssh --since "1 hour ago"   # this service's recent logs
journalctl -f                            # follow the whole log live (Ctrl+C to stop)
dmesg | tail -20                         # kernel messages (hardware, drivers)
```

`journalctl` is systemd's log viewer. Most "why won't this start"
mysteries end here.

**Next:** [Troubleshooting](troubleshooting.md)
