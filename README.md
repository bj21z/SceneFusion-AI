# 人在景中 · Scene Fusion AI V1.0

手机优先的 AI 场景人像融合 PWA，可部署到 Cloudflare Pages。

## 功能
- 上传人物照片并在本地压缩
- 12 个内置场景主题
- 可上传第二张真实场景照片作为参考
- 全身 / 半身 / 环境人像三种构图
- 竖版 / 正方形 / 横版输出
- 快速 / 标准 / 精细三档画质
- Cloudflare Pages Function 后端安全调用 OpenAI Responses API + image_generation
- OpenAI API Key 只保存在服务器环境变量中
- 结果保存、iPhone 原生分享、PWA 添加到主屏幕
- 上传授权确认与 AI 合成图使用提示

## Cloudflare Pages 部署
1. 将整个文件夹上传至 GitHub 仓库。
2. Cloudflare → Workers & Pages → Create → Pages → Connect to Git。
3. Framework preset 选 None；Build command 留空；输出目录使用仓库根目录（通常为 `.`）。
4. 部署后进入 Settings → Variables and Secrets。
5. 添加加密变量：`OPENAI_API_KEY` = 你的 OpenAI API Key。
6. 重新部署。
7. iPhone Safari 打开网址 → 分享 → 添加到主屏幕。

## 说明
- 直接打开 index.html 可以浏览完整界面，但真正生成图片必须部署，因为 `/api/generate` 是 Cloudflare Pages Function。
- ChatGPT Plus 与 OpenAI API 是分开计费的；生成图片会消耗 API 用量。
- 当前代码按 2026-08-17 OpenAI 官方文档使用 `gpt-5.6` 的 Responses API `image_generation` 工具。
- 用户照片会在浏览器压缩后传给 OpenAI API；本程序自身不建立照片数据库。
- 对公众开放前建议增加账号、速率限制、配额、隐私政策、用户协议和滥用防护。
