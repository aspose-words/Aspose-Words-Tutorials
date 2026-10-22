---
category: general
date: 2026-10-13
description: Узнайте, как программно настраивать подписи к диаграммам в документе
  Word с помощью C#. Это руководство охватывает работу с диаграммами Aspose.Words
  и выравнивание подписей.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: ru
lastmod: 2026-10-13
og_description: Программно регулируйте подписи диаграмм в документе Word с помощью
  C#. Следуйте этому полному руководству, чтобы изменить размещение подписи, выравнивание
  и многое другое.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Программно корректировать подписи диаграмм в Word – пошаговое руководство
  по C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Программно изменять подписи диаграмм в документе Word с помощью C#
url: /ru/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Программная настройка подписей диаграмм в документе Word с помощью C#

Если вам нужно **программно настроить подписи диаграмм** в документе Word, это руководство покажет, как сделать это на C#. Независимо от того, генерируете ли вы отчёты, автоматизируете панели мониторинга или настраиваете шаблоны, вы увидите полностью рабочий пример, который изменяет расположение и выравнивание подписей диаграммы внутри файла .docx.

Вы также узнаете, как использовать **Aspose.Words chart manipulation**, работать с несколькими сериями и избегать распространённых ошибок при работе с объектами **C# chart data label**.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 (или новее) установлен  
* Visual Studio 2022 (или любая IDE для C#)  
* NuGet‑пакет **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
* Документ Word (`input.docx`), содержащий хотя бы одну диаграмму  

Эти элементы необходимы для **Word document chart example**, который мы будем модифицировать.

## Шаг 1: Создание проекта и импорт пространств имён

Создайте новый консольный проект и добавьте необходимые директивы `using`. Это подготовит окружение для **programmatically adjust chart labels**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Зачем этот шаг?*  
Загрузка документа даёт доступ к внутреннему дереву **Word document chart example**, где диаграммы хранятся как узлы‑формы.

## Шаг 2: Поиск первой формы диаграммы

Диаграммы хранятся как узлы `Shape`. Следующий код получает первую диаграмму в документе, которую мы будем настраивать.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Зачем этот шаг?*  
Метод `GetChild` рекурсивно ищет (`true`) и возвращает первый узел типа `Shape`. Приведение к `Chart` позволяет работать с API, специфичным для диаграмм.

## Шаг 3: Доступ к подписи данных, которую нужно изменить

Каждая серия в диаграмме имеет коллекцию подписей данных. Для простой диаграммы часто достаточно первой подписи. Ниже показано, как к ней обратиться.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Зачем этот шаг?*  
`ChartSeries` представляет серию точек. `DataLabelCollection` содержит подписи для этой серии, позволяя точно управлять их расположением и выравниванием.

## Шаг 4: Изменение расположения и выравнивания подписи

Теперь мы **programmatically adjust chart labels**, задав позицию, горизонтальное и вертикальное выравнивание. Эти свойства соответствуют параметрам, которые вы видите в пользовательском интерфейсе Word.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Зачем такие настройки?*  

* `OutsideEnd` размещает подпись сразу за концом каждой полосы или столбца, улучшая читаемость.  
* `HorizontalAlignment.Center` центрирует текст над точкой, а `VerticalAlignment.Top` выравнивает верхний край подписи с точкой данных, предотвращая перекрытие с другими элементами.

### Совет профессионала
Если в диаграмме несколько серий, пройдитесь циклом по `chart.Series` и примените те же настройки к каждой `DataLabelCollection`. Это обеспечит единообразный вид всей диаграммы.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Шаг 5: Сохранение изменённого документа

После настройки подписей сохраните изменения в новый файл. Это завершает процесс **modify chart label position**.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Когда откроете `output.docx`, вы увидите, что каждая подпись диаграммы перемещена к внешнему концу её точки, центрирована по горизонтали и выровнена по верхнему краю вертикально.

## Особые случаи и варианты

| Ситуация | На что обратить внимание | Рекомендуемый подход |
|-----------|--------------------------|----------------------|
| **Несколько диаграмм** в одном документе | `GetChild` возвращает только первую диаграмму. | Использовать `doc.GetChildNodes(NodeType.Shape, true)` для перебора всех форм‑диаграмм. |
| **Серии без подписей данных** | `DataLabelCollection` может быть пустой. | Проверять `series.HasDataLabels` перед доступом к коллекции. |
| **Разные типы диаграмм** (pie, line, scatter) | Не все значения `DataLabelPosition` допустимы. | Использовать `DataLabelPosition.Auto` для диаграмм, которые автоматически выбирают оптимальное расположение. |
| **Локализация** | Константы выравнивания не зависят от языка, но отображаемый текст может требовать поддержки справа‑налево. | Установить `dataLabel.TextDirection`, если нужны RTL‑языки. |

## Полный, готовый к запуску пример

Ниже представлен полный код программы, который можно скопировать, вставить и запустить. Замените `YOUR_DIRECTORY` на реальный путь к папке.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Ожидаемый результат:** При открытии `output.docx` каждая подпись диаграммы будет расположена за точкой данных, центрирована по горизонтали и выровнена по верхнему краю — именно тот эффект **programmatically adjust chart labels**, который вы запрограммировали.

## Заключение

Теперь вы знаете, как **programmatically adjust chart labels** в документе Word с помощью C#. В этом руководстве мы рассмотрели:

* Загрузку документа с помощью **Aspose.Words chart manipulation**  
* Доступ к **C# chart data label**  
* Изменение **modify chart label position** и выравнивания  
* Сохранение файла и обработку распространённых особых случаев  

Далее вы можете изучать более продвинутые сценарии, такие как настройка шрифтов подписей, добавление условного форматирования или массовое обновление нескольких диаграмм. Поэкспериментируйте с различными вариантами `DataLabelPosition`, чтобы подобрать стиль, который лучше всего подходит вашим отчётам.

---

*Готовы улучшить ваш автоматизированный конвейер отчётности? Попробуйте добавить пользовательские числовые форматы к подписям или экспортировать диаграмму как изображение для использования в PDF.*


## Что изучать дальше?


Следующие учебные материалы охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}