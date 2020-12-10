# Linux_docker_anaconda
Record various common and easy-to-forget command. 指令记录相关

# 目录
- [Linux下的环境安装](#Linux下的环境安装)
	- [anaconda安装](#conda安装)
	- [docker安装](#docker安装)
- [常用易忘指令汇总](#指令汇总)
	- [Linux指令](#Linux)
		- [tmux托管进程](#tmux)
		- [vim文本编辑器](#vim)
		- [proxychains代理](#proxychains)


# Linux下的环境安装
## conda安装
### 相关链接
1.[Anaconda使用总结](https://www.jianshu.com/p/2f3be7781451#) <br>
2.[conda国内镜像修改（最新版）](https://zhuanlan.zhihu.com/p/95100538) <br>
3.[更改pip源/anaconda源](https://blog.csdn.net/u012436149/article/details/66974668) <br>
<br>
PS:建议[阿里，清华源](https://blog.csdn.net/ljh_csdn_ljh/article/details/90294202)


## docker安装
pass<br>

# 指令汇总
## Linux指令
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
pass<br>

### proxychains
pass<br>
