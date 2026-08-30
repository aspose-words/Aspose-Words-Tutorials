---
category: general
date: 2026-08-17
description: 如何使用 Aspose.Words for Python 保存 PNG。学习为形状添加阴影、将文档保存为 PDF，并在同一指南中将 Word
  导出为 PNG。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: zh
lastmod: 2026-08-17
og_description: 如何使用 Aspose.Words 保存 PNG。本教程展示了向形状添加阴影、将文档保存为 PDF，以及将 Word 导出为 PNG。
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: 如何使用 Aspose.Words 保存 PNG 并为形状添加阴影
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: 如何使用 Aspose.Words 保存 PNG 并为形状添加阴影
url: /zh/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 保存 PNG 并为形状添加阴影

如果您需要**从 Word 文件保存 PNG**，本指南提供完整、可运行的解决方案。您还将看到如何**为形状添加阴影**、**将文档保存为 PDF**以及**将 Word 导出为 PNG**，且全部在 Aspose.Words 环境中完成。

本教程涵盖了将空白 Word 文档转换为 PDF 和 PNG 图像的全部必要步骤，同时对矩形形状应用简单的阴影效果。无需外部工具，代码可在 Aspose.Words for Python via .NET 7 或更高版本中运行。

## 您将实现的目标

* 以编程方式创建一个新的 Word 文档。  
* 插入一个矩形形状并配置阴影效果。  
* 将同一文档保存为 PDF 文件。  
* 将文档导出为 PNG 图像。  

这些步骤回答了常见的查询**如何保存 PNG**，同时在单一工作流中处理**为形状添加阴影**和**将文档保存为 PDF**。

## 前提条件

* Python 3.9 或更高版本。  
* 已安装 Aspose.Words for Python via .NET（`pip install aspose-words`）。  
* 对您指定的输出目录具有写入权限。  

如果您尚未安装 Aspose.Words，请运行：

```bash
pip install aspose-words
```

## 使用 Aspose.Words 保存 PNG

第一步是创建文档和 `DocumentBuilder`。Builder 为您提供流式 API，以插入形状、表格或文本等内容。

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` 表示内存中的整个 Word 文件。`aw.DocumentBuilder` 指向当前的插入位置，初始时位于第一个（也是唯一一个）节的起始处。

## 导出前为形状添加阴影

形状可以是任何绘图对象——矩形、椭圆或自定义多边形。这里我们创建一个 100 × 100 点的矩形并应用柔和的阴影。

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

为什么要在保存之前配置阴影？Aspose.Words 在 PDF 和 PNG 导出阶段渲染阴影，因此视觉效果在两种输出格式中都得以保留。

### 专业提示
如果需要更锐利的阴影，请减小 `blur`。若想获得更明显的偏移，请增大 `distance`。`Shadow` 类还提供 `angle` 和 `transparency`，以实现精细控制。

## 将文档保存为 PDF

一旦内容准备好，将 Word 文档保存为 PDF 只需一行代码。`SaveFormat.PDF` 常量指示 Aspose.Words 执行转换。

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

生成的 PDF 包含您定义的矩形及其精确阴影。Aspose.Words 处理矢量图形，因此 PDF 文件大小保持适中。

## 将 Word 导出为 PNG

导出为 PNG 会为每页创建光栅图像。默认情况下，Aspose.Words 使用 96 DPI；您可以通过提供 `PngSaveOptions` 对象来提高此值，以获得更高分辨率的输出。

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

当您**将 Word 导出为 PNG**时，每页都会保存为单独的 PNG 文件。由于我们的示例文档只有一页，因此只会出现一个 PNG 文件。

### 可选：更高分辨率的 PNG

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

更高的 DPI 在 PNG 用于打印或需要清晰缩略图时非常有用。

## 完整脚本 – 复制、粘贴并运行

下面是完整的、独立的脚本，实现了上述所有步骤。将其保存为 `generate_assets.py` 并在命令行中运行。

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### 预期输出

运行脚本会生成三个文件：

* `output/output.pdf` – 包含投射黑色阴影矩形的 PDF。  
* `output/output.png` – 以 96 DPI 渲染相同页面的 PNG。  
* `output/high_res_output.png` – 300 DPI 的 PNG，质量更高。  

使用您喜欢的查看器打开任意文件，以验证阴影是否如定义般准确呈现。

## 常见问题与边缘情况

**如果输出目录不存在怎么办？**  
脚本调用 `os.makedirs(output_dir, exist_ok=True)`，会自动创建文件夹。这可防止在保存操作期间出现 `FileNotFoundError`。

**我可以添加多个具有不同阴影的形状吗？**  
可以。创建额外的 `Shape` 对象，独立配置每个 `shadow` 属性，并在保存前使用 `builder.insert_node(shape)` 将它们插入。

**将阴影转换为其他光栅格式（例如 JPEG）时会保留吗？**  
Aspose.Words 会为 `SaveFormat` 支持的所有光栅格式渲染阴影。您可以将 `aw.SaveFormat.PNG` 替换为 `aw.SaveFormat.JPEG`，阴影仍会出现。

**这与“convert word to pdf”有何不同？**  
`convert word to pdf` 本质上与第 4 步执行的操作相同。使用 `SaveFormat.PDF` 的同一 `doc.save` 调用在内部处理转换，保留布局、字体以及阴影等图形。

**形状大小是否有限制？**  
形状以点为单位测量（1 pt ≈ 1/72 英寸）。非常大的尺寸可能会增加生成文件的大小，但 Aspose.Words 没有硬性限制。构造 `aw.Shape` 时可调整 `width` 和 `height` 参数以适应您的布局。

## 结论

现在，您已经了解了如何使用 Aspose.Words for Python **从 Word 文档保存 PNG**，并学习了 **为形状添加阴影**、**将文档保存为 PDF**以及**将 Word 导出为 PNG**。完整的脚本展示了一个简洁、可重复的模式，您可以将其应用于更大的文档、多页或更复杂的图形效果。

下一步可以包括：

* 试验其他 `ShapeType` 值（ellipse、cloud 等）。  
* 使用 `

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方法。

- [Aspose.Words 形状阴影教程 – 在 C# 中为 Word 形状添加阴影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [如何在 Java 中将 DOCX 转换为 PNG – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [使用 Aspose.Words 在 Python 中将 Word 文档保存为 PostScript：综合指南](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}