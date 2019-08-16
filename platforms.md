# 关于基础平台（platform）的一些考虑

基础平台提供一套教学应用程序的基础运行环境。硬件主要是指板子（board），软件主要
包含BSP（bootloader、硬件驱动程序）、OS（一般是linux）、中间件runtime的库、
SDK、各种工具软件和文档。

## 原则

1. 要避免多个功能相似的板子。

    硬件上差异至少增加了BSP开发维护的难度和成本，所以应该避免。

    取而代之的原则是：共享一个基础性的板子（cpu/gpu，i/o），在其上添加扩展（比如：
    麦克风阵列）。这样做的好处是不光统一了硬件环境，并且让统一软件环境变得更容易。

    **注意**：
    >这个原则经常不适用于来自外部的项目，因为一般这些项目有自己硬件平台，除非我们
    >用自己的硬件做了替换。

2. i/o接口要丰富。

    i/o接口越丰富越好用，教学案例的开发越方便。
    
    这里“好用”包含了提供python/javascript等编程接口（以及响应的文档）。

