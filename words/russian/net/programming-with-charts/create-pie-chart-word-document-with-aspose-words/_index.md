---
category: general
date: 2026-08-10
description: Создайте документ Word с круговой диаграммой, используя Aspose.Words.
  Узнайте, как вставить диаграмму, настроить цвета круговой диаграммы и изменить цвет
  сектора диаграммы в C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: ru
lastmod: 2026-08-10
og_description: Создайте документ Word с круговой диаграммой с помощью Aspose.Words.
  Это руководство объясняет, как вставить диаграмму, настроить цвета круговой диаграммы
  и изменить цвет сектора в приложении C#.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Создание круговой диаграммы в документе Word – руководство Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Создать документ Word с круговой диаграммой с помощью Aspose.Words
url: /ru/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Word‑документа с круговой диаграммой с помощью Aspose.Words

Если вам нужно **создать Word‑документ с круговой диаграммой** программно, этот учебник покажет, как это сделать. Мы пройдём через вставку диаграммы, **кастомизацию цветов круговой диаграммы** и **изменение цвета сектора** с использованием Aspose.Words для .NET.

Вы увидите полностью готовый пример, который можно скопировать в Visual Studio, запустить и сразу открыть сгенерированный *.docx* для проверки стилизованной круговой диаграммы. Внешняя документация не требуется — всё, что нужно, находится в этом руководстве.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 SDK или более поздняя версия  
* Действующая лицензия Aspose.Words для .NET (или временный оценочный ключ)  
* Visual Studio 2022 (или любой другой IDE для C#)  

Код использует только пространства имён `Aspose.Words` и `Aspose.Words.Drawing.Charts`, поэтому дополнительных пакетов NuGet помимо библиотеки Aspose.Words не требуется.

## Создание Word‑документа с круговой диаграммой — полный пример

Следующая программа на C# создаёт новый Word‑документ, вставляет круговую диаграмму, стилизует первые два сектора и сохраняет файл. Каждый шаг подробно объяснён.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Пояснение к каждому шагу

| Шаг | Что делает | Почему это важно |
|------|--------------|----------------|
| **1** | Создаёт новый `Document` и `DocumentBuilder`. | `DocumentBuilder` предоставляет удобные методы для вставки содержимого, например диаграмм, в файл Word. |
| **2** | Вызывает `InsertChart` с `ChartType.Pie` и фиксированным размером. | `InsertChart` — это метод **вставки диаграммы**; указание ширины/высоты гарантирует, что диаграмма хорошо впишется на страницу. |
| **3** | Добавляет серию данных с тремя категориями и числовыми значениями. | Круговая диаграмма без данных невидима; её заполнение демонстрирует шаги стилизации. |
| **4** | Устанавливает `Explosion` для первой точки. | "Взрыв" сектора привлекает внимание к определённому сегменту — полезно для выделения ключевых данных. |
| **5** | Устанавливает `ForeColor` для первых двух точек. | Это основа **кастомизации цветов круговой диаграммы**; можно использовать любой `System.Drawing.Color`. |
| **6** | Показано, как **изменить цвет сектора** для остальных секторов. | Демонстрирует, что стилизация не ограничивается первыми двумя секторами; каждый сектор можно раскрасить индивидуально. |
| **7** | Сохраняет документ как `PieChartStyled.docx`. | Итоговый файл можно открыть в Microsoft Word, Google Docs или любом совместимом просмотрщике. |

#### Ожидаемый результат

Открывая `PieChartStyled.docx`, вы увидите одну страницу с круговой диаграммой размером 400 × 300 pt:

* Сектор 1 (оранжевый) «взрывается» наружу.  
* Сектор 2 (зелёный) расположен рядом с взорванным сектором.  
* Сектор 3 (стальной синий) заполняет оставшийся сегмент.

Диаграмма отражает значения данных (30, 45, 25) и пользовательские цвета, которые вы задали.

## Как стилизовать круговую диаграмму — дополнительные советы

* **Используйте цвета темы** — вместо жёсткого указания `Color.Orange` можно брать цвета из темы документа:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Добавьте подписи данных** — если хотите отображать проценты на диаграмме:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Динамическое изменение размера** — вычисляйте размер диаграммы исходя из полей страницы:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Эти варианты демонстрируют гибкость **стилизации круговой диаграммы** за пределами базового примера.

## Часто задаваемые вопросы

**В: Работает ли это с .NET Core?**  
**О:** Да. Aspose.Words для .NET совместим с .NET Core, .NET 5, .NET 6 и более новыми версиями. Достаточно подключить тот же пакет NuGet.

**В: Что если нужен график‑пончик вместо круговой диаграммы?**  
**О:** Замените `ChartType.Pie` на `ChartType.Doughnut`. Те же API стилизации (`Explosion`, `ForeColor`) применимы.

**В: Могу ли я вставить диаграмму в существующий документ?**  
**О:** Откройте существующий файл с помощью `new Document("Existing.docx")`, создайте `DocumentBuilder` для этого документа и вызовите `InsertChart` в нужной позиции курсора.

**В: Как работать с большими наборами данных?**  
**О:** Круговые диаграммы лучше использовать для ограниченного количества категорий (обычно < 10). При большом числе категорий предпочтительнее столбчатая или линейная диаграмма.

## Полный исходный код в одном блоке

Ниже представлен полный код программы в одном блоке для удобного копирования:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Запуск этого кода создаёт Word‑документ со стилизованной круговой диаграммой, описанной выше.

## Заключение

Теперь вы знаете, как **создавать Word‑документы с круговой диаграммой** с помощью Aspose.Words, **кастомизировать цвета круговой диаграммы** и **изменять цвет сектора** программно. Руководство охватывало вставку диаграммы, заполнение данными, «взрыв» сектора, применение пользовательских цветов и сохранение результата.  

Отсюда вы можете изучать связанные темы, такие как **вставка других типов диаграмм**, добавление легенд или генерация многостраничных отчётов с несколькими диаграммами. Экспериментируйте с различными цветовыми схемами и наборами данных, чтобы подобрать оптимальное решение для ваших отчётных задач.

Удачной разработки!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Вставка столбчатой диаграммы в Word с помощью Aspose.Words для .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Вставка областной диаграммы в документ Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Создание точечной диаграммы Word с использованием Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}