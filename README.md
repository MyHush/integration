# Hush Full Node Integration Docs

This document will help you install and maintain a Hush Full Node. It is mainly geared towards exchanges and mining pools, but
will be useful to any service provider adding Hush, such as a Discord Tipbot service provider like https://tip.cc

# Installing Hush from source

On Ubuntu/Linux systems, you can install Hush with these commands:

```
# install build depedencies
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib \
      autoconf libtool ncurses-dev unzip git python zlib1g-dev wget \
      bsdmainutils automake curl unzip nano libsodium-dev
git clone https://github.com/MyHush/hush3.git
cd hush3
./build.sh -j4
```

More details can be found [here](https://github.com/MyHush/hush3/blob/master/INSTALL.md)

# Installing Hush from a binary

You can also install a binary from an [official release](https://github.com/MyHush/hush3/releases/tag/v3.5.0)

3.5.0 is our latest mandatory release, [3.5.1](https://github.com/MyHush/hush3/releases/tag/v3.5.1) is an optional update that has some new features.

## Config changes for exchanges and pools

The default location on Linux for the HUSH config file is `~/.komodo/HUSH3/HUSH3.conf` . This file will have a username and password for RPC
access, so don't show the contents to untrusted people.

An advanced feature we suggest exchanges+pools use is called `consolidation=1` which keeps wallets small and hence fast.
This feature will always make small transactions in the background, "consolidating" funds into very efficient amounts. This
makes future transactions fast by spending small amounts of time consolidating funds in the background.

