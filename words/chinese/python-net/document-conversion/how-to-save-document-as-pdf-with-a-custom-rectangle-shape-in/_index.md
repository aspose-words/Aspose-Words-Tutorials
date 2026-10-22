---
category: general
date: 2026-10-07
description: 了解如何使用 Aspose.Words for Python 将文档保存为 PDF，同时添加矩形形状和自定义阴影。附带逐步代码示例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: zh
lastmod: 2026-10-07
og_description: 使用 Aspose.Words for Python 将文档保存为 PDF，并使用自定义矩形形状。完整示例演示如何绘制、设置样式并将
  Word 导出为 PDF。
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: 将文档保存为带矩形形状的 PDF – 完整 Python 指南
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: 如何在 Python 中将文档保存为带自定义矩形形状的 PDF
url: /zh/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Python 中使用自定义矩形形状将文档保存为 PDF

如果您需要 **将文档保存为 PDF** 并添加自定义图形，本指南将手把手教您完成。我们将演示如何创建一个空白 Word 文件、**绘制矩形形状**、设置其尺寸、应用可见阴影，最后使用 Aspose.Words for Python 库 **将 Word 导出为 PDF**。

完成后，您将得到一个包含完美定位矩形的 PDF，适用于报告、发票或任何文档自动化场景。无需外部工具——只需 Python 和 Aspose.Words 包。

## 您需要的条件

| Requirement | Why it matters |
|-------------|----------------|
| Python 3.8+ | Aspose.Words for Python API 面向现代解释器。 |
| `aspose-words` 包 (`pip install aspose-words`) | 提供代码示例中使用的 `aw` 命名空间。 |
| 对 Python 和面向对象编程有基本了解 | 本教程会操作 `Document`、`Shape` 等对象。 |
| 对将保存 PDF 的文件夹拥有写入权限 | **保存文档为 PDF** 步骤会将文件写入磁盘。 |

> **Pro tip:** 使用虚拟环境（`python -m venv venv`）来保持依赖隔离。

## 如何使用矩形形状将文档保存为 PDF

下面是完整、可运行的示例。每一步都有解释，让您了解 **为什么** 要执行该操作，而不仅仅是 **做了什么**。

### 步骤 1：初始化一个新的空白文档

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

创建一个全新的 `Document` 对象即可获得干净的页面集合。如果您想稍后 **将 Word 导出为 PDF**，也可以加载已有的 *.docx*，但从空白开始更能突出本例的重点。

### 步骤 2：向文档添加矩形形状

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

`add rectangle shape` 步骤使用 `ShapeType.RECTANGLE`。通过将形状追加到段落，Aspose.Words 能够确定在最终 PDF 中的渲染位置。

### 步骤 3：设置矩形尺寸

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

显式 **设置矩形尺寸** 能确保形状在各平台上保持一致。如果您更喜欢英制单位，也可以使用 `convert_to_inches` 辅助方法。

### 步骤 4：（可选）应用可见的自定义阴影

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

阴影可以让矩形在 PDF 中更突出。必须将 `shadow.visible` 标记为 true；否则其他属性不会生效。

### 步骤 5：保存文档为 PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

使用 **.pdf** 扩展名调用 `document.save`，Aspose.Words 会自动 **将文档保存为 PDF**，利用其内置的 PDF 渲染器。无需额外的转换步骤，这也是推荐的 **将 Word 导出为 PDF** 方式。

> **为何可行：** Aspose.Words 将文档布局（包括矩形及其阴影）直接写入 PDF 流。过程无损且保持矢量质量。

## 完整源码（单文件脚本）

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

运行此脚本会生成 `shadow_rectangle.pdf`，效果如下：

![生成的 PDF 示例图，显示保存文档为 PDF 后的矩形形状](placeholder-image.png)

*该 PDF 包含单页，页面中心有一个带黑色阴影的矩形。*

## 常见问题与边缘情况

| Question | Answer |
|----------|--------|
| **我可以将矩形放在特定位置吗？** | 可以。在保存前设置 `rectangle.left` 和 `rectangle.top`（单位为点）。 |
| **如果需要多个形状怎么办？** | 创建更多 `Shape` 对象，分别配置后追加到同一段落或不同段落即可。 |
| **阴影会影响 PDF 大小吗？** | 影响极小；阴影以矢量元数据存储，而非光栅图像。 |
| **能否用它来转换已有的 *.docx* 文件？** | 完全可以。将 `aw.Document()` 替换为 `aw.Document("input.docx")`，其余步骤保持不变。 |
| **如何更改矩形的填充颜色？** | 设置 `rectangle.fill_color = aw.drawing.Color.light_blue`（或任意您喜欢的 `Color`）。 |

## 后续步骤

了解了如何使用自定义矩形 **将文档保存为 PDF** 后，您可以进一步探索：

* 使用 **将 Word 导出为 PDF** 时添加页眉、页脚和页码。  
* 使用相同的 `Shape` 类 **添加其他绘图对象**（如 `Ellipse`、`Polygon`）。  
* **批量处理** 文件夹中的 Word 文件，为每个文件叠加相同的矩形。  

这些扩展遵循相同的模式：创建形状、配置属性，然后 **保存文档为 PDF**。

---

**摘要：** 本教程展示了如何在使用 Aspose.Words for Python 时 **将文档保存为 PDF**，并 **添加矩形形状**、**设置矩形尺寸**、以及应用自定义阴影。完整脚本已准备好复制、运行并适配到您的文档自动化流水线。祝编码愉快！


## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式，每篇资源均提供完整可运行的代码示例和逐步解释。

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Add rectangle to PDF with Aspose.Words – Step‑by‑Step Guide](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Save Document as PDF with Aspose.Words – Complete C# Guide](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}