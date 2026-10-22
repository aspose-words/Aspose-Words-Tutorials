---
category: general
date: 2026-07-29
description: Рисуем прямоугольник в Word с помощью Aspose.Words. Узнайте, как добавить
  форму прямоугольника, добавить форму линии и управлять несколькими формами Word
  в одном документе.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: ru
lastmod: 2026-07-29
og_description: Рисуйте прямоугольник в Word с помощью Aspose.Words. Следуйте этому
  пошаговому руководству, чтобы добавить форму прямоугольника, добавить форму линии
  и без труда работать с несколькими формами в Word.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: Рисуем прямоугольник в Word – мастер добавления фигур в Word
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Рисовать прямоугольник в Word – Добавление фигур в Word с Aspose
url: /ru/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Полное руководство по добавлению фигур в Word

Когда‑то задумывались, как **draw rectangle word** документы без постоянного открытия пользовательского интерфейса? Вы не одиноки. Многие разработчики нуждаются в генерации файлов Word «на лету», и самый простой способ – позволить библиотеке выполнить всю тяжёлую работу. В этом руководстве мы покажем, как **добавлять фигуры** — конкретно прямоугольник и линию — используя Aspose.Words for .NET, и будем сосредоточены на фразе *draw rectangle word*, чтобы вы никогда не терялись.

Представьте это как мини‑арт‑студию, живущую внутри вашего кода. К концу вы сможете **добавлять прямоугольную фигуру**, **добавлять линейную фигуру** и даже объединять их в группы **multiple shapes word**. Без UI, без ручного вмешательства, только чистый, повторяемый C#.

## Что вы узнаете

- Как создать новый документ Word с помощью Aspose.Words.  
- Как создать **GroupShape**, способный содержать несколько объектов.  
- **add rectangle shape** и **add line shape** внутри этой группы.  
- Как вставить сгруппированные фигуры в тело документа.  
- Как сохранить файл и сразу увидеть результат.  

Если вы знакомы с базовым C# и имеете копию Aspose.Words, вы готовы. Дополнительные NuGet‑пакеты, помимо основной библиотеки, не требуются.

> **Pro tip:** Aspose.Words работает с .NET 6, .NET 7 и .NET Framework 4.6+. Выберите среду выполнения, соответствующую вашему проекту.

![draw rectangle word example](https://example.com/placeholder-image.png "draw rectangle word – grouped shapes in a Word file")

## draw rectangle word – Setting Up the Document

Прежде чем мы сможем **draw rectangle word**, нам нужен чистый холст. Класс `Document` — это холст; `DocumentBuilder` — наша кисть.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Эти две строки создают свежий документ `.docx` в памяти. На диск ничего не записывается, что позволяет экспериментировать, не захламляя файловую систему.

## How to Add Shapes – Creating a GroupShape Container

Когда вам нужно, чтобы **multiple shapes word** вели себя как единое целое — перемещались вместе, вращались вместе — вы помещаете их в `GroupShape`. Представьте группу как папку, содержащую другие фигуры.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Зачем нужна группа? Потому что позже вы захотите **add rectangle shape** и **add line shape**, а затем переместить их вместе. Без группы пришлось бы позиционировать каждую фигуру отдельно.

## add rectangle shape – Inserting a Rectangle Inside the Group

Теперь, когда контейнер существует, давайте **add rectangle shape**. Прямоугольник — это `Shape` с `ShapeType`, равным `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Обратите внимание, что значения `Left` и `Top` задаются относительно начала группы, а не страницы. Это упрощает точное выравнивание фигур. Прямоугольник появится рядом с верхним‑левым углом группы.

## add line shape – Adding a Line to the Same Group

Линия — это тоже `Shape`, но её `ShapeType` — `Line`. Мы разместим её под прямоугольником.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Поскольку высота линии равна нулю, свойство `Top` определяет её вертикальное положение. Ширина (`Width`) задаёт длину линии по горизонтали.

## multiple shapes word – Inserting the Group into the Document Body

У нас есть группа, содержащая **add rectangle shape** и **add line shape**. Последний шаг — поместить её в документ.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` вставляет группу точно в том месте, где сейчас находится `DocumentBuilder`. Если нужно разместить её в конкретном абзаце, сначала переместите builder с помощью `builder.MoveToParagraph(index)`.

## Saving the Result – Seeing the draw rectangle word Output

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Откройте сгенерированный файл в Microsoft Word, и вы увидите одну группу, содержащую прямоугольник и линию. Вы можете кликнуть по группе, перетащить её или даже изменить размер — все фигуры перемещаются вместе. Это и есть сила **multiple shapes word**.

### Expected Output

- Файл `.docx` с именем `GroupShape.docx`.  
- Одна страница с группированным прямоугольником (120 × 80 pt) в верхнем‑левом углу.  
- Горизонтальная линия (150 pt) сразу под прямоугольником.  
- Обе фигуры выбираются как один объект.

Если дважды кликнуть по группе, Word позволит редактировать каждую фигуру отдельно — идеально для тонкой настройки.

## Common Questions & Edge Cases

**Что делать, если нужно больше двух фигур?**  
Продолжайте вызывать `group.AppendChild(yourShape)` для каждого дополнительного объекта. Группа может содержать произвольное количество фигур, что делает её идеальной для сложных диаграмм.

**Можно ли изменить цвет заливки прямоугольника?**  
Конечно. После создания прямоугольника задайте `rectangle.FillColor = System.Drawing.Color.LightBlue;`. Это работает для любой фигуры, поддерживающей заливку.

**Нужно ли устанавливать `Height = 0` для линии?**  
Да, для прямой горизонтальной линии высота должна быть нулевой. Для вертикальной линии задайте `Width = 0` и положительное значение `Height`.

**Будет ли работать с файлами .doc (Word 97‑2003)?**  
Aspose.Words может сохранять в старый формат `.doc`, но некоторые современные возможности фигур могут быть ограничены. Для полной точности используйте `.docx`.

**Как повернуть всю группу?**  
Установите `group.Rotation = 45;` (градусы) перед вставкой. Поворот применяется ко всем дочерним фигурам.

## Recap – How to Add Shapes in Word Programmatically

- **draw rectangle word** начинается с создания `Document` и `DocumentBuilder`.  
- Создайте **GroupShape** для удержания **multiple shapes word**.  
- **add rectangle shape** и **add line shape** добавляются в группу.  
- Вставьте группу в тело с помощью `builder.InsertNode`.  
- Сохраните файл и откройте его, чтобы убедиться в визуальном результате.

Это весь процесс, упакованный в один простой и понятный пример кода.

## Next Steps & Related Topics

Теперь, когда вы знаете **how to add shapes**, рассмотрите следующие темы:

- **add rectangle shape** с закруглёнными углами (`ShapeType.Rectangle` + `CornerRadius`).  
- Стилизация линий различными шаблонами штрихов (`line.LineFormat.DashStyle`).  
- Встраивание изображений рядом с фигурами для более богатых отчётов.  
- Использование **multiple shapes word** для построения блок‑схем или простых UML‑диаграмм.  

Каждая из этих тем естественно продолжает фундамент, который мы заложили, и следует той же схеме — создание фигур, их настройка и, при необходимости, группировка.

---

Счастливого кодинга! Если столкнётесь с нюансами или захотите поделиться интересным случаем применения, оставляйте комментарий ниже. Ваши отзывы помогают всем нам освоить искусство **draw rectangle word** и не только.


## What Should You Learn Next?


Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом пособии. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, чтобы вы могли освоить дополнительные возможности API и исследовать альтернативные подходы в своих проектах.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}