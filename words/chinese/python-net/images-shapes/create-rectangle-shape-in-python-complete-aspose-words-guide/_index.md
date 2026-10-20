---
category: general
date: 2026-06-24
description: 使用 Aspose.Words 在 Python 中创建矩形形状，学习如何为形状添加阴影、设置阴影角度，并在几分钟内将文档保存为 PDF。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: zh
og_description: 在 Python 中创建矩形形状，向形状添加阴影，设置阴影角度，并使用 Aspose.Words 将文档保存为 PDF。请按照此分步指南操作。
og_title: 在 Python 中创建矩形形状 – 完整的 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: 在 Python 中创建矩形形状 – 完整的 Aspose.Words 指南
url: /zh/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Python 中创建矩形形状 – 完整 Aspose.Words 指南

是否曾想过如何在 Word 文档中使用 Python **create rectangle shape**？也许你需要一个醒目的提示框、图表的视觉指示，或仅仅是报告中的一个精美矩形。无论是哪种情况，你都来对地方了。在本教程中，我们将完整演示整个过程——从插入矩形、添加细腻的阴影、调整阴影角度，最后 **save document as PDF**，以便与你的任何人共享。

我们将使用 **Aspose.Words for Python via .NET**，这是一款强大的库，能够在不打开 Word 本身的情况下操作 Word 文件。阅读完本指南后，你将能够自信地回答 “how to add shape shadow” 这一问题，并拥有一段可直接在任何项目中运行的脚本。

---

## 您需要的准备

在开始之前，请确保具备以下条件：

- 已在机器上安装 **Python 3.8+**。  
- 已安装 **Aspose.Words for Python via .NET**（`aspose-words` 包）。使用以下命令进行安装：

  ```bash
  pip install aspose-words
  ```

- 一个可写入的文件夹，用于保存生成的 PDF。  
- （可选）IDE 或文本编辑器——VS Code 表现出色。

就这些。无需额外的 DLL、无需 Office 安装，只需一个 pip 包即可。

---

## 第一步：设置 Document 和 Builder

首先需要创建 **create rectangle shape** 所需的对象：`Document` 和 `DocumentBuilder`。可以把 Builder 当作你的画笔，它会为你绘制一切。

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **为什么这很重要：** `Document` 对象代表整个 .docx 文件，而 `DocumentBuilder` 提供了诸如 `insert_shape` 之类的方法，让绘制形状变得轻而易举。

---

## 第二步：插入矩形形状

有了 Builder 后，我们终于可以 **create rectangle shape**。`insert_shape` 方法需要三个参数：形状类型、宽度和高度。这里我们使用 200 pt 的宽度和 100 pt 的高度，以获得良好的比例。

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

此时，你已经成功在文档中 **create rectangle shape**。如果稍后打开生成的 DOCX（我们稍后会演示），你会看到一个普通的矩形出现在光标所在的位置。

---

## 第三步：获取阴影格式对象

要 **add shadow to shape**，首先需要获取形状的阴影格式。Aspose.Words 中的每个形状都有一个 `shadow_format` 属性，暴露了所有与阴影相关的设置。

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

拥有 `shadow` 引用后，我们就可以在几行代码内切换可见性、模糊程度、距离、角度、颜色以及透明度。

---

## 第四步：启用阴影并配置外观

下面就是魔法所在。我们将 **add shadow to shape**，让它稍微模糊、稍作偏移，设置方向（即 **set shadow angle**），并赋予半透明的黑色调。

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **小技巧：** 如果需要更强的效果，可增大 `blur_radius` 或降低 `transparency`。相反，想要锐利、完全不透明的阴影，只需将 `blur_radius = 0` 且 `transparency = 0`。

---

## 第五步：将文档保存为 PDF

我们已经 **create rectangle shape**，已经 **add shadow to shape**，现在要 **save document as PDF**，这样无论在哪台设备上查看，效果都保持一致。Aspose.Words 只需一行代码即可完成。

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

运行脚本后，`output` 文件夹中会生成 `shadowed_rectangle.pdf`。使用任意 PDF 阅读器打开，你会看到一个干净的矩形，带有 45 度的柔和阴影——正是我们刚才配置的效果。

---

## 完整可运行示例

下面是结合上述所有步骤的完整脚本。将其复制粘贴到名为 `create_rectangle_with_shadow.py` 的文件中，然后执行 `python create_rectangle_with_shadow.py`。

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**预期输出：** 一个 PDF 文件，显示单个矩形并带有轻柔的对角阴影。没有多余页面，也没有隐藏的伪影——只有我们精心打造的形状。

---

## 常见问题与特殊情况

### 如果我需要其他形状怎么办？

Aspose.Words 支持多种 `ShapeType`（椭圆、星形、标注等）。只需将 `aw.drawing.ShapeType.RECTANGLE` 替换为所需的枚举，例如 `aw.drawing.ShapeType.ELLIPSE`。

### 能否为同一个形状添加多个阴影？

API 每个形状仅暴露一个 `ShadowFormat`，但可以通过复制形状、分别偏移并调整透明度的方式模拟多个阴影。

### 如何将阴影颜色改为品牌色？

只需将 `shadow.color` 设置为任意 `aw.drawing.Color`。例如品牌蓝可以使用 `aw.drawing.Color.from_argb(255, 0, 120, 215)`。

### 想保存为 DOCX 而不是 PDF 怎么办？

将 `document.save(pdf_path)` 替换为 `document.save("output/shadowed_rectangle.docx")`。阴影渲染在两种格式中都会保留。

### 老旧的 PDF 阅读器能显示阴影吗？

Aspose.Words 将阴影渲染为矢量效果，兼容性相当好。但极老的阅读器可能会将其展平；在目标受众的设备上进行测试始终是好习惯。

---

## 美化 PDF 的小技巧

- **添加边框：** `rectangle.line_format.width = 1.5` 并设置颜色，以获得清晰的轮廓。  
- **居中矩形：** 在插入前调用 `builder.move_to_document_start()`，随后设置 `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`。  
- **配合文字使用：** 在矩形后插入 `TextFragment`，例如 `"Important Section"`，用于标注。

这些细微的调整可以把普通矩形升级为专业的提示框，适用于报告、提案或电子书等场景。

---

## 结论

现在，你已经掌握了使用 Python **create rectangle shape**、**add shadow to shape**、**set shadow angle** 并 **save document as PDF** 的完整流程，全部基于 Aspose.Words。步骤清晰、代码自包含，并且我们已经解释了每行代码的意义——从文档初始化到最终 PDF 的打磨。

接下来，你可以探索 **how to add shape shadow** 在更复杂绘图中的应用，尝试渐变填充，或在形状内部生成表格。该库还支持将形状链接到书签，对于交互式 PDF 非常实用。

有什么新尝试吗？欢迎在评论区分享，或提出任何剩余疑问。祝编码愉快，尽情为文档增添层次感吧！

![矩形形状带阴影 – Python 中 create rectangle shape 示例](/images/rectangle-shadow.png)


## 接下来该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助你在项目中进一步扩展技巧。每篇资源都提供完整的可运行代码示例以及逐步解释，帮助你掌握更多 API 功能并探索替代实现方式。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}