# Common-Commands

docker命令
---------

`docker run --gpus all --entrypoint=/bin/bash \

-it -d -v [local mount dir]:[target dir in docker]\

-e TZ=Asia/Beijing --name [name] \

[docker image]` 

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
