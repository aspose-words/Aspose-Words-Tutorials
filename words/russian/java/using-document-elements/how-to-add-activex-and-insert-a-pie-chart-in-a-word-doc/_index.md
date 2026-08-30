---
category: general
date: 2026-08-17
description: Как добавить элементы управления ActiveX и вставить круговую диаграмму
  в документ Word с помощью Aspose.Words. Выделить отдельный сектор и сохранить как
  DOCX за несколько шагов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: ru
lastmod: 2026-08-17
og_description: Как добавить элементы управления ActiveX, вставить круговую диаграмму,
  выделить сектор и сохранить в формате DOCX с помощью Aspose.Words — полное пошаговое
  руководство.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Как добавить ActiveX и вставить круговую диаграмму в документ Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Как добавить ActiveX и вставить круговую диаграмму в документ Word
url: /ru/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как добавить ActiveX и вставить круговую диаграмму в документ Word

Если вам нужно **как добавить ActiveX**‑элементы управления и встроить диаграмму в документ Word, этот учебник покажет полное, готовое к запуску решение. С помощью Aspose.Words вы можете разместить ActiveX CommandButton, создать круговую диаграмму, «взрыв» (выделить) один из секторов для акцента и, наконец, **сохранить как DOCX** всего в несколько строк C#.

В разделах ниже вы увидите все необходимые импорты, полный список кода и объяснения, почему каждый шаг важен. К концу вы сможете интегрировать интерактивные элементы управления и визуальные данные в любой .docx‑файл, генерируемый программно.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 или новее (код также работает с .NET Framework 4.7+)
* Пакет Aspose.Words for .NET (доступен через NuGet)
* Среда разработки, например Visual Studio 2022 или VS Code
* Базовые знания C# и модели объектов Word

Дополнительные сторонние библиотеки для построения диаграмм не требуются — Aspose.Words предоставляет встроённые возможности создания диаграмм.

## Как добавить ActiveX‑элементы управления с помощью Aspose.Words

ActiveX‑элементы позволяют встраивать интерактивные UI‑компоненты непосредственно в файл Word. В этом руководстве мы добавляем **CommandButton**, который позже можно привязать к коду VBA.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Почему это работает:**  
`InsertForms2OleControl` создаёт OLE‑контейнер, который пользовательский интерфейс Word распознаёт как ActiveX‑элемент. Установка типа элемента управления в `CommandButton` и задание подписи заставляют его вести себя как обычная кнопка, когда пользователь открывает файл в Word.

## Вставка круговой диаграммы и «взрыв» сектора

Диаграммы полезны для визуализации данных без выхода из документа. Следующие шаги демонстрируют **как вставить диаграмму** и, конкретно, **круговую диаграмму**, у которой первый сектор «взрывается».

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Почему «взрываем» сектор:**  
Вызов `SetExplode(0, true)` сообщает Aspose.Words сместить первую точку данных, привлекая взгляд зрителя к этому сегменту. Это распространённая техника в презентациях для выделения ключевого значения.

## Сохранить как DOCX

После добавления кнопки ActiveX и диаграммы сохраняем документ на диск. Этот шаг демонстрирует **save as DOCX** с использованием стандартного метода.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

Файл `Output.docx` теперь содержит интерактивную кнопку, круговую диаграмму с «взрывом» сектора и может быть открыт в Microsoft Word без дополнительных плагинов.

## Полный рабочий пример

Объединив всё вместе, получаем автономную программу, которую можно скопировать в консольное приложение и сразу запустить.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Ожидаемый результат:**  
Открытие `Output.docx` в Word показывает кнопку с надписью *Click Me* и круговую диаграмму, где первый сектор (January) смещён от остальных. Кнопка готова к обработке событий VBA, а диаграмму можно редактировать с помощью встроенных средств Word.

## Часто задаваемые вопросы и особые случаи

* **Можно ли добавить другие типы ActiveX?**  
  Да. Замените `Forms2OleControlType.CommandButton` на любое значение из перечисления `Forms2OleControlType` (например, `CheckBox`, `OptionButton`). Паттерн вставки остаётся тем же.

* **А если нужен другой тип диаграммы?**  
  Используйте `ChartType.Bar`, `ChartType.Line` и т.д. в вызове `InsertChart`. Шаг **how to insert chart** остаётся идентичным; меняется только значение перечисления.

* **Как контролировать размер «взрыва» сектора?**  
  В текущей версии Aspose.Words поддерживается только бинарный флаг «взрыв» (true/false). Для более точной настройки (например, расстояния смещения) потребуется изменить underlying OOXML после сохранения.

* **Совместим ли документ со старыми версиями Word?**  
  Сохранение как DOCX обеспечивает совместимость с Word 2007 и новее. Для Word 2003 можно использовать `SaveFormat.Doc`, но поддержка ActiveX в этом формате ограничена.

* **Нужно ли ссылаться на `System.Drawing`?**  
  Нет. Все графические объекты предоставляются Aspose.Words, поэтому единственный необходимый пакет NuGet — `Aspose.Words`.

## Заключение

Теперь вы знаете **как добавить ActiveX**, **вставить круговую диаграмму**, **взять сектор диаграммы** и **сохранить как DOCX** с помощью Aspose.Words for .NET. Полный пример охватывает каждый шаг от создания документа до финального сохранения и объясняет логику каждого вызова API.

Дальше вы можете изучить:

* Добавление VBA‑макросов, реагирующих на клик CommandButton (**how to insert chart** и автоматизацию обновления данных)
* Настройку внешнего вида диаграммы (цвета, подписи данных) в соответствии с корпоративным брендингом
* Встраивание дополнительных ActiveX‑элементов, таких как **ComboBox** или **ListBox**, для более сложных форм

Экспериментируйте с кодом, заменяйте примерные данные и интегрируйте решение в свои конвейеры генерации документов. Приятного кодинга!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}