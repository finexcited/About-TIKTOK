# About-TIKTOK

抖音 / 小红书视频素材采集与语音本地化 Agent Skill。

| 目录 | 技能 | 功能 | 版本 |
|---|---|---|---|
| [`douyin-xhs-video-harvest/`](douyin-xhs-video-harvest/) | 抖音 / 小红书视频采集 | 关键词或参考素材检索 → 竖屏 1080P+ 筛选 → 无水印下载 → 中文人声删除或目标语言 AI 配音 → 元数据清理 | V1.0 |

## 主要能力

- 通过 ego lite 使用已有登录态检索抖音或小红书。
- 按主体形式、画面风格和排除项筛选，最多检查 50 条候选。
- 交付 9:16、短边至少 1080 像素、无明显平台水印的视频。
- 检测到明显中文语音后，可删除人声并保留背景音，或替换为指定语言的 AI 配音。
- 视频流不重新编码，只处理音频并清理容器元数据。

## 安装

```bash
git clone https://github.com/finexcited/About-TIKTOK.git
cp -R About-TIKTOK/douyin-xhs-video-harvest ~/.codex/skills/douyin-xhs-video-harvest
```

也可把 `douyin-xhs-video-harvest/` 整个目录复制到其他兼容 Agent Skills 的技能目录。

## 依赖

- `ffmpeg`、`ffprobe`、Python 3
- ego lite 及目标平台登录态
- 人声分离：Demucs `htdemucs`
- 目标语言配音：本机或用户指定的 TTS / AI 语音服务

## 使用

```text
用 douyin-xhs-video-harvest 在抖音找 3 条“潮流女装大衣穿搭”视频，
只要真人女装展示，排除横版、低于 1080P、明显水印和带货硬广。
```

检测到中文语音后，Skill 会要求选择删除人声、目标语言 AI 配音，或同时导出两种版本。

## 目录

```text
.
├── LICENSE
├── README.md
└── douyin-xhs-video-harvest/
    ├── SKILL.md
    ├── agents/openai.yaml
    ├── references/
    │   ├── condition-pool.md
    │   └── voice-localization.md
    └── scripts/media_guard.py
```

## 边界

只处理用户有权使用的素材。用于公开发布、商用或二次分发前，请自行确认授权。AI 配音不等于唇形同步；源视频中的烧录字幕需要单独处理。

## License

MIT，见 [LICENSE](LICENSE)。
