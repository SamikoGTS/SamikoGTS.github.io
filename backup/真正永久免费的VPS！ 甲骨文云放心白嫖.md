![](https://www.freedidi.com/wp-content/uploads/2024/11/a1c5ea586620241106160045.webp)
不同地区注册甲骨文云服务器的页面链接是不一样的，具体注册链接如下：

大陆：【[链接直达](https://www.oracle.com/cn/cloud/free/)】

台湾：【[链接直达](https://www.oracle.com/tw/cloud/free/)】

美国：【[链接直达](https://www.oracle.com/cloud/free/)】

澳洲：【[链接直达](https://www.oracle.com/au/cloud/free/)】

日本： 【[链接直达](https://www.oracle.com/jp/cloud/free/)】

韩国： 【[链接直达](https://www.oracle.com/kr/cloud/free/)】

更多地区，稍后补充……

1.WindTerm 远程终端连接器：【[官方下载](https://github.com/kingToolbox/WindTerm/releases/tag/2.5.0)】、【[备用下载](https://www.dongli7.com/thread-151-1-1.html) 】

2.开放端口：
```
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -F
```
3.部署代理节点

比如一键安装SSR

wget -N --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh
chmod +x shadowsocksR.sh
./shadowsocksR.sh
 

一键安装OpenVPN
```
wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh
```
或者一键安装V2ray等
```
apt update
apt install -y git  ### 安装 git 环境
wget -N --no-check-certificate -q -O install.sh "https://raw.githubusercontent.com/wulabing/V2Ray_ws-tls_bash_onekey/dev/install.sh" && chmod +x install.sh && bash install.sh
```
4.如果你担心网站使用率不高被回收，可以配合保活脚本【[开源脚本](https://github.com/spiritLHLS/Oracle-server-keep-alive-script)】、【[网盘下载](http://pan.tuio.cc/s/lJxCp)】：
```
bash <(wget -qO- --no-check-certificate https://gitlab.com/spiritysdx/Oracle-server-keep-alive-script/-/raw/main/oalive.sh)
```
© 版权声明
文章版权归作者所有，未经允许请勿转载。