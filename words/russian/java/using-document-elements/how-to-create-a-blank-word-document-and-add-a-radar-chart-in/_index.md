---
category: general
date: 2026-09-21
description: Создайте пустой документ Word и узнайте, как вставить радиальную диаграмму
  в файл Word с помощью DocumentBuilder – пошаговое руководство.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: ru
lastmod: 2026-09-21
og_description: Создайте пустой документ Word и вставьте в него диаграмму‑радар с
  помощью Aspose.Words. Следуйте этому руководству, чтобы быстро создать диаграмму
  в документе Word.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: Создайте пустой документ Word и добавьте радиальную диаграмму — полное руководство
  по C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: Как создать пустой документ Word и добавить радарную диаграмму в C#
url: /ru/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать пустой документ Word и добавить радиальную (radar) диаграмму в C#

Если вам нужно **создать пустой документ Word** и встроить радиальную (radar) диаграмму, этот учебник предоставляет готовое решение. Вы увидите, как использовать Aspose.Words .NET для генерации файла, вставки диаграммы и сохранения результата — всё в нескольких лаконичных шагах.

Пустой документ предоставляет чистый холст для любого сценария автоматической генерации отчётов, а добавление радиальной диаграммы позволяет визуализировать многомерные данные непосредственно в Word. К концу руководства вы сможете генерировать документ Word с диаграммой без ручного редактирования.

## Что вы узнаете

* Как **программно создать пустой документ Word** с помощью C#.
* Точный код **как вставить радиальную диаграмму** с помощью `DocumentBuilder`.
* Способы **вставки диаграммы в файл Word** и настройки её размеров.
* Как **создать диаграмму в документе Word** и проверить результат.
* Советы по **добавлению радиальной диаграммы в файлы Word**, включая типичные подводные камни.

### Предварительные требования

* .NET 6.0 или новее (код также работает с .NET Framework 4.6+).
* Aspose.Words for .NET (NuGet‑пакет `Aspose.Words` версии 23.9 или новее).
* Базовые знания C# и Visual Studio или вашей предпочтительной IDE.

## Создание пустого документа Word с помощью C#

Первый шаг — создать пустой объект `Document`. Этот объект представляет полностью пустой файл `.docx`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` формирует структуру файла, но пока не содержит ни разделов, ни страниц. Aspose.Words автоматически добавляет раздел по умолчанию, когда вы начинаете добавлять содержимое, поэтому следующий шаг работает без дополнительной конфигурации.

## Как вставить радиальную диаграмму в файл Word

Радиальная диаграмма (также называемая radial chart) визуализирует точки данных на осях, расходящихся из центральной точки. Aspose.Words предоставляет метод `DocumentBuilder.insertChart` для этой задачи.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` возвращает объект `Chart`, который можно дальше настраивать. Диаграмма появляется на первой странице пустого документа, потому что построитель по умолчанию позиционируется в начале документа.

## Вставка диаграммы в файл Word — добавление серий данных

Диаграмма без данных невидима. Заполните радиальную диаграмму одной или несколькими сериями, чтобы она стала осмысленной.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

Можно добавить столько серий, сколько требуется. Каждая серия может иметь собственное имя, которое отображается в легенде диаграммы. Точки данных соответствуют радиальным осям; порядок их добавления определяет их расположение вокруг круга.

## Генерация диаграммы в документе Word — сохранение файла

После построения диаграммы сохраните документ на диск. Выберите место, где у вас есть права записи.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Когда вы откроете полученный файл `.docx` в Microsoft Word, вы увидите пустую страницу с радиальной диаграммой размером 400 × 300 пунктов, заполненной примерными данными.

### Ожидаемый результат

* Файл `RadialChartExample.docx` на рабочем столе.
* На первой странице радиальная диаграмма с пятью точками данных, помеченными как “Series 1”.
* Дополнительный текст отсутствует, поскольку документ начинался пустым.

## Добавление радиальной диаграммы в Word — обработка типичных граничных случаев

### 1. Изменение размера диаграммы после вставки

Если начальные размеры не подходят вашему макету, измените размер диаграммы так:

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. Вставка диаграммы в определённое место

Можно переместить курсор построителя к закладке, ячейке таблицы или абзацу перед вызовом `InsertChart`.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. Настройка внешнего вида диаграммы

Aspose.Words раскрывает полную модель объекта диаграммы, позволяя задавать заголовки, подписи осей и цвета.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. Работа с отсутствующими шрифтами

Если в целевой среде отсутствует шрифт, использованный в диаграмме, Aspose.Words заменит его шрифтом по умолчанию. Чтобы обеспечить согласованность, внедрите необходимые шрифты:

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. Экспорт в другие форматы

Тот же документ можно сохранить как PDF, HTML или PNG без дополнительных изменений кода:

```csharp
doc.Save("RadialChartExample.pdf");
```

## Полный, готовый к запуску пример

Собрав все части вместе, вы получите одну программу, которую можно скопировать, вставить и запустить.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Запустите эту программу, откройте сгенерированный файл, и вы увидите профессиональную радиальную диаграмму, готовую к распространению.

## Заключение

Теперь вы знаете, как **создать пустой документ Word**, **вставить радиальную диаграмму** и **создать диаграмму в документе Word** с помощью Aspose.Words. Следуя описанным шагам, вы также сможете **добавлять радиальные диаграммы в файлы Word** в любой автоматизированной цепочке отчётности, настраивать размер, стиль и экспортировать в дополнительные форматы.

**Следующие шаги**

* Исследуйте другие типы диаграмм (`ChartType.Column`, `ChartType.Pie`), чтобы расширить набор средств отчётности.
* Комбинируйте несколько диаграмм на одной странице, вызывая `InsertChart` последовательно.
* Интегрируйте данные из базы данных или CSV‑файла для динамического заполнения серий.
* Ознакомьтесь с документацией Aspose.Words для продвинутых параметров форматирования, таких как условные подписи данных и шаблоны диаграмм.

Не стесняйтесь экспериментировать с кодом, менять размеры или заменять примерные данные реальными бизнес‑метриками. Приятного кодинга!


## Что стоит изучить дальше?


Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}