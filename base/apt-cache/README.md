https://soulteary.com/2021/04/12/use-docker-to-build-apt-cacher-ng-caching-proxy-service.html

##  Ubuntu / Debian 设置APT代理
```
echo "Acquire::http::proxy \"http://YOUR_HOST_DOMAIN_OR_IP\";" > /etc/apt/apt.conf.d/00aptproxy

```


## 容器内使用
```
docker run --rm -it -e http_proxy=http://YOUR_HOST_DOMAIN_OR_IP ubuntu:20.04 bash
sed -i 's/http:\/\/.*.ubuntu.com/http:\/\/mirrors.tuna.tsinghua.edu.cn/' /etc/apt/sources.list
apt update && apt upgrade -y && apt install -y apt-transport-https  ca-certificates curl software-properties-common
curl -fsSL https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/ubuntu/gpg  | apt-key add -
add-apt-repository "deb http://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
apt install -y docker-ce

```

## 查看控制台
/acng-report.html