# spacevim

系统： ubuntu 20.04

（目前还未完成，在使用docker配置的时候出问题了）

## 安装
1. 需要先安装git, curl
```
sudo apt-get install curl
sudo apt-get install git
```

2. 安装spacevim
```
curl -sLf https://spacevim.org/cn/install.sh | bash -s -- --install vim
```

3. 安装docker
```
sudo apt-get install docker.io  (可能还需要安装docker)
sudo usermod -a -G docker $user  (注意user用户需要重新登录才可以使用docker)
```

4. docker支持
```
docker pull spacevim/spacevim
docker run -it --rm spacevim/spacevim nvim
```


## link
_**1. [SpaceVim](https://spacevim.org/cn/quick-start-guide/)**_  
_**2. [在 Linux 上安装和使用 Docker](https://linux.cn/article-9352-1.html)**_  
