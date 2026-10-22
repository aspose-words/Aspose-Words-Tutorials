---
category: general
date: 2026-10-07
description: Создать пустой документ Word на C# и научиться добавлять прямоугольную
  форму, вставлять изображение и группировать несколько форм для динамических отчётов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: ru
lastmod: 2026-10-07
og_description: Создайте пустой документ Word на C# с помощью Aspose.Words. Узнайте,
  как добавить прямоугольную форму, вставить изображение в виде формы и объединить
  несколько форм для профессиональных документов.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Создание пустого документа Word и группировка фигур в C# — пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Как создать пустой документ Word и сгруппировать фигуры в C#
url: /ru/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать пустой документ Word и сгруппировать фигуры в C#

Если вам нужно **create blank Word document** программно, это руководство покажет, как это сделать. Вы увидите, как **add rectangle shape**, **insert image shape**, и **group multiple shapes**, чтобы они вели себя как один объект, когда вы позже **add image to Word**.

Работа с файлами Word из кода может показаться сложной, но Aspose.Words делает процесс простым. К концу этого руководства у вас будет переиспользуемый фрагмент C#, который генерирует чистый пустой файл Word, содержащий сгруппированный прямоугольник и логотип. Вы сможете внедрять результат в счета, отчёты или любой автоматизированный документооборот.

## Предварительные требования

* .NET 6.0 или новее (код также работает с .NET Framework 4.7+).  
* Действительная лицензия Aspose.Words for .NET или бесплатный ключ оценки.  
* Файл изображения (например, `logo.png`), размещённый в папке, к которой можно обратиться из кода.  
* Visual Studio 2022 или любой IDE, поддерживающий C#.

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words`.

## Как создать пустой документ Word с помощью Aspose.Words

Первый шаг всегда — **create blank Word document**. Этот объект будет хранить все последующие фигуры.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` представляет весь файл `.docx`. На данном этапе файл пуст, что удовлетворяет требованию *create blank Word document*.

## Создание контейнера для группировки нескольких фигур

Группировка фигур позволяет перемещать, вращать или изменять их размер одновременно. Aspose.Words предоставляет класс `GroupShape` для этой цели.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

Прямоугольник `Bounds` определяет, где группа будет отображаться на странице. Поместив группу в первый абзац, вы гарантируете, что **create blank Word document** сразу же будет содержать визуальный контейнер.

## Как добавить прямоугольную фигуру внутри группы

Обычное требование — **add rectangle shape** в качестве фона или рамки. Следующий код создаёт прямоугольник и добавляет его в ранее определённую группу.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Поскольку прямоугольник находится внутри `GroupShape`, он будет перемещаться вместе с любыми другими фигурами, которые вы добавите позже. Это основа функциональности **group multiple shapes**.

## Как вставить изображение внутри группы

Далее вы **insert image shape** (логотип) и разместите его рядом с прямоугольником. Это демонстрирует процесс **add image to Word**.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

Метод `SetImage` читает файл и встраивает его напрямую в документ Word, гарантируя, что изображение сохранится даже при перемещении исходного файла. Это завершает шаг **insert image shape** и удовлетворяет требование **add image to Word**.

## Сохранение документа

Наконец, сохраняем файл на диск. Сохранённый файл содержит пустой документ, сгруппированный прямоугольник и встроенный логотип.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Когда вы откроете `GroupShape.docx` в Microsoft Word, вы увидите одну группу, включающую светло‑серый прямоугольник и логотип, расположенные рядом. Выбор любой части группы позволяет перемещать или изменять размер всей коллекции, подтверждая, что фигуры действительно **group multiple shapes**.

## Полный, исполняемый пример

Ниже представлен полный код программы, который можно скопировать, вставить и запустить. Замените `YOUR_DIRECTORY` на абсолютный или относительный путь, существующий на вашем компьютере.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Ожидаемый результат

* Файл с именем `GroupShape.docx`, расположенный в `YOUR_DIRECTORY`.  
* При открытии файла в Word отображается одна визуальная группа, содержащая серый прямоугольник слева и `logo.png` справа.  
* Выбор любой части визуальной группы позволяет перемещать или изменять размер всей коллекции, подтверждая, что фигуры правильно **group multiple shapes**.

## Часто задаваемые вопросы и обработка граничных случаев

| Question | Answer |
|---|---|
| **Can I add more than two shapes to the same group?** | Yes. Call `group.AppendChild(yourShape)` for each additional `Shape`. The group can contain any number of drawing objects. |
| **What if the image file is missing?** | `SetImage` will throw a `FileNotFoundException`. Wrap the call in a try‑catch block and provide a fallback (e.g., a placeholder shape). |
| **Do I need to set `WrapType` for the shapes?** | By default shapes are inline. If you need floating behavior, set `picture.WrapType = WrapType.Inline;` or another wrap mode before adding to the group. |
| **How does the document size affect the group’s bounds?** | The `Bounds` rectangle is defined in points (1 pt ≈ 1/72 in). Adjust the size if you place the group on a different page layout (e.g., A4 vs. Letter). |
| **Can I reuse the same group in another document?** | Yes. Clone the group with `GroupShape cloned = (GroupShape)group.Clone(true);` and insert it into a different `Document`. |

## Профессиональные советы

* **Reuse the `DocumentBuilder`** for adding text before or after the group. It automatically respects the current cursor position.  
* **Set `Shape.StrokeColor`** if you need a visible border around the rectangle.  
* **Use high‑resolution PNGs** for the logo to avoid pixelation when

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в собственных проектах.

- [Создание групповой фигуры в документе Word с помощью Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Создание прямоугольной фигуры в Word с использованием C# – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Вставка встроенного изображения в документ Word с помощью Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}