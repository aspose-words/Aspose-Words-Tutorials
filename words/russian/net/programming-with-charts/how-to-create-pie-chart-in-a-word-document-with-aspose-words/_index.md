---
category: general
date: 2026-09-21
description: «Узнайте, как создать круговую диаграмму и вставить её в Word с помощью
  Aspose.Words, добавить подписи данных к круговой диаграмме и отобразить проценты
  на диаграмме всего за несколько шагов».
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: ru
lastmod: 2026-09-21
og_description: Создайте круговую диаграмму в Word с помощью Aspose.Words, вставьте
  её в документ, добавьте подписи данных и отобразите проценты — всё с понятными примерами
  кода.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Создайте круговую диаграмму в Word с помощью Aspose.Words – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Как создать круговую диаграмму в документе Word с помощью Aspose.Words
url: /ru/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать круговую диаграмму в документе Word с помощью Aspose.Words

Если вам нужно **create pie chart** программно, Aspose.Words делает это простым. В этом руководстве вы увидите, как **insert chart into Word**, настроить серии, **add data labels to pie chart**, и наконец **show percentages on pie chart**, чтобы визуализация передавала точные значения. К концу у вас будет полностью готовый, исполняемый пример, который можно вставить в любой проект .NET.

Это руководство охватывает всё, что вам нужно знать: необходимые пакеты NuGet, полный исходный код C#, объяснения, почему каждый вызов API важен, и советы по настройке диаграммы. Внешняя документация не требуется — просто скопируйте, запустите и адаптируйте.

## Предварительные требования

* .NET 6.0 SDK или более поздняя версия установлен.
* Visual Studio 2022 (или любой IDE, поддерживающий .NET).
* Лицензия Aspose.Words for .NET (бесплатная пробная версия подходит для тестирования).
* Базовые знания C# и структуры документов Word.

Если у вас уже есть всё это, вы можете сразу перейти к коду.

## Шаг 1: Настройка проекта и импорт Aspose.Words

Создайте новый консольный проект и добавьте пакет Aspose.Words NuGet:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

Пакет включает пространство имён `Aspose.Words.Drawing.Charts`, которое содержит классы `Chart` и `ChartSeries`, которые мы будем использовать.

> **Pro tip:** Держите файл лицензии (`Aspose.Words.lic`) в корне проекта и загружайте его при запуске, чтобы избежать водяных знаков оценки.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Шаг 2: Создание пустого документа и DocumentBuilder

`Document` представляет файл Word, а `DocumentBuilder` предоставляет удобный API для вставки содержимого.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** `DocumentBuilder` сохраняет текущую точку вставки, гарантируя, что диаграмма появится точно там, где вы хотите в потоке документа.

## Шаг 3: Вставка круговой диаграммы в документ Word

Теперь мы **insert chart into Word**. Метод `InsertChart` принимает тип диаграммы, ширину и высоту (в пунктах).

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

На данном этапе диаграмма содержит серию данных по умолчанию с заполнителями (25, 25, 25, 25). При необходимости вы можете заменить их позже.

## Шаг 4: Доступ к первой серии и настройка подписей данных

Круговая диаграмма обычно имеет одну серию. Чтобы **add data labels to pie chart**, мы получаем её и включаем отображение процентов.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Why we set `ShowPercentage`:** Этот флаг указывает Aspose.Words вычислять долю каждого сектора и отображать её в виде процента. Свойство `Position` гарантирует, что подпись не будет перекрывать сектор, что повышает читаемость — особенно когда сектора малы.

## Шаг 5: (Опционально) Замена данных‑заполнителей

Если вам нужны конкретные значения, замените точки по умолчанию:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

Отображаемые проценты автоматически скорректируются в соответствии с новыми значениями.

## Шаг 6: Сохранение документа

Наконец, запишите документ на диск. Расширение определяет формат; `.docx` создаёт современный файл Word.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

Запуск программы создаёт файл с именем **PieChart.docx** в папке вывода. Открывая его в Microsoft Word, вы увидите круговую диаграмму, где каждый сектор помечен его процентом, расположенным за пределами секторов.

### Ожидаемый результат

When you open the generated document, you should see:

* Одна круговая диаграмма размером 400 × 300 pt.  
* Четыре сектора (или столько точек, сколько вы добавили).  
* Подписи‑проценты, такие как “40 %”, “30 %” и т.д., отображаемые за пределами каждого сектора.

Если подписи отображаются внутри секторов, дважды проверьте, что `ChartDataLabelPosition.OutsideEnd` установлен правильно.

## Шаг 7: Распространённые варианты и граничные случаи

### Добавление заголовка к диаграмме

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Изменение цветов секторов

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Обработка пустой серии

Если ваш источник данных может быть пустым, защититесь от `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Экспорт в PDF вместо Word

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

Та же логика отрисовки диаграммы применяется; Aspose.Words автоматически преобразует макет Word в PDF.

## Полный список исходного кода

Ниже представлен полный готовый к запуску пример программы. Скопируйте его в `Program.cs` и выполните `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Заключение

Теперь вы знаете, как **create pie chart** в файле Word с помощью Aspose.Words, **insert chart into Word**, **add data labels to pie chart** и **show percentages on pie chart**. Пример демонстрирует полный рабочий процесс — от настройки проекта до финального документа — чтобы вы могли адаптировать его для панелей мониторинга, отчётов или автоматической генерации счетов.  

Далее изучайте связанные темы, такие как **how to display percentages in chart** легендах, настройка цветов диаграммы или конвертация документа Word в PDF для распространения. Экспериментируйте с различными типами диаграмм (Bar, Line), используя тот же метод `InsertChart`, чтобы расширить возможности автоматизации.

Удачной работы с диаграммами!

## Что следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые опираются на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}