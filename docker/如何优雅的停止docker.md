使用docker stop和docker kill命令直接停止的，并不优雅

##### init系统的特点
启动守护进程。回收孤儿进程。将操作系统信号转发给子进程。

#### docker容器停止过程
对于容器来说init系统不是必须的，通过命令docker stop mycontainer停止容器时，docker CLI将==TERM==信号发送给mycontainer进程的==PID==为1的进程

##### 如果PID 1是init进程，
将TERM信号转发给子进程，然后子进程开始关闭，容器停止

##### 如果没有init进程
容器中的应用程序ENTRYPOINT或者CMD指定的应用就是PID 1，应用进程直接负责响应TERM信号，其中有==两种==结果：

###### 1.应用不处理SINTERM
应用没有监听SINTERM信号，或者应用中没有实现处理SINTERM信号的逻辑，就不会停止，容器也不会终止

###### 2.容器停止时间很长
运行命令docker stop mycontainer，docker等待10s，如果10s后容器没有停止，docker会绕过应用直接向内核发送SINKILL，内核会强行杀死应用，从而停止进程。

#### 容器进程收不到SINTERM信号
很可能是应用进程不是PID 1，PID 1是shell，而应用进程是shell的子进程，而shell不具备init系统的功能，不会将操作系统的信号转发到子进程，是常见的没收到SINTERM信号的原因。

问题根源来自dockerfile，ENTRYPOINT指令使用的是shell模式，docker会把应用放到shell中运行，因此shell是PID 1

##### 解决方案
###### 1.使用exec模式的ENTRYPOINT指令。

PID 1 将负责响应所有发送到容器的信号，至于是否真的能捕捉到信号是另一码事，

停止时，因为没实现捕获和处理SINTERM信号的逻辑，需要10s左右才能停止容器，解决这个问题往里面添加信号处理代码，让他捕获到SINTERM信号时就终止进程。

###### 2.直接使用exec命令
想使用 shell 模式的 ENTRYPOINT 指令，也不是不可以，只需将启动命令追加到 exec 后面即可

exec 就会将 shell 进程替换为 ./popcorn.sh 进程，PID 1 仍然是 ./popcorn.sh

###### 3.使用init系统
如果容器中的应用默认无法处理 SIGTERM 信号，又不能修改代码，这时候1,2无法使用，只能往里添加一个init系统

安装 tini

将 tini 设为容器的默认应用

将 popcorn.sh 作为 tini 的参数

现在 tini 就是 PID 1，它会将收到的系统信号转发给子进程 popcorn.sh
