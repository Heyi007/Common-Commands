# Common-Commands

docker命令
---------
从镜像启动容器

    $ docker run --ipc host --gpus all --entrypoint=/bin/bash \
    $ -it -d -v [local mount dir]:[target dir in docker] -p [ip]:[port]:[target port]\
    $ -e TZ=Asia/Beijing --name [name] [docker image]
    
删除本地镜像

    $ docker image rm [image]
    
将容器提交为镜像

    $ docker commit -m "message" -a "heyi" container_id [repo[:TAG]]
    $ example docker commit -m "horovod-tensorflow2.1.0-pytorch1.4.0-cuda10" -a "heyi" 8d5cf23df4ad [docker repo address]
    

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
[看官方文档，看官方文档，看官方文档](https://github.com/horovod/horovod#running-horovod)（重说三！！！）

人生苦短，请用Docker，最简单的安装方法，使用Horovod官方给的[Docker镜像](https://github.com/horovod/horovod/blob/master/docs/docker.rst)。

直接从Docker官方仓库拉取大型镜像不可取，需要配置[镜像加速](https://developer.aliyun.com/article/752958?spm=a2c6h.14164896.0.0.165bbf44ErrAfl)。

保险起见，需要安装[Nvidia-Docker](https://github.com/NVIDIA/nvidia-docker)。

vim8原生插件管理使用
----------------------
`mkdir ~/.vim/pack/[name]/[start, opt]`

`:helptags ~/.vim/pack/[name]/[start, opt]`

`:helptags ALL`

NerdTree使用方法：

NERDTree的常用快捷键，[详细命令](https://www.jianshu.com/p/28bd9def1235)：

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


