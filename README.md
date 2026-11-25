# AstrBot 表情包资源包

用于 AstrBot 插件「表情包管理器」（`meme_manager`）的自定义表情包仓库。

## 结构

```
.
├── manifest.json      # 包元信息与分类定义
├── memes/            # 每个分类一个目录，放图片
│   └── happy/
├── previews/
│   └── cover.jpg     # 资源广场封面图
└── SKILL.md          # 给 Agent 用的制作说明
```

## 安装到机器人

AstrBot 面板 → 插件 → 表情包管理器 → 资源广场 → 「按来源安装」：

| 字段 | 值 |
| --- | --- |
| 仓库 | `jayv00691-sudo/astrbot-meme-pack` |
| 分支 | `main` |
| 目录 | `.` |

## 添加表情

1. 把图片放进 `memes/<分类>/`，文件名随意，建议用有意义的英文或数字。
2. 修改 `manifest.json` 里的 `version`（例如 0.1.0 → 0.1.1），否则插件不会认为有新版本。
3. 提交并推送。
4. 在面板「可更新」里更新已安装的包。

## 分类

分类名固定，见 `manifest.json` 的 `categories`。没有图的分类可以留着空目录。
