* [jupyter](#远程使用jupyter)
* [nodejs](#nodejs)
* [安装golang及配置环境](#安装golang及配置环境)
* [Postman](#postman)
* [mysql5.7安装](#mysql57安装)

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

## 安装golang及配置环境
1.下载
Golang官网下载地址：https://golang.org/dl/
国内用户推荐：https://studygolang.com/dl
2.解压
> tar -C /usr/local -zxvf  go1.11.5.linux-amd64.tar.gz
3.环境变量配置
```
# GOROOT配置
# 习惯用vim，没有的话可以用命令`sudo apt-get install vim`安装一个
vim /etc/profile
# 在最后一行添加
export GOROOT=/usr/local/go
export PATH=$PATH:$GOROOT/bin
# 保存退出后source一下（vim 的使用方法可以自己搜索一下）
source /etc/profile
```
4.工作空间配置
```
# 编辑 ~/.bashrc 文件
vim ~/.bashrc
# 在最后一行添加下面这句。$HOME/go 为你工作空间的路径，你也可以换成你喜欢的路径
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
# 保存退出后source一下（vim 的使用方法可以自己搜索一下）
source ~/.bashrc
```
5.工作空间目录结构    
go  
--pkg:编译包时，生成的.a文件的存放路径  
--bin:编译后可的执行文件的存放路径(go install)  
--src:源码路径，一般我们的工程就创建在src下面。  

## Postman
下载安装包之后解压到指定位置
1. 设置链接
> sudo ln -s /usr/postman/Postman/Postman /usr/bin/postman #为可执行文件设置链接，就不用再专门设置环境变量

2. 添加启动器应用图标  
```
//sudo vim /usr/share/applications/postman.desktop
[Desktop Entry]
 
Encoding=UTF-8
 
Name=Postman
 
Exec=postman
 
Icon=/usr/postman/Postman/app/resources/app/assets/icon.png
 
Terminal=false
 
Type=Application
 
Categories=Development;
```

## mysql5.7安装
1. apt install
```
sudo apt-get install mysql-server
```
2. 登录修改密码
```
sudo mysql
mysql>

mysql> use mysql;
mysql> select user,plugin,authentication_string from user;

mysql> update user set plugin = 'mysql_native_password' where user='root';
​
mysql> update user set authentication_string=PASSWORD('admin') where user='root';
```
3. 重启服务
```
sudo service mysql restart
```
