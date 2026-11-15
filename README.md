# Proxmox VE 中文文档下载

这里是 **Proxmox VE 9.2.13 非官方简体中文文档的公开下载仓库**，用于发布 EPUB、PDF、离线 HTML 和完整源码归档。可编辑文档、完整译文映射及构建脚本公开于 [源码仓库 Thweki/pve-docs-zh-cn](https://github.com/Thweki/pve-docs-zh-cn)。

## 下载版本

请从 [Releases](https://github.com/Thweki/pve-docs-zh-cn-releases/releases) 下载已发布的文件。当前发行标签为 **`v9.2.13-zh.2`**，对应上游文档版本 **9.2.13**。

| 文件格式 | 内容与用途 |
| --- | --- |
| EPUB | 完整电子书，适合电子书阅读器和移动设备。 |
| PDF | 完整分页版本，适合检索、打印及归档。 |
| 离线 HTML ZIP | 解压后在浏览器中离线阅读完整文档。 |
| Source ZIP | 完整可编辑源码、原始输入快照、有效译文映射、构建脚本及开放字体。 |
| SHA256 校验文件 | 校验每份下载文件的完整性。 |

在线阅读：[GitBook 完整中文文档](https://thweki.gitbook.io/pve-docs-zh-cn/)。

## 内容范围

- 完整管理手册及附录，按原始 **29 个章节**组织；每章及其全部子节在同一页完整呈现。
- **29 份**命令、服务和配置参考手册，每篇同页。
- 完整 **680 个 API 操作**及请求参数、返回结构、权限说明，按资源组同页组织。
- 保留原始图片、技术图、命令、配置、代码示例、表格、提示框、脚注与交叉引用。

这是由 AI 辅助完成的非官方译文，未经 Proxmox 官方审核。截图保持原图，图中英文界面文字不重绘。遇到译文歧义，请对照 [Proxmox VE 官方文档](https://pve.proxmox.com/pve-docs/)。

## 来源与许可证

原始文档 Copyright (C) 2015–2026 Proxmox Server Solutions GmbH。文档及中文译文依据 **GNU Free Documentation License 1.3 或更新版本**分发，无不变章节、无封面文字、无封底文字，完整条款见 [LICENSE](LICENSE)。

API JavaScript 程序及构建程序的 AGPL、原始 AsciiDoc 脚本的 GPL、开放字体的 SIL OFL 许可分别保留；详情及对应源地址见 [NOTICE.md](NOTICE.md)、[LICENSES](LICENSES) 和 [字体许可及来源](export-assets/fonts)。本仓库保留声明和许可文件，字体程序、完整文档及可重建输入随正式下载归档提供。

技术问题及翻译更正请提交到 [源码仓库 Issues](https://github.com/Thweki/pve-docs-zh-cn/issues)。

## 元数据校验

使用 Python 3.9 或更新版本，无需安装依赖：

```sh
python3 scripts/validate_metadata.py
python3 -m unittest discover -s tests -v
```

校验字体来源清单的字段、固定提交与 SHA256 格式，两份本地 OFL 文件的字节数和哈希，README/NOTICE 的发行及上游版本，以及两份文档中行内 Markdown 链接的本地文件或目录目标（不检查锚点）。GitHub Actions 在检出后离线运行相同命令，不下载字体或安装依赖。

四份字体二进制文件仅随发行归档提供，本校验不要求它们存在，也不核对其实际哈希。不检查远程链接、发行资产、源码归档内容或译文数量。根目录 GFDL 文本的完整性校验留待独立许可证修复后添加；本校验不修改或固定该文本。

## 生成发行说明

将本次实际改动写入一个 UTF-8 Markdown 文件（例如 `changes.md`），再运行：

```sh
python3 scripts/generate_release_notes.py changes.md
```

此只读工具离线输出可供审阅的中文发行说明，包含改动摘要、README 的“下载版本”和“内容范围”章节，以及对应发行标签的来源与许可证链接。它复用元数据校验器检查 README/NOTICE 的版本一致性；摘要为空、所需章节缺失或版本冲突时返回非零状态，不输出部分说明。默认读取脚本所在仓库，也可用 `--root PATH` 指定其他检出目录。

确认输出后可用 `> release-notes.md` 保存，再手动用于 GitHub Release；输入摘要和输出文件须使用不同路径。工具不推断历史改动、不检查附件或远程链接，也不创建标签或发布发行。发布前请确认标签指向包含相应声明文件的提交，并审阅摘要及下载说明。仅需 Python 3.9 或更新版本，测试已纳入上述 unittest 命令。
