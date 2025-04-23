**好消息！低显存显卡也能玩转AI视频生成，斯坦福团队发布FramePack新技术，仅需6GB显存即可生成60秒高清视频**

GitHub开发者 Lvmin Zhang 与斯坦福大学教授 Maneesh Agrawala 联合发布了一项颠覆性的AI视频生成技术——**FramePack**。该方法通过引入**固定长度的时域上下文（Temporal Context）**，大幅降低显存与算力需求，使得普通硬件也能胜任高质量视频的生成任务。

![](https://www.freedidi.com/wp-content/uploads/2025/04/bbd7268f5d20250423120658.webp)

在实测中，研究人员使用基于 FramePack 的 130 亿参数模型，仅借助一块**6GB 显存的显卡**，就成功生成了**时长达 60 秒**的视频，性能表现令人惊艳。
![](https://www.freedidi.com/wp-content/uploads/2025/04/f51e897ff020250423120713.webp)

要求：

- Nvidia GPU RTX 30XX、40XX、50XX 系列支持 fp16 和 bf16。GTX 10XX/20XX 未经测试。
- Linux 或 Windows 操作系统。
-  6GB GPU 内存。

### 开源项目：【[点击前往](https://github.com/lllyasviel/FramePack)】

1、一键安装包：【**[点击下载](https://github.com/lllyasviel/FramePack/releases/tag/windows)**】

2、CUDA 引擎：【**[点击下载](https://developer.nvidia.com/cuda-toolkit)**】

3、N卡驱动：【**[点击下载](https://www.nvidia.cn/geforce/drivers/)**】、或【**[海外版](https://www.nvidia.com/en-us/geforce/drivers/)**】

下载后，解压，使用update.bat更新，使用run.bat运行。请注意，运行update.bat很重要，否则您可能会使用未修复潜在错误的先前版本。

运行后模型将自动下载。您将从 HuggingFace 下载超过 30GB 的数据。

### ✅ FramePack 的核心优势：

- **固定时域上下文**：不同于传统视频扩散模型随着帧数增加而显存需求暴涨，FramePack 会自动分析输入帧的重要性，进行压缩处理，将输入统一转换为固定长度的上下文，有效控制资源占用。
    
- **显存占用低**：计算量与图像扩散模型相当，大幅减少硬件门槛。
    
- **实时预览支持**：每一帧生成后可立即显示，便于随时调整。
    
- **解决漂移问题**：有效缓解视频长度增加后画面质量下降的“drifting”问题，实现**更长、更稳、更清晰**的本地视频生成。
    

### 🧠 技术架构与兼容性：

FramePack 本质上是一种**多级优化的神经网络架构**，目前底层采用的是定制化的腾讯混元模型。但更关键的是，它对**市面上已有的预训练扩散模型也具备良好的兼容性与适配能力**，便于进行迁移学习与个性化微调。

### 💻 硬件与系统支持一览：

- **显卡要求**：支持 FP16、BF16 精度，兼容 RTX 30、40、50 系列显卡（除 RTX 3050 4GB 外基本全覆盖）。RTX 20 系列及更早版本尚未验证，暂不支持 AMD 或 Intel GPU。
    
- **系统支持**：兼容 Windows 与 Linux 系统，部署灵活。
    
- **性能表现**：在 RTX 4090 上经 Teacache 优化后，**生成速度可达每秒 0.6 帧**，效率不俗。
    

---

这项技术的推出，或将彻底改变AI视频创作的门槛：不再需要高端工作站，仅凭一块入门显卡，人人都可以打造专属的AI视频。

**Linux 安装步骤**：

我们建议拥有独立的 Python 3.10。
```
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126
pip install -r requirements.txt
```
要启动 GUI，请运行：
```
python demo_gradio.py
```
