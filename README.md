# 真人白板手绘视频 Skill

把中文文案整理成口播稿，通过 **ElevenLabs 配音 + Hyperframes** 制作白板手绘讲解视频。

## 画面规范

- 默认 **3:4 / 1080×1440 / 30fps**，可按明确要求调整。
- 真人摄影持笔手素材，笔尖跟随绘制路径；素材缺失时不会自动降级为无手模式。
- 多元素情境插画，呈现 **素描 → 轮廓细节 → 彩色**。
- 主标题与重点列表使用加粗中文黑体，列表默认圆点符号；重点词与字幕使用清晰的文楷等艺术字体。
- 字幕中心位于画面自上而下约2/3处，也就是距底部约1/3高度。
- 重点词组、逐条列表、圈画及箭头跟随口播出现。
- 背景中心明亮，四角带柔和相机暗角；不加顶部栏目编号和底部装饰署名。

## 安装到 Codex

将本仓库放到技能目录，文件夹名保持为 `whiteboard-elevenlabs-hyperframes`：

```bash
git clone https://github.com/wbin888/whiteboard-elevenlabs-hyperframes.git ~/.codex/skills/whiteboard-elevenlabs-hyperframes
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
- [画面制作规范](references/visual-production.md)：真人手、素描上色、字幕、字体与暗角。
- [参考片分析](references/reference-analysis.md)：参考视频观察及分析边界。

原片分析采用间隔抽帧和字幕证据，不代表已经完成逐帧或完整听觉分析。实际成片仍须检查绘制同步、字幕位置、字体、解码和声音。
