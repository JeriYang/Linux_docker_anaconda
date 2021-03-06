# Linux_docker_anaconda_git
Record various common and easy-to-forget command. 指令记录相关

# 目录
- [Linux下的环境安装](#Linux下的环境安装)
	- [anaconda安装](#conda安装)
	- [docker安装](#docker安装)
	- [gpu安装](#gpu安装)
- [常用易忘指令汇总](#指令汇总)
	- [Linux指令](#Linux)
		- [tmux托管进程](#tmux)
		- [vim文本编辑器](#vim)
		- [proxychains代理](#proxychains)
		- [GPU相关信息](#GPU)
	- [Git指令](#Git)


# Linux下的环境安装
## conda安装
### 相关链接
1.[Anaconda使用总结](https://www.jianshu.com/p/2f3be7781451#) <br>
2.[conda国内镜像修改（最新版）](https://zhuanlan.zhihu.com/p/95100538) <br>
3.[更改pip源/anaconda源](https://blog.csdn.net/u012436149/article/details/66974668) <br>
<br>
PS:建议[阿里，清华源](https://blog.csdn.net/ljh_csdn_ljh/article/details/90294202)
[jupyter增加多版本python内核](https://blog.csdn.net/flyer_tang/article/details/81305087)

步骤：<br>
1）用户页面建立隐藏的local文件夹：

    mkdir .local

2）运行anaconda.sh安装包文件：

    bash anaconda.sh
    /home/username/.local/anaconda  # 自定义路径部分
    #安装完成后，重启远程链接
    #使用conda测试

3）建立conda环境：

    # 创建一个名为python34的环境，指定Python版本是3.4（不用管是3.4.x，conda会为我们自动寻找3.x.x中的最新版本）
    conda create --name python34 python=3

4）安装好后，使用activate激活某个环境：

    activate python34 # for Windows
    source activate python34 # for Linux & Mac
    
    # 删除一个已有的环境
    conda remove --name python34 --all
    
    # 如果想返回默认的python 2.7环境，运行
    deactivate python34 # for Windows
    source deactivate python34 # for Linux & Mac

5）更换源：

    # 先查看已经安装过的镜像源，执行命令：
    conda config --show
    # 查看配置项channels，如果显示带有tsinghua，则说明已安装过清华镜像。
    # 下一步，使用conda config --remove channels url地址删除清华镜像，如下命令删除第一个。然后，依次删除所有镜像源
    conda config --remove channels https://mirrors.tuna.tsinghua.edu.cn/tensorflow/linux/cpu/
    添加目前可用的中科大镜像源：
    conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
    并设置搜索时显示通道地址：
    conda config --set show_channel_urls yes

6）conda相关命令

    # 查看conda环境：
    conda info --envs
    conda env list
    
## docker安装
pass<br>

## gpu安装
查看cuda()是否可以使用：

    import torch
    device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")
    # Assume that we are on a CUDA machine, then this should print a CUDA device:
    print(device)

# 指令汇总
## Linux
### tmux
启动新会话：

    tmux [new -s 会话名 -n 窗口名]

恢复会话：

    tmux at [-t 会话名]

列出所有会话：

    tmux ls

退出托管页面：

	Ctrl + B, 松开, + D

<a name="killSessions"></a>关闭会话：

    tmux kill-session -t 会话名

<a name="killAllSessions"></a>关闭所有会话：

    tmux ls | grep : | cut -d. -f1 | awk '{print substr($1, 0, length($1)-1)}' | xargs kill


### vim
1.退出编辑器：

    wq：保存当前文件并退出
    wqa：保存所有文件并退出
    q!： 不保存，强制退出
    qa!： 有多个文件被打开，同时退出

2.移动光标：

    j：向下
    20j： 向下移动 20 行
    k：向上
    h：向左
    l：向右
    0：到行首
    ^：到行首第一个字符，如果前面有空格的话
    $：到行尾
    gg：快速到文件头
    G：快速到文件尾
    50G：跳转到第 50 行

### proxychains
pass<br>

### GPU

    nvidia-smi：查看本机GPU状态
    
    watch -n 1 nvidia-smi：实时监控GPU的使用情况。其中1是动态刷新的时间间隔
    
    ps -aux：这个指令可以看到当前服务器下的各种信息

## Git
Git global set up

    git config --global user.name 'jeriYang'
    git config --global user.email 'xxx@gmail.com'

Git global set up

    git clone http://gitlab.alibaba-inc.com/tjxxx/hpxxx.git
    cd hpxxx
    touch README.md
    git add README.md
    git commit -m "add README"
    git push -u origin master
 
 Existing folder or Git repository

    cd existiong_folder
    git init
    git remote add origin http://gitlab.alibaba-inc.com/tjxxx/hpxxx.git
    git add .
    git commit -m "push的描述"
    git push -u origin master

Pull相关操作

    git pull origin master ： 相当于是从远程获取最新版本并merge到本地
    
Readme.md添加图片

    ![image](图片地址)
   
