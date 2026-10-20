---
category: general
date: 2026-08-07
description: Быстро создайте круговую диаграмму в C#. Узнайте, как вставить круговую
  диаграмму, добавить подписи данных, отобразить процентные значения и настроить подписи
  диаграммы.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: ru
lastmod: 2026-08-07
og_description: Создайте круговую диаграмму в Word с помощью C# и Aspose.Words. В
  этом руководстве показано, как вставить круговую диаграмму, добавить подписи данных
  к ней и отобразить процентные значения, настроив подписи данных диаграммы.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Создание круговой диаграммы в C# – полный учебник
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Создание круговой диаграммы Word в C# — пошаговое руководство
url: /ru/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание круговой диаграммы в Word с помощью C# – пошаговое руководство

Если вам нужно **создать круговую диаграмму Word** в C#, это руководство предоставляет готовое решение, которое можно сразу запустить. Вы узнаете, как **вставить круговую диаграмму**, **добавить подписи данных к круговой диаграмме** и **отобразить процентные значения**, а также **настроить подписи данных диаграммы** для профессионального вида.

Программное создание диаграмм экономит время, избавляя от ручного редактирования, особенно когда отчёты или панели мониторинга должны генерироваться автоматически. В следующих разделах вы изучите всё, что необходимо для внедрения полностью подписанной круговой диаграммы в файл Word с помощью Aspose.Words for .NET.

## Предварительные требования и настройка

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 SDK или более поздняя версия.  
* Действительная лицензия Aspose.Words for .NET (или временный оценочный ключ).  
* Visual Studio 2022 (или любая IDE, поддерживающая C#).  

Добавьте пакет Aspose.Words NuGet в ваш проект:

```bash
dotnet add package Aspose.Words
```

> **Полезный совет:** Если планируете генерировать множество диаграмм, включите режим **Free‑Form Drawing** (`DocumentBuilder.UseFreeFormDrawing = true`) для повышения производительности.

## Создание круговой диаграммы Word с помощью Aspose.Words

Первый основной шаг – создать пустой документ Word и объект `DocumentBuilder`. Этот объект управляет всеми последующими вставками.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Почему это важно*: `Document` представляет весь файл `.docx`, а `DocumentBuilder` предоставляет удобный API для добавления абзацев, таблиц и диаграмм. Начало с чистого документа гарантирует отсутствие скрытого форматирования, которое могло бы помешать расположению диаграммы.

## Вставка круговой диаграммы в документ

Теперь разместим круговую диаграмму нужного размера. Метод `InsertChart` возвращает объект `Chart`, который мы можем дальше настраивать.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Почему это важно*: Флаг `ChartType.Pie` указывает Aspose.Words создать круглую диаграмму. Ширина (`400`) и высота (`300`) задаются в пунктах, что даёт точный контроль над визуальным размером.

## Заполнение диаграммы данными

Круговая диаграмма требует как минимум один ряд числовых значений. Здесь мы добавляем три категории: «Apples», «Bananas» и «Cherries».

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Почему это важно*: Каждый вызов `AddCategory` создаёт отдельный сектор. Числовое значение определяет размер сектора, а подпись становится названием категории, отображаемым при включённых подписьх данных.

## Добавление подписей данных к круговой диаграмме и отображение процентов

Чтобы диаграмма была информативной, включаем подписи данных, размещаем их за пределами секторов и просим Aspose.Words показывать как название категории, так и процент.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Почему это важно*: Установка `Position` в `OutsideEnd` улучшает читаемость, особенно когда сектора малы. Включение `ShowCategoryName` и `ShowPercentage` удовлетворяет требование **show percentage chart** и цель **add data labels pie**.

## Дополнительная настройка подписей диаграммы (необязательно)

Вы можете изменить шрифт, добавить линию‑выноску или скрыть легенду. Ниже показан фрагмент кода с типичными настройками:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Почему это важно*: Настройка внешнего вида подписи гарантирует, что диаграмма соответствует стилевому гиду вашего документа. Удаление легенды уменьшает визуальный шум, когда подписи уже передают всю необходимую информацию.

## Сохранение документа с настроенной диаграммой

Наконец, запишите документ на диск. Выберите путь, к которому у вас есть права записи.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

При открытии `ChartWithCustomLabels.docx` в Microsoft Word вы увидите круговую диаграмму, где каждый сектор подписан названием категории и процентом, подписи находятся снаружи сектора и оформлены пользовательским шрифтом.

### Ожидаемый результат

| Сектор   | Значение | Процент | Подпись в Word |
|----------|----------|---------|----------------|
| Apples   | 40       | 40 %    | Apples – 40 % |
| Bananas  | 35       | 35 %    | Bananas – 35 % |
| Cherries | 25       | 25 %    | Cherries – 25 % |

Диаграмма должна выглядеть примерно так:

![Word документ, отображающий круговую диаграмму с процентными подписями за каждым сектором](pie-chart-word.png "Пример создания круговой диаграммы Word")

*Текст alt‑изображения включает основной ключевой запрос для SEO.*

## Обработка нескольких рядов и граничных случаев

Базовый пример использует один ряд, что типично для круговой диаграммы. Если требуется отобразить несколько рядов (например, сравнение двух годов), необходимо:

1. Вызвать `chart.Series.Add()` для каждого дополнительного ряда.  
2. Убедиться, что каждый ряд использует одинаковые категории; иначе Aspose.Words выбросит `ArgumentException`.  
3. При желании установить `labels.ShowSeriesName = true` для различения секторов.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

При наличии нескольких рядов диаграмма автоматически отображается как **clustered pie** (также называемая «pie of pies»). Проверьте вывод, чтобы убедиться, что подписи остаются разборчивыми.

## Распространённые ошибки и способы их избежать

| Проблема | Причина | Решение |
|----------|---------|---------|
| Подписи перекрывают сектора | Маленькая область диаграммы или слишком много категорий | Увеличьте размеры диаграммы (`InsertChart(width, height)`) или переключите `Position` на `InsideEnd`. |
| Проценты не складываются до 100 % | Ошибки округления в данных | Используйте `labels.ShowPercentage = true` (Aspose.Words автоматически нормализует). |
| Диаграмма отображается пустой в Word | Отсутствие лицензии или истёк срок оценки | Убедитесь, что перед созданием документа загружена действительная лицензия Aspose.Words. |
| Цвета шрифтов отличаются от темы Word | Пользовательский шрифт, заданный в коде | Удалите пользовательские настройки шрифта или подберите цвета темы Word (`System.Drawing.Color.Black`). |

## Полный исходный код (готов к запуску)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Запуск программы создаёт `ChartWithCustomLabels.docx`, содержащий пример **create pie chart word**, удовлетворяющий всем требованиям, перечисленным в руководстве.

## Заключение

Теперь вы знаете, как **создавать круговую диаграмму Word** в C# с помощью Aspose.Words. Руководство охватывало вставку круговой диаграммы, **add data labels pie**, **show percentage chart** и **customize chart data labels** для получения профессионального, ориентированного на данные документа Word.  

Далее вы можете изучать связанные темы, такие как **insert pie chart** в существующие абзацы, генерировать **bar** или **line** диаграммы, а также автоматизировать пакетное создание отчётов с различными наборами данных. Экспериментируйте с позициями подписей, стилями шрифтов и конфигурациями нескольких рядов, чтобы адаптировать вывод под конкретные потребности отчётности.

Удачной работы с диаграммами!

## Что изучать дальше?

Следующие учебные материалы охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}