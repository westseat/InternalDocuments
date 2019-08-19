# 树莓派的使用说明

教学应用开发过程中，可能发现我们的基础平台缺乏对某一特定硬件的支持，或者可能硬件有问题，
这时候可以考虑使用树莓派。

参考你的树莓派版本，我这里以
[Raspbery Pi 3 B](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/)
来简单说明ubuntu的安装和使用。

1. 下载和烧录ubuntu image

   ubuntu有两个版本，一个是[ubuntu-mate](https://ubuntu-mate.org/raspberry-pi/), 
   另一个是[ubuntu官方](https://ubuntu.com/download/iot/raspberry-pi-2-3)，都可以用。 似乎ubuntu mate更友好一些。

2. 启动ubuntu
   
   将烧录好ubuntu image的SD卡插进树莓派，接上hdmi显示器、键盘和鼠标，就可以上电启动了。

3. 连接wifi

   命令行连接WiFi, 请看这里[这里](https://github.com/joeyu/handy_shell_commands/blob/master/ubuntu.md#enabling-wifi)。

4. 改动ubuntu-ports源【可选】

   `/etc/apt/source.list`里的`http://ports.ubuntu.com`源对中国大陆用户可能慢点了点，
   可以考虑换成`https://mirrors.aliyun.com/ubuntu-ports`。

5. 增大swap分区【可选】

   树莓派内存为1GB时，native compilation可能会有内存不够用的情况，这时候可以增大swap
   分区，具体请看[这里](https://www.fosslinux.com/1064/how-to-create-or-add-a-swap-partition-in-ubuntu-and-linux-mint.htm)

6. 通过ssh连接板子

   可能openssh-server没有安装，或者安装了没有启动，通过下列命令安装启动：

   ```bash
   $ sudo apt install openssh-server
   $ sudo systemctl enable sshd
   $ sudo systemctl start sshd
   ```

   这样就可以在PC上通过ssh连接树莓派了，显示器和键盘就不需要了。

7. 运行`raspi-config`

   `raspi-config`提供了很多有用的功能，比如：禁止图形桌面起来，以节省内存。

8. 扩展硬件的使用

   请参考相应硬件厂商的文档。

