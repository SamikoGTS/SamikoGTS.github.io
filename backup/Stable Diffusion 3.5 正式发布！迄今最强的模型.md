今天 Anthropic 正式发布 Stable Diffusion 3.5，这是它们迄今为止最强的模型，此公开版本包含多个型号变体，包括 Stable Diffusion 3.5 Large 和 Stable Diffusion 3.5 Large Turbo。此外，Stable Diffusion 3.5 Medium 将于 10 月 29 日发布。

这些模型的尺寸可高度定制，可在消费级硬件上运行，并且根据宽松的Stability AI 社区许可，可免费用于商业和非商业用途。 

您现在可以从Hugging Face下载

Stable Diffusion 3.5 Large 【**[点击下载](https://huggingface.co/stabilityai/stable-diffusion-3.5-large)**】、【**[备用下载](https://civitai.com/models/878387/stable-diffusion-35-large?modelVersionId=983309)** 】 推荐16G以上显存

Stable Diffusion 3.5 Large Turbo 【**[点击下载](https://huggingface.co/stabilityai/stable-diffusion-3.5-large-turbo)**】、【**[备用下载](https://civitai.com/models/878645?modelVersionId=983611)**】 推荐8G以上显存

**版本的区别：**

- [**Stable Diffusion 3.5 Large**](https://huggingface.co/stabilityai/stable-diffusion-3.5-large)：该基础型号拥有 80 亿个参数，质量卓越，响应迅速，是 Stable Diffusion 系列中最强大的型号。该型号非常适合 1 百万像素分辨率的专业用例。
    
- [**稳定扩散 3.5 Large Turbo**：](https://huggingface.co/stabilityai/stable-diffusion-3.5-large-turbo)稳定扩散 3.5 Large 的精简版仅需 4 个步骤即可生成高质量图像，且具有出色的快速依从性，速度比稳定扩散 3.5 Large 快得多。
    
- **Stable Diffusion 3.5 Medium（将于 10 月 29 日发布）**： 该模型拥有 25 亿个参数，采用改进的 MMDiT-X 架构和训练方法，可在消费级硬件上“开箱即用”，在质量和定制易用性之间取得平衡。它能够生成分辨率在 0.25 到 2 百万像素之间的图像。 
    

## **安装方法：**

## **最新 ComfyUI 已经支持最新的稳定版 Stable Diffusion 3.5** 

[立即使用这些示例工作流程](https://huggingface.co/Comfy-Org/stable-diffusion-3.5-fp8/tree/main?ref=blog.comfy.org)来使用 Stable Diffusion 3.5 Large 和 Stable Diffusion 3.5 Large Turbo ！

1. 更新至 ComfyUI 最新版本 【**[点击下载](https://github.com/comfyanonymous/ComfyUI)**】或【**[网盘下载](https://www.dongli7.com/thread-4-1-1.html)**】
2. [将Stable Diffusion 3.5 Large](https://huggingface.co/stabilityai/stable-diffusion-3.5-large?ref=blog.comfy.org)或[Stable Diffusion 3.5 Large Turbo](https://huggingface.co/stabilityai/stable-diffusion-3.5-large-turbo?ref=blog.comfy.org)下载到您的 models/checkpoint 文件夹
3. [将clip_g.safetensors](https://huggingface.co/stabilityai/stable-diffusion-3-medium/resolve/main/text_encoders/clip_g.safetensors?ref=blog.comfy.org)、[clip_l.safetensors](https://huggingface.co/stabilityai/stable-diffusion-3-medium/resolve/main/text_encoders/clip_l.safetensors?ref=blog.comfy.org)和[t5xxl_fp16.safetensors](https://huggingface.co/stabilityai/stable-diffusion-3-medium/resolve/main/text_encoders/t5xxl_fp16.safetensors?ref=blog.comfy.org)下载到 models/clip 文件夹（您可能已经下载了它们）注意：低显存请选择量化版 [t5xxl_fp8_e4m3fn.safetensors](https://huggingface.co/Comfy-Org/stable-diffusion-3.5-fp8/resolve/main/text_encoders/t5xxl_fp8_e4m3fn.safetensors?download=true&ref=blog.comfy.org)
4. 拖入工作流程并生成！

2.添加中文语言包

3.汉化 ComfyUI 中文语言设置：【**[语言包下载](https://github.com/AIGODLIKE/AIGODLIKE-ComfyUI-Translation)**】或【**[网盘下载](https://www.dongli7.com/forum.php?mod=viewthread&tid=4)**】

然后，将 ZIP 包解压到 ComfyUI\custom_nodes 目录中：

进入设置中心切换语言为中文

生成提示词：

1.穿着穿着牛仔短裤，白色衬衣的中国女孩
```
Chinese girl, wearing denim shorts, white shirt, yellow hair, abstract photography
```
## **低 RAM 解决方案**

- 如果一代崩溃，则很可能表明 RAM 不足。
- 使用[fp8_scaled 工作流 json](https://huggingface.co/Comfy-Org/stable-diffusion-3.5-fp8/blob/main/sd3.5-t2i-fp8-scaled-workflow.json?ref=blog.comfy.org)（实验性）和[fp8 缩放模型](https://huggingface.co/Comfy-Org/stable-diffusion-3.5-fp8/blob/main/sd3.5_large_fp8_scaled.safetensors?ref=blog.comfy.org)作为低 vram 选项
- 您可以尝试使用[t5xxl_fp8_e4m3fn_scaled.safetensors](https://huggingface.co/Comfy-Org/stable-diffusion-3.5-fp8/resolve/main/sd3.5_large_fp8_scaled.safetensors?download=true&ref=blog.comfy.org)或[t5xxl_fp8_e4m3fn.safetensors](https://huggingface.co/Comfy-Org/stable-diffusion-3.5-fp8/resolve/main/text_encoders/t5xxl_fp8_e4m3fn.safetensors?download=true&ref=blog.comfy.org)代替 t5xxl_fp16 以降低内存使用率（缩放版本是我们的一个实验性检查点）。但是，如果您的 RAM 超过 32GB，我们仍然建议您使用 t5xxl_fp16。

**模型的优势**

Stable Diffusion 3.5 版本在以下方面表现出色，使其成为市场上最可定制、最易于访问的图像模型之一，同时在及时性和图像质量方面保持顶级性能：

- **可定制性：**轻松微调模型以满足您的特定创作需求，或根据定制的工作流程构建应用程序。
    
- **高效性能：**经过优化，可在标准消费硬件上运行，无需繁重工作，尤其是 Stable Diffusion 3.5 Medium 和 Stable Diffusion 3.5 Large Turbo 型号。
    
- **多样化输出：**创建代表世界的图像，而不仅仅是一种类型的人，具有不同的肤色和特征，无需大量提示。 
    

当然除了在[GitHub](https://github.com/Stability-AI/sd3.5) 上下载推理代码，你可以直接在线体验文生图片的效果：

Stable Diffusion 3.5 Large【[点击前往](https://huggingface.co/spaces/stabilityai/stable-diffusion-3.5-large)】

Stable Diffusion 3.5 Large Turbo【[点击前往](https://huggingface.co/spaces/stabilityai/stable-diffusion-3.5-large-turbo)】

---
**Stable Diffusion 3.5 美图生成提示词大全**
```
NSFW, front angle, (8k, best quality, masterpiece:1.2), (realistic, photo-realistic:1.37), ultra-detailed, 1 girl, looking at viewer, beautiful detailed sky, detailed cafe street, sitting, full body, small head, intricate choker, (pretty legs:1.2), (long legs:1.2), slim legs, (high heels:1.3), (bare legs:1.4), medium breasts, high-waist, narrow waist, off-shoulder, belt, short bottoms, beautiful detailed eyes, daytime, warm tone, white lace, (long hair:1.4), silver medium hair, white skin, cinematic light, street light,
```

```
(RAW photo, best quality), (realistic, photo-realistic:1.3), masterpiece, an extremely delicate and beautiful, extremely detailed, CG, unity, 8k, amazing, finely detail, ultra-detailed, highres, absurdres, soft light, (black hair, short hair, curly hair, messy hair, bangs), beautiful detailed girl, detailed fingers, extremely detailed eyes and face, beautiful detailed nose, beautiful detailed eyes, (light on face), looking at viewer, (closed mouth:1.2), 1girl, cute, young, mature face, pale skin, (half body:1.3, sitting), (medium breasts), realistic face, realistic body, beautiful detailed thigh, (ulzzang-6500-v1.1:0.6), <lora:koreandolllikeness_v20:0.5>, (white shirt, collared shirt, lace, black miniskirt, pantyhose, detached sleeves, bowtie), <lora:zhengyingshan6:0.6>, (semi smile:1.3), (aegyo sal:1), (kpop idol:1), relaxed,
```

```
close-up shot front view of an attractive chinese girl wearing next-generation Apple Vision Pro VR glasses with glowing words “LING DU” clearly written on the VR glasses, blue lightings on the VR glasses, award-winning picture, highly detailed, ultra-high resolutions, 32K UHD
```

```
chinese girl,solo,flower,dress,black dress,black hair,holding,strapless,bare shoulders,holding flower,rose,watermark,strapless dress,parted lips,earrings,pink flower,jewelry,dark,bare arms
```

```
Chinese girl, wearing denim shorts, white shirt, yellow hair, abstract photography
```