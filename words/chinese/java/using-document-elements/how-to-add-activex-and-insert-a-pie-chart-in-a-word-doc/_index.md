---
category: general
date: 2026-08-17
description: 如何使用 Aspose.Words 在 Word 文档中添加 ActiveX 控件并插入饼图。拆分切片并在几步内保存为 DOCX。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: zh
lastmod: 2026-08-17
og_description: 如何使用 Aspose.Words 添加 ActiveX 控件、插入饼图、拆分切片并保存为 DOCX——完整的分步指南。
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: 如何在 Word 文档中添加 ActiveX 并插入饼图
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: 如何在 Word 文档中添加 ActiveX 并插入饼图
url: /zh/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文档中添加 ActiveX 并插入饼图

如果您需要 **如何添加 ActiveX** 控件并在 Word 文档中嵌入图表，本教程将为您展示一个完整、可运行的解决方案。使用 Aspose.Words，您可以放置一个 ActiveX CommandButton、创建饼图、为突出显示而炸开一个切片，最后 **保存为 DOCX**，仅需几行 C# 代码。

在下面的章节中，您将看到所有必需的导入、完整的代码清单以及每一步为何重要的解释。完成后，您就能够在任何通过代码生成的 .docx 文件中集成交互式控件和可视化数据。

## 前置条件

在开始之前，请确保您具备：

* .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.7+）
* Aspose.Words for .NET 包（可通过 NuGet 获取）
* 如 Visual Studio 2022 或 VS Code 等开发环境
* 对 C# 和 Word 对象模型的基本了解

无需额外的第三方图表库——Aspose.Words 已内置图表创建功能。

## 使用 Aspose.Words 添加 ActiveX 控件

ActiveX 控件允许您直接在 Word 文件中嵌入交互式 UI 元素。本指南将添加一个 **CommandButton**，后续可绑定 VBA 代码。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**为什么这样可行：**  
`InsertForms2OleControl` 会创建一个 OLE 容器，Word UI 将其识别为 ActiveX 控件。将控件类型设为 `CommandButton` 并设置标题后，用户在 Word 中打开文件时，它的行为就像普通按钮一样。

## 插入饼图并炸开切片

图表可在文档内直观展示数据。以下步骤演示 **如何插入图表**，特别是 **饼图**，并将第一块切片炸开。

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**为何要炸开切片：**  
调用 `SetExplode(0, true)` 会让 Aspose.Words 将第一个数据点偏移，吸引观看者的视线到该段。这是演示中常用的突出关键数值的技巧。

## 保存为 DOCX

在添加 ActiveX 按钮和图表后，将文档持久化到磁盘。本步骤演示使用标准方法 **保存为 DOCX**。

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

文件 `Output.docx` 现在包含一个交互式按钮、一个带炸开切片的饼图，并且可以在 Microsoft Word 中打开，无需额外插件。

## 完整可运行示例

将所有内容整合在一起，下面是一个可直接复制到控制台应用程序并立即运行的自包含程序。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**预期结果：**  
在 Word 中打开 `Output.docx` 时，会看到一个标有 *Click Me* 的按钮以及一个第一块（January）已偏离其余部分的饼图。按钮已准备好接受 VBA 事件处理，图表可使用 Word 内置的图表工具进行编辑。

## 常见问题与边缘情况

* **我可以添加其他类型的 ActiveX 吗？**  
  可以。将 `Forms2OleControlType.CommandButton` 替换为 `Forms2OleControlType` 枚举中的任意值（例如 `CheckBox`、`OptionButton`）。插入方式保持不变。

* **如果我需要不同的图表类型怎么办？**  
  在 `InsertChart` 调用中使用 `ChartType.Bar`、`ChartType.Line` 等。**如何插入图表** 的步骤保持一致，仅枚举值不同。

* **如何控制炸开切片的大小？**  
  Aspose.Words 目前仅支持二元炸开标志（true/false）。若需更精细的控制（如偏移距离），需在保存后编辑底层 OOXML。

* **文档是否兼容旧版 Word？**  
  保存为 DOCX 可兼容 Word 2007 及以后版本。若需 Word 2003，可改为 `SaveFormat.Doc`，但该格式对 ActiveX 的支持有限。

* **是否需要引用 `System.Drawing`？**  
  不需要。所有绘图对象均由 Aspose.Words 提供，唯一必需的 NuGet 包是 `Aspose.Words`。

## 结论

现在您已经掌握了 **如何添加 ActiveX**、**插入饼图**、**炸开饼图切片**，以及使用 Aspose.Words for .NET **保存为 DOCX** 的完整流程。完整示例覆盖了从文档创建到最终持久化的每一步，并解释了每个 API 调用背后的原理。

接下来，您可以探索：

* 为 CommandButton 点击添加 VBA 宏（**如何插入图表** 并自动更新数据）
* 自定义图表外观（颜色、数据标签）以匹配企业品牌
* 嵌入其他 ActiveX 控件，如 **ComboBox** 或 **ListBox**，以实现更丰富的表单

欢迎尝试修改代码、替换示例数据，并将该方案集成到您自己的文档生成流水线中。祝编码愉快！


## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。每个资源均提供完整的可运行代码示例和逐步解释。

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}