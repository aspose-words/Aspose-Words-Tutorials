---
category: general
date: 2026-08-23
description: 学习如何使用 Aspose.Words 在 C# 中对形状进行分组。本指南还涵盖了如何插入矩形形状以及在复杂文档中添加形状的 Word。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: zh
lastmod: 2026-08-23
og_description: 如何在 C# 中使用 Aspose.Words 对形状进行分组。请跟随本完整教程，插入矩形形状、向 Word 添加形状，并高效地对多个形状进行分组。
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: 如何在 C# 中对形状进行分组——一步一步指南
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: 如何在 C# 中使用 Aspose.Words 对形状进行分组
url: /zh/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用 Aspose.Words 对形状进行分组

如果您需要在 Word 文档中以编程方式 **如何对形状进行分组**，本教程将展示使用 Aspose.Words for .NET 的完整步骤。无论您是在构建报表生成器、模板引擎，还是绘图工具，您都将学习如何启动一个组、插入矩形形状，以及在不离开代码的情况下向形状中添加 Word 级别的内容。

您还将看到如何 **将多个形状分组**，这在您希望将一组对象作为单个实体进行移动、旋转或设置样式时至关重要。下面的示例基于最新的 Aspose.Words 24.x 版本，仅需 .NET 6 或更高版本。

## 前置条件

- .NET 6 SDK（或任何 Aspose.Words 支持的 .NET 版本）
- Visual Studio 2022 或 VS Code
- Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）
- 对 C# 和 Aspose.Words 对象模型的基本了解

> **专业提示：** 使用 Aspose 提供的免费评估许可证，可在测试期间避免水印限制。

## 使用 Aspose.Words 对形状进行分组的方法

下面是一个完整的、可运行的示例程序，演示 **如何启动分组**、添加矩形并完成分组。代码遵循您提供的代码片段的逻辑流程，同时加入了上下文、错误处理和注释，以提升可读性。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### 每一步的重要性

| 步骤 | 目的 | 与关键词的关联 |
|------|------|----------------|
| **创建一个新的空白文档** | 为形状操作提供干净的画布。 | 为后续的 **add shapes word** 做准备。 |
| **初始化 DocumentBuilder** | Builder 是插入对象的主要 API。 | 在能够 **how to start group** 之前必须先完成此步骤。 |
| **StartGroupShape** | 开始一个逻辑容器；随后所有形状都成为该组的成员。 | 直接回答 **how to start group**。 |
| **InsertShape**（矩形、椭圆、文本） | 将单个形状放入组内。矩形调用满足 **insert rectangle shape**；文本形状满足 **add shapes word**。 | 演示 **group multiple shapes**。 |
| **EndGroupShape** | 完成分组，使您可以将其作为整体移动或设置样式。 | 完成 **how to group shapes** 工作流。 |

## 插入矩形形状 – 深入解析

`InsertShape` 方法接受 `ShapeType` 枚举、宽度和高度。若要 **insert rectangle shape** 并自定义样式，可在示例基础上进行扩展：

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **为什么要设置样式？** 样式可以确保矩形在后续重新定位组时仍然突出显示。同时也演示了在关闭组之前即可设置形状属性。

## 添加 Word 级别的形状（add shapes word）

如果需要在形状内部直接嵌入文本——通常称为 “WordArt” 或 “文本框”，请使用 `ShapeType.TextPlainText`。插入后，您可以通过 `DocumentBuilder.Writeln` 或访问形状的 `TextBox` 属性来写入文本：

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

这满足了 **add shapes word** 关键词的需求，并展示了文本如何随组一起移动。

## 将多个形状分组 – 实际场景

当您 **group multiple shapes** 时，可以将它们视为单个对象进行定位、旋转或缩放。例如，组关闭后，您可以移动整个组：

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

或者旋转该组：

```csharp
group.Rotation = 45; // degrees
```

这些操作之所以可行，是因为这些形状共享同一个父组。

## 处理边缘情况

1. **嵌套组** – Aspose.Words 支持组内再组。要创建嵌套组，只需在内部组的 `EndGroupShape` 之前再次调用 `StartGroupShape`。
2. **空组** – 如果启动了组但从未插入形状，`EndGroupShape` 仍会创建一个空容器。虽然无害，但可能会略微增加文件大小。
3. **兼容性** – 生成的 DOCX 可在 Word 2010 及更高版本中正常工作。旧版本可能会忽略分组元数据，请务必在目标 Word 版本上进行测试。

## 完整源码供参考

将以下内容保存为 `.NET` 控制台项目中的 `Program.cs`。代码无需修改即可编译运行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### 预期输出

在 Microsoft Word 中打开 `GroupedShapes.docx` 时，将看到：

- 一个浅珊瑚色的矩形、一个椭圆和一个文本框——它们在视觉上被绑定在一起。
- 选中组内任意部分时，整个组都会被选中（出现单一的边界框）。
- 移动或旋转组时，三个形状会同步移动。

## 常见问题

**问：我可以对文档中已经存在的形状进行分组吗？**  
答：可以。获取已有的 `Shape` 对象，调用 `builder.StartGroupShape()`，使用 `builder.InsertShape(existingShape)` 重新插入它们，然后调用 `EndGroupShape()`。

**问：分组会影响底层 XML 吗？**  
答：Aspose.Words 会添加一个 `<w:grpSp>` 元素，其中包含每个形状的 `<w:sp>` 节点。这完全符合 Office Open XML 规范。

**问：如果以后需要取消分组怎么办？**  
答：没有直接的 “ungroup” API，但您可以遍历组的子形状 (`group.GroupShape.Children`) 并将它们复制到文档主体中。

## 后续步骤

既然您已经掌握了 **how to group shapes**，可以进一步探索以下相关主题：

- **对分组形状应用复杂格式** – 学习如何设置渐变填充、阴影效果和线条样式。  
- **将分组形状导出为图像** – 使用 `Shape.GetShapeRenderer().Save(...)` 将组栅格化为图片。  
- **创建动态图表** – 将数据驱动的定位与分组相结合，自动生成流程图。

这些内容都建立在本指南的基础之上，帮助您创建更丰富、更具交互性的 Word 文档。

---

*祝编码愉快！如果本指南对您有帮助，请与团队分享或给包含示例项目的仓库加星。*


## 接下来应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您在自己的项目中进一步掌握 API 功能并探索替代实现方式。

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}