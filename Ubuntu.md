### **总纲**#5
确定系统版本号，显卡型号。然后根据显卡型号安装驱动，根据驱动安装支持的cuda版本，根据cuda版本安装相应cudnn版本。
### 安装
**1.** 在ubuntu官网选择需要下载的ubuntu版本（16.4或者18.04均可）
[https://www.ubuntu.com/download/desktop/thank-you?country=JP&version=18.04.1&architecture=amd64](url)
**2.** 然后安装UltraISO软件，免费试用就行。安装好后，导入已经下载好的Ubuntu的ios文件。
[https://www.ultraiso.com/](url)
**3.** 准备一个空的U盘，在UltraISO中点击启动，写入硬件映像到U盘里即可。
**4.** 然后需要为linux系统腾出磁盘空间，越大越好。右键点击开始，磁盘管理。选择腾好的磁盘，右键点击删除卷就行。这些删除掉的磁盘会变成可用空间，一会安装linux系统时会自动检测可用空间进行安装。
**5.** 重启电脑，进入boot模式，选择U盘启动，重启。
**6.0**修改配置文件`sudo vim /etc/apt/apt.conf.d/10periodic`关闭系统更新

### 卸载（If needed）
**windows**下打开磁盘管理，删除Liunx所在的分区即可。
重启电脑，如果进入grub rescue状态，这里最简单的方法就是重启插入U盘，用U盘打开Linux系统。然后在终端里输入以下指令，删除引导组件。
**sudo apt-get install lilo
sudo lilo -M /dev/sda mbr**
然后重启电脑就不会询问是否进入**Linux**系统了。

**Grub修复**
`sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update`
`sudo apt-get install -y boot-repair && boot-repair`
选择第一项 Recommended repair
Ref:[https://blog.csdn.net/zouguo1211/article/details/81200628](url)

**链接快速启动**`sudo ln -s /home/lab/MATLAB/R2018a/bin/matlab /usr/local/bin/matlab`