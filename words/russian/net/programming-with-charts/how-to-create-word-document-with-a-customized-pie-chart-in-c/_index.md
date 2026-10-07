---
category: general
date: 2026-10-07
description: Узнайте, как создать документ Word и вставить круговую диаграмму с помощью
  Aspose.Words в C#. Руководство также показывает, как сгенерировать файл Word с пользовательскими
  метками диаграммы.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: ru
lastmod: 2026-10-07
og_description: Создайте документ Word и вставьте круговую диаграмму на C#. Следуйте
  этому пошаговому руководству, чтобы создать файл Word с полностью настроенными метками
  диаграммы.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Создайте документ Word с настраиваемой круговой диаграммой на C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Как создать документ Word с настраиваемой круговой диаграммой на C#
url: /ru/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать документ Word с настраиваемой круговой диаграммой в C#

Если вам нужно **создать документ Word** программно, этот учебник покажет, как **вставить круговую диаграмму** и настроить её подписи данных с помощью Aspose.Words for .NET. Вы также узнаете, как **сгенерировать файл Word**, содержащий полностью стилизованную диаграмму, от настройки проекта до сохранения окончательного документа.

Руководство пошагово описывает каждый этап добавления диаграммы, настройки положения подписей, включения линий‑выноски и, наконец, сохранения результата в файл `.docx`. Не требуется никаких внешних инструментов, кроме библиотеки Aspose.Words, а полный исходный код предоставлен, чтобы вы могли скопировать, вставить и сразу запустить его.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 SDK или более поздняя версия  
* Действительная лицензия Aspose.Words for .NET (или бесплатный ключ оценки)  
* IDE, например Visual Studio 2022 или Visual Studio Code  

Вам также понадобится добавить в проект следующие пакеты NuGet:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Эти пакеты предоставляют классы `Document`, `DocumentBuilder` и связанные с диаграммами, используемые в примерах ниже.

## Создание документа Word и добавление диаграммы

Первый шаг — **создать документ Word** и получить `DocumentBuilder`, который позволяет вставлять содержимое. Builder работает как курсор, расположенный внутри документа.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Объект `Document` представляет весь файл Word, а `DocumentBuilder` предоставляет методы, такие как `InsertChart`, которые помещают объекты непосредственно в поток документа.

## Вставка круговой диаграммы в документ

Теперь, когда builder готов, вы можете **вставить круговую диаграмму** с заданным размером. Диаграмма добавляется в текущую позицию builder’а.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` возвращает объект `Chart`, которым можно дальше управлять. Пример данных создаёт четыре сектора, представляющих квартальные продажи.

## Настройка подписей данных круговой диаграммы

Чтобы диаграмма была более читаемой, часто требуется **настроить подписи** круговой диаграммы — разместить их за пределами секторов и показать линии‑выноски. Здесь в дело вступает `ChartDataLabelCollection`.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Установка `Position` в `OutsideEnd` перемещает каждую подпись за край сектора, а `ShowLeaderLines` рисует линию, соединяющую подпись с её сектором. Дополнительные флаги `ShowValue` и `ShowPercentage` позволяют отображать как абсолютные значения, так и относительные проценты.

**Совет:** Если нужно отформатировать шрифт подписи, используйте `dataLabels.Font` для задания размера, цвета и стиля. Это гарантирует соответствие диаграммы фирменному стилю.

## Сохранение и генерация файла Word

После полной настройки диаграммы вы можете **сгенерировать файл Word**, сохранив экземпляр `Document` на диск. Выберите формат `.docx` для максимальной совместимости с современными версиями Word.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Когда вы откроете `CustomPieChart.docx`, вы увидите круговую диаграмму из четырёх секторов, каждый из которых подписан за пределами сектора, соединён линией‑выноской и отображает как значение, так и процент.

![Снимок экрана документа Word, содержащего настраиваемую круговую диаграмму, созданную с помощью C#](image-placeholder.png)

*Изображение демонстрирует окончательный результат учебника **создания документа Word**.*

## Распространённые варианты и особые случаи

| Сценарий | Как адаптировать код |
|----------|----------------------|
| **Несколько рядов** | Добавьте дополнительные объекты `ChartSeries` в `pieChart.Series`. Каждый ряд может иметь собственную коллекцию `DataLabels` для независимого стилизования. |
| **Другой размер диаграммы** | Измените параметры ширины и высоты в `InsertChart(width, height)`. Значения указываются в пунктах (1 pt ≈ 1/72 in). |
| **Заголовок диаграммы** | Используйте `pieChart.Title.Text = "Quarterly Sales"` для добавления описательного заголовка. |
| **Экспорт в PDF** | Вызовите `document.Save("Report.pdf", SaveFormat.Pdf);` после построения диаграммы. |
| **Работа с лицензией** | Поместите файл лицензии (`Aspose.Words.lic`) в папку приложения и загрузите его с помощью `new License().SetLicense("Aspose.Words.lic");` перед созданием документа. |

Эти варианты позволяют ответить на вопрос **как добавить круговую диаграмму** в самых разных реальных сценариях, от простых отчётов до сложных панелей мониторинга.

## Заключение

Теперь вы знаете, как **создать документ Word**, **вставить круговую диаграмму** и **настроить подписи** диаграммы с помощью Aspose.Words for .NET. Полный пример демонстрирует чистый рабочий процесс: инициализация документа, добавление диаграммы, настройка положения подписей, включение линий‑выноски и, наконец, **генерацию файла Word**, которым можно делиться с кем угодно.

Попробуйте расширить этот учебник, экспериментируя с другими типами диаграмм (`ChartType.Column`, `ChartType.Line`) или применяя пользовательские цветовые палитры, соответствующие вашему бренду. Если возникнут проблемы, обратитесь к документации Aspose.Words или изучите связанные темы, такие как «как добавить круговую диаграмму» с несколькими рядами и динамическими источниками данных.

Удачной разработки, делитесь результатами или задавайте дополнительные вопросы в комментариях!

## Что изучать дальше?

Следующие учебники охватывают близкие темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}