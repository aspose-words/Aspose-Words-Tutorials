---
category: general
date: 2026-04-28
description: Узнайте, как задать относительный путь к изображению в Markdown при конвертации
  Word в Markdown, извлекать изображения из Word и создавать папку resources для экспортированных
  изображений.
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: ru
og_description: Установите относительный путь к изображению в markdown при конвертации
  Word в markdown, извлеките изображения из Word и создайте папку resources для экспортированных
  изображений.
og_title: Относительный путь к изображению в markdown – Конвертация Word в Markdown
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: Относительный путь к изображению в markdown – Конвертация Word в Markdown
url: /ru/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# относительный путь к изображению markdown – Конвертация Word в Markdown

Когда‑то вам нужен был **относительный путь к изображению markdown** при **конвертации Word в markdown**? Вы не одиноки. Большинство разработчиков сталкиваются с проблемой, когда сгенерированный Markdown ссылается на изображения в плоской папке, нарушая ожидаемую структуру относительных ссылок в статическом сайте или репозитории GitHub.

В этом руководстве мы пройдем полный, сквозной процесс, который **извлекает изображения из Word**, **создаёт папку ресурсов**, и переписывает ссылки на изображения так, чтобы они использовали чистый *относительный путь к изображению markdown*. К концу вы получите готовый к публикации файл `.md` и аккуратно организованную директорию `Resources`, содержащую каждое изображение, извлечённое из исходного `.docx`.

> **Что вы получите:** один C#‑программный файл (без внешних скриптов), чёткое объяснение *почему* каждый элемент важен, и несколько практических советов, которые можно скопировать‑вставить в свои проекты.

---

## Предварительные требования

Прежде чем погрузиться в код, убедитесь, что у вас есть:

- **.NET 6.0** или новее (можно также целиться в .NET Framework 4.7+, но .NET 6 – оптимальный вариант для новых проектов).
- **Aspose.Words for .NET** (последний NuGet‑пакет на момент написания, версия 23.12). Установите его командой:
  ```bash
  dotnet add package Aspose.Words
  ```
- Word‑документ, действительно содержащий изображения — назовём его `WithImages.docx`.
- Папка, в которой вы хотите разместить выводимый markdown и изображения, например `C:\Projects\MarkdownExport`.

Дополнительные библиотеки не требуются; всё остальное обрабатывается Aspose.Words.

---

## Шаг 1: Загрузить исходный документ Word (отправная точка для convert word to markdown)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*Почему это важно:* загрузка документа даёт нам доступ к внутреннему дереву узлов, которое включает части изображений, которые позже нам понадобится **export images from docx**. Если загрузка не удалась, ни один из последующих шагов не выполнится, поэтому проверьте путь и права доступа к файлу.

---

## Шаг 2: Настроить `MarkdownSaveOptions` с пользовательским обратным вызовом (сердце create resources folder)

`ResourceSavingCallback` позволяет вмешаться каждый раз, когда Aspose.Words хочет записать файл изображения. Внутри обратного вызова мы **создадим подпапку Resources** и скорректируем ссылку, чтобы сгенерированный markdown использовал *относительный путь к изображению markdown*.

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

Обратите внимание, что мы передали `resourcesFolder` в конструктор обратного вызова — это делает путь к папке гибким и избавляет от жёстко прописанных строк в коде.

---

## Шаг 3: Реализовать обратный вызов, который **создаёт папку ресурсов** и переписывает путь

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*Почему это работает:* `args.Stream` содержит необработанные байты изображения. Копируя их в файл внутри нашей папки `Resources`, мы **export images from docx** безопасно. Затем мы заменяем `args.ResourceFileName` на относительный URL (`Resources/image.png`). Когда Aspose.Words позже запишет markdown, он вставит именно эту строку, давая нам желаемый *относительный путь к изображению markdown*.

---

## Шаг 4: Проверить сгенерированный Markdown (как выглядит окончательный вывод)

Откройте `Doc.md` в любом текстовом редакторе. Вы должны увидеть нечто подобное:

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

Главное, что каждая ссылка на изображение указывает на `Resources/...` — это **относительный путь к изображению markdown**, который мы искали.

![пример относительного пути к изображению markdown](example.png "пример относительного пути к изображению markdown")

*Подсказка:* если открыть markdown в просмотрщике, поддерживающем относительные ссылки (предпросмотр VS Code, GitHub или генератор статических сайтов), картинки отобразятся корректно без дополнительной настройки.

---

## Шаг 5: Распространённые подводные камни и профессиональные советы

| Проблема | Почему происходит | Как исправить |
|----------|-------------------|---------------|
| Изображения оказываются в корневой папке вместо `Resources` | Обратный вызов не был привязан или `args.ResourceFileName` не был переопределён. | Убедитесь, что `ResourceSavingCallback` установлен **до** вызова `doc.Save`. |
| Имена файлов содержат недопустимые символы | Word иногда даёт изображениям имена с пробелами или юникод‑символами. | Используйте `Path.GetInvalidFileNameChars()` для очистки `args.ResourceFileName` внутри обратного вызова. |
| Большие документы обрабатываются долго | Каждое изображение записывается синхронно. | Перейдите на асинхронный ввод‑вывод (`await args.Stream.CopyToAsync(fileStream)`) если вы на .NET 6+ и нужна производительность. |
| Относительные пути ломаются при перемещении markdown | Путь относителен расположению markdown‑файла. | Держите `Doc.md` и папку `Resources` вместе, либо измените обратный вызов, чтобы использовать другой относительный префикс (например, `../assets`). |

---

## Шаг 6: Расширение решения (что делать, если нужен больший контроль?)

- **Несколько форматов вывода:** замените `MarkdownSaveOptions` на `HtmlSaveOptions` или `PdfSaveOptions`, оставив тот же обратный вызов — Aspose.Words будет вызывать его для каждого изображения независимо от формата.
- **Пользовательское именование изображений:** если хотите переименовать изображения (например, `figure-01.png`), измените `args.ResourceFileName` внутри обратного вызова перед записью файла.
- **Встраивание изображений как Base64:** задайте `args.ResourceFileName` как data‑URI (`data:image/png;base64,...`) и пропустите запись файла. Это удобно для экспорта в один markdown‑файл.

---

## Заключение

Теперь у вас есть полностью рабочая C#‑программа, которая **конвертирует Word в markdown**, **извлекает изображения из word**, **создаёт папку ресурсов** и гарантирует чистый **относительный путь к изображению markdown** для каждой картинки. Код автономный, работает с последней версией Aspose.Words и может быть добавлен в любой .NET‑проект с минимальными усилиями.

Что дальше? Попробуйте передать сгенерированный markdown в генератор статических сайтов, такой как Hugo или Jekyll, либо поэкспериментируйте с обратным вызовом, чтобы встраивать изображения напрямую как Base64‑строки. Если столкнётесь с особенными случаями — например, SVG‑изображениями или необычно большими файлами — обратитесь к таблице «Распространённые подводные камни»; небольшая правка обычно решает проблему.

Счастливого кодинга, и пусть ваш markdown всегда указывает в правильную папку!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}