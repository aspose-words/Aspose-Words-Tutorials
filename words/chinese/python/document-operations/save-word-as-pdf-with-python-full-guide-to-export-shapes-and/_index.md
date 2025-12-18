---
category: general
date: 2025-12-18
description: 使用 Aspose.Words for Python 快速将 Word 保存为 PDF。了解如何将 Word 转换为 PDF、导出浮动形状以及在单个脚本中处理
  docx 转换。
draft: false
keywords:
- save word as pdf
- convert word to pdf
- how to convert docx
- how to export shapes
- python word to pdf conversion
language: zh
og_description: 即时将 Word 保存为 PDF。本教程展示了如何转换 DOCX、导出形状，以及使用 Aspose.Words 进行 Python
  Word 转 PDF 转换。
og_title: 将 Word 保存为 PDF – 完整的 Python 教程
tags:
- Aspose.Words
- PDF conversion
- Python
title: 使用 Python 将 Word 保存为 PDF – 完整指南：导出形状并转换 DOCX
url: /chinese/python/document-operations/save-word-as-pdf-with-python-full-guide-to-export-shapes-and/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 Word 保存为 PDF – 完整 Python 教程

有没有想过在不打开 Microsoft Word 的情况下 **将 Word 保存为 PDF**？也许你正在自动化报告流水线，或需要批量处理数十份合同。好消息是，你不必盯着界面——Aspose.Words for Python 只需几行代码就能完成繁重的工作。

在本指南中，你将看到如何 **将 Word 转换为 PDF**、将浮动形状导出为内联标签，以及如何处理常见的 “如何导出形状” 的坑。完成后，你将拥有一个可直接运行的脚本，能够将任何 `.docx` 转换为干净的 PDF，即使源文件中包含图片、文本框或 WordArt。

---

![展示将 Word 保存为 PDF 工作流的示意图 – 加载 docx、设置 PDF 选项、导出为 PDF](image.png)

## 所需环境

- **Python 3.8+** – 任意近期版本均可；我们在 3.11 上测试过。
- **Aspose.Words for Python via .NET** – 使用 `pip install aspose-words` 安装。
- 一个示例 **input.docx** 文件，文件中至少包含一个浮动形状（例如图片或文本框）。  
- 对 Python 脚本有基本了解（无需高级知识）。

就是这么简单。无需 Office 安装，无需 COM 互操作，纯代码即可。

## 步骤 1：加载源 Word 文档

首先，需要将 `.docx` 加载到内存中。Aspose.Words 将文档视为对象图，这样你就可以在保存之前对其进行操作。

```python
import aspose.words as aw

# Step 1 – Load the source Word document
# Replace "YOUR_DIRECTORY/input.docx" with the actual path to your file.
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

*为什么重要：* 加载文档后，你可以访问每一个节点——段落、表格，以及对我们而言最关键的 **浮动形状**。如果跳过这一步，就没有机会调整这些形状在 PDF 中的渲染方式。

## 步骤 2：配置 PDF 保存选项 – 将浮动形状导出为内联标签

默认情况下，Aspose.Words 会尝试保留浮动对象的精确布局，这有时会导致 PDF 中出现布局偏移。将 `export_floating_shapes_as_inline_tag` 设置为 `True` 可以强制将这些对象视为内联元素，从而获得更可预测的结果。

```python
# Step 2 – Configure PDF save options
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
```

*为什么重要：* 如果你在寻找 **如何导出形状** 的答案，这个标志就是关键。它会把每个浮动形状包装在一个隐藏的 `<span>` 标签中，PDF 渲染器随后会把它当作普通文本流处理。结果是：不会出现漂浮在页面之外的孤立图片。

### 何时可能想保留默认设置？

- 如果文档依赖精确定位（例如宣传册布局），请将标志保持为 `False`。
- 对于大多数业务报告、发票或合同，将其设为 `True` 可以消除意外。

## 步骤 3：将文档保存为 PDF

选项配置完成后，就可以 **将 Word 保存为 PDF** 了。`save` 方法接受输出路径以及我们刚才配置的选项对象。

```python
# Step 3 – Save the document as a PDF using the configured options
# Replace "YOUR_DIRECTORY/output.pdf" with your desired output location.
document.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)
```

脚本执行完毕后，检查 `output.pdf`。你应该能看到原始文本、表格以及任何浮动形状都已内联渲染——正是一次干净的转换所应有的效果。

## 完整、可直接运行的脚本

将所有内容组合在一起，下面是可以复制粘贴到名为 `convert_docx_to_pdf.py` 的文件中的完整示例：

```python
import aspose.words as aw

def convert_docx_to_pdf(input_path: str, output_path: str) -> None:
    """
    Convert a DOCX file to PDF while exporting floating shapes as inline tags.
    
    Parameters
    ----------
    input_path : str
        Full path to the source .docx file.
    output_path : str
        Desired path for the generated PDF.
    """
    # Load the Word document
    document = aw.Document(input_path)

    # Set PDF options – export floating shapes as inline tags
    pdf_options = aw.saving.PdfSaveOptions()
    pdf_options.export_floating_shapes_as_inline_tag = True

    # Save as PDF
    document.save(output_path, pdf_options)

if __name__ == "__main__":
    # Example usage – adjust paths as needed
    convert_docx_to_pdf(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.pdf"
    )
```

### 预期输出

运行脚本后生成的 PDF 应该：

1. 保留所有文本、标题和表格。  
2. 将图片或文本框 **内联** 显示在相邻段落中。  
3. 与原始布局高度吻合，且没有漂浮的对象。

你可以使用任意阅读器打开 PDF——Adobe Reader、Chrome，甚至移动端应用，都能验证结果。

## 常见变体与边缘情况

### 批量转换文件夹中的多个文件

如果需要为整个目录 **将 word 转换为 pdf**，可以将函数放入循环中：

```python
import os, glob

source_folder = "YOUR_DIRECTORY/docs"
target_folder = "YOUR_DIRECTORY/pdfs"
os.makedirs(target_folder, exist_ok=True)

for docx_path in glob.glob(os.path.join(source_folder, "*.docx")):
    pdf_name = os.path.splitext(os.path.basename(docx_path))[0] + ".pdf"
    pdf_path = os.path.join(target_folder, pdf_name)
    convert_docx_to_pdf(docx_path, pdf_path)
```

### 处理受密码保护的文档

Aspose.Words 可以通过提供密码来打开加密文件：

```python
load_options = aw.loading.LoadOptions()
load_options.password = "mySecret"
protected_doc = aw.Document("protected.docx", load_options)
protected_doc.save("protected.pdf", pdf_options)
```

### 使用不同的 PDF 渲染器

有时你可能需要更高的保真度（例如保留精确的字体形状），可以切换渲染器：

```python
pdf_options.pdf_rendering_options = aw.saving.PdfRenderingOptions()
pdf_options.pdf_rendering_options.use_emf_embedded_fonts = True
```

## 专业提示与常见坑点

- **专业提示：** 始终使用至少包含一个浮动形状的文档进行测试。这是验证 `export_floating_shapes_as_inline_tag` 标志是否生效的最快方法。  
- **注意事项：** 非常大的图片会导致 PDF 体积膨胀。考虑在转换前使用 `ImageSaveOptions` 对图片进行降采样。  
- **版本检查：** 本示例代码适用于 Aspose.Words 23.9 及以上版本。如果使用旧版本，属性名可能为 `ExportFloatingShapesAsInlineTag`（首字母大写的 “E”）。

## 结论

现在，你已经掌握了使用 Python **将 Word 保存为 PDF** 的完整端到端方案。通过加载文档、调整 PDF 保存选项并调用 `save`，你已经精通了 **python word to pdf conversion** 的核心，同时也学会了 **如何正确导出形状**。

接下来，你可以：

- 批量处理成千上万的文件，  
- 将脚本集成到 Web 服务中，  
- 扩展以处理受密码保护的 DOCX 文件，或  
- 切换到其他输出格式，如 XPS 或 HTML。

动手试一试，调整选项，让自动化为你的文档工作流减负。祝编码愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}