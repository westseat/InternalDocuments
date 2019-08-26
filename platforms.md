# 基础平台（platform）

基础平台为教学应用程序提供了一套基础运行环境。硬件主要是指板子（board），
软件主要包含BSP（bootloader、kernel、硬件驱动程序）、OS（一般是linux）、
runtime libraries、SDK、各种工具软件和文档。

## 设计原则
:bulb: 请参考Arduino和Raspberry Pi！！！

1. 要避免多个功能相似的板子。

    硬件上差异至少增加了BSP开发维护的难度和成本，所以应该避免。

    取而代之的设计是：采取一个基础板（cpu/gpu，i/o）+ 多个扩展板（比如：
    麦克风阵列扩展板）设计。这样做的好处是不光统一了硬件环境，并且让统一软件环
    境变得更容易。

    **注意**：
    > 这个经常不适用于来自外部的项目，因为一般这些项目有自己硬件平台，除非我们
    > 用自己的硬件做了替换。

2. i/o接口要丰富易用。

   i/o接口越丰富越好用，教学案例的开发越方便。

   * 丰富

     基础板尽量提供这些接口，不能在基础板上提供的就 通过扩展板提供。
    
   * 易用

     提供python/javascript等编程接口（以及配套的文档）。

     可参考树莓派的[GPIO Zero](https://gpiozero.readthedocs.io/en/stable/), 
     [pigpio](http://abyz.me.uk/rpi/pigpio/) and [WiringPi](http://wiringpi.com/)。

## SDK

维护SDK，包含bootloader, kernel, runtime library, rootfs。

SDK要通过git维护管理。

提供包含SDK以及所需环境的docker image。

## pre-built image

维护预编译好的linux image，包含bootloader、kernel、hardware drivers、rootfs、runtime libraries以及必要的其它软件和文档。

## 使用树莓派做原型

教学应用开发过程中，可能发现我们的基础平台缺乏对某一特定硬件的支持，或者可能硬件有问题，
这时候可以考虑使用树莓派。树莓派的使用请参照[这里](raspi.md)

## `qemu for arm`

很多软件cross-build环境设置很麻烦 —— 一般需要rootfs中的库，不如板子上natvie-build简单，
但是因为开发板性能让编译变得耗时过长，甚至因为内存太小导致编译出错。

`qemu for arm`是一个在pc上的arm虚拟机，支持armv7以及armv8（aarch64），请参考
[qemu的文档](https://wiki.qemu.org/Documentation/Platforms/ARM)。

注意：文档里的[tutorial](https://translatedcode.wordpress.com/2017/07/24/installing-debian-on-qemus-64-bit-arm-virt-board/)里安装的是debian，ubuntu
的image在如下地址：
> https://mirrors.aliyun.com/ubuntu-ports/dists/xenial/main/installer-arm64/current/images/netboot/ubuntu-installer/arm64/initrd.gz

> https://mirrors.aliyun.com/ubuntu-ports/dists/xenial/main/installer-arm64/current/images/netboot/ubuntu-installer/arm64/linux