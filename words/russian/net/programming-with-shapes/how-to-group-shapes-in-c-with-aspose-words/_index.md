---
category: general
date: 2026-08-23
description: Узнайте, как группировать фигуры в C# с использованием Aspose.Words.
  Руководство также описывает, как вставлять прямоугольную фигуру и добавлять фигуры
  Word для сложных документов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: ru
lastmod: 2026-08-23
og_description: Как группировать фигуры в C# с помощью Aspose.Words. Следуйте этому
  полному руководству, чтобы вставить прямоугольную фигуру, добавить фигуры в Word
  и эффективно группировать несколько фигур.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: Как группировать фигуры в C# – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Как группировать фигуры в C# с помощью Aspose.Words
url: /ru/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как группировать фигуры в C# с помощью Aspose.Words

Если вам нужно **how to group shapes** в документе Word программно, этот учебник покажет точные шаги с использованием Aspose.Words для .NET. Независимо от того, создаёте ли вы генератор отчетов, движок шаблонов или инструмент для построения диаграмм, вы узнаете, как начать группу, вставить прямоугольную фигуру и добавить **add shapes word**‑уровневый контент, не покидая код.

Вы также увидите, как **group multiple shapes** вместе, что необходимо, когда требуется перемещать, вращать или стилизовать набор объектов как единое целое. Пример ниже работает с последним выпуском Aspose.Words 24.x и требует только .NET 6 или новее.

## Требования

- .NET 6 SDK (или любая версия .NET, поддерживаемая Aspose.Words)
- Visual Studio 2022 или VS Code
- NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Базовые знания C# и объектной модели Aspose.Words

> **Pro tip:** Используйте бесплатную оценочную лицензию Aspose, чтобы избежать ограничений водяного знака во время тестирования.

## Как группировать фигуры с помощью Aspose.Words

Ниже приведена полностью готовая к запуску программа, демонстрирующая **how to start group**, добавление прямоугольника и завершение группы. Код следует той же логической последовательности, что и ваш фрагмент, но добавляет контекст, обработку ошибок и комментарии для ясности.

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
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Почему важен каждый шаг

| Шаг | Назначение | Как относится к ключевым словам |
|------|------------|--------------------------------|
| **Create a new blank document** | Обеспечивает чистый холст для операций с фигурами. | Подготавливает сцену для **add shapes word** позже. |
| **Initialize DocumentBuilder** | Builder — основной API для вставки объектов. | Необходим перед тем, как вы сможете **how to start group**. |
| **StartGroupShape** | Начинает логический контейнер; все последующие фигуры становятся членами этой группы. | Прямой ответ на **how to start group**. |
| **InsertShape** (rectangle, ellipse, text) | Размещает отдельные фигуры внутри группы. Вызов прямоугольника удовлетворяет **insert rectangle shape**; вызов текстовой фигуры удовлетворяет **add shapes word**. | Демонстрирует **group multiple shapes**. |
| **EndGroupShape** | Завершает группу, позволяя перемещать или стилизовать её как единое целое. | Завершает рабочий процесс **how to group shapes**. |

## Вставка прямоугольной фигуры – более подробно

Метод `InsertShape` принимает перечисление `ShapeType`, ширину и высоту. Чтобы **insert rectangle shape** с пользовательским оформлением, вы можете расширить пример:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Почему стоит оформить?** Оформление гарантирует, что прямоугольник будет выделяться, когда группа позже будет перемещена. Это также демонстрирует, что свойства фигуры можно задать *до* закрытия группы.

## Добавление фигур уровня Word (**add shapes word**)

Если нужно встроить текст непосредственно в фигуру — часто называют «WordArt» или «текстовое поле» — используйте `ShapeType.TextPlainText`. После вставки вы можете записать текст в фигуру с помощью `DocumentBuilder.Writeln` или через свойство `TextBox` фигуры:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

Это удовлетворяет ключевому слову **add shapes word** и показывает, как текст может перемещаться вместе с группой.

## Группировка нескольких фигур — практические сценарии

Когда вы **group multiple shapes**, их можно рассматривать как один объект для позиционирования, вращения или масштабирования. Например, после закрытия группы вы можете переместить всю группу:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Или повернуть её:

```csharp
group.Rotation = 45; // degrees
```

Эти операции возможны только потому, что фигуры находятся в одном родительском контейнере.

## Обработка особых случаев

1. **Вложенные группы** — Aspose.Words поддерживает группы внутри групп. Чтобы создать вложенную группу, вызовите `StartGroupShape` снова перед вызовом `EndGroupShape` для внутренней группы.  
2. **Пустые группы** — Если вы начнёте группу, но не вставите ни одной фигуры, `EndGroupShape` всё равно создаст пустой контейнер. Это безвредно, но может слегка увеличить размер файла.  
3. **Совместимость** — Сгенерированный DOCX работает в Word 2010 и новее. Более старые версии могут игнорировать метаданные группировки, поэтому всегда тестируйте с целевой версией Word.

## Полный исходный файл для справки

Сохраните следующее как `Program.cs` в консольном проекте .NET. Код компилируется и запускается без изменений.

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
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Ожидаемый результат

Открытие `GroupedShapes.docx` в Microsoft Word покажет:

- Светло‑коралловый прямоугольник, эллипс и текстовое поле — все визуально объединённые.  
- Выбор любой части группы также выделяет всю группу (появляется единый ограничивающий прямоугольник).  
- Перемещение или вращение группы перемещает все три фигуры вместе.

## Часто задаваемые вопросы

**В: Можно ли группировать фигуры, уже существующие в документе?**  
О: Да. Получите существующие объекты `Shape`, вызовите `builder.StartGroupShape()`, повторно вставьте их с помощью `builder.InsertShape(existingShape)`, затем вызовите `EndGroupShape()`.

**В: Влияет ли группировка на нижележащий XML?**  
О: Aspose.Words добавляет элемент `<w:grpSp>`, содержащий каждый `<w:sp>` узел фигуры. Это полностью соответствует спецификации Office Open XML.

**В: Что делать, если позже понадобится разгруппировать?**  
О: Прямого API «ungroup» нет, но можно пройтись по дочерним фигурам группы (`group.GroupShape.Children`) и скопировать их в тело документа.

## Следующие шаги

Теперь, когда вы знаете **how to group shapes**, рассмотрите изучение связанных тем:

- **Apply complex formatting to grouped shapes** — узнайте, как задавать градиентные заливки, тени и стили линий.  
- **Export grouped shapes as images** — используйте `Shape.GetShapeRenderer().Save(...)` для растрирования группы.  
- **Create dynamic diagrams** — комбинируйте позиционирование, управляемое данными, с группировкой для автоматической генерации блок‑схем.

Каждый из этих пунктов опирается на основу, изложенную здесь, и поможет вам создавать более богатые и интерактивные документы Word.

---

*Счастливого кодинга! Если этот гид оказался полезным, поделитесь им с коллегами или поставьте звёздочку репозиторию, содержащему пример проекта.*

## Что следует изучить дальше?


Ниже представлены учебники, охватывающие тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}