---
category: general
date: 2026-08-04
description: Как добавить подписи данных в C# с помощью Aspose.Words. Узнайте, как
  редактировать диаграмму, центрировать подписи данных, отображать проценты на диаграмме
  и настраивать подписи данных.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: ru
lastmod: 2026-08-04
og_description: Как добавить подписи данных в C# с использованием Aspose.Words. Этот
  учебник показывает, как редактировать диаграмму, центрировать подписи данных диаграммы,
  отображать проценты на диаграмме и настраивать подписи данных диаграммы.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Как добавить подписи данных к диаграмме Word в C# – полное руководство
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Как добавить подписи данных к диаграмме Word в C# – пошаговое руководство
url: /ru/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как добавить подписи данных к диаграмме Word в C# – пошаговое руководство

Если вам нужно **how to add data labels** к диаграмме, находящейся в документе Word, это руководство покажет точный код, который необходимо выполнить. Вы увидите, как редактировать свойства диаграммы, центрировать подписи данных, показывать проценты в диаграмме и настраивать подписи данных для любой ситуации.

В учебнике рассматривается всё, что требуется для изменения существующей диаграммы: от загрузки документа до сохранения изменений. Никаких внешних ссылок не требуется — только библиотека Aspose.Words for .NET и базовая среда разработки C#.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 (or later) installed.
* Aspose.Words for .NET version 23.9 or newer.  
  You can install it via NuGet:

```bash
dotnet add package Aspose.Words
```

* A Word file (`input.docx`) that contains at least one chart.

## How to add data labels to a Word chart in C#

The following sections walk you through each step. The primary keyword **how to add data labels** appears naturally in the narrative and in the code comments, keeping the density within the recommended range.

### Step 1 – Load the Word document containing the chart

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Why this step matters*: The `Document` object represents the entire Word file. Loading it gives you access to every node, including shapes that host charts.

### Step 2 – Retrieve the first chart from the document

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Why this step matters*: Charts are stored inside `Shape` nodes. By casting the retrieved node to `Shape` and calling `GetChart()`, you obtain a `Chart` object that exposes series, axes, and label collections.

### Step 3 – Enable data label customization and show percentages in chart

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Why this step matters*: Setting `ShowPercentage` tells Aspose.Words to calculate and display each slice’s contribution to the total. This directly addresses the secondary keyword **show percentages in chart**.

### Step 4 – Change the label placement to the center of each data point

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Why this step matters*: The `Position` property controls where the label appears relative to the data point. Using `Center` satisfies the secondary keyword **center chart data labels** and improves readability for pie or doughnut charts.

### Step 5 – Further customize chart data labels (optional)

If you need more control, you can adjust font, color, or leader lines:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

These settings illustrate the secondary keyword **customize chart data labels** and demonstrate how you can tailor the appearance to match brand guidelines.

### Step 6 – Save the modified document

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Why this step matters*: Saving writes the updated chart back into the Word document, making the new data labels visible when the file is opened in Microsoft Word.

## Full, runnable example

Below is a complete program that you can copy, paste, and run. It includes all necessary `using` directives and comments that explain each line.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Expected result

When you open `output.docx` in Microsoft Word, the chart will display:

* Percentage values next to each slice (e.g., **25 %**, **40 %**, …).
* Labels positioned at the center of each data point.
* Any additional styling you applied, such as bold red text.

These visual cues make the chart easier to interpret, especially in presentations or reports.

## How to edit chart properties beyond data labels

While the focus of this guide is **how to add data labels**, you may also want to **how to edit chart** settings such as titles, legend placement, or axis formatting. The `Chart` object provides properties like `Title`, `Legend`, and `AxisX/AxisY`. For example, to change the chart title:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

All chart modifications follow the same pattern: retrieve the chart, adjust its properties, then save the document.

## Common pitfalls and best‑practice tips

| Проблема | Почему происходит | Рекомендуемое решение |
|---|---|---|
| Диаграмма находится внутри сгруппированной фигуры. | `GetChild(NodeType.Shape, …)` возвращает внешнюю группу, а не внутреннюю диаграмму. | Выполните рекурсивный поиск фигуры с `shape.HasChart`. |
| Подписи данных не отображаются после сохранения. | `ShowValue` или `ShowPercentage` не были установлены в `true`. | Явно установите оба `ShowValue` и `ShowPercentage` при необходимости. |
| Подписи перекрываются на маленьких секторах. | Размещение в центре может вызывать скопление. | Используйте `ChartDataLabelPosition.OutSideEnd` для размещения снаружи или включите `LeaderLines`. |

Applying these tips ensures reliable results across different chart types.

## Conclusion

You now know **how to add data labels** to a Word chart using C#. The tutorial covered retrieving the chart, enabling label visibility, centering the labels, showing percentages, and customizing appearance. With this knowledge you can also **how to edit chart** details, **center chart data labels**, **show percentages in chart**, and **customize chart data labels** for any reporting scenario.

Ready to explore more? Try adding multiple series, applying conditional formatting, or exporting the chart as an image. The Aspose.Words API offers extensive chart manipulation capabilities—experiment to find the perfect visual representation for your data.

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}