//TODO 学习记录
## 学习记录

 我们这次尝试着用vscode的remote ssh远程连接访问我们自己的linux服务器
首先我们得在本地的vscode中安装好需要的ssh remote插件

>这个软件只是一个应用的封装,具体能不能实现我们可以通过windows自带的powershell里面去看能不能用

### step1
我们安装完需要的插件后,去到我们linux系统,将我们的ssh服务打开,具体命令有
```sudo pacman -S ssh-service``` (没有的话得安装)

用 ```sudo systemctl status sshd``` 来查看我们的ssh服务有没有开启,
如果没有开启(也就是unable的状态的话),需要输入命令 ```sudo systemctl start sshd``` ,
如果需要开机自启动ssh服务的话,还可以输入命令 ```sudo systemctl enable sshd``` .

### step2
这样一来,linux这边的ssh服务设置已经大功告成,我们接下来需要输入命令 ```ip addr``` 来获取我们的linux服务器对应的ip地址,注意不是127.0.0.1,而是enp0s8旁边的(不一定是这个,但是名字应该很接近的).

我们切换到windows系统上,```win + r``` 输入 ```services.msc```,在里面寻找 ```OpenSSH SSH Server``` 打开服务,没有的话请参考[这个网站](https://blog.csdn.net/weixin_41601114/article/details/108052922?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170376401616800184126758%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170376401616800184126758&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-108052922-null-null.142^v99^pc_search_result_base2&utm_term=windows%20%E6%B2%A1%E6%9C%89openssh&spm=1018.2226.3001.4187)的教程去开启.

接下来我们在windows power shell 中输入命令 ```ping xxx.xxx.xxx.xxx```,  ip 填刚刚自己的ip地址即可,
如果能ping通,那么我们接下来输入命令```ssh user_name@xxx.xxx.xxx.xxx```,user_name填linux用户名即可,后面一样填ip地址.
输完密码后成功,那么就大功告成了.

step3

如果出现error, 报错显示```permission denied```,那么你陷入了比较麻烦的错误中,我也遇到了该麻烦.我讲一讲我自己的解决方案,你们可以参考一下.

首先我们得查看我们的windows系统的ip地址,如果你的linux系统的ip子网和windows的,那么我们得去虚拟机设置里面将额外添加一个桥接网络的网卡设置,然后跳转到```ip addr``` ,查看新的ip地址,将其作为ssh的新ip地址去试试.我这样设置以后成功连接了.




