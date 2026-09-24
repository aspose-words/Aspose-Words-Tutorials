---
category: general
date: 2026-02-18
description: Создайте markdown из документа с простыми шагами по экспорту документа
  в markdown и сохранению изображений в подпапку. Узнайте, как сохранить документ
  в markdown на C#.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: ru
og_description: Создайте markdown из документа на C# и узнайте, как экспортировать
  документ в markdown, сохраняя изображения в подпапку. Следуйте пошаговому руководству.
og_title: Создать markdown из документа – экспортировать и сохранять изображения
tags:
- C#
- Aspose.Words
- Markdown export
title: Создать markdown из документа — экспортировать и сохранять изображения
url: /ru/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание markdown из документа – Экспорт и сохранение изображений

Когда‑нибудь вам нужно было **create markdown from document**, но вы не знали, как аккуратно хранить встроенные изображения? Вы не одиноки. Во многих проектах мы генерируем отчёты, руководства или черновики блогов программно, и последнее, чего мы хотим, — это беспорядок из файлов изображений, разбросанных по папке вывода.  

В этом руководстве мы пройдём полный, готовый к запуску пример, который **exports document to markdown**, сохраняет каждое изображение в отдельную подпапку *md‑resources*, и в конце **saves document as markdown** с использованием Aspose.Words for .NET API. К концу у вас будет один метод, который можно вставить в любой код C#, а также несколько советов по обработке граничных случаев.

> **Быстрый обзор:**  
> • Настройте `MarkdownSaveOptions`  
> • Предоставьте `IResourceSavingCallback`, который перенаправляет изображения в подпапку  
> • Вызовите `Document.Save` с настроенными параметрами  

Если вам интересно, почему мы выбираем callback вместо пост‑обработки, продолжайте чтение — рассуждения объясняются шаг за шагом.

---

## Предварительные требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.7+)  
- Aspose.Words for .NET (пакет NuGet `Aspose.Words`)  
- Исходный объект `Document` (может быть .docx, .pdf, .rtf и т.д.)  

Дополнительные библиотеки не требуются; API callback встроен в Aspose.Words.

---

## Шаг 1: Create markdown from document – настройка параметров сохранения

Первое, что мы делаем, — создаём экземпляр `MarkdownSaveOptions`. Этот объект указывает Aspose.Words, как должна вести себя конверсия, например, какой вариант Markdown использовать, следует ли встраивать изображения как Base64 и куда помещать сгенерированные файлы.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **Почему это важно:**  
> Если явно не создать `MarkdownSaveOptions`, библиотека использует настройки по умолчанию, которые встраивают изображения непосредственно в файл Markdown в виде строк Base64. Это делает файл огромным и сводит на нет цель иметь чистую папку *images*.

---

## Шаг 2: Export document to markdown и определение обработки ресурсов

Теперь мы указываем сохраняющему модулю **где** разместить каждое изображение. Интерфейс `IResourceSavingCallback` предоставляет нам точку входа, которая вызывается для каждого ресурса (изображения, SVG и т.д.), обнаруженного во время экспорта. Внутри callback мы:

1. Убеждаемся, что целевая папка существует (`md-resources/`).  
2. Устанавливаем `OutputFileName` в путь к папке плюс оригинальное имя ресурса.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **Распространённый вопрос:** *Что если я хочу встраивать изображения вместо их сохранения?*  
> Просто пропустите callback или установите `args.OutputFileName = null;` — сохраняющий модуль автоматически встроит изображение как строку Base64.

> **Граничный случай:** В некоторых старых документах встречаются дублирующиеся имена изображений. Приведённый выше callback перезапишет предыдущий файл. Чтобы этого избежать, можно добавить GUID:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## Шаг 3: Save document as markdown и проверка сохранённых изображений

После полной настройки параметров, окончательный вызов — однострочная команда, которая записывает файл Markdown и связанные изображения на диск.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

Если всё прошло успешно, вы увидите:

- `MyReport.md` — представление вашего исходного документа в формате Markdown.  
- `md-resources/` — папка рядом с файлом .md, содержащая все извлечённые изображения (например, `image001.png`, `image002.jpg`).  

**Пример фрагмента Markdown** (автогенерированный Aspose.Words):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **Полезный совет:** Откройте сгенерированный файл `.md` в VS Code или любом просмотрщике Markdown; изображения должны отображаться мгновенно, потому что относительные пути соответствуют структуре папок.

---

## Полный, исполняемый пример

Ниже приведена автономная консольная программа, которую можно вставить в новый проект .NET и запустить. Она создаёт простой документ Word, добавляет изображение, а затем **creates markdown from document**, сохраняя изображение в подпапку.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**Что вы должны увидеть** после запуска:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

Откройте `ExportedDoc.md` — ссылка на изображение будет указывать на `md-resources/sample-image.png`, и картинка отобразится корректно в любом просмотрщике Markdown.

---

## Часто задаваемые варианты

| Сценарий | Как адаптировать код |
|----------|----------------------|
| **Пропустить экспорт изображений** (встроить как Base64) | Omit `ResourceSavingCallback` entirely, or set `args.OutputFileName = null;` inside the callback. |
| **Изменить формат изображения** (например, все PNG) | Inside the callback, modify `args.ResourceFileName` and optionally convert the stream before writing. |
| **Пользовательское имя папки** | Replace `"md-resources/"` with any relative or absolute path you prefer. |
| **Несколько документов в пакете** | Loop over a collection of `Document` objects, reusing the same `MarkdownSaveOptions` instance (just ensure the folder is cleared or uniquely named per run). |

---

## Заключение

Мы только что показали вам **how to create markdown from document**, **export document to markdown** и **save images to subfolder**, используя чистый подход на основе callback. Основные выводы:

- Используйте `MarkdownSaveOptions` для получения тонкого контроля над экспортом.  
- Реализуйте `IResourceSavingCallback`, чтобы направлять изображения в отдельную папку, поддерживая ваш Markdown в порядке.  
- Тот же шаблон работает и для других типов ресурсов (SVG, audio) — просто проверяйте `args.ResourceType`.  

Далее вы можете исследовать **saving document as markdown** с пользовательскими стилями заголовков или интегрировать эту процедуру в ASP.NET Web API, который возвращает ZIP, содержащий файл `.md` и его ресурсы. В любом случае, строительные блоки теперь находятся в вашем наборе инструментов.

Есть вопросы или вы заметили случай, который мы не рассмотрели? Оставьте комментарий ниже, и удачной разработки!

---

![create markdown from document example](placeholder.png "create markdown from document example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}