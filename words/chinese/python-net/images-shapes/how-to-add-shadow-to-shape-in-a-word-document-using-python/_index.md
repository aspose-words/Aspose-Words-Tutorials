---
category: general
date: 2026-11-25
description: 使用 Python 为 Word 文档中的形状添加阴影。学习如何在 Word 中插入矩形形状并使用 Aspose.Words 应用透明阴影。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: zh
lastmod: 2026-11-25
og_description: 使用 Python 为 Word 文档中的形状添加阴影。本教程展示了如何在 Word 中插入矩形形状，并使用 Aspose.Words
  设置 30% 透明的阴影。
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: 使用 Python 为 Word 文档中的形状添加阴影——一步一步指南
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: 如何使用 Python 为 Word 文档中的形状添加阴影
url: /zh/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Python 为 Word 文档中的形状添加阴影

如果你需要 **为形状添加阴影**，本指南提供了一个完整、可运行的解决方案。你将看到如何创建 Word 文件、插入矩形形状，并使用 Aspose.Words for Python 库应用 30 % 透明度的阴影。

以编程方式操作 Word 文档可以避免手动格式化，并让你能够大规模生成报告、合同或营销传单。阅读完本教程后，你将能够用准备好的代码示例回答 “**如何使用 Python 创建 Word 文档**”。

## 前置条件

在开始之前，请确保你已经：

* 安装了 Python 3.8 或更高版本。
* 拥有有效的 Aspose.Words for Python 许可证（免费试用可用于评估）。
* 通过 `pip install aspose-words` 安装了 `aspose-words` 包。
* 有一个可以写入输出文件的文件夹（在代码中将 `YOUR_DIRECTORY` 替换为实际路径）。

无需其他依赖。

## 步骤 1：创建新的 Word 文档

第一步是实例化一个 `Document` 对象。该对象在内存中表示整个 .docx 文件。

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` 的工作方式类似于虚拟光标。调用其方法时，库会在当前光标位置插入相应的元素。

## 步骤 2：插入矩形形状

接下来使用构建器的 `insert_shape` 方法 **插入矩形形状**。该方法需要指定形状类型以及以点为单位的大小（1 点 = 1/72 英寸）。

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

你可以根据设计需求更改尺寸。矩形会成为文档绘图层的一部分，这意味着以后可以修改其填充、轮廓或阴影。

## 步骤 3：访问形状的阴影格式

每个绘图对象都暴露一个 `shadow_format` 属性，用于控制阴影外观。获取该属性后即可调整透明度、偏移、模糊和颜色。

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

此时形状仍使用默认阴影（即无阴影）。`ShadowFormat` 对象包含创建真实效果所需的所有参数。

## 步骤 4：将阴影设为 30 % 透明

透明度的取值范围是 `0`（完全不透明）到 `1`（完全透明）。将其设为 `0.3` 即可得到 30 % 透明的阴影，这通常足以增加层次感而不会喧宾夺主。

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

这些额外属性不是必需的，但它们展示了如何微调效果。`visible` 标志是关键；如果忘记设置，即使其他属性已配置，阴影也不会显示。

## 步骤 5：保存文档以查看结果

最后，将文档写入磁盘。使用 Microsoft Word 或任何兼容的查看器打开生成的 `.docx` 文件，即可看到带有透明阴影的矩形。

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

打开 `output.docx` 时，你会看到一个普通矩形，右下角带有细微的灰色阴影。30 % 的透明度让形状看起来像是悬浮在页面上。

![Add shadow to shape example](placeholder-image.png){: .align-center alt="使用 Python 在 Word 文档中为形状添加阴影的示例"}

## 完整、可运行的脚本

将所有代码片段组合在一起，即可得到一个可直接复制、粘贴并立即运行的独立脚本。

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**预期输出：** 打开生成的 `output.docx`，会看到单页文档中有一个矩形投射出轻微、半透明的阴影。无需额外格式化。

## 常见变体和边缘情况

| 场景 | 代码适配方式 |
|-----------|-----------------------|
| **不同的形状类型**（例如椭圆） | 将 `aw.drawing.ShapeType.RECTANGLE` 改为 `aw.drawing.ShapeType.ELLIPSE`。 |
| **自定义阴影颜色** | 使用 `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` 设置为红色阴影。 |
| **多个形状** | 多次调用 `builder.insert_shape`；每次调用都会返回一个独立的 `Shape` 对象，可分别设置样式。 |
| **另存为 PDF** | 将 `doc.save(output_path)` 替换为 `doc.save(output_path.replace('.docx', '.pdf'))` 并使用 `.pdf` 扩展名。 |
| **无许可证运行** | 免费试用会在首页添加水印。获取许可证即可在生产环境中去除水印。 |

这些变体说明，同一套流程——创建文档、插入形状、调整 `shadow_format`、保存——能够覆盖大多数自动化场景。

## 提示与最佳实践

* **复用 builder**：在整个文档生命周期中保持单一 `DocumentBuilder` 实例，避免不必要的对象创建。
* **释放资源**：在长时间运行的服务中，保存后调用 `doc.dispose()` 以释放本机内存。
* **验证输出**：如果需要确保符合 Open XML 标准，可在保存前使用 `doc.validate(aw.ValidationType.FULL_VALIDATION)`。
* **版本兼容性**：代码适用于 Aspose.Words for Python ≥ 22.9。使用 `pip install --upgrade aspose-words` 确保包是最新的。

## 结论

现在你已经掌握了如何使用 Python **为 Word 文档中的形状添加阴影**。通过五个步骤——创建文档、**插入矩形形状**、配置阴影并保存——你可以实现报告、发票或营销材料的自动化、精美文档生成。

接下来，你可以探索梯度填充、文本环绕或将文档转换为 PDF 等其他格式化选项。所有这些主题都基于本教程中介绍的 `DocumentBuilder` 与形状格式化概念。

祝编码愉快，享受简单阴影为自动化 Word 文档带来的视觉层次感！

## 接下来该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助你进一步掌握 API 功能并在项目中尝试不同实现方式。

- [How to create rectangle shape in a Word document using Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Create Blank Word Document and Add Shadow to Shape – Full Python Guide](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}