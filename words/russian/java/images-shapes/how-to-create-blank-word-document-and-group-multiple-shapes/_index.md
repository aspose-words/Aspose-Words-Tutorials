---
category: general
date: 2026-10-26
description: Создайте пустой документ Word на C# и узнайте, как вставить групповую
  форму, затем добавить прямоугольник в эту группу. Это руководство пошагово охватывает
  группировку нескольких форм.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: ru
lastmod: 2026-10-26
og_description: Создайте пустой документ Word на C# и посмотрите, как вставить группу,
  затем добавить прямоугольную форму. Овладейте группировкой нескольких фигур с полным
  примером кода.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: Создать пустой документ Word и сгруппировать несколько фигур – учебник C#
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Как создать пустой документ Word и сгруппировать несколько фигур
url: /ru/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать пустой документ Word и сгруппировать несколько фигур

Если вам нужно **создать пустой документ Word** программно, этот учебник покажет, как это сделать. Вы увидите, как вставить групповую фигуру, а затем **добавить прямоугольник** в эту группу, охватывая весь процесс от пустого документа до сгруппированного рисунка.

Работа с файлами Word часто подразумевает расположение нескольких рисунков вместе — представьте диаграмму, состоящую из множества фигур. К концу этого руководства вы сможете **группировать несколько фигур**, вставить **прямоугольную фигуру** и понять **как вставить группу** и **как добавить прямоугольник** чистым, переиспользуемым способом.

## Что вам понадобится

* .NET 6.0 или новее (код также работает с .NET Framework 4.6+)
* NuGet‑пакет **Aspose.Words for .NET** (`Install-Package Aspose.Words`)
* Базовые знания C# и среды Visual Studio IDE (подойдёт любая IDE)

> **Pro tip:** Aspose.Words работает полностью офлайн; после установки пакета подключение к Интернету не требуется.

## Шаг 1: Создать пустой документ Word

Первая операция — создать экземпляр пустого объекта `Document`. Этот объект представляет **пустой документ Word**, который позже будет обогащён фигурами.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Почему это важно:* `Document` без разделов и абзацев всё равно является корректным файлом .docx. Начало с чистого листа гарантирует, что скрытое форматирование не будет влиять на добавляемые позже фигуры.

## Шаг 2: Вставить групповую фигуру (how to insert group)

**Групповая фигура** выступает как контейнер, способный удерживать другие графические объекты. В Aspose.Words её создают с помощью `InsertGroupShape`.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*Зачем нужна группа?* Группировка позволяет перемещать, вращать или изменять размер нескольких фигур как единого целого. Это необходимо для диаграмм, где элементы должны оставаться выровненными.

## Шаг 3: Вставить прямоугольную фигуру (insert rectangle shape)

Теперь добавим прямоугольник в документ. Метод `InsertShape` возвращает объект `Shape`, который позже можно присоединить к группе.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*Почему прямоугольник?* Прямоугольники — наиболее часто используемый строительный блок для блок‑схем, макетов UI и графических заглушек. Размеры задаются в пунктах (1 pt ≈ 1/72 дюйма).

## Шаг 4: Добавить прямоугольник в группу (how to add rectangle)

Фигура, созданная через `InsertShape`, изначально находится непосредственно в теле документа. Чтобы сделать её частью группы, вызовите `AppendChild` у объекта `GroupShape`.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*Что происходит «под капотом»?* `AppendChild` перемещает узел прямоугольника из основной истории документа во внутреннюю коллекцию группы, сохраняя его размер и позицию относительно начала группы.

## Шаг 5: Сохранить документ

Наконец, запишите файл на диск. Откройте полученный `.docx` в Microsoft Word, чтобы увидеть сгруппированный прямоугольник.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Edge case:** Если планируется добавить в ту же группу другие фигуры (например, круги, линии), повторите **Шаг 3** и **Шаг 4** для каждой новой фигуры перед сохранением. Группа автоматически скорректирует свою ограничивающую рамку, чтобы охватить всех дочерних элементов.

## Как группировать несколько фигур — расширение примера

Ниже приведён короткий фрагмент кода, который добавляет вторую фигуру (эллипс) в ту же группу, демонстрируя **group multiple shapes** в одном документе.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

Когда откроете `GroupedShapeExample.docx`, вы увидите, что прямоугольник и эллипс перемещаются вместе при выборе группы в Word.

## Часто задаваемые вопросы и устранение неполадок

| Question | Answer |
|----------|--------|
| **Do I need a license for Aspose.Words?** | A free evaluation works without a license, but it adds a watermark. For production, apply a license to remove the watermark and unlock full performance. |
| **Can I position shapes precisely?** | Yes. After inserting a shape you can set `Shape.Left`, `Shape.Top`, `Shape.Width`, and `Shape.Height` properties. |
| **What if the rectangle disappears after saving?** | Ensure you call `group.AppendChild(rectangle)` *after* inserting the rectangle. Adding the shape to the document body first and then moving it into the group is required. |
| **Is it possible to group shapes across different sections?** | No. All shapes in a group must belong to the same story (section). Create separate groups per section if needed. |

## Итоги

Теперь вы знаете, как **создать пустой документ Word**, **вставить группу**, **добавить прямоугольник** и **группировать несколько фигур** с помощью Aspose.Words for .NET. Полный, готовый к запуску пример выше можно скопировать в консольное приложение и выполнить сразу.

## Следующие шаги

* Поэкспериментируйте с размерами и цветами **insert rectangle shape** (`rectangle.FillColor = Color.LightBlue;`).  
* Исследуйте другие типы фигур (`ShapeType.Polygon`, `ShapeType.Line`), чтобы обогатить свои диаграммы.  
* Узнайте, как конвертировать готовый `.docx` в PDF (`doc.Save("output.pdf");`) для распространения.  
* Погрузитесь в **how to add rectangle** в существующие документы, уже содержащие текст — используйте `DocumentBuilder.MoveTo`, чтобы разместить группу в нужном месте.

Не стесняйтесь адаптировать код под собственные задачи по отчётности или генерации диаграмм. Приятного кодинга!


## Что изучать дальше?


Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [How to create blank Word document and group shapes in C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [How to group shapes in Word and add shapes to Word document](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}