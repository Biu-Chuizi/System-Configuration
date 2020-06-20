### 总纲#5

现在pytorch在论文发布时使用率已经和tensorflow持平，并且代码更为简洁，推荐一下。
`pip install torch torchvision`
如果这里出现pip的permission问题，那是环境变量和anaconda安装有问题，可以执行以下指令安装pytorch
`sudo anaconda3/bin/pip install torch torchvision`
进入python编辑模式，输入以下指令检验GPU是否可用：
`import torch`
`print(torch.cuda.is_available())`

**Reference**
https://zhuanlan.zhihu.com/p/48082080
