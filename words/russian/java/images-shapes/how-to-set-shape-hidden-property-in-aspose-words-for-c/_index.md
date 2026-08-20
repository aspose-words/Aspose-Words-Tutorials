---
category: general
date: 2026-08-20
description: Узнайте, как установить свойство скрытия формы в Aspose.Words для C#.
  Это руководство показывает, как вставить изображение и скрыть форму, чтобы она никогда
  не отображалась в пользовательском интерфейсе и не выводилась при печати.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: ru
lastmod: 2026-08-20
og_description: Установите скрытое свойство формы в Aspose.Words с помощью C#. Вставьте
  изображение, скройте форму и убедитесь, что она никогда не отображается в пользовательском
  интерфейсе и не выводится при печати.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Установить скрытое свойство формы в Aspose.Words — полное руководство по
  C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Как установить свойство Hidden у Shape в Aspose.Words для C#
url: /ru/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как установить свойство скрытия фигуры в Aspose.Words для C#

Если вам нужно **установить свойство скрытия фигуры** в документе Word, этот учебник покажет точные шаги с использованием Aspose.Words для .NET. Независимо от того, создаёте ли вы движок шаблонов, генерируете отчёты или внедряете логотип, который должен оставаться невидимым, вы узнаете, как вставить изображение и скрыть фигуру, чтобы она никогда не появлялась в пользовательском интерфейсе или при печати.

В этом руководстве мы также рассматриваем **вставку изображения в документ**, объясняем, почему скрытие фигуры важно для печати, и пошагово проходим полный, исполняемый код. Внешних ссылок не требуется — просто скопируйте, вставьте и запустите.

## Prerequisites

Перед началом убедитесь, что у вас есть:

* .NET 6.0 или новее (последняя версия Aspose.Words ориентирована на .NET 6+)
* Действительная лицензия Aspose.Words для .NET (или используйте бесплатный режим оценки)
* Visual Studio 2022 или любая другая IDE для C#, которую вы предпочитаете
* Файл изображения (например, `logo.png`), размещённый в папке, к которой можно обратиться из кода

## Step 1: Create a new Document and DocumentBuilder

Класс `DocumentBuilder` является точкой входа для программного построения содержимого Word. Он позволяет вставлять абзацы, таблицы и фигуры, такие как изображения.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Почему этот шаг?*  
Создание `Document` даёт вам представление файла .docx в памяти, а `DocumentBuilder` предоставляет fluent API для вставки объектов. Без этих объектов вы не сможете разместить фигуру в документе.

## Step 2: Insert the image as a shape

Aspose.Words рассматривает каждую картинку как `Shape`. Метод `InsertImage` возвращает экземпляр этой `Shape`, которым вы сможете управлять позже.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*Почему этот шаг?*  
Использование `InsertImage` не только добавляет картинку в поток текста, но и даёт вам ссылку (`picture`), которую можно настроить. Это необходимо для **C# shape hidden property**, которое мы установим дальше.

## Step 3: Set the shape hidden property

Свойство `Hidden` определяет, будет ли фигура участвовать в UI и печати. Установка его в `true` делает фигуру невидимой в интерфейсе Word и гарантирует, что она не будет напечатана.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*Почему этот шаг?*  
Когда фигура помечена как скрытая, Word обрабатывает её как комментарий — она присутствует в структуре документа, но никогда не отображается. Это суть **set shape hidden property**.

## Step 4: Save the document

Наконец, запишите документ на диск. Вы можете выбрать любой формат, поддерживаемый Aspose.Words (`.docx`, `.pdf`, `.html` и т.д.).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*Почему этот шаг?*  
Сохранение фиксирует изменения в памяти. Открытие полученного `.docx` в Microsoft Word не покажет изображение, а экспорт в PDF подтвердит, что фигура не появляется в печатном выводе.

## Full, runnable example

Объединив всё вместе, получаем полную программу, которую можно скомпилировать и запустить:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**Ожидаемый результат**

* Открытие `HiddenImageDocument.docx` в Microsoft Word не показывает видимого изображения.
* Экспорт или печать документа (или открытие PDF) также не отображают изображение.
* Скрытая фигура всё ещё присутствует в XML документа, что можно проверить, открыв `.docx` как zip‑архив и изучив `word/document.xml` — вы увидите элемент `<w:pict>` с атрибутом `w:hidden="true"`.

## Common variations and edge cases

| Ситуация | Что делать | Почему это важно |
|-----------|------------|----------------|
| **Отсутствует файл изображения** | Оберните `InsertImage` в `try/catch` и обработайте `FileNotFoundException`. | Предотвращает падение приложения и позволяет записать понятную ошибку в журнал. |
| **Несколько скрытых фигур** | Вызовите `picture.Hidden = true` для каждой вставляемой `Shape` или пройдитесь по `doc.GetChildNodes(NodeType.Shape, true)`. | Гарантирует, что каждый нежелательный визуальный элемент останется невидимым. |
| **Требуется, чтобы фигура была видна только в режиме редактирования** | Установите `picture.Hidden = false` после редактирования, затем переключите обратно перед сохранением. | Позволяет работать с фигурой в UI, при этом финальный вывод остаётся чистым. |
| **Печать в старых версиях Word** | Проверьте документ в Word 2010 или новее; флаг скрытия поддерживается во всех современных версиях. | Обеспечивает совместимость с базой пользователей. |
| **Использование другого формата файла (например, напрямую PDF)** | Флаг `Hidden` работает одинаково; Aspose.Words учитывает его при конвертации в PDF. | Подтверждает, что **prevent shape from printing** работает для всех целей экспорта. |

## Pro tip: Verify the hidden flag programmatically

Если необходимо убедиться, что фигура скрыта перед сохранением, можно проверить свойство:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

Эта простая проверка полезна в автоматизированных конвейерах, где требуется гарантировать соответствие политикам генерации документов.

## Conclusion

Теперь вы знаете, как **установить свойство скрытия фигуры** в Aspose.Words для C#. Вставив изображение, применив `picture.Hidden = true` и сохранив документ, фигура исчезает из UI и никогда не появляется в печатном выводе. Эта техника незаменима, когда нужны заполнители, водяные знаки или элементы брендинга, которые должны оставаться невидимыми для конечных пользователей.

### What’s next?

* Исследуйте другие свойства фигур, такие как `picture.WrapType`, `picture.Rotation` и `picture.RelativeHorizontalPosition`.
* Узнайте, как **hide shape in Aspose.Words** условно, в зависимости от ввода пользователя или конфигурации.
* Сочетайте скрытые фигуры с **insert image into document** в циклах для создания динамических, невидимых маркеров для последующей обработки (например, поля слияния).

Экспериментируйте с различными форматами изображений, макетами документов и целевыми форматами экспорта. Скрытие фигур даёт тонкий контроль над тем, что видят ваши читатели, и тем, что остаётся за кулисами. Приятного кодинга!

## What Should You Learn Next?

Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}