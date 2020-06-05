# dstation-2020

A simple installer script for [Docking Station (DS)](https://creatures.wiki/Docking_Station),
a freeware entry in the [Creatures series](https://creatures.wiki/Creatures_series). If you don't care about features or
compatibility and just want the game to run, this may help.

It installs hard to find library versions and creates a set of folders for the game.

## I had a problem!

[Create an issue](https://github.com/Nazushvel/dstation-2020/issues/new/choose)! Do the following:
1. Run `lsb_release -a`, then paste the input so we know what distro you're on
2. Include a short 1-2 sentence summary of what you tried to do
3. Include a short 1-2 sentence summary of what went wrong
4. Paste the error output if any
5. Add any additional information you think might help

## How to use it
Some distros (Arch 64) have been reported to run the script without any sort of setup beforehand. Others such as
Ubuntu and Debian may need you to do some setup work before running the script. See the **Pre-run Steps** section for
information on what you need to install beforehand.

### General requirements
1. At least 75 mb of free space on the partition you're installing to
2. 32-bit compatibility enabled, see the the **Pre-run Steps** section

### Installing the game

1. Put the script in a directory you'd like to install DS into. 
2. Make sure the script is set to executable, either through your file manager's GUI,
 or by running `chmod +x dstation-2020`.
3. Run `./dstation-2020 setup`


### Running the game
If all went well with install, all you should need to do to run is:

    ./dstation-2020 start

If you get a message that looks like the following...

    vagrant@buster:~/dockingstation$ ./dstation-2020 start
    ./dstation-2020: line 199: ./lc2e: No such file or directory

then you need to enable compatibility for 32 bit binaries. If your distro isn't listed in the 
**Pre-run Steps** section, please file an issue as described in the **I had a problem!** section. If possible, please be
ready to help test solutions.


## Pre-run Steps

This only lists distros that are known to have issues. Yours might work perfectly, or it might break. The only way to 
find out is try!

### 64-Bit Debian & Ubuntu
These instructions have been reported to work with the following distros:
* Debian 10 Buster, 64 Bit
* Ubuntu 20.04 LTS, 64 Bit

They may also work for Mint and other similar distros.

#### 1. Install the script's dependencies

You'll need to make sure that `p7zip-full` and `zstd` are installed as not all debian family OSes come with them:

    sudo apt-get install p7zip-full zstd

#### 2. Add i386 architecture & update apt
Add the 386 architecture

    sudo dpkg --add-arch i386

then apt-get update

    sudo apt-get update

If everything worked correctly, running `dpkg --print-foreign-architectures` should look like the following:

    vagrant@buster:~$ dpkg --print-foreign-architectures
    i386

#### 3. Install additional dependencies

These are needed for the game to run.

    sudo apt-get install libstdc++6:i386 libgcc1:i386 zlib1g:i386 libncurses5:i386 libxi6:i386
    
There may be additional steps required for enabling sound.