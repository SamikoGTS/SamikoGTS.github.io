WAN2.1 是一套全面开放的视频生成模型，它突破了视频生成的界限。1.3B型号仅需要8.19 GB VRAM，使其与几乎所有消费级GPU兼容。它可以在大约4分钟内在RTX 4090上生成5秒的480p视频（无需量化等优化技术）。它的性能甚至可以与某些封闭式模型相媲美。

在 SOTA性能方面，始终优于多个基准测试的现有开源模型，并且可以和最先进的闭源商业模型相媲美！

![](https://www.freedidi.com/wp-content/uploads/2025/03/d27886e24b20250308222106.webp)

**Wan 2.1  视频生成模型本地部署：**

### **文字转视频**

**1、**下载 ComfyUI 一键安装包 ：【[点击前往](https://www.comfy.org/) 】，支持 Windows 和 mac 系统

**2、**下载文本编码器和 VAE ：[umt5_xxl_fp8_e4m3fn_scaled.safetensors](https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/tree/main/split_files/text_encoders) 放入：ComfyUI/models/text_encoders/ [wan_2.1_vae.safetensors](https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/blob/main/split_files/vae/wan_2.1_vae.safetensors) 放入：ComfyUI/models/vae/

**3、**下载视频生成模型 【[点击下载](https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/tree/main/split_files/diffusion_models)】

注意：建议使用 fp16 版本而不是 bf16 版本，因为它们会产生更好的结果。

质量等级（从高到低）：fp16 > bf16 > fp8_scaled > fp8_e4m3fn

这些文件位于：ComfyUI/models/diffusion_models/

这些示例使用 16 位文件，但如果内存不足，则可以使用 fp8 文件。

4、文字转视频工作流：下载 [Json 格式的工作流](https://comfyanonymous.github.io/ComfyUI_examples/wan/text_to_video_wan.json)

<video width="320" height="240" controls>
  <source src="https://video.bittly.cc/Wan8765665.mp4?_=1" type="video/mp4">
</video>

### **进阶篇:  图像转视频**

此工作流程需要[wan2.1_i2v_480p_14B_fp16.safetensors](https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/blob/main/split_files/diffusion_models/wan2.1_i2v_480p_14B_fp16.safetensors)文件（将其放入：ComfyUI/models/diffusion_models/）和 [clip_vision_h.safetensors](https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/blob/main/split_files/clip_vision/clip_vision_h.safetensors)放入：ComfyUI/models/clip_vision/

请注意，此示例仅生成 512×512 的 33 帧，因为我希望它易于访问，但模型可以做的不止这些。如果您有硬件/耐心运行它，720p 模型就相当不错。

[Json 格式的工作流](https://comfyanonymous.github.io/ComfyUI_examples/wan/image_to_video_wan_example.json)

[输入图像可以在通量](https://comfyanonymous.github.io/ComfyUI_examples/flux)页面上找到。

[以下是720p](https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/blob/main/split_files/diffusion_models/wan2.1_i2v_720p_14B_fp16.safetensors) 型号的相同示例：

![](https://www.freedidi.com/wp-content/uploads/2025/03/8b917fc01120250308222359.webp)

