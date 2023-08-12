## 镜像源、常用软件
```
cp /etc/apt/sources.list /etc/apt/sources.list.backup
cat <<EOF > /etc/apt/sources.list
  deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
  deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse

  deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
  deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse

  deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
  deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse

  deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse
  deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse
EOF
apt update && apt upgrade -y
apt install language-pack-zh-hant language-pack-zh-hans -y
apt install git zsh wget curl unzip vim -y
```

## 安装docker、docker
### 常规安装 
https://www.python100.com/html/118934.html

```
apt-get install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
apt update
apt install docker-ce
apt install docker-compose
chmod +x /usr/local/bin/docker-compose
systemctl start docker
```


### 使用苏洋的APT加速服务
```
curl http://dist.lab.com/docker.gpg|apt-key add -add-apt-repository "deb http://cache.lab.com/mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/ubuntu$(lsb_release -cs) stable"
apt install -y docker-ce
curl -L http://dist.lab.com/docker-compose-o/usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
mkdir -p /etc/docker && touch /etc/docker/daemon.json
cat <<EOF > /etc/docker/daemon.json
  {
  "registry-mirrors": [
  "https://YOUR.MIRRORS"
    ]
  }
EOF
```