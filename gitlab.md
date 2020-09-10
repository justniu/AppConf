## 手动搭建gitlab服务

1.&nbsp;安装必要的依赖,邮件服务
```
sudo apt-get update
sudo apt-get install -y curl openssh-server ca-certificates tzdata

// email serve
sudo apt-get install -y postfix
```

2.&nbsp;添加gitlab源,并安装
```
// package-repository
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | sudo bash

// install
sudo EXTERNAL_URL="https://gitlab.example.com" apt-get install gitlab-ee
```
3.&nbsp;修改配置以及邮箱服务
```
vim /etc/gitlab/gitlab.rb

//修改ip以及端口
external_url 'http://xxx.xxx.xxx.xxx:xxxx'

//邮件服务配置
gitlab_rails['smtp_enable'] = true
gitlab_rails['smtp_address'] = 'smtp.qq.com'
gitlab_rails['smtp_port'] = 465
gitlab_rails['smtp_user_name'] = 'example@qq.com'
gitlab_rails['smtp_password'] = '************' //qq邮箱第三方授权码
gitlab_rails['smtp_domain'] = 'smtp.qq.com'
gitlab_rails['smtp_authentication'] = 'login'
gitlab_rails['smtp_enable_starttls_auto'] = true
gitlab_rails['smtp_tls'] = true
gitlab_rails['gitlab_email_from'] = 'example@qq.com'
```
### 问题
1.&nbsp;配置完成后第一次访问会默认进入重置密码界面，用户为root，但是会重置失败
> 等待一段时间后问题自动消失了？？？

2.&nbsp;在阿里云服务器配置gitlab服务是，需要注意配置安全组，打开端口

