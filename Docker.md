## 配置docker私人仓库
官方提供了一个registry镜像用于构建私人docker仓库
1. 拉取镜像
``` 
docker pull registry
```
2. 配置insecure-registries
```
vim /etc/docker/daemon.json
"insecure-registries": ["127.0.0.1:5000"]

重启docker服务
sudo systemctl daemon-reload
sudo systemctl restart docker
```
3. 启动镜像服务容器
```
docke run -d -p 5000:5000 --name registry docker.io/library/registry
```
4. push
```
docker tag hypeledger/fabric-ccenv:2.2.0 127.0.0.1:5000/fabric-ccenv:2.2.0
docker push 127.0.0.1:5000/fabric:2.2.0
```
5. pull
```
docker pull 127.0.0.1:5000/fabric:2.2.0
```
6. 查看仓库
> web: localhost:5000/v2/_catalog