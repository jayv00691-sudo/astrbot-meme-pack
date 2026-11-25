---
name: astrbot-meme-pack
description: "制作、校验并发布 AstrBot 表情包管理器（meme_manager）的自定义表情包仓库。当需要新增表情图片、调整分类、更新 manifest.json 版本、或把表情包发布到 GitHub 供插件安装时使用。"
---

# AstrBot 表情包仓库制作

## 适用场景

- 给 AstrBot 的 `meme_manager` 插件做自定义表情包
- 往已有表情包仓库补图、改分类、发新版本
- 排查「按来源安装」失败的原因

## 仓库结构

```
.
├── manifest.json
├── memes/<category>/*.png|jpg|gif|webp
└── previews/cover.jpg
```

分类名固定为：`angry baka color confused cpu fool givemoney happy like meow morning reply sad see shy sigh sleep surprised work`。

## manifest.json 必填字段

| 字段 | 说明 |
| --- | --- |
| `schema_version` | 固定 `1` |
| `id` | 唯一包 ID，仅小写字母、数字、`.` `_` `-` |
| `name` | 展示名称 |
| `version` | 语义化版本，**每次改动都要递增** |
| `description` | 一句话说明 |
| `maintainer` | GitHub 用户名 |
| `license` | 许可证，例如 `CC-BY-NC-SA-4.0` |
| `tags` | 字符串数组 |
| `source` | `{type: "github", repo, ref, subpath}` |
| `categories` | 只写实际有图的分类，每个给 `description` |

## 操作步骤

1. 确认要新增的分类，在 `memes/` 下建同名目录。
2. 放入图片。建议单张不超过 1 MB，格式优先 png / jpg / gif / webp。
3. 若新增了分类，同步在 `manifest.json` 的 `categories` 里补 `description`。
4. 递增 `version`。
5. 提交并推送。
6. 在 AstrBot 面板的「可更新」里更新已安装的包。

## 安装（给使用者）

面板 → 插件 → 表情包管理器 → 资源广场 → 「按来源安装」：

- 仓库：`owner/repo`，**不要贴完整 URL**
- 分支/标签：`main`
- 目录：根目录填 `.`

## 常见失败原因

| 现象 | 原因 |
| --- | --- |
| 安装报错说格式不对 | 仓库字段填了 URL，应填 `owner/repo` |
| 装上了但没有表情 | `memes/` 下的分类目录名不在固定列表里 |
| 更新后没变化 | `version` 没递增 |
| 拉取失败 | 仓库私有，或默认分支不是填的那个 |

## 校验清单

- [ ] `manifest.json` 能被 JSON 解析
- [ ] `id` 只含小写字母、数字、`.` `_` `-`
- [ ] 每个有图的目录名都在固定分类列表里
- [ ] `version` 已递增
- [ ] `source.repo` 与实际仓库一致
