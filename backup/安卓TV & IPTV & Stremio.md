## Android TV安装第三方应用
- U盘
- ADB调试
1. 开启开发者模式和ADB调试
2. 连接电视盒子
```
adb connect [电视盒子的IP地址]:[端口号]
```
3. 常用ADB命令
```
adb install [apk文件路径]  //安装应用
adb uninstall [应用包名]  //卸载应用 
adb shell  //进入系统目录
adb shell am start -n [包名]/[包名.类名]  //启动指定Activity
adb logcat  //查看日志
```
- 开心电视助手: [点击下载](https://mega.nz/file/jmRA0IDL#htpLPQidk9fVO8EqZFDpg8vC6zEtEPRoyFQCNxbLXP0)    
开心电视助手主要功能：
1. 图形化操作，小白也能轻松管理智能电视、电视盒子、投影仪等安卓设备；

2. 便捷安装第三方APK，远程截图，虚拟遥控器，一键去广告，优化系统，更加稳定流畅，支持刷第三方ROM固件；

3. 支持自定义加载bat批处理、py脚本等插件,比如免拆批量刷盒子，一键备份机顶盒系统固件;支持远程投屏、虚拟遥控、删除内置软件等功能。   
- mytv-android# 安卓TV电视直播软件：[点击前往](https://github.com/yaoxieyoulei/mytv-android)
mytv-android主要功能：
### 操作方式
> 遥控器操作方式与主流电视直播软件类似；
- 频道切换：使用上下方向键，或者数字键切换频道；屏幕上下滑动；
- 频道选择：OK键；单击屏幕；
- 设置页面：按下菜单、帮助键，长按OK键；双击、长按屏幕
### 触摸键位对应
- 方向键：屏幕上下左右滑动
- OK键：点击屏幕
- 长按OK键：长按屏幕
- 菜单、帮助键：双击屏幕
### 自定义设置
- 访问以下网址：`http://<设备IP>:10481`
- 打开应用设置界面，移到最后一项
- 支持自定义直播源、自定义节目单、缓存时间等等
- 须知：网页中引用了`jsdelivr`的cdn，请确保能够正常访问

### 自定义直播源
- 设置入口：自定义设置网址
- 格式支持：m3u格式、tvbox格式
## IPTV直播源
- IPTV项目: [点击前往](https://github.com/iptv-org/iptv)
- 范明明直播源 Github项目: [点击前往](https://github.com/fanmingming/live)
- IPTV-Checker: [点击下载](https://mega.nz/file/37JBjRqb#HhmPQeiNg5lZv1tfHTNOzDfh2CMuEg-75_CNsq-DkTY)  
- IPv6是否开启 : [点击检测](https://github.com/fanmingming/live)
- 自定义节目单
```
http://epg.51zmt.top:8000/e.xml.gz
```
## Stremio

<img src="https://www.stremio.com/website/desktop-app-mockup@2x.png" width="600" />

Stremio 提供安全、现代和无缝的娱乐体验。 Stremio 界面简单易用，内容丰富多样，支持 4K HDR，用户可以在所有设备上欣赏自己喜爱的电影和电视节目。 Stremio 还致力于安全，是用户获得无忧、高质量流媒体体验的不二之选。搭配插件使用(来源bt协议)：[点击前往](https://stremio-addons.netlify.app/)
- [Torrentio v0.0.14](https://stremio-addons.netlify.app/torrentio)
- [cyberflix-catalog](https://stremio-addons.netlify.app/cyberflix-catalog)
- [thepiratebay](https://stremio-addons.netlify.app/thepiratebay)
### BitTorrent (协议)
该技术由美国的程序员[布莱姆·科亨](https://zh.wikipedia.org/wiki/%E5%B8%83%E8%8E%B1%E5%A7%86%C2%B7%E7%A7%91%E4%BA%A8 "布莱姆·科亨")于2001年4月时发布，并于2001年7月2日时首次正式应用。BitTorrent协议（简称BT，俗称比特洪流、BT下载）是用在对等网络中文件分享的网络协议程序。和点对点（point-to-point）的协议程序不同，它是用户群对用户群（peer-to-peer），而且用户越多，下载同一文件的人越多，下载该档案的速度越快。且下载后，继续维持上传的状态，就可以“分享”，成为其用户端节点下载的种子文件（.torrent），同时上传及下载。  
1.基本原理
BitTorrent（简称BT）通过将大文件分割成多个小块来实现文件传输。每个下载者在下载文件的同时，也会将已下载的部分上传给其他下载者。这种方式不仅减轻了服务器的负担，还能加快下载速度。
2.种子文件
BT下载需要一个种子文件（.torrent），该文件包含了下载文件的元数据和Tracker服务器的信息。Tracker服务器负责协调和管理下载者之间的连接。
3.下载过程
获取种子文件：用户首先需要下载种子文件。
连接Tracker：BT客户端读取种子文件中的Tracker地址，并向Tracker服务器发送请求。
获取节点信息：Tracker服务器返回正在下载该文件的其他用户的IP地址。
数据交换：BT客户端与其他用户建立连接，交换各自已下载的文件块。
4.DHT技术
为了应对Tracker服务器故障，BT引入了DHT（分布式哈希表）技术。即使Tracker不可用，DHT网络也能帮助找到其他下载节点。
5.优点
高效利用带宽：下载的人越多，速度越快。
分散服务器压力：减轻了单一服务器的负担。
抗封锁能力强：通过加密协议和DHT技术，BT能有效应对网络封锁。
6.常见应用
BT技术广泛应用于大文件的分发，如软件、视频和游戏等。许多知名的BT客户端软件如uTorrent、BitTorrent和qBittorrent等都基于这一技术。