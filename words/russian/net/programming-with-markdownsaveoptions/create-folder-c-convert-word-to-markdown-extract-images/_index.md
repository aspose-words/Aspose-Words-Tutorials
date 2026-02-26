---
category: general
date: 2026-02-26
description: Создайте папку C# tutorial, показывающую, как конвертировать Word в markdown,
  извлекать изображения из docx и копировать поток в файл — всё в один шаг.
draft: false
keywords:
- create folder c#
- convert word to markdown
- extract images from docx
- copy stream to file
language: ru
og_description: Учебник по C# от Create folder шаг за шагом показывает, как конвертировать
  Word в markdown, извлекать изображения из docx и копировать поток в файл, с понятными
  примерами кода.
og_title: Создать папку C# – Конвертировать Word в Markdown и извлекать изображения
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: Создать папку C# – Конвертировать Word в Markdown и извлекать изображения
url: /ru/net/programming-with-markdownsaveoptions/create-folder-c-convert-word-to-markdown-extract-images/
---

.

Now produce final output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создать папку C# – Конвертировать Word в Markdown и извлечь изображения

Когда‑нибудь вам нужно было **create folder C#** одновременно преобразовать документ Word в markdown и извлечь из него каждое изображение? Вы не одиноки в этом вопросе. Во многих автоматизационных конвейерах приходится одновременно заниматься задачами файловой системы, конвертацией форматов и обработкой бинарных данных — всё в одном процессе.  

В этом руководстве мы пройдем полный, исполняемый пример, который делает именно это: создает целевой каталог, конвертирует `.docx` в markdown, извлекает каждое встроенное изображение и использует логику **copy stream to file**, чтобы изображения оказались там, где вы хотите. Никаких внешних скриптов, никаких ручных шагов. Только чистый C# и библиотека Aspose.Words.

> **Что вы получите**  
> * Четкая структура папок, готовая для markdown и ресурсов  
> * Файл markdown, который правильно ссылается на извлеченные изображения  
> * Полный исходный код, который можно добавить в любой .NET проект  

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 (или новее) SDK установлен — код использует современные возможности языка.  
* Лицензия на **Aspose.Words for .NET** (бесплатная пробная версия подходит для тестирования).  
* Visual Studio 2022 или ваш любимый редактор.  

Если вам интересно, *почему* стоит извлекать изображения вместо их встраивания, подумайте о генераторах статических сайтов: они любят markdown с относительными путями к изображениям, а хранение ресурсов в отдельной папке делает их упорядоченными и удобными для кэширования.

---

## Создать папку C# и подготовить структуру вывода

Первое, что нам нужно, — место на диске, где будет храниться всё. На этом этапе происходит действие **create folder C#**, и оно удивительно простое благодаря `Directory.CreateDirectory`. Метод идемпотентен — он не бросит исключение, если папка уже существует, что избавляет от дополнительных проверок.

```csharp
using System;
using System.IO;

// Define the base output directory (adjust as needed)
string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");

// Subfolders for markdown and images
string markdownFolder = Path.Combine(baseOutput, "markdown");
string imagesFolder   = Path.Combine(baseOutput, "MyImages");

// Ensure the folders exist
Directory.CreateDirectory(markdownFolder);
Directory.CreateDirectory(imagesFolder);

Console.WriteLine($"Created folders:\n • {markdownFolder}\n • {imagesFolder}");
```

**Почему это важно:**  
Создание папок заранее гарантирует, что последующие операции сохранения не завершатся ошибкой `DirectoryNotFoundException`. Это также дает предсказуемую структуру: `output/markdown` для файла `.md` и `output/MyImages` для каждого изображения, которое мы извлекаем.

> **Pro tip:** Если вы запускаете программу многократно, возможно, захотите сначала очистить папку с изображениями (`Directory.GetFiles(imagesFolder).ToList().ForEach(File.Delete);`), чтобы избежать устаревших файлов.

## Конвертировать Word в Markdown с помощью Aspose.Words

Теперь, когда дерево каталогов готово, давайте преобразуем документ Word в markdown. Aspose.Words делает всю тяжелую работу — без возни с OpenXML или сторонними конвертерами.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX (replace with your actual path)
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
var doc = new Document(inputPath);

// Configure markdown options and attach the image callback (we’ll define it later)
var mdOptions = new MarkdownSaveOptions
{
    // The callback will redirect each extracted image to our custom folder
    ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
};

// Save the markdown file into the previously created folder
string markdownPath = Path.Combine(markdownFolder, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Word document converted to markdown at: {markdownPath}");
```

**Что происходит под капотом?**  
`MarkdownSaveOptions` указывает Aspose генерировать синтаксис markdown. По умолчанию библиотека помещает изображения в ту же папку, что и файл markdown, с автоматически сгенерированными именами. Предоставив `ResourceSavingCallback`, мы перехватываем это поведение и используем **copy stream to file** в выбранном нами месте.

## Извлечь изображения из DOCX и сохранить их

Класс обратного вызова реализует `IResourceSavingCallback`. Внутри мы получаем объект `ResourceSavingArgs`, содержащий исходный поток изображения и предложенное имя файла. Затем мы записываем этот поток на диск, при желании переименовываем файл и сообщаем Aspose, что обработали его.

```csharp
using Aspose.Words.Saving;
using System.IO;

/// <summary>
/// Handles image extraction during markdown conversion.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageSavingCallback(string targetFolder)
    {
        _targetFolder = targetFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the target folder exists (defensive, though we created it earlier)
        Directory.CreateDirectory(_targetFolder);

        // Build a new, friendly file name – you can customize the pattern
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // **Copy stream to file** – the core of the image extraction
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Tell Aspose to use our new path in the markdown reference
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true; // Prevent default saving logic
    }
}
```

### Как будет выглядеть markdown

После конвертации сгенерированный `output.md` будет содержать строки вроде:

```markdown
![Image 1](MyImages/img_picture1.png)
```

Поскольку мы изменили `args.ResourceFileName` на относительный путь, markdown напрямую указывает на созданную нами папку. Это именно то, что ожидают генераторы статических сайтов.

**Обработка граничных случаев:**  
*Если документ содержит дублирующиеся имена изображений*, префикс `img_` плюс оригинальное имя обычно предотвращает столкновения, но можно также добавить GUID (`Guid.NewGuid()`) для абсолютной уникальности.

## Copy stream to file — обработка данных изображения

Возможно, вы задаетесь вопросом, почему мы не просто вызываем `File.WriteAllBytes`. Ответ кроется в **гибкости потоков**. `args.Stream` может быть потоком памяти, сетевым потоком или любой другой реализацией. Используя `CopyTo`, мы остаёмся нейтральными и позволяем .NET эффективно управлять размером буфера.

Вот компактный вспомогательный метод, если вам когда‑нибудь понадобится скопировать общий поток в другое место:

```csharp
/// <summary>
/// Copies any readable stream to a file on disk.
/// </summary>
public static void CopyStreamToFile(Stream source, string destinationPath)
{
    using (var file = new FileStream(destinationPath, FileMode.Create, FileAccess.Write))
    {
        source.CopyTo(file);
    }
}
```

Вы можете заменить встроенное копирование в `ImageSavingCallback` вызовом `CopyStreamToFile`, если предпочитаете подход единой ответственности.

## Полный исполняемый пример

Собрав все части вместе, вы получаете автономную программу, которую можно запустить из командной строки:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the folder structure
        string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");
        string markdownFolder = Path.Combine(baseOutput, "markdown");
        string imagesFolder   = Path.Combine(baseOutput, "MyImages");
        Directory.CreateDirectory(markdownFolder);
        Directory.CreateDirectory(imagesFolder);

        // 2️⃣ Load the DOCX
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(inputPath);

        // 3️⃣ Set up markdown options with our image callback
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
        };

        // 4️⃣ Save as markdown
        string markdownPath = Path.Combine(markdownFolder, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Images folder: {imagesFolder}");
    }
}

// ---------- ImageSavingCallback (same as earlier) ----------
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageSavingCallback(string targetFolder) => _targetFolder = targetFolder;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        Directory.CreateDirectory(_targetFolder);
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true;
    }
}
```

**Ожидаемый результат**

* `output/markdown/output.md` – файл markdown, ссылки на изображения в котором выглядят как `![Alt text](MyImages/img_picture1.png)`.  
* `output/MyImages/` – один файл PNG/JPEG на каждое изображение, которое изначально находилось в `input.docx`.  

Откройте markdown в любом просмотрщике (VS Code, GitHub или генератор статических сайтов), и вы увидите изображения, отрисованные точно в тех местах, где они находились в оригинальном файле Word.

## Часто задаваемые вопросы и устранение неполадок

| Вопрос | Ответ |
|----------|--------|
| **Что если целевая папка уже содержит файлы?** | `Directory.CreateDirectory` не перезапишет. Если нужен чистый запуск, удалите

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}