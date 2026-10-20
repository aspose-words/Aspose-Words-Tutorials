---
category: general
date: 2026-09-18
description: Создайте прямоугольную фигуру в документе Word с помощью C#. Узнайте,
  как добавить несколько фигур, добавить фигуры в группу и вставить групповую фигуру
  с помощью Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: ru
lastmod: 2026-09-18
og_description: Создайте прямоугольную форму в файле Word с помощью C#. Это руководство
  показывает, как добавить несколько фигур, добавить фигуры в группу и вставить групповую
  фигуру с использованием Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Создать прямоугольник и сгруппировать формы в C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Создать прямоугольную форму и сгруппировать несколько форм в C#
url: /ru/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создать прямоугольную форму и сгруппировать несколько форм в C#

Если вам нужно **создать прямоугольную форму** в документе Word, этот учебник показывает полное решение. Вы увидите, как **добавлять несколько форм**, **добавлять формы в группу** и **вставлять групповую форму** с использованием Aspose.Words API для .NET.

Работа с формами является распространённой задачей при программном создании отчётов, контрактов или маркетинговых материалов. К концу этого руководства у вас будет исполняемое консольное приложение C#, которое создаёт файл `.docx`, содержащий прямоугольник, эллипс и группу, включающую обе формы.

Единственными предварительными требованиями являются современный .NET SDK (6.0 или новее) и лицензированная копия Aspose.Words для .NET. Дополнительные инструменты не требуются.

## Предварительные требования

- .NET 6.0 SDK или новее  
- Aspose.Words для .NET (пакет NuGet `Aspose.Words`)  
- Базовое знакомство с синтаксисом C#  

Вы можете установить пакет с помощью следующей команды:

```bash
dotnet add package Aspose.Words
```

## Шаг 1: Создать прямоугольную форму с помощью Aspose.Words

Первый шаг — создать объект `Shape` типа `Rectangle`. Этот объект представляет визуальный прямоугольник, который появится в документе.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Почему это важно:** `ShapeType.Rectangle` указывает Aspose.Words отрисовать геометрический прямоугольник. Установка `Width` и `Height` определяет его размер в пунктах (1 пункт = 1/72 дюйма). Добавление цветов заливки и контура делает форму видимой без необходимости дополнительного стилирования.

## Шаг 2: Добавить несколько форм в документ

После прямоугольника вы можете создать любое количество дополнительных форм. В этом примере мы добавляем эллипс, чтобы продемонстрировать, как работает **добавление нескольких форм**.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Почему это важно:** Каждый вызов `new Shape` создаёт независимый объект рисунка. Вставляя их последовательно, вы формируете коллекцию форм, которые позже можно группировать или позиционировать отдельно.

## Шаг 3: Добавить формы в группу

Группировка форм упрощает управление макетом, поскольку группа ведёт себя как один узел. Этот шаг показывает, как **добавлять формы в группу** с помощью `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Почему это важно:** `GroupShape` работает как контейнер. Когда вы перемещаете, вращаете или изменяете размер группы, все дочерние формы автоматически следуют за ней. Ограничивающая рамка (200 × 200 пунктов) определяет координатное пространство для дочерних форм.

## Шаг 4: Вставить групповую форму в документ

Теперь, когда группа содержит прямоугольник и эллипс, вам нужно **вставить групповую форму** в нужное место. Builder уже разместил пустую группу, но при необходимости её можно вставить и в другое место.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Почему это важно:** Настройка `Left` и `Top` перемещает всю группу внутри страницы. Сохранение документа записывает иерархию форм в файл `.docx`, который можно открыть в Microsoft Word, LibreOffice или любом совместимом просмотрщике.

## Полный исполняемый пример

Ниже представлен полный код программы, объединяющий все шаги. Скопируйте код в новый консольный проект и запустите его, чтобы сгенерировать `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Ожидаемый результат:**  
Открытие `GroupShapeExample.docx` показывает одну группу, содержащую светло‑голубой прямоугольник и светло‑коралловый эллипс, оба расположены внутри контейнера размером 200 × 200 пунктов. Группу можно выбрать как один объект в Word, подтверждая, что **добавление форм в группу** выполнено успешно.

## Распространённые варианты и граничные случаи

| Ситуация | Рекомендованная корректировка |
|-----------|------------------------|
| Разные типы форм (например, `ShapeType.Line`) | Создайте форму с нужным `ShapeType` и задайте её геометрию соответствующим образом. |
| Необходимо повернуть форму | Используйте `shape.Rotation = 45;` (градусы) перед добавлением её в группу. |
| Большие документы с множеством групп | Переиспользуйте один экземпляр `DocumentBuilder`; избегайте создания нового builder'а для каждой группы, чтобы уменьшить нагрузку на память. |
| Сохранение в PDF вместо DOCX | Вызовите `doc.Save("output.pdf", SaveFormat.Pdf);` после вставки группы. |

**Совет профессионала:** Всегда задавайте явные значения `Left` и `Top` для группы, когда требуется точное размещение. Если их опустить, группа наследует текущую позицию курсора builder'а, что может привести к неожиданным результатам макета.

## Заключение

Теперь вы знаете, как **создавать прямоугольную форму**, **добавлять несколько форм**, **добавлять формы в группу** и **вставлять групповую форму** в документ Word с помощью C#. Полный пример демонстрирует весь процесс от создания документа до сохранения конечного файла.  

Далее изучайте связанные темы, такие как **позиционирование форм относительно текста**, **применение обтекания текстом** и **экспорт сгруппированных форм в PDF**. Эти расширения позволяют создавать сложные программные макеты документов с Aspose.Words.

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Создать прямоугольную форму в Word с помощью C# – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Создать групповую форму в документе Word с использованием Aspose.Words для .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Создать пустой документ Word с теневой прямоугольной формой – пошаговое руководство](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}