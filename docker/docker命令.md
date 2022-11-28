## 常用命令
docker images查看本地镜像

docker pull下载镜像，docker rmi删除镜像，加-f强制删除，尽量先删除容器再删除镜像。

docker run启动镜像，-d表示后台运行，-P表示随机端口，-p指定端口映射

docker ps列出正在运行的镜像，-a列出所有容器，-f过滤，-q只列容器的id

docker version列出版本，docker info查看系统信息，例如cpu，内存，容器个数，

docker kill容器id，杀掉一个运行中的容器

docker start/stop/restart容器id，启动，停止，重启容器

docker build -t 标签名称 目录，-t表示指定一个标签

docker tag打标签

docker history 指定镜像创建历史

docker save指定镜像创建成tar文件

docker load导出镜像

docker import归档文件创建镜像

docker help查看命令操作

## 剩余命令（未知是否常用）

docker (un)pause(恢复)暂停容器中所有进程

docker create创建新容器但是不启动

docker exec在运行容器中执行命令

docker inspect获取容器元数据

docker top查看容器中运行的进程信息

docker attach连接到正在运行中的容器

docker events从服务器获取实时事件

docler logs获取日志

docker wait阻塞运行直到容器停止，然后打印退出代码

docker export导出为tar文件

docker port列出指定容器端口映射

docker commit从容器创建一个新的镜像

docker cp容器和主机之间数据拷贝

docker diff检查容器文件结构更改

docker login/logout登入登出镜像仓库

docker pull/push从镜像仓库拉取/上传指定镜像

docker search查找镜像



