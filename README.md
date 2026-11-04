# 真人白板手绘视频 Skill

把中文文案整理成口播稿，通过 **ElevenLabs 配音 + Hyperframes** 制作白板手绘讲解视频。

## 画面示例

以下是《财富阶梯》示例片的真实渲染截图，展示真人持笔、逐笔绘制、上色和字幕排版。示例为此前版本；新版规范进一步要求每页使用新绘制的主体和道具。

| 真人手与素描 | 彩色画面与排版 | 上色过程 |
| --- | --- | --- |
| ![真人持笔逐笔绘制](docs/images/pencil-and-real-hand.png) | ![彩色手绘、重点列表与上移字幕](docs/images/color-and-layout.png) | ![区域上色与场景细节](docs/images/color-reveal.png) |

## 画面规范

- 默认 **3:4 / 1080×1440 / 30fps**，可按明确要求调整。
- 真人摄影持笔手素材，笔尖跟随绘制路径；素材缺失时不会自动降级为无手模式。
- **每页使用新元素**：主体、动作和道具均重新设计，禁止复制插画后仅换色、缩放或镜像。真人手、字体和背景等制作层保持统一。
- 多元素情境插画，呈现 **素描 → 轮廓细节 → 彩色**。
- 主标题与重点列表使用加粗中文黑体，列表默认圆点符号；重点词与字幕使用清晰的文楷等艺术字体。
- 字幕中心位于画面自上而下约2/3处，也就是距底部约1/3高度。
- 重点词组、逐条列表、圈画及箭头跟随口播出现。
- 背景中心明亮，四角带柔和相机暗角；不加顶部栏目编号和底部装饰署名。

## 默认配音

- 模型：`eleven_v4`；音色：`5eoK8NqMBsMdqUmImHNs`。
- 已确认 A 版“温柔清晰”：标准普通话、自然有感情，重音与语调服务句意。
- 参数：`language_code=zh`、`stability=0.65`、`similarity_boost=0.8`；V4 不传 `speed`、`style` 或 SSML。
- 直接复用已确认设置；先有正式配音，再按字词时间生成字幕和动画事件。原稿、展示稿与读法稿分开保存，整篇配音优先。
- 配音后检查错漏和读法，修改音频后重新对齐；ASR 正确率不能证明主观自然度或每个声调准确。

## 安装到 Codex

将本仓库放到技能目录，文件夹名保持为 `whiteboard-elevenlabs-hyperframes`：

```bash
git clone https://github.com/wbin888/whiteboard-sb.git ~/.codex/skills/whiteboard-elevenlabs-hyperframes
```

如果目标目录已存在，请先检查本地修改，再决定合并或更新。安装后重新打开 Codex 会话以发现技能。

## 使用

```text
用 $whiteboard-elevenlabs-hyperframes，把下面文案做成3:4真人手绘视频：
[粘贴你的文案]
```

默认流程：原文 → 口播稿 → 分镜 → ElevenLabs 配音 → 字幕对齐 → Hyperframes 动画 → MP4验证与交付。

## 依赖与素材

本仓库是给 Codex 使用的制作流程技能，不是独立渲染程序，也不包含可直接运行的视频模板。执行环境需要：

- Hyperframes CLI 及对应的 core / animation / cli 技能、Node.js 和 FFmpeg。
- ElevenLabs API 权限和对应技能；凭据仅通过环境变量 `ELEVENLABS_API_KEY` 或本机私密配置提供。
- 有使用授权的真人手透明素材及中文字体；需要生成插画时使用图像生成能力。

仓库不包含 API 密钥、账号配置、原视频、字体、真人手素材或成片。使用素材时须单独确认来源与许可。

## 文件

- [SKILL.md](SKILL.md)：主流程与验收要求。
- [配音与词级同步](references/voiceover-timing.md)：V4 A 版设置、读法、对齐与语义事件。
- [画面制作规范](references/visual-production.md)：真人手、素描上色、字幕、字体与暗角。
- [参考片分析](references/reference-analysis.md)：参考视频观察及分析边界。

原片分析采用间隔抽帧和字幕证据，不代表已经完成逐帧或完整听觉分析。实际成片仍须检查绘制同步、字幕位置、字体、解码和声音。
