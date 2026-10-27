---
category: general
date: 2026-09-08
description: Узнайте, как создать пустой документ Word, вставить прямоугольник и сгруппировать
  несколько фигур с помощью C#. Следуйте этому пошаговому руководству.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: ru
lastmod: 2026-09-08
og_description: Создайте пустой документ Word, вставьте прямоугольник и сгруппируйте
  несколько фигур в C#. Этот учебник проведёт вас через весь процесс.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Создать пустой документ Word с группированными фигурами в C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Как создать пустой документ Word с группированными фигурами
url: /ru/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать пустой документ Word с группой фигур

Если вам нужно **создать пустой документ Word**, содержащий пользовательскую графику, это руководство покажет вам, как это сделать. Вы научитесь **вставлять прямоугольную фигуру**, **группировать несколько фигур** и **добавлять фигуры в группу** с помощью Aspose.Words for .NET.

Пустой документ предоставляет чистый холст, а группировка фигур позволяет перемещать, изменять размер или вращать их как единое целое. Это руководство охватывает каждый шаг — от инициализации документа до сохранения конечного файла — чтобы вы могли скопировать код в свой проект и увидеть мгновенный результат.

## Что вам понадобится

* .NET 6.0 или новее (код также работает с .NET Framework 4.6+)
* Действительная лицензия Aspose.Words for .NET (бесплатная оценочная версия подходит для тестирования)
* IDE, например Visual Studio 2022 или Visual Studio Code
* Базовое знакомство с синтаксисом C#

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words`.

## Как создать пустой документ Word

Первый шаг — создать объект `Document`. Этот объект представляет пустой файл `.docx`, который можно редактировать с помощью `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Конструктор `Document` создает **пустой документ Word** в памяти. `DocumentBuilder` предоставляет удобный API для вставки текста, изображений и графических объектов.

## Вставка прямоугольной фигуры в документ

Далее добавьте прямоугольную фигуру. Прямоугольник будет первым дочерним элементом группы, которую мы создадим позже.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Вызов `InsertShape` с параметром `ShapeType.Rectangle` **вставляет прямоугольную фигуру** в текущую позицию курсора. Ширина и высота задаются в пунктах (1 pt ≈ 1/72 in).

## Группировка нескольких фигур вместе

`GroupShape` работает как контейнер. Все дочерние фигуры внутри группы перемещаются и трансформируются совместно. Сначала создайте группу, затем добавьте только что построенный прямоугольник.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

Метод `InsertGroupShape` размещает пустую группу в позиции курсора билдера. Добавив прямоугольник, мы **группируем несколько фигур** — прямоугольник становится частью внутренней коллекции узлов группы.

## Добавление фигур в группу и сохранение файла

Теперь добавьте вторую фигуру — эллипс, — чтобы продемонстрировать, как несколько объектов используют один контейнер. После этого сохраните документ.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Вызов `InsertShape` **добавляет фигуры в группу**, когда вы присоединяете возвращённый `Shape` к `GroupShape`. Сохранение `Document` записывает файл `.docx`, который можно открыть в Microsoft Word, LibreOffice или любом совместимом просмотрщике.

### Ожидаемый результат

При открытии *GroupShapeDemo.docx* вы увидите пустую страницу с группированным объектом, содержащим светло‑голубой прямоугольник и розовый эллипс. Выбор группы позволяет перемещать обе фигуры одновременно, подтверждая, что **группировать несколько фигур** работает как задумано.

## Зачем использовать GroupShape?

* **Атомарные трансформации** – Масштабирование, вращение или перемещение группы одинаково влияет на всех дочерних элементов.
* **Логическая организация** – Держит связанные графические элементы вместе, упрощая структуру документа.
* **Производительность** – Рендеринг одного контейнера часто быстрее, чем обработка множества независимых фигур.

Если позже понадобится изменить отдельный дочерний элемент, его можно получить из `group.ChildNodes` по индексу или по свойству `Name`.

## Общие варианты и граничные случаи

| Сценарий                                 | Как адаптировать код                                                            |
|------------------------------------------|----------------------------------------------------------------------------------|
| **Разные типы фигур**                    | Replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other `ShapeType` |
| **Добавление текста внутри фигуры**      | Use `Shape.TextPath.Text = "Hello"` after inserting the shape                    |
| **Установка угла вращения**               | `group.Rotation = 45;` (degrees)                                                 |
| **Сохранение в PDF вместо DOCX**         | `doc.Save("GroupShapeDemo.pdf");`                                                |
| **Применение границы к группе**          | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## Профессиональные советы

* **Назовите ваши фигуры** – `rectangle.Name = "MyRect";` упрощает их поиск позже.
* **Используйте относительное позиционирование** – Установите `group.RelativeHorizontalPosition` в `RelativeHorizontalPosition.Page`, если хотите, чтобы группа оставалась привязанной к полям страницы.
* **Освобождайте ресурсы** – Оберните `Document` в блок `using` при работе в крупных приложениях, чтобы своевременно освобождать неуправляемую память.

## Полный исходный код для быстрого копирования

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Скопируйте код в новый консольный проект, восстановите пакет NuGet `Aspose.Words` и запустите. Файл‑результат появится в папке проекта `bin/Debug/net6.0` (или аналогичной).

## Следующие шаги

Теперь, когда вы умеете **создавать пустой документ Word**, **вставлять прямоугольную фигуру** и **группировать несколько фигур**, вы можете исследовать:

* Добавление **текстовых полей** внутри группы для создания подписанных диаграмм.
* Экспорт сгруппированной графики в изображение с помощью `doc.Save("image.png", SaveFormat.Png)`.
* Комбинирование групп с таблицами для богато оформленных отчетов.

Экспериментируйте с различными свойствами фигур, иерархиями групп и форматами экспорта, чтобы полностью раскрыть возможности рисования в Aspose.Words.

--- 

*Помните*: группировка фигур — мощный способ поддерживать порядок в документах Word и поддерживаемость кода. Приятного кодинга!

## Что вам следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Создать прямоугольную фигуру в Word с помощью C# – Пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Вставка фигур в документы Word с использованием Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Создание групповой фигуры в документе Word с использованием Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}