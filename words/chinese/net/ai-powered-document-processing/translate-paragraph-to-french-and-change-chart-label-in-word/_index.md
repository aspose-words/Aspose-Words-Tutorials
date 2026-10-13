---
category: general
date: 2026-10-10
description: 将段落翻译成法语，并学习如何更改图表数据标签、定制图表数据标签，以及使用 Aspose.Words AI 保存编辑后的 docx 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: zh
lastmod: 2026-10-10
og_description: 将段落翻译成法语，并学习如何更改图表数据标签、定制图表数据标签，以及使用 Aspose.Words AI 保存编辑后的 docx 文件。
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: 将段落翻译成法语并在 Word 中更改图表标签
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: 将段落翻译成法语并在 Word 中更改图表标签
url: /zh/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将段落翻译为法语并在 Word 中更改图表标签

如果您需要在同一个 Word 文档中 **将段落翻译为法语** 并同时更新图表，本指南将一步步展示具体操作。使用 Aspose.Words AI，您可以自动翻译文本，然后修改图表的数据标签，最后保存编辑后的 `.docx` 文件——全部只需几个简单步骤。

本教程涵盖了从加载源文件到持久化更改的全部过程。完成后，您将能够翻译任意段落、定制图表数据标签，并生成可供分发的新 Word 文件。无需外部脚本；整个工作流都在一个 C# 程序中完成。

## 前置条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.7+）
- Aspose.Words for .NET 许可证（或免费评估密钥）
- 用于 Google AI 翻译器的互联网访问（`Translator` 类在底层使用 Google 的 API）
- 一个包含至少一个段落和一个图表的 Word 文档（`input.docx`）

## 步骤 1：设置项目并导入命名空间

创建一个新的控制台应用程序并添加 Aspose.Words NuGet 包：

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

现在在 `Program.cs` 顶部加入所需的命名空间：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

这些导入让您可以访问文档加载、AI 翻译以及图表编辑功能。

## 步骤 2：加载源 Word 文档

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

加载文件会在内存中创建一个表示，您可以在不触碰磁盘上原始文件的情况下查询和修改它。

## 步骤 3：将第一段翻译为法语

第一段通常是标题或引言句子，是翻译的理想对象。`Translator` 类封装了对 Google AI 模型的调用。

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**为什么这样有效：**  
`paragraph.Runs.Clear()` 会移除所有现有的文本运行，确保新翻译不会与旧内容拼接。`new Run(document, translatedText)` 会创建一个继承段落格式的全新运行。

## 步骤 4：定位第一个图表并自定义其数据标签

图表以 `Shape` 节点（类型为 `NodeType.Shape`）的形式存储。可以使用 `GetChild` 获取第一个图表。

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**关键步骤说明：**

- `GetChild(NodeType.Shape, 0, true)` 执行深度优先搜索并返回第一个形状，在本例中即为图表。
- `ChartSeries` 表示一组数据点；第一个系列 (`Series[0]`) 通常对应主数据集。
- `ChartDataLabelPosition.OutsideEnd` 将标签移动到柱形的末端之外，提升可读性。
- 将 `dataLabel.Text` 设置为法语字符串，使标签与已翻译的段落保持一致。

## 步骤 5：保存包含翻译段落的文档

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

此时文档已包含法语段落，但仍保留原始的图表配置。

## 步骤 6：保存包含更新图表的文档

您可以复用同一个 `Document` 实例——无需重新加载——因为图表的修改已经在内存中完成。

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

两个文件现已准备好分发：

- **`translated.docx`** – 包含法语段落。
- **`chart-updated.docx`** – 同时包含法语段落和自定义的图表标签。

## 完整、可运行的示例

下面是完整程序，您可以直接复制粘贴到 `Program.cs` 中。只要将 `YOUR_DIRECTORY` 替换为实际文件夹路径，即可编译运行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

namespace WordAiDemo
{
    class Program
    {
        static void Main()
        {
            // ---------- Load the source document ----------
            string inputPath = @"YOUR_DIRECTORY/input.docx";
            Document document = new Document(inputPath);
            Console.WriteLine("Document loaded.");

            // ---------- Translate the first paragraph ----------
            Paragraph paragraph = document.FirstSection.Body.FirstParagraph;
            string original = paragraph.GetText();
            string translated = Translator.Translate(original, Language.French);
            Console.WriteLine


## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您在已有技巧的基础上进一步深入。每个资源都提供完整的可运行代码示例和逐步解释，助您掌握更多 API 功能并在项目中探索替代实现方案。

- [自定义图表数据标签](/words/english/net/programming-with-charts/chart-data-label/)
- [在图表中格式化数据标签的数字](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [图表数据标签](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}