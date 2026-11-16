---
category: general
date: 2026-11-15
description: 使用 Aspose.Words 在 Python 中将 Word 保存为 PDF，了解如何导出形状并将浮动形状标记为内联，以实现准确的 docx
  到 PDF 转换。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word as pdf
- convert docx to pdf
- how to export shapes
- how to convert docx
- how to tag shapes
language: zh
lastmod: 2026-11-15
og_description: 使用 Aspose.Words 在 Python 中将 Word 保存为 PDF。本指南展示了如何导出形状、将浮动形状标记为内联，以及可靠地将
  docx 转换为 PDF。
og_image_alt: Screenshot of Python code that saves a Word document as PDF with shape
  tagging
og_title: 使用 Python 将 Word 保存为带形状标签的 PDF – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Save Word as PDF in Python using Aspose.Words, learn how to export
    shapes and tag floating shapes as inline for accurate docx to PDF conversion.
  headline: How to save Word as PDF with shape tagging in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF conversion
title: 如何在 Python 中将 Word 保存为带有形状标签的 PDF
url: /zh/python/document-conversion/how-to-save-word-as-pdf-with-shape-tagging-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Python 将 Word 保存为 PDF 并进行形状标记

如果您需要 **save Word as PDF** 并保持每个绘图恰好位于其所在位置，本指南将向您展示使用 Aspose.Words for Python 的可靠方法。您还将学习 **how to export shapes** 和 **how to tag shapes**，以便在转换过程中将浮动对象变为内联元素。

在本教程中，我们将覆盖：

* 将 DOCX 文件转换为 PDF (`convert docx to pdf`)  
* 将浮动形状导出为内联标签 (`how to export shapes`)  
* 在 PDF 保存操作期间标记形状 (`how to tag shapes`)  

无需外部工具——只需几行 Python 代码。

## 前提条件

在开始之前，请确保您拥有：

* 已安装 Python 3.8+  
* 有效的 Aspose.Words for Python 许可证（或免费试用）  
* `aspose-words` 包已安装 (`pip install aspose-words`)  
* 一个包含浮动形状（图片、文本框等）的 DOCX 文件 (`input.docx`)

## 第一步：安装并导入 Aspose.Words

首先，将库添加到您的环境中并在脚本中导入它。

```python
# Install the package (run once):
# pip install aspose-words

import aspose.words as aw
```

*Why?* `aspose.words` 模块提供了我们控制形状处理所需的 `Document` 类和 `PdfSaveOptions`。

## 第二步：加载 Word 文档

使用 `Document` 构造函数读取源文件。

```python
# Load the Word document you want to convert
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

如果文件不存在，Aspose.Words 会抛出 `FileNotFoundError`。在生产代码中请将调用包装在 `try/except` 块中。

## 第三步：配置 PDF 保存选项 – 导出并标记形状

干净转换的关键是 `PdfSaveOptions` 对象。将 `export_floating_shapes_as_inline_tag` 设置为 `True` 会告诉引擎将浮动绘图视为内联元素，从而消除生成的 PDF 中的布局偏移。

```python
# Create PDF save options and enable inline tagging for floating shapes
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True  # how to tag shapes
```

*Why?* 当 `export_floating_shapes_as_inline_tag` 为 `False`（默认值）时，浮动形状保留其原始位置元数据，这可能导致它们在 PDF 中出现位置错误。启用内联标签会强制 Aspose.Words 嵌入一个小的 XML 标签，PDF 渲染器将其解释为内联对象，从而保持视觉保真度。

## 第四步：将文档保存为 PDF

现在使用配置好的选项写入 PDF 文件。

```python
# Save the document as a PDF, applying the shape‑tagging options
output_path = "YOUR_DIRECTORY/output.pdf"
doc.save(output_path, pdf_opts)

print(f"PDF saved to {output_path}")
```

执行后，`output.pdf` 包含原始 Word 布局，所有浮动形状均正确渲染为内联元素。

## 第五步：验证转换（可选）

您可以通过编程方式验证 PDF 已创建且至少包含一页：

```python
import os
from aspose.pdf import Document as PdfDocument

if os.path.exists(output_path):
    pdf_doc = PdfDocument(output_path)
    print(f"PDF has {pdf_doc.pages.count} page(s).")
else:
    raise FileNotFoundError("PDF was not created.")
```

*Tip:* 使用 PDF 查看器仔细检查图片、文本框和标注是否恰好出现在 DOCX 文件中的位置。

## 常见变体和边缘情况

| 情况 | 需要更改的内容 |
|-----------|----------------|
| **您需要保持浮动形状为浮动状态** | Set `pdf_opts.export_floating_shapes_as_inline_tag = False`. |
| **批量转换多个文件** | 遍历文件路径列表并复用单个 `PdfSaveOptions` 实例。 |
| **您想嵌入密码** | 在调用 `save` 之前使用 `pdf_opts.encrypt_options.password = "your‑password"`。 |
| **大文档导致内存压力** | 启用 `pdf_opts.memory_optimization = True` 以降低 RAM 使用。 |

## 专业提示：处理缺失字体

如果源 DOCX 使用的字体未在服务器上安装，PDF 渲染可能会回退到默认字体。使用 `FontSettings` 注册缺失的字体：

```python
font_settings = aw.FontSettings()
font_settings.set_fonts_folder("YOUR_DIRECTORY/fonts", recursive=True)
doc.font_settings = font_settings
```

这可确保 PDF 与原始 Word 文件的外观完全一致。

## 完整可运行示例

```python
import aspose.words as aw
import os

def convert_docx_to_pdf(input_path: str, output_path: str) -> None:
    """
    Saves a Word document as PDF while tagging floating shapes as inline.
    """
    # Load the DOCX
    doc = aw.Document(input_path)

    # Optional: register custom fonts
    # font_settings = aw.FontSettings()
    # font_settings.set_fonts_folder("fonts", recursive=True)
    # doc.font_settings = font_settings

    # Configure PDF options to export shapes as inline tags
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True  # how to tag shapes

    # Save as PDF
    doc.save(output_path, pdf_opts)
    print(f"PDF saved to {output_path}")

if __name__ == "__main__":
    INPUT = "YOUR_DIRECTORY/input.docx"
    OUTPUT = "YOUR_DIRECTORY/output.pdf"

    if not os.path.isfile(INPUT):
        raise FileNotFoundError(f"Input file not found: {INPUT}")

    convert_docx_to_pdf(INPUT, OUTPUT)

    # Verify creation
    if os.path.isfile(OUTPUT):
        from aspose.pdf import Document as PdfDocument
        pdf = PdfDocument(OUTPUT)
        print(f"Conversion successful – PDF has {pdf.pages.count} page(s).")
    else:
        raise RuntimeError("PDF conversion failed.")
```

运行脚本会生成 `output.pdf`，其中所有浮动形状均已正确标记，为您提供干净的 **save word as pdf** 结果。

## 结论

您现在了解如何在 Python 中 **save Word as PDF** 并控制形状处理。通过配置 `PdfSaveOptions.export_floating_shapes_as_inline_tag`，您可以可靠地 **convert docx to pdf**，将 **export shapes** 为内联标签，并在转换过程中解答 **how to tag shapes**。

接下来您可以探索：

* 添加水印 (`pdf_opts.add_watermark`) – PDF 定制的自然扩展。  
* 使用相同的 `save` 模式转换其他格式（HTML、EPUB）。  
* 为大型文档库自动化批量转换。

运行脚本，尝试可选设置，并将其集成到您的文档处理流水线中。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在自己的项目中探索替代实现方法。

- [保存 Word 为 PDF – 使用 Aspose.Words 将形状转换为内联](/words/english/python-net/document-conversion/save-word-as-pdf-convert-shapes-to-inline-with-aspose-words/)
- [如何使用 Aspose.Words for Python 保存 Word 为 PDF](/words/english/python-net/document-conversion/how-to-save-word-as-pdf-with-aspose-words-for-python/)
- [如何使用 Aspose.Words 在 Python 中将 DOCX 转换为 PDF](/words/english/python-net/document-conversion/how-to-convert-docx-to-pdf-in-python-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}