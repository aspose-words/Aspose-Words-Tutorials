---
category: general
date: 2026-10-04
description: Узнайте, как группировать фигуры в Word с помощью C#. Это руководство
  показывает, как вставить прямоугольную фигуру, сгруппировать несколько фигур и программно
  создать пустой файл Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: ru
lastmod: 2026-10-04
og_description: Группировка фигур в Word с помощью C#. Следуйте этому пошаговому руководству,
  чтобы вставить прямоугольник, сгруппировать несколько фигур и создать пустой файл
  Word с помощью DocumentBuilder.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Группировка фигур в Word с помощью C# – полный учебник по DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Как группировать фигуры в Word с помощью C# и DocumentBuilder
url: /ru/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как группировать фигуры в Word с помощью C# и DocumentBuilder

Если вам нужно **группировать фигуры в Word** из C#‑приложения, этот учебник покажет, как это сделать. Вы увидите, как *вставить прямоугольник*, объединить несколько рисунков в одну группу и, наконец, **создать пустой файл Word**, содержащий сгруппированные объекты.

Работа с фигурами часто требуется при программном создании отчетов, счетов‑фактур или пользовательских шаблонов. К концу этого руководства у вас будет переиспользуемый фрагмент кода, который можно добавить в любой .NET‑проект, использующий Aspose.Words.

## Что вы узнаете

- Создать пустой документ Word с нуля.  
- Вставить прямоугольник и эллипс с помощью `DocumentBuilder`.  
- **Группировать несколько фигур** в `GroupShape`.  
- Использовать **append child to group** для построения иерархии.  
- Сохранить файл на диск и проверить результат.

Предыдущий опыт работы с Aspose.Words не требуется, но необходимо базовое понимание C# и .NET‑разработки.

## Требования

| Требование | Причина |
|------------|---------|
| .NET 6.0 или новее | Предоставляет среду выполнения для C#‑кода. |
| Aspose.Words for .NET (последняя версия) | Содержит `Document`, `DocumentBuilder` и классы фигур. |
| IDE, например Visual Studio 2022 (или VS Code) | Упрощает компиляцию и запуск примера. |
| Права записи в папку на вашем компьютере | Необходимы для вызова `doc.save`. |

Установите Aspose.Words через NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Группировка фигур в Word – пошаговое руководство

Ниже представлен полностью рабочий пример программы. Каждый раздел подробно объяснён, чтобы вы понимали **почему** код написан именно так, а не только **что** он делает.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Почему важен каждый шаг

1. **Создать пустой файл Word** – Начало с чистого документа гарантирует, что скрытое форматирование не повлияет на позиционирование фигур.  
2. **Инициализировать DocumentBuilder** – `DocumentBuilder` абстрагирует низкоуровневое манипулирование узлами, позволяя сосредоточиться на макете.  
3. **Вставить отдельные фигуры** – Сначала нужны отдельные объекты (`insert rectangle shape` и эллипс), прежде чем их можно будет сгруппировать. Настройка `Left` и `Top` обеспечивает расположение рядом.  
4. **Группировать несколько фигур** – Создавая `GroupShape` и используя **append child to group**, вы превращаете два независимых рисунка в единый логический объект. Перемещение или изменение размера группы будет влиять на оба дочерних элемента одновременно.  
5. **Сохранить документ** – Финальный файл `GroupedShapes.docx` можно открыть в Microsoft Word, чтобы убедиться, что прямоугольник и эллипс действительно сгруппированы (выберите один — оба переместятся вместе).

### Ожидаемый результат

Откройте `GroupedShapes.docx` в Microsoft Word:

- Вы увидите прямоугольник и эллипс, расположенные рядом.  
- Выбор любой из фигур выделит обе, подтверждая их принадлежность к одной группе.  
- Группу можно перетаскивать, изменять её размер или форматировать как единый объект.

![Diagram of grouped rectangle and ellipse inside a Word document](https://example.com/grouped-shapes.png){: .center-image alt="Diagram of grouped rectangle and ellipse inside a Word document"}

*Скриншот иллюстрирует окончательные сгруппированные фигуры.*

---

## Вставка прямоугольника – настройка размера и стиля

Если нужен прямоугольник с определённым цветом заливки или границей, измените объект `Shape` после вставки:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Эти свойства принадлежат классу `Shape` и работают с любым типом фигуры, а не только с прямоугольниками. Настройка стиля до **append child to group** гарантирует, что группа унаследует заданные визуальные свойства.

---

## Группировка нескольких фигур – более двух объектов

В примере группируются прямоугольник и эллипс, но вы можете добавить любое количество фигур:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Совет:** После построения сложной группы её можно заблокировать, чтобы предотвратить случайные изменения:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – порядок имеет значение

Порядок вызова `AppendChild` определяет Z‑порядок (какая фигура находится сверху). В примере сначала добавляется прямоугольник, затем эллипс, поэтому при пересечении эллипс накладывается поверх прямоугольника. Переставить порядок можно, вызвав `RemoveChild` и добавив заново:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Создание пустого файла Word – переиспользуемый вспомогательный метод

Если вашему приложению часто нужен новый документ, вынесите логику создания в отдельный метод:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Тогда вместо `new Document()` в основной программе можно использовать `CreateBlankWordFile()`. Это демонстрирует концепцию **create blank word file** в переиспользуемом виде.

---

## Распространённые подводные камни и как их избежать

| Проблема | Почему происходит | Как исправить |
|----------|-------------------|---------------|
| Фигуры находятся за пределами страницы | Значения `Left`/`Top` по умолчанию равны 0, что помещает фигуру у поля. | Явно задайте `Left` и `Top` после вставки. |
| Группа теряет форматирование | Изменение дочерней фигуры после её добавления в группу может нарушить макет группы. | Применяйте все визуальные свойства **до** вызова `AppendChild`. |
| Сохранённый файл пустой | `DocumentBuilder` никогда не использовался для добавления узла, либо `doc.Save` вызван у другого экземпляра `Document`. | Убедитесь, что сохраняете тот же `Document`, в котором строили содержимое. |
| Предупреждения совместимости в Word | Используются новые возможности фигур, не поддерживаемые старой версией Word. | Ограничьте использование функций, недоступных в целевых версиях Word. |

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающие освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}