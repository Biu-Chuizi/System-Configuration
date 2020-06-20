# [System-Configuration](https://github.com/John-Joe/System-Configuration)
**自己编译：**
还可以参考https://www.pyimagesearch.com/opencv-tutorials-resources-guides/
官网下载源码https://opencv.org/releases.html
然后自己编译https://docs.opencv.org/master/d7/d9f/tutorial_linux_install.html
编译报错解决https://stackoverflow.com/questions/46584000/cmake-error-variables-are-set-to-notfound

`sudo find / -name "*opencv*" -exec rm -i {}`

**卸载Opencv**
`sudo make uninstall`
`sudo rm -r build`
`sudo rm -r /usr/local/include/opencv2 /usr/local/include/opencv /usr/include/opencv /usr/include/opencv2 /usr/local/share/opencv /usr/local/share/OpenCV /usr/share/opencv /usr/share/OpenCV /usr/local/bin/opencv* /usr/local/lib/libopencv*`
`sudo rm -r opencv`
`cd /usr/`
`sudo find . -name "*opencv*" | xargs sudo rm -rf`
`apt-get remove opencv-doc opencv-data python-opencv`移除python相关

**Anaconda环境下安装opencv-python**
即：直接在cmd命令行输入：conda install --channel https://conda.anaconda.org/menpo opencv3
然后，根据提示输入y即可
安装以及卸载Opencv
**sudo anaconda3/bin/pip install opencv-python
sudo anaconda3/bin/pip uninstall "模块名"**
Open cv 查看版本号
**python
import cv2
cv2.__version __ **

**pip安装：**
`sudo apt-get install python-pip`
`sudo apt install libopencv-dev`
`pip install matplotlib`
`pip install numpy`
`pip install opencv-python`