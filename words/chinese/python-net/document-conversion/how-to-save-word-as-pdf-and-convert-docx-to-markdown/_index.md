---
category: general
date: 2026-10-23
description: 学习如何使用 Aspose.Words for Python 将 Word 保存为 PDF 并将 DOCX 转换为 Markdown，支持恢复模式和
  LaTeX 数学。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word as pdf
- convert docx to markdown
- enable recovery mode
- markdown latex math
- export equations latex
language: zh
lastmod: 2026-10-23
og_description: 使用 Aspose.Words for Python 将 Word 保存为 PDF 并将 DOCX 转换为 Markdown。本指南涵盖恢复模式、LaTeX
  数学导出以及 PDF 形状处理。
og_image_alt: Screenshot illustrating how to save Word as PDF using Aspose.Words in
  Python
og_title: 将 Word 保存为 PDF 并将 DOCX 转换为 Markdown – 完整的 Python 指南
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to save Word as PDF and convert DOCX to Markdown using Aspose.Words
    for Python, with recovery mode and LaTeX math support.
  headline: How to save Word as PDF and convert DOCX to Markdown
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF conversion
- Markdown
- LaTeX
title: 如何将 Word 保存为 PDF 并将 DOCX 转换为 Markdown
url: /zh/python/document-conversion/how-to-save-word-as-pdf-and-convert-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何将 Word 保存为 PDF 并将 DOCX 转换为 Markdown

如果您需要 **将 Word 保存为 PDF**，同时将同一个 DOCX 文件转换为 Markdown，本教程将为您展示一个可重复使用的完整工作流。您将看到 Aspose.Words for Python 如何处理损坏的源文件、将公式导出为 LaTeX，并在 PDF 输出中对浮动形状进行细粒度控制。

本指南逐步演示每一步所需的导入、选项配置以及保存调用，您可以直接复制粘贴脚本到项目中使用。

![展示如何使用 Aspose.Words for Python 将 Word 保存为 PDF 的流程图](image-placeholder.png "展示将 Word 保存为 PDF 的工作流")

## 前置条件

在开始之前，请确保您已具备：

* 已安装 Python 3.8+。
* 有效的 Aspose.Words for Python 许可证（或免费试用版）。
* 通过 `pip install aspose-words` 安装了 `aspose-words` 包。
* 一份需要处理的 DOCX 文件（示例使用 `input.docx`）。

准备好以上内容后，代码即可直接运行，无需额外的设置步骤。

## 步骤 1：加载源文档

首先需要打开 DOCX 文件。Aspose.Words 会将文件读取为 `Document` 对象，后续所有保存操作都基于该对象。

```python
import aspose.words as aw

# Load the DOCX file from the file system
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

> **为什么重要：** 加载文档后会在内存中创建一个表示，这样您可以在不重新读取文件的情况下应用不同的保存选项。

## 步骤 2：启用恢复模式以优雅地处理损坏的文档

如果源 DOCX 可能已损坏——缺少部分、XML 损坏或出现意外流——请启用 **恢复模式**。这会让 Aspose.Words 忽略非关键错误并仍然生成输出。

```python
# Configure load options for recovery
load_opts = aw.LoadOptions()
load_opts.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER
# Re‑load the document using the recovery options
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_opts)
```

> 在批量处理流水线中，**启用恢复模式** 特别有用，因为单个损坏的文件不应导致整个过程停止。

## 步骤 3：准备 Markdown 保存选项 – 将 Office Math 公式导出为 LaTeX

在 **将 DOCX 转换为 Markdown** 时，通常希望公式以 LaTeX 形式出现，以便下游工具（如 Jupyter、静态站点生成器）能够正确渲染。

```python
# Markdown options with LaTeX export for equations
md_opts = aw.saving.MarkdownSaveOptions()
md_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

> **Markdown LaTeX 数学** 支持可确保复杂公式在转换过程中保持原样，保留科学精度。

## 步骤 4：准备纯文本保存选项 – 同样将 Office Math 导出为 LaTeX

即使您只需要 `.txt` 版本，将公式保留为 LaTeX 对后续解析也很有价值。

```python
# Plain‑text options with LaTeX export
txt_opts = aw.saving.TxtSaveOptions()
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

## 步骤 5：准备 PDF 保存选项 – 控制浮动形状的标签方式

浮动形状（文本框、图片）在 PDF 中可以表现为内联标签或独立对象。下面的选项将它们保持为内联，这符合多数可访问性工具的偏好。

```python
# PDF options controlling floating shape handling
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True  # Set to False to keep separate
```

> **导出公式为 LaTeX** 已由 PDF 引擎自动处理；在 PDF 路径中无需单独的 LaTeX 标志。

## 步骤 6：以所有期望的格式保存文档

现在您已经拥有三个完整配置的选项对象。对每种格式调用一次 `doc.save` 即可写出相应的输出文件。

```python
# Save as Markdown (with LaTeX math)
doc.save("YOUR_DIRECTORY/output.md", md_opts)

# Save as plain text (with LaTeX math)
doc.save("YOUR_DIRECTORY/output.txt", txt_opts)

# Save as PDF (with inline‑tagged floating shapes)
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

### 预期结果

| 输出文件 | 关键特性 |
|----------|----------|
| `output.md` | Markdown 文本，公式以 `$$...$$` LaTeX 块形式出现 |
| `output.txt` | 纯文本表示，LaTeX 公式内联 |
| `output.pdf` | 原始布局的 PDF 渲染，浮动形状以内联标签方式标记 |

您可以在相应的查看器中打开每个文件，以验证转换是否成功。

## 如何使用自定义选项将 Word 保存为 PDF

如果您的唯一目标是 **将 Word 保存为 PDF**，可以跳过 Markdown 和 TXT 步骤，仅关注 PDF 选项：

```python
# Minimal script to save only PDF
import aspose.words as aw

doc = aw.Document("YOUR_DIRECTORY/input.docx")
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

此代码片段演示了在 **将 Word 保存为 PDF** 时仍然能够控制形状标签的最简方式。

## 为批量转换启用恢复模式

在处理大量文件时，可将加载‑保存逻辑放入循环，并复用同一个 `LoadOptions` 对象：

```python
import os
import aspose.words as aw

load_opts = aw.LoadOptions()
load_opts.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER

for filename in os.listdir("batch_input"):
    if filename.lower().endswith(".docx"):
        path = os.path.join("batch_input", filename)
        doc = aw.Document(path, load_opts)

        # Save PDF only (example)
        pdf_path = os.path.join("batch_output", filename.replace(".docx", ".pdf"))
        pdf_opts = aw.saving.PdfSaveOptions()
        pdf_opts.export_floating_shapes_as_inline_tag = True
        doc.save(pdf_path, pdf_opts)
```

> **专业提示：** 记录 Aspose.Words 返回的任何 `LoadWarning` 信息；这些信息指示了损坏文件的哪些部分已被修复。

## 在 Markdown 与纯文本中导出 LaTeX 公式

`MarkdownSaveOptions` 与 `TxtSaveOptions` 都暴露了相同的 `office_math_export_mode` 属性。将其设为 `LATEX` 可让引擎将 Office Math XML 转换为 LaTeX 语法。如果您更倾向于使用图片，则将枚举改为 `IMAGE`。

```python
md_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.IMAGE  # Alternative
```

选择符合您下游渲染管道的模式即可。

## 保存 Word 为 PDF 时控制浮动形状

`export_floating_shapes_as_inline_tag` 标志决定形状是作为文本流的一部分 (`True`) 还是保持独立 (`False`)。内联标签可提升文本提取的准确性。

## 接下来该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并探索在项目中的其他实现方式。每篇资源均提供完整可运行的代码示例以及逐步解释。

- [How to Export LaTeX from Word: Convert DOCX to Markdown & Save as PDF](/words/english/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/)
- [Save Word as PDF in C# – Full Guide to Convert DOCX to PDF with Shape Export](/words/english/net/programming-with-pdfsaveoptions/save-word-as-pdf-in-c-full-guide-to-convert-docx-to-pdf-with/)
- [How to export LaTeX from Word and convert DOCX to Markdown](/words/english/python-net/document-conversion/how-to-export-latex-from-word-and-convert-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}