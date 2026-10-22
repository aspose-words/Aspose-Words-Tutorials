---
category: general
date: 2026-10-16
description: 使用 Python 创建一个空白 Word 文档，在 Word 中插入形状，添加外部阴影，并将其保存为 PDF。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: zh
lastmod: 2026-10-16
og_description: 使用 Aspose.Words for Python 创建一个带有外部阴影形状的空白 Word 文档。本指南展示了如何插入形状、应用阴影以及将文件保存为
  PDF。
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: 创建带形状阴影的空白 Word 文档 – Python 指南
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: 在 Python 中创建带阴影形状的空白 Word 文档
url: /zh/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Python 创建带阴影形状的空白 Word 文档

如果您需要 **创建空白 Word 文档** 并添加自定义图形，本指南将为您提供完整步骤。我们将演示如何 **在 Word 中插入形状**、为其应用 **外部阴影**，并最终 **使用 Python 将其保存为 PDF**。

您将学习如何配置 Aspose.Words for Python、构建矩形、设置阴影样式，以及生成保留视觉效果的 PDF。无需事先了解 Aspose API，但需要具备基本的 Python 知识，并已安装 Python 3.10 或更高版本。

## 前置条件

在开始之前，请确保您具备以下条件：

* 已安装 Python 3.10 或更高版本。
* 拥有有效的 Aspose.Words for Python 许可证（免费试用版可用于评估）。
* 能通过 `pip` 安装 `aspose-words` 包。
* 对将要保存 PDF 的目录拥有写入权限。

您可以使用以下单行命令安装库：

```bash
pip install aspose-words
```

## 创建空白 Word 文档 – 环境准备

第一步是创建一个空的 Word 文件，作为放置形状的画布。

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` 表示一个完全空白的 Word 文件。通过使用 `DocumentBuilder`，您可以访问诸如 `insert_shape` 的方法，后续步骤将使用该方法。

## 在 Word 中插入形状并设置尺寸

现在我们添加一个矩形，稍后将在其上应用外部阴影。尺寸使用点（pt）表示（1 pt ≈ 1/72 英寸）。

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

`insert_shape` 调用返回一个 `Shape` 对象，您可以进一步自定义。此时，文档在 Microsoft Word 中打开时已经包含一个可见的矩形。

## 添加外部阴影 – 自定义效果

Aspose.Words 提供了 `ShadowEffect` 类，用于定义阴影属性，如样式、模糊程度、距离和颜色。

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

将 `style` 设置为 `OUTER` 可确保阴影出现在矩形边框之外，呈现出细腻的 3‑D 效果。您可以通过调整 `blur` 和 `distance` 来实现更紧凑或更柔和的阴影。

## 保存为 PDF（Python） – 完成文档

在完成形状样式后，文档可以直接保存为 PDF。Aspose.Words 在内部处理转换，保留阴影效果。

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

在任意 PDF 查看器中打开 `shape_with_shadow.pdf`，即可看到与 Word 中完全相同的外部阴影矩形。

## 完整工作示例

下面是整合所有步骤的完整脚本。将其复制到名为 `create_word_with_shadow.py` 的文件中并运行。

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**预期输出**

运行脚本后会打印确认信息，例如：

```
PDF generated at: output/shape_with_shadow.pdf
```

打开生成的 PDF，您将看到单页上有一个 200 pt × 100 pt 的矩形，带有柔和的黑色外部阴影。

## 常见变体和边缘情况

* **更改阴影颜色** – 将 `aw.Color.black` 替换为任意其他 `aw.Color` 值，例如 `aw.Color.red` 或 `aw.Color.from_argb(255, 0, 120, 215)`。
* **使用不同形状** – 将 `aw.drawing.ShapeType.RECTANGLE` 改为 `OVAL`、`DIAMOND` 或任何受支持的枚举值。
* **保存为 DOCX 而非 PDF** – 调用 `doc.save("output/shape.docx")` 以保持 Word 格式。
* **多个形状** – 再次调用 `builder.insert_shape` 创建额外形状；每个形状都可以拥有独立的 `ShadowEffect`。

**小技巧**：如果需要将形状放置在特定位置，可在插入后设置 `rectangle.left` 和 `rectangle.top`。这样可以实现像素级的精准定位。

## 结论

现在您已经掌握了 **创建空白 Word 文档**、**在 Word 中插入形状**、**添加外部阴影**以及 **使用 Python 保存为 PDF** 的完整流程。完整代码示例展示了端到端的工作流，解释阐明了每个 API 调用的必要性。

接下来，您可以探索更高级的样式选项，在形状内部添加文字，或组合多个形状构建复杂图表。尝试不同的阴影参数，以匹配品牌的视觉语言，并将此方法集成到更大的文档生成流水线中。

祝编码愉快！


## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。每个资源均提供完整可运行的代码示例和逐步说明。

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create PDF from Word – Complete Python Guide with Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}