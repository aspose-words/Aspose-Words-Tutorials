---
category: general
date: 2026-10-23
description: Узнайте, как вставлять эллипс и как добавлять прямоугольную форму в Word
  с помощью Aspose.Words. Включает перемещение курсора к форме и создание групповой
  формы.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: ru
lastmod: 2026-10-23
og_description: Как вставить эллипс и как добавить прямоугольник в Word с помощью
  Aspose.Words. Следуйте пошаговому руководству, чтобы переместить курсор к фигуре
  и создать групповую фигуру.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Как вставить эллипс и прямоугольник в группу фигур в Word
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Как вставить эллипс и прямоугольник в групповую форму с помощью Aspose.Words
url: /ru/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как вставить эллипс и прямоугольник в группу фигур с Aspose.Words

Если вам нужно узнать **how to insert ellipse** в документ Word программно, это руководство показывает полный процесс. Вы также увидите **how to add rectangle** shape, узнаете **move cursor to shape**, и откроете **how to create group shape**, который содержит несколько графических объектов.

Автоматизация Word часто требует точного позиционирования графических объектов. К концу этого руководства вы сможете создать файл `.docx`, содержащий сгруппированный прямоугольник и эллипс, готовый для дальнейшего стилизации или экспорта. Не требуются внешние инструменты, кроме библиотеки Aspose.Words for .NET и среды разработки .NET.

## Требования

* .NET 6.0 или более поздняя версия, установленная на вашем компьютере.  
* Aspose.Words for .NET (пакет NuGet `Aspose.Words`) добавлен в ваш проект.  
* Базовые знания синтаксиса C# и работа в Visual Studio (или любой другой IDE).

Эти требования гарантируют, что код скомпилируется без дополнительной настройки.

## Как создать групповую фигуру в Word

Групповая фигура выступает в роли контейнера, позволяющего перемещать, вращать или форматировать несколько фигур как единый объект. Ниже представленный код создаёт группу фиксированного размера (300 × 200 пунктов) и подготавливает документ для дальнейших операций рисования.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Почему этот шаг важен*: Групповая фигура определяет локальную систему координат. Все фигуры, добавленные после перемещения курсора в группу, будут позиционироваться относительно начала группы, что упрощает расчёты раскладки.

## Как добавить прямоугольник в Word

Теперь, когда группа существует, вы можете **insert rectangle shape** внутри неё. Прямоугольник будет служить фоном или визуальным заполнителем для другого контента.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Explanation*: `MoveTo(group)` сообщает построителю, что активная точка вставки находится в группе. Без перемещения курсора `InsertShape` добавит прямоугольник в основное тело документа, а не в группу.

## Как вставить эллипс

С прямоугольником на месте вы теперь можете продемонстрировать **how to insert ellipse**. Эллипс будет центрирован в той же группе, при необходимости перекрывая прямоугольник.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Why the cursor must be moved*: Каждый вызов `InsertShape` учитывает текущее положение курсора. Повторный вызов `MoveTo(group)` гарантирует, что эллипс также станет дочерним элементом группы, сохраняя задуманную иерархию.

## Переместить курсор к фигуре перед вставкой дополнительных объектов

Если вам понадобится добавить ещё фигуры позже, всегда **move cursor to shape** перед каждой вставкой. Такой подход предотвращает случайное размещение объектов за пределами группы.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Tip*: Повторное использование `MoveTo(group)` дешево по ресурсам и повышает читаемость кода. Это также упрощает будущую поддержку, поскольку контекст вставки явно указан.

## Сохранить документ

Наконец, сохраняем документ на диск. В примере файл сохраняется как `GroupShape.docx` в указанной вами папке.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

При открытии сохранённого файла в Microsoft Word вы увидите одну группу, содержащую прямоугольник и эллипс, оба правильно расположенные.

### Ожидаемый результат

* Файл `.docx` с именем `GroupShape.docx`.  
* Внутри документа — сгруппированный графический объект размером 300 × 200 пунктов.  
* Внутри группы:  
  * Прямоугольник (100 × 50 пунктов), расположенный в начале группы.  
  * Эллипс (80 × 80 пунктов), перекрывающий прямоугольник.  
  * Любые дополнительные фигуры, добавленные после перемещения курсора.

## Распространённые варианты и граничные случаи

| Situation | Recommended approach |
|-----------|----------------------|
| **Разные размеры единиц** | Aspose.Words использует пункты (1 pt = 1/72 in). Преобразуйте сантиметры или дюймы в пункты перед вызовом `InsertShape`. |
| **Вращение фигур внутри группы** | После вставки фигуры получите её объект `ShapeBase` и задайте `ShapeBase.RotationAngle`. |
| **Добавление текста внутри фигуры** | Используйте `ShapeBase.AppendChild(new Paragraph(document))`, а затем добавьте `Run` с нужным текстом. |
| **Сохранение в PDF вместо DOCX** | Вызовите `document.Save("GroupShape.pdf", SaveFormat.Pdf);` — иерархия группы сохраняется в PDF‑выводе. |

Эти варианты демонстрируют, что одна и та же логика **how to insert ellipse** может быть адаптирована для множества реальных сценариев.

## Полезные советы

* **Reuse the same `DocumentBuilder` instance** — это уменьшает нагрузку на память и сохраняет состояние документа согласованным.  
* **Validate shape dimensions** — чрезвычайно большие ширины или высоты могут вызвать проблемы отображения в старых версиях Word.  
* **Group before styling** — применение заливок или стилей линий к группе после добавления всех дочерних элементов обеспечивает единообразный внешний вид.

## Заключение

Теперь вы знаете, как **how to insert ellipse** и **how to add rectangle** shape внутри группового контейнера в документе Word с помощью Aspose.Words. Последовательное **move cursor to shape** перед каждой вставкой сохраняет чистую иерархию и предотвращает случайное размещение. Полный пример компилируется, запускается и создаёт сгруппированную фигуру, которую можно дальше настраивать или экспортировать.

Готовы исследовать дальше? Попробуйте комбинировать эту технику с **how to create group shape** для сложных диаграмм или поэкспериментировать с **insert rectangle shape word** вместе с текстовыми полями для создания насыщенных отчётов. Happy coding!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [How to create blank Word document and add a hidden ellipse shape in C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [How to create group shape docx and add interactive controls in C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}