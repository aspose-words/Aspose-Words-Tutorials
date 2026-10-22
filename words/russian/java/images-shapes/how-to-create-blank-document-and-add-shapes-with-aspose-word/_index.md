---
category: general
date: 2026-09-30
description: Создайте пустой документ и вставьте прямоугольник, эллипс, а также сгруппируйте
  несколько фигур в C# с использованием Aspose.Words. Узнайте, как вставлять фигуры
  и как создавать группы.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: ru
lastmod: 2026-09-30
og_description: Создайте пустой документ на C# и узнайте, как вставлять фигуры и группировать
  несколько фигур с помощью Aspose.Words. Следуйте пошаговому руководству.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Создайте пустой документ и сгруппируйте фигуры в C# – руководство Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Как создать пустой документ и добавить фигуры с помощью Aspose.Words в C#
url: /ru/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать пустой документ и добавить фигуры с помощью Aspose.Words в C#

Если вам нужно **создать пустой документ** и заполнить его графикой, это руководство покажет вам, как это сделать. Вы увидите, как **вставить прямоугольную фигуру**, добавить другие графические объекты и затем **группировать несколько фигур**, чтобы они вели себя как единый объект.

Работа с фигурами часто требуется при генерации контрактов, сертификатов или пользовательских отчетов. В этом учебнике вы изучите полный рабочий процесс — от инициализации документа до сохранения конечного файла, используя Aspose.Words API для .NET.

## Предварительные требования

Перед началом убедитесь, что у вас есть:

* .NET 6.0 (или новее) SDK установлен  
* Действительная лицензия Aspose.Words for .NET (бесплатная пробная версия подходит для этого примера)  
* IDE, например Visual Studio 2022 или Visual Studio Code  

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words`.

## Как создать пустой документ и работать с фигурами

Первый шаг — создать объект `Document`. Этот объект представляет Word‑файл в памяти и предоставляет доступ к `DocumentBuilder`, который является основным инструментом для вставки содержимого.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Почему это важно:** Пустой документ предоставляет чистое полотно. `DocumentBuilder` поддерживает текущую точку вставки, поэтому каждая добавляемая фигура автоматически размещается на соответствующей странице.

## Вставка прямоугольной фигуры и других фигур

Далее мы добавляем прямоугольник и эллипс. Оба вызова используют один и тот же метод `InsertShape`, который является рекомендуемым способом **how to insert shapes** в Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*Метод `InsertShape` автоматически позиционирует фигуру в текущем месте курсора.* Если требуется точное размещение, вы можете скорректировать `Shape.Left` и `Shape.Top` после вставки.

## Группировка нескольких фигур в один объект

Теперь мы объединяем прямоугольник и эллипс в одну логическую сущность. Группировка полезна, когда нужно переместить или изменить размер нескольких фигур одновременно.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Как это работает:** `InsertGroupShape` создает контейнер, который ведёт себя как любой другой `Shape`. Вызвав `AppendChild`, вы перемещаете существующие фигуры в контейнер, который автоматически обновляет их относительные координаты.

### Практический совет

Если позже понадобится **how to create group** программно для более чем двух фигур, просто повторите `AppendChild` для каждой дополнительной экземпляра `Shape`. Группа может содержать любое количество графических объектов, включая изображения, текстовые поля или даже другие группы.

## Полный пример – как вставить фигуры и сохранить документ

Ниже приведена полная, исполняемая программа, демонстрирующая каждый шаг, обсуждённый до сих пор. При запуске кода будет создан файл `ShapesDemo.docx`, содержащий прямоугольник, эллипс и сгруппированную фигуру.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Ожидаемый результат:** Открытие `ShapesDemo.docx` в Microsoft Word показывает одну страницу с синим прямоугольником, зелёным эллипсом и окружающей их серой рамкой, представляющей группу. Перемещение группы перемещает обе фигуры вместе, подтверждая, что операция **group multiple shapes** выполнена успешно.

## Часто задаваемые вопросы и обработка крайних случаев

| Question | Answer |
|----------|--------|
| *Что если мне нужны фигуры на определённой странице?* | Вызовите `builder.MoveToDocumentEnd();` перед вставкой фигур, либо используйте `builder.MoveToSection(sectionIndex);` для перехода к конкретному разделу. |
| *Можно ли добавить текст внутри сгруппированной фигуры?* | Да. Создайте `Shape` типа `ShapeType.TextBox`, настройте его текст и затем `AppendChild` его в `GroupShape`. |
| *Размеры фигур измеряются в пунктах или пикселях?* | Aspose.Words использует **points** (1 pt = 1/72 inch). Это обеспечивает одинаковый размер на принтерах и экранах. |
| *Как изменить вращение группы?* | Установите `groupShape.RotationAngle = 45;` (degrees). Все дочерние фигуры вращаются вокруг начала группы. |

## Заключение

Теперь вы знаете, как **create blank document**, **insert rectangle shape**, **how to insert shapes** такие как эллипсы, и **group multiple shapes** в один объект, используя Aspose.Words для .NET. Полный пример кода демонстрирует рекомендованный подход, а приведённые выше советы помогут адаптировать решение к более сложным сценариям, например, добавлению текстовых полей или вращению групп.

Готовы исследовать дальше? Попробуйте добавить в группу фигур изображение, поэкспериментируйте с разными цветами заливки или сгенерируйте многостраничный отчёт, где каждая страница содержит собственную сгруппированную диаграмму. Те же принципы применимы, поэтому вы можете масштабировать этот шаблон для любого проекта автоматизации документов.

## Что стоит изучить дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в собственных проектах.

- [Создать групповую фигуру в документе Word с помощью Aspose.Words для .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Вставка фигур в документы Word с помощью Aspose.Words для .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Создать пустой документ Word с Aspose.Words – пошаговое руководство](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}