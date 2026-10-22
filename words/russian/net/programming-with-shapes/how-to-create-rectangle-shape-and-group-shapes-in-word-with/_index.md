---
category: general
date: 2026-09-05
description: Создайте прямоугольную форму в документе Word с помощью Aspose.Words,
  затем узнайте, как вставлять эллипс и группировать формы в Word для более богатых
  макетов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: ru
lastmod: 2026-09-05
og_description: Создайте прямоугольную форму в документе Word с помощью Aspose.Words,
  затем посмотрите, как вставлять эллипс и группировать формы в Word для сложных макетов.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Создание прямоугольной формы и группировка фигур в Word – руководство Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Как создать прямоугольную форму и сгруппировать формы в Word с помощью Aspose.Words
url: /ru/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать прямоугольную форму и группировать формы в Word с помощью Aspose.Words

Если вам нужно **создать прямоугольную форму** в документе Word, это руководство покажет вам точные шаги с Aspose.Words for .NET. Вы также увидите, как вставить эллипс, группировать формы в Word и сохранить результат в файл DOCX. Решение работает в любом проекте .NET 6+ и не требует установки Microsoft Office на сервере.

В руководстве рассматривается всё — от настройки проекта до обработки распространённых проблем компоновки, так что вы можете скопировать код и сразу запустить его.

## Предварительные требования

* .NET 6 SDK или более поздняя версия, установленная  
* IDE, совместимая с NuGet (Visual Studio, Rider или VS Code)  
* Лицензия Aspose.Words for .NET (или временный оценочный ключ)  
* Базовые знания C# и структуры документа Word  

Эти элементы позволяют коду компилироваться и формам отображаться корректно.

## Шаг 1: Настройте проект и добавьте Aspose.Words

Создайте новый консольный проект и добавьте пакет Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Пакет предоставляет классы `Document`, `DocumentBuilder`, `Shape` и `GroupShape`, используемые в этом руководстве.

## Шаг 2: Инициализируйте пустой документ и builder

`Document` представляет весь файл Word, а `DocumentBuilder` позволяет программно вставлять содержимое.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Создание документа вначале гарантирует, что все последующие операции с формами будут иметь действительный контейнер.

## Шаг 3: **Создать прямоугольную форму** и задать её размеры

Прямоугольник — наиболее распространённый контейнер для текста или изображений. Вы задаёте его размер в пунктах (1 pt ≈ 1/72 дюйма).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Почему этот шаг важен: класс `Shape` инкапсулирует геометрию, свойства заливки и линии. Установка `Width` и `Height` до вставки гарантирует, что форма появится с ожидаемыми размерами.

## Шаг 4: **Как вставить эллипс** – добавить форму эллипса

Эллипс может использоваться для значков, маркеров или декоративных элементов. Код повторяет создание прямоугольника, меняется только `ShapeType`.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

Свойства `FillColor` и `Line.Color` показывают, как настроить внешний вид без внешних изображений.

## Шаг 5: **Группировать формы в Word** – объединить прямоугольник и эллипс

Группировка позволяет перемещать, изменять размер или вращать несколько форм как единое целое. Это необходимо, когда требуется составная графика (например, значок с подписью).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

При вызове `AppendChild` исходные формы удаляются из основного потока документа и становятся дочерними элементами `GroupShape`. Группа ведёт себя как единая форма, что упрощает последующие настройки компоновки.

## Шаг 6: Сохраните документ

Наконец, запишите документ на диск. Вы можете выбрать любой поддерживаемый формат (`.docx`, `.pdf`, `.html` и т.д.). Для этого руководства мы оставляем нативный формат Word.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

После запуска программы откройте *GroupShape.docx* в Microsoft Word. Вы увидите прямоугольник и эллипс, сгруппированные вместе, расположенные по указанным координатам.

## Распространённые варианты и особые случаи

| Situation | What to change | Reason |
|-----------|----------------|--------|
| **Разные единицы измерения** | Use `ConvertUtil.InchToPoint(2.5)` for inches or `ConvertUtil.MillimeterToPoint(30)` for millimetres. | Keeps code readable when you work with non‑point measurements. |
| **Добавление текста внутрь прямоугольника** | Create a `Paragraph` node, set its `Text` property, and add it to `rectangleShape` via `AppendChild`. | Allows you to label the shape without separate text boxes. |
| **Вращение группы** | Set `groupShape.Rotation = 45;` (degrees). | Useful for creating diagonal badges or watermarks. |
| **Сохранение в PDF** | Call `doc.Save("GroupShape.pdf");`. | Aspose.Words automatically rasterizes vector shapes for PDF output. |
| **Несколько групп** | Create additional `GroupShape` instances and repeat the append/insert steps. | Enables complex page layouts with several independent composites. |

### Совет профессионала

Всегда добавляйте формы **до** их группировки. Если попытаться сгруппировать форму, уже входящую в другую группу, Aspose.Words бросит `ArgumentException`. Формирование группы в одном методе предотвращает эту ошибку во время выполнения.

### На что обратить внимание

* **Система координат** – `Left` и `Top` измеряются от левого и верхнего полей страницы, а не от края документа. Неправильное понимание может привести к размещению форм за пределами страницы.
* **Лицензирование** – Без действующей лицензии сохранённый документ будет содержать водяной знак с надписью “Aspose.Words for .NET Evaluation”. Примените лицензию в начале кода (`License license = new License(); license.SetLicense("Aspose.Words.lic");`), чтобы избежать этого.

## Полный исходный код (исполняемый)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Запуск этой программы создаёт *GroupShape.docx* с группированными формами точно так, как описано.

## Заключение

Теперь вы знаете, как **создать прямоугольную форму**, **вставить эллипс** и **группировать формы в Word** с помощью Aspose.Words. Полный пример демонстрирует весь рабочий процесс — от инициализации документа до сохранения окончательного файла — чтобы вы могли интегрировать работу с формами в любое решение для автоматической генерации отчетов или документов.

### Что дальше?

* Изучите **aspose.words create shapes** для более сложной геометрии, такой как `Polygon` или `Freeform`.  
* Скомбинируйте сгруппированные формы с **content controls**, чтобы создавать динамические шаблоны.  
* Преобразуйте DOCX в PDF или HTML, чтобы увидеть, как векторные формы отображаются в разных форматах.  

Не стесняйтесь экспериментировать с различными размерами, цветами и вращениями. Освоив группировку форм, вы сможете создавать сложные диаграммы, значки и пользовательские элементы интерфейса непосредственно в документах Word.

## Что вам следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}