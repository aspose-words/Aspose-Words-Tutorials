---
category: general
date: 2026-09-08
description: Узнайте, как группировать фигуры в Word с помощью DocumentBuilder, создать
  пустой документ Word и вставить прямоугольную форму всего за несколько строк кода
  на C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: ru
lastmod: 2026-09-08
og_description: Группировать фигуры в Word с помощью DocumentBuilder. Этот учебник
  показывает, как создать пустой документ Word, вставить прямоугольную форму и объединить
  фигуры в GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Группировка фигур в Word с помощью DocumentBuilder – полный пример на C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Как группировать фигуры в Word с помощью DocumentBuilder – пошаговое руководство
url: /ru/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как группировать фигуры в Word с помощью DocumentBuilder – пошаговое руководство

Если вам нужно **группировать фигуры в Word** программно, это руководство покажет полное решение на C#. Вы увидите, как **создать пустой документ Word**, использовать **DocumentBuilder** и **вставить прямоугольную фигуру**, а затем сгруппировать её с эллипсом. В результате получится один `GroupShape`, который можно перемещать, изменять размер или применять стиль как к единому объекту.

Это руководство охватывает всё, что необходимо знать для создания документа Word с группированными графическими элементами с помощью библиотеки Aspose.Words for .NET. К концу статьи у вас будет готовый проект, генерирующий `GroupedShapes.docx`, содержащий прямоугольник и эллипс, объединённые в одну фигуру.

## Предварительные требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.7.2+)
- NuGet‑пакет Aspose.Words for .NET (`Aspose.Words`) – версия 23.12 или новее
- IDE для C#, например Visual Studio 2022 или Visual Studio Code
- Базовые знания синтаксиса C# и объектно‑ориентированного программирования

> **Совет:** Установите NuGet‑пакет из командной строки, чтобы ваш проект оставался чистым:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Шаг 1: Создать пустой документ Word

Первой операцией является создание объекта `Document`, представляющего пустой файл Word, и `DocumentBuilder`, позволяющего добавлять содержимое.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Почему это важно:** `Document` предоставляет контейнер файла, а `DocumentBuilder` предлагает удобный API для вставки текста, изображений и фигур. Без `DocumentBuilder` вам пришлось бы вручную манипулировать деревом узлов документа, что склонно к ошибкам.

## Шаг 2: Вставить прямоугольную фигуру

Прямоугольник часто используется как базовый элемент диаграмм. Используйте `InsertShape` с `ShapeType.Rectangle` и укажите ширину и высоту в пунктах (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Почему это важно:** Установка `Left` и `Top` позиционирует прямоугольник точно на странице, что необходимо для последующего группирования с другими фигурами. Метод `InsertShape` автоматически добавляет фигуру в текущий абзац.

## Шаг 3: Вставить эллипс

Далее добавьте эллипс, который будет располагаться рядом с прямоугольником.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Почему это важно:** Использование другого `ShapeType` демонстрирует, как один и тот же API `DocumentBuilder` может создавать разнообразные графические элементы. Позиционирование эллипса так, чтобы он перекрывал прямоугольник, делает эффект группировки очевидным.

## Шаг 4: Сгруппировать две фигуры

`GroupShape` работает как контейнер. Добавив прямоугольник и эллипс как дочерние элементы, они будут вести себя как один объект.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Почему это важно:** Свойство `Bounds` указывает Word, где находится группа на странице. Добавляя дочерние фигуры, вы сохраняете их индивидуальное форматирование, одновременно позволяя выполнять коллективные трансформации (перемещение, вращение, изменение размера).

## Шаг 5: Сохранить документ

Наконец, запишите документ на диск. Вы можете изменить путь к любой папке по вашему выбору.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Когда вы откроете `GroupedShapes.docx` в Microsoft Word, вы увидите прямоугольник и эллипс, сгруппированные вместе. Выделив группу, обе фигуры будут подсвечены, и их можно будет перемещать или изменять размер как единое целое.

### Ожидаемый результат

- Файл Word с именем **GroupedShapes.docx**
- На первой странице **прямоугольник** (100 pt × 50 pt) в позиции (50, 50)
- **Эллипс** (80 pt × 80 pt) в позиции (200, 70)
- Обе фигуры находятся в **GroupShape** с ограничивающим прямоугольником 300 pt × 200 pt

## Распространённые варианты и граничные случаи

| Сценарий | Корректировка |
|----------|----------------|
| **Другой размер страницы** | Установите `document.Sections[0].PageSetup.PageWidth` и `PageHeight` перед вставкой фигур. |
| **Более двух фигур** | Создайте дополнительные объекты `Shape` и вызовите `groupShape.AppendChild(newShape)` для каждого. |
| **Применить цвет заливки** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Повернуть группу** | `groupShape.Rotation = 45;` (градусов) |
| **Экспорт в PDF** | После сохранения DOCX вызовите `document.Save("GroupedShapes.pdf");` |

## Полный исходный код (готов к запуску)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Скопируйте код в новый консольный проект, восстановите NuGet‑пакет Aspose.Words и запустите. Консоль подтвердит расположение файла, а открытие файла покажет сгруппированную графику.

## Заключение

Теперь вы знаете, **как группировать фигуры в Word** с помощью `DocumentBuilder` из Aspose.Words. В руководстве показано создание **пустого документа Word**, **вставка прямоугольной фигуры**, добавление эллипса и их объединение в `GroupShape`. Имея эту основу, вы сможете создавать более сложные диаграммы, блок‑схемы или пользовательскую графику непосредственно из C#.

### Что дальше?

- Изучите **как использовать DocumentBuilder** для таблиц, колонтитулов и нижних колонтитулов.
- Сочетайте **техники вставки прямоугольника в Word** с текстовыми полями для аннотированных диаграмм.
- Используйте **создание пустого документа Word** как шаблон для автоматической генерации отчетов.

Экспериментируйте с цветами, градиентами и дополнительными фигурами. Приятного кодинга!

## Что вам следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом пособии. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Создать групповую фигуру в документе Word с помощью Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Вставить фигуры в документы Word с помощью Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Создать прямоугольную фигуру в Word с помощью C# – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}