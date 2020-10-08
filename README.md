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


