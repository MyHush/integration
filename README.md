# Hush Full Node Integration Docs

This document will help you install and maintain a Hush Full Node. It is mainly geared towards exchanges and mining pools, but
will be useful to any service provider adding Hush, such as a Discord Tipbot service provider like https://tip.cc

# Installing Hush from source

On Ubuntu/Linux systems, you can install Hush from [source](https://github.com/MyHush/hush3) with these commands:

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

Here is an [example config file](https://gist.github.com/leto/2c3401df2f21a2ed5639bdffe0ff8717) for HUSH which is recommended for exchanges and mining pools.

## How Shielded Addresses (zaddrs) Are Different

  * Change from a zaddr goes back to itself! Not a different address, like in transparent addresses (taddrs).
  * Making zaddr transactions are slower, taking a few seconds instead of a few milliseconds
  * Shielded transactions do not show the sender address, receiver address or amounts on the public explorer. You will need to use local RPC methods such as `z_viewtransaction` to see those details
  * Shielded transactions are larger than transparent transactions, because more data is stored
