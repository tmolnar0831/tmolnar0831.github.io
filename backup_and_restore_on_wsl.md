Title: How to backup and restore a distro on WSL
Date: 2022-05-02
Modified: 2022-05-02
Category: Windows
Tags: windows, wsl, howto
Slug: how-to-backup-and-restore-wsl
Authors: Tamas Molnar

Follow the process on my [YouTube video](https://youtu.be/dx2WoQo8hho)!

Backing up and restoring WSL distros is easier than anyone can think! It is simply an export of the stopped distro that can be moved on an external disk or share. Restoring a backup is importing the generated tar archive.

Moreover we can add **multiple instances** of the same distro with exporting then importing it. With this let's say we can have three different Debian WSL boxes.

To list our current distros use the following command:

```
wsl --list --verbose
```

It will have an output something like this:

```
  NAME          STATE           VERSION
* Debian        Running         2
  kali-linux    Stopped         2
```

To terminate a distro use the following command:

```
wsl --terminate kali-linux
```

The `kali-linux` is the distro name from the list command above!

# Backup a WSL distro

Backing up a WSL distro happens with the `--export` option of the `wsl` command:

```
wsl --export kali-linux D:\home_lab\Kali_WSL.tar
```

The command will create a tar archive at the defined place.

# Restore a WSL distro

Restoring an image happens with the `--import` option.

```
wsl --import kali-linux-restored D:\home_lab\ D:\home_lab\Kali_WSL.tar
```

The command will restore the saved state of our WSL distro.