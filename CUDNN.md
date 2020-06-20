# [System-Configuration](https://github.com/John-Joe/System-Configuration)
1. 下载与CUDA匹配的版本
https://developer.nvidia.com/rdp/cudnn-download
https://developer.nvidia.com/rdp/cudnn-download#a-collapse731-10
2. 要下载四个文件
**cuDNN v7.3.1 Library for Linux
cuDNN v7.3.1 Runtime Library for Ubuntu18.04 (Deb)
cuDNN v7.3.1 Developer Library for Ubuntu18.04 (Deb)
cuDNN v7.3.1 Code Samples and User Guide for Ubuntu18.04 (Deb)**
3. 进入到文件下载目录里，比如download
在终端输入 （一定要按照顺序安装不然会出错）
`tar -xzvf cudnn-10.0-linux-x64-v7.3.1.20.tgz`
`sudo cp cuda/include/cudnn.h /usr/local/cuda/include`
`sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64`
`sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*`
4. 安装其余的包
`sudo dpkg -i libcudnn7_7.3.1.20-1+cuda10.0_amd64.deb`
`sudo dpkg -i libcudnn7-dev_7.3.1.20-1+cuda10.0_amd64.deb`
`sudo dpkg -i libcudnn7-doc_7.3.1.20-1+cuda10.0_amd64.deb`
5. 验证cudnn 是否安装成功
`cp -r /usr/src/cudnn_samples_v7/ $HOME`
`cd $HOME/cudnn_samples_v7/mnistCUDNN`
`make clean && make`
`./mnistCUDNN`

**Reference**
#https://blog.csdn.net/qq_43118318/article/details/83691204