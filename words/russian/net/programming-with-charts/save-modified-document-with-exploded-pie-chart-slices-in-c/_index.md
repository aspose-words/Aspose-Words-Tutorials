---
category: general
date: 2026-10-13
description: 'Сохранить изменённый документ после настройки круговой диаграммы: разъединить
  сектора, изменить угол первого сектора и отобразить подписи с процентами в C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: ru
lastmod: 2026-10-13
og_description: Сохраните изменённый документ после настройки круговой диаграммы в
  C#. Узнайте, как «взрывать» сектора диаграммы, менять угол первого сектора и отображать
  подписи с процентами.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Сохранить изменённый документ с вырезанными секторами круговой диаграммы –
  руководство по C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Сохранить изменённый документ с разнесёнными секторами круговой диаграммы в
  C#
url: /ru/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохранить изменённый документ с взорванными кусочками круговой диаграммы в C#

Если вам нужно **save modified document** после настройки круговой диаграммы Word, это руководство покажет, как именно. Вы узнаете, как взорвать кусочки круговой диаграммы, изменить угол первого куска и отобразить подписи процентов — всё это с помощью нескольких строк кода на C#.

Настройка диаграмм — распространённое требование при программной генерации отчётов, счетов или панелей мониторинга. К концу этого руководства вы сможете загрузить файл DOCX, изменить внешний вид диаграммы и **save modified document**, готовый к распространению.

## Предварительные требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.6+)
- Aspose.Words for .NET 23.10 или новее (бесплатная пробная версия или лицензированная копия)
- Файл Word (`input.docx`), содержащий одну круговую диаграмму
- Visual Studio 2022 или любой IDE для C#

> **Подсказка:** Пакет NuGet Aspose.Words добавляется с помощью `dotnet add package Aspose.Words`.

## Шаг 1: Загрузить документ Word, содержащий диаграмму

Первый шаг — открыть исходный файл DOCX. Класс `Document` представляет весь файл Word в памяти.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

Загрузка документа предоставляет полный доступ ко всем узлам, включая формы, содержащие диаграммы.

## Шаг 2: Получить первую форму с диаграммой из документа

Диаграммы хранятся внутри узлов `Shape`. Вы можете найти первую диаграмму с помощью `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Если документ содержит несколько диаграмм, скорректируйте индекс (`0`) или пройдитесь по коллекции. Эта строка гарантирует, что у вас есть ссылка на объект `Chart`, который вы будете изменять.

## Шаг 3: Взорвать кусочки круговой диаграммы

Взрыв куска отделяет его от остальных частей круговой диаграммы, делая её более читаемой. Свойство `Explode` применяется ко всей серии.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Установка `Explode` в `true` **explodes pie chart slices** для всей серии, что полезно, когда нужно, чтобы каждый кусок выделялся.

## Шаг 4: Изменить угол первого куска

Иногда требуется, чтобы первый кусок начинался под пользовательским углом, например, чтобы соответствовать дизайнерскому руководству.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

Свойство `FirstSliceAngle` **changes first slice** ориентацию, вращая весь круг так, чтобы первый кусок начинался под углом 30 градусов.

## Шаг 5: Показать процентные подписи на кусочках диаграммы

Отображение числового вклада каждого куска часто требуется в отчетах. Флаг `DataLabel.ShowPercentage` включает процентные значения.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Этот шаг **show percentage labels** непосредственно на диаграмме, что также удовлетворяет требованию **display percentages pie**.

## Шаг 6: Сохранить изменённый документ

После применения всех настроек сохраните изменения в новый файл. Метод `Save` записывает обновлённый DOCX на диск.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Теперь у вас есть **save modified document**, содержащий взорванную круговую диаграмму, повернутый первый кусок и видимые процентные подписи.

![Сохранённый изменённый документ, показывающий взорванные кусочки круговой диаграммы](/images/pie-chart-exploded.png "Сохранённый изменённый документ с взорванными кусочками круговой диаграммы и процентными подписями")

*Скриншот иллюстрирует конечный результат после сохранения документа.*

## Полный, исполняемый пример

Объединив все части, представляем полный код программы, который можно скопировать и вставить в консольный проект:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Ожидаемый результат

Открытие `output.docx` покажет круговую диаграмму, где:

- Каждый кусок слегка отделён (**exploded pie chart slices**)
- Первый кусок начинается со смещения в 30 градусов (**change first slice**)
- Каждый кусок показывает свой вклад в процентах (**show percentage labels**, **display percentages pie**)
- Файл был **save modified document** без изменения оригинала.

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| **Что если в документе нет диаграммы?** | Код проверяет `null` после `GetChild`. Если диаграмма отсутствует, вы можете либо добавить её программно, либо прервать выполнение с чётким сообщением. |
| **Можно ли взорвать только один кусок?** | Да. Используйте `chart.PieChart.Series[0].DataPoints[i].Explosion = true;`, где `i` — индекс куска. |
| **Как изменить формат подписи (например, показать значение + %)?** | Установите `chart.PieChart.DataLabel.ShowValue = true;` и при необходимости `chart.PieChart.DataLabel.ShowPercentage = true;`, чтобы объединить оба. |
| **Сохраняется ли стиль диаграммы после сохранения?** | Aspose.Words сохраняет всю стилизацию, включая цвета и шрифты, когда вы **save modified document**. |
| **Можно ли обработать несколько диаграмм в одном файле?** | Пройдитесь по всем узлам `Shape` с помощью `NodeType.Shape` и отфильтруйте их по `shape.HasChart`. Примените те же шаги к каждой диаграмме. |

## Заключение

Теперь вы знаете, как **save modified document** после программного изменения круговой диаграммы в Word. Руководство охватывало взрыв кусочков диаграммы, изменение угла первого куска и отображение процентных подписей — удовлетворяя требования **show percentage labels**, **explode pie chart slices**, **display percentages pie** и **change first slice**.

Далее рассмотрите изучение:

- Добавление серий данных динамически (`chart.Series.Add(...)`)  
- Настройка размещения легенды и заголовков диаграмм  
- Конвертация DOCX в PDF с сохранением стилей диаграммы  

Не стесняйтесь экспериментировать с различными углами, настройками взрыва или форматами подписей, чтобы соответствовать вашим требованиям к отчетности. Приятного кодинга!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как сохранить отредактированный документ в C# с Aspose.Words – пошаговое руководство](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Обновление данных серии диаграммы в документе Word с помощью Aspose.Words для .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Вставка столбчатой диаграммы в документ Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}