---
category: general
date: 2026-09-08
description: Создайте пустой документ Word и добавьте в него диаграмму с помощью Aspose.Words.
  Узнайте, как вставить радарную диаграмму, включить деления и сохранить файл.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: ru
lastmod: 2026-09-08
og_description: Создайте пустой документ Word и добавьте в него диаграмму с помощью
  Aspose.Words. В этом руководстве показано, как вставить радиальную диаграмму, настроить
  оси и сохранить документ.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Создайте пустой документ Word и добавьте диаграмму‑радар — пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Как создать пустой документ Word и добавить в него диаграмму
url: /ru/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать пустой документ Word и добавить в него диаграмму

Если вам нужно **создать пустой документ Word** для отчёта, шаблона или автоматического слияния писем, это руководство проведёт вас через весь процесс с использованием C# и Aspose.Words. Вы также узнаете, как **добавить диаграмму в Word**, в частности как **вставить радиальную диаграмму**, включить деления и сохранить результат в файл .docx.

В этом учебнике рассматривается всё: от настройки проекта до финального шага проверки. К концу вы получите переиспользуемый фрагмент кода, который можно вставить в любое .NET‑приложение. Предварительный опыт работы с Aspose.Words не требуется, но необходимо базовое знание C# и установленный недавний .NET SDK.

## Требования

- .NET 6.0 SDK или новее  
- Aspose.Words for .NET (NuGet‑пакет `Aspose.Words`)  
- IDE, например Visual Studio 2022 или VS Code  
- Права записи в папку, куда будет сохраняться документ  

Установить библиотеку можно следующей командой:

```bash
dotnet add package Aspose.Words
```

## Шаг 1: Создать пустой документ Word

Первый шаг — **создать пустой документ Word** в памяти. Класс `Document` представляет весь файл, а `DocumentBuilder` предоставляет удобный API для добавления содержимого.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` изначально пуст, поэтому у вас чистый холст для размещения диаграммы. Оставляя документ пустым на этом этапе, вы облегчаете повторное использование того же кода для разных шаблонов.

## Шаг 2: Добавить диаграмму в Word

Далее мы **добавляем диаграмму в Word**, вызывая `InsertChart`. Методу требуется тип диаграммы и желаемые размеры в пунктах (1 пункт = 1/72 дюйма).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` указывает Aspose.Words сгенерировать радиальную диаграмму, что идеально подходит для отображения многомерных данных в круговой раскладке. Значения размеров (400 × 300) хорошо подходят для большинства портретных страниц, но их можно изменить под ваш макет.

## Шаг 3: Вставить радиальную диаграмму и настроить деления

Теперь мы **вставляем радиальную диаграмму** и включаем деления (ticks) на осях категорий (X) и значений (Y). Деления повышают читаемость, показывая точные позиции каждой точки данных.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

Установка `HasGraduations` в `true` рисует метки делений на осях. Необязательный параметр `GraduationStep` управляет расстоянием между делениями на радиальной оси; шаг 10 означает деление каждые 10 градусов.

### Совет
Если нужно отобразить подписи данных, вызовите `radarChart.Series[0].HasDataLabel = true;`. Это добавит числовое значение рядом с каждой точкой, что удобно для презентаций.

## Шаг 4: Заполнить диаграмму образцовыми данными (по желанию)

Радиальная диаграмма без данных невидима. Ниже показан быстрый способ добавить серию образцовых значений. Вы можете заменить этот блок своим источником данных.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Каждый вызов `Add` вставляет точку в серию. Порядок точек соответствует угловым позициям вокруг круга.

## Шаг 5: Сохранить документ с диаграммой

Наконец, сохраняем документ на диск. Метод `Save` автоматически записывает файл .docx, сохраняя диаграмму и всё форматирование.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Запуск программы создаёт **пустой документ Word**, который теперь содержит полностью функционирующую радиальную диаграмму. Откройте файл в Microsoft Word, чтобы увидеть результат.

![Radar chart in Word document](radar_chart.png){alt="Радарная диаграмма, вставленная в пустой документ Word"}

## Общие варианты и граничные случаи

| Ситуация | Что изменить |
|-----------|----------------|
| **Другой размер диаграммы** | Отрегулируйте параметры ширины/высоты в `InsertChart`. |
| **Другие типы диаграмм** | Замените `ChartType.Radar` на `ChartType.Column`, `ChartType.Pie` и т.д., оставив ту же логику делений. |
| **Сохранение в поток** | Используйте `document.Save(Stream, SaveFormat.Docx)` |

## Что изучать дальше?


Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}