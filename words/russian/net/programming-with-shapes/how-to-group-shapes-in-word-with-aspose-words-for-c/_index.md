---
category: general
date: 2026-09-21
description: Узнайте, как группировать фигуры в Word с помощью Aspose.Words для C#.
  Это пошаговое руководство охватывает создание, позиционирование и сохранение сгруппированных
  фигур.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: ru
lastmod: 2026-09-21
og_description: Группируйте фигуры в Word с помощью Aspose.Words для C#. Следуйте
  этому краткому руководству, чтобы программно создавать, позиционировать и сохранять
  сгруппированные фигуры.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Группировка фигур в Word с помощью Aspose.Words – полное руководство по
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Как сгруппировать фигуры в Word с помощью Aspose.Words для C#
url: /ru/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как группировать фигуры в Word с помощью Aspose.Words для C#

Если вам необходимо **группировать фигуры в Word** программно, Aspose.Words делает это простым. В этом руководстве показано, как создать две прямоугольные фигуры, разместить их рядом, объединить их в `GroupShape` и сохранить результат в файл DOCX.

Вы увидите полностью готовый, исполняемый пример, объяснения, почему каждый шаг важен, и советы по работе с распространёнными краевыми случаями, такими как перекрывающиеся фигуры или динамический размер. К концу этого руководства вы сможете интегрировать группировку фигур в любой проект автоматизации Word.

## Необходимые условия

* .NET 6.0 (или новее) установлен – Aspose.Words поддерживает .NET Standard 2.0+, .NET Core и .NET Framework.  
* Действительная лицензия Aspose.Words for .NET (или временный оценочный ключ) – библиотека работает без лицензии, но добавляет водяной знак.  
* Visual Studio 2022 (или любой C# IDE) для компиляции и запуска примера.  

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words`.

## Как группировать фигуры в Word с помощью Aspose.Words

Ядром решения является объект **`GroupShape`**, который выступает контейнером для отдельных фигур. Ниже мы разбиваем процесс на понятные шаги.

### Шаг 1: Создать пустой документ и `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Зачем этот шаг?*  
`Document` представляет весь файл DOCX, а `DocumentBuilder` предоставляет цепочечные методы (например, `InsertShape`), которые автоматически размещают новые элементы в текущей позиции курсора.

### Шаг 2: Вставить первую прямоугольную фигуру

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Вызов `InsertShape` добавляет фигуру в документ и возвращает объект `Shape`, который можно дальше настраивать (цвет, граница и т.д.). Размер задаётся в пунктах (1 pt ≈ 1/72 in).

### Шаг 3: Вставить второй прямоугольник и сместить его

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Установка `Left` позиционирует фигуру относительно полей страницы. Смещение должно быть больше ширины первой фигуры (100 pt), чтобы избежать перекрытия; мы используем 120 pt, чтобы оставить небольшой зазор.

### Шаг 4: Создать `GroupShape` достаточного размера для обоих прямоугольников

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` принимает владеющий `Document` и размеры контейнера. Ширина контейнера должна превышать правый край самой удалённой фигуры; иначе вторая фигура будет обрезана.

### Шаг 5: Добавить отдельные фигуры в группу

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

Добавление перемещает фигуры во внутреннюю коллекцию группы. После этого вызова фигуры больше не являются независимыми объектами в дереве документа — они принадлежат группе.

### Шаг 6: Вставить сгруппированную фигуру обратно в документ

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` размещает весь `GroupShape` в том месте, где сейчас находится курсор. Если вам нужна группа в определённом абзаце, сначала переместите builder в этот абзац.

### Шаг 7: Сохранить документ

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

Полученный файл содержит два прямоугольника, которые ведут себя как один объект — их можно перемещать, изменять размер или удалять вместе в Microsoft Word.

## Полный исходный код

Объединение всех шагов вместе даёт автономную программу:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Ожидаемый результат:** При открытии *GroupedShapes.docx* в Microsoft Word отображаются два прямоугольника рядом, рассматриваемые как один выбираемый объект. Перетаскивание группы перемещает оба прямоугольника вместе.

## Распространённые варианты и краевые случаи

| Ситуация | Рекомендуемая корректировка |
|-----------|------------------------|
| **Более двух фигур** | Создайте дополнительные объекты `Shape`, разместите их соответствующим образом и добавьте каждый в тот же `GroupShape`. |
| **Динамический размер** | Вычислите ширину/высоту группы на основе максимальных значений `Right` и `Bottom` дочерних фигур. |
| **Разные типы фигур** | `ShapeType.Ellipse`, `ShapeType.Triangle` и т.д. можно вставлять тем же способом; контейнер группы не учитывает тип. |
| **Повернутые фигуры** | Установите `shape.Rotation = 45;` перед добавлением; поворот сохраняется внутри группы. |
| **Сохранение в PDF** | Вызовите `doc.Save("GroupedShapes.pdf");` — группа сохраняется при рендеринге PDF. |

**Совет:** После группировки вы всё ещё можете изменять отдельные фигуры, получая доступ к `group.GetChildNodes(NodeType.Shape, true)`. Это полезно, когда нужно изменить цвет заливки одного прямоугольника, не разрывая группу.

## Как программно проверить группировку

Если вам нужно убедиться, что фигуры правильно сгруппированы (например, в модульных тестах), изучите иерархию узлов документа:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

Вывод должен быть:

```
Number of groups: 1
Children in first group: 2
```

Это подтверждает, что **группировка фигур в Word** была выполнена как ожидалось.

## Заключение

Теперь вы знаете, как **группировать фигуры в Word** с помощью Aspose.Words для C#. Процесс включает создание отдельных фигур, их позиционирование, обёртывание их в `GroupShape` и вставку группы обратно в документ. С полным примером выше вы можете расширить эту технику на любое количество фигур, разных типов или даже комбинировать её с текстовыми полями и изображениями.

Далее изучайте связанные темы, такие как **группировка фигур Aspose.Words**, **манипуляция фигурами Word в C#** и **вставка фигуры DocumentBuilder**, для более продвинутых сценариев автоматизации документов. Экспериментируйте с динамическим размером, условной группировкой и экспортом в PDF, чтобы полностью раскрыть возможности Aspose.Words.

## Что вам следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Вставка фигур в документы Word с помощью Aspose.Words для .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Создание прямоугольной фигуры в Word с Aspose.Words – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Учебник по теням фигур Aspose.Words – добавление тени к фигуре Word в C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}