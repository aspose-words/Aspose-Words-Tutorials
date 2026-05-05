---
category: general
date: 2026-05-04
description: 学习如何使用 Aspose.Words for Python 创建矩形形状、添加带阴影的形状、更改阴影颜色、设置阴影距离以及将文档保存为
  PDF。
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: zh
og_description: 使用 Aspose.Words for Python 创建矩形形状，学习如何添加形状、更改阴影颜色、设置阴影距离，并将文档保存为 PDF。
og_title: 创建矩形形状 – 添加阴影、更改颜色并保存为 PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: 在 Python 中创建矩形形状 – 添加阴影与保存为 PDF 的完整指南
url: /zh/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建矩形形状 – Python 开发者完整教程

是否曾经需要在 Word 文档中**创建矩形形状**并想为其添加精致的阴影？也许你正在构建报告生成器，视觉效果很重要——尤其是最终输出为 PDF 时。好消息是？使用 Aspose.Words for Python，你不仅可以**如何添加形状**，还能微调每个阴影属性，从颜色到距离，然后在一次流畅的操作中**将文档保存为 pdf**。

在本指南中，我们将一步步完整演示整个过程。你将看到可以直接复制粘贴的完整代码，了解*为什么*每行代码重要，并获取一些处理边缘情况（如透明阴影或非标准 DPI）的技巧。完成后，你将能够**创建矩形形状**、自定义其阴影，并轻松导出清晰的 PDF。

## 前置条件

- 已在机器上安装 Python 3.8+。  
- 通过 `pip install aspose-words` 安装 Aspose.Words for Python。  
- 对面向对象的 Python 有基本了解（无需高级技巧）。  

如果你已经设置好虚拟环境，只需运行安装命令即可开始。

## 步骤 1：初始化 Document 和 Builder

在你能够**如何添加形状**之前，需要一个空白文档作为工作对象。`Document` 类代表整个文件，而 `DocumentBuilder` 则是你的画笔。

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Why this matters:* `Document` 保存所有章节、页面和资源。`DocumentBuilder` 为你提供流式 API，能够在需要的位置插入内容——可以把它想象成文字处理器中的光标。

## 步骤 2：插入矩形形状

现在我们真正**如何添加形状**。`insert_shape` 方法需要指定形状类型以及尺寸（以点为单位）。这里我们选择一个 200 × 100 pt 的矩形，并填充淡蓝色。

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Pro tip:* 如果需要形状与现有文本对齐，请在插入前使用 `builder.move_to`，或在创建后调整 `left`/`top` 属性。

## 步骤 3：打开阴影

没有阴影的形状会显得平坦。要**设置阴影距离**并让效果可见，需要获取阴影格式并将其启用。

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Why this step:* 阴影格式是一个独立的对象；首先必须将 `visible` 切换为 true，否则其他所有阴影属性都会被忽略。

## 步骤 4：样式化阴影 – 颜色、模糊、距离、方向

这就是魔法发生的地方。我们将**更改阴影颜色**、调整模糊半径、设置阴影相对于矩形的距离，并将其旋转 45°。

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Explanation of each property:*

| 属性 | 功能 | 典型值 |
|----------|--------------|----------------|
| `style` | 决定阴影是*内部*还是*外部*。 | `OUTER`（最常用） |
| `blur_radius` | 控制柔软度；数值越高，边缘越模糊。 | 0–20 px 为常见范围 |
| `distance` | 阴影相对于形状的偏移距离。 | 0–10 pt 为细腻，>10 为夸张 |
| `direction` | 光源的角度，以顺时针方向从 x 轴测量。 | 0‑360° |
| `color` | 阴影颜色。 | 任意 `aw.Color`（例如 `gray`、`dark_red`） |

*Edge case:* 如果将 `distance` 设置为 `0`，阴影会直接位于形状下方，实际上会遮盖形状的填充。请保持大于 `0` 以获得可见的偏移。

## 步骤 5：将文档保存为 PDF

最后，我们**将文档保存为 pdf**。Aspose.Words 会自动栅格化阴影，因此 PDF 看起来与 Word 视图完全一致。

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Why PDF?* PDF 能在不同平台上保持布局一致，非常适合报告、发票或任何可打印的文档。

---

![创建矩形形状并添加阴影](https://example.com/images/rectangle-shadow.png){: .align-center alt="创建带阴影的矩形示例"}

*上图展示了最终的 PDF 输出——一个淡蓝色矩形带有柔和的灰色外阴影，正如我们配置的那样。*

## 常见问题与变体

### 如果我需要**透明**阴影怎么办？

在阴影颜色上设置 alpha 通道：

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### 能否将相同的阴影应用于多个形状？

可以。从一个形状提取 `ShadowFormat`，再赋给另一个形状：

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### 如何为**不同的形状类型**更改阴影？

所有形状类型共享相同的 `ShadowFormat` 属性，因此可以复用相同的配置块——只需将 `ShapeType.RECTANGLE` 替换为 `ShapeType.OVAL`、`ShapeType.TRIANGLE` 等。

### 关于用于打印的**高分辨率 PDF**怎么办？

使用更高 DPI 的 `PdfSaveOptions`：

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## 回顾

我们已经覆盖了实现**创建矩形形状**、**如何添加形状**、自定义其**阴影颜色**、**设置阴影距离**，以及最终**将文档保存为 pdf**所需的全部内容。完整、可运行的脚本如下：

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

运行脚本，打开生成的 `ShadowedShape.pdf`，你会看到一个边缘清晰、带有细腻灰色阴影的矩形——正是专业报告应有的视觉效果。

## 接下来该做什么？

- **探索其他形状类型**（`ShapeType.OVAL`、`ShapeType.LINE`）以丰富文档。  
- **通过叠加形状**组合多个阴影；甚至可以使用带明亮颜色的内部阴影来创建“发光”效果。  
- **自动化批处理**：遍历数据行集合，为每行生成一个形状，并将所有内容合并为单个 PDF。  
- **与其他 Aspose 库集成**（例如 Aspose.Slides），如果需要将相同的视觉效果导出到 PowerPoint。

随意实验——更改 `blur_radius`、尝试不同的 `direction`，或将 `gray` 替换为品牌专属色调。API 足够灵活，少量调整即可显著改变视觉冲击力。

有问题或遇到棘手场景？在下方留言或在 Aspose 社区论坛发帖。祝编码愉快，尽情享受这些精美的带阴影矩形吧！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}