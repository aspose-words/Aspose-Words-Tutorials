---
category: general
date: 2026-08-14
description: Как группировать фигуры в документе Word с помощью C#. Узнайте, как создать
  документ Word, вставить прямоугольную фигуру, сгруппировать фигуры в Word и сохранить
  документ в формате docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: ru
lastmod: 2026-08-14
og_description: Как группировать фигуры в документе Word с помощью C#. Следуйте этому
  полному руководству, чтобы создать файл Word, вставить прямоугольную фигуру, сгруппировать
  фигуры в Word и сохранить результат в формате docx.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: Как сгруппировать фигуры в документе Word с помощью C# – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Как сгруппировать фигуры в документе Word с помощью C#
url: /ru/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как группировать фигуры в документе Word с помощью C#

Если вам нужно **how to group shapes** в документе Word, это руководство покажет точные шаги с использованием C# и библиотеки Aspose.Words. Вы увидите, как создать документ Word, вставить прямоугольную фигуру, сгруппировать фигуры в Word и, наконец, **save document as docx** — всё в одной исполняемой программе.

Создание и манипулирование фигурами — распространённая задача при программной генерации отчетов, контрактов или маркетинговых брошюр. К концу этого руководства у вас будет переиспользуемый фрагмент кода, который можно вставить в любой .NET‑проект.

## Предварительные требования

- .NET 6.0 или новее установлен  
- Visual Studio 2022 (или любой IDE, поддерживающий .NET)  
- Лицензия Aspose.Words for .NET (или бесплатная пробная версия)  
- Базовое знакомство с синтаксисом C#  

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words`.

## Как группировать фигуры в документе Word

В основе решения лежит пятишаговый процесс. Каждый шаг подробно объяснён, а полный исходный код предоставлен в конце статьи.

### Шаг 1: Создать новый пустой документ

Первое, что вы делаете, когда хотите **create Word document** программно, — это создаёте объект `Document`. Этот объект представляет весь файл .docx в памяти.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** `DocumentBuilder` — это высокоуровневый помощник, позволяющий вставлять текст, таблицы и фигуры без ручного управления внутренним деревом узлов.

### Шаг 2: Вставить прямоугольную фигуру

Чтобы продемонстрировать **insert rectangle shape**, мы используем метод `InsertShape`. Прямоугольник будет первым элементом группы.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Why this matters:** Фигуры позиционируются относительно точки вставки. Установка цвета заливки помогает увидеть фигуру при открытии получившегося документа.

### Шаг 3: Вставить эллипс

Далее мы **insert ellipse shape** (в API он называется `Ellipse`). Это будет второй элемент группы.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Why this matters:** Вставляя эллипс сразу после прямоугольника, обе фигуры оказываются в одном абзаце, что упрощает последующее группирование.

### Шаг 4: Сгруппировать прямоугольник и эллипс

Теперь мы отвечаем на главный вопрос **how to group shapes** в документе Word. Aspose.Words предоставляет `AppendGroupShape` для создания контейнера группы, после чего вызывается `Group()` у этого контейнера.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Why this matters:** После группировки любое преобразование (перемещение, изменение размера, вращение), применённое к `groupedShape`, автоматически влияет и на прямоугольник, и на эллипс. Это важно для поддержания согласованности макета в сгенерированных документах.

### Шаг 5: Сохранить документ в формате DOCX

Последний шаг — **save document as docx**. Вы можете указать любой путь; в примере используется заполнитель `"YOUR_DIRECTORY"`, который следует заменить реальной папкой.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Why this matters:** Сохранение в формате DOCX сохраняет метаданные группировки, поэтому при открытии файла в Microsoft Word вы увидите прямоугольник и эллипс как единый объект.

## Полный, исполняемый пример

Ниже приведена полная программа, объединяющая все пять шагов. Скопируйте её в новый консольный проект, восстановите пакет Aspose.Words NuGet и запустите.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### Ожидаемый результат

Когда вы откроете `groupedShapes.docx` в Microsoft Word, вы увидите светло‑голубой прямоугольник и светло‑коралловый эллипс, соединённые вместе. Щелчок по любой из фигур выделит обе, позволяя перемещать или изменять их размер как единое целое.

## Часто задаваемые вопросы и особые случаи

| Question | Answer |
|----------|--------|
| **Can I group more than two shapes?** | Да. Передайте любое количество объектов `Shape` в `AppendGroupShape`. Метод принимает массив, поэтому вы можете динамически формировать коллекцию. |
| **What if I need the group to be anchored to a table cell?** | Вставьте фигуры в абзац ячейки таблицы, затем вызовите `AppendGroupShape` для этого абзаца. Группа унаследует привязку ячейки. |
| **Does grouping affect the underlying XML?** | Aspose.Words записывает элемент `<w:grpSp>`, содержащий дочерние фигуры. Word распознаёт его как группу, сохраняя относительное позиционирование. |
| **How do I ungroup later?** | Вызовите `groupedShape.Ungroup()`; метод возвращает отдельные фигуры, чтобы вы могли работать с ними отдельно. |
| **Is there a performance impact when grouping many shapes?** | Само группирование мало ресурсоёмко, но рендеринг очень больших групп (сотни фигур) может увеличить размер файла. При необходимости рассмотрите «уплощение» изображений. |

## Профессиональные советы

- **Set explicit positions** (`Left`, `Top`), если требуется точное выравнивание перед группировкой.  
- **Use `Shape.WrapType = WrapType.Inline`**, когда нужно, чтобы группа вела себя как элемент абзаца, а не как плавающий объект.  
- **Apply a line style** к группе (`groupedShape.LineFormat`), чтобы задать границу всей коллекции.  
- **Reuse the group**: после вызова `Group()` вы можете клонировать `groupedShape` и вставить клон в другое место документа.

## Следующие шаги

Теперь, когда вы знаете **how to group shapes** в документе Word, вы можете изучить связанные темы, такие как:

- **Insert rectangle shape** с пользовательским текстом или изображениями внутри фигуры.  
- **Create complex diagrams** путем вложения групп (группировать группу).  
- **Export the document as PDF** с сохранением группировки фигур (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

Каждый из этих пунктов опирается на те же основы, рассмотренные здесь, поэтому вы готовы расширять свой набор инструментов автоматизации Word.

## Заключение

Это руководство продемонстрировало **how to group shapes** в документе Word с помощью C#. Вы научились **create Word document**, **insert rectangle shape**, **group shapes in Word** и, наконец, **save document as docx**. С полным исполняемым примером и практическими советами вы можете интегрировать группировку фигур в любой процесс генерации документов. Happy coding!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}