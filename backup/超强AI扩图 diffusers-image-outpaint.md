**前言**：Diffusers Image Outpaint 技术，是一种基于扩散模型的图像生成方法。它能根据现有图像内容，生成图像的外部区域，使图像看起来更自然和完整。这在图像编辑、游戏开发、虚拟现实等领域非常有用。

### **主要应用**

- **图像编辑**：可以用于扩展照片或绘画的边界，使其适应不同的比例和用途。
- **游戏开发**：在生成游戏场景时，使用这种技术可以创建更加完整和丰富的背景。
- **虚拟现实**：在 VR 环境中，通过扩展视角范围，增强用户的沉浸感和真实感。

### **优势**

- **高质量生成**：生成的图像细节丰富，过渡自然。
- **多样性和灵活性**：可以应用于不同类型的图像和场景。
- **自动化处理**：减少了手动编辑的工作量，提高了效率。

1、在线免费使用 【**[点击前往](https://huggingface.co/spaces/fffiloni/diffusers-image-outpaint)**】，无需安装，免费使用，但是需 “魔法”，共享GPU，高峰期多人使用速度会比较慢

2、本地安装使用，不受限制，无需网络，速度快！

 **前提准备**：需要安装 [Python 3.10](https://www.python.org/downloads/release/python-3100/)或更高版本  ，并安装 **[Git](https://git-scm.com/)** ，[CUDA](https://developer.nvidia.com/cuda-toolkit) ，[ffmpeg](https://www.freedidi.com/13051.html) 以及 [Conda](https://docs.anaconda.com/miniconda/) 环境。

安装后可以通过CMD：
```
nvidia-smi，nvcc -V，git --version，conda --version，ffmpeg -version
```
来检测你是否已安装好环境

3、下载安装

- 克隆Huggingface上的代码
```
git lfs install
git clone https://huggingface.co/spaces/fffiloni/diffusers-image-outpaint
```

- 进入项目文件夹内
```
cd diffusers-image-outpaint
```
**注意：大陆用户如果无法下载，可手动下载完整项目包：【[点击下载](http://pan.tuio.cc/s/Yd2Tl)】** **然后进入项目文件夹内，继续下面的操作。**

###  **创建&激活虚拟环境**
```
#Python版本官方无要求，这里以常见的3.10.x为例

conda create -n diffusers-image-outpaint python=3.10 -y
conda activate diffusers-image-outpaint
```
###  **安装三方库**
```
#国外用户
pip install -r requirements.txt --extra-index-url https://download.pytorch.org/whl/cu118

#国内用户
pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple --extra-index-url https://download.pytorch.org/whl/cu118
```
### 启动项目

制作批处理启动程序，双击运行。
```
@echo off
set HF_ENDPOINT=https://hf-mirror.com
:: 模型文件有近20G，可手动选择模型下载路径
set HF_HOME=D:\AI_Models
call conda activate diffusers-image-outpaint
start http://127.0.0.1:7860
python app.py
pause
```
创建好的批处理文件放在diffusers-image-outpaint 根目录下 ，比如我的是C:\Users\LINGDU\diffusers-image-outpaint

然后双击运行 diffusers-image-outpaint.bat批处理即可！

第一次启动时需要下载模型，大概20G左右，耐心等待一段时间。下载后会自动启动程序，并弹出页面地址：http://127.0.0.1:7860 ，当模型下载完成以后，页面才会正常访问！

最后大功告成！愉快的不受限制的使用吧……

**提醒： NVIDIA显卡，显存建议>=16G。8G和12G时也可运行，但会用到共享显存，稍慢！**