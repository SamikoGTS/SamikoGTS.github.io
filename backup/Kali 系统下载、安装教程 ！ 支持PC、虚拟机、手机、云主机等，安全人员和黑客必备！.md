![](https://www.freedidi.com/wp-content/uploads/2025/01/649cf3e01920250123143323.webp)

1、Kail 官方下载：【[点击前往](https://www.kali.org/)】

2、Kail 手机版下载：【[点击前往](https://www.kali.org/get-kali/#kali-mobile)】

3、Kail 虚拟机版：【[点击前往](https://www.kali.org/get-kali/#kali-virtual-machines)】

3、虚拟机下载：【[VMware](https://www.freedidi.com/6937.html)】、【[VirtualBox](https://www.virtualbox.org/)】

这两款虚拟机都是完全免费的，而且支持Windows、Mac、Linux，根据自己喜爱下载使用！

Kali Linux是基于Debian的Linux发行版，设计用于数字鉴识和渗透测试。由Offensive Security公司维护和资助。

Kali Linux内置了大约600个渗透测试程序（工具），包括Armitage（图形化网络攻击管理工具）、Nmap（端口扫描工具）、Wireshark（数据包分析器）、Metasploit（渗透测试框架）、John the Ripper（密码破解器）、sqlmap（自动SQL注入和数据库接管工具）、Aircrack-ng（用于渗透测试无线局域网的软件包）、Burp suite以及OWASP ZAP网络应用安全扫描器等。

默认情况下， Kali 系统的语言是英文的，如果你需要将Kali系统设置为中文语言，那么可以通过下方步骤来实现：

1、打开终端，更新系统包列表：
```
sudo apt-update
sudo apt-upgrade
```
2、安装中文语言包：
```
sudo apt-get install locales
```
3、生成中文语言环境（以zh_CN.UTF-8为例）：
```
sudo dpkg-reconfigure locales
```
在出现的界面中，选择 zh_CN.UTF-8，通常通过空格选择。
![](https://www.freedidi.com/wp-content/uploads/2025/01/160351-.png)

确认后，在出现的界面中可以看到 zh_CN.UTF-8，右键选中OK，确认，如下图。
![](https://www.freedidi.com/wp-content/uploads/2025/01/160358-.png)

4、更新系统区域设置：
```
sudo locale-gen zh_CN.UTF-8
```
5、应用中文设置：
```
sudo update-locale LANG=zh_CN.UTF-8
```
6、重新登录或重启Kali Linux，以使配置生效。
