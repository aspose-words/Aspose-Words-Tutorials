---
category: general
date: 2026-10-13
description: Пример радиальной диаграммы Aspose.Words, показывающий, как включить
  деления на радиальной диаграмме с использованием C# и Aspose.Words 24.9+.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: ru
lastmod: 2026-10-13
og_description: Пример радиальной диаграммы Aspose.Words, демонстрирующий включение
  делений на радиальной диаграмме с использованием C# и последней библиотеки версии 24.9+.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Пример радиальной диаграммы Aspose.Words – включить градации в C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Пример радиальной диаграммы Aspose.Words: включить деления в C#'
url: /ru/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Пример радиальной диаграммы Aspose.Words: включение делений в C#

Если вы ищете **aspose.words radial chart example**, вы попали в нужное место. Этот учебник проведет вас через точные шаги включения делений для радиальной диаграммы с использованием API Aspose.Words для .NET.

Радиальные диаграммы полезны для визуализации циклических данных, таких как метрики времени суток или сезонные тенденции. По умолчанию деления (метки вокруг круговой оси) скрыты, что может затруднить чтение диаграммы. Включить их можно одной строкой, но необходимо знать правильную объектную модель и версию, поддерживающую эту функцию.

В этом руководстве вы узнаете, как:

* Загрузить документ Word, который уже содержит радиальную диаграмму.  
* Получить доступ к фигуре диаграммы через API Aspose.Words chart.  
* Включить **graduations visibility** (доступно начиная с **Aspose.Words version 24.9**).  
* Сохранить изменённый документ и проверить результат.

Полный, исполняемый код включён, так что вы можете скопировать‑вставить его в новый консольный проект и сразу увидеть результат.

![Пример радиальной диаграммы Aspose.Words с делениями](https://example.com/images/radial-chart-graduations.png "Пример радиальной диаграммы Aspose.Words, показывающий включённые деления")

## Требования

Before you start, make sure you have:

| Требование | Почему это важно |
|-------------|----------------|
| .NET 6.0 или новее | Aspose.Words for .NET 24.9+ ориентирован на .NET Standard 2.0 и работает на .NET 6+. |
| Aspose.Words for .NET **24.9** или новее | Свойство `IsGraduationsVisible` было введено в версии 24.9. Более старые версии вызовут `MissingMemberException`. |
| Документ Word (`RadialChart.docx`), содержащий радиальную диаграмму | Пример изменяет существующую диаграмму; создание её с нуля — отдельная тема. |
| IDE для C# (Visual Studio, Rider, VS Code) | Любая IDE, способная компилировать проекты .NET, подойдёт. |
| Пакет NuGet `Aspose.Words` | Установить через `dotnet add package Aspose.Words --version 24.9.0` (или позже). |

> **Совет:** Если вы не можете обновить до версии 24.9, вы всё равно можете изменять другие свойства диаграммы, но деления останутся скрытыми, поскольку API не предоставляет этот флаг.

## Пример радиальной диаграммы Aspose.Words – пошаговое руководство

Следующие разделы разбивают процесс на отдельные, легко‑следуемые шаги. Каждый шаг включает точный код, который вам нужен, и краткое объяснение *почему* шаг необходим.

### Шаг 1: Загрузить документ, содержащий радиальную диаграмму

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Почему это важно:**  
`Document` является точкой входа в **API Aspose.Words chart**. Он загружает файл DOCX в память, предоставляя доступ ко всем узлам — абзацам, таблицам и фигурам диаграмм. Если файл не найден, `Document` бросает `FileNotFoundException`, который следует обрабатывать в продакшн‑коде.

### Шаг 2: Получить первую фигуру диаграммы из документа

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Почему это важно:**  
Диаграммы хранятся как узлы `Shape`. Метод `GetChild` с параметром `NodeType.Shape` проходит по DOM и возвращает первую подходящую фигуру. Приведение к `Chart` даёт доступ к специфическим свойствам диаграммы, таким как `RadialChart`. Проверка на `null` обеспечивает понятную ошибку, если документ не содержит диаграмму, что часто встречается при повторном использовании шаблонов.

### Шаг 3: Включить деления на радиальной диаграмме

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Почему это важно:**  
`IsGraduationsVisible` управляет метками вокруг круговой оси. При установке в `true` диаграмма отображает деления, улучшая читаемость для тех, кто нуждается в точном определении значений. Свойство находится в `RadialChart`, который является подтипом `Chart`. Если попытаться применить его к не‑радиальной диаграмме (например, столбчатой), свойство `RadialChart` будет `null`, поэтому в более сложных сценариях следует сначала проверять тип диаграммы.

#### Обработка не‑радиальных диаграмм (опционально)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Эта проверка делает код надёжным, когда исходный документ может содержать различные типы диаграмм.

### Шаг 4: Сохранить изменённый документ

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Почему это важно:**  
Вызов `Save` записывает DOM из памяти обратно в файл .docx, сохраняет внесённые изменения в диаграмме. Полученный файл можно открыть в Microsoft Word, LibreOffice или любом просмотрщике, поддерживающем DOCX. Вы увидите радиальную диаграмму с видимыми делениями.

## Полный, исполняемый пример

Ниже приведена полная программа, которую вы можете вставить в `Program.cs` проекта .NET консольного приложения.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Ожидаемый результат

Когда вы откроете `RadialChart_Graduations.docx` в Word, радиальная диаграмма отобразит метки (деления) вокруг круговой оси, аналогично скриншоту, показанному выше. Остальная часть диаграммы (серии данных, легенда, заголовок) останется без изменений.

## Распространённые варианты и граничные случаи

| Ситуация | Решение |
|-----------|----------|
| **Старая версия Aspose.Words (< 24.9)** | Обновите до последнего пакета NuGet. Свойство `IsGraduationsVisible` отсутствует в более ранних версиях. |
| **Несколько диаграмм в одном документе** | Используйте `doc.GetChild(NodeType.Shape, index, true)` с соответствующим `index` или переберите `doc.GetChildNodes(NodeType.Shape, true)` и отфильтруйте по `ChartType.Radial`. |
| **Диаграмма, созданная программно** | Используйте `DocumentBuilder` для вставки диаграммы, затем установите `RadialChart.IsGraduationsVisible` на |

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Обновить данные серии диаграммы в документе Word с помощью Aspose.Words для .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Удалить серию диаграммы из документа Word с помощью Aspose.Words для .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Скрыть границу области построения в столбчатой диаграмме с Aspose.Words для .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}