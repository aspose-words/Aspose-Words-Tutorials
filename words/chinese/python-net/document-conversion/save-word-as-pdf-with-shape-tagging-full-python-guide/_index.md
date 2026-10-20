---
category: general
date: 2026-05-30
description: 在 Python 中将 Word 保存为 PDF 并进行形状标记。将 docx 转换为 PDF，使 PDF 可访问，并学习如何标记浮动形状以提升可访问性。
draft: false
keywords:
- save word as pdf
- convert docx to pdf
- convert word document pdf
- make pdf accessible
- how to tag shapes
language: zh
og_description: 使用 Python 将 Word 保存为 PDF 并为浮动形状添加标签以实现可访问性。学习在几分钟内将 docx 转换为 PDF 并使
  PDF 可访问。
og_title: 使用形状标记将 Word 保存为 PDF – 完整 Python 指南
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Save Word as PDF with shape tagging in Python. Convert docx to pdf,
    make pdf accessible, and learn how to tag floating shapes for better accessibility.
  headline: Save Word as PDF with Shape Tagging – Full Python Guide
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for Python via .NET runs on .NET Core, which is cross‑platform.
      Just install the appropriate runtime (`dotnet-sdk-6.0` or later) and the `aspose-words`
      package.
    question: Does this work on Linux?
  - answer: Absolutely. Wrap the `convert_word_to_accessible_pdf` call in a `for`
      loop that iterates over `os.listdir()` and filters for `*.docx`.
    question: Can I batch‑process a folder of .docx files?
  - answer: Iterate over `doc.get_child_nodes(aw.NodeType.SHAPE, True)` and set `shape.title`
      or `shape.alternative_text` before saving.
    question: What if I need to add custom alt text to each shape?
  - answer: 'The inline tagging respects the original layout; however, if you enable
      PDF/A compliance, some visual tweaks (like color profiles) might be applied
      automatically. ## Wrapping Up We’ve just covered how to **save Word as PDF**
      while ensuring that floating shapes are tagged correctly for accessibility.'
    question: Is there a way to keep the original layout exactly the same?
  type: FAQPage
tags:
- Aspose.Words
- PDF conversion
- Python
- Document automation
title: 将 Word 保存为 PDF 并进行形状标记 – 完整 Python 指南
url: /zh/python/document-conversion/save-word-as-pdf-with-shape-tagging-full-python-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 Word 保存为 PDF 并进行形状标记 – 完整 Python 指南

是否曾想过在 **将 Word 保存为 PDF** 的同时保持那些漂浮形状可被访问？你并不是唯一有此需求的人。在许多合规性要求严格的环境中，普通的 PDF 并不足够——屏幕阅读器需要正确的标签，尤其是悬浮在文字上方的形状。  

在本教程中，我们将通过一个完整、可运行的示例，演示如何 **将 docx 转换为 pdf**，配置 PDF 选项使输出既视觉正确 *又* 可访问，最后以正确的方式为形状添加标签。完成后，你将拥有一个可直接放入任何 Python 项目的单文件解决方案。

## 你将学到

- 加载包含漂浮形状（图片、文本框、图表）的 Word 文档。  
- 使用 Aspose.Words for Python via .NET **将 Word 文档 pdf** 并进行自定义标记。  
- 启用 *inline* 标记模式，使 PDF 符合可访问性标准。  
- 验证结果并处理常见问题，如缺失字体或图片过大。  

无需外部服务，无需晦涩的命令行技巧——只需纯 Python 代码和少量说明性注释。

## 前置条件

在开始之前，请确保你具备以下条件：

| 要求 | 原因 |
|------|------|
| Python 3.9+ | Aspose .Words for Python via .NET 包的最低要求。 |
| 已安装 `aspose-words` NuGet 包（通过 `pip install aspose-words`） | 提供示例中使用的 `aw` 命名空间。 |
| 一个至少包含一个漂浮形状（例如文本框）的 `.docx` 文件 | 用于演示标记功能。 |
| 可选：PDF/A‑1a 验证器（如 veraPDF），如果需要认证可访问性。 | 帮助确认 PDF 真正可访问。 |

如果你从未使用过 Aspose.Words，可以把它想象成文档操作的 “瑞士军刀”——功能远超内置的 `python-docx` 库，尤其在需要细粒度控制的 PDF 输出时。

## 步骤 1：安装并导入 Aspose.Words

首先——安装库并导入所需类。此步骤很短，但如果跳过，后面会遇到 `ImportError`。

```bash
pip install aspose-words
```

```python
# Step 1: Import the Aspose.Words namespace
import aspose.words as aw
```

> **小贴士：** 如果你在虚拟环境中工作，请在运行 `pip` 命令前激活它。这样可以保持项目依赖的整洁。

## 步骤 2：加载包含漂浮形状的 Word 文档

现在我们真正打开源文件。`Document` 构造函数接受路径或流，因此你可以从本地文件到 S3 对象任意提供。

```python
# Step 2: Load the source .docx
input_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(input_path)
```

> **为什么重要：** 加载文档后我们即可访问其内部节点树，漂浮形状在其中表现为 `Shape` 对象。如果文件不存在，Aspose 会抛出 `FileNotFoundError`，你可以捕获并优雅地处理。

## 步骤 3：配置 PDF 保存选项以实现可访问的形状标记

下面是本教程的核心。默认情况下，Aspose.Words 将漂浮形状保存为 *块级* 标签，许多辅助技术会将其视为独立的、非阅读顺序元素。将 `export_floating_shapes_as_inline_tag` 设置为 `True` 可强制形状以 *inline* 方式标记，保持阅读顺序并提升屏幕阅读器体验。

```python
# Step 3: Create PDF save options and enable inline shape tagging
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True   # True → inline (accessible) tagging
```

> **工作原理：** 当 `export_floating_shapes_as_inline_tag` 为 `True` 时，Aspose 会在每个形状周围注入 `<Figure>` 标签并将其置入文档流中。这是实现 **make pdf accessible** 合规性的推荐做法，尤其符合 WCAG 2.1 指南 1.3.1。

### 可选微调

| 选项 | 描述 | 常用取值 |
|------|------|----------|
| `pdf_opts.compliance` | 设置 PDF/A 合规级别（例如 PDF/A‑1a）。 | `aw.saving.PdfCompliance.PDF_A_1A` |
| `pdf_opts.embed_full_fonts` | 嵌入所有使用的字体以避免替代。 | `True` |
| `pdf_opts.save_format` | 强制输出格式（如果以后切换到 XPS 时很有用）。 | `aw.SaveFormat.PDF` |

如果项目对合规性要求更高，可以链式设置这些选项。

## 步骤 4：使用配置好的选项将文档保存为 PDF

最后，我们写出输出文件。`save` 方法接受目标路径和我们刚才配置的选项对象。

```python
# Step 4: Save the document as a PDF with the accessible tagging options
output_path = "YOUR_DIRECTORY/output.pdf"
doc.save(output_path, pdf_opts)
print(f"✅ PDF saved to {output_path}")
```

就这样——你的 **convert word document pdf** 操作完成。生成的 PDF 将把漂浮形状以内联标签形式保存，极大提升辅助技术的友好度。

## 验证可访问的 PDF

如果想进一步确认 PDF 确实符合可访问性标准，可在 Adobe Acrobat Pro 中打开并检查 **Tags** 面板。你应该能看到类似如下的条目：

```
/Figure
  /Alt (optional alt text you may have set)
  /Para
```

或者，运行命令行验证器：

```bash
verapdf --format text output.pdf
```

如果验证器返回 “No errors”，则说明你已经成功 **make pdf accessible**。

## 常见边缘情况及处理办法

| 场景 | 可能出现的问题 | 建议的解决方案 |
|------|----------------|----------------|
| **文档包含大量高分辨率图片** | PDF 文件体积膨胀，性能下降。 | 将 `pdf_opts.jpeg_quality = 80`，或在保存前使用 `doc.get_child_nodes(aw.NodeType.SHAPE, True)` 对图片进行降采样。 |
| **服务器缺少字体** | 文本使用回退字体，布局错乱。 | 启用 `pdf_opts.embed_full_fonts = True` 并确保所需字体已安装在操作系统上。 |
| **形状没有 alt 文本** | 可访问性工具只能读到 “Figure” 而无描述。 | 在保存前遍历形状并设置 `shape.title = "描述"`。 |
| **大型文档（>100 MB）** | 32 位运行时出现内存不足错误。 | 使用 `PdfSaveOptions.memory_usage_setting = aw.saving.MemoryUsageSetting.LOW` 进行流式写入。 |
| **需要 PDF/A‑2b 而非 PDF/A‑1a** | 合规性不匹配。 | 将 `pdf_opts.compliance = aw.saving.PdfCompliance.PDF_A_2B`。 |

提前处理这些情况，可避免后期再次修改转换逻辑。

## 完整工作示例

下面是完整脚本，可直接复制到名为 `convert_to_accessible_pdf.py` 的文件中。只需将 `YOUR_DIRECTORY` 替换为实际文件夹路径。

```python
import aspose.words as aw

def convert_word_to_accessible_pdf(input_docx: str, output_pdf: str) -> None:
    """
    Loads a Word document, configures PDF save options to tag floating shapes inline,
    and saves the result as an accessible PDF.
    """
    # Load the .docx file
    doc = aw.Document(input_docx)

    # Configure PDF options for accessible shape tagging
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True   # Inline tagging for accessibility
    pdf_opts.compliance = aw.saving.PdfCompliance.PDF_A_1A  # Optional: enforce PDF/A‑1a
    pdf_opts.embed_full_fonts = True                       # Ensure fonts are embedded

    # Save the PDF
    doc.save(output_pdf, pdf_opts)
    print(f"✅ Successfully saved accessible PDF to: {output_pdf}")

if __name__ == "__main__":
    # Adjust these paths as needed
    INPUT_PATH = "YOUR_DIRECTORY/input.docx"
    OUTPUT_PATH = "YOUR_DIRECTORY/output.pdf"

    convert_word_to_accessible_pdf(INPUT_PATH, OUTPUT_PATH)
```

运行脚本：

```bash
python convert_to_accessible_pdf.py
```

你应该会看到确认信息，`output.pdf` 将包含内联标记的形状，准备好供屏幕阅读器使用。

## 常见问答

**Q: 这在 Linux 上能运行吗？**  
A: 能。Aspose.Words for Python via .NET 基于 .NET Core，跨平台。只需安装相应的运行时（`dotnet-sdk-6.0` 或更高）以及 `aspose-words` 包。

**Q: 能批量处理一个文件夹中的 .docx 文件吗？**  
A: 当然。将 `convert_word_to_accessible_pdf` 调用包装在遍历 `os.listdir()` 并过滤 `*.docx` 的 `for` 循环中即可。

**Q: 如果需要为每个形状添加自定义 alt 文本怎么办？**  
A: 在保存前遍历 `doc.get_child_nodes(aw.NodeType.SHAPE, True)`，并为每个 `shape` 设置 `shape.title` 或 `shape.alternative_text`。

**Q: 有办法保持原始布局完全不变吗？**  
A: 内联标记会保留原始布局；但如果启用 PDF/A 合规，可能会自动应用一些视觉调整（如颜色配置文件）。

## 小结

我们已经介绍了如何 **将 Word 保存为 PDF**，并确保漂浮形状得到正确的可访问性标记。整个过程——加载、配置、保存——已经完整呈现。

## 接下来你可以学习什么？

- [Create Accessible PDF from Word – Convert to PDF/UA](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-word-convert-to-pdf-ua/)
- [Save Word as PDF with Aspose.Words – Complete C# Guide](/words/english/net/basic-conversions/save-word-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}