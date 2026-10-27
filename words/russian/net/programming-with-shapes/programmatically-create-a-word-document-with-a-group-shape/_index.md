---
category: general
date: 2026-09-27
description: Программно создайте документ Word с групповой фигурой, используя Aspose.Words
  в C#. Следуйте этому пошаговому руководству, чтобы создать файл и узнать полезные
  советы.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: ru
lastmod: 2026-09-27
og_description: Программно создайте документ Word с групповой фигурой, используя Aspose.Words.
  Этот учебник пошагово проведёт вас через полный код на C#, объяснит каждый шаг и
  покажет конечный результат.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Программное создание документа Word с групповой фигурой – руководство по
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Программно создать документ Word с групповой фигурой
url: /ru/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Программное создание Word‑документа с групповой фигурой

Если вам нужно **программно создавать Word‑документ**, содержащий сгруппированное изображение, это руководство покажет, как сделать это с помощью Aspose.Words for .NET. Независимо от того, создаёте ли вы генератор контрактов, конструктор отчётов или инструмент заполнения форм, вы изучите полный код на C#, почему каждый вызов API важен и как обрабатывать распространённые граничные случаи.

Создание групповой фигуры в Word может показаться сложным, поскольку объектная модель Word рассматривает групповые фигуры как контейнеры для других графических объектов. Это руководство не только отвечает на вопрос, как создать документ Word с групповой фигурой, но и демонстрирует, как встроить простую текстовую StructuredDocumentTag (SDT) внутрь группы, чтобы фигура могла содержать редактируемый контент.

## Что вы достигнете

- Инициализировать новый пустой Word‑документ с помощью `Document` и `DocumentBuilder`.
- Вставить `GroupShape` в текущую позицию курсора.
- Добавить простую текстовую `StructuredDocumentTag` (SDT) в групповую фигуру.
- Сохранить файл как `.docx`, который можно открыть в Microsoft Word.
- Понять ключевые свойства `GroupShape` и `StructuredDocumentTag` для будущих расширений.

### Предварительные требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.7+).
- NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`).
- IDE для C#, например Visual Studio 2022 или VS Code с расширением C#.

---

## Программное создание Word‑документа – настройка проекта

1. **Создайте новый консольный проект**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Откройте проект в своей IDE** и замените содержимое `Program.cs` кодом, показанным в следующих разделах.

> **Pro tip:** Держите папку проекта в чистоте; Aspose.Words записывает выходной файл в рабочий каталог, если не указать абсолютный путь.

## Шаг 1: Инициализация документа и builder'а

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Почему это важно:**  
`Document` представляет весь файл Word, а `DocumentBuilder` позволяет позиционировать новые элементы без ручного перемещения по дереву узлов. Установка размеров страницы заранее гарантирует, что групповая фигура не выйдет за пределы страницы.

## Шаг 2: Вставка GroupShape в текущую позицию курсора

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Объяснение:**  
`GroupShape` — это графический объект, который может содержать другие фигуры, изображения или текстовые поля. Устанавливая `Width`, `Height`, `Left` и `Top`, вы задаёте точное расположение на странице. Метод `InsertNode` помещает фигуру в основной поток документа, ведя себя как плавающий объект.

## Шаг 3: Добавление простой текстовой StructuredDocumentTag (SDT) внутри группы

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Зачем использовать SDT?**  
StructuredDocumentTags — это нативные элементы управления содержимым Word. Они позволяют пользователям редактировать текст напрямую в сохранённом документе и могут быть программно доступны позже для извлечения данных. Размещение SDT внутри групповой фигуры позволяет сочетать визуальное группирование с редактируемым содержимым.

## Шаг 4: Сохранение документа

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Результат:**  
Открывая `GroupShapeDemo.docx` в Microsoft Word, вы увидите плавающий прямоугольник (групповую фигуру), содержащий заполнитель текста «Enter text here». Пользователи могут кликнуть внутри фигуры и вводить текст напрямую.

### Ожидаемый скриншот результата (концептуально)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

Внешний прямоугольник — это `GroupShape`; внутренняя серая область — `StructuredDocumentTag`.

## Как создать group shape word – дополнительные соображения

### Добавление дополнительных дочерних фигур

Вы можете обогатить группу, добавив дополнительные графические объекты, такие как изображения или текстовые поля:

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Управление стилем обтекания

Если необходимо, чтобы групповая фигура находилась позади текста или имела плотное обтекание, задайте свойство `WrapType`:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Граничный случай: пустая групповая фигура

`GroupShape` без дочерних элементов отображается как невидимый заполнитель. Всегда проверяйте, что добавлен хотя бы один дочерний элемент (например, SDT или изображение); иначе Word может удалить группу при сохранении.

### Примечание о совместимости

Aspose.Words 23.10+ полностью поддерживает `GroupShape` и `StructuredDocumentTag`. Если вы используете более старые версии, метод `AppendChild` может вести себя иначе, и после сохранения может потребоваться вызов `UpdatePageLayout`.

## Полный исполняемый пример

Скопируйте весь фрагмент ниже в `Program.cs` и запустите проект. Код включает все шаги, описанные выше, в единой автономной программе.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.PageSetup.PageWidth = 595;
        builder.PageSetup.PageHeight = 842;

        // 2️⃣ Create and insert a GroupShape.
        GroupShape groupShape = new GroupShape(doc)
        {
            Width = 300,
            Height = 150,
            Left = 100,
            Top = 100
        };
        builder.InsertNode(groupShape);

        // 3️⃣ Add a plain‑text StructuredDocumentTag (SDT) inside the group.
        StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
        {
            Title = "GroupShapeText",
            PlaceholderName = "Enter text here"
        };
        groupShape.AppendChild(sdtTag);

        // 4️⃣ Optional: add a picture to demonstrate multiple children.
        // Uncomment and adjust the path if you want to test this.
        /*
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            ImageData = ImageData.FromFile("logo.png"),
            Width = 100,
            Height = 50,
            Left


## Что следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые расширяют техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в собственных проектах.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}