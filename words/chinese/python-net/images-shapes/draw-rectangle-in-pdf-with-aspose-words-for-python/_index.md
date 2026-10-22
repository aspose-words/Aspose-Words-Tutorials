---
category: general
date: 2026-08-07
description: 使用 Aspose.Words for Python 在 PDF 中绘制矩形，并学习如何为形状添加阴影、配置形状阴影以及将文档保存为 PDF。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: zh
lastmod: 2026-08-07
og_description: 使用 Aspose.Words for Python 在 PDF 中绘制矩形。本教程展示如何为形状添加阴影、配置形状阴影，并将文档保存为
  PDF，以实现专业文档生成。
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: 使用 Aspose.Words for Python 在 PDF 中绘制矩形 – 指南
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: 使用 Aspose.Words for Python 在 PDF 中绘制矩形
url: /zh/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 PDF 中使用 Aspose.Words for Python 绘制矩形

如果您在 Python 中需要 **在 PDF 中绘制矩形**，本指南提供了完整、可直接运行的解决方案。您将看到如何 **为形状添加阴影**、配置该阴影，最后 **将文档保存为 PDF** 以便分发或归档。

创建带阴影的矩形是报表、发票或可视化标注的常见需求。完成本教程后，您将拥有一个生成包含真实阴影矩形的 PDF 的脚本，并了解如何调整大小、颜色和偏移以适配任何设计。

## 前提条件

开始之前，请确保您已具备：

* 已安装 Python 3.8+。
* 通过 .NET 的 Aspose.Words for Python 包（`aspose-words`）——使用以下命令安装：

```bash
pip install aspose-words
```

* 对您打算保存 PDF 的文件夹拥有写入权限。

无需额外的库；Aspose.Words 在内部处理形状创建、阴影配置以及 PDF 导出。

## 第一步：创建一个新的空白文档（在 PDF 中绘制矩形 – 初始化）

第一步是实例化一个 `Document` 对象。该对象代表整个 PDF 文件，并提供章节、段落和形状的容器。

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**为什么重要：** Aspose.Words 将 PDF 生成视为从 Word 文档模型的转换，因此即使最终输出是 PDF，我们仍然从 `Document` 开始。

## 第二步：向文档主体插入矩形形状

矩形是特定的 `ShapeType`。我们将其添加到第一个章节的主体中，保存为 PDF 时会自动创建新页面。

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**说明：** `width` 和 `height` 属性控制形状在 PDF 中的视觉尺寸。添加文本可以在测试期间更容易验证矩形。

## 第三步：为形状添加阴影 – 启用并自定义

现在打开阴影效果并微调其外观。这正是 **为形状添加阴影** 关键字发挥作用的地方。

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**为什么要配置形状阴影？** 调整 `blur`、`distance` 和 `angle` 可以模拟真实的光照效果，从而提升生成 PDF 的可读性和视觉层次。

## 第四步：将文档保存为 PDF – 最终输出

在定义好矩形及其阴影后，最后一步是将 Word 文档导出为 PDF。这满足了 **将文档保存为 PDF** 的需求。

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

打开 `shadow_rectangle.pdf` 时，您会看到单页上有一个带灰色边框、标题为 “Shadow demo” 的矩形，且拥有清晰的对角阴影。

### 预期输出

* 一个名为 `shadow_rectangle.pdf` 的 PDF 文件。
* 单页包含一个 200 pt × 100 pt 的矩形。
* 可见的阴影偏移 5 pt，角度为 45°，模糊度为 8 pt。

## 第五步：探索变体和边缘情况（可选）

以下是实际项目中常见的调整方式：

| 变体 | 代码片段 | 何时使用 |
|-----------|--------------|-------------|
| **不同的形状类型**（例如椭圆） | `aw.drawing.ShapeType.OVAL` 替代 `RECTANGLE` | 用于圆形图形或徽章 |
| **自定义阴影颜色** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | 当需要灰色或品牌专属的阴影时 |
| **多个形状** | 重复形状创建块并调整 `left`/`top` 属性 | 构建复杂图表 |
| **形状内部无文本** | 省略 `rectangle.text = "..."` | 当形状仅用于装饰时 |
| **更高 DPI 输出** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` 并在 `PdfSaveOptions` 中设置图像质量 | 用于可打印的 PDF |

**专业提示：** 在调整其他属性之前务必先设置 `shadow.visible = True`；否则更改会被静默忽略。

## 完整脚本 – 复制、粘贴并运行

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

在终端或 IDE 中运行脚本。将 `YOUR_DIRECTORY` 替换为实际的文件夹路径，例如 `"/tmp"` 或 `"C:\\Users\\Me\\Documents"`。

## 结论

现在您已经掌握了如何使用 Aspose.Words for Python **在 PDF 中绘制矩形**、**为形状添加阴影**、**配置形状阴影**，以及 **将文档保存为 PDF**。完整示例展示了从文档创建到最终导出的每一步，可选变体则说明了如何将代码适配到更复杂的场景。

接下来，您可以探索：

* 添加其他形状类型（`ShapeType.LINE`、`ShapeType.ELLIPSE`）。
* 应用渐变填充或边框以提升视觉效果。
* 使用 `PdfSaveOptions` 嵌入字体或控制图像压缩。

欢迎根据您的品牌或设计指南自由实验参数。祝您 PDF 脚本编写愉快！

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。

- [Optimize PDF Bookmarks Using Aspose.Words for Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Optimize Pdf Loading Python Aspose Words Skip Images](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python Pdf Manipulation](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}