---
category: general
date: 2026-09-30
description: 使用 C# 在 Word 中对形状进行分组——学习如何对形状进行分组、添加矩形和椭圆，并以编程方式在 Word 文档中插入矩形形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: zh
lastmod: 2026-09-30
og_description: 使用 C# 和 Aspose.Words 在 Word 中对形状进行分组。请参阅本完整指南，了解如何添加矩形、添加椭圆，并学习如何高效地对形状进行分组。
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: 使用 C# 在 Word 中对形状进行分组 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 和 Aspose.Words 在 Word 中对形状进行分组
url: /zh/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 和 Aspose.Words 在 Word 中对形状进行分组

如果您需要 **在 Word 中以编程方式对形状进行分组**，本指南将一步步演示。您将看到如何添加矩形、添加椭圆，然后使用 Aspose.Words for .NET 将它们合并为一个组形状。

在自动生成报告、合同或营销材料时，处理形状是常见需求。完成本教程后，您将拥有一个可复用的 C# 方法，能够加载 DOCX 文件、插入矩形和椭圆、对它们进行分组并保存结果——全部无需手动打开 Word。

## 前置条件

在开始之前，请确保您已具备：

* 已安装 .NET 6.0 SDK 或更高版本  
* 如 Visual Studio 2022（社区版即可）等开发环境  
* Aspose.Words for .NET 许可证或免费评估版（API 在无许可证情况下仍可使用，但会添加水印）  

您还需要在代码可引用的文件夹中准备一个源 Word 文档（`input.docx`）。该文档可以是空的；本教程侧重于形状处理。

## 第一步：创建新控制台项目并添加 Aspose.Words

打开终端或 Visual Studio 命令提示符，运行：

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

此命令会创建一个名为 **WordShapeDemo** 的全新控制台应用，并添加 `Aspose.Words` NuGet 包，其中包含用于操作 Word 文件的 `Document` 和 `DocumentBuilder` 类。

## 第二步：加载或创建文档

在处理 **Word 中的组形状** 时，第一步是获取 `Document` 对象。您可以加载已有的 DOCX 文件，也可以从空白文档开始。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

`Document` 类代表整个 Word 文件。加载文件后，您将拥有一个可用于插入形状的画布。

## 第三步：开始组形状

*组形状* 允许您将多个独立形状视为一个单元——非常适合一起移动或缩放。要开始一个组，请在 `DocumentBuilder` 上调用 `StartGroupShape()`。

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

调用 `StartGroupShape` 告诉 Aspose.Words，随后插入的所有形状都属于同一个逻辑组，直到您调用 `EndGroupShape` 为止。

## 第四步：在 Word 中添加矩形形状

组已打开后，插入矩形。`InsertShape` 方法接受一个 `ShapeType` 枚举，随后是宽度和高度（单位为点）。

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

矩形成为该组的第一个成员。后续如果需要，您可以自定义其填充、轮廓或文本。

## 第五步：在 Word 中添加椭圆形状

接下来，添加椭圆（宽高相等时为圆形）。这演示了 **如何添加椭圆**，使用相同的 builder。

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

两个形状现在共享同一坐标空间，便于在视觉上对齐。

## 第六步：关闭组形状定义

当所有期望的成员都已添加完毕后，关闭组。这会将形状集合最终确定为 Word 中的单一对象。

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

此时文档中包含一个由矩形和椭圆组成的单一组形状。

## 第七步：保存修改后的文档

最后，将更改写回磁盘。您可以覆盖原文件，也可以创建新文件。

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

运行程序后会生成 `output.docx`。在 Microsoft Word 中打开该文件，选中形状，您会发现矩形和椭圆一起移动——这证明 **在 Word 中对形状进行分组** 的操作已成功。

### 预期结果

* Word 文件包含一个单一的组对象。  
* 选中该组后，您可以同时拖动、缩放或旋转矩形和椭圆。  
* 无需手动操作 Word，所有工作均通过 C# 代码完成。

![Word 文档中的分组形状](grouped-shapes.png "显示 Word 文档中分组的矩形和椭圆形状的截图")

*图片替代文字：“显示 Word 文档中分组的矩形和椭圆形状的截图”*（满足图片 alt‑text 要求）。

## 为什么形状分组很重要

形状分组不仅是视觉上的便利，还能：

* **保持布局一致性**——移动组时，内部相对位置保持不变。  
* **一次性应用变换**——对整个组进行旋转或缩放，而不是对每个形状单独操作。  
* **简化后续处理**——其他工具读取 DOCX 时，只会看到一个复合形状，降低复杂度。

如果以后需要向同一逻辑单元添加更多形状（例如直线或文本框），只需在 `EndGroupShape` 之前再次调用 `InsertShape` 即可。

## 常见变体与边缘情况

| 情况 | 处理方式 |
|-----------|-----------------|
| **不同单位** – 您的测量值是厘米 | 在调用 `InsertShape` 前将厘米转换为点（`1 cm ≈ 28.35 pt`）。 |
| **添加文本标签** – 想在组内放置说明文字 | 在矩形和椭圆之后插入 `ShapeType.TextBox`，然后设置其 `Text` 属性。 |
| **应用填充颜色** – 需要一个蓝色矩形 | 在 `InsertShape` 后，通过 `builder.CurrentParagraph.Runs[0].Font` 获取最近的形状，并设置 `shape.FillColor = System.Drawing.Color.Blue;`。 |
| **使用不同文档格式** – 目标是 `.doc` 而非 `.docx` | 代码保持不变，只需在调用 `Save` 时更改文件扩展名。Aspose.Words 会自动处理格式。 |

## 专业技巧

* **复用 builder** – 您可以在同一文档中启动并结束多个组，只需在 `EndGroupShape` 后再次调用 `StartGroupShape`。  
* **性能** – 在单个 `StartGroupShape/EndGroupShape` 块内批量插入形状，比在组外逐个插入更快。  
* **授权** – 评估许可证会在首页添加水印。生产环境请安装正式许可证以去除水印。

## 结论

现在，您已经掌握了使用 C# **在 Word 中对形状进行分组** 的方法，了解了 **如何添加矩形**、**如何添加椭圆**，并学会了使用 Aspose.Words 在 Word 文档中 **插入矩形形状**。完整的可运行示例演示了从项目设置到最终保存文件的每一步。

接下来，您可以探索更多形状类型、应用样式，或将组形状与表格、图片结合，创建更复杂的程序化文档。

---

**后续步骤**

* 学习 **旋转组形状**：在关闭组后使用 `Shape.RotationAngle`。  
* 探索 **矩形和椭圆的填充与轮廓自定义**。  
* 将此逻辑集成到 ASP.NET Core API 中，以按需生成报告。  

祝编码愉快！


## 接下来应该学习什么？

以下教程涵盖与本指南紧密相关的主题，帮助您进一步掌握 API 功能并在项目中尝试替代实现方式。

- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words for .NET 在 Word 文档中插入形状](/words/english/net/working-with-shapes/insert-shape/)
- [在 Word 中创建矩形形状 – 完整 Aspose.Words 指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}