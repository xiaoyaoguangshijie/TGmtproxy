### 1、安装docker
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
```
```bash
sudo sh get-docker.sh
```
### 2、安装xdd
Debian：
```bash
apt-get install xxd
```
### 3、拉取镜像
```bash
docker pull ellermister/nginx-mtproxy:latest
```

### 4、自定义安装
获取secret
```bash
secret=$(head -c 16 /dev/urandom | xxd -ps)
```
查看secret
```bash
echo $secret
```
从 https://t.me/MTProxybot 获取tag
```bash
tag="123450c81a27491a867fad333a4e7dbd"
```
添加伪装
```bash
domain="cloudflare.com"
```
部署nginx-mtproxy 
```bash
docker run --name nginx-mtproxy -d -e tag="$tag" -e secret="$secret" -e domain="$domain" -e ip_white_list="OFF" -p 8080:80 -p 8443:443 ellermister/nginx-mtproxy:latest
```

docker logs nginx-mtproxy
