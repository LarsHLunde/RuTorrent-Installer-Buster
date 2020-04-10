# RuTorrent-Installer-Buster v1.3.1 (Beta)

## Description
This is a RuTorrent installer for debian buster linux systems.
My original goal for the project was to make a RuTorrent installer
for the Raspberry Pi 3 running Raspbian-jessie-lite,
this fork is for debian and raspbian buster.

Due to a bug with the buster repo version of libcurl4,
where if you add more than 2000-3000 torrents to rtorrent,
rtorrent will segfault and die.

This version adds the testing repo to debian as the non-default,
and gets the libcurl4 version from there isntead of from buster.

## Systems
### Working and tested
* Debian Buster x64
* Armbian Buster (not stress tested)

## Dependecies
This script installer is made in Lua,
and as such Lua is required.
For people running Debian and Devuan please see notes
further down the page.

## Installment
In order to install RuTorrent on your pi
copy and paste every individual line in
to your console.
```
sudo apt-get update
sudo apt-get install -y lua5.2 git sox
git clone https://github.com/LarsHLunde/RuTorrent-Installer-Buster.git
cd RuTorrent-Installer-Buster
lua installer.lua
```

or just copy the monster line in to your terminal:
```
sudo apt-get update && sudo apt-get install -y lua5.2 git sox && git clone https://github.com/LarsHLunde/RuTorrent-Installer-Buster.git && cd RuTorrent-Installer-Buster && lua installer.lua
```

## Changelog
### Version 1
Initial working release
### Version 1.01
* Fixed ownership of rtorrent.rc file
* Re-added seedtime in config

### Version 1.1
* Made compatible with Ubuntu 16.04
* Lost comaptibility for Ubuntu 14.04

### Version 1.2
* Added support for repo installation

### Version 1.3
* Added a support script for the liteserver.nl VPSs
* Added support for Debian stretch
* Cleaned up a lot of dirty hacks
* Made it self destruct upon completion

### Version 1.3.1
* Changed low disk space limit for 10GB to 100MB in .rtorrent.rc

## Planned features

* Make dialog screens, which I need to learn how to use
* Make script safe to run multiple times without side effects
* Add support for nginx
* Maybe add support for lighttpd
* Add support for using the reposetory versions of xml-rpc, rtorrent and libtorrent

## Notes
I have made the not about the Debian and Devuan on which I test
that "sudo" is not installed by default. This program does however depend
on you being a sudoer. To check if you are a sudoer type in.

```
sudo -v
```

It should't return anything ask you for your password and return nothing,
if you get any other message, do the following steps:  

**_WARNING_: This presumes that you have control over the root user of the system**

1. Copy and paste this line in to terminal:
```
su - root -c "apt-get install sudo -y && adduser $USER sudo"
```

2. Enter the root user password

3. Type in
```
exit
```
4. Log back in and check that you are part of the sudoers
It should ask for your password and return nothing
```
sudo -v
```


You can repeat this proccess if needed
