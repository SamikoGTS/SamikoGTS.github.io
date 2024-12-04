此开源的视频生成模型：包含 PyTorch 模型定义、预训练权重和推理/采样代码

下表为运行HunyuanVideo模型（batch size = 1）生成视频的要求：
模型 | 设置（高度/宽度/框架） | 去噪步骤 | GPU 峰值内存
-- | -- | -- | --
混元视频 | 720px1280px129f | 三十 | 60GB
混元视频 | 544px960px129f | 三十 | 45GB

- 需要支持 CUDA 的 NVIDIA GPU。
- 我们已经在单个 H800/H20 GPU 上进行了测试。
- 最低限度：720px1280px129f 所需的最低 GPU 内存为 60GB，544px960px129f 所需的最低 GPU 内存为 45G。
- 建议：我们建议使用具有 80GB 内存的 GPU 以获得更好的生成质量。
- 测试的操作系统：Linux

🛠️ 依赖项和安装
首先通过下方的命令来克隆存储库：
```
git clone https://github.com/tencent/HunyuanVideo
cd HunyuanVideo
```
或者网盘打包下载【[点击前往](http://pan.tuio.cc/s/3avI8)】
Linux 安装指南
我们提供了一个environment.yml用于设置 Conda 环境的文件。Conda 的安装说明可[在此处](https://docs.anaconda.com/free/miniconda/index.html)获得。

我们推荐 CUDA 版本 11.8 和 12.0+。
```
# 1. Prepare conda environment
conda env create -f environment.yml

# 2. Activate the environment
conda activate HunyuanVideo

# 3. Install pip dependencies
python -m pip install -r requirements.txt

# 4. Install flash attention v2 for acceleration (requires CUDA 11.8 or above)
python -m pip install git+https://github.com/Dao-AILab/flash-attention.git@v2.5.9.post1
```
此外，HunyuanVideo还提供了预先构建的Docker镜像： [docker_hunyuanvideo](https://aivideo.hunyuan.tencent.com/download/HunyuanVideo/hunyuan_video_cu12.tar)。
```
# 1. Use the following link to download the docker image tar file (For CUDA 12).
wget https://aivideo.hunyuan.tencent.com/download/HunyuanVideo/hunyuan_video_cu12.tar

# 2. Import the docker tar file and show the image meta information (For CUDA 12).
docker load -i hunyuan_video.tar

docker image ls

# 3. Run the container based on the image
docker run -itd --gpus all --init --net=host --uts=host --ipc=host --name hunyuanvideo --security-opt=seccomp=unconfined --ulimit=stack=67108864 --ulimit=memlock=-1 --privileged  docker_image_tag
```
🧱 下载预训练模型
下载预训练模型的详细信息显示[在此处](https://github.com/Tencent/HunyuanVideo/blob/main/ckpts/README.md)，或者在HuggingFace上下载【[点击前往](https://huggingface.co/tencent/HunyuanVideo/tree/main)】共26G左右。

 
🧱下载文本编码器
HunyuanVideo采用MLLM模型和CLIP模型作为文本编码器。

1.MLLM 模型（text_encoder 文件夹）
HunyuanVideo 支持不同的 MLLM（包括 HunyuanMLLM 和开源 MLLM 模型），现阶段我们尚未发布 HunyuanMLLM，建议社区用户使用[Xtuer](https://huggingface.co/xtuner)提供的[llava-llama-3-8b](https://huggingface.co/xtuner/llava-llama-3-8b-v1_1-transformers)，可通过以下命令下载
```
cd HunyuanVideo/ckpts
huggingface-cli download xtuner/llava-llama-3-8b-v1_1-transformers --local-dir ./llava-llama-3-8b-v1_1-transformers
```
为了节省模型加载的GPU内存资源，我们将的语言模型部分分离llava-llama-3-8b-v1_1-transformers成text_encoder。
```
cd HunyuanVideo
python hyvideo/utils/preprocess_text_encoder_tokenizer_utils.py --input_dir ckpts/llava-llama-3-8b-v1_1-transformers --output_dir ckpts/text_encoder
```
2.CLIP 模型（text_encoder_2 文件夹）
我们使用[OpenAI](https://openai.com/)提供的[CLIP](https://huggingface.co/openai/clip-vit-large-patch14)作为另一个文本编码器，社区用户可以通过以下命令下载此模型
```
cd HunyuanVideo/ckpts
huggingface-cli download openai/clip-vit-large-patch14 --local-dir ./text_encoder_2
```
我们在下表中列出了我们支持的高度/宽度/框架设置。</p>
分辨率 | 时长=9:16 | 高/宽=16:9 | 高/宽=4:3 | 高/宽=3:4 | 高/宽=1:1
-- | -- | -- | -- | -- | --
540p | 544px960px129f | 960px544px129f | 624px832px129f | 832px624px129f | 720px720px129f
720p（推荐） | 720px1280px129f | 1280px720px129f | 1104px832px129f | 832px1104px129f | 960px960px129f

使用命令行
```
cd HunyuanVideo

python3 sample_video.py \
    --video-size 720 1280 \
    --video-length 129 \
    --infer-steps 50 \
    --prompt "A cat walks on the grass, realistic style." \
    --flow-reverse \
    --use-cpu-offload \
    --save-path ./results
```

更多配置
我们列出了一些更有用的配置以便于使用：

参数 | 默认 | 描述
-- | -- | --
--prompt | 没有任何 | 视频生成的文字提示
--video-size | 720 1280 | 生成的视频的大小
--video-length | 129 | 生成视频的长度
--infer-steps | 50 | 采样步数
--embedded-cfg-scale | 6.0 | 嵌入式分类器免费指导量表
--flow-shift | 7.0 | 流匹配调度程序的移位因子
--flow-reverse | 错误的 | 如果反向，从 t=1 -> t=0 学习/采样
--seed | 没有任何 | 生成视频的随机种子，如果没有，我们初始化一个随机种子
--use-cpu-offload | 错误的 | 使用 CPU 卸载来加载模型以节省更多内存，这对于高分辨率视频生成是必要的
--save-path | 。/结果 | 生成视频的保存路径

HunyuanVideo 开源项目地址
GitHub仓库：https://github.com/Tencent/HunyuanVideo/
HuggingFace模型库：https://huggingface.co/tencent/HunyuanVideo