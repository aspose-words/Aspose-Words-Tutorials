---
category: general
date: 2026-11-25
description: 了解如何使用 Aspose.Words 将 docx 保存为 pdf、将 docx 转换为 pdf，并在一步操作中将浮动形状导出为内联标签。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx as pdf
- convert docx to pdf
- how to export shapes
- convert word to pdf
- aspose docx to pdf
language: zh
lastmod: 2026-11-25
og_description: 使用 Aspose.Words 将 docx 保存为 PDF，转换 docx 为 PDF，并学习如何将形状导出为内联标签，以实现完美的
  PDF 输出。
og_image_alt: Screenshot showing a DOCX file being saved as PDF with shapes preserved
og_title: 使用 Aspose.Words 将 docx 保存为 PDF – 正确导出形状
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to save docx as pdf using Aspose.Words, convert docx to pdf,
    and export floating shapes as inline tags in a single step.
  headline: How to save docx as pdf with Aspose.Words while exporting shapes
  type: TechArticle
- description: Learn how to save docx as pdf using Aspose.Words, convert docx to pdf,
    and export floating shapes as inline tags in a single step.
  name: How to save docx as pdf with Aspose.Words while exporting shapes
  steps:
  - name: Converting multiple DOCX files in a batch
    text: 'When you need to **convert docx to pdf** for many files, wrap the three
      steps in a loop:'
  - name: Dealing with very large documents
    text: For large Word files, consider enabling `pdf_opts.save_format = aw.SaveFormat.PDF`
      (the default) and adjusting `pdf_opts.compliance` if you need PDF/A compliance.
      These options do not affect shape export but improve compatibility with archival
      systems.
  - name: When shapes should remain floating
    text: If a specific document requires floating shapes to stay floating (e.g.,
      a design‑heavy brochure), set the flag to `False`. The PDF will then render
      shapes as separate drawing objects, which may be preferable for precise graphic
      positioning.
  type: HowTo
tags:
- Aspose.Words
- PDF conversion
- Word automation
title: 如何在导出形状时使用 Aspose.Words 将 docx 保存为 PDF
url: /zh/python/document-conversion/how-to-save-docx-as-pdf-with-aspose-words-while-exporting-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 在导出形状时将 docx 保存为 pdf

如果您需要 **save docx as pdf** 并且保持每个浮动形状恰好位于其所在位置，本指南将向您展示完整的过程。教程结束时，您将能够将 Word 文档转换为 PDF 文件，正确导出形状，并了解每个设置的意义。

将 Word 文件转换为 PDF 是发票生成、报告发布和文档归档的常见需求。本教程涵盖 **convert docx to pdf** 工作流，解释 **how to export shapes** 使其以内联形式出现，并演示使用 Aspose.Words 库进行 **convert word to pdf** 操作。除 Aspose.Words for Python via .NET 包外，无需其他外部工具。

## 前提条件

* 已在开发机器上安装 Python 3.9+。  
* `aspose-words` 包（可通过 `pip install aspose-words` 安装）。  
* 包含浮动形状（例如文本框、图片或 SmartArt）的 DOCX 文件。  
* 对输出目录具有写入权限。

所有这些前提条件均为自由形式；本教程可在 Windows、macOS 和 Linux 上运行。

## 步骤 1：加载源文档

第一步是将 DOCX 文件加载到 `aw.Document` 对象中。该对象在内存中表示整个 Word 文档，提供对其章节、段落和绘图对象的访问。

```python
import aspose.words as aw

# Step 1: Load the source document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

**此步骤的重要性：**  
加载文件会创建 Aspose.Words 可操作的结构化对象模型。没有此模型，后续的 PDF 转换将没有来源可读取。

## 步骤 2：配置 PDF 保存选项并启用浮动形状的内联导出

Aspose.Words 提供了 `PdfSaveOptions` 类，可让您微调输出 PDF。属性 `export_floating_shapes_as_inline_tag` 控制浮动形状是渲染为内联 `<w:wrap>` 标记（PDF 渲染器将其视为文本流的一部分），还是作为独立的绘图对象。

```python
# Step 2: Create PDF save options and enable inline export for floating shapes
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True
```

**此设置的重要性：**  
当您正确 **how to export shapes** 时，可避免形状消失或在 PDF 中移动到意外位置的常见问题。将该标志设为 `True` 告诉渲染器将每个浮动形状视为内联锚定，从而保持布局的忠实度。这是大多数业务文档推荐的做法。

## 步骤 3：使用配置好的选项将文档保存为 PDF

在文档已加载且保存选项已准备好的情况下，您现在可以将 PDF 文件写入磁盘。

```python
# Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

**此最终步骤完成工作流的原因：**  
使用 `PdfSaveOptions` 实例调用 `doc.save` 会触发转换管道。Aspose.Words 读取 DOCX 结构，应用内联形状规则，并写入与原始布局相匹配的 PDF。此调用后，`output.pdf` 包含与源 DOCX 相同的文本、图像和形状。

## 预期输出

* `output.pdf` 出现在目标文件夹中。  
* 所有段落、表格和浮动形状（文本框、图片、SmartArt）的位置与 `input.docx` 中完全一致。  
* 文件大小与未进行形状导出调整的普通 Word 文档生成的标准 PDF 相当。

如果您在 Adobe Acrobat 或任何现代查看器中打开 PDF，应该看不到缺失的图形，也没有位移的元素。

## 常见变体和边缘情况

### 批量转换多个 DOCX 文件

当您需要对多个文件 **convert docx to pdf** 时，可将这三个步骤放入循环中：

```python
import pathlib

source_dir = pathlib.Path("YOUR_DIRECTORY")
for docx_path in source_dir.glob("*.docx"):
    doc = aw.Document(str(docx_path))
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True
    pdf_path = docx_path.with_suffix(".pdf")
    doc.save(str(pdf_path), pdf_opts)
```

### 处理超大文档

对于大型 Word 文件，考虑启用 `pdf_opts.save_format = aw.SaveFormat.PDF`（默认）并在需要 PDF/A 合规时调整 `pdf_opts.compliance`。这些选项不影响形状导出，但可提升与归档系统的兼容性。

### 当形状应保持浮动时

如果特定文档要求浮动形状保持浮动（例如设计密集的宣传册），将标志设为 `False`。PDF 将把形状渲染为独立的绘图对象，这在精确图形定位时可能更合适。

## 专业技巧

* **专业提示：** 始终在目标查看器（例如 Chrome、Edge、Acrobat）上测试 PDF，因为某些查看器对内联标签的解释略有不同。  
* **注意事项：** 使用旧版 VML 绘图格式的文档；Aspose.Words 会自动将 VML 转换为现代绘图对象，但复杂的 VML 可能需要额外清理。  
* **性能提示：** 在处理大量文件时复用同一个 `PdfSaveOptions` 实例，以减少对象分配开销。

## 完整、可运行的示例

下面是完整的脚本，您可以复制粘贴到名为 `docx_to_pdf.py` 的文件中。将 `YOUR_DIRECTORY` 替换为您机器上的实际路径。

```python
import aspose.words as aw
import pathlib

def convert_docx_to_pdf(input_path: pathlib.Path, output_path: pathlib.Path):
    """
    Loads a DOCX file, configures PDF save options to export floating shapes as inline tags,
    and writes the result to a PDF file.
    """
    # Load the DOCX document
    doc = aw.Document(str(input_path))

    # Configure PDF options – export floating shapes as inline tags
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True

    # Save the PDF
    doc.save(str(output_path), pdf_opts)

if __name__ == "__main__":
    base_dir = pathlib.Path("YOUR_DIRECTORY")
    input_file = base_dir / "input.docx"
    output_file = base_dir / "output.pdf"

    convert_docx_to_pdf(input_file, output_file)
    print(f"Conversion complete: {output_file}")
```

运行 `python docx_to_pdf.py` 将生成包含所有形状的 `output.pdf`。该脚本演示了 **aspose docx to pdf** 能力，以简洁、可复用的函数形式呈现。

## 结论

现在您已经了解如何使用 Aspose.Words **save docx as pdf**，以及在控制形状导出时 **convert docx to pdf** 的方法，并且明白 `export_floating_shapes_as_inline_tag` 标志是可靠布局保留的关键。此方法适用于 **convert word to pdf** 场景，支持批量处理，并为您提供按文档调整形状处理的灵活性。

接下来，探索相关主题，例如 **adding watermarks to PDFs**、**compressing PDF output** 或 **converting DOCX to other formats**（如 HTML 或 EPUB）。这些功能都基于您在此使用的相同 `aw.Document` 对象模型，您可以自信地扩展自动化流水线。

祝编码愉快，享受无缝的 PDF 结果！

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术紧密相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方法。

- [如何在 Python 中使用 Aspose.Words 将 docx 保存为 pdf](/words/english/python-net/document-conversion/how-to-save-docx-as-pdf-with-aspose-words-in-python/)
- [在 C# 中将 Word 保存为 PDF – 完整指南：使用形状导出将 DOCX 转换为 PDF](/words/english/net/programming-with-pdfsaveoptions/save-word-as-pdf-in-c-full-guide-to-convert-docx-to-pdf-with/)
- [使用 Aspose.Words 将 docx 保存为 pdf 并检测缺失字体](/words/english/net/working-with-fonts/save-docx-as-pdf-detect-missing-fonts-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}