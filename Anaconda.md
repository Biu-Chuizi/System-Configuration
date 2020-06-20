# [System-Configuration](https://github.com/John-Joe/System-Configuration)
在这里可以下载，推荐python3.6。(**Anaconda3-5.0.1-Linux-x86_64.sh**)
https://repo.anaconda.com/archive/

`conda list` 查看anaconda中已经安装的python的包
`conda install XXXX` 这个conda指令只能在anaconda文件夹中运行

启动图形界面
`source ~/anaconda3/bin/activate root`
 `anaconda-navigator`

卸载
`rm -rf ~/anaconda3`

pip只是包管理器，无法对环境进行管理。因此如果想在指定环境中使用pip进行安装包，则需要先切换到指定环境中，再使用pip命令安装包。pip无法更新python，因为pip并不将python视为包。pip可以安装一些conda无法安装的包；conda也可以安装一些pip无法安装的包。因此当使用一种命令无法安装包时，可以尝试用另一种命令。

基本操作
`conda update conda`
`conda create --name <env_name> <package_names>  ex: conda create -n python3 python=3.5 numpy pandas`
`conda --help/h`
`source activate <env_name>`
`source deactivate`
`conda info --envs / conda env list`
`conda create --name py2 --clone python2` ，即为克隆名为“python2”的环境，克隆后的新环境名为“py2”。
`conda remove --name <env_name> --all`
`conda search --full-name <package_full_name>`
`conda list`
`conda install --name python2 pandas `
`conda install <package_name>`

**导出已有环境及安装：**
**`conda env export > environment.yaml `**
**`conda env create -f environment.yaml`**

创建虚拟环境
基本命令为 conda create --name XXX，–name可缩写为-n

如果在创建虚拟环境时报错（跟urls.txt或者environments.txt有关，一般是第一次使用Anaconda时会出现），参考下方一些错误部分

关于创建虚拟环境，分以下三种情况陈述

**`conda create --name test1`**
此时虚拟环境并不起作用，进入test1后会发现实际上使用的依旧是本机Python环境，并且在test1中使用pip安装或者删除包均是对本机环境操作

所以不要使用这种方式

**`conda create --name test2 python=X.X.X`**
该命令会创建一个名为test2的纯净虚拟环境，并且会安装python X.X.X版本，无其他Python包。进入test2后，使用python -V和pip -V可以看到使用的的确是该虚拟环境，并且在test2中使用pip安装或者删除包均是对该虚拟环境进行操作，不会影响本机环境

这里python的入参有多种

如果只写python，则安装的是Anaconda自带的Python版本（在这里是3.6.5）

如果是python=2或者python=3，则安装的是python2或者python3的最新版本（目前是2.7.15和3.6.5）

如果写了二级版本号，例如python=2.6或者python=3.5，则安装的是python2.6或者python3.5分支的最新版本（目前是2.6.9和3.5.5）

如果写了最小的版本号，例如python=2.7.8或者python=3.6.2，则安装的便是输入的特定版本

**`conda create --name test3 python=2.7 numpy`**
该命令会创建一个名为test3的纯净虚拟环境，并且会安装python2.7的最新版本，在此基础上还会额外安装numpy包。当然numpy包也可以类似Python一样指定版本，例如numpy=1.10，则会安装1.10.4版本。不指定则安装的就是最新版本。其他同上

**`conda create --name test4 numpy`**
该命令会创建一个名为test4的纯净虚拟环境，并且会安装Anaconda自带的Python版本（在这里是3.6.5），在此基础上还会额外安装numpy包。其他同上