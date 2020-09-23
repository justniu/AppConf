## 远程使用jupyter 
通过SSH远程使用jupyter notebook   
1.&nbsp;在远程服务器启动jupyter notebook服务
> jupyter notebook --no-browser --port=****
2. &nbsp;在本机的Terminal中启动SSH
> ssh -N -f -L localhost:8888:localhost:**** remote_user@remote_host
