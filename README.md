# ubports-smt285-gtexslte
Ubuntu Touch ported to the Samsung Galaxy A 7.0 (2016) Model: SM-T285 Codename: gtexslte

Note: This repo is 10 gigabytes in size. when you successfully build the system.img and the boot.img. it may take several gigabytes. Make sure you have enough space

Note: The BUILDDIR is the folder called halium containing everything. it has another halium folder inside it. the first halium folder is the BUILDDIR

Building Dependencies:

For Debian (Newer than Stretch) and Ubuntu 16.04 or 18.04:

If your host PC has a 64-bit architecture (amd64), enable the usage of the i386 architecture:

```
sudo dpkg --add-architecture i386 
```

Update your package lists to take advantage of the new architecture:

```
sudo apt update 
```

Install the required dependencies:

```
sudo apt install git gnupg flex bison gperf build-essential \ zip bzr curl libc6-dev libncurses5-dev:i386 x11proto-core-dev \ libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \ libgl1-mesa-dev g++-multilib mingw-w64-i686-dev tofrodos \ python-markdown libxml2-utils xsltproc zlib1g-dev:i386 schedtool \ repo liblz4-tool bc lzop imagemagick libncurses5 rsync
```

For Ubuntu 20.04 or newer

If your host PC has a 64-bit architecture (amd64), enable the usage of the i386 architecture:

```
sudo dpkg --add-architecture i386 

```

Update your package lists to take advantage of the new architecture:

```
sudo apt update 

```

Install the required dependencies:

```
sudo apt install git gnupg flex bison gperf build-essential \ zip bzr curl libc6-dev libncurses5-dev:i386 x11proto-core-dev \ libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \ libgl1-mesa-dev g++-multilib mingw-w64-i686-dev tofrodos \ python3-markdown libxml2-utils xsltproc zlib1g-dev:i386 schedtool \ liblz4-tool bc lzop imagemagick libncurses5 rsync \ python-is-python3 python2 

```

Create a directory named ‘bin’ in your home directory, and include it in your path:

```
mkdir -p ~/bin echo export PATH=\$PATH:\$HOME/bin >> ~/.bashrc source ~/.bashrc 

```
Download the repo script and make it executable:

```
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo chmod a+rx ~/bin/repo

```

Build Instructions:

First you need to initialize the environment using the envsetup.sh tool included in the source tree. Enter your BUILDDIR and issue the command:

```
source build/envsetup.sh 

```

The output will look like this:

```
including device/samsung/gtexslte/vendorsetup.sh including vendor/cm/vendorsetup.sh including sdk/bash_completion/adb.bash including vendor/cm/bash_completion/git.bash including vendor/cm/bash_completion/repo.bash 

```

The breakfast command is used to set up the build environment for this device. From the root of your BUILDDIR run the following command:

```
breakfast gtexslte
```

Breakfast will attempt to find your device, set up all of the environment variables needed for building, and give you a summary at the end


Halium will use the mkbootimg tool for creating the boot image. In most cases it is not on the local harddisk, so it can be built by issuing:

```
mka mkbootimg 
```

Now build the halium-boot.img using the commands:

```
export USE_HOST_LEX=yes mka halium-boot
```

Note: If you prefer make instead of mka youshould set -j[num] for parallel building, which reduces build time. Replace [num] with the number of threads in your system plus 2.

Once you are building the halium-boot.img. you can now build system.img by running this command

```
mka systemimage
```
