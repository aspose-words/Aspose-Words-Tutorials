---
category: general
date: 2026-08-10
description: Создайте документ Word программно с помощью Aspose.Words, узнайте, как
  группировать несколько фигур в Word, добавить прямоугольник в Word и создать групповую
  фигуру на C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: ru
lastmod: 2026-08-10
og_description: Создайте документ Word программно с помощью Aspose.Words. В этом руководстве
  показано, как сгруппировать несколько фигур в Word, добавить прямоугольник и внедрить
  элемент управления содержимым простого текста, всё на C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Создать документ Word программно – группировать фигуры в C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Создание Word‑документа программно и группировка фигур в C#
url: /ru/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Word‑документа программно и группировка фигур в C#

Если вам нужно **создать Word‑документ программно**, этот учебник покажет, как собрать файл DOCX с помощью Aspose.Words и **группировать несколько фигур в Word**. Мы также рассмотрим, как **добавить прямоугольник в Word** и **как создать групповую фигуру**, содержащую как прямоугольник, так и эллипс, плюс простой StructuredDocumentTag для ввода пользователем текста.

В конце вы получите готовый файл Word, в котором есть сгруппированная фигура «прямоугольник‑эллипс» и элемент управления содержимым, где пользователь может ввести имя. После выполнения кода никакое ручное редактирование в Word не требуется.

## Что понадобится

- .NET 6.0 или новее (пример ориентирован на .NET 6, но подойдёт любая современная версия .NET)
- Лицензия Aspose.Words for .NET (бесплатная trial‑версия подходит для тестирования)
- Visual Studio 2022 или любой другой предпочитаемый IDE для C#
- Базовые знания синтаксиса C#

## Создание Word‑документа программно – общий рабочий процесс

Процесс состоит из трёх логических фаз:

1. **Инициализировать** `Document` и `DocumentBuilder` – фундамент для любого генерируемого Word‑файла.
2. **Создать групповую фигуру**, содержащую прямоугольник и эллипс – демонстрация **группировать несколько фигур в Word** и **как создать групповую фигуру**.
3. **Вставить StructuredDocumentTag (SDT)** – простой текстовый элемент управления содержимым, позволяющий конечным пользователям вводить данные, иллюстрируя **добавить прямоугольник в Word** как часть общей разметки документа.

Ниже приведён полностью готовый, исполняемый код, после которого следует пошаговый разбор.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Шаг 1 – Инициализация документа и builder‑а
Объект `Document` представляет весь файл DOCX, а `DocumentBuilder` предоставляет удобный API для добавления содержимого. Их инициализация – первое требование при **создании Word‑документа программно**.

> **Pro tip:** Если планируется многократное использование одного и того же документа в разных операциях, храните один экземпляр `DocumentBuilder`, чтобы избежать лишнего создания объектов.

### Шаг 2 – Создание контейнера групповой фигуры
`Shape` с `ShapeType.Group` выступает в роли холста, способного удерживать другие фигуры. Установка `Width` и `Height` определяет ограничивающий прямоугольник группы. Это ядро **как создать групповую фигуру** в Aspose.Words.

> **Edge case:** Если ширина группы меньше суммарной ширины её дочерних элементов, дочерние элементы будут обрезаны. Делайте группу достаточно большой, чтобы вместить каждую дочернюю фигуру.

### Шаг 3 – Добавить прямоугольник в Word
Прямоугольник создаётся с помощью `ShapeType.Rectangle`. Свойства `Left` и `Top` позиционируют его относительно начала группы. Этот шаг демонстрирует **добавить прямоугольник в Word** и показывает, как точно управлять размещением.

> **Common mistake:** Если не задать `Left`/`Top`, прямоугольник появится в начале группы (0,0), что может привести к наложению с другими элементами.

### Шаг 4 – Добавить эллипс (окружность) в группу
Эллипс добавляется так же, как и прямоугольник, но с `ShapeType.Ellipse`. Значение `Left = 210` смещает его вправо от прямоугольника, создавая визуально отдельную пару фигур внутри одной группы.

> **Why use a group?** Группировка позволяет позже перемещать, вращать или изменять размер обеих фигур одновременно одной операцией, сохраняя их относительное расположение.

### Шаг 5 – Вставить готовую групповую фигуру в документ
`builder.InsertNode(groupShape)` помещает всю группу в текущую позицию курсора. Поскольку группа уже содержит свои дочерние элементы, дополнительные вызовы вставки для прямоугольника или эллипса не требуются.

### Шаг 6 – Создать простой текстовый StructuredDocumentTag (SDT)
StructuredDocumentTag – это элемент управления содержимым, который пользователь может заполнить при открытии документа в Word. Установка `Title = "CustomerName"` даёт элементу понятный идентификатор, полезный для последующего извлечения данных.

> **Why a plain‑text SDT?** Он ограничивает ввод простым текстом, предотвращая случайное форматирование, которое могло бы нарушить дальнейшую обработку.

### Шаг 7 – Сохранить документ
`doc.Save("GroupAndSDT.docx")` записывает файл на диск. Получившийся DOCX содержит сгруппированные фигуры и SDT. При открытии файла в Microsoft Word вы увидите прямоугольник рядом с кругом, оба выделяются как один объект, а под ними – заполнитель «Enter name here …».

#### Ожидаемый результат
- Файл **GroupAndSDT.docx** в папке выполнения.
- В Word: групповая фигура (прямоугольник + эллипс), которую можно перемещать как единое целое.
- Сразу под группой – серый элемент управления содержимым, предлагающий пользователю ввести имя.

## Дополнительные варианты и лучшие практики

### Использование разных типов фигур
Можно заменить `ShapeType.Rectangle` или `ShapeType.Ellipse` на любой другой `ShapeType` (например, `ShapeType.Polygon`, `ShapeType.Line`). Логика группировки остаётся той же.

### Установка цвета заливки и границ
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Добавление заливки и обводки улучшает визуальное различие, особенно когда документ просматривают не‑технические заинтересованные стороны.

### Вращение всей группы
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Вращать группу эффективнее, чем вращать каждый дочерний элемент отдельно.

### Экспорт в PDF
Если нужен PDF, достаточно вызвать:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Все сгруппированные фигуры и SDT (отображаемый как текстовое поле) появятся в PDF‑файле.

## Распространённые подводные камни и как их избежать

| Symptom | Cause | Fix |
|---------|-------|---|

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогая вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}