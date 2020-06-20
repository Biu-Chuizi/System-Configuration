### **总纲**#5

Ubuntu16.04
**CUDA8.0**要求GCC版本是5.x或者6.x
### 安装显卡驱动
首先安装显卡驱动。首先看自己显卡
**lspci | grep -i vga
lspci | grep -i nvidia**
**lsmod | grep -i nvidia**
在ubuntu16.04中，更换驱动非常方便，去 
系统设置->软件更新->附加驱动->切换到最新的NVIDIA驱动即可。应用更改->重启
**再运行nvidia-smi来看看**


### CUDA9.0安装
**CUDA9.0**下载到~/Downloads文件夹中。之后，在这里打开终端，依次输入下面的命令：
**sudo dpkg -i cuda-repo-ubuntu1604-9-0-local_9.0.176-1_amd64.deb
sudo apt-key add /var/cuda-repo-9-0-local/7fa2af80.pub
sudo apt-get update
sudo apt-get install cuda**
再CUDA完成安装之后，还需要添加环境变量，打开终端，输入下面的命令：
**export PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}**
如果是64位系统，输入： 
 **export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}**
如果是32位系统，输入： 
 **export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}**
上述过程完成了整个的CUDA9.0的安装

**如果下载的是runfile文件**
**sudo sh cuda_8.0.44_linux.run --tmpdir=/tmp**

= Summary =
Driver: Not Selected
Toolkit: Installed in /usr/local/cuda-8.0
Samples: Installed in /home/textminer
13

14
Please make sure that
15
– PATH includes /usr/local/cuda-8.0/bin
16
– LD_LIBRARY_PATH includes /usr/local/cuda-8.0/lib64, or, add /usr/local/cuda-8.0/lib64 to /etc/ld.so.conf and run ldconfig as root
17

18
To uninstall the CUDA Toolkit, run the uninstall script in /usr/local/cuda-8.0/bin
19

20
Please see CUDA_Installation_Guide_Linux.pdf in /usr/local/cuda-8.0/doc/pdf for detailed information on setting up CUDA.
21

22
***WARNING: Incomplete installation! This installation did not install the CUDA Driver. A driver of version at least 361.00 is required for CUDA 8.0 functionality to work.
23
To install the driver using this installer, run the following command, replacing with the name of this run file:
24
sudo .run -silent -driver
25

26
Logfile is /tmp/cuda_install_6583.log
安装完毕后，再声明一下环境变量，并将其写入到 ~/.bashrc 的尾部:
1
export CUDA_HOME=/usr/local/cuda
2
export PATH=$PATH:$CUDA_HOME/bin
3
export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
保存退出，运行source ~/.bashrc 
测试是否安装成功
1
// 如果怕把samples搞坏了那就先搞一个备份，在备份里搞
2
cd /usr/local/cuda/samples/1_Utilities/deviceQuery
3
sudo make
4
./deviceQuery
结果如下
之前有看到说要把gcc改成4.9的。不过我现在用5.4的也可以编译，就是有几个警告，不知道会不会有什么大的影响。


### 安装cuDNN v7.0.
下载地址：https://developer.nvidia.com/cudnn
进入之后点击Download，之后进入下载界面，选择上I Agree To the Terms of the cuDNN Software License Agreement的复选框，一次要选择上**正确**的版本！！！！！
同样的，假设下载目录是~/Downloads，在这里打开终端，之后输入以下命令： 
 **sudo dpkg -i libcudnn7_7.0.5.15-1+cuda9.0_amd64.deb** 
注意，上述命令中的可能会由于cudnn版本的细微差异而不同，注意tab键补齐就行。之后等待完成cuDNN的安装。

### 安装Tensorflow-GPU版本
安装pip和Virtualenv 
打开终端； 
如果使用Python 2.7的版本，输入**sudo apt-get install python-pip python-dev python-virtualenv** 
如果使用Python 3.x的版本，输入**sudo apt-get install python3-pip python3-dev python-virtualenv** 
两者选择一个就行，个人推荐Python 3.x版本
创造一个虚拟的Python开发环境： 
第一步如果选择Python 2.7版本，终端输入：**virtualenv --system-site-packages ~/tensorflow** 
第一步如果选择Python 3.x版本，终端输入：**virtualenv --system-site-packages -p python3 ~/tensorflow** 
注意，~/tensorflow是自己选择的位置并创建的目录。大家可以自行选择其他的位置和命名。本教程创建完成之后，会在用户家目录下看到多出的tensorflow文件夹。
激活虚拟环境： 
如果你的终端是bash, sh, ksh, zsh中的一个，那么输入：**source ~/tensorflow/bin/activate** 
如果你的终端是csh,tcsh，那么输入：**source ~/tensorflow/bin/activate.csh** 
如果你不知道的话。。。。那就输入第一个吧，Ubuntu默认是第一个。。。。。
保证pip的版本不低于8.1，在虚拟环境中输入：**easy_install -U pip**

### 安装tersorflow-gpu版本： 
Python 2.7版本：pip install --upgrade tensorflow-gpu 
Python 3.x版本：pip3 install --upgrade tensorflow-gpu 
经过这一步骤之后，tensorflow就安装完成了。
以后，如果需要使用tenssorflow，则打开终端输入：**source ~/tensorflow/bin/activate**,如果关闭虚拟环境，输入**deactivate**即可。
有些IDE 会自动检测**tensorflow**创建的虚拟环境，不必在终端中单独开启或者关闭，比如**pycharm**等。
实际运行检验： 
使用**pycharm**作为**IDE**，进行检验。 