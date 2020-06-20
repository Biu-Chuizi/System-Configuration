### **总纲**#5

**下载LabelImg**
**方式1**：网址：**https://github.com/John-Joe/labelImg** 直接下载，下载后将**labelImg-master.zip**移动至**home**主文件夹下解压，得到**LabelImg-master**文件。
**方式2**：使用**git**命令
**git clone https://github.com/John-Joe/labelImg**

**安装**
$ **sudo apt-get install pyqt4-dev-tools** # 安装PyQt4
$ **sudo pip install lxml # 安装lxml** #如果报错，可以试试下面语句
$ **sudo apt-get install python-lxml**
然后打开终端，进入LabelImg目录后使用make编译
**cd labelImg
make all**

**快捷键**
Ctrl + u  加载目录中的所有图像，鼠标点击Open dir同功能
Ctrl + r  更改默认注释目标目录(xml文件保存的地址) 
Ctrl + s  保存
Ctrl + d  复制当前标签和矩形框
space     将当前图像标记为已验证
w         创建一个矩形框
d         下一张图片
a         上一张图片
del       删除选定的矩形框
Ctrl++    放大
Ctrl--    缩小
↑→↓←        键盘箭头移动选定的矩形框

**具体事项**
想要修改图2中的标签类别内容（如默认的dog、person、cat等）则在主目录下data文件夹中的predefined_classes.txt文件中修改。
使用时，使用ctrl+u快捷键加载图片后，使用ctrl+r快捷键指定生成的xml文件的保存位置，然后开始按照类别将图片中的目标进行矩形框标注，每标注一个目标后软件自动弹出类别信息以供选择，在弹出的类别信息中选择对应的类别名称双击即可。当一张图片中各个类别所需要标注的目标全部标注后，点击保存按键或者使用ctrl+s快捷键保存就生成了相对应的xml位置信息文件，此时可以开始下一张图片的标注。