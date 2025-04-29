**Qwen 3**是 Qwen 系列中最新一代大型语言模型，提供全面的密集和混合专家 (MoE) 模型。旗舰模型**Qwen3-235B-A22B**在编码、数学、通用能力等基准测试中取得了与 DeepSeek-R1、o1、o3-mini、Grok-3 和 Gemini-2.5-Pro 等顶级模型相比极具竞争力。此外，小型 MoE 模型**Qwen3-30B-A3B**的激活参数量是 QwQ-32B 的 10 倍，即使是像 Qwen3-4B 这样的微型模型也能与 Qwen2.5-72B-Instruct 的性能相媲美。

![](https://www.freedidi.com/wp-content/uploads/2025/04/585a16792420250429131417.webp)

- **独特地支持****单一模型**内思维模式（用于复杂的逻辑推理、数学和编码）与**非思维模式**（用于高效、通用的对话）之间的无缝切换，确保在各种场景下实现最佳性能。
- **推理能力大幅增强**，在数学、代码生成、常识逻辑推理等方面超越了之前的QwQ（思维模式）和Qwen2.5指令模型（非思维模式）。
- **卓越的人类偏好一致性**，擅长创意写作、角色扮演、多轮对话和指令遵循，提供更自然、更具吸引力和身临其境的对话体验。
- **精通代理能力**，能够以思考和非思考两种模式与外部工具精准集成，在基于代理的复杂任务中取得开源模型的领先性能。
- **支持 100 多种语言和方言，具有强大的****多语言指令跟踪和翻译**能力。

![](https://www.freedidi.com/wp-content/uploads/2025/04/75f27bd8ea20250429131609.webp)
![](https://www.freedidi.com/wp-content/uploads/2025/04/21745fc23120250429131610.webp)

### 模型

1、首先我们需要安装下Ollama 客户端 【**[点击下载](https://www.freedidi.com/?golink=aHR0cHM6Ly9vbGxhbWEuY29tLw==)**】

2、选择适合自己的开源模型，通过下方的命令进行安装部署：

**0.6B参数模型**
```
ollama run qwen3:0.6b
```
**1.7B参数模型**
```
ollama run qwen3:1.7b
```
**4B参数模型**
```
ollama run qwen3:4b
```
**8B参数模型**
```
ollama run qwen3:8b
```
**14B参数模型**
```
ollama run qwen3:14b
```
**32B参数模型**
```
ollama run qwen3:32b
```
**30B 混合专家模型，包含 3B 个活动参数**
```
ollama run qwen3:30b-a3b
```
**235B 混合专家模型，包含 22B 个有效参数**
```
ollama run qwen3:235b-a22b
```
**如何卸载已安装过的模型？在CMD终端下，通过命令：**
```
ollama list  # 查询已安装的模型
ollama rm 模型名称  # 卸载并删除模型
```
比如需要删除gemma2:27b 模型，那么只需输入：
```
ollama rm gemma2:27b
```
部署Ollama后推荐对接到 Cherry-Studio这个开源软件【[点击下载](https://www.freedidi.com/?golink=aHR0cHM6Ly93d3cuY2hlcnJ5LWFpLmNvbS8=)】，使用会更加方便！

![](https://www.freedidi.com/wp-content/uploads/2025/04/e3d609708520250429133909.webp)
