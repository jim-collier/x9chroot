# x9chroot

## Purpose

Creates and/or enters a bare-bones chroot environment, mainly intended for testing development projects.

It has no third-party libraries or applciations installed, and only a subset of standard GNU/POSIX utilities for basic functionality.

Once created, the environment can be deliberately or accidentally trashed, without harming the real OS.

The script could conceivably be modified without too much effort to facilitate secure jails, but as it is now that's not the point.

## Why

There are surprisingly few (to no) tools that do this - this directly and simply.

LXD or Docker containers, for example, are too heavy and full-featured for this purpose.

Likewise, a virtual machine with a common Linux distro can't actually be created, practically speaking, this bare-bones.

It is also somewhat suprising how difficult it is, to chroot into a chroot environment and arrive as your own unprivleged user. (Answers can be found, but most don't work - at least on Ubuntu 18.04.*.)

## Usage

| Command | Description |
|:--- |:--- |
| `x9chroot` | Displays help. |
| `x9chroot create [file1\|dir1 to copy to ~] ... [file8\|dir8 to copy to ~]` | [Re-]creates and enters the chroot as current user. |
| `x9chroot enter  [file1\|dir1 to copy to ~] ... [file8\|dir8 to copy to ~]` | Enters previously created chroot as current user. |

## Known limitations

- Written and tested only on Ubuntu 18.04. (It should work on older and newer versions though, as well as other distros. The locations of important system binaries are not hard-coded.)
- The copy functionality (arguments 2 through 9) could be better. Either way, it's probably better, and generally easier, to:
  1. Create the environment (`x9chroot create`).
  1. Exit out of it, so that you can access both inside the chroot directory structure, *and* the broader filesystem outside of it (`exit`).
  1. Manually copy what you need and exactly where you need it in the chroot file structure, via graphical file manager (or, for example, midnight commander), which is located by default at `/var/x9chroot/`.
  1. Enter back into the chroot environment (`x9chroot enter`).
