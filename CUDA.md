### **总纲**#5
**安装前最好先看一遍官方手册**
官网下载选择对应自己需求的版本（下载runfile{local}）：
10.0版本：**https://developer.nvidia.com/cuda-downloads**
Run `sudo sh cuda_10.0.130_410.48_linux.run`
8.0版本：**https://developer.nvidia.com/cuda-80-ga2-download-archive**
Run `sudo sh cuda_8.0.61_375.26_linux.run`

**检查系统，检查gcc, 检查kernel header和 package development ，禁用nouveau
`gcc  --version`
`uname -r`
`sudo apt-get install linux-headers-$(uname -r)`

`lsmod | grep nouveau`
`sudo update-initramfs -u`

**= Summary =**
Driver: Not Selected


**添加环境变量**需确定版本
`vim ~/.bashrc`
在最后加上：
`export PATH=/usr/local/cuda-9.0/bin:$PATH`
`export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64:$LD_LIBRARY_PATH`
`nvcc -V` 查看cuda8.0是否安装成功

**卸载**
` sudo /usr/local/cuda-10.0/bin/uninstall_cuda_10.0.pl`
`sudo apt-get remove cuda `
`sudo apt-get autoclean`
`sudo apt-get remove cuda`
然后在目录切换到/esr/local/下
`cd /usr/local/`
`sudo rm -r cuda-9.1`
**多版本CUDA共存配置**切换软连接
`sudo rm -rf cuda`
`sudo ln -s /usr/local/cuda-9.1 /usr/local/cuda`
`![image](https://user-images.githubusercontent.com/31396426/61423958-c341f880-a94c-11e9-9b38-ccd64fc55da7.png)

参考cuda安装配置
#https://gist.github.com/Brainiarc7/470a57e5c9fc9ab9f9c4e042d5941a40