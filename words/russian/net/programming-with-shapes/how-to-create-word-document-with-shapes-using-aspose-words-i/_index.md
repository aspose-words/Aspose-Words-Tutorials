---
category: general
date: 2026-09-11
description: Узнайте, как создать документ Word, добавить прямоугольную форму и задать
  её размеры с помощью Aspose.Words. Пошаговое руководство на C# для точного задания
  размеров формы.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: ru
lastmod: 2026-09-11
og_description: Создайте документ Word с помощью Aspose.Words на C#. Это руководство
  показывает, как добавить прямоугольную форму, установить её размер и управлять размерами
  формы программно.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Создание Word‑документа с фигурами – учебник Aspose.Words C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Как создать документ Word с фигурами с помощью Aspose.Words в C#
url: /ru/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать документ Word с фигурами, используя Aspose.Words в C#

Если вам нужно **создать документ Word**, содержащий пользовательскую графику, вы можете сделать это полностью в коде. Этот учебник проведёт вас через процесс создания файла Word, добавления прямоугольной фигуры и управления каждой её размерностью. В конце у вас будет переиспользуемый фрагмент, который можно вставить в любой проект .NET.

Вы узнаете, как **add rectangle shape**, **set shape size** и **set shape dimensions** внутри группового контейнера. В примере используется Aspose.Words 13.9, но концепции применимы и к более поздним версиям. Предыдущий опыт работы с API рисования Aspose не требуется — достаточно базовых знаний C#.

## Prerequisites

- .NET 6.0 или новее, установленный на компьютере  
- NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- IDE, например Visual Studio 2022 (подойдёт любой редактор, поддерживающий C#)  

Наличие этих инструментов позволяет сразу запустить код без дополнительной настройки.

## Step 1: Initialize the document and builder – create word document basics

Первая операция — создать объект `Document` и `DocumentBuilder`. `Document` представляет сам файл, а `DocumentBuilder` предоставляет удобный API для вставки содержимого.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
Создание документа заранее даёт чистый холст. Курсор билдера начинается с первого абзаца, где мы позже **create shapes in word**.

## Step 2: Build a GroupShape to hold multiple graphics

`GroupShape` работает как контейнер; его можно перемещать, вращать или изменять размер как единое целое. Здесь мы задаём ширину и высоту контейнера в пунктах (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Why this matters:**  
Группировка фигур упрощает управление макетом. Если позже понадобится добавить другие фигуры (например, круги или текстовые поля), они унаследуют позицию и масштаб группы.

## Step 3: Create a rectangle shape and configure its dimensions

Теперь добавляем сам прямоугольник. Конструктор `Shape` требует ссылку на документ и тип фигуры. После создания мы явно **set shape size** и **set shape dimensions**.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Why this matters:**  
Указание ширины, высоты, левого и верхнего отступов даёт пиксель‑точный контроль над фигурой. Это важно, когда документ должен соответствовать дизайнерской спецификации или печатной форме.

## Step 4: Assemble the group by appending the rectangle

Добавление прямоугольника в `GroupShape` делает его дочерним узлом. Вы можете добавить столько дочерних элементов, сколько потребуется, прежде чем вставлять группу в документ.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Tip:** Если планируется добавить вторую фигуру, создайте её тем же способом и вызовите `group.AppendChild(secondShape)`. Все дочерние элементы используют одну систему координат группы.

## Step 5: Insert the grouped shape into the document and save

После полной сборки группы мы помещаем её в текущий абзац. Свойство `CurrentParagraph` билдера предоставляет прямой доступ к внутреннему дереву узлов.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Why this matters:**  
Добавление группы в абзац гарантирует, что фигура будет отображаться в потоке текста. Сохранение документа завершает операцию **create word document**.

## Common variations and edge cases

| Сценарий | Корректировка |
|----------|----------------|
| **Different page orientation** | Set `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` before creating the group. |
| **Multiple rectangles** | Create additional `Shape` objects and call `group.AppendChild(newRect)` for each. |
| **Dynamic size based on content** | Compute width/height from image dimensions or text metrics, then assign to `rectangle.Width` / `rectangle.Height`. |
| **Export to PDF** | After `doc.Save`, call `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Compatibility with older Word versions** | Save using `SaveFormat.Doc` instead of `Docx` for Word 97‑2003 compatibility. |

## Full, runnable example

Ниже приведена полная программа, которую можно скопировать, вставить и запустить. В ней указаны все директивы `using`, точка входа `Main` и комментарии, поясняющие каждую строку.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Expected output:**  
При открытии *GroupShape.docx* первая страница показывает прямоугольник с серой границей, расположенный на 50 pt от левого/верхнего поля, а сам прямоугольник смещён внутри группы на 10 pt. Размеры соответствуют значениям, заданным в коде.

## Conclusion

Теперь вы знаете, как **create word document**, **add rectangle shape** и точно **set shape size** и **set shape dimensions** с помощью Aspose.Words. Подход с групповой фигурой делает ваш макет гибким и готовым к будущим расширениям, таким как дополнительные графические элементы или текстовые поля.

Далее изучайте связанные темы, например **create shapes in word** для кругов, стрелок или пользовательских SVG‑контуров, а также как **set shape fill color** или **apply rotation**. Поэкспериментируйте с различными единицами измерения, чтобы увидеть, как Word отображает пункты versus сантиметры, и интегрируйте код в более крупные конвейеры генерации документов.

Happy coding, and feel free to adapt this pattern to any automated reporting or form‑filling scenario you encounter!

## What Should You Learn Next?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Создать прямоугольную фигуру в Word с помощью C# – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Создать пустой документ Word с фигурой‑прямоугольником с тенью – пошаговое руководство](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Учебник по теням фигур Aspose.Words – добавить тень к фигуре Word в C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}