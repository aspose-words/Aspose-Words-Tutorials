---
category: general
date: 2026-08-04
description: Вставьте прямоугольную форму в документ Word с помощью C#. Узнайте, как
  группировать формы в Word, сохранять документ в формате docx и использовать DocumentBuilder
  для сложных макетов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: ru
lastmod: 2026-08-04
og_description: Вставьте прямоугольную форму в файл Word с помощью C# и затем сгруппируйте
  формы для сложных макетов. В этом руководстве также рассматривается сохранение документа
  в формате docx и эффективное использование DocumentBuilder.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Вставка прямоугольной формы в Word – пошаговое руководство по C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Вставка прямоугольной формы в Word с помощью C# – полное руководство
url: /ru/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Вставка прямоугольной фигуры в Word с помощью C# – полное руководство

Если вам нужно **вставить прямоугольную фигуру** в документ Word с помощью C#, это руководство покажет, как это сделать. Вы также узнаете, **как группировать фигуры** в Word, **как сохранить документ в формате docx** и **как использовать Builder** для чистого, поддерживаемого кода.

Работа с фигурами часто требуется при программной генерации отчетов, сертификатов или пользовательских макетов. К концу этого руководства у вас будет полностью рабочий пример, который создает прямоугольник, добавляет эллипс, группирует их и сохраняет результат в файл DOCX.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 или более новая версия  
* Visual Studio 2022 (или любая IDE, поддерживающая C#)  
* Библиотека **Aspose.Words for .NET** (доступна через NuGet)  

Библиотеку можно добавить следующей командой:

```bash
dotnet add package Aspose.Words
```

## Вставка прямоугольной фигуры с помощью DocumentBuilder

Первый шаг – создать новый `Document` и `DocumentBuilder`. Builder предоставляет удобный API для вставки контента, включая фигуры.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

Экземпляр `DocumentBuilder` – это основной объект, который вы будете использовать для **вставки прямоугольной фигуры** и других элементов. Он отслеживает текущую позицию курсора внутри документа, поэтому любая вставка происходит точно там, где это необходимо.

## Как вставить прямоугольную фигуру

Когда Builder готов, вызовите `InsertShape`. Укажите `ShapeType`, ширину и высоту в пунктах (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Почему это важно*: Установка `FillColor` и `StrokeColor` делает прямоугольник визуально отличимым, что помогает при последующей группировке с другими фигурами.

## Как группировать фигуры в Word

Группировка фигур позволяет перемещать, вращать или форматировать несколько объектов как единое целое. После вставки прямоугольника добавьте другую фигуру (в данном примере — эллипс) и затем создайте `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

Вызов `InsertGroupShape` создает контейнер, который может содержать любое количество дочерних фигур. Добавив прямоугольник и эллипс, вы фактически **группируете фигуры в Word**. Группа ведет себя как одна фигура — её можно перемещать, применять границу или изменять размер, не затрагивая внутреннее расположение каждой дочерней фигуры.

### Совет профессионала

После группировки вы можете изменить позицию группы относительно страницы:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Сохранение документа в формате docx

После того как фигуры расположены, необходимо сохранить файл. Метод `Document.Save` автоматически определяет формат по расширению файла. Чтобы **сохранить документ в формате docx**, передайте путь, оканчивающийся на `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

Запуск программы создаст `output.docx`. Откройте файл в Microsoft Word, и вы увидите светло‑голубой прямоугольник и светло‑коралловый эллипс, сгруппированные вместе. Вы можете кликнуть группу и переместить её как один объект.

## Как эффективно использовать DocumentBuilder

`DocumentBuilder` — это не только вставщик фигур; он также работает с текстом, таблицами, колонтитулами. Когда вы комбинируете создание фигур с текстом, не забудьте сбросить курсор, если нужно вставить контент в другое место:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Явное управление состоянием Builder помогает избежать случайных перезаписей и делает код проще в поддержке.

## Особые случаи и варианты

| Ситуация | Рекомендуемый подход |
|-----------|----------------------|
| **Более двух фигур** | Вставьте каждую фигуру, затем вызовите `AppendChild` для каждой перед сохранением. |
| **Вложенные группы** | Создайте группу, добавьте фигуры, затем вставьте эту группу в другую `GroupShape`. |
| **Разные единицы измерения** | Используйте `builder.ConvertPixelsToPoints`, если размеры заданы в пикселях. |
| **Совместимость со старыми версиями Word** | Сохраните как `.doc`, изменив расширение; большинство функций фигур продолжают работать. |

## Полный рабочий пример

Ниже представлен полный код программы, который можно скопировать и вставить в новый консольный проект. Дополнительные фрагменты не требуются.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Ожидаемый результат**: При открытии `output.docx` вы увидите светло‑голубой прямоугольник и светло‑коралловый эллипс, сгруппированные вместе, расположенные на 150 pt от левого поля и 100 pt от верхнего края. Подпись появляется под группой.

## Заключение

Теперь вы знаете, как **вставить прямоугольную фигуру** в файл Word с помощью C#, **как группировать фигуры в Word** и **как сохранить документ в формате docx** с помощью `DocumentBuilder` из Aspose.Words. Овладев этими шагами, вы сможете создавать сложные макеты — сертификаты, отчёты или пользовательские формы — полностью программно.

Далее исследуйте связанные темы, такие как **добавление текстовых полей**, **работа с таблицами** или **экспорт в PDF**. Все они опираются на те же основы `DocumentBuilder`, которые вы только что освоили.

Готовы автоматизировать свои документы Word? Попробуйте расширить пример, добавив больше фигур, применив градиенты или реализовав цикл по данным для генерации полного отчёта за один запуск. Приятного кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Создать групповую форму в документе Word с использованием Aspose.Words для .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Вставка фигур в документы Word с использованием Aspose.Words для .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Создание прямоугольной фигуры в Word с Aspose.Words – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}