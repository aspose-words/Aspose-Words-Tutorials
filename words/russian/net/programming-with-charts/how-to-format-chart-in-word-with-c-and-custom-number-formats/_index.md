---
category: general
date: 2026-10-13
description: Как форматировать диаграмму в Word с помощью C#, применяя пользовательский
  числовой формат, например валюту, к осям диаграммы. Пошаговый пример кода включён.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: ru
lastmod: 2026-10-13
og_description: Как форматировать диаграмму в Word с помощью C# позволяет применить
  пользовательский числовой формат к осям диаграммы, обеспечивая отображение значений
  в виде валюты, процентов или любого другого требуемого шаблона. Следуйте пошаговому
  руководству.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Как отформатировать диаграмму в Word с помощью C# – пользовательские числовые
  форматы
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Как форматировать диаграмму в Word с помощью C# и пользовательских числовых
  форматов
url: /ru/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как отформатировать диаграмму в Word с помощью C# и пользовательских числовых форматов

Форматирование диаграммы в Word с помощью C# — распространённая задача, когда нужно представить данные профессионально. В этом руководстве показано, как применить пользовательский числовой формат к оси диаграммы, используя **Aspose.Words for .NET**, чтобы значения отображались точно так, как вы ожидаете.

Вы узнаете, как загрузить файл DOCX, найти первую диаграмму, прочитать текущий формат и затем задать новый шаблон, например, валютный с двумя знаками после запятой. В руководстве также рассматривается, как изменить формат оси диаграммы для дополнительных рядов и как сбросить формат при необходимости.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 или более поздняя версия  
* Проект Visual Studio 2022 (или любой IDE, поддерживающий .NET)  
* Пакет NuGet **Aspose.Words for .NET** (`Aspose.Words`)  
* Документ Word (`input.docx`), содержащий как минимум одну диаграмму

Пакет можно добавить с помощью следующей команды:

```bash
dotnet add package Aspose.Words
```

## Как отформатировать диаграмму в Word с помощью Aspose.Words

Ниже приведена полная программа, демонстрирующая каждый шаг, необходимый для **форматирования значений оси диаграммы**. Сохраните файл как `Program.cs` и запустите его из командной строки или вашей IDE.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Пояснение каждого шага

| Шаг | Почему это важно | Ключевой код |
|------|-------------------|--------------|
| **Load the document** | Вам нужен объект `Document` для работы с файлом Word. | `new Document("input.docx")` |
| **Retrieve the chart** | Объекты `Chart` хранятся как узлы `Shape`; приведение типа позволяет использовать API, специфичные для диаграмм. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Access X‑values** | Форматирование оси применяется к коллекции значений ряда данных. | `chart.ChartData.Series[0].XValues` |
| **Read current format** | Знание текущего `FormatCode` помогает решить, заменять его или дополнять. | `xValues.FormatCode` |
| **Set custom format** | Свойство `FormatCode` принимает любой шаблон, совместимый с Excel, позволяя использовать валюту, проценты, даты и т.д. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Save the document** | Сохранение изменений записывает новый формат оси обратно в файл DOCX. | `doc.Save("output_formatted.docx")` |

Запуск программы создаёт `output_formatted.docx`. Откройте его в Word, и вы увидите, что значения оси X отображаются как **$1,234.00**, **$2,345.00**, … вместо простых чисел.

## Применить пользовательский числовой формат к оси диаграммы

Если нужно **применить пользовательский числовой формат** к оси Y или к дополнительным рядам, процесс идентичен — просто обратитесь к другой коллекции:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Совет:** Используйте двойные кавычки внутри строкового формата, чтобы вставить буквальные символы (например, `"$"` для валюты). Экранируйте кавычки, как показано выше.

## Пользовательский числовой формат в Word — учёт локали документа

Word учитывает локаль документа при интерпретации числовых форматов. Если документ использует не‑американскую локаль, возможно, потребуется скорректировать строку формата:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Тестирование формата в документе с немецкими настройками языка подтверждает, что значения отображаются как **€ 1.234,00**.

## Как программно задавать свойства диаграммы

Помимо форматирования осей, часто требуется **задать свойства диаграммы**: заголовки, легенды или подписи данных. Ниже короткий фрагмент, демонстрирующий установку заголовка диаграммы после форматирования оси:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Комбинация этого с пользовательским числовым форматом даёт полностью отполированную диаграмму, готовую к отчётности.

## Динамическое изменение формата оси диаграммы в зависимости от ввода пользователя

В реальных приложениях пользователи могут выбирать формат во время выполнения. Следующий метод инкапсулирует логику форматирования:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

Вы можете вызвать `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` для валюты или `SetAxisFormat(chart, 0, "0%")` для процентов. Такой подход сохраняет основной код чистым и поддерживает будущие расширения.

## Пограничные случаи и распространённые подводные камни

| Ситуация | На что обратить внимание | Предлагаемое решение |
|-----------|--------------------------|----------------------|
| Документ **не содержит диаграмм** | `GetChild` возвращает `null`, что приводит к исключению приведения типа. | Проверяйте `null` перед приведением (см. пример). |
| В документе несколько диаграмм | Код всегда берёт первую диаграмму (`index 0`). | Проходите в цикле `doc.GetChildNodes(NodeType.Shape, true)` и фильтруйте по `ShapeType.Chart`. |
| Ряды **без X‑значений** (например, круговые диаграммы) | Доступ к `XValues` может вызвать `ArgumentOutOfRangeException`. | Убедитесь, что `Series[i].XValues` не пустой перед форматированием. |
| Несоответствие локали | Символ валюты может отображаться неверно. | Явно задавайте `xValues.FormatCode` с нужными символами локали. |

## Ожидаемый результат

После выполнения примера откройте **output_formatted.docx**. Ось X диаграммы должна показывать числа в выбранном пользовательском формате. Для примера с валютой подписи оси выглядят так:

```
$1,000.00
$2,000.00
$3,000.00
```

Если вы применили процентный формат к значениям Y, подписи оси Y будут выглядеть так:

```
10%
20%
30%
```

## Заключение

В этом руководстве показано, **как отформатировать диаграмму** в Word с помощью C#, **применяя пользовательский числовой формат** к значениям осей. Теперь у вас есть переиспользуемый шаблон для установки валюты, процентов или любого другого числового шаблона, а также рекомендации по работе с локалями, несколькими рядами и динамическим вводом пользователя.

Далее вы можете изучить **как задавать заголовки диаграмм**, подписи данных или даже экспортировать диаграмму как изображение с помощью `ChartRenderer`. Эти темы напрямую опираются на рассмотренные здесь концепции и помогут создать полностью автоматизированные решения для отчётности.

---


## Что вам следует изучить дальше?


Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы реализации в ваших проектах.

- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Format Secondary X‑Axis and Set Display Units to Thousands in Word Line Charts Using Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}