Title: Installing Kali Linux on WSL
Date: 2022-05-11
Modified: 2022-05-11
Category: Linux
Tags: linux, wsl, windows, howto
Slug: installing-kali-on-wsl
Authors: Tamas Molnar

# Pre-install steps

* WSL must be installed on the host machine prior this task. Microsoft has an [extensive documentation](https://docs.microsoft.com/en-us/windows/wsl/install) on the topic.
* Basic WSL management skills are nice to have, like importing/exporting/removing WSL instances. Use `wsl --help` for reference.
* Read the [Kali documentation](https://www.kali.org/get-kali/#kali-wsl) about the topic as well.

# Kali WSL installation

Install the Kali WSL machine from the [Microsoft Store](https://apps.microsoft.com/store/detail/kali-linux/9PKR34TNCV07?hl=en-us&gl=US) and do NOT use the wsl.exe command for it. At the time of writing this document there is an error in the system when installing Kali with wsl.exe, and it installs and outdated version. Use the [Microsoft Store](https://apps.microsoft.com/store/detail/kali-linux/9PKR34TNCV07?hl=en-us&gl=US) instead.

After installing the Kali machine start it from the Start menu, let it install the necessary services and set up the user.

In the end of the initial setup update the system with the apt:

```
sudo apt update && sudo apt full-upgrade -y
```

Let the process finish the upgrade, then remove the unnecessary files:

```
sudo apt autoremove
```

# Win-KeX installation (Kali desktop on Windows WSL)

As Microsoft more and more integrates Linux in its operating system the usability is better day by day.
Win-KeX is giving a great Kali desktop environment on our Windows system.

Install the Win-KeX package:

```
sudo apt install -y kali-win-kex
```

Then if we have enough patience and space, then we can install the whole Kali linux toolset:

```
sudo apt install -y kali-linux-large
```

When the process stopped then we have all the tools we need for our Cyber Security learning journey.

# Starting Win-KeX from Kali

I use [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=en-us&gl=US) for its features and simplicity. 

After starting the Kali in terminal, KeX can be activated with the following command:

```
kex --esm --ip -s
```

Now we can use our usual Kali tools on Windows running a Kali WSL box.

More [documentation](https://www.kali.org/docs/wsl/win-kex/) about the possibilities.