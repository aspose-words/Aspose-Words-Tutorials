---
category: general
date: 2026-08-04
description: Настройка размещения подписей данных для диаграмм в C# позволяет центрировать
  подписи на сегментах диаграммы. Следуйте этому пошаговому руководству, используя
  API диаграмм Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: ru
lastmod: 2026-08-04
og_description: Пользовательское размещение подписей данных для диаграмм в C# показывает,
  как центрировать все подписи данных на каждом сегменте диаграммы Word. Овладейте
  позиционированием подписей данных диаграмм с помощью Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Настройка размещения подписей данных на диаграммах в C# – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Пользовательское размещение подписей данных для диаграмм в C#
url: /ru/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Пользовательское размещение меток данных для диаграмм в C#

**Custom Data‑Label Placement for Charts** позволяет точно контролировать, где появляется каждая метка на диаграмме в документе Word. В этом руководстве вы узнаете, как центрировать все метки данных на каждом сегменте, используя C# и API диаграмм Aspose.Words.

Вы получите полностью готовый пример, который загружает файл `.docx`, получает доступ к первой форме диаграммы, меняет `Position` каждой метки на `Center` и сохраняет обновлённый документ. Внешние ссылки не требуются — только библиотека Aspose.Words для .NET и базовая среда разработки C#.

**Что вы узнаете**

* Как загрузить документ Word, содержащий диаграмму.  
* Как найти форму диаграммы с помощью API диаграмм Aspose.Words.  
* Как применить **позиционирование меток данных диаграммы** к каждому ряду в диаграмме.  
* Как сохранить документ, чтобы центрированные метки отображались в Word.  

**Требования**

* .NET 6.0 (или новее) установлен.  
* Visual Studio 2022 (или любая IDE для C#).  
* Ссылка на пакет NuGet `Aspose.Words`.  
* Файл Word (`Chart.docx`), содержащий хотя бы одну диаграмму.

---

## Пользовательское размещение меток данных для диаграмм – шаг 1: загрузка документа

Первое действие — открыть файл Word, содержащий диаграмму. `Document` является точкой входа для любой манипуляции с Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Почему этот шаг важен*: без загрузки документа вы не сможете получить доступ к объекту диаграммы. Проверка гарантирует получение понятной ошибки, если в файле нет диаграммы, предотвращая ошибку null‑reference позже.

---

## Использование API диаграмм Aspose.Words для доступа к формам диаграмм

Aspose.Words рассматривает диаграмму как объект `Chart`, вложенный в `Shape`. Вы получаете его, приводя соответствующий дочерний узел.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Почему этот шаг важен*: прямой доступ к `Chart` дает полный контроль над рядами, точками данных и свойствами меток. Если форма не является диаграммой, код завершится раннее с информативным сообщением.

---

## Установка позиционирования меток данных диаграммы в C#

Теперь пройдите по каждому ряду и каждой метке данных, устанавливая `Position` в `Center`. Это ядро **Custom Data‑Label Placement for Charts**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Совет**: если вам требуется другое размещение (например, `InsideEnd` для столбчатой диаграммы), измените значение перечисления соответственно. Перечисление `ChartDataLabelPosition` охватывает все стандартные позиции, поддерживаемые Word.

*Почему этот шаг важен*: изменение `label.Position` обновляет базовое представление OOXML, поэтому метка будет отображаться по центру при открытии документа в Microsoft Word.

---

## Сохранение документа Word с обновлёнными метками

После изменения диаграммы сохраните изменения в файл. Вы можете перезаписать оригинал или создать новую копию.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Почему этот шаг важен*: сохранение записывает обновлённый OOXML на диск. Открытие `ChartLabelsCentered.docx` в Word покажет каждую метку сегмента центрированной, подтверждая успешность **Custom Data‑Label Placement for Charts**.

---

## Пограничные случаи и варианты

| Ситуация | Как решить |
|-----------|---------------|
| **Несколько диаграмм** в одном документе | Выполните цикл по `doc.GetChildNodes(NodeType.Shape, true)` и проверьте `shape.HasChart` для каждой формы. |
| **Разные типы диаграмм** (pie, doughnut, bar) | То же `ChartDataLabelPosition.Center` работает для круговых диаграмм. Для столбчатых/барных диаграмм может подойти `InsideEnd` или `OutsideEnd`. |
| **Текст метки требует форматирования** | Обратитесь к `label.TextProperties`, чтобы задать размер шрифта, цвет или полужирность. |
| **Запуск на .NET Core** | Убедитесь, что вы ссылаетесь на версию Aspose.Words для .NET Standard; API идентичен. |

---

## Полный рабочий пример

Ниже приведена полная программа, которую можно скопировать и вставить в консольное приложение. Она включает все необходимые директивы `using` и обработку ошибок.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Ожидаемый результат**: откройте `ChartLabelsCentered.docx` в Microsoft Word. Каждый сегмент диаграммы теперь отображает свою метку данных непосредственно в центре сегмента, обеспечивая более чистый визуальный вид.

---

## Заключение

Теперь у вас есть полное решение **Custom Data‑Label Placement for Charts** на C#. Загрузив документ, получив доступ к диаграмме через API диаграмм Aspose.Words, установив `ChartDataLabelPosition.Center` для каждой метки и сохранив файл, вы можете автоматизировать позиционирование меток для любой диаграммы в Word.

Далее изучайте другие варианты **позиционирования меток данных диаграммы**, такие как `InsideEnd` или `OutsideEnd`, или экспериментируйте с **манипуляцией диаграммами в C#**, меняя цвета, добавляя легенды или создавая диаграммы с нуля. Эти расширения опираются непосредственно на рассмотренные здесь техники и расширяют ваши навыки автоматизации диаграмм в документах Word. Приятного кодинга!

## Что следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Настройка меток данных диаграммы](/words/english/net/programming-with-charts/chart-data-label/)
- [Форматирование числа метки данных в диаграмме](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Метка данных диаграммы](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}