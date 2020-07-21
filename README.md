# Common-Commands

docker命令
---------
从镜像启动容器

    $ docker run --gpus all --entrypoint=/bin/bash \
    $ -it -d -v [local mount dir]:[target dir in docker]\
    $ -e TZ=Asia/Beijing --name [name] [docker image]

git 命令
--------

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

pdb命令
-------------

打印 `pp`

下一步执行 `n`

步进 's'

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

NERDTree的常用快捷键：

h j k l移动光标定位

ctrl+w+w 光标在左右窗口切换

ctrl+w+r 切换当前窗口左右布局

ctrl+p 模糊搜索文件

gT 切换到前一个tab

g t 切换到后一个tab

o 打开关闭文件或者目录，如果是文件的话，光标出现在打开的文件中

O 打开结点下的所有目录

X 合拢当前结点的所有目录

x 合拢当前结点的父目录

i和s水平分割或纵向分割窗口打开文件

u 打开上层目录

t 在标签页中打开

T 在后台标签页中打开

p 到上层目录

P 到根目录

K 到同目录第一个节点

J 到同目录最后一个节点

m 显示文件系统菜单（添加、删除、移动操作）

? 帮助

:q 关闭
