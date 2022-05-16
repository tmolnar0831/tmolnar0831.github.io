Title: How to upgrade to Debian Bullseye from Buster in WSL
Date: 2022-05-13
Modified: 2022-05-13
Category: Linux
Tags: linux, wsl, howto, upgrade
Slug: upgrade-debian-in-wsl
Author: Tamas Molnar

If we installed a Debian WSL distro on our system, and in the mean time a new version is released, it is possible to upgrade.

The distribution upgrade happens almost the same way as on other virtual and physical platforms.

I upgrade my WSL distros while I write this post: the current Debian oldstable is 10.12 (buster),
and I am going to upgrade to 11.03 (bullseye).

My approach is the following:
```
prepare -> backup -> upgrade -> clean up -> checks
```

# Preparation

Before we start, check the current Debian version to make sure on which version should we upgrade:
```
$ cat /etc/debian_version 
10.12
```

On the [releases page](https://www.debian.org/releases/) of the Debian homepage we can double-check the release names and version numbers.
```
Debian 10 == buster
Debian 11 == bullseye
```

Now we know that we want to upgrade from 10 to 11. Let's read the [release notes](https://www.debian.org/releases/stable/amd64/release-notes/index.en.html) and make sure we understand the consequences of the upgrade!

# Backup

Taking a backup of a WSL distro is realatively easy: we export the distro to a tar archive.

Terminate the WSL distro and take a backup of it as I show it in my [video post](https://youtu.be/dx2WoQo8hho) on YouTube.

In case of emergency we can simply import back the the current state of the machine with its files and stuff.

# The upgrade

The actual Debian distribution upgrade happens as the upgrade documentation states it.
In the first phase the minimal system is being changed, then in the second phase the full upgrade happens.

Let's make sure we start with the latest Debian 10 version!

Update the current Debian buster version with the latest patches:
```
sudo apt update -y && sudo apt full-upgrade -y
```

Remove the unnecessary packages:
```
sudo apt autoremove
```

At this point we have a **clean state** of the **freshest** Debian Buster, so we are ready to change the package repository configuration, and point it to the new release.
```
sudo sed -i 's/buster/bullseye/g' /etc/apt/sources.list
```

The bullseye security repo follows a different convention than the buster repo did.
Find the following line in the `/etc/apt/sources.list` file:
```
deb http://security.debian.org/debian-security bullseye/updates main
```
And change it to:
```
deb http://security.debian.org/debian-security bullseye-security main
```

Thus the `/etc/apt/sources.list` file should look something like this:
```
deb http://deb.debian.org/debian bullseye main
deb http://deb.debian.org/debian bullseye-updates main
deb http://security.debian.org/debian-security bullseye-security main
deb http://ftp.debian.org/debian bullseye-backports main
```

Let's update the package repository cache!
```
$ sudo apt update
Hit:1 http://ftp.debian.org/debian bullseye-backports InRelease
Hit:2 http://deb.debian.org/debian bullseye InRelease
Hit:3 http://security.debian.org/debian-security bullseye-security InRelease
Hit:4 http://deb.debian.org/debian bullseye-updates InRelease
Reading package lists... Done
Building dependency tree
Reading state information... Done
396 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

If everything is fine and the command ran without any error then the upgrade should happen in two phases:
1. Minimal upgrade
1. Full upgrade

## Minimal upgrade

Upgrade the base system with the bullseye packages:
```
sudo apt upgrade --without-new-pkgs
```

If the upgrade ran without any errors, then let's clean up the unnecessary packages:
```
sudo apt autoremove
```

## Full upgrade

The full upgrade happens with the following command:
```
sudo apt full-upgrade
```

Again if everything ran without any issue, let's clean up the packages again:
```
sudo apt autoremove
```

The distribution upgrade is done at this point, checks and monitoring can be done depending on the function of the system.

# Post checks

Let's see if the upgrade was successful and we have Debian 11:
```
$ cat /etc/debian_version
11.3
```

The further checks depend on the system's function.