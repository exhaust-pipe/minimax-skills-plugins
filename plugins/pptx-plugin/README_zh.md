# PPTX Plugin

[English](./README.md)

## 快速参考

| 任务 | 指南 |
|------|------|
| 读取/分析内容 | `python -m markitdown presentation.pptx` |
| 编辑或基于模板创建 | 阅读 `ppt-editing-skill` |
| 从零创建 | 使用 subagents + PptxGenJS，见下文 |

---

## 读取内容

```bash
# 文本提取
python -m markitdown presentation.pptx
```

---

## 编辑工作流

**完整细节请阅读 `ppt-editing-skill`。**

1. 使用 `markitdown` 分析模板
2. 解包 → 操作幻灯片 → 编辑内容 → 清理 → 打包

---

## 从零创建

**当没有模板或参考演示文稿时使用。**

1. 搜索并理解用户需求
2. 使用 color-font-skill 选择配色和字体
3. 阅读 ppt-orchestra-skill 设计 PPT 大纲
4. 派生 subagents 创建 slide JS 文件（最多 5 个并发）
5. 将所有 slide 模块编译成最终 PPTX

### Subagent 类型

- `cover-page-generator` - 封面页
- `table-of-contents-generator` - 目录页
- `section-divider-generator` - 章节过渡页
- `content-page-generator` - 内容页
- `summary-page-generator` - 总结/CTA 页

### 输出结构

```
slides/
├── slide-01.js          # Slide modules
├── slide-02.js
├── ...
├── imgs/                # Images used in slides
└── output/              # Final artifacts
    └── presentation.pptx
```

### 告诉 Subagents

1. 文件命名：`slides/slide-01.js`、`slides/slide-02.js`
2. 图片放在：`slides/imgs/`
3. 最终 PPTX 放在：`slides/output/`
4. 尺寸：10" × 5.625"（LAYOUT_16x9）
5. 字体：中文=Microsoft YaHei，英文=Arial
6. 颜色：不带 # 的 6 位十六进制（例如 `"FF0000"`）

---

## QA 与依赖

QA 流程和依赖见 **ppt-orchestra-skill**。
