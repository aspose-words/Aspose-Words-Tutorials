---
category: general
date: 2026-09-05
description: Создайте диаграмму‑радар в Word с помощью C#. Узнайте, как быстро сгенерировать
  пустой документ Word, добавить диаграмму‑радар, задать её размер и включить деления.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: ru
lastmod: 2026-09-05
og_description: Создайте радарную диаграмму в Word с помощью C#. Это руководство покажет,
  как создать пустой документ Word, добавить радарную диаграмму, задать её размер
  и включить деления — всё за несколько минут.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Создание радиальной диаграммы в Word – пошаговое руководство по C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: Как создать радиальную диаграмму и добавить её в Word с помощью C#
url: /ru/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать радиальную диаграмму и добавить диаграмму в Word с помощью C#

Если вам нужно **create radar chart** внутри файла Word, это руководство проведет вас через весь процесс. Вы узнаете, как **generate blank word document**, вставить радиальную диаграмму, **set chart size word**, и включить деления осей — всё с помощью нескольких строк кода на C#.

Добавление визуальных данных в отчеты — распространённая потребность, и использование Aspose.Words упрощает задачу. В нижеописанных шагах мы также рассматриваем, как **add chart to word** документы программно, чтобы вы могли автоматизировать панели мониторинга, финансовые сводки или любой контент, основанный на данных.

## Требования

* .NET 6.0 или более поздняя версия установлена  
* Лицензия Aspose.Words for .NET (или бесплатная пробная версия) — библиотека предоставляет `Document`, `DocumentBuilder` и API диаграмм, используемые в этом руководстве  
* Visual Studio 2022 (или любой C# IDE)  

> **Pro tip:** Если вы тестируете, поместите DLL Aspose.Words в папку `bin` вашего проекта и подключите её через NuGet (`Install-Package Aspose.Words`).

## Как создать радиальную диаграмму в документе Word

Первый шаг — **generate blank word document**, который будет содержать диаграмму. Это дает вам чистый холст и позволяет управлять метаданными документа до добавления любого содержимого.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Почему это важно:* Пустой объект `Document` гарантирует отсутствие скрытых стилей или разделов, которые могут влиять на расположение диаграммы. Он также позволяет позже установить свойства документа (author, title), если это необходимо.

## Как добавить диаграмму в Word с помощью Aspose.Words

Далее создайте `DocumentBuilder`. Builder — это основной инструмент, позволяющий вставлять текст, изображения и диаграммы в документ.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

Теперь вы можете **add radar chart** непосредственно в месте, где находится курсор. Метод `InsertChart` принимает перечисление `ChartType`, ширину и высоту в пунктах.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*Почему 400 × 300?* Эти размеры обеспечивают чёткую, читаемую диаграмму на стандартной странице A4. При необходимости вы можете изменить размер позже с помощью шага **set chart size word**, если ваш макет требует другого соотношения сторон.

## Установка размера диаграммы в Word

Если необходимо точно настроить размер после вставки, вы можете изменить свойства `Width` и `Height` диаграммы. Это полезно, когда окружающий текст или поля страницы требуют другого визуального баланса.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Note:** Перегрузка `InsertChart` уже задаёт размер, поэтому приведённый выше код является необязательным и приведён для полноты.

## Включение делений на радиальной оси

Радиальная диаграмма наиболее полезна, когда радиальная ось показывает чёткие деления. Следующие настройки включают деления и задают интервал 30 градусов, что соответствует типичным компасным радиальным дисплеям.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Почему это важно:* Деления помогают читателям оценивать значения под каждым углом, повышая читаемость для заинтересованных сторон, не знакомых с данными.

## Сохранение документа с диаграммой

Наконец, запишите документ на диск. Вы можете выбрать любую папку; просто убедитесь, что путь существует.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

Когда вы откроете `RadialChart.docx` в Microsoft Word, вы увидите полностью отрисованную радиальную диаграмму, центрированную на странице, с указанным размером и делениями каждые 30 градусов.

### Ожидаемый результат

* Файл `.docx` с именем **RadialChart.docx**  
* Первая страница содержит радиальную диаграмму размером 400 × 300 пунктов  
* Ось X (радиальная ось) отображает деления при 0°, 30°, 60°, …, 330°  

Теперь вы можете заменить серию данных-заполнителя своими значениями, получив доступ к `radarChart.Series` — но это выходит за рамки базового руководства **add radar chart**.

## Распространённые варианты и граничные случаи

| Сценарий | Корректировка |
|----------|------------|
| **Different chart type** | Замените `ChartType.Radar` на `ChartType.Column`, `ChartType.Pie` и т.д. |
| **Multiple charts** | Вызывайте `InsertChart` многократно; каждый вызов размещает новую диаграмму после предыдущей. |
| **Large data sets** | Используйте `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` для заполнения большим количеством точек. |
| **Saving as PDF** | Вызовите `document.Save("RadialChart.pdf", SaveFormat.Pdf);` после добавления диаграммы. |
| **Running on .NET Core** | Убедитесь, что вы подключили пакет `Aspose.Words.NETCore`; использование API идентично. |

## Полный, исполняемый пример

Ниже приведена полная программа, которую вы можете скопировать и вставить в консольное приложение. Она включает все шаги, необязательные настройки размера и комментарии для ясности.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Запустите программу, откройте полученный файл, и вы увидите радиальную диаграмму точно как описано.

## Заключение

Теперь вы знаете, как **create radar chart** и **add chart to Word** документы с помощью C#. Руководство охватывало создание **blank word document**, вставку радиальной диаграммы, **set chart size word**, и включение делений осей. Имея эту основу, вы можете расширить решение до нескольких диаграмм, пользовательских серий данных или экспорта в PDF.

### Следующие шаги

* Исследуйте другие типы диаграмм с помощью `ChartType` (например, `Bar`, `Line`) — см. ключевое слово **add radar chart** для связанных примеров.

## Что вам следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}