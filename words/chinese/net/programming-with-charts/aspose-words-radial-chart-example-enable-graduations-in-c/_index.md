---
category: general
date: 2026-10-13
description: Aspose.Words 径向图示例，展示如何使用 C# 和 Aspose.Words 24.9+ 在径向图上启用刻度。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: zh
lastmod: 2026-10-13
og_description: Aspose.Words 径向图示例，演示使用 C# 和最新的 24.9+ 版库在径向图上启用刻度。
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Aspose.Words 径向图示例 – 在 C# 中启用刻度
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: Aspose.Words 径向图示例：在 C# 中启用刻度
url: /zh/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words 径向图表示例：在 C# 中启用刻度线

如果您正在寻找 **aspose.words radial chart example**，恭喜您来对地方了。本教程将手把手教您如何使用 Aspose.Words for .NET API 为径向图表打开刻度线（graduations）。

径向图表非常适合可视化循环数据，例如一天中的时间指标或季节性趋势。默认情况下，刻度线（圆形坐标轴周围的刻度标记）是隐藏的，这会导致图表阅读困难。只需一行代码即可启用它们，但前提是您了解正确的对象模型以及支持此功能的版本。

在本指南中，您将学习如何：

* 加载已包含径向图表的 Word 文档。  
* 通过 Aspose.Words 图表 API 访问图表形状。  
* 打开 **graduations visibility**（自 **Aspose.Words version 24.9** 起可用）。  
* 保存修改后的文档并验证结果。

完整、可运行的代码已提供，您可以直接复制粘贴到新的控制台项目中，立刻看到效果。

![Aspose.Words 径向图表示例（已启用刻度线）](https://example.com/images/radial-chart-graduations.png "Aspose.Words 径向图表示例，显示已启用的刻度线")

## 前置条件

在开始之前，请确保您具备以下条件：

| 要求 | 为什么重要 |
|------|------------|
| .NET 6.0 或更高版本 | Aspose.Words for .NET 24.9+ 目标为 .NET Standard 2.0，并在 .NET 6+ 上运行。 |
| Aspose.Words for .NET **24.9** 或更新版本 | `IsGraduationsVisible` 属性在 24.9 版中引入。旧版本会抛出 `MissingMemberException`。 |
| 包含径向图表的 Word 文档（`RadialChart.docx`） | 示例操作的是已有图表；从头创建图表是另一个主题。 |
| C# IDE（Visual Studio、Rider、VS Code） | 任意能够编译 .NET 项目的 IDE 都可。 |
| NuGet 包 `Aspose.Words` | 通过 `dotnet add package Aspose.Words --version 24.9.0`（或更高）安装。 |

> **专业提示：** 如果无法升级到 24.9，仍然可以修改其他图表属性，但刻度线将保持隐藏，因为 API 未公开该标志。

## Aspose.Words 径向图表示例 – 步骤指南

以下章节将整个过程拆分为若干易于跟随的步骤。每一步都提供了所需的完整代码以及简短的*原因*说明。

### 步骤 1：加载包含径向图表的文档

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**原因说明：**  
`Document` 是 **Aspose.Words chart API** 的入口点。它将 DOCX 文件加载到内存中，让您能够访问所有节点——段落、表格以及图表形状。如果文件未找到，`Document` 会抛出 `FileNotFoundException`，在生产代码中应进行相应处理。

### 步骤 2：从文档中检索第一个图表形状

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**原因说明：**  
图表以 `Shape` 节点的形式存储。使用 `GetChild` 方法并指定 `NodeType.Shape` 可以遍历 DOM 并返回第一个匹配的形状。将其强制转换为 `Chart` 后，即可访问图表特有的属性，如 `RadialChart`。空值检查可以在文档不包含图表时提供明确的错误提示，这在复用模板时是常见的边缘情况。

### 步骤 3：在径向图表上启用刻度线

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**原因说明：**  
`IsGraduationsVisible` 控制圆形坐标轴周围的刻度标记。设为 `true` 后，图表会渲染刻度线，提升需要精确读数的观众的可读性。该属性位于 `RadialChart` 下，它是 `Chart` 的子类型。如果在非径向图表（例如柱形图）上使用，`RadialChart` 将为 `null`，因此在更复杂的场景中应先验证图表类型。

#### 处理非径向图表（可选）

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

此防护代码可在源文档可能包含不同图表类型时提升代码的鲁棒性。

### 步骤 4：保存修改后的文档

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**原因说明：**  
调用 `Save` 会将内存中的 DOM 写回 .docx 文件，持久化您对图表所做的更改。输出文件可在 Microsoft Word、LibreOffice 或任何支持 DOCX 的查看器中打开。您将看到带有可见刻度线的径向图表。

## 完整、可运行的示例

下面是完整的程序代码，您可以将其粘贴到 .NET 控制台项目的 `Program.cs` 中。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### 预期输出

当您在 Word 中打开 `RadialChart_Graduations.docx` 时，径向图表的圆形坐标轴上会显示刻度线（graduations），效果如前面的截图所示。图表的其他部分（数据系列、图例、标题）保持不变。

## 常见变体和边缘情况

| 情形 | 解决方案 |
|------|----------|
| **旧版 Aspose.Words (< 24.9)** | 升级到最新的 NuGet 包。早期版本不存在 `IsGraduationsVisible` 属性。 |
| **同一文档中有多个图表** | 使用 `doc.GetChild(NodeType.Shape, index, true)` 并提供相应的 `index`，或遍历 `doc.GetChildNodes(NodeType.Shape, true)` 并根据 `ChartType.Radial` 进行过滤。 |
| **以编程方式创建的图表** | 使用 `DocumentBuilder` 插入图表，然后在其 `RadialChart.IsGraduationsVisible` 上设置属性。 |

## 接下来您可以学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。每篇资源均提供完整的可运行代码示例和逐步解释。

- [使用 Aspose.Words for .NET 在 Word 文档中更新图表系列数据](/words/english/net/programming-with-charts/modify-chart-series/)
- [使用 Aspose.Words for .NET 从 Word 文档中删除图表系列](/words/english/net/programming-with-charts/remove-chart-series/)
- [使用 Aspose.Words for .NET 在柱形图中隐藏绘图区域边框](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}