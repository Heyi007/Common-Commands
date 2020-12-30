# Common-Commands

使用gdb调试python底层错误
-----------
注意：在docker中启用gdb调试需要在启动container时指定--cap-add和--security-opt选项，详见docker命令部分。

[gdb调试python教程1](https://wiki.python.org/moin/DebuggingWithGdb)

[gdb调试python教程2](https://confluence.desy.de/display/FSEC/Debugging+Python#:~:text=If%20the%20python%20macros%20return,attached%20to%20the%20same%20process.)

#### 两种启动gdb的方法:

1.直接启动

    $ gdb -ex r --args python your-python-file --[python-file args]
    
2.启动python脚本后，attach gdb到其所在的进程：

    $ gdb -p python-pid
    
    
#### 常用的gdb命令：
```
c continues execution (Ctrl + C stops it again)
bt prints the C stack trace
py-bt prints the Python stack trace
py-bt-full prints both
py-list lists the current Python source code
py-up/py-down moves one Python frame up or down
py-locals shows local variables in the current frame
py-print <var> prints the representation of a variable in the current frame
info threads displays all threads
thread <id> switches current thread to thread number <id>
thread apply all <cmd> applies <cmd> to all threads, e.g., thread apply all py-list
python MAX_OUTPUT_LEN=<N> sets the length after which the output of a Python value is truncated (default is 1024)
```

#### 抓取core的方法（未经测试）

1. 使用 ulimit -c 查看core开关，如果为0表示关闭，不会生成core文件；

2. 使用 ulimit -c [filesize] 设置core文件大小，当最小设置为4之后才会生成core文件；

3. 使用 ulimit -c unlimited 设置core文件大小为不限制，这是常用的做法；

```
1. Find the pid:
pgrep -af <name>
2. Generate core dump:
gcore <pid>
This will stop the program while creating the core dump, which might take a few seconds.
3. Start the debugger:
gdb python <core_file> or gdb python3 <core_file>, depending on the programs Python version
4. Use the usual gdb commands to investigate the state of the program, see above.
```

docker命令
---------

linux内核或显卡驱动升级后，docker启动失败解决方法：
[更新yum](https://github.com/NVIDIA/nvidia-docker/issues/836#issuecomment-428450111)
[安装nvidia-container toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker)

从镜像启动容器

    $ docker run --ipc host --gpus all --entrypoint=/bin/bash \
    $ -it -d -v [local mount dir]:[target dir in docker] -p 0.0.0.0:[port]:[target port]\
    $ -e TZ=Asia/Beijing --name [name] [docker image]

启动gdb调试

    $ docker run --cap-add=SYS_PTRACE --security-opt seccomp=unconfined
    
删除本地镜像

    $ docker image rm [image]
    
将容器提交为镜像

    $ docker commit -m "message" -a "heyi" container_id [repo[:TAG]]
    $ example docker commit -m "horovod-tensorflow2.1.0-pytorch1.4.0-cuda10" -a "heyi" imageid [docker repo address]
    

git 命令
--------

拉取远端代码并强制覆盖本地代码
`git fetch --all`
`git reset --hard origin/master`

查看是否有远程关联仓库
`git remote -v ` 

添加远程关联仓库
```git remote add origin [git address]```

删除远程关联仓库
`git remote rm origin`

上传代码
`git push origin master`

拉取代码
`git pull origin master`

tmux 命令
---------

新建会话
`tmux new -s [name]`

连接会话
`tmux a -t [name]`

断开会话
`tmux detach`

pdb命令
-------------

打印 `pp`

下一步执行 `n`

步进 `s`

列出 `l`

继续执行 `c`

返回 `r`

CUDA
-------
查看CUDA版本号

`cat /usr/local/cuda/version.txt`

查看cuDNN版本号

`cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2`

Horovod安装方法
------------------
[看官方文档](https://github.com/horovod/horovod#running-horovod)

最简单的安装方法，使用Horovod官方给的[Docker镜像](https://github.com/horovod/horovod/blob/master/docs/docker.rst)。

直接从Docker官方仓库拉取大型镜像不可取，需要配置[镜像加速](https://developer.aliyun.com/article/752958?spm=a2c6h.14164896.0.0.165bbf44ErrAfl)。

保险起见，需要安装[Nvidia-Docker](https://github.com/NVIDIA/nvidia-docker)。

[vim8原生插件管理使用](https://blog.csdn.net/qq_27825451/article/details/100557133)
----------------------
`mkdir ~/.vim/pack/[name]/[start, opt]`

`:helptags ~/.vim/pack/[name]/[start, opt]`

`:helptags ALL`

NerdTree使用方法：

NERDTree的常用快捷键，[详细命令](https://www.jianshu.com/p/28bd9def1235)：
```
F3：自定义启用/隐藏目录树

?: 快速帮助文档

o: 打开一个目录或者打开文件，创建的是buffer，也可以用来打开书签

go: 打开一个文件，但是光标仍然留在NERDTree，创建的是buffer

t: 打开一个文件，创建的是Tab，对书签同样生效

T: 打开一个文件，但是光标仍然留在NERDTree，创建的是Tab，对书签同样生效

i: 水平分割创建文件的窗口，创建的是buffer

gi: 水平分割创建文件的窗口，但是光标仍然留在NERDTree

s: 垂直分割创建文件的窗口，创建的是buffer

gs: 和gi，go类似

x: 收起当前打开的目录

X: 收起所有打开的目录

e: 以文件管理的方式打开选中的目录

D: 删除书签

P: 大写，跳转到当前根路径

p: 小写，跳转到光标所在的上一级路径

K: 跳转到第一个子路径

J: 跳转到最后一个子路径

和: 在同级目录和文件间移动，忽略子目录和子文件

C: 将根路径设置为光标所在的目录

u: 设置上级目录为根路径

U: 设置上级目录为跟路径，但是维持原来目录打开的状态

r: 刷新光标所在的目录

R: 刷新当前根路径

I: 显示或者不显示隐藏文件

f: 打开和关闭文件过滤器

q: 关闭NERDTree

A: 全屏显示NERDTree，或者关闭全屏
```

pip使用清华源
-----------------
#### 临时使用

    $ pip install -i https://pypi.tuna.tsinghua.edu.cn/simple some-package

#### 设为默认（推荐）

```
pip install pip -U
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```
