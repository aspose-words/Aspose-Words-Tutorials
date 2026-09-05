---
category: general
date: 2026-09-05
description: Узнайте, как создать групповой объект в docx, вставить кнопку ActiveX
  и загрузить Markdown в документ Word с полным примером на C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: ru
lastmod: 2026-09-05
og_description: Создайте групповую форму в docx, вставьте кнопку ActiveX и загрузите
  Markdown в документ Word с помощью C#. Следуйте этому пошаговому руководству.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Создать групповую фигуру в docx и встроить элементы управления ActiveX —
  руководство по C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: Как создать групповую фигуру docx и добавить интерактивные элементы управления
  в C#
url: /ru/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать групповой объект docx и добавить интерактивные элементы управления в C#

Если вам нужно **create group shape docx** файлы программно, это руководство покажет вам, как это сделать. Вы также увидите, как **insert ActiveX command button** элементы управления и **load Markdown into a Word document** без потери подчеркивания. К концу урока у вас будет полностью функциональный `.docx`, объединяющий векторную графику, интерактивные элементы UI и контент на основе markdown.

Это руководство предполагает, что у вас есть базовая среда разработки C# и установленная библиотека Aspose.Words for .NET. Внешние инструменты не требуются — всё работает внутри стандартного .NET‑консольного или настольного приложения.

## Предварительные требования

- .NET 6.0 SDK или новее (код также работает с .NET Framework 4.7+)
- Aspose.Words for .NET (NuGet‑пакет `Aspose.Words`)
- Действительный сертификат X.509 (`.pfx`), если вы хотите протестировать шаг подписи
- Файл изображения (например, `logo.png`) и файл markdown (`sample.md`), размещённые в известной папке

> **Pro tip:** Храните все входные файлы в одной папке *resources*, чтобы упростить относительные пути.

## Шаг 1: Настройте проект и импортируйте пространства имён

Создайте новый консольный проект и добавьте необходимые директивы `using`. Этот блок также демонстрирует, как ссылаться на классы Aspose.Words, которые вы будете использовать позже.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

Инструкции `using` дают вам прямой доступ к `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl` и другим типам, используемым в течение всего руководства.

## Шаг 2: **Create group shape docx** – добавьте сгруппированный объект с дочерними элементами

*Group shape* позволяет рассматривать несколько графических объектов как единое целое. Это удобно для перемещения или изменения размеров связанных графиков одновременно.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Почему нужен group shape?**  
Группировка сохраняет выравнивание прямоугольника и эллипса, когда пользователь перетаскивает их в Word. Она также упрощает последующие операции, такие как применение общей рамки или программное перемещение всей графики.

## Шаг 3: Вставьте простой текстовый элемент управления содержимым (placeholder для ввода пользователя)

Элементы управления содержимым предоставляют конечным пользователям структурированную область для ввода текста. Текст‑заполнитель исчезает, как только пользователь начнёт печатать.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

Свойство `PlaceholderName` — это то, что Word отображает светло‑серой подсказкой. Пользователи могут заменить его своим текстом, а базовый XML остаётся корректным.

## Шаг 4: **Insert ActiveX command button** – добавьте интерактивный UI в документ

ActiveX‑элементы управления всё ещё поддерживаются в современных файлах Word и могут вызывать макросы или внешнюю автоматизацию. Ниже мы добавляем *command button* и задаём его подпись.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**Когда использовать ActiveX‑кнопку?**  
Если вы распространяете документ в корпоративной среде, где используются VBA‑макросы, ActiveX‑кнопка может запускать макрос или внешнее приложение. Для чисто HTML‑основанной интерактивности рассмотрите использование *content controls* с *Office.js*.

## Шаг 5: Вставьте скрытое изображение (например, логотип) для брендинга или последующего доступа скриптом

Скрытые фигуры не отображаются в печатном документе, но остаются в XML, позволяя программно извлекать их позже.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Шаг 6: **Load markdown into a Word document** с сохранением подчеркивания

Aspose.Words может импортировать Markdown напрямую. Включение `ImportUnderlineFormatting` гарантирует, что подчеркивания markdown (`<u>` или `__text__`) превращаются в стили подчеркивания Word, а не в обычный текст.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Edge case:** Если markdown‑файл содержит таблицы, они автоматически преобразуются в таблицы Word. Если требуется пользовательское оформление таблиц, примените `DocumentBuilder` после вставки.

## Шаг 7: Подпишите документ с помощью XAdES‑EPES (необязательный шаг безопасности)

Цифровые подписи гарантируют целостность документа. Следующий код подписывает файл **create group shape docx** профилем XAdES‑EPES.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Security note:** Храните пароль сертификата вне системы контроля версий. Используйте переменные окружения или защищённое хранилище в продакшене.

## Полный исполняемый пример

Объединив все шаги, получаем единый, самодостаточный программный модуль. Сохраните файл как `Program.cs` и запустите его из командной строки.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Запуск программы генерирует `CompleteGroupShape.docx`, содержащий:

- Сгруппированный прямоугольник + эллипс (ядро **create group shape docx**)
- Простой текстовый элемент управления содержимым с placeholder‑текстом
- **insert ActiveX command button** с подписью «Click Me»
- Скрытое изображение‑логотип
- Содержимое markdown с сохранёнными подчеркиваниями
- Цифровую подпись XAdES‑EPES (если предоставлен сертификат)

## Часто задаваемые вопросы и устранение неполадок

| Вопрос | Ответ |
|---|---|
| **Will the ActiveX button work on macOS Word?** | macOS Word не поддерживает ActiveX‑элементы управления. Кнопка будет отображаться как статическое изображение. Используйте content controls с Office.js для кросс‑платформенной интерактивности. |
| **What if the markdown file contains custom CSS?** | Aspose.Words игнорирует CSS; обрабатывается только стандартный синтаксис markdown. Преобразуйте элементы, стилизованные CSS, в стили Word вручную после импорта. |
| **Can I add more shapes to the same group later?** | Да. Получите `GroupShape` по имени или индексу, затем вызовите `AppendChild(newShape)`. Не забудьте пересохранить документ после изменений. |
| **How do I change the signature algorithm?** | Установите `signature.SignatureAlgorithm` перед вызовом `Sign`. По умолчанию используется SHA‑256, что удовлетворяет большинству требований к соответствию. |
| **Is the hidden image visible in the Word UI?** | Нет, но её можно отобразить, включив *Show hidden text* в параметрах Word. Это удобно для хранения метаданных без захламления макета. |

## Следующие шаги

Теперь, когда вы умеете **create group shape docx**, **insert ActiveX command button** и **load markdown into a Word document**, вы можете исследовать:

- **Embedding VBA macros**, реагирующие на клик ActiveX‑кнопки.
- **Applying custom styles** к абзацам, сгенерированным из markdown.
- **Generating PDFs** из того же документа с помощью `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **Automating batch processing** множества markdown‑файлов в один собранный отчёт.

Эти расширения позволяют построить полностью автоматизированный конвейер создания документов, объединяющий богатую графику, интерактивные элементы и авторинг на основе markdown — всё из C#.

---

*Happy coding! If you found this tutorial

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, развивая техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Создать групповой объект в документе Word с помощью Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Создать прямоугольный объект в Word с использованием C# – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Создать markdown из Word – полное руководство C#](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}