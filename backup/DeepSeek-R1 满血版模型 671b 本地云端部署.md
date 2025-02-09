DeepSeek-R1 虽然有1.5b、7b、8b、14b、32b等，但是这些都是量化版，非满血版，真正和官方一样的满血版只有一个，那就是未量化的 671b DeepSeek-R1 大模型！是目前最强最聪明的一个开源模型。

![](https://www.freedidi.com/wp-content/uploads/2025/02/5cdc4f669a20250208143411.webp)

DeepSeek-R1 满血开源版下载： 【**[点击前往](https://huggingface.co/deepseek-ai/DeepSeek-R1)**】

本地部署的最低硬件要求：
```
CPU：32核Intel Xeon或AMD EPYC

内存：512GB RAM  

GPU：4块NVIDIA A100（80GB显存）

硬盘：2TB NVMe SSD

网络：10Gbps带宽
```
这是官方给出的默认硬件配置，大家可以看下我的硬盘是2T的，安装后只剩下399G

![](https://www.freedidi.com/wp-content/uploads/2025/02/3f665e739620250208143805-scaled.webp)

虽然我的内存只有64G，跟官方要求的512G相差甚远，那么我们可不可以使用虚拟内存来凑呢？相信很多人都想到这里，就用硬盘换内存，这个我会在视频里给大家实际验证！

本地安装满血版 Deepseek R1 模型步骤：

1、安装 Ollama 【**[点击前往](https://ollama.com/)** 】

2、下载并部署 671b Deepseek R1 模型：
```
ollama run deepseek-r1:671b
```
3、UI 调用模型 【**[点击安装](https://chromewebstore.google.com/detail/page-assist-%E6%9C%AC%E5%9C%B0-ai-%E6%A8%A1%E5%9E%8B%E7%9A%84-web/jfgfiigpkhlkbnfnbobbkinehhfdhndo)** 】

如何卸载已安装过的模型？
```
ollama list  # 查询已安装的模型
ollama rm 模型名称  # 卸载并删除模型
```
4、土豪套餐 【云端部署】

在云端部署真正满血版的671b Deepseek R1 模型，需要你钱包够硬，在线开通高级的云GPU

在线开通专业级云GPU：【**[点击前往](https://www.vultr.com/?ref=9667930-9J)**】

这里看我操作就行，别盲目跟从，价格都是按小时计费的，不便宜，当然土豪们可以无视！

![](https://www.freedidi.com/wp-content/uploads/2025/02/98b8ddd6cf20250208144949.webp)

我会选择8张H100，640G显存，地址只能选芝加哥才有货

![](https://www.freedidi.com/wp-content/uploads/2025/02/5db78144c920250208145303-scaled.webp)

成功部署效果:

![](https://www.freedidi.com/wp-content/uploads/2025/02/5ccfc7cc2320250208145407-scaled.webp)

云端部署 deepseek-r1-671b 命令：
```
curl -fsSL https://ollama.com/install.sh | sh
ollama create deepseek-r1-671b --model deepseek/deepseek-r1-671b
```
然后通过Open-WebUI 来调用deepseek-r1-671b 模型，安装命令如下：
```
docker run -d -p 8082:8080 -v open-webui:/app/backend/data --name Open-WebUI --restart always ghcr.io/open-webui/open-webui:main
```
然后访问 http:// 服务器IP:8082，打开后在 Open-WebUI **“Models”** 设置中，添加 `deepseek-r1`，即可使用！

如果服务器有防火墙，记得开放 8082端口，否则外网无法访问