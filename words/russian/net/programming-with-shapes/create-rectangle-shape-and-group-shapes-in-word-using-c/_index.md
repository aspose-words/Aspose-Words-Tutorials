---
category: general
date: 2026-09-08
description: Создайте прямоугольную форму в документе Word с помощью C#. Узнайте,
  как задать размер формы, сгруппировать несколько форм и программно создать пустой
  документ Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: ru
lastmod: 2026-09-08
og_description: Создайте прямоугольную форму в документе Word с помощью C#. Это руководство
  показывает, как задать размер формы, сгруппировать несколько форм и программно создать
  пустой документ Word.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Создание прямоугольной фигуры и группировка фигур в Word с помощью C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Создание прямоугольной формы и группировка форм в Word с помощью C#
url: /ru/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной фигуры и группировка фигур в Word с помощью C#

Если вам нужно **create rectangle shape** внутри файла Word, этот учебник предоставляет полное готовое решение. Вы увидите, как задать размер фигуры, сгруппировать несколько фигур и создать пустой документ Word с нуля — всё с использованием библиотеки Aspose.Words for .NET.

Работа с документами Word программно часто напоминает жонглирование множеством мелких деталей. К концу этого руководства у вас будет один метод, который создаёт файл `.docx`, содержащий прямоугольник и эллипс, объединённые в группу, готовые к дальнейшему редактированию или печати.

## Prerequisites

Перед началом убедитесь, что у вас есть:

* .NET 6.0 или новее (код также работает с .NET Framework 4.6+)
* Лицензированная копия **Aspose.Words for .NET** (можно использовать бесплатный оценочный ключ)
* IDE, например Visual Studio 2022 или Visual Studio Code
* Базовые знания синтаксиса C#

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words`.

## Step 1: Create a blank Word document

Первый шаг — создать пустой документ, который будет содержать фигуры. Это удовлетворяет требованию *create blank word document*.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Создание пустого документа даёт чистый холст. Объект `Document` представляет весь файл `.docx`, а его `FirstSection.Body.FirstParagraph` служит точкой вставки новых узлов по умолчанию.

## Step 2: Create rectangle shape

Теперь можно добавить прямоугольник. Здесь происходит операция **create rectangle shape**.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Указание размеров напрямую отвечает ключевому слову **set shape size**. Все значения размеров выражаются в пунктах, что обеспечивает точный контроль над внешним видом фигуры в конечном документе.

## Step 3: Create an additional shape (ellipse)

Типичный сценарий — комбинировать несколько фигур. Здесь мы добавляем эллипс, который позже будет находиться в том же контейнере.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Обе фигуры пока независимы. Следующий шаг покажет, как **group multiple shapes** вместе.

## Step 4: Group shapes in Word

Группировка фигур позволяет перемещать, изменять размер или форматировать их как единое целое. Это удовлетворяет требованиям **group shapes in word** и **group multiple shapes**.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

Свойство `GroupShape.Bounds` определяет систему координат для дочерних фигур. Поместив прямоугольник и эллипс в один `GroupShape`, вы сможете позже перемещать или вращать их вместе одним вызовом.

## Step 5: Save the document

Наконец, сохраняем документ на диск. Файл будет содержать только что созданные сгруппированные фигуры.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

После выполнения программы откройте `GroupedShapes.docx` в Microsoft Word. Вы должны увидеть прямоугольник и эллипс, объединённые в группу; выбор одной фигуры автоматически выбирает другую, подтверждая успешную группировку.

## Full source code

Скопируйте приведённую ниже полную программу в новый проект консольного приложения и запустите её. Дополнительный код не требуется.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Expected output

Запуск программы создаёт `GroupedShapes.docx`. Открытие файла в Word показывает:

* **Прямоугольник** (100 pt × 50 pt) с синей границей и светло‑серой заливкой.
* **Эллипс** (80 pt × 80 pt) с тёмно‑зелёной границей и светло‑жёлтой заливкой.
* Обе фигуры находятся в одной группе, поэтому перемещение одной перемещает и другую.

## Common questions and edge cases

| Вопрос | Ответ |
|----------|--------|
| **Могу ли я добавить в группу более двух фигур?** | Да. Создайте дополнительные объекты `Shape` и вызовите `group.AppendChild(yourShape)` для каждого. |
| **Что если мне нужно повернуть группу?** | Установите `group.RotationAngle = 45;` (градусы). Все дочерние фигуры повернутся вместе. |
| **Можно ли группировать фигуры после сохранения документа?** | Нужно изменить структуру документа до сохранения; иначе придётся загрузить файл, найти фигуры и заново создать группу. |
| **Нужно ли явно освобождать какие‑либо объекты?** | Aspose.Words управляет своими ресурсами, но следует освобождать объекты `FileStream`, если вы открываете потоки вручную. |
| **Будет ли код работать с форматом .doc (binary)?** | Да, измените `doc.Save("output.doc")`. Поведение группировки останется тем же. |

## Conclusion

Теперь вы знаете, как **create rectangle shape**, **set shape size** и **group multiple shapes** внутри файла Word с помощью C#. Такой подход позволяет программно создавать сложные диаграммы, водяные знаки или отчёты на основе шаблонов без ручного редактирования.

### Next steps

* Подробнее изучите **group shapes in word**, добавив в ту же группу текстовые блоки или изображения.  
* Используйте шаблон `SetShapeSize` для динамического расчёта размеров в зависимости от макета страницы.  
* Сочетайте эту технику с полями слияния для массовой генерации персонализированных документов.

Экспериментируйте с различными типами фигур, цветами и трансформациями групп. Приятного кодинга!

## What Should You Learn Next?

Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}