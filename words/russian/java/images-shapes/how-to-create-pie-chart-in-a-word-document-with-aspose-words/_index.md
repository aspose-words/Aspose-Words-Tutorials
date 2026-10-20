---
category: general
date: 2026-10-20
description: Создайте круговую диаграмму в документе Word с помощью Aspose.Words —
  пошаговое руководство, показывающее, как задать цвет, вырезать сектор и сохранить
  документ Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: ru
lastmod: 2026-10-20
og_description: Создайте круговую диаграмму в документе Word с помощью Aspose.Words.
  Узнайте, как задать цвет, выделить отдельный сектор и сохранить документ Word в
  одном исполняемом примере.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Создайте круговую диаграмму в документе Word – полное руководство по C#
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Как создать круговую диаграмму в документе Word с помощью Aspose.Words
url: /ru/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать круговую диаграмму в документе Word с помощью Aspose.Words

Если вам нужно **создать круговую диаграмму** внутри файла Word, это руководство покажет, как это сделать. Вы увидите, как задать пользовательский цвет, «взрыв» сектора для акцента и, наконец, **сохранить документ Word** с внедрённой диаграммой.

Программное создание диаграмм устраняет ручные шаги: открытие Word, вставка диаграммы и настройка её внешнего вида. К концу этого урока у вас будет полностью готовое консольное приложение C#, которое создаёт круговую диаграмму, настраивает её и сохраняет результат на диск.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 SDK или более поздняя версия  
* Действительная лицензия Aspose.Words for .NET (или бесплатный ключ оценки)  
* IDE, например Visual Studio 2022 или VS Code  

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words`.

## Как создать круговую диаграмму в документе Word

Первый шаг — создать экземпляры `Document` и `DocumentBuilder`. Builder предоставляет доступ к высокоуровневым функциям Word, включая вставку диаграмм.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

На данном этапе документ уже содержит базовую круговую диаграмму. В следующих разделах объясняется, **как «взрывать» сектор**, **как задать цвет** и **как сохранить документ Word**.

## Как «взрывать» сектор для акцента

«Взрыв» сектора отделяет его от остальной части круговой диаграммы, привлекая внимание читателя. API Aspose.Words позволяет указать расстояние взрыва в пунктах.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Зачем «взрывать» сектор? В отчётах, где выделяется определённая категория — например, «Топ‑продающийся продукт» — визуальное отделение делает точку данных мгновенно узнаваемой.

## Как задать цвет сектору диаграммы

Пользовательские цвета повышают согласованность бренда и читаемость. Вы можете назначить любой `System.Drawing.Color` конкретной точке данных.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Вы не ограничены предопределёнными цветами; можно создать значение `Color.FromArgb` для точных оттенков.

## Как сохранить документ Word с диаграммой

Как только диаграмма выглядит так, как вам нужно, её сохранение простое. Метод `Document.Save` записывает документ в указанный формат — здесь используется стандартный `.docx`.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Запуск программы создаёт `PieChart.docx`. Открытие файла в Microsoft Word показывает круговую диаграмму, где первый сектор «взрывается» и окрашен в красный цвет, точно как указано в коде.

### Ожидаемый результат

* Файл Word с именем **PieChart.docx** в `C:\Temp`.  
* Документ содержит одну круговую диаграмму размером 400 × 300 пунктов.  
* Сектор 0 смещён на 20 пунктов и заполнен красным, остальные сектора сохраняют цвет по умолчанию.  

Вы можете проверить взрыв и цвет, выбрав диаграмму в Word и изучив свойства сектора.

## Профессиональные советы и распространённые подводные камни

* **Совет:** Если нужно изменить заголовок диаграммы или легенду, используйте свойства `pieChart.Title.Text` и `pieChart.Legend` перед сохранением.  
* **Осторожно:** Если не очистить точки данных по умолчанию, могут появиться лишние, нежелательные сектора. Всегда вызывайте `Series[0].DataPoints.Clear()` перед добавлением своих данных.  
* **Подсказка по производительности:** Для больших документов переиспользуйте один экземпляр `DocumentBuilder` вместо создания множества билдера; это снижает нагрузку на память.

## Как создать диаграмму с помощью Aspose.Words (дополнительный контекст)

Метод `InsertChart` поддерживает множество типов диаграмм помимо круговых, таких как столбчатые, линейные и областные. Чтобы переключиться на другой тип, замените `ChartType.Pie` нужным значением перечисления, например `ChartType.Column`. Остальные шаги настройки (взрыв секторов, задание цветов) остаются теми же, хотя не все типы диаграмм поддерживают свойство «взрыв».

## Как «взрывать» сектор в других типах диаграмм

Только диаграммы типа «pie» предоставляют метод `SetExplosion`. Если попытаться вызвать его для гистограммы, API бросит `ArgumentException`. В таких случаях используйте подписи данных или выноски, чтобы выделить конкретный столбец.

## Как задать цвет серии вместо отдельного сектора

Если нужно, чтобы все сектора в серии имели один и тот же цвет, пройдитесь по точкам данных в цикле:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Этот подход удобен, когда требуется единая цветовая схема для нескольких диаграмм.

## Как сохранить документ Word в других форматах

Aspose.Words может экспортировать в PDF, HTML и многие другие форматы. Измените расширение файла в `Save` и при необходимости передайте объект `SaveOptions`:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

Механизм рендеринга диаграмм автоматически преобразует её в целевой формат, сохраняя цвета и настройки взрыва.

## Заключение

Теперь вы знаете, как **создать круговую диаграмму** в документе Word, настроить её внешний вид с помощью **взрыва сектора** и **задания цвета**, а также **сохранить документ Word** с внедрённой диаграммой. Этот сквозной пример даёт прочную основу для автоматизации генерации отчётов, панелей мониторинга или любой ситуации, где необходимо программно вставлять визуальные данные.

### Следующие шаги

* Изучите другие типы диаграмм (`ChartType.Column`, `ChartType.Line`), чтобы расширить набор инструментов отчётности.  
* Объедините несколько диаграмм в одном документе для создания комплексных панелей мониторинга.  
* Поэкспериментируйте с `ChartDataLabel`, чтобы отображать проценты или значения непосредственно на секторах.  

Не стесняйтесь адаптировать код под свои источники данных — будь то база данных, API или CSV‑файл, workflow Aspose.Words остаётся тем же. Приятного построения диаграмм!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}