---
category: general
date: 2026-07-29
description: Создайте пустой документ Word и узнайте, как скрыть форму, создать скрытый
  объект и создать эллипс с помощью Aspose.Words на C#. Пошаговый код включён.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- how to hide shape
- create hidden object
- create ellipse shape
language: ru
lastmod: 2026-07-29
og_description: Создайте пустой документ Word и мгновенно скройте форму. Узнайте,
  как создать скрытый объект и нарисовать эллипс с помощью Aspose.Words в C#.
og_image_alt: Hidden ellipse shape inserted into a blank Word document
og_title: Создайте пустой документ Word со скрытой эллиптической фигурой – учебник
  C#
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  headline: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  type: TechArticle
- description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  name: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  steps:
  - name: What if the target Word version doesn’t support hidden shapes?
    text: The `Hidden` flag is part of the Office Open XML spec and is respected by
      Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so
      always save as `.docx` when you need reliable hiding.
  - name: Can I hide other types of objects (pictures, tables)?
    text: Yes. Any node derived from `Shape`—including pictures, text boxes, and even
      SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.
  - name: Does hiding a shape affect document performance?
    text: Negligibly. The shape is stored as XML markup, and Word skips rendering
      hidden objects during layout. If you embed many hidden objects, the file size
      grows, but rendering stays fast.
  - name: How does this differ from using a bookmark or comment as a marker?
    text: Bookmarks are invisible by design, but they’re meant for navigation, not
      visual placeholders. Comments appear in the margin. A hidden shape gives you
      a visual object (size, position) that you can later reveal or manipulate, which
      is handy for templating scenarios.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Создание пустого документа Word с скрытым эллипсом – Полное руководство по
  C#
url: /ru/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание пустого документа Word со скрытой эллипсной фигурой – Полное руководство на C#

Когда‑нибудь нужно было создать **пустой документ Word**, а затем скрыть в нём форму? Возможно, вы генерируете шаблон, где определённые маркеры должны оставаться невидимыми до более позднего шага. В этом руководстве мы подробно разберём, **как скрыть форму**, как **создать скрытый объект**, и даже как **создать эллипсную форму** с помощью Aspose.Words для .NET. К концу вы получите готовый фрагмент C#, который создаёт DOCX‑файл с невидимым эллипсом.

## Что вы узнаете

- Инициализировать новый пустой документ Word с помощью Aspose.Words.  
- Создать эллипсную форму, задать её размеры и позицию на странице.  
- Пометить форму как скрытую, чтобы она никогда не отображалась на экране и не печаталась.  
- Сохранить результат на диск и убедиться, что скрытый объект действительно невидим.  

Никаких внешних библиотек, кроме Aspose.Words, не требуется, а код работает с версией 24.10 и новее (свойство `Hidden` было введено в этом релизе). Приступим.

![Диаграмма скрытого эллипса внутри пустого документа Word](https://example.com/hidden-ellipse.png "Скрытая эллипсная форма, вставленная в пустой документ Word")

## Создание пустого документа Word и вставка скрытой эллипсной формы

Первый шаг – создать совершенно новый документ. Думайте о `Document` как о пустом холсте; `DocumentBuilder` – это ваша кисть.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder to edit it.
Document document = new Document();               // This is your blank word document.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Почему начинать с пустого документа?**  
> Чистый лист гарантирует, что никакое предсуществующее содержимое не помешает добавлению скрытой формы. Это также упрощает копирование‑вставку примера в любой проект.

## Как скрыть форму: установка свойства Hidden

Aspose.Words 24.10 ввёл флаг `Hidden` у `Shape`. При установке в `true` Word обрабатывает форму как комментарий — полностью невидимую в пользовательском интерфейсе и при печати.

```csharp
// Step 2: Create an ellipse shape and set its size and position.
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width = 100;   // Width in points
ellipseShape.Height = 80;   // Height in points
ellipseShape.Left = 150;    // Horizontal offset from the left margin
ellipseShape.Top = 150;     // Vertical offset from the top margin

// Step 3: Hide the shape so it does not appear when the document is viewed or printed.
ellipseShape.Hidden = true;   // This is the key to "how to hide shape"
```

> **Полезный совет:** Если позже понадобится раскрыть форму программно, просто переключите `ellipseShape.Hidden = false;` и заново сохраните документ.

## Создание скрытого объекта: вставка формы в документ

Теперь, когда эллипс подготовлен и скрыт, вставляем его в текущую позицию курсора билдера. Позиция билдера по умолчанию находится в начале первого абзаца, что идеально подходит для пустого документа.

```csharp
// Step 4: Insert the hidden shape into the document at the current builder position.
builder.InsertNode(ellipseShape);
```

> **А что если нужна форма на определённой странице?**  
> Сначала переместите билдер на нужную страницу (`builder.MoveToDocumentEnd();` или `builder.MoveToPage(pageNumber);`), а затем вызывайте `InsertNode`.

## Сохранение документа с скрытой формой

Наконец, записываем файл на диск. В результате получится обычный DOCX, который любой процессор Word откроет — только эллипс останется невидимым.

```csharp
// Step 5: Save the document containing the hidden shape.
document.Save("YOUR_DIRECTORY/HiddenShape.docx");
```

> **Ожидаемый результат:** Откройте `HiddenShape.docx` в Microsoft Word. Графики вы не увидите, но размер файла будет немного больше, чем у действительно пустого документа, потому что скрытый эллипс хранится в XML.

## Программная проверка скрытого эллипса (необязательно)

Если хотите убедиться, что форма действительно скрыта, загрузите сохранённый файл и проверьте свойство `Hidden` у формы:

```csharp
Document loaded = new Document("YOUR_DIRECTORY/HiddenShape.docx");
Shape loadedShape = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
Console.WriteLine($"Is shape hidden? {loadedShape.Hidden}"); // Should print True
```

Запуск этого фрагмента выводит `True`, подтверждая, что скрытый объект выжил после цикла сохранения‑загрузки.

## Пограничные случаи и часто задаваемые вопросы

### Что если целевая версия Word не поддерживает скрытые формы?

Флаг `Hidden` является частью спецификации Office Open XML и учитывается Word 2007+ и LibreOffice. Старые форматы (например, `.doc`) игнорируют этот флаг, поэтому всегда сохраняйте как `.docx`, когда нужна надёжная скрытность.

### Можно ли скрыть другие типы объектов (изображения, таблицы)?

Да. Любой узел, наследующий `Shape` — включая картинки, текстовые блоки и даже SmartArt — имеет свойство `Hidden`. Просто установите его в `true` перед вставкой.

### Влияет ли скрытие формы на производительность документа?

Практически не влияет. Форма хранится как XML‑разметка, и Word пропускает её рендеринг при построении макета. При большом количестве скрытых объектов размер файла растёт, но отрисовка остаётся быстрой.

### Чем это отличается от использования закладки или комментария как маркера?

Закладки по умолчанию невидимы, но предназначены для навигации, а не для визуальных заполнителей. Комментарии отображаются в полях. Скрытая форма предоставляет визуальный объект (размер, позицию), который можно позже раскрыть или изменить — удобно для шаблонных сценариев.

## Полный рабочий пример

Ниже представлен полностью готовый к копированию и вставке код. В нём присутствуют все директивы `using`, создание скрытого эллипса и шаг проверки.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HiddenEllipseDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Build the ellipse shape.
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width = 100,
            Height = 80,
            Left = 150,
            Top = 150,
            Hidden = true               // ← how to hide shape
        };

        // 3️⃣ Insert the hidden shape.
        builder.InsertNode(ellipse);

        // 4️⃣ Save the file.
        string outPath = "HiddenEllipse.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");

        // 5️⃣ Optional: Verify that the shape is hidden.
        Document loaded = new Document(outPath);
        Shape loadedEllipse = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
        Console.WriteLine($"Is the ellipse hidden? {loadedEllipse.Hidden}");
    }
}
```

Запуск программы создаёт `HiddenEllipse.docx` в папке выполнения. Откройте его — вы увидите полностью обычную пустую страницу, но скрытый эллипс будет тихо находиться внутри.

## Итоги

Мы рассмотрели, как **создать пустой документ Word**, **скрыть форму**, **создать скрытый объект** и **создать эллипсную форму** с помощью нескольких строк C#. Главный вывод — свойство `Hidden` у `Shape`, которое превращает любой визуальный элемент в невидимый маркер без нарушения совместимости с Word.

## Что дальше?

- **Оформить скрытую форму** (цвет заливки, стиль линии), чтобы при последующем раскрытии она выглядела точно так, как задумано.  
- **Комбинировать скрытые формы с закладками** для построения динамических шаблонов, которые можно включать и отключать.  
- **Исследовать другие типы фигур** — прямоугольники, стрелки или даже пользовательские SVG‑контуры — заменив `ShapeType.Ellipse`.  

Экспериментируйте: меняйте размер, перемещайте позицию или вставляйте несколько скрытых эллипсов. Та же схема работает для любой фигуры Aspose.Words, которую нужно скрыть от глаз.

Если возникнут трудности или появятся идеи по расширению этой схемы, оставляйте комментарий ниже. Счастливого кодинга!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}