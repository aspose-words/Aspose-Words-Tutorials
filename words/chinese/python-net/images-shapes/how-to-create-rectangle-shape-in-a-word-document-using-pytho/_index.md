---
category: general
date: 2026-09-30
description: 学习如何使用 Aspose.Words for Python 创建矩形形状、为形状应用阴影，并保存带有形状的 Word 文档。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: zh
lastmod: 2026-09-30
og_description: 在 Word 文档中快速创建矩形形状。本教程展示如何添加形状、为形状应用阴影、设置阴影模糊以及保存包含形状的 Word 文档。
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: 使用 Python 在 Word 中创建矩形形状 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: 如何使用 Python 在 Word 文档中创建矩形形状
url: /zh/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文档中使用 Python 创建矩形形状

如果你需要 **在 Word 文件中创建矩形形状**，本指南提供了完整、可运行的解决方案。你将看到如何添加形状、应用阴影效果、调整模糊程度，最后 **保存带有形状的 Word**，以便在 Microsoft Word 或任何兼容的查看器中打开。

示例使用 **Aspose.Words for Python via .NET**，这是一款无需安装 Microsoft Office 即可操作 Word 文档的库。无需事先了解 API——只要具备基础的 Python 知识即可。

## 你将实现的目标

- 在新文档的第一个节中插入一个矩形。  
- 通过设置模糊、偏移和颜色来配置柔和阴影。  
- 将文档持久化到磁盘并验证视觉效果。

## 前置条件

- Python 3.8 或更高版本。  
- 已安装 `aspose-words` 包（`pip install aspose-words`）。  
- 对输出目录拥有写入权限。

## 创建矩形形状并配置外观

第一步是实例化一个空白文档并向其添加矩形形状。该形状将作为阴影效果的画布。

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**为什么这很重要：**  
创建矩形会得到一个具体的对象（`shape`），后续可以对其进行样式设置。显式指定尺寸可确保形状在所有平台上外观一致。

## 如何向 Word 文档添加形状

虽然上面的代码已经添加了矩形，但以后可能需要添加其他形状（例如圆形、箭头）。相同的模式适用：在文档的 body 上调用 `append_child` 并传入所需的 `ShapeType`。

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**提示：** 使用 `ShapeType` 枚举可以查看所有受支持的形状。这让代码更易读，避免使用魔法数字。

## 为形状应用阴影并设置阴影模糊

阴影可以增加深度和视觉趣味。`ShadowEffect` 类让你能够控制模糊、偏移和颜色。下面我们为矩形应用柔和的黑色阴影。

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**为什么要设置模糊？**  
`blur` 决定阴影的扩散程度。低值（例如 1.0）产生锐利边缘，而较高值（例如 5.0）则产生柔和的渐变，这通常更具美感。

**边缘情况：** 如果将 `blur` 设置为 0，阴影会变成实心轮廓。一些查看器可能会出现锯齿伪影，因此建议使用大于 0 的值以获得更平滑的输出。

## 保存带有形状的 Word

持久化文档会将所有更改写入磁盘。`save` 方法会生成一个 `.docx` 文件，任何现代的 Word 处理器都能打开。

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

打开 `output.docx` 时，你会看到一个矩形位于左上角一英寸处，带有向右下方偏移两个点的柔和黑色阴影。阴影的模糊效果让形状看起来像是悬浮在页面上。

**专业技巧：** 如果需要在循环中生成大量文档，复用同一个 `Document` 实例并在每次迭代之间清空其 body，可降低内存开销。

## 常见变体与故障排除

| 情况 | 需要更改的内容 | 原因 |
|-----------|----------------|--------|
| 不同的阴影颜色 | `shadow.color = aw.Color.red` | 使用品牌色或突出重要形状。 |
| 更大的阴影偏移 | 增加 `shadow.offset_x`/`offset_y` | 在 UI 原型中强调深度感。 |
| 完全不使用阴影 | 删除 `shape.shadow = shadow` 行 | 适用于极简报告。 |
| 导出为 PDF 而非 DOCX | `doc.save("output.pdf")` | PDF 适合只读分发。 |

如果形状未出现，请确认你已将其添加到正确的节（`get_first_section()`），并且在修改后已保存文档。

## 完整、可运行的示例

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

运行脚本后会生成 `output.docx`，其中包含带有柔和阴影的矩形。使用 Microsoft Word 打开文件即可确认视觉效果与描述相符。

## 结论

现在你已经掌握了如何 **创建矩形形状**、**向 Word 文档添加形状**、**为形状应用阴影**、**设置阴影模糊**，以及最终 **保存带有形状的 Word**，全部使用 Aspose.Words for Python。相同的模式可以扩展到其他形状类型、颜色和效果，让你在不依赖 Office 自动化的情况下，完全控制文档图形。

**后续步骤**

- 试验 `Shape.fill` 为矩形添加渐变或图片背景。  
- 使用 `Paragraph` 对象在矩形内部放置文本。  
- 将多个形状组合成复杂图表，然后导出为 PDF 进行分发。  

欢迎根据自己的报告或模板需求调整代码，并在评论区分享你的成果！

## 接下来你应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助你进一步掌握 API 功能并探索项目中的替代实现方式。每个资源都提供完整的可运行代码示例和逐步解释。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}