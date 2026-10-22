---
category: general
date: 2026-06-21
description: 使用 Aspose.Words 在 Python 中创建矩形形状。学习如何为形状添加阴影、设置形状填充颜色，并在几分钟内将文档保存为 PDF。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: zh
og_description: 使用 Aspose.Words 在 Python 中创建矩形形状。本指南展示如何为形状添加阴影、设置形状填充颜色以及将文档保存为 PDF。
og_title: 在 Python 中创建矩形形状 – Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: 在 Python 中创建矩形形状 – Aspose.Words 教程
url: /zh/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Python 中创建矩形形状 – Aspose.Words 教程

有没有想过 **如何在 Word 文档中创建矩形形状**，而且是在用 Python 编码时？你并不是唯一的遇到这个问题的人。许多开发者在需要快速的视觉元素——比如带有细微阴影的彩色框——并将整个文档导出为 PDF 时，常常卡住。

在本指南中，我们将逐步演示一个完整、可运行的示例，**创建矩形形状**、**设置形状填充颜色**、**为形状添加阴影**，最后 **将文档保存为 PDF**。没有模糊的引用，只有可以直接复制粘贴并立即运行的具体代码。

## 您需要的环境

在开始之前，请确保您的机器上具备以下条件：

- Python 3.8 或更高（我们使用的语法在任何近期版本都适用）。
- 有效的 Aspose.Words for Python 许可证或免费试用版（该库是纯 Python 的，无需 COM 互操作）。
- 您熟悉的文本编辑器或 IDE——VS Code 表现不错，其他编辑器同样可用。

就这些。没有繁重的框架，也没有额外的系统级依赖。让我们开始吧。

## 第一步：安装 Aspose.Words for Python

首先，如果还没有安装，请从 PyPI 拉取包：

```bash
pip install aspose-words
```

为什么这一步很重要：Aspose.Words 提供了我们后面要依赖的 `Document` 和 `DocumentBuilder` 类。没有这个库，后续的调用（比如 `insert_shape`）根本不存在，脚本会在绘制任何内容之前就崩溃。

> **小技巧**：保持虚拟环境整洁。安装前先运行 `python -m venv .venv && source .venv/bin/activate`，这样库就会被隔离在系统包之外。

## 第二步：创建新文档和 DocumentBuilder

现在我们真正 **创建矩形形状**——但首先需要一个空白画布。

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

`Document` 对象代表整个文件，而 `DocumentBuilder` 是一个便利的助手，知道光标所在位置并可以在该点插入元素。把 builder 想象成在页面上书写的笔。

## 第三步：插入矩形形状

下面就是主要操作所在。我们将 **创建矩形形状**，指定固定的宽度和高度，然后将其定位在页面上。

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

为什么选矩形？它是最简单的形状，却足以展示填充颜色和阴影。如果以后需要圆形或星形，只需将 `ShapeType.RECTANGLE` 换成相应的枚举值即可。

## 第四步：设置形状填充颜色

一个纯白的盒子并不吸引人，所以让我们 **设置形状填充颜色** 为柔和的颜色——浅蓝色在报告中效果很好。

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

您可以使用任何预定义的 `aw.Color` 成员（`red`、`green`、`dark_gray` 等），或传入 RGB 元组（`aw.Color.from_argb(255, 30, 144, 255)`）。填充颜色是用户在看到阴影或边框之前首先看到的颜色。

## 第五步：为形状添加阴影

接下来进行视觉优化：**为形状添加阴影**。阴影能提供深度，使矩形在页面上更突出。

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**如何添加阴影**？上面的代码正是如此实现的，下面我们逐项解释每个属性的意义：

- `visible` – 开关效果的开/关。
- `color` – 定义阴影的色调；深灰色模拟自然光照。
- `blur` – 值越大，边缘越柔和。
- `offset_x` / `offset_y` – 将阴影从形状向外移动；通过调节这些值可以模拟不同的光照角度。
- `transparency` – 0 为不透明，1 为完全透明；0.2 能产生细腻的效果。
- `type` – `OUTER` 将阴影投射到形状外部，`INNER` 则会在内部产生阴影。

如果需要更夸张的投影阴影，可将 `blur` 调高至 10‑15，并将 `offset_x`/`offset_y` 提升至 6‑8。

## 第六步：将文档保存为 PDF

所有的工作如果不能 **将文档保存为 PDF** 并分享出去就毫无意义。Aspose.Words 只需一行代码即可完成：

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

为什么选择 PDF？PDF 能在不同平台上保持布局一致，非常适合报告、发票或任何可打印的材料。`save` 方法会自动根据文件扩展名选择正确的格式——只要确保路径以 `.pdf` 结尾即可。

### 预期结果

打开生成的 `ShapeWithShadow.pdf`，您应该会看到一个浅蓝色的矩形位于第一页顶部居中位置，右下方有一个柔和的深灰色阴影，略微偏移。矩形边缘清晰，阴影细腻，文件大小通常在 100 KB 以下。

## 进阶：微调阴影 – “如何添加阴影”的答案

您可能会想，*“能否在不移动形状本身的情况下改变阴影方向？”* 完全可以。阴影的位置独立于形状坐标，只需调整 `offset_x` 和 `offset_y`。正值会让阴影向右/下移动，负值则向左/上移动。若想模拟左上方光源，可使用 `offset_x = -3`、`offset_y = -3`。

另一个常见问题：*“如果需要在同一形状上添加多个阴影怎么办？”* Aspose.Words 只支持每个形状一个阴影。如果需要层叠效果，可以复制一份形状，稍微偏移后为每个形状分别设置不同的阴影。这是一个小技巧，但确实可行。

## 完整脚本 – 可直接运行

下面是完整的、独立的脚本。将其复制到名为 `create_rectangle_with_shadow.py` 的文件中，并使用 `python create_rectangle_with_shadow.py` 运行。

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **注意**：将 `YOUR_DIRECTORY` 替换为您机器上实际存在的绝对或相对路径。如果文件夹不存在，Python 会抛出 `FileNotFoundError`。

## 常见陷阱及规避方法

| 问题 | 产生原因 | 解决方案 |
|------|----------|----------|
| 阴影未显示 | `shadow.visible` 默认是 `False` | 确保 `shadow.visible = True` |
| 形状不可见 | 填充颜色设为 `aw.Color.transparent` 或 `None` | 使用实色，例如 `aw.Color.light_blue` |
| PDF 为空 | 忘记调用 `doc.save` 或使用了错误的扩展名 | 调用 `doc.save("output.pdf")` 并检查路径 |
| 运行时 `ImportError` | 未安装 Aspose.Words 或使用了错误的 Python 环境 | 在激活的虚拟环境中运行 `pip install aspose-words` |

## 后续步骤 – 探索更多形状和格式化

掌握了 **create rectangle shape** 后，您可以：

- 将 `ShapeType.RECTANGLE` 替换为 `ShapeType.ELLIPSE` 或 `ShapeType.PENTAGON`，尝试其他几何形状。
- 使用 `builder.move_to(rectangle.absolute_position)` 然后 `builder.writeln("Hello World")` 在形状内部添加文字。
- 使用 `group = aw.drawing.GroupShape(doc)` 将多个形状组合成组，以绘制复杂图表。
- 导出为其他格式，如 DOCX (`doc.save("output.docx")`) 或 HTML (`doc.save("output.html")`) 以观察阴影的转换效果。

这些扩展都基于相同的核心概念：**add shadow to shape**、**set shape fill color**，以及 **save document as PDF**（或其他格式）。

---

### 图片预览 *(可选)*

![Create rectangle shape with shadow in Python](https://example.com/rectangle-shadow.png "在 Python 中创建带阴影的矩形形状")

*截图展示了最终 PDF 输出，其中包含浅蓝色矩形和细腻的外部阴影。*

---

## 结论

我们已经逐步演示了在 Python 中 **create rectangle shape**、设置自定义填充、**add shadow to shape**，并最终 **save document as PDF** 的完整过程。代码可直接运行，解释覆盖了每个属性背后的原因，并讨论了常见的边缘情况以及后续的扩展方向。

---

## 接下来该学习什么？

以下教程与本指南紧密相关，进一步深化您在本章节中使用的技术。每篇资源都提供完整可运行的代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}