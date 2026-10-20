---
category: general
date: 2026-07-20
description: Добавьте подписи к круговой диаграмме с помощью Aspose.Words для .NET.
  Узнайте, как изменить подписи к круговой диаграмме, отобразить процентные подписи
  и быстро обновить подписи серий диаграммы.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: ru
lastmod: 2026-07-20
og_description: Добавьте подписи к круговым диаграммам в C# с помощью Aspose.Words.
  Овладейте изменением подписей круговых диаграмм, отображением процентных меток и
  обновлением подписей серий диаграммы всего за несколько шагов.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Добавьте подписи к круговой диаграмме в C# – Полный учебник Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Добавление подписей к круговой диаграмме в C# с использованием Aspose.Words –
  Полное руководство
url: /ru/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Добавление подписей к круговой диаграмме в C# с помощью Aspose.Words – Полное руководство

Need to **add pie chart labels** to a Word document using C#? With Aspose.Words you can effortlessly **change pie chart labels** and **display pie chart percentages** right inside the file—no manual tweaking in Word required.  

In this tutorial we’ll walk through the exact steps to **show percentage labels**, reposition them, and even **update chart series labels** for dynamic data. By the end you’ll have a reusable snippet that you can drop into any .NET project.

> **Quick preview:** After following the guide, opening the saved `.docx` will reveal a pie chart where each slice is labeled with its percentage, positioned outside the slice for maximum readability.

---

## Что понадобится

- **Aspose.Words for .NET** (последняя версия на 2026 год). Вы можете получить её из NuGet: `Install-Package Aspose.Words`.
- **Документ Word**, который уже содержит круговую или кольцевую диаграмму (мы будем называть его `Chart.docx`).
- Базовое знакомство с **C#** и Visual Studio (или вашей любимой IDE).

That’s it—no extra libraries, no COM interop, just pure managed code.

---

## Добавление подписей к круговой диаграмме — Полная реализация

Below is a **complete, runnable** C# console program that loads a document, modifies the first pie chart, and saves the result. Every line is commented so you’ll understand **why** we’re doing what we’re doing, not just **what**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Ожидаемый результат

Open `ChartWithCustomLabels.docx` in Microsoft Word. You should see the pie chart **with percentage labels positioned outside each slice**. The labels look something like “35 %”, “20 %”, etc., making the chart instantly understandable.

---

## Изменение подписей к круговой диаграмме: позиционирование и форматирование

If you only need to **change pie chart labels** without showing percentages, you can adjust the `Position` property to one of the following:

| Перечисление Position | Визуальный эффект |
|-----------------------|--------------------|
| `InsideEnd`   | Подписи находятся внутри сектора, прямо у его края. |
| `Center`      | Подписи отображаются в середине сектора (подходит для небольших кругов). |
| `OutsideEnd`  | Подписи находятся снаружи сектора, соединённые линией‑выноской (по умолчанию). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Совет:** `OutsideEnd` лучше всего работает, когда диаграмма имеет много секторов; он предотвращает наложение текста.

---

## Показ процентных подписей на круговой диаграмме

The property `ShowPercentage` is a **boolean flag**. Setting it to `true` tells Aspose.Words to calculate each slice’s contribution based on the underlying data source.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

You can also combine it with `ShowValue` if you need both raw numbers **and** percentages:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

When both flags are enabled, the label looks like “45 % (120)”.

---

## Обновление подписей серий диаграммы для динамических данных

Often you’ll generate charts on the fly—think monthly sales or survey results. To **update chart series labels** programmatically, modify the `Series` collection before you touch the data labels:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

This snippet demonstrates how to **update chart series labels** for any series, not just the first one. It’s handy when you’re building reports that combine actual vs. forecast data.

---

## Пограничные случаи и типичные ошибки

| Ситуация | На что обратить внимание | Решение |
|----------|--------------------------|---------|
| **Диаграмма не является круговой/кольцевой** | `Position` может не оказывать визуального эффекта. | Убедитесь, что `chart.Type` равен `ChartType.Pie` или `ChartType.Doughnut`. |
| **Диаграмма не найдена** | `GetChild` возвращает `null`. | Добавьте проверку (см. код) и выведите полезное сообщение в журнал. |
| **Старая версия Word** | Некоторые функции подписей игнорируются. | Сохраните как `.docx` (современный формат), чтобы обеспечить полную поддержку. |
| **Большое количество секторов** | Подписи могут накладываться друг на друга даже при `OutsideEnd`. | Рассмотрите возможность уменьшения количества секторов или увеличения размера диаграммы. |

---

## Полный рабочий пример (копировать‑вставить)

Below is the **entire program** you can copy into a new console project. Just replace `YOUR_DIRECTORY` with the folder that holds `Chart.docx`.



## Что стоит изучить дальше?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Установить параметры по умолчанию для подписей данных в диаграмме](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Настроить отдельную серию диаграммы](/words/english/net/programming-with-charts/single-chart-series/)
- [Вставить столбчатую диаграмму в Word с помощью Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}