## 远程使用jupyter 
通过SSH远程使用jupyter notebook   
1.&nbsp;在远程服务器启动jupyter notebook服务
> jupyter notebook --no-browser --port=****
2. &nbsp;在本机的Terminal中启动SSH
> ssh -N -f -L localhost:8888:localhost:**** remote_user@remote_host  

其中： -N 告诉SSH没有命令要被远程执行； -f 告诉SSH在后台执行； -L 是指定port forwarding的配置，远端端口是8889，本地的端口号的8888。remote_user@remote_host 用实际的远程帐户和远程地址替换  
3.&nbsp;打开浏览器，输入地址：http://localhost:8888/ 

## nodeJS

Node.js 就是运行在服务端的 JavaScript。

### 安装Node.js10

ubuntu18.04默认安装8.x的版本，在使用webpack过程中各种loader提示需要10.x+的支持

1. 添加NodeSource二进制分发存储库
> curl -sL https://deb.nodesource.com/setup_10.x | sudo bash

2. 安装
> sudo apt update
> sudo apt -y install gcc g++ make
> sudo apt -y install nodejs

3. 确认版本
$ node -v
v10.22.0
