---
category: general
date: 2026-09-27
description: 使用 Aspose.Words 在 Python 中将 docx 转换为 txt。学习加载 Word 文档、设置 UTF‑8 编码，并在几行代码中导出
  Word 文档为 txt。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- convert docx to txt
- convert word to plain text
- save word as plain text
- export word document txt
- load word document python
language: zh
lastmod: 2026-09-27
og_description: 使用 Aspose.Words 在 Python 中将 docx 转换为 txt。本教程展示如何加载 Word 文档、配置编码并将其保存为纯文本。
og_image_alt: Screenshot of Python code that converts a DOCX file to a TXT file
og_title: 在 Python 中将 docx 转换为 txt – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Convert docx to txt in Python using Aspose.Words. Learn to load a Word
    document, set UTF‑8 encoding, and export Word document txt in a few lines.
  headline: How to convert docx to txt in Python with Aspose.Words
  type: TechArticle
tags:
- Python
- Aspose.Words
- Document conversion
title: 如何在 Python 中使用 Aspose.Words 将 docx 转换为 txt
url: /zh/python/document-conversion/how-to-convert-docx-to-txt-in-python-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 在 Python 中将 docx 转换为 txt

如果您需要快速 **convert docx to txt**，本指南将在 Python 中为您展示完整的解决方案。您将学习如何 **load word document python**，配置 UTF‑8 编码，并仅用几行代码 **export word document txt**。

本教程涵盖了在任何支持 Python 3 的平台上运行转换所需的全部内容。阅读完本文后，您将能够可靠地 **save word as plain text**，即使源文档包含特殊字符或非 ASCII 符号。

## 前提条件

* 已安装 Python 3.8 或更高版本。
* 拥有有效的 Aspose.Words for Python 许可证（免费试用可用于评估）。
* 通过 `pip install aspose-words` 安装 `aspose-words` 包。
* 准备好要转换的 DOCX 文件（示例使用 `input.docx`）。

> **Pro tip:** 将许可证文件 (`Aspose.Words.lic`) 放在脚本同一文件夹中，或显式设置 `Aspose.Words.License` 路径，以避免评估模式水印。

## 安装 Aspose.Words

在终端或命令提示符中运行以下命令：

```bash
pip install aspose-words
```

该包包含在代码示例中使用的 `aw` 命名空间。

## 第一步 – 加载 Word 文档（convert docx to txt）

第一步是将 DOCX 文件读取为 `aw.Document` 对象。此步骤对应 **load word document python** 的需求。

```python
import aspose.words as aw

# Load the source DOCX file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Why this matters*：加载文档会在内存中创建一个表示，Aspose.Words 可以对其进行操作，而不受原始文件格式的限制。

## 第二步 – 配置 TXT 保存选项（convert word to plain text）

Aspose.Words 提供 `TxtSaveOptions` 来控制纯文本输出的生成方式。将 `encoding` 属性设置为 `"utf-8"` 可确保所有 Unicode 字符得以保留。

```python
# Create TXT save options and set UTF‑8 encoding
txt_options = aw.saving.TxtSaveOptions()
txt_options.encoding = "utf-8"
```

*Why this matters*：如果未显式指定编码，默认系统代码页可能会将非 ASCII 字符替换为问号。UTF‑8 是多语言文档最安全的选择。

## 第三步 – 将文档保存为纯文本（save word as plain text）

现在使用上述选项将文档写入 `.txt` 文件。

```python
# Export the document to a plain‑text file
output_path = "YOUR_DIRECTORY/out.txt"
doc.save(output_path, txt_options)
print(f"Document exported successfully to {output_path}")
```

生成的 `out.txt` 文件仅包含 `input.docx` 的文本内容，换行符与原始段落结构相匹配。

### 预期输出

如果 `input.docx` 包含以下句子：

> **“Hello, world! Привет мир!”**

生成的 `out.txt` 将显示：

```
Hello, world! Привет мир!
```

所有字符保持完整，因为已应用 UTF‑8 编码。

## 处理常见边缘情况

| Situation | Recommended approach |
|-----------|----------------------|
| **文档包含表格** | Aspose.Words 会将表格单元格展平成以制表符分隔的纯文本。如果需要自定义分隔符，请相应设置 `txt_options.table_cell_separator`。 |
| **大文件（≥ 100 MB）** | 对文档进行流式处理以避免高内存消耗：使用 `doc.save(output_stream, txt_options)`，其中 `output_stream` 为以二进制模式打开的文件对象。 |
| **缺少字体** | 在主机上安装所需字体或在转换前将其嵌入 DOCX。缺少字体仅影响视觉渲染，不会影响纯文本提取。 |
| **受密码保护的 DOCX** | 加载时提供密码：`doc = aw.Document("secure.docx", aw.LoadOptions(password="MySecret"))`。 |

## 完整脚本 – 可直接运行

将以下代码保存为 `convert_docx_to_txt.py` 并使用 `python convert_docx_to_txt.py` 执行。

```python
import aspose.words as aw
import os

def convert_docx_to_txt(input_path: str, output_path: str, encoding: str = "utf-8") -> None:
    """
    Converts a DOCX file to a TXT file using Aspose.Words.

    Args:
        input_path: Path to the source .docx file.
        output_path: Desired path for the resulting .txt file.
        encoding: Text encoding for the output file (default UTF‑8).
    """
    if not os.path.isfile(input_path):
        raise FileNotFoundError(f"Input file not found: {input_path}")

    # Load the Word document (load word document python)
    document = aw.Document(input_path)

    # Configure TXT save options (convert word to plain text)
    txt_options = aw.saving.TxtSaveOptions()
    txt_options.encoding = encoding

    # Save as plain‑text (save word as plain text)
    document.save(output_path, txt_options)
    print(f"Conversion complete: {output_path}")

if __name__ == "__main__":
    INPUT_FILE = "YOUR_DIRECTORY/input.docx"
    OUTPUT_FILE = "YOUR_DIRECTORY/out.txt"
    convert_docx_to_txt(INPUT_FILE, OUTPUT_FILE)
```

运行脚本后会打印确认信息，并在指定目录下生成 `out.txt`。

## 验证结果

执行后，在任意文本编辑器（例如 VS Code、Notepad++）中打开 `out.txt`，确认内容与原始 DOCX 文本一致。如果出现乱码，请再次确认 `txt_options.encoding` 已设置为 `"utf-8"`。

## 后续步骤及相关主题

* **Convert docx to pdf** – 使用 `aw.saving.PdfSaveOptions` 以获得高保真 PDF 输出。
* **Extract images from a Word document** – 探索 `aw.NodeType.SHAPE` 与 `Shape` 类。
* **Batch conversion** – 遍历包含 DOCX 文件的文件夹，对每个文件调用 `convert_docx_to_txt`。
* **Advanced encoding** – 在处理从右到左脚本时尝试使用 `txt_options.add_bidi_marks`。

通过掌握上述步骤，您可以在任何自动化流水线中 **export word document txt**，无论是构建命令行工具、与 Web 服务集成，还是在云端处理文档。

---

## 接下来应该学习什么？

以下教程涵盖与本指南技术密切相关的主题，构建在本指南演示的技巧之上。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [Convert docx to txt – Complete Guide to Saving Word as Plain Text](/words/english/net/programming-with-txtsaveoptions/convert-docx-to-txt-complete-guide-to-saving-word-as-plain-t/)
- [Aspose.Words – Save docx as txt and Export Word Equations as LaTeX – Complete Guide](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [Word to PDF Tutorial: Convert DOCX to PDF with Aspose.Words](/words/english/net/basic-conversions/word-to-pdf-tutorial-convert-docx-to-pdf-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}