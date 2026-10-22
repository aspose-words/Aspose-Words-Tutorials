---
category: general
date: 2026-08-10
description: Вставьте прямоугольную форму в Word с помощью C#. Узнайте, как скрыть
  форму, скрыть форму в Word и создать скрытую форму с помощью Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: ru
lastmod: 2026-08-10
og_description: Вставка прямоугольной формы в Word с помощью C#. Этот учебник объясняет,
  как скрыть форму, как скрыть форму в Word и как создать скрытую форму с полными
  примерами кода.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: Вставка прямоугольной фигуры в Word с помощью C# – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Вставка прямоугольной формы в Word с помощью C# – полное руководство
url: /ru/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Вставка прямоугольной фигуры в Word с помощью C# – полное руководство

Если вам нужно **вставить прямоугольную фигуру** в документ Word с помощью C#, это руководство покажет точные шаги. Вы также узнаете, **как скрыть фигуру**, чтобы она не отображалась в конечном файле, что отвечает на часто задаваемый вопрос **hide shape in Word** и демонстрирует, как **create hidden shape** программно.

В учебнике рассматривается всё: от настройки Aspose.Words SDK до проверки, что фигура скрыта. К концу статьи у вас будет переиспользуемый фрагмент кода, который можно вставить в любой .NET‑проект.

## Prerequisites

Прежде чем начать, убедитесь, что у вас есть:

- .NET 6.0 или новее (код также работает с .NET Framework 4.6+)
- Действительная лицензия Aspose.Words for .NET или временный ключ оценки
- Visual Studio 2022 (или любой IDE, поддерживающий C#)
- Базовое знакомство с синтаксисом C# и Document Object Model (DOM) файлов Word

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words`.

## Step 1: Create a new blank document and a DocumentBuilder

Первой операцией является создание объекта `Document`. `DocumentBuilder` предоставляет удобный API для вставки содержимого, такого как фигуры, абзацы и таблицы.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document` представляет весь файл .docx, тогда как `DocumentBuilder` поддерживает курсор, который отслеживает, куда будет помещён следующий элемент. Инициализация обоих объектов — фундамент любой автоматизации Word.

## Step 2: Insert rectangle shape

Теперь вставляем прямоугольник. Метод `InsertShape` требует тип фигуры и её размеры в пунктах (1 point ≈ 1/72 дюйма). Размер **200 × 100 points** даёт прямоугольник приблизительно 2.78 × 1.39 дюйма.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Why this matters:** Полученный объект `Shape` полностью настраиваемый — можно изменить цвет, границу, текст и видимость до сохранения документа.

## Step 3: Hide the shape

Чтобы предотвратить отображение или печать прямоугольника, установите его свойство `Hidden` в `true`. Это свойство напрямую сопоставляется с атрибутом Word «Hidden», который учитывается как в режиме просмотра, так и при печати.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Why this matters:** Установка `Hidden` — стандартный способ **hide shape in Word** без удаления её из структуры документа. Фигура остаётся доступной коду, позволяя позже выполнять такие операции, как условное форматирование или переключение видимости на основе данных.

## Step 4: Save the document

Наконец, сохраняем документ на диск. Выберите любую папку; в примере используется путь‑заполнитель, который следует заменить реальным.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Why this matters:** Сохранение завершает файл и записывает флаг скрытия в underlying Open XML. При открытии документа в Microsoft Word прямоугольник будет невидим, подтверждая, что вы успешно **created hidden shape**.

## Step 5: Verify the hidden shape

Откройте сгенерированный `HiddenShape.docx` в Microsoft Word:

1. Перейдите в **File → Options → Display** и убедитесь, что *“Show hidden text”* **снят**.  
2. Прямоугольник не должен быть виден на любой странице.  
3. Чтобы проверить ещё раз, включите *“Show hidden text”*; прямоугольник появится с лёгкой пунктирной обводкой, подтверждая, что фигура существует, но скрыта.

Если прямоугольник всё ещё виден, проверьте, что вы сохранили файл после установки `Hidden = true` и что открываете правильный файл.

## Full runnable example

Ниже приведена полная программа, которую можно скопировать, вставить и запустить напрямую.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Expected output:** Консоль выводит путь к файлу и короткое напоминание. При открытии файла в Word прямоугольник будет невидим, если не включён режим отображения скрытого текста.

## Common questions and edge cases

### Can I hide only the outline but keep the fill visible?

Да. Вместо `Hidden = true` можно установить `rectangle.LineFormat.Visible = false`, чтобы скрыть границу, оставив цвет заливки. Это вариант **how to hide shape**, сохраняющий часть визуального представления.

### Does the hidden flag work in older Word versions (2003, 2007)?

Атрибут hidden является частью спецификации Open XML, введённой в Word 2007. Документы, сохранённые в старом бинарном формате `.doc`, не сохраняют этот флаг. Чтобы поддерживать устаревшие форматы, сохраняйте документ как `.docx` и, при необходимости, конвертируйте его позже с помощью `Aspose.Words` `SaveFormat.Doc`.

### What if I need to hide multiple shapes at once?

Итерируйте коллекцию `Document.GetChildNodes(NodeType.Shape, true)` и устанавливайте `Hidden = true` для каждой фигуры, соответствующей вашим критериям (например, определённый `ShapeType` или пользовательское значение `AlternativeText`).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Is there a performance impact when hiding shapes?

Флаг hidden добавляет к XML лишь крошечный атрибут; он не влияет на скорость рендеринга. Однако очень большое количество скрытых объектов может незначительно увеличить размер файла. Удаляйте фигуры, которые вам никогда не нужны, чтобы документ оставался лёгким.

## Tips and best practices

- **Give the shape a meaningful name** с помощью `rectangle.Name = "MyHiddenRectangle"`; это поможет позже находить фигуру в DOM.  
- **Set `AlternativeText`** в пользовательский тег (например, `"HiddenShape"`). Это позволяет находить фигуру без привязки к её индексу.  
- **Wrap the code in a try‑catch block** для graceful‑обработки ошибок лицензирования или I/O‑исключений.  
- **Dispose of the Document** после сохранения, если вы обрабатываете множество файлов в цикле, чтобы освободить неуправляемые ресурсы: `document.Dispose();`.

## Conclusion

Теперь вы знаете, как **insert rectangle shape** в документ Word с помощью C#, как **hide shape in Word**, и как **create hidden shape**, которая остаётся частью структуры документа, но невидима для конечных пользователей. Полный, исполняемый пример демонстрирует весь рабочий процесс — от создания документа до проверки.

Далее вы можете исследовать **how to hide shape** на основе ввода пользователя или комбинировать скрытые фигуры с элементами управления содержимым для динамической генерации документов. Тот же приём применим к другим типам фигур, таким как эллипсы, стрелки или пользовательские рисунки.

Экспериментируйте с различными размерами, цветами и настройками видимости. Если возникнут проблемы, вернитесь к описанным шагам или обратитесь к документации Aspose.Words для более глубокого изучения API. Happy coding!

## What Should You Learn Next?

Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}