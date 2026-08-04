---
category: general
date: 2026-08-04
description: 使用 Aspose.Words 恢复模式恢复损坏的 docx 文件，并将 docx 转换为 markdown，导出公式为 LaTeX。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to use recovery mode
- export equations latex
language: zh
lastmod: 2026-08-04
og_description: 使用 Aspose.Words 恢复模式修复损坏的 docx 文件，然后将 docx 转换为 markdown，并将公式导出为 LaTeX。按照本分步指南，还可生成
  PDF 和 TXT 输出。
og_image_alt: Screenshot of Aspose.Words Python code converting a corrupted docx to
  markdown with LaTeX equations
og_title: 恢复损坏的 docx 并转换为 markdown – Aspose 指南
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  headline: Recover corrupted docx and convert to markdown with Aspose
  type: TechArticle
- description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  name: Recover corrupted docx and convert to markdown with Aspose
  steps:
  - name: Export floating shapes as inline tags
    text: Floating images or text boxes can cause layout issues when converting to
      PDF. Setting `export_floating_shapes_as_inline_tag` forces Aspose.Words to treat
      those shapes as regular inline elements, preserving the visual flow.
  - name: Adjust the shadow of the first shape
    text: You might want to enhance the appearance of a specific shape before saving
      the final PDF. The code below accesses the first `Shape` node, enables its shadow,
      and tweaks visual parameters.
  - name: Expected output
    text: '| File | Description | |------|-------------| | `output.md` | Markdown
      version of the original DOCX. All equations appear as LaTeX (`$...$` or `$$...$$`).
      | | `output.txt` | Plain‑text dump'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document conversion
title: 使用 Aspose 恢复损坏的 docx 并转换为 Markdown
url: /zh/python/document-conversion/recover-corrupted-docx-and-convert-to-markdown-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 恢复损坏的 docx 并使用 Aspose 转换为 markdown

如果您需要 **恢复损坏的 docx** 文件，Aspose.Words 提供了内置的恢复模式，能够自动修复受损的 Word 文档。文件恢复后，您可以 **将 docx 转换为 markdown**，甚至 **导出 LaTeX 形式的公式**，以便在科学文档中无缝使用。本教程将一步步演示在 Python 中如何完成这些操作，并提供 PDF 与纯文本输出的额外选项。

您将学习：

* 使用恢复模式加载可能损坏的 DOCX。  
* 将恢复后的文档保存为带有 LaTeX 公式的 Markdown。  
* 生成同样包含 LaTeX 公式的纯文本（TXT）版本。  
* 导出 PDF 时将浮动形状标记为内联元素。  
* 调整形状的阴影并生成最终的 PDF。

无需任何外部工具——只需免费版的 Aspose.Words for Python 库。

## 前置条件

| 要求 | 为什么重要 |
|------|------------|
| Python 3.8+ | Aspose.Words for Python 的最低版本要求 |
| `aspose-words` 包（`pip install aspose-words`） | 提供代码中使用的 `aw` 命名空间 |
| 可能受损的 DOCX 文件（例如 `corrupted.docx`） | 用于演示恢复工作流 |
| 对输出目录的写入权限 | 脚本会生成多个文件（`.md`、`.txt`、`.pdf`） |

如果超出评估限制，请确保已正确配置 Aspose.Words 许可证（免费试用或已购买）。

## 使用 Aspose.Words 恢复损坏的 docx

第一步是告诉 Aspose.Words 将输入文件视为可能损坏的文件。这通过 `LoadOptions.recovery_mode` 实现。

```python
import aspose.words as aw

# Step 1: Load a possibly corrupted document using recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # Enables automatic recovery of damaged files
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**为什么有效：**  
`RecoveryMode.RECOVER` 强制加载器忽略结构错误并尝试重建文档树。如果文件仅部分受损，大多数内容——包括文本、图像和公式——都会被恢复。

**提示：** 如果您只想验证文档而不进行修复，可使用 `RecoveryMode.NO_RECOVERY`。想要完整恢复，请保持如上所示的设置。

## 将 docx 转换为带 LaTeX 公式的 markdown

文档加载到内存后，即可将其保存为 Markdown。将 `office_math_export_mode` 设置为 `LATEX`，即可让 Aspose.Words 将每个 Word 公式渲染为 LaTeX 字符串。

```python
# Step 2: Save the document as Markdown while exporting equations in LaTeX format
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)
```

生成的 `output.md` 看起来像普通的 Markdown 文件，但每个公式都会以 `$...$`（行内）或 `$$...$$`（块级）形式出现。这对于 Pandoc、Jupyter Notebook 等能够识别 LaTeX 语法的下游工具至关重要。

## 如何在受损文件中使用恢复模式

恢复模式可以在任何加载操作中复用。下面提供了一个紧凑的模式，您可以直接复制到其他脚本中使用：

```python
def load_with_recovery(path: str) -> aw.Document:
    opts = aw.loading.LoadOptions()
    opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    return aw.Document(path, opts)
```

调用 `load_with_recovery("myfile.docx")` 将返回一个已经尝试修复的 `Document` 对象。该函数演示了 **如何在项目中安全使用恢复模式**。

## 导出公式 LaTeX 时保存为 markdown 与 txt

如果您还需要纯文本版本，同样的 `office_math_export_mode` 标志可与 `TxtSaveOptions` 配合使用。

```python
# Step 3: Save the same document as plain‑text (TXT) with LaTeX equations
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)
```

`.txt` 文件包含 Word 文档的原始文本，且每个公式都以 LaTeX 代码形式呈现。此格式便于索引或将内容喂入能够识别 LaTeX 的搜索引擎。

## 其他选项：带内联形状和形状阴影的 PDF

### 将浮动形状导出为内联标签

浮动的图片或文本框在转换为 PDF 时可能导致布局问题。设置 `export_floating_shapes_as_inline_tag` 可强制 Aspose.Words 将这些形状视为普通的内联元素，从而保持视觉流畅。

```python
# Step 4: Export the document to PDF and tag floating shapes as inline elements
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)
```

### 调整第一个形状的阴影

在生成最终 PDF 前，您可能想要增强特定形状的外观。下面的代码访问第一个 `Shape` 节点，启用其阴影并微调视觉参数。

```python
# Step 5: Adjust the shadow of the first shape and save the result
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0          # Controls shadow softness
shape_shadow.distance = 3.0      # Distance from the shape
shape_shadow.angle = 45          # Direction of the light source
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

**结果：** `shadowed.pdf` 与 `output.pdf` 外观相同，但第一个形状现在投射出细微的黑色阴影，可提升演示时的可读性。

## 完整可运行脚本

以下是整合所有步骤的完整脚本。将其复制到名为 `recover_and_convert.py` 的文件中，替换 `YOUR_DIRECTORY` 为实际路径，然后运行 `python recover_and_convert.py`。

```python
import aspose.words as aw

# -------------------------------------------------
# 1. Load the possibly corrupted DOCX using recovery mode
# -------------------------------------------------
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)

# -------------------------------------------------
# 2. Save as Markdown with LaTeX equations
# -------------------------------------------------
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)

# -------------------------------------------------
# 3. Save as plain‑text (TXT) with LaTeX equations
# -------------------------------------------------
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)

# -------------------------------------------------
# 4. Export to PDF, converting floating shapes to inline
# -------------------------------------------------
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)

# -------------------------------------------------
# 5. Add a shadow to the first shape and save a new PDF
# -------------------------------------------------
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0
shape_shadow.distance = 3.0
shape_shadow.angle = 45
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

### 预期输出

| 文件 | 描述 |
|------|------|
| `output.md` | 原始 DOCX 的 Markdown 版本。所有公式均以 LaTeX（`$...$` 或 `$$...$$`）形式出现。 |
| `output.txt` | 纯文本转储，包含 LaTeX 公式 |

## 接下来应该学习什么？

以下教程涵盖与本指南密切相关的主题，帮助您进一步掌握 API 功能并探索在项目中实现的替代方案。每个资源都提供完整的可运行代码示例和逐步解释。

- [如何使用 Markdown：将 DOCX 转换为带 LaTeX 公式的 Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-use-markdown-convert-docx-to-markdown-with-latex-equa/)
- [如何使用 Aspose.Words 恢复 docx – 步骤详解](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [恢复损坏的 DOCX 并将 Word 转换为 Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}