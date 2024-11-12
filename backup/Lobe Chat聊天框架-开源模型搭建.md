一款免费开源的项目即可搞定：ChatGPT、Claude、Google Gemini、Mistral、LLaMA2等主流AI大模型的无缝切换使用！

Lobe UI 是一个开源 UI 组件库，用于构建 AIGC Web 应用程序。

1.开源项目:【[Github](https://github.com/lobehub/lobe-chat)】、【**[网盘下载](https://www.dongli7.com/forum.php?mod=viewthread&tid=15)**】

2.通过免费容器进行一键安装！也可以通过【[Vulr](https://www.vultr.com/?ref=7045490)】进行搭建获得更快的速度。

- 安装好再获取你自己的 【[OpenAI API 密钥】](https://platform.openai.com/account/api-keys)
- 获取自己的Google Gemini API KEY 【[点击获取](https://aistudio.google.com/app/apikey)】
#### 注意：Vercel分配的域名在部分地区受到屏蔽； 绑定自定义域名可以直接连接。当然通过【[Vulr](https://www.vultr.com/?ref=7045490)】进行Docker一键部署，可以获得更好的性能和访问速度！
```
$ docker run -d -p 3210:3210 \
  -e OPENAI_API_KEY=sk-xxxx \
  -e ACCESS_CODE=lobe66 \
  --name lobe-chat \
  lobehub/lobe-chat
```
- dockers 环境一键安装：[https://bbs.freedidi.com/t/topic/481](https://bbs.freedidi.com/t/topic/481)

3. 本地部署

您可以使用GitHub Codespaces进行在线开发：

或者克隆它以进行本地开发：
```
$ git clone https://github.com/lobehub/lobe-chat.git
$ cd lobe-chat
$ pnpm install
$ pnpm dev
```
