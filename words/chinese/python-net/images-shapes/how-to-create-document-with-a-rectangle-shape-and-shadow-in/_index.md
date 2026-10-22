---
category: general
date: 2026-10-04
description: 如何使用 Aspose.Words 在 Python 中创建文档并为形状添加阴影。学习设置阴影颜色、插入矩形形状以及自定义外部阴影。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: zh
lastmod: 2026-10-04
og_description: 如何在 Python 中创建文档并为形状添加阴影。本指南展示了如何设置阴影颜色、插入矩形形状以及使用 Aspose.Words 应用外部阴影。
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: 如何在 Python 中创建带有矩形形状和阴影的文档
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: 如何在 Python 中创建带有矩形形状和阴影的文档
url: /zh/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Python 中创建带矩形形状和阴影的文档

如果您需要 **how to create document** 并包含一个样式化的矩形，本指南提供完整的解决方案。您将看到如何 **add shadow to shape**，设置阴影颜色，并控制其偏移量和模糊程度——全部使用 Aspose.Words for Python。教程结束时，您可以生成一个外观精致、可直接分发的 `.docx` 文件。

下面的步骤涵盖了从安装库到自定义阴影外观的全部内容。无需外部文档；代码已准备好可直接复制、运行并适配到您的项目中。您还将学习如何 **insert rectangle shape**，选择 **outer shadow style**，以及处理常见的陷阱，如阴影不可见或环绕设置不正确。

## 前提条件

* 已安装 Python 3.8 或更高版本。
* 有效的 Aspose.Words for Python 许可证（或免费评估密钥）。
* 对 Python 脚本有基本了解。
* 有可写入的文件系统位置，用于保存生成的文档。

您可以使用 pip 安装 SDK：

```bash
pip install aspose-words
```

## 步骤 1：导入库并创建一个新的空白文档

在任何 Word 自动化场景中，创建新文档是第一步。`aw.Document()` 构造函数为您提供一个空文件，您可以向其中填充文本、图像或形状。

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

`DocumentBuilder` 对象简化了内容的插入。它会跟踪当前光标位置，使您能够顺序添加元素，而无需手动管理节。

## 步骤 2：插入指定大小的矩形形状

矩形形状充当可视元素的容器。您可以使用点（pt）来定义其宽度和高度（1 pt ≈ 1/72 英寸）。

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

此时形状没有任何视觉样式，因此只显示为普通轮廓。接下来的步骤将为其添加深度和颜色。

## 步骤 3：将形状设置为与周围文本内联流动

当形状为 **inline**（内联）时，它的行为类似于段落中的字符。这可确保矩形在文档布局中保持在您预期的位置。

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

如果您希望形状漂浮在文本之上，可以使用 `WrapType.SQUARE` 或 `WrapType.TOP_BOTTOM`，但对于大多数报告而言，内联形状能够保持布局的可预测性。

## 步骤 4：使阴影可见并选择其颜色

不可见的阴影没有任何视觉效果。`visible` 标志用于激活该效果，`color` 属性决定其色调。使用黑色可呈现经典且细腻的深度感。

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

您可以将 `aw.drawing.Color.black` 替换为其他颜色，例如 `aw.drawing.Color.gray` 或自定义 RGB 值（`aw.drawing.Color.from_argb(255, 128, 128, 128)`）。

## 步骤 5：定义阴影的偏移和模糊以赋予深度

偏移量控制阴影相对于形状的位移距离，模糊半径则软化边缘。较小的数值会产生锐利的阴影；较大的数值则呈现更柔和的效果。

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

请尝试调整这些数值以符合您的设计规范。若需较重的投影，可同时增大偏移量和模糊半径。

## 步骤 6：选择外部阴影样式

Aspose.Words 提供多种阴影样式，如 `INNER`、`OUTER` 和 `PERSPECTIVE`。**outer**（外部）样式将阴影放置在形状边框之外，非常适合干净、专业的外观。

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

如果需要更具戏剧性的效果，可尝试 `ShadowStyle.PERSPECTIVE`——它会添加三维倾斜感。

## 步骤 7：保存带有阴影的文档

保存操作会将文件定稿并将所有格式写入磁盘。请选择您拥有写入权限的目录，并为文件起一个描述性的名称。

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

运行脚本后会生成一个 Word 文件，其中包含带有可见彩色阴影的矩形。请在 Microsoft Word 或 LibreOffice 中打开该文件以验证结果。

## 完整可运行示例

下面是整合了所有步骤的完整脚本。将代码复制到名为 `create_shadowed_shape.py` 的文件中，并使用 `python create_shadowed_shape.py` 运行。

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**预期输出**

打开 `ShapeWithShadow.docx` 时，您会看到页面中心有一个单独的矩形。该矩形带有轻微向右下偏移、略微模糊的黑色阴影，以营造深度感。阴影遵循外部样式，不会与矩形内部相交。

## 常见问题与边缘情况

### 为什么阴影有时会不可见？

只有当 `shadow.visible` 设置为 `True` **且** 形状的 `wrap_type` 允许显示时，阴影才会被渲染。内联形状可靠；漂浮形状可能需要额外的布局调整。

### 如何将阴影颜色更改为符合品牌配色方案？

将 `aw.drawing.Color.black` 替换为自定义 RGB 值：

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### 如果需要形状显示在文本后面怎么办？

将环绕类型设置为 `WrapType.BEHIND`，并在必要时调整 `z_order_position`。请注意，某些查看器可能会以不同方式渲染文本后置形状。

### 我可以将相同的阴影设置应用于多个形状吗？

可以。创建一个配置阴影的辅助函数，并在插入每个形状时调用它。这有助于代码复用并确保样式一致。

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## 结论

现在，您已经了解如何使用 Aspose.Words for Python 创建包含自定义阴影矩形形状的 **how to create document** 文件。教程涵盖了插入矩形、将形状设为内联、启用阴影、设置颜色、偏移、模糊和样式，最后保存文件的全过程。

接下来，您可以探索相关主题，例如对其他形状类型使用 **add shadow to shape**、根据数据动态 **set shadow color**，或 **how to add shadow** 到图像和文本框。尝试不同的尺寸、颜色和阴影样式，以符合您的品牌指南或设计体系。

准备好自动化更多 Word 文档了吗？接下来可以尝试添加表格、页眉或动态内容——每一步都基于本指南展示的相同原理。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南紧密相关的主题，构建在本指南展示的技术之上。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [How to Manage Document Variables with Aspose.Words in Python&#58; A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}