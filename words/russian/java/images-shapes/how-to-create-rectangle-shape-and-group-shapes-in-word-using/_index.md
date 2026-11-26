---
category: general
date: 2026-11-18
description: Узнайте, как создать прямоугольную форму в документе Word с помощью C#.
  Руководство также охватывает установку размера формы, установку её позиции и группировку
  форм в Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: ru
lastmod: 2026-11-18
og_description: Создайте прямоугольную форму в файле Word с помощью C# и научитесь
  задавать размеры формы, устанавливать её позицию и группировать формы в Word.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Создайте прямоугольную форму и сгруппируйте формы в Word с помощью C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Как создать прямоугольную форму и сгруппировать формы в Word с помощью C#
url: /ru/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать прямоугольную форму и сгруппировать формы в Word с помощью C#

Если вам нужно **создать прямоугольную форму** в документе Word, этот учебник покажет вам полное, готовое к запуску решение. Вы увидите, как задать размер формы, задать позицию формы и сгруппировать формы в Word, чтобы они вели себя как один объект.

Работа с формами является распространённой задачей при программной генерации отчетов, счетов или диаграмм. К концу этого руководства вы сможете создать файл `.docx`, содержащий прямоугольник, эллипс и сгруппированный контейнер — всё создано с помощью Aspose.Words for .NET.

## Требования

- .NET 6.0 SDK или новее (код также работает с .NET Framework 4.7+)
- NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Редактор кода или IDE (Visual Studio, VS Code, Rider и т.д.)

Дополнительные библиотеки не требуются.

## Как создать прямоугольную форму и сгруппировать формы в Word

Основные шаги:

1. **Создать пустой документ** и `DocumentBuilder`.
2. **Вставить `GroupShape`**, который будет содержать отдельные формы.
3. **Создать прямоугольную форму**, задать её размеры и добавить в группу.
4. **Создать форму‑эллипс**, задать её размер и позицию, и добавить в группу.
5. **Сохранить** документ.

Каждый шаг объясняется ниже, а полный исходный код следует за объяснением.

### Шаг 1: Инициализация документа и builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` представляет весь файл Word, а `DocumentBuilder` предоставляет удобный API для вставки содержимого. Инициализация их обязательна перед тем, как добавить любые формы.

### Шаг 2: Вставка групповой формы

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

`GroupShape` работает как контейнер; все дочерние формы перемещаются вместе. Это рекомендуемый способ **группировать формы в Word**, когда нужны коллективные преобразования (например, перемещение, вращение или удаление).

### Шаг 3: Создание прямоугольника и задание его размера

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Здесь мы **создаём прямоугольную форму** и **задаём размер формы**, присваивая `Width` и `Height`. В Aspose.Words размеры задаются в пунктах (1 pt ≈ 1/72 in). Явное задание размеров гарантирует, что прямоугольник будет выглядеть точно так, как задумано.

### Шаг 4: Создание эллипса, задание размеров и позиционирование

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

Параметры **set shape dimensions** для эллипса одинаковы по ширине и высоте, что создаёт идеальный круг. Свойство `Left` демонстрирует **set shape position**: эллипс начинается на 120 pt правее начала группы, поэтому не перекрывает прямоугольник.

### Шаг 5: Сохранить документ

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Сохранение записывает файл Word на диск. Вы можете открыть `GroupShape.docx` в Microsoft Word, чтобы убедиться, что прямоугольник и эллипс сгруппированы и расположены правильно.

## Задание размеров и габаритов формы – более подробно

- **Points vs. inches**: 72 pt = 1 in. Если вы предпочитаете дюймы, умножьте на 72 (например, `2.5 * 72` для 2.5 in).
- **Automatic scaling**: Если опустить `Width` или `Height`, форма использует размер по умолчанию. Явно **set shape size**, чтобы избежать сюрпризов в разметке.
- **Aspect ratio**: Для форм, таких как `Ellipse`, равные `Width` и `Height` сохраняют круглую форму.

## Позиционирование формы в Word

Свойства `Left` и `Top` управляют смещением формы внутри её контейнера (группы или страницы). Положительные значения перемещают форму вправо/вниз; отрицательные — влево/вверх. При группировке позиции задаются относительно начала группы, что упрощает расчёты разметки.

## Группировка форм в Word с помощью Aspose.Words

Группировка необходима, когда вы хотите, чтобы несколько форм вели себя как единый объект. Объект `GroupShape`:

- Поддерживает `AppendChild` для добавления любой `Shape` (прямоугольник, эллипс, изображение и т.д.).
- Позволяет перемещать, вращать или удалять всю группу одним вызовом.
- Сохраняет позиции дочерних форм относительно группы, упрощая работу со сложными диаграммами.

**Pro tip:** После добавления всех дочерних форм вы можете скорректировать `Width`, `Height`, `Left` и `Top` группы, чтобы переместить всю коллекцию за один шаг.

## Полный исполняемый пример

Ниже приведена полная программа, которую вы можете скопировать, вставить и запустить. Она включает все директивы `using`, метод `Main` и комментарии, объясняющие каждую строку.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Expected output:** После выполнения программы файл `GroupShape.docx` появится в папке выполнения. Открывая его в Word, вы увидите прямоугольник (100 pt × 50 pt) слева и эллипс (80 pt × 80 pt), расположенный на 120 pt правее, оба внутри единого сгруппированного объекта.

![Документ Word с группированным прямоугольником и эллипсом](grouped_shapes.png){: .center alt="Скриншот документа Word, показывающего группированный прямоугольник и эллипс, созданный с помощью C#" }

*Изображение выше иллюстрирует конечный результат; прямоугольник и эллипс можно выбрать как одну группу.*

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| **Можно ли добавить более двух форм?** | Да. Вызывайте `group.AppendChild(yourShape)` для каждой дополнительной формы. |
| **Что если мне нужно повернуть группу?** | Используйте `group.RotationAngle = 45;` (градусы) после добавления всех дочерних элементов. |
| **Как изменить цвет фона группы?** | Установите `group.FillColor = System.Drawing.Color.LightGray;`. |
| **Будет ли это работать с файлами .doc?** | Aspose.Words поддерживает `.doc` и `.docx`. Тот же код работает; просто измените расширение файла в `Save`. |
| **Есть ли влияние на память при группировке большого количества форм?** | Само по себе группирование добавляет минимальные накладные расходы. Основная проблема — общее количество форм; держите его в разумных пределах для больших документов. |

## Заключение

В этом учебнике вы узнали, как **создать прямоугольную форму** в файле Word с помощью C#, как **задать размер формы**, **задать габариты формы**, **задать позицию формы**, а также как **группировать формы в Word** с помощью Aspose.Words. Полный пример демонстрирует чистый, поддерживаемый подход, который можно расширить для более сложных диаграмм, графиков или пользовательской графики.

Далее вы можете изучить:

- Добавление текста внутри форм (`Shape.TextPath.Text = "Hello"`).
- Вставка изображений в `GroupShape`.
- Экспорт сгруппированных форм в PDF с помощью `doc.Save("output.pdf")`.

Не стесняйтесь экспериментировать с различными размерами, позициями и дополнительными типами форм, чтобы соответствовать потребностям вашего проекта. Приятного кодинга!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Создать групповую форму в документе Word с использованием Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}