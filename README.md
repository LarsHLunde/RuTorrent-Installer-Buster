# RuTorrent-Installer-Buster v1.1.1

## Description
This is a RuTorrent installer for debian buster linux systems.
My original goal for the project was to make a RuTorrent installer
for the Raspberry Pi 3 running Raspbian-jessie-lite,
this fork is for Debian and Raspbian Buster.

Due to a bug with the buster repo version of libcurl4,
where if you add more than 2000-3000 torrents to rtorrent,
rtorrent will segfault and die.

This version adds the testing repo to debian as the non-default,
and gets the libcurl4 version from there instead of from buster.

For other Debian based systems and Ubuntu see: 
https://github.com/LarsHLunde/RuTorrent-Installer

## Systems
Operating System | State
--- | ---
Raspbian Buster | :heavy_check_mark:
Debian Buster | :heavy_check_mark:
Armbian Buster | :heavy_check_mark:

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


## Changelog
Description | Version | State
--- | --- | ---
New bug where dependency for libgcc-8-dev fails on install | v1.1.1 | release
Added code for raspbian, stress tested for all systems | v1.1 | release
Initial working release for armbian and debian | v1.0 | beta
