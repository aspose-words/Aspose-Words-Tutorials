---
category: general
date: 2026-08-07
description: 使用 Aspose.Words 在 C# 中插入矩形形状，并学习如何隐藏形状、设置填充颜色，以及高效地将矩形形状添加到 Word 文档中。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: zh
lastmod: 2026-08-07
og_description: 使用 C# 在 Word 文档中插入矩形形状。了解如何隐藏形状、设置填充颜色，以及使用 Aspose.Words 添加矩形形状。
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: 在 C# 中插入矩形形状 – 完整的 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: 在 C# 中使用 Aspose.Words 插入矩形形状 – 步骤指南
url: /zh/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用 Aspose.Words 插入矩形形状 – 步骤指南

如果您需要在 C# 中 **向 Word 文档插入矩形形状**，本指南将手把手教您如何实现。您将看到如何设置填充颜色、隐藏形状使其在最终布局中不显示，以及如何保存文件——全部只需几行代码。

在接下来的章节中，我们会覆盖您需要了解的所有内容：前置条件、完整代码清单、每一步的解释，以及常见变体的技巧（例如再次显示形状或使用不同颜色）。阅读完本篇后，您就能以编程方式 **向任意 .docx 文件添加矩形形状**。

## 前置条件

开始之前，请确保您已具备：

* **Aspose.Words for .NET**（版本 23.10 或更高）。您可以通过 NuGet 安装：

  ```bash
  dotnet add package Aspose.Words
  ```

* 已在机器上安装 .NET 6.0 SDK 或更高版本。
* 对 C# 和 Visual Studio（或您喜欢的任何 IDE）有基本了解。

无需额外的库——与形状相关的 API 已包含在核心 Aspose.Words 包中。

## 使用 Aspose.Words 插入矩形形状

解决方案的核心是一段简短、独立的程序，它会创建一个空白文档、插入矩形、为其着色、隐藏，然后保存文件。下面是带有内联注释的完整源代码，解释每行代码背后的 *原因*。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### 每一步的作用

| 步骤 | 原因 |
|------|------|
| **创建新文档** | 提供一个干净的画布；您也可以通过 `new Document(path)` 传入文件路径来加载已有的 .docx。 |
| **初始化 DocumentBuilder** | `DocumentBuilder` 是高级助手，可让您在不处理底层节点树的情况下插入文本、表格和形状。 |
| **插入矩形形状** | `InsertShape` 方法返回一个 `Shape` 对象，您可以进一步自定义（大小、位置、边框等）。 |
| **设置填充颜色** | `FillColor` 属性控制内部颜色；您可以使用任意 `Color` 值（如 `Color.Red`、`Color.FromArgb(255, 0, 255, 0)` 等）。 |
| **隐藏形状** | `Hidden = true` 告诉 Word 在布局时忽略该形状，但仍保留在文档的 XML 中。这是存储不可见对象的标准方式。 |
| **保存文档** | 将更改持久化为 .docx 文件。保存后的文件将包含隐藏的矩形形状。 |

## 如何为形状设置填充颜色

更改填充颜色只需将 `System.Drawing.Color` 赋给 `FillColor` 属性。如果需要自定义色调，可使用 `Color.FromArgb`：

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*为何重要*：填充颜色存储在形状的 XML 中（`<w:fill>` 属性）。即使形状被隐藏，颜色仍然存在，这对后续处理（例如根据颜色代码提取元数据）很有帮助。

## 如何在最终文档中隐藏形状

`Hidden` 标志是 `Shape` 类的布尔属性。将其设为 `true` 可确保 Word 布局引擎忽略该形状。

```csharp
rectangleShape.Hidden = true;
```

**常见陷阱**

* **Hidden 与 Visible** – 如果以后需要显示形状，只需将 `Hidden = false` 即可。
* **兼容性** – 旧版 Word（2007 之前）可能对隐藏的绘图对象处理方式不同。Aspose.Words 通过在相应的 OOXML 元素中存储标志来保持兼容性。

## 如何以编程方式插入形状

虽然示例使用的是矩形，但同一 `InsertShape` 方法同样适用于许多其他形状（椭圆、三角形、直线等）。第一个参数是 `ShapeType` 枚举值：

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**提示**：如果需要将形状放置在页面的特定位置，可在调用 `InsertShape` 前使用 `builder.MoveTo` 设置插入点。

## 向已有文档添加矩形形状

通常您会在模板上进行增强，而不是从头开始。将步骤 1 替换为：

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

其余步骤保持不变，矩形将被添加到构建器光标所在的位置（默认情况下是文档末尾）。

## 处理边缘情况和变体

### 1. 再次显示形状

如果工作流的后续环节需要显示隐藏的矩形，可以切换该标志：

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. 添加边框（描边）

隐藏的形状仍可以在显示时拥有可见边框。设置 `LineColor` 和 `LineWidth` 属性：

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. 绝对定位矩形

若需精确布局控制，可将形状的 `WrapType` 切换为 `WrapType.Inline`（默认）或 `WrapType.TopBottom`，并调整 `Left`/`Top` 属性：

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. 使用不同的计量单位

Aspose.Words 使用点（1 pt = 1/72 英寸）。如果您更喜欢厘米，可先进行转换：

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## 完整可运行示例

下面是可直接复制、粘贴并运行的 *完整* 程序。它包含所有必要的 `using` 指令，并使用了您需要根据实际环境调整的绝对路径。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**预期结果**：文件 `HiddenRectangleShape.docx` 在 Microsoft Word 中打开时 *没有可见形状*，但隐藏的矩形已存在于文档 XML 中。您可以将 .docx 当作 zip 包打开，检查 `word/document.xml` 中是否有带有 `w:fill="yellow"` 和 `w:hidden="true"` 属性的 `<w:shape>` 元素。

## 结论

现在，您已经掌握了如何使用 C# 和 Aspose.Words **插入矩形形状**、**设置填充颜色**，以及 **隐藏形状** 使其在最终布局中不可见。相同的模式同样适用于其他形状类型、自定义颜色和已有模板。尝试添加边框、绝对定位以及不同计量单位，以满足您的精确需求。

### 后续步骤

* 探索 **在表格或页眉/页脚中插入形状** 用于水印的实现方式。  
* 将 **add rectangle shape** 与内容控件结合，创建动态占位符。  
* 查看 Aspose.Words 的 **shape manipulation** API，了解旋转、渐变填充和 SVG 导入等高级功能。

欢迎将代码应用到自己的项目中，并在评论区告诉我们您下一个解决的形状相关挑战是什么！

## 接下来该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并探索替代实现方案：

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}