---
category: general
date: 2026-09-21
description: Как отформатировать серии в линейной диаграмме Word с помощью C#. Узнайте,
  как создать документ Word, вставить линейную диаграмму и применить пользовательский
  числовой формат.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: ru
lastmod: 2026-09-21
og_description: Как форматировать серии в линейной диаграмме Word с помощью C#. Этот
  учебник покажет, как создать документ Word, вставить линейную диаграмму и применить
  пользовательский числовой формат.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Как форматировать серии в линейной диаграмме Word с помощью C# — пошаговое
  руководство
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Как форматировать серии в линейной диаграмме Word с помощью C#
url: /ru/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как отформатировать серии в линейной диаграмме Word с помощью C#

Если вам нужно **как отформатировать серии** в линейной диаграмме Word, это руководство предоставляет готовое решение, которое можно сразу запустить. Вы увидите, как **создать документ Word**, **вставить линейную диаграмму** и **применить пользовательский числовой формат** к значениям Y — все это с помощью Aspose.Words for .NET.

Автоматизация Word становится простой, как только вы поймёте модель объектов диаграмм. К концу этого урока у вас будет файл Word, содержащий линейную диаграмму, у которой серии данных отображаются в виде процентов с двумя знаками после запятой.

## Что вы получите

* Программно сгенерировать пустой файл `.docx`.  
* Добавить линейную диаграмму размером 400 × 300 точек.  
* Получить доступ к первой серии данных диаграммы.  
* Применить код формата `#,##0.00%`, чтобы значения Y отображались как проценты.  

Никакие внешние инструменты не требуются, кроме пакета Aspose.Words NuGet.

## Предварительные требования

* .NET 6.0 SDK или новее.  
* Visual Studio 2022 (или любой IDE для C#).  
* Aspose.Words for .NET 23.10 или новее — установите через `dotnet add package Aspose.Words`.  

Код работает на Windows, Linux и macOS, поскольку Aspose.Words не зависит от платформы.

## Создание документа Word с помощью Aspose.Words

Первый шаг — создать объект `Document`. Этот объект представляет весь файл Word в памяти.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Почему это важно*: `Document` — точка входа для всех операций обработки Word. Без него нельзя добавить абзацы, таблицы или диаграммы.

## Вставка линейной диаграммы в документ

`DocumentBuilder` записывает содержимое в `Document`. Вызов `InsertChart` создаёт форму диаграммы на текущей странице.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Почему это важно*: `InsertChart` возвращает объект `Chart`, который даёт полный контроль над сериями, осями и форматированием. Параметры размера задаются в точках (1 точка = 1/72 дюйма).

## Доступ к первой серии данных

Каждая диаграмма содержит одну или несколько `ChartSeries`. Первая серия имеет индекс 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Почему это важно*: Объект `ChartSeries` хранит значения Y, значения X и параметры форматирования для отдельной линии в линейной диаграмме. Изменение этого объекта меняет визуальное представление данных.

## Применение пользовательского числового формата к серии

Свойство `FormatCode` определяет, как отображаются числовые значения. Установив его в `#,##0.00%`, вы говорите Word отображать значения как проценты с двумя знаками после запятой.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Почему это важно*: Без пользовательского формата Word показывает сырые десятичные числа (например, `0.15`). Код формата преобразует их в `15.00%`, что часто требуется в бизнес‑отчётах.

## Сохранение документа и проверка результата

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Когда вы откроете `FormattedSeriesLineChart.docx` в Microsoft Word, вы увидите линейную диаграмму, где подписи оси Y выглядят как `15.00%`, `30.00%`, `45.00%` и `60.00%`. Размер диаграммы соответствует параметрам, переданным в `InsertChart`.

### Ожидаемый скриншот результата

> *Изображение: Страница документа Word, показывающая линейную диаграмму с процентно‑отформатированными значениями оси Y.*  
> *(Alt text: Скриншот документа Word, показывающий линейную диаграмму с процентно‑отформатированными значениями оси Y)*

## Распространённые варианты и граничные случаи

| Ситуация | Корректировка |
|-----------|------------|
| **Несколько серий** | Пройтись циклом по `chart.Series` и установить `FormatCode` для каждой серии. |
| **Другой тип диаграммы** | Заменить `ChartType.Line` на `ChartType.Column`, `ChartType.Pie` и т.д. |
| **Разделители, зависящие от локали** | Использовать строки формата, учитывающие `CultureInfo`, например `"# ##0,00 %"` для французской локали. |
| **Динамический источник данных** | Заполнить `series.YValues` данными из базы данных или CSV‑файла перед применением формата. |

**Совет:** Всегда применяйте формат **после** добавления значений Y. Применять формат сначала, а затем добавлять значения тоже возможно, но применение его позже гарантирует, что формат будет использован для окончательного набора данных.

## Итоги

Теперь вы знаете **как отформатировать серии** в линейной диаграмме Word с помощью C#. В этом руководстве рассмотрено:

* Создание документа Word (`create word document`).  
* Вставка линейной диаграммы (`insert line chart`, `add chart to word`).  
* Доступ к первой серии диаграммы.  
* Применение пользовательского числового формата (`apply custom number format`) для отображения процентов.

## Следующие шаги

* Поэкспериментировать с различными значениями `ChartType`, чтобы увидеть, как работают другие типы визуализаций.  
* Добавить заголовки, подписи осей и легенды с помощью `chart.Title`, `chart.AxisX.Title` и `chart.AxisY.Title`.  
* Экспортировать диаграмму как изображение (`chart.Save` с `SaveFormat.Png`) для использования в веб‑отчётах.

Не стесняйтесь адаптировать этот шаблон для создания дашбордов, финансовых отчётов или любых документов, требующих программного построения диаграмм. Приятного кодинга!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}