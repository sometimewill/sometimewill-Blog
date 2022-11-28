docker容器是完全使用沙箱机制，相互之间不会有任何接口（类似 iPhone 的 app）,更重要的是容器性能开销极低。

##### 应用场景

web应用自动打包和发布

自动化测试和持续集成，发布

服务型环境部署，调整数据库和其他后台应用

##### docker优点
docker是一个开发，交付，运行应用程序的开放平台，能够将应用程序和基础架构区分开，从而快速交付软件

1.快速一致的交付应用程序

2响应式部署和扩展

3在同一硬件上运行更多工作负载

##### 启动容器
CONTAINER ID 容器ID

IMAGE使用的镜像

COMMAND启动容器时运行的命令

CREATED容器的创建时间

STATUS容器状态
七种状态：
created（已创建）
restarting（重启中）
running 或 Up（运行中）
removing（迁移中）
paused（暂停）
exited（停止）
dead（死亡）

PORTS 容器端口信息和使用的连接类型(tcp/udp)

NAMES 自动分配的容器名称

##### 停止容器
docker stop停止容器
