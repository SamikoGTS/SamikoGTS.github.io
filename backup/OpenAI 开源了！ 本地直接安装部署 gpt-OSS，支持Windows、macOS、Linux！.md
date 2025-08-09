就在刚刚，OpenAI 发布了 gpt-oss-120b 和 gpt-oss-20b——两款性能卓越的开放轻量级语言模型，可在低成本下实现强大的实际应用性能。这些模型在灵活的 Apache 2.0 许可证下提供，与同等规模的开放模型相比，在推理任务中表现更优，展现出强大的工具使用能力，并针对在消费级硬件上高效部署进行了优化。它们通过强化学习与 OpenAI 最先进内部模型（包括 o3 及其他前沿系统）所启发的技术相结合进行训练。

**模型选择：**

- `gpt-oss-120b`— 适用于生产、通用、高推理用例，适合单个 H100 GPU（117B 参数，其中 5.1B 活动参数）
- `gpt-oss-20b`— 适用于较低延迟和本地或特殊用例（210 亿个参数，其中 36 亿个活动参数）

这两个模型都是使用OpenAI的[和声反应格式](https://www.freedidi.com/?golink=aHR0cHM6Ly9naXRodWIuY29tL29wZW5haS9oYXJtb255)进行训练的，并且只能与这种格式一起使用；否则，它们将无法正常工作。

### 亮点

- **宽松的 Apache 2.0 许可证**：自由构建，不受版权限制或专利风险 – 非常适合实验、定制和商业部署。
- **可配置的推理力度**：根据您的具体用例和延迟需求轻松调整推理力度（低、中、高）。
- **完整的思路链**：提供对模型推理过程的完整访问权限，从而简化调试并增强输出的可信度。此信息不打算向最终用户显示。
- **可微调**：通过参数微调完全根据您的特定用例定制模型。
- **Agentic 功能**：使用模型的本机功能进行函数调用、[网页浏览](https://www.freedidi.com/?golink=aHR0cHM6Ly9naXRodWIuY29tL29wZW5haS9ncHQtb3NzI2Jyb3dzZXI=)、[Python 代码执行](https://www.freedidi.com/?golink=aHR0cHM6Ly9naXRodWIuY29tL29wZW5haS9ncHQtb3NzI3B5dGhvbg==)和结构化输出。
- **原生 MXFP4 量化**：模型使用原生 MXFP4 精度针对 MoE 层进行训练，允许`gpt-oss-120b`在单个 H100 GPU 上运行并`gpt-oss-20b`在 16GB 内存内运行。

### 安装要求

- python 3.12 【**[点击下载](https://www.freedidi.com/?golink=aHR0cHM6Ly93d3cucHl0aG9uLm9yZy9kb3dubG9hZHMvcmVsZWFzZS9weXRob24tMzEyMC8=)**】
- 在 macOS 上：安装 Xcode CLI 工具 –>`xcode-select --install`
- 在 Linux 上：这些参考实现需要 CUDA
- 在 Windows 上：如果您想在本地运行模型，请尝试使用 Ollama 等解决方案。

如果您尝试在消费类硬件上运行，你可以有2种安装方式：

1、在安装 Ollama上进行部署， 点击下载【**[官方版](https://www.freedidi.com/?golink=aHR0cHM6Ly9vbGxhbWEuY29tL2Rvd25sb2Fk)**】后运行以下命令来使用 Ollama 。

```
# gpt-oss-20b
ollama pull gpt-oss:20b
ollama run gpt-oss:20b

# gpt-oss-120b
ollama pull gpt-oss:120b
ollama run gpt-oss:120b
```

![](https://www.freedidi.com/wp-content/uploads/2025/08/71d930bd9920250806125214.webp)

2、在 LM Studio 上部署 ，如果您使用[LM Studio，](https://www.freedidi.com/?golink=aHR0cHM6Ly9sbXN0dWRpby5haS8=)则可以使用以下命令进行下载。

```
# gpt-oss-20b
lms get openai/gpt-oss-20b
# gpt-oss-120b
lms get openai/gpt-oss-120b
```

3、如果需要下载原尺寸模型，您可以直接从 Hugging Face CLI下载[Hugging Face Hub](https://www.freedidi.com/?golink=aHR0cHM6Ly9odWdnaW5nZmFjZS5jby9jb2xsZWN0aW9ucy9vcGVuYWkvZ3B0LW9zcy02ODkxMTk1OTU5MGExNjM0YmExMWM3YTQ=)中的模型权重：

```
# gpt-oss-120b
huggingface-cli download openai/gpt-oss-120b --include "original/*" --local-dir gpt-oss-120b/

# gpt-oss-20b
huggingface-cli download openai/gpt-oss-20b --include "original/*" --local-dir gpt-oss-20b/
```
