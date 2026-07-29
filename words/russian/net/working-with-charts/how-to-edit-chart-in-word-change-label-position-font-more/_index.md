---
category: general
date: 2026-07-29
description: Как редактировать диаграмму в документе Word — узнайте, как изменить
  положение подписи диаграммы, настроить подписи столбчатой диаграммы, изменить подписи
  данных диаграммы и изменить шрифт подписи диаграммы.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: ru
lastmod: 2026-07-29
og_description: Как быстро редактировать график в Word. Овладейте изменением положения
  подписи графика, настройкой подписей столбчатой диаграммы, изменением подписей данных
  графика и изменением шрифта подписи графика.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Как редактировать диаграмму в Word – изменить подписи и шрифт
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Как редактировать диаграмму в Word: изменить положение подписи, шрифт и другое'
url: /ru/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как редактировать диаграмму в Word: изменить позицию метки, шрифт и другое

Редактирование диаграммы в документе Word — распространённая задача, когда нужно, чтобы отчёты выглядели безупречно. Когда‑нибудь сталкивались с проблемой **change chart label position** или пытались сделать метки читаемыми, не копаясь в бесконечных меню? Вы не одни — большинство разработчиков сталкиваются с этим при автоматизации генерации отчётов. В этом руководстве мы пройдём через полностью готовый, исполняемый пример, который покажет, как **adjust bar chart labels**, **modify chart data labels** и **change chart label font** с помощью C# и библиотеки Aspose.Words.

## Что вы узнаете

- Загрузить файл .docx, уже содержащий столбчатую диаграмму.  
- Получить первую форму диаграммы и доступ к её коллекции меток данных.  
- **Change chart label position**, чтобы столбцы выглядели аккуратнее.  
- **Adjust bar chart labels** — изменить размер шрифта для лучшей читаемости.  
- Сохранить изменённый документ обратно на диск.  

Никаких внешних инструментов, никаких ручных действий в UI — только чистый код, который можно вставить в любой .NET‑проект. К концу вы получите автономное решение, которое можно переиспользовать в десятках документов.

> **Prerequisites**  
> - .NET 6.0 или новее (код также работает на .NET Framework 4.7+).  
> - Aspose.Words for .NET (доступен через NuGet).  
> - Файл Word (`BarChart.docx`), уже содержащий столбчатую диаграмму.  

Если чего‑то не хватает, скачайте последнюю версию пакета Aspose.Words сейчас:

```bash
dotnet add package Aspose.Words
```

---

## Как редактировать диаграмму: получение диаграммы из документа Word

Первый шаг в **how to edit chart** — загрузить документ и найти форму диаграммы. Aspose.Words рассматривает диаграммы как узлы `Shape`, поэтому мы можем использовать `GetChild` с `NodeType.Shape`, чтобы получить первую найденную диаграмму.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Why this matters:**  
> By directly accessing the `Chart` object, you avoid the overhead of opening the file in Word and manually adjusting each label. This is the cornerstone of any **modify chart data labels** automation.

## Adjust Bar Chart Labels: Change Chart Label Position

Теперь, когда у нас есть экземпляр `Chart`, пройдём по его `DataLabelCollection`. Цель — **change chart label position**, чтобы каждая метка удобно располагалась внутри основания своего столбца, а не парила над ним.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Pro tip:**  
> `InsideBase` works well for vertical bar charts. If you’re dealing with a horizontal bar chart, try `InsideEnd` instead. Experimenting with positions is cheap—just re‑run the code and open the saved document.

## Change Chart Label Font: Adjust Font Size for Readability

Крошечный шрифт — тихий убийца читаемости отчётов. Чтобы **change chart label font**, просто задайте свойство `Font.Size` у каждой `ChartDataLabel`. Мы увеличим его до 9 pt, что является оптимальным размером для большинства печатных отчётов.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Why we do this:**  
> Adjusting the font size is part of **modify chart data labels** best practices. Larger fonts improve accessibility and reduce the need for manual post‑processing.

## Save the Updated Document

После изменения позиций и шрифтов последний шаг в **how to edit chart** — сохранить изменения. Aspose.Words делает это в одну строку.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

Откройте `BarChartCustomLabels.docx` в Word, и вы увидите метки, аккуратно размещённые внутри столбцов, отрисованные чётким шрифтом 9 pt. Больше не придётся щуриться из‑за крошечных цифр.

---

## Полный рабочий пример (все шаги в одном файле)

Ниже представлен полностью готовый к запуску консольный проект, демонстрирующий весь процесс — от загрузки документа до сохранения обновлённой версии. Скопируйте‑вставьте его в новый .NET‑консольный проект и нажмите **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Expected output** when you run the program:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Откройте полученный файл, и вы увидите **adjust bar chart labels**, расположенные внутри столбцов с комфортным размером шрифта.

---

## Часто задаваемые вопросы и особые случаи

### Что делать, если в документе несколько диаграмм?

Приведённый код берёт *первая* диаграмма (`GetChild(NodeType.Shape, 0, true)`). Чтобы редактировать все диаграммы, замените одиночный вызов на цикл:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### Как **change chart label font** только для конкретного ряда?

У каждого `ChartSeries` есть собственная `DataLabelCollection`. Выберите ряд по индексу:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Работает ли это с круговыми или линейными диаграммами?

Да — `ChartDataLabelPosition` поддерживает значения вроде `InsideEnd`, `OutsideEnd` и `BestFit`. Для круговой диаграммы обычно предпочтительнее `OutsideEnd`, чтобы метки оставались читаемыми.

### Что насчёт локализации (например, разных десятичных разделителей)?

Aspose.Words учитывает региональные настройки документа. Если нужно принудительно задать определённый формат, измените `label.NumberFormat` перед сохранением.

---

## Итоги и дальнейшие шаги

Мы рассмотрели **how to edit chart** в документе Word от начала до конца: загрузка файла, получение диаграммы, **changing chart label position**, **adjusting bar chart labels**, **modifying chart data labels** и, наконец, **changing chart label font** перед сохранением. Полный пример готов к использованию в продакшене и может быть внедрён в любой конвейер автоматизации.

Готовы к следующему уровню? Подумайте о следующих улучшениях:

- **Add data label colors** (`dataLabel.Font.Color = Color.Blue;`).  
- **Show values as percentages** (`dataLabel.NumberFormat = "0%";`).  
- **Create charts programmatically** вместо загрузки готовых.

Все эти возможности используют тот же API, который мы применяли сегодня, так что вы будете чувствовать себя как дома.

Если возникли трудности, оставьте комментарий ниже или обратитесь к документации Aspose.Words для более глубоких настроек диаграмм. Приятного кодинга и красивых меток на диаграммах!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом пособии. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в своих проектах.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}