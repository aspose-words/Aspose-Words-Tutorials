---
category: general
date: 2026-07-26
description: Вставьте круговую диаграмму в документ Word с помощью Aspose.Words. Узнайте,
  как добавить диаграмму, «взрывать» сектор и отображать проценты всего за несколько
  шагов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: ru
lastmod: 2026-07-26
og_description: Вставьте круговую диаграмму в файл Word с помощью Aspose.Words. Следуйте
  этому руководству, чтобы быстро узнать, как добавить диаграмму, выделить сектор
  и отобразить проценты.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Вставка круговой диаграммы в Word – пошаговое руководство Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Вставка круговой диаграммы в Word с помощью Aspose.Words – полное руководство
url: /ru/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Вставка круговой диаграммы в Word с помощью Aspose.Words – Полное руководство

Когда‑нибудь вам нужно было **вставить круговую диаграмму** в отчет Word, но вы не знали, с чего начать? Вы не одиноки. Во многих бизнес‑приложениях визуальная сила круговой диаграммы делает данные мгновенно понятными, а Aspose.Words делает это возможным всего лишь несколькими строками кода.

В этом руководстве мы пошагово пройдем все действия, чтобы **добавить диаграмму в Word**, «взорвать» сегмент для акцента и отобразить проценты на подписи данных. К концу вы получите готовый к запуску пример, который можно вставить в любой проект .NET.

---

## Требования

Прежде чем начать, убедитесь, что у вас есть:

- .NET 6.0 или новее (код работает как с .NET Core, так и с .NET Framework)
- Установленный пакет NuGet Aspose.Words for .NET  
  ```bash
  dotnet add package Aspose.Words
  ```
- Базовое понимание синтаксиса C# — ничего сложного не требуется
- Любая IDE по вашему выбору (Visual Studio, Rider или VS Code)

Вот и всё. Приступим.

---

## Вставка круговой диаграммы в документ Word

Первое, что нам нужно, — это новый объект `Document` и `DocumentBuilder`. Думайте о `DocumentBuilder` как о ручке, которая пишет непосредственно на холсте Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Почему это важно:** `Document` представляет весь файл .docx, а `DocumentBuilder` предоставляет удобный API для вставки элементов, таких как диаграммы, таблицы и текст. Это фундамент для любой операции **как добавить диаграмму**.

---

## Как добавить диаграмму в Word

Теперь, когда у нас есть builder, мы действительно можем **вставить круговую диаграмму**. Метод `insertChart` принимает тип диаграммы и желаемые размеры в пунктах (1 пункт = 1/72 дюйма).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Подсказка:** Если нужен другой размер, просто измените значения ширины и высоты. Диаграмма автоматически масштабируется под поля страницы.

---

## Как «взорвать» сегмент для акцента

Распространённый визуальный приём — «взорвать» сегмент, чтобы он вышел за пределы круга. Это привлекает взгляд читателя к самому важному фрагменту.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Зачем «взорвать» сегмент?** Когда нужно выделить определённую категорию — например, «Выручка Q1» в финансовом отчёте — «взорванный» сегмент делает её мгновенно заметной без дополнительных пояснений.

---

## Как отобразить проценты на подписи данных

Большинство круговых диаграмм выглядит лучше, когда каждый сегмент показывает свой процент. Aspose.Words позволяет включить это одной настройкой.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Краткое замечание:** Флаг `ShowPercentage` работает для всех точек в серии, поэтому нет необходимости задавать его для каждого сегмента отдельно.

---

## Сохранение документа с диаграммой

Наконец, записываем документ на диск. Выберите любую папку; просто убедитесь, что путь существует.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Когда откроете `PieChart.docx` в Microsoft Word, вы увидите идеально отрисованную круговую диаграмму с первым «взорванным» сегментом и отображёнными процентами — именно то, что ожидается от отшлифованного бизнес‑отчёта.

---

## Полный рабочий пример

Ниже представлен полностью готовый к копированию и вставке код. Запустите его как консольное приложение и проверьте полученный файл.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Ожидаемый результат:** Откройте сгенерированный `PieChart.docx`. Вы увидите трёхсегментную круговую диаграмму с заголовком «Sales Q1», где первый сегмент вынут наружу, а каждый сегмент помечен «30 %», «45 %» и «25 %». Визуал соответствует поданным данным.

---

## Часто задаваемые вопросы и особые случаи

- **Что делать, если нужно более одной серии?**  
  Просто добавьте дополнительные объекты `ChartSeries` в `chart.Series`. У каждой серии может быть собственный набор данных, цвета и настройки «взрыва».

- **Можно ли изменить цвета диаграммы?**  
  Да. У каждого `ChartPoint` есть свойство `Format.Fill.ForeColor`, которое можно задать любым `System.Drawing.Color`.

- **А как насчёт других типов диаграмм?**  
  Перечисление `ChartType` включает столбчатые, линейные, кольцевые и многие другие типы. Замените `ChartType.Pie` на нужный вам тип.

- **Можно ли редактировать диаграмму в Word после вставки?**  
  Абсолютно. Word рассматривает диаграмму как нативную Office‑диаграмму, поэтому пользователь может двойным щелчком открыть встроенный редактор диаграмм.

---

## Заключение

Теперь вы точно знаете, как **вставить круговую диаграмму** в документ Word с помощью Aspose.Words, **как добавить диаграмму в Word**, **как «взорвать» сегмент** и **как отобразить проценты** на подписи данных. Полный пример выше готов к запуску, и вы можете расширять его пользовательскими данными, стилями или дополнительными сериями.

Готовы к следующему шагу? Попробуйте заменить круговую диаграмму на кольцевую, либо автоматически генерировать пакет отчётов с разными наборами данных. Если вам интересны другие визуализации, ознакомьтесь с нашими руководствами по **как добавить диаграмму** для столбчатых и линейных графиков, либо изучите справочник API **add chart to word** для более глубоких настроек.

Счастливого кодинга, и пусть ваши документы всегда будут так же ясны, как идеально разрезанный пирог!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом пособии. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в собственных проектах.

- [Вставка столбчатой диаграммы в Word с помощью Aspose.Words для .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Вставка областной диаграммы в документ Word | Aspose.Words для .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Создание точечной диаграммы Word с помощью Aspose.Words для .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}