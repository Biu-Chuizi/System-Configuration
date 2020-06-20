### **总纲**#5
**如果是双系统，首先禁用Windows安全模式**
从官方网站下载最新的**匹配**的驱动
**https://www.nvidia.com/Download/index.aspx**
注意：按理说安装cuda的时候会自带英伟达显卡驱动，不需要自己安装。但是，此时linux系统默认启动的是主板自带的集存显卡，只有先禁用了集存显卡，再在安装时去掉opengl文件才行。否则会进入linux系统循环登陆的BUG。
0. Pre action
` sudo apt-get remove --purge nvidia*`
 #若安装失败也是这样卸载以及
` ./NVIDIA-Linux-x86_64-390.48.run --uninstall` #确保卸载干净。

1. Install requirement
 `sudo apt-get update `
` sudo apt-get install dkms build-essential linux-headers-generic`
` sudo apt-get install gcc-multilib xorg-dev`
` sudo apt-get install freeglut3-dev libx11-dev libxmu-dev install libxi-dev  libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev`

2. prohibit nouveau
编辑配置文件：**`sudo vim /etc/modprobe.d/blacklist.conf`**
在文本的最后一行加入:**`blacklist nouveau`**
`  blacklist lbm-nouveau`
` options nouveau modeset=0`
` alias nouveau off`
` alias lbm-nouveau off`
保存执行更新:**`sudo update-initramfs -u`**
重启后执行：**`lsmod | grep nouveau`**
没有输出就禁用成功了
进入tty关闭图形界面`sudo service lightdm stop`

3. Install
**sudo chmod a+x NVIDIA-Linux-x86_64-410.73.run**
**sudo ./NVIDIA-Linux-x86_64-410.73.run –no-opengl-files --dkms --no-opengl-files**
##dkms 安装最好 选yes
##32位兼容 安装最好 选yes
##x-org 最好别安，选no，有的电脑可能导致登录界面黑屏
然后重启
`sudo service lightdm start` #没自动跳的话 crtl+alt+f7

4. Check version
cat /proc/driver/nvidia/version

5. Reinstall
**重新安装注意gcc版本是否合适**
`sudo apt-get remove --purge nvidia*`
Then force step 3.

6. 关于循环登陆，可以**卸载显卡驱动重装**。

7. 关于命令行循环滚动
```
sudo gedit /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi"
sudo update-grub
sudo reboot
```

**Ref：**
#https://zhuanlan.zhihu.com/p/48082080
#https://blog.csdn.net/haoji007/article/details/81983440
#https://blog.csdn.net/u014561933/article/details/79958017