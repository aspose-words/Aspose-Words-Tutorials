---
category: general
date: 2026-09-18
description: Создайте пустой документ Word и скройте эллипс с помощью Aspose.Words.
  Узнайте, как скрыть форму в Word, как вставить эллипс и быстро создать скрытую форму.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: ru
lastmod: 2026-09-18
og_description: Создайте пустой документ Word и скройте форму эллипса в Word. Это
  руководство пошагово покажет, как вставить эллипс, скрыть форму в Word и создать
  скрытую форму с помощью Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: Создайте пустой документ Word с скрытой эллиптической фигурой
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Создать пустой документ Word со скрытой эллиптической фигурой
url: /ru/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создайте пустой документ Word со скрытой эллиптической фигурой

Если вам нужно **создать пустой документ Word**, который содержит форму, которую вы не хотите, чтобы она отображалась в макете, это руководство покажет вам, как это сделать. С помощью Aspose.Words for .NET вы можете программно вставить эллипс и затем скрыть форму, чтобы документ оставался визуально пустым, но при этом сохранял данные формы.

В этом руководстве вы узнаете:

* как **создать пустой документ Word** объекты,
* как **вставить эллипс** с помощью `DocumentBuilder`,
* как **скрыть форму в Word**, чтобы она не влияла на страницу,
* как **создать скрытую форму** объекты для последующей обработки.

Эти шаги работают с .NET 6+ и последней версией Aspose.Words (23.9 на момент написания). Дополнительная установка Office не требуется.

## Требования

* Visual Studio 2022 (или любой IDE для C#)
* .NET 6 SDK или более поздняя версия
* NuGet‑пакет Aspose.Words for .NET  
  ```bash
  dotnet add package Aspose.Words
  ```
* Базовые знания C# и концепций документов Word

## Шаг 1: Создать пустой документ Word

Первое, что вам нужно сделать, — создать объект `Document`. Этот объект представляет пустой файл `.docx` и служит основой для всех дальнейших операций.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

Создание **пустого документа Word** дает вам чистый холст — без абзацев, без разделов, только базовая структура пакета. Это идеальная отправная точка, когда вам нужна только скрытая форма и ничего больше.

## Шаг 2: Инициализировать DocumentBuilder

`DocumentBuilder` предоставляет удобный API для добавления содержимого в `Document`. Он работает как курсор, которым вы перемещаетесь по документу.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder автоматически создает первый раздел и абзац по умолчанию, поэтому вы можете сразу начинать вставлять формы, не добавляя разделы вручную.

## Шаг 3: Вставить эллиптическую форму

Теперь мы **вставляем эллипс** с помощью метода `InsertShape`. Метод принимает перечисление `ShapeType`, ширину и высоту (в пунктах).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

Почему именно эллипс? Эллипс — это векторная форма, которую можно скрыть, не влияя на поток окружающего текста. Ширина 100 pt и высота 50 pt выбраны произвольно; вы можете изменить их в соответствии с вашими потребностями последующей обработки.

## Шаг 4: Скрыть форму, чтобы она не отображалась в макете

Чтобы **скрыть форму в Word**, установите свойство `Hidden` у объекта `Shape` в значение `true`. Когда документ откроется в Microsoft Word, форма будет невидима и не займет место в макете.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

Флаг `Hidden` сохраняется в XML формы (`<w:hidden/>`). Word учитывает этот атрибут при рендеринге, поэтому документ выглядит полностью пустым, хотя форма присутствует.

### Совет профессионала

Если позже понадобится снова сделать форму видимой, просто установите `ellipse.Hidden = false;` и сохраните документ.

## Шаг 5: Сохранить документ со скрытой формой

Наконец, сохраните документ на диск. Файл будет обычным `.docx`, который может открыть любой процессор Word.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

Сохранённый файл `HiddenEllipse.docx` — это **созданный пустой документ Word**, содержащий скрытый эллипс. При открытии в Microsoft Word отображается пустая страница, но форма всё ещё присутствует в структуре Open XML.

## Полный рабочий пример

Ниже представлен полный, автономный пример программы, который вы можете скопировать, вставить и запустить.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Ожидаемый результат**

* Файл с именем `HiddenEllipse.docx` появляется в `C:\Temp`.
* При открытии файла в Microsoft Word отображается полностью пустая страница.
* Если вы исследуете документ с помощью Open XML SDK или просмотрщика zip, вы найдете элемент `<w:shape>` с `<w:hidden/>` внутри части документа.

## Часто задаваемые вопросы и особые случаи

### Что делать, если форма всё ещё отображается?

* Убедитесь, что вы используете Aspose.Words 23.9 или более новую версию — в более старых версиях была ошибка, при которой `Hidden` игнорировался для некоторых типов форм.
* Проверьте, что вы не применяете дополнительное форматирование (например, `WrapType`), которое заставляет форму занимать место в макете.

### Можно ли скрыть другие типы форм?

Да. То же свойство `Hidden` работает для `ShapeType.Rectangle`, `ShapeType.Picture` и т.д. Просто замените `ShapeType.Ellipse` на нужный тип.

### Как позже перечислить скрытые формы?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

Этот фрагмент кода перебирает все формы и выводит те, которые скрыты, что полезно для рабочих процессов **создания скрытых форм**, где позже необходимо их обработать или сделать видимыми.

## Заключение

Теперь вы знаете, как **создать пустой документ Word**, **вставить эллипс** и **скрыть форму в Word**, чтобы получить **созданную скрытую форму**, которая остаётся невидимой для читателя. Эта техника полезна для хранения метаданных, закладок или пользовательского XML в документе без изменения его визуального вида.

### Следующие шаги

* Изучите **как условно скрывать форму** в зависимости от содержимого документа.
* Узнайте **как сделать форму видимой** при генерации финальной версии документа.
* Сочетайте скрытые формы с **пользовательскими свойствами документа**, чтобы внедрять машинно‑читаемые данные.

Не стесняйтесь экспериментировать с различными типами форм, размерами и логикой скрытого состояния, чтобы подобрать их под ваш сценарий автоматизации. Приятного кодинга!

## Что вам следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Создать пустой документ Word с фигурой прямоугольника с тенью – пошаговое руководство](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Создать прямоугольную форму в Word с Aspose.Words – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Создать групповую форму в документе Word с использованием Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}