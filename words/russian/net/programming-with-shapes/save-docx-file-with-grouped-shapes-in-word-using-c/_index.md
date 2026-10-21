---
category: general
date: 2026-08-04
description: Сохраняйте файл docx программно, добавляя прямоугольный объект и группируя
  формы в Word. Узнайте, как задавать размеры формы и создавать текстовое поле программно.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: ru
lastmod: 2026-08-04
og_description: Сохранить файл docx с помощью C#, добавив прямоугольную форму, сгруппировав
  формы в Word, установив размеры формы и программно создав текстовое поле.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Сохранить файл docx с группированными фигурами в Word – пошаговое руководство
  на C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Сохранить файл docx с группированными объектами в Word с использованием C#
url: /ru/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохранить файл docx с группированными фигурами в Word с помощью C#

Если вам нужно **сохранить файл docx**, содержащий несколько фигур, расположенных вместе, это руководство покажет, как сделать это на C#. Вы узнаете, как **добавить прямоугольную фигуру**, сгруппировать несколько фигур в документе Word, **установить размеры фигур** и **создать текстовое поле программно**. Решение работает с последней версией Aspose.Words for .NET и запускается на .NET 6 или новее.

В руководстве последовательно рассматриваются все шаги — от настройки проекта до финального вызова `doc.Save`. В конце вы получите переиспользуемый фрагмент кода, который можно вставить в любой консольный или ASP.NET проект. Никакие внешние скрипты или ручное редактирование DOCX не требуются.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6 SDK (или новее) установлен.
* Действующая лицензия **Aspose.Words for .NET** (бесплатная пробная версия подходит для тестирования).
* Visual Studio 2022, VS Code или любая IDE, способная собирать проекты .NET.

Код использует только пространство имён Aspose.Words, поэтому дополнительные пакеты NuGet не требуются.

## Сохранить файл docx с группированными фигурами в Word

Суть решения — построить `GroupShape`, содержащий прямоугольник и текстовое поле, затем вставить группу в документ и вызвать `doc.Save`. Ниже процесс разбит на удобные части.

### 1. Создать новый документ и билдера

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Почему важен этот шаг* — Новый объект `Document` представляет пустой *.docx* файл. `DocumentBuilder` предоставляет высокоуровневые методы, такие как `InsertNode`, которые мы будем использовать для размещения групповой фигуры.

### 2. Добавить прямоугольную фигуру в группу

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Почему важен этот шаг* — Операция **add rectangle shape** демонстрирует, как задать визуальный элемент с точными размерами и позицией. Прямоугольник находится внутри `group`, поэтому перемещение группы автоматически перемещает и прямоугольник.

### 3. Группировать фигуры в документе Word

Класс `GroupShape` агрегирует несколько объектов рисования. Группировка полезна, когда нужно рассматривать несколько объектов как единое целое (например, перемещать, вращать или копировать их вместе).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Почему мы группируем* — Группировка уменьшает сложность раскладки. Вместо позиционирования каждой фигуры отдельно на странице, вы один раз задаёте `Left`, `Top`, `Width` и `Height` группы.

### 4. Установить размеры фигур для точного расположения

И группе, и её дочерним фигурам нужны явные размеры; иначе Word применит размеры по умолчанию, которые могут не соответствовать вашему дизайну.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Почему мы задаём размеры* — Точные измерения гарантируют, что прямоугольник и текстовое поле не будут непреднамеренно перекрываться и что итоговый **save docx file** будет соответствовать задуманному макету.

### 5. Создать текстовое поле программно внутри группы

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Почему важен этот шаг* — Сегмент **create textbox programmatically** показывает, как встроить форматированный текст в фигуру. Использование `Paragraph` и `Run` даёт полный контроль над последующим форматированием.

### 6. Вставить групповую фигуру и **сохранить файл docx**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Почему важен финальный шаг* — Вызов `InsertNode` размещает сгруппированные фигуры точно там, где находится курсор билдера. Метод `doc.Save` выполняет операцию **save docx file**, записывая полностью готовый документ Word на диск.

> **Результат:** Открытие *GroupShape.docx* в Microsoft Word показывает прямоугольник слева и текстовое поле справа, оба закреплены вместе внутри одной группы. Вы можете перемещать группу как единое целое, изменять её размер или применять дополнительное форматирование.

## Полный, готовый к запуску пример

Скопируйте код ниже в новый консольный проект (`dotnet new console`) и выполните `dotnet run`. Программа создаст `GroupShape.docx` в папке вывода проекта.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Ожидаемый результат

* В каталоге вывода появляется файл **GroupShape.docx**.
* При открытии файла отображается прямоугольная фигура слева и текстовое поле с надписью «Grouped text» справа, оба закреплены вместе.
* Выбор любой из фигур перемещает всю группу, подтверждая, что функциональность **group shapes word** работает как задумано.

## Распространённые варианты и граничные случаи

| Ситуация | Рекомендация |
|-----------|----------------|
| Нужно более двух фигур | Добавьте дополнительные объекты `Shape` в `group` перед вызовом `builder.InsertNode`. |
| Требуется, чтобы группа появилась на определённой странице | Переместите курсор билдера с помощью `builder.MoveToDocumentEnd()` или `builder.MoveToPage(pageNumber)`. |
| Необходимы другие единицы измерения (например, сантиметры) | Используйте `ConvertUtil.InchToPoint(1.0)` для преобразования дюймов в пункты — единицы, которые ожидает Word. |
| Нужно, чтобы текстовое поле обтекало текст | Установите `textBox.TextBoxWrap = TextBoxWrapType.Square` после создания текстового поля. |
| Работа с более старыми версиями .NET Framework | Тот же API работает с .NET Framework 4.7+, но убедитесь, что подключена правильная версия Aspose.Words. |

**Совет:** Всегда задавайте `Width` и `Height` группы *после* добавления всех дочерних фигур. Это гарантирует, что группа полностью охватывает своё содержимое и не будет обрезаться при открытии документа в Word.

## Заключение

Теперь вы знаете, как **сохранить файл docx**, одновременно **add rectangle shape**, **group shapes word**, **set shape dimensions** и **create textbox programmatically** с помощью Aspose.Words for .NET. Полный пример демонстрирует чистый, повторяемый шаблон, который можно адаптировать под более сложные макеты, такие как диаграммы, изображения,

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}