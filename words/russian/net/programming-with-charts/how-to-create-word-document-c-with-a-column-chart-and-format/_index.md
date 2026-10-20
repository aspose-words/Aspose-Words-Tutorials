---
category: general
date: 2026-09-21
description: Узнайте, как создать документ Word на C#, вставить столбчатую диаграмму,
  задать положение подписи и отобразить значения с помощью Aspose.Words в пошаговом
  руководстве.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: ru
lastmod: 2026-09-21
og_description: Создайте документ Word на C# с помощью Aspose.Words. Этот учебник
  показывает, как вставить столбчатую диаграмму, установить положение меток и отобразить
  значения.
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: Создать документ Word на C# – вставить столбчатую диаграмму, задать подпись,
  отобразить значения
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: Как создать документ Word на C# со столбчатой диаграммой и отформатированными
  метками
url: /ru/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать Word документ C# с столбчатой диаграммой и отформатированными метками

Если вам нужно **create Word document C#**, включающий диаграмму, это руководство покажет, как это сделать. Вы узнаете, как вставить столбчатую диаграмму, разместить её подписи данных и отобразить значения подписи — всё с помощью Aspose.Words for .NET.

Раньше создание Word‑файла с диаграммой требовало ручной работы в Microsoft Word. С помощью шагов **how to insert chart**, описанных здесь, вы можете автоматизировать весь процесс из кода, делая генерацию отчетов быстрой и повторяемой. В руководстве также рассматриваются свойства **how to set label** и **how to display values**, чтобы диаграмма была готова к использованию конечными пользователями.

К концу этой статьи у вас будет полностью готовая, исполняемая программа на C#, создающая файл `.docx`, содержащий столбчатую диаграмму, у которой подписи данных находятся внутри каждого столбца и показывают их числовые значения.

## Предварительные требования

* .NET 6.0 SDK или более поздняя версия, установленная  
* Лицензионная копия **Aspose.Words for .NET** (бесплатная пробная версия подходит для тестирования)  
* IDE, например Visual Studio 2022 или Visual Studio Code  

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words`.

## Шаг 1: Настройте проект и добавьте Aspose.Words

Создайте новый консольный проект и добавьте пакет Aspose.Words:

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

Команда `dotnet add package` загружает последнюю стабильную версию **Aspose.Words**, которая включает API диаграмм, используемый в примере **insert column chart word**.

## Шаг 2: Создайте новый пустой Word документ

Первый фрагмент кода создает пустой документ и `DocumentBuilder`, позволяющий вставлять содержимое. Это основа для **create word document C#**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` представляет весь файл `.docx`, а `DocumentBuilder` предоставляет методы, такие как `InsertParagraph`, `InsertImage` и, что особенно важно для этого руководства, `InsertChart`.

## Шаг 3: Вставьте столбчатую диаграмму (how to insert chart)

Теперь мы вставляем **column chart**. Метод `InsertChart` принимает тип диаграммы, ширину и высоту в пунктах.

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

На данном этапе диаграмма содержит серию данных по умолчанию с заполнителями. Вы можете заменить данные серии, если нужны пользовательские числа, но для демонстрации **how to set label** и **how to display values** достаточно данных по умолчанию.

## Шаг 4: Разместите подписи данных внутри каждого столбца (how to set label)

Подписи данных — это текст, отображаемый на каждом столбце. Чтобы упростить чтение диаграммы, мы перемещаем подпись внутрь столбца и включаем её числовое значение.

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` размещает подпись в верхней части столбца, но всё ещё внутри формы столбца, что является распространённым визуальным стилем для отчётов. Установка `ShowValue` в `true` удовлетворяет требование **how to display values**.

## Шаг 5: Сохраните документ

Наконец, запишите документ на диск. Файл можно открыть в Microsoft Word, LibreOffice или любом просмотрщике, поддерживающем формат Open XML.

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Запуск программы создаёт `output.docx`, содержащий столбчатую диаграмму с подписями данных, расположенными внутри каждого столбца и отображающими их значения.

### Ожидаемый результат

При открытии `output.docx` вы должны увидеть одну столбчатую диаграмму, похожую на изображение ниже. Каждый столбец имеет числовую подпись в верхней части, внутри столбца, отображающую значение серии.

![Диаграмма в документе Word, созданном с помощью C#](/images/word-chart-example.png "Диаграмма в документе Word, созданном с помощью C# – create word document C#")

*Alt text:* *Диаграмма в документе Word, созданном с помощью C#, демонстрирующая, как вставить column chart word и отобразить значения.*

## Общие варианты и граничные случаи

### Добавление пользовательских данных в диаграмму

Если необходимо заменить данные‑заполнители, вы можете изменить коллекцию `Series` диаграммы:

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### Изменение шрифта и цвета подписи

Вы можете дополнительно настроить внешний вид подписи:

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### Вставка нескольких диаграмм

`DocumentBuilder` может вставлять столько диаграмм, сколько требуется. Просто вызовите `InsertChart` снова после перемещения курсора с помощью `builder.Writeln()` или `builder.InsertParagraph()`.

## Профессиональные советы

* **Pro tip:** Установите `chart.HasTitle = true` и задайте `chart.Title.Text`, чтобы добавить диаграмме описательный заголовок. Это улучшает доступность для программ чтения с экрана.
* **Watch out for:** При сохранении на сетевой ресурс убедитесь, что приложение имеет права записи; иначе `doc.Save` выбросит `UnauthorizedAccessException`.
* **Performance tip:** Переиспользуйте один экземпляр `DocumentBuilder` для нескольких вставок; создание нового билдера для каждой операции добавляет лишние накладные расходы.

## Заключение

Теперь вы знаете, как **create Word document C#**, содержащий столбчатую диаграмму, как **insert chart** элементы, **set label** позиции и **display values** внутри каждого столбца. Полный пример кода выше готов к запуску, и вы можете расширить его пользовательскими данными, стилями или дополнительными диаграммами.

Далее изучайте связанные темы, такие как **how to insert picture**, **how to generate tables** или **how to apply document themes**, чтобы сделать ваши автоматизированные отчёты ещё более насыщенными. Приятного кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, опирающиеся на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Вставить столбчатую диаграмму в Word с помощью Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Вставить простую столбчатую диаграмму в Word с помощью Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Вставить диаграмму областей в документ Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}