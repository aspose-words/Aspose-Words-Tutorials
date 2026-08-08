---
category: general
date: 2026-08-07
description: Как группировать фигуры в Word с помощью Aspose.Words и добавлять фигуры
  в документ Word, используя C#. Следуйте этому пошаговому руководству для чистого,
  переиспользуемого кода.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: ru
lastmod: 2026-08-07
og_description: Как группировать фигуры в Word с помощью Aspose.Words для .NET. Этот
  учебник покажет, как добавить фигуры в документ Word, сгруппировать их и сохранить
  файл с понятным кодом C#.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Как сгруппировать фигуры в Word – быстрый гид по C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Как группировать фигуры в Word и добавлять фигуры в документ Word
url: /ru/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как группировать фигуры в Word и добавлять фигуры в документ Word

Если вам нужно **how to group shapes in Word**, это руководство проведет вас через весь процесс с использованием Aspose.Words for .NET. Вы также узнаете, как **add shapes to Word document** с помощью нескольких строк кода C#, так что результат готов для любых сценариев отчетности или шаблонизации.

В руководстве рассматривается всё, что вам необходимо: требуемые пакеты NuGet, полный исходный файл и объяснение, почему каждый шаг важен. К концу вы сможете сгенерировать DOCX, содержащий прямоугольник и эллипс, объединённые в одну групповую фигуру.

## Предварительные требования

Перед началом убедитесь, что у вас есть:

* .NET 6.0 SDK или более поздняя версия установлена  
* Visual Studio 2022 (или любая IDE, поддерживающая .NET)  
* NuGet‑пакет Aspose.Words for .NET (`Aspose.Words`) — бесплатная пробная версия подходит для тестирования, но лицензия удаляет водяные знаки оценки  

Эти элементы являются единственными внешними зависимостями для **add shapes to Word document**.

## Как группировать фигуры в Word

Суть решения состоит в создании отдельных фигур, размещении их на странице и последующей упаковке их в `GroupShape`. Ниже перечислены шаги в том порядке, в котором они реализованы в коде.

### Шаг 1: Создать документ и DocumentBuilder

Объект `Document` представляет весь файл DOCX. `DocumentBuilder` предоставляет удобный API для редактирования документа.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters*: `Document` — контейнер для всех элементов Word. `DocumentBuilder` отслеживает текущую позицию курсора, что необходимо при последующей вставке групповой фигуры.

### Шаг 2: Добавить прямоугольную фигуру

Прямоугольник создаётся указанием `ShapeType.Rectangle`. Ширина, высота и расположение задаются в пунктах (1 pt ≈ 1/72 in).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*Why this matters*: Установка `StrokeColor` делает фигуру видимой при открытии документа. При необходимости можно также заполнить её цветом с помощью `FillColor`.

### Шаг 3: Добавить эллипс

Эллипс использует `ShapeType.Ellipse`. Его размер и позиция независимы от прямоугольника, что позволяет контролировать окончательное расположение группы.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*Why this matters*: Разместив эллипс с `Left = 120`, он не перекрывает прямоугольник, делая группу визуально различимой.

### Шаг 4: Сгруппировать две фигуры

`GroupShape` выступает в роли контейнера, рассматривающего своих детей как один объект. Это ключевая операция для **how to group shapes in Word**.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*Why this matters*: Группировка позволяет перемещать, изменять размер или вращать обе фигуры одновременно. Любое преобразование, применённое к `groupShape`, распространяется на её дочерние элементы.

### Шаг 5: Вставить групповую фигуру в документ

`DocumentBuilder.InsertNode` размещает `GroupShape` в текущей позиции курсора. Поскольку мы не перемещали builder, группа появляется в начале первой страницы.

```csharp
builder.InsertNode(groupShape);
```

*Why this matters*: Прямая вставка узла избавляет от необходимости создавать отдельный абзац или ячейку таблицы. Группа становится частью потока документа.

### Шаг 6: Сохранить документ

Наконец, запишите файл DOCX на диск. Используйте полный путь, в который ваше приложение имеет право записи.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*Why this matters*: `doc.Save` фиксирует все изменения. Полученный файл можно открыть в Microsoft Word, LibreOffice или любом просмотрщике, поддерживающем DOCX.

## Полный исходный файл

Скопируйте код ниже в новый консольный проект (`dotnet new console`) и запустите его. Программа создаст файл `GroupShape.docx`, содержащий сгруппированный прямоугольник и эллипс.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### Ожидаемый результат

Откройте `GroupShape.docx`. Вы увидите один визуальный объект, содержащий синий прямоугольник слева и зелёный эллипс справа. Выделение объекта в Word подсвечивает обе фигуры одновременно — доказательство того, что **how to group shapes in Word** выполнено успешно.

## Часто задаваемые вопросы и особые случаи

* **Можно ли добавить более двух фигур?**  
  Да. Вызовите `groupShape.AppendChild` для каждой дополнительной `Shape` перед вставкой группы.

* **Что делать, если нужно повернуть группу?**  
  Установите `groupShape.RotationAngle = 45;` (угол в градусах) после построения группы.

* **Нужно ли вызывать `doc.UpdatePageLayout()`?**  
  Не требуется для данного сценария. Макет обновляется автоматически при сохранении документа.

* **Как лицензирование влияет на код?**  
  При наличии действующей лицензии Aspose.Words (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) сгенерированный документ не содержит водяных знаков оценки.

## Заключение

Теперь вы знаете **how to group shapes in Word** и **add shapes to Word document** с помощью Aspose.Words for .NET. В руководстве рассмотрены создание документа, определение отдельных фигур, их группировка, вставка группы и сохранение файла.  

Отсюда вы можете экспериментировать с:

* Добавлением текстовых полей или изображений в группу  
* Изменением цветов заливки, стилей линий или эффектов тени  
* Группировкой фигур внутри таблиц или колонтитулов  

Эти расширения позволяют программно создавать сложные шаблоны Word, сохраняя код чистым и поддерживаемым. Приятного кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}