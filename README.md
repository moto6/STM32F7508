# STM32F7508
 > introduction this git repo
  - DHKim's STM32F7508 Discovery kit(F7508 down below) infomation shareing
  - This Git Repo contains that not only studying STM32F7508 but also Touch GFX
  - This project sponsered by "STMicroelectroincs South Korea branch" and "Naver cafe 전자공작"
  - my goal is get used it F7508's cotrol peri and make user application
 > 이 깃허브 저장소 간단 소개
  - 제가 STM32F7508 Discovery kit(이하 F7508)학습한 내용에 대하여 공유합니다
  - F7508 뿐만 아니라 Touch GFX 에 대한 내용도 포함됩니다
  - 이 프로젝트는 ST마이크로 코리아와 네이버 카페 전자공작에서 후원(보드)을 받아 진행합니다.
  - 이 프로젝트를 통해 많은 분들이 F7508 을 활용한 다양한 응용 어플리케이션을 제작하는데 도움이 되기를 바랍니다
 ## Firmware 관련
   0. [하드웨어 분석](https://github.com/d-h-k/STM32F7508/blob/master/2_Contents/F7508_0_sch_anlz.md)
   1. [프로젝트 생성 및 BSP가져오기](https://github.com/d-h-k/STM32F7508/blob/master/2_Contents/F7580_1_project-make.md)
 ## TouchGFX관련
   - [Swipe GUI 구현하기](https://github.com/d-h-k/STM32F7508/blob/master/2_Contents/F7508_2_swipeGUI.md)
   - [MVP 구조에 대한 설명](https://github.com/d-h-k/STM32F7508/blob/master/2_Contents/doc_TheScreenConceptandModel-View-Presenter.md)
   - [문서 목차](https://github.com/d-h-k/STM32F7508/blob/master/2_Contents/doc_index.md)
   - [튜토리얼 요약](https://github.com/d-h-k/STM32F7508/blob/master/2_Contents/tgfx_zendesk/Tutorials_Summary.md)   
 ## 샘플 프로젝트 (By 전자공작)
   - [Quest 게시판](https://cafe.naver.com/ArticleList.nhn?search.clubid=18968931&search.menuid=1759&search.boardtype=L)
   - [Quest2 게시판](https://cafe.naver.com/ArticleList.nhn?search.clubid=18968931&search.menuid=1761&search.boardtype=L)
   - [Quest3 게시판](https://cafe.naver.com/ArticleList.nhn?search.clubid=18968931&search.menuid=1762&search.boardtype=L)
   - [Quest4 게시판](https://cafe.naver.com/ArticleList.nhn?search.clubid=18968931&search.menuid=1763&search.boardtype=L)
   - [Quest5 게시판](https://cafe.naver.com/ArticleList.nhn?search.clubid=18968931&search.menuid=1764&search.boardtype=L)
 ## 최종결과 : 원문(네이버 카페 전자공작 : https://cafe.naver.com/circuitsmanual/214004)
   - 준우승 ㅎㅎ!! 화웨이 와치를 받아버렸따!! : https://cafe.naver.com/circuitsmanual/214059
   - ![사진2](./img/resr.jpg)
   - ![사진1](./img/1221.jpg)
   
   
   
 ## fdgdfgd
 
 Compilation of kernel:
1. Pre-requisite
2. Initialise cross-compilation via SDK
3. Prepare kernel source code
4. Manage the kernel source code
5. Configure kernel source code
6. Compile kernel source code
7. Update software on board

1. Pre-requisite:
-----------------
OpenSTLinux SDK must be installed.

For kernel build, you need to install:
- libncurses and libncursesw dev package
    Ubuntu: sudo apt-get install libncurses5-dev libncursesw5-dev
    Fedora: sudo yum install ncurses-devel
- mkimage
    Ubuntu: sudo apt-get install u-boot-tools
    Fedora: sudo yum install u-boot-tools

Only if you like to have a git management of the code (see section 4
[Manage the kernel source code]):
- git:
    Ubuntu: sudo apt-get install git-core gitk
    Fedora: sudo yum install git

If you have never configured your git configuration, run the following commands:
    $> git config --global user.name "your_name"
    $> git config --global user.email "your_email@example.com"

2. Initialise cross-compilation via SDK:
----------------------------------------
Source SDK environment:
    $> source <path to SDK>/environment-setup-cortexa7t2hf-neon-vfpv4-openstlinux_weston-linux-gnueabi

To verify if your cross-compilation environment has been put in place correctly,
run the following command:
    $> set | grep CROSS
    CROSS_COMPILE=arm-openstlinux_weston-linux-gnueabi-

Warning: the environment is valid only on the shell session where you have
sourced the SDK environment.

3. Prepare kernel source:
-------------------------
If you have the tarball and the list of patches, then you must extract the
tarball and apply the patches.
    $> tar xfz <kernel source>.tar.gz
    or
    $> tar xfj <kernel source>.tar.bz2
    or
    $> tar xfJ <kernel source>.tar.xz
A new directory containing kernel standard source code will be created, go into it:
    $> cd <directory to kernel source code>

NB: if you like to have a git management of the code, see section 4 [Manage the
kernel source code]
    if there is some patch, please apply it on source code
    $> for p in `ls -1 <path to patch>/*.patch`; do patch -p1 < $p; done

4. Manage the kernel source code:
---------------------------------
4.1 Setup kernel source code under git
--------------------------------------
If you like to have a better management of change made on kernel source, you can
use git.

* With the kernel source code extracted in the section 3 [Prepare kernel source]
    $> cd <directory to kernel source code>
    $> test -d .git || git init . && git add . && git commit -m "new kernel" && git gc
    $> git checkout -b WORKING
    Apply patches:
    $> for p in `ls -1 <path to patch>/*.patch`; do git am $p; done
  NB: this is the fastest way to get your kernel source code ready for development

Or

* With the kernel source code from the Linux kernel git repositories:
    URL: https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git
    Branch: master
    Revision: INVALID

    $> git clone https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git
    $> cd <kernel source>
    $> git checkout -b WORKING INVALID
    $> for p in `ls -1 <path to patch>/*.patch`; do git am $p; done
  NB: this way is slightly slower than the tarball extraction but you get
      advantage of all git history.

4.2 Predefined kernel version vs auto-generated kernel version:
---------------------------------------------------------------
If you are using git for managing your source code, kernel makefile get the SHA1
of current git and add it to kernel version number generated.
 ex.: 4.9.23-g3e866b0 (kernel version  + SHA1 of current git commit)
To bypass this auto-generation of kernel version number:
    $> cd <directory to kernel source code>
    $> echo "" > .scmversion
This file avoid to have a kernel version with SHA1:
- With scmversion file: 4.9.23
- Without scmversion file: 4.9.23-g3e866b0
This configuration allows to build new kernel from modified source code without
any issue when using the new kernel binary on target regarding any external
kernel module already available on target rootfs (as built without scmversion).

5. Configure kernel source code:
--------------------------------
There are two methods to configure and compile kernel source code:
- Inside kernel source tree directory
- Outside kernel source tree in a build directory
We highly preconized the build is a build directory method as:
- It avoids mixing files generated by the build with the source files inside
  same directories
- To remove all the files generated by the build, it's enough to remove the
  build directory
- You can build for different configurations in several build directories, e.g.:
    1) build in "build_1" for a first kernel configuration
    2) build in "build_2" for a second kernel configuration
    Then this leaves the 2 images available for tests

* Configure on a build directory (different of kernel source code directory)
    Here for example, build directory is located at the same level of kernel
    source code
    $> cd <directory to kernel source code>
    $> mkdir -p ../build
    $> make ARCH=arm O="$PWD/../build" multi_v7_defconfig fragment*.config

    If there are some fragments, apply them
    * manually one by one:
    $> scripts/kconfig/merge_config.sh -m -r -O $PWD/../build $PWD/../build/.config ../fragment-01-xxx.config
    $> scripts/kconfig/merge_config.sh -m -r -O $PWD/../build $PWD/../build/.config ../fragment-02-xxx.config
    ...
    $> yes '' | make ARCH=arm oldconfig O="$PWD/../build"
    * or, by loop:
    $> for f in `ls -1 ../fragment*.config`; do scripts/kconfig/merge_config.sh -m -r -O $PWD/../build $PWD/../build/.config $f; done
    $> yes '' | make ARCH=arm oldconfig O="$PWD/../build"

* Configure on the current source code directory
    $> cd <directory to kernel source code>
    $> make ARCH=arm multi_v7_defconfig fragment*.config

    If there are some fragments, apply them
    * manually one by one:
    $> scripts/kconfig/merge_config.sh -m -r .config ../fragment-01-xxxx.config
    $> scripts/kconfig/merge_config.sh -m -r .config ../fragment-02-xxxx.config
    ...
    $> yes '' | make oldconfig
    * or, by loop:
    $> for f in `ls -1 ../fragment*.config`; do scripts/kconfig/merge_config.sh -m -r .config $f; done
    $> yes '' | make ARCH=arm oldconfig

NB: Two types of fragments are provided:
    * official fragments (fragment-xxx.config)
    * optional fragments as example (optional-fragment-xxx.config) to add a
      feature not enabled by default.
    The order in which fragments are applied is determined by the number of the
    fragment filename (fragment-001, fragment-002, e.g.).
    Please pay special attention to the naming of your optional fragments to
    ensure you select the right features.

6. Compile kernel source code:
------------------------------
You MUST compile from the directory on which the configuration has been done (i.e.
the directory which contains the '.config' file).

It's preconized to use the method with dedicated build directory for a better
managment of changes made on source code (as all build artifacts will be located
inside the dedicated build directory).

* Compile and install on a build directory (different of kernel source code directory)
    $> cd <directory to kernel source code>
    * Build kernel images (uImage and vmlinux) and device tree (dtbs)
    $> make ARCH=arm uImage vmlinux dtbs LOADADDR=0xC2000040 O="$PWD/../build"
    * Build kernel module
    $> make ARCH=arm modules O="$PWD/../build"
    * Generate output build artifacts
    $> make ARCH=arm INSTALL_MOD_PATH="$PWD/../build/install_artifact" modules_install O="$PWD/../build"
    $> mkdir -p $PWD/../build/install_artifact/boot/
    $> cp $PWD/../build/arch/arm/boot/uImage $PWD/../build/install_artifact/boot/
    $> cp $PWD/../build/arch/arm/boot/dts/st*.dtb $PWD/../build/install_artifact/boot/

    or

    $> cd <build directory>
    * Build kernel images (uImage and vmlinux) and device tree (dtbs)
    $> make ARCH=arm uImage vmlinux dtbs LOADADDR=0xC2000040
    * Build kernel module
    $> make ARCH=arm modules
    * Generate output build artifacts
    $> make ARCH=arm INSTALL_MOD_PATH="$PWD/../build/install_artifact" modules_install
    $> mkdir -p $PWD/../build/install_artifact/boot/
    $> cp $PWD/../build/arch/arm/boot/uImage $PWD/../build/install_artifact/boot/
    $> cp $PWD/../build/arch/arm/boot/dts/st*.dtb $PWD/../build/install_artifact/boot/

* Compile and install on the current source code directory
    $> cd <directory to kernel source code>
    * Build kernel images (uImage and vmlinux) and device tree (dtbs)
    $> make ARCH=arm uImage vmlinux dtbs LOADADDR=0xC2000040
    * Build kernel module
    $> make ARCH=arm modules
    * Generate output build artifacts
    $> make ARCH=arm INSTALL_MOD_PATH="$PWD/install_artifact" modules_install
    $> mkdir -p $PWD/install_artifact/boot/
    $> cp $PWD/arch/arm/boot/uImage $PWD/install_artifact/boot/
    $> cp $PWD/arch/arm/boot/dts/st*.dtb $PWD/install_artifact/boot/

7. Update software on board:
----------------------------
7.1. Partitioning of binaries:
------------------------------
* Bootfs:
  Bootfs contains the kernel and the devicetree.
* Rootfs:
  Rootfs contains the external kernel modules.
Please refer to User guide for more details.

7.2. Update via network:
------------------------
* kernel + devicetree
    $> cd <path to install_artifact dir>/install_artifact
    if bootfs are not monted on target, mount it
        $> ssh root@<ip of board> df to see if there is a partition mounted on /boot
    else
        $> ssh root@<ip of board> mount <device corresponding to bootfs> /boot
    $> scp -r boot/* root@<ip of board>:/boot/
    $> ssh root@<ip of board> umount /boot

* kernel modules
    $> cd <path to install_artifact dir>/install_artifact
    Remove the link on install_artifact/lib/modules/<kernel version>/
    $> rm lib/modules/<kernel version>/source lib/modules/<kernel version>/build
    Optionally, strip kernel modules (to reduce the size of each kernel modules)
    $> find . -name "*.ko" | xargs $STRIP --strip-debug --remove-section=.comment --remove-section=.note --preserve-dates

    Copy kernel modules:
    $> scp -r lib/modules/* root@<ip of board>:/lib/modules/

    Generate a list of module dependencies (modules.dep) and a list of symbols
    provided by modules (modules.symbols):
    $> ssh root@<ip of board> /sbin/depmod -a
    Synchronize data on disk with memory
    $> ssh root@<ip of board> sync
    Reboot the board in order to take update into account
    $> ssh root@<ip of board> reboot

7.3. Update via SDCARD on your Linux PC:
----------------------------------------
* kernel + devicetree
    $> cd <path to install_artifact dir>/install_artifact
    Verify sdcard are mounted on your Linux PC: /media/$USER/bootfs
    $> cp -r boot/* /media/$USER/bootfs/
    Depending of your Linux configuration, you may call the command under sudo
        $> sudo cp -r boot/* /media/$USER/bootfs/
    Don't forget to unmount properly sdcard

* kernel modules
    $> cd <path to install_artifact dir>/install_artifact
    Remove the link on install_artifact/lib/modules/<kernel version>/
    $> rm lib/modules/<kernel version>/source lib/modules/<kernel version>/build
    Optionally, strip kernel modules (to reduce the size of each kernel modules)
    $> find . -name "*.ko" | xargs $STRIP --strip-debug --remove-section=.comment --remove-section=.note --preserve-dates

    Verify sdcard are mounted on your Linux PC: /media/$USER/rootfs
    Copy kernel modules:
    $> cp -r lib/modules/* /media/$USER/rootfs/lib/modules/
    Depending of your Linux configuration, you may call the command under sudo
        $> sudo cp -r lib/modules/* /media/$USER/rootfs/lib/modules/
    Don't forget to unmount properly sdcard

    Generate a list of module dependencies (modules.dep) and a list of symbols
    provided by modules (modules.symbols):
    $> ssh root@<ip of board> depmod -a
    Synchronize data on disk with memory
    $> ssh root@<ip of board> sync
    Reboot the board in order to take update into account
    $> ssh root@<ip of board> reboot

7.4. Update via SDCARD on your BOARD (via U-Boot):
--------------------------------------------------
You MUST configure first, via U-Boot, the board into usb mass storage:
* Plug the SDCARD on Board.
* Start the board and stop on U-boot shell:
    Hit any key to stop autoboot: 0
    STM32MP>
* plug an USB cable between the PC and the board via USB OTG port.
* On U-Boot shell, call the usb mass storage functionnality:
    STM32MP> ums 0 mmc 0
    ums <USB controller> <dev type: mmc|usb> <dev[:part]>
Example:
For SDCARD:    ums 0 mmc 0
For USB Disk:  ums 0 usb 0

* kernel + devicetree
    $> cd <path to install_artifact dir>/install_artifact
    Remove the link on install_artifact/lib/modules/<kernel version>/
    $> rm lib/modules/<kernel version>/source lib/modules/<kernel version>/build
    Optionally, strip kernel modules (to reduce the size of each kernel modules)
    $> find . -name "*.ko" | xargs $STRIP --strip-debug --remove-section=.comment --remove-section=.note --preserve-dates

    Verify sdcard mount point are mounted on your Linux PC: /media/$USER/bootfs
    $> cp -r boot/* /media/$USER/bootfs/
    Depending of your Linux configuration, you may call the command under sudo
        $> sudo cp -rf boot/* /media/$USER/bootfs/
    Don't forget to unmount properly sdcard
    Warning: kernel and device tree file name must be aligned between
    extlinux.conf file and file system.

* kernel modules
    $> cd <path to install_artifact dir>/install_artifact
    Remove the link on install_artifact/lib/modules/<kernel version>/
    $> rm lib/modules/<kernel version>/source lib/modules/<kernel version>/build
    Optionally, strip kernel modules (to reduce the size of each kernel modules)
    $> find . -name "*.ko" | xargs $STRIP --strip-debug --remove-section=.comment --remove-section=.note --preserve-dates

    Verify sdcard mount point are mounted on your Linux PC: /media/$USER/rootfs
    Copy kernel modules:
    $> cp -rf lib/modules/* /media/$USER/rootfs/lib/modules/
    Depending of your Linux configuration, you may call the command under sudo
        $> sudo cp -r lib/modules/* /media/$USER/rootfs/lib/modules/
    Don't forget to unmount properly sdcard

    At next runtime, don't forget to generate a list of module dependencies
    (modules.dep) and a list of symbols provided by modules (modules.symbols):
    $on board> depmod -a
    Synchronize data on disk with memory
    $on board> sync
    Reboot the board in order to take update into account
    $on board> reboot

8. Useful information:
----------------------
* How to re-generate kernel database on board:
    $on board> depmod -a
    (don't forget to synchronize the filesystem before to reboot)
    $on board> sync

* How to see the list of external kernel modules loaded:
    $on board> lsmod

* How to see information about kernel module:
    $on board> modinfo ./install_artifact/lib/modules/<kernel version>/kernel/drivers/leds/led-class-flash.ko
Example usage:
filename:       <build directory>./install_artifact/lib/modules/4.9.23-g3e866b0/kernel/drivers/leds/led-class-flash.ko
license:        GPL v2
description:    LED Flash class interface
author:         Jacek Anaszewski <j.anaszewski@samsung.com>
depends:
intree:         Y
vermagic:       4.9.23-g3e866b0 SMP mod_unload ARMv7 p2v8


