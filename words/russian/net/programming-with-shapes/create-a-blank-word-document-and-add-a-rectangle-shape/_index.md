---
category: general
date: 2026-09-05
description: Узнайте, как создать пустой документ Word и добавить прямоугольную форму,
  которую можно скрыть, используя Aspose.Words в C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: ru
lastmod: 2026-09-05
og_description: Создание пустого документа Word и вставка скрытого прямоугольного
  объекта с помощью Aspose.Words — пошаговое руководство для разработчиков C#.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Создайте пустой документ Word с скрытой прямоугольной фигурой
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Создайте пустой документ Word и добавьте прямоугольную фигуру
url: /ru/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создайте пустой документ Word и добавьте прямоугольную фигуру

Если вам нужно **создать пустой документ Word**, который также содержит фигуру, не отображающуюся в макете, это руководство покажет, как сделать это с помощью Aspose.Words для .NET. Вы увидите полностью готовый, исполняемый пример, который создаёт новый документ, добавляет прямоугольную фигуру, скрывает её и сохраняет файл — без дополнительного инструментария.

В руководстве рассматривается всё: от настройки проекта до устранения распространённых проблем. К концу вы сможете генерировать файл Word, который выглядит пустым для читателя, но всё ещё содержит скрытые метаданные, что полезно для водяных знаков, пользовательского XML‑хранилища или якорей макета.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 SDK или новее (код также работает с .NET Framework 4.7+)
* Visual Studio 2022 (или любой IDE, поддерживающий C#)
* Действующая лицензия **Aspose.Words** NuGet (бесплатная пробная версия подходит для тестирования)
* Базовые знания C# и концепции узлов документа

Вы можете установить библиотеку с помощью следующей команды CLI:

```bash
dotnet add package Aspose.Words
```

> **Совет:** Держите версию Aspose.Words актуальной; API, используемое в этом руководстве, стабильно начиная с версии 23.10.

## Как создать пустой документ Word с помощью Aspose.Words

Первый шаг — создать объект `Document`. Новый `Document` представляет пустой **пустой документ Word** — без абзацев, без разделов, только контейнер файла.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Почему это важно:** Начало с чистого документа гарантирует, что добавляемая позже скрытая фигура не будет конфликтовать с существующим содержимым или стилями.

## Добавьте прямоугольную фигуру в документ

Далее мы создаём прямоугольную фигуру. В Aspose.Words фигура — это узел, который можно разместить где угодно в дереве документа, и его можно настроить по размеру, заливке, стилю линии и видимости.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

Код выше создаёт видимый прямоугольник. На данном этапе вы могли бы вставить его в документ с помощью `builder.InsertNode(rectangle)`. Однако, поскольку нам нужно, чтобы фигура оставалась скрытой, мы изменим её свойство `Hidden` перед вставкой.

## Как скрыть фигуру в документе Word

Word предоставляет атрибут `Hidden` для узлов фигур. Когда он установлен в `true`, фигура не отображается в макете страницы, но остаётся частью XML‑документа. Это и есть основа требования **как скрыть фигуру**.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Объяснение:** Установка `Hidden = true` добавляет атрибут `<w:hide>` в XML фигуры. Обработчики Word игнорируют её при рендеринге, однако к фигуре можно обратиться программно или через XML‑просмотр Word.

## Вставьте скрытую фигуру в пустой документ

Теперь помещаем скрытый прямоугольник в дерево документа. Поскольку документ всё ещё пуст, фигура становится первым узлом в основной истории.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Если открыть полученный файл в Microsoft Word, вы увидите, казалось бы, пустую страницу. Фигура присутствует, но она невидима.

## Сохраните документ

Наконец, запишите документ на диск. Вы можете выбрать любой поддерживаемый формат (`.docx`, `.pdf`, `.odt` и т.д.). Для этого руководства мы используем современный формат DOCX.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Ожидаемый результат

Откройте `HiddenRectangle.docx` в Word:

* Документ выглядит пустым (нет видимых фигур или текста).
* Если исследовать файл с помощью инструмента, например **Open XML SDK** или **Word XML Viewer**, вы увидите элемент `<w:pict>`, содержащий прямоугольник с атрибутом `hidden`.

![пустой документ Word с скрытой прямоугольной фигурой](image.png){: .align-center alt="пустой документ Word с скрытой прямоугольной фигурой"}

## Полный, исполняемый пример

Ниже приведена полная программа, которую можно скопировать и вставить в консольное приложение. В ней включены все необходимые директивы `using`, обработка ошибок и комментарии.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Запустите программу (`dotnet run`) и проверьте созданный файл. Консоль выведет путь к сохранённому документу.

## Часто задаваемые вопросы и особые случаи

### Можно ли скрыть сразу несколько фигур?

Да. Создайте каждую фигуру, установите `Hidden = true` и вставляйте их последовательно. Флаг скрытия работает для каждого узла отдельно, поэтому смешивание скрытых и видимых фигур в одном документе поддерживается.

### Что если нужно, чтобы фигура была скрыта только в режиме печати?

Word различает **отображение** и **печать** через свойство `DisplayWhen`. Aspose.Words не предоставляет прямого API для этого флага, но вы можете изменить базовый XML:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Используйте это только в случае, когда требуется видимость только при печати.

### Влияет ли скрытая фигура на размер файла?

Скрытая фигура добавляет тот же XML‑payload, что и видимая, поэтому увеличение размера файла одинаково. Однако, поскольку фигура


## Что изучать дальше?


Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы реализации в ваших проектах.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}