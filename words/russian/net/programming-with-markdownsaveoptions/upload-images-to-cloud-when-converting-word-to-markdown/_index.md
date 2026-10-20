---
category: general
date: 2026-05-01
description: Загружайте изображения в облако при конвертации документа Word в markdown.
  Узнайте, как извлекать изображения из docx и сохранять их в Azure Blob storage.
draft: false
keywords:
- upload images to cloud
- convert word to markdown
- extract images from docx
- convert docx to markdown
- store images azure blob
language: ru
og_description: Загружайте изображения в облако при конвертации документа Word в markdown.
  Это руководство показывает, как извлечь изображения из docx и сохранить их в Azure
  Blob Storage.
og_title: Загружать изображения в облако при конвертации Word в Markdown
tags:
- Aspose.Words
- C#
- Azure Blob Storage
title: Загрузка изображений в облако при конвертации Word в Markdown
url: /ru/net/programming-with-markdownsaveoptions/upload-images-to-cloud-when-converting-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Загрузка изображений в облако при конвертации Word в Markdown

Когда‑нибудь нужно было **загрузить изображения в облако** при преобразовании файла Word в markdown? Вы не одиноки — разработчики постоянно балансируют между конвертацией документов и управлением ресурсами, а объединить оба процесса в едином плавном потоке бывает как попытка поймать движущийся объект.  

Хорошие новости? С помощью Aspose.Words можно извлечь каждую картинку, диаграмму или схему из .docx, сразу отправить её в Azure Blob Storage и позволить сгенерированному markdown ссылаться на эти облачные URL вместо локальных файлов. В этом руководстве мы пройдём весь процесс от загрузки исходного документа до получения чистого markdown‑файла, указывающего на ваш Azure‑бакет.

К концу этого руководства вы сможете **конвертировать docx в markdown**, **извлекать изображения из docx** и **сохранять изображения в Azure Blob** — всё это несколькими строками C#. Никаких внешних инструментов, ручного копирования‑вставки и, конечно, никаких битых ссылок на изображения.

## Что понадобится

- **.NET 6.0** или новее (код работает и на .NET Core, и на .NET Framework)  
- **Aspose.Words for .NET** (NuGet‑пакет `Aspose.Words`)  
- Учётная запись **Azure Storage** с контейнером (например, `images`) и общим ключом доступа — понадобится строка подключения для загрузки файлов.  
- Базовое понимание C# и async/await (необязательно, но полезно).  

Если всё уже готово — отлично, сразу переходим к решению. Если нет, раздел «Prerequisites» в конце подскажет быстрые шаги по настройке.

## Шаг 1: Создание помощника Azure Blob (Зачем это нужно)

Прежде чем трогать документ Word, нам нужен небольшой помощник, умеющий отправлять массив байтов в Azure Blob Storage и возвращать публичный URL. Такая абстракция сохраняет чистоту логики конвертации и упрощает замену провайдера хранилища в будущем.

```csharp
using Azure;
using Azure.Storage.Blobs;
using Azure.Storage.Blobs.Models;

/// <summary>
/// Simple wrapper around Azure Blob Storage for uploading images.
/// </summary>
public class AzureBlobUploader
{
    private readonly BlobContainerClient _container;

    public AzureBlobUploader(string connectionString, string containerName)
    {
        var service = new BlobServiceClient(connectionString);
        _container = service.GetBlobContainerClient(containerName);
        _container.CreateIfNotExists(PublicAccessType.Blob);
    }

    /// <summary>
    /// Uploads the supplied image bytes and returns a publicly accessible URL.
    /// </summary>
    public async Task<string> UploadAsync(string fileName, byte[] content)
    {
        // Ensure the file name is safe for URLs.
        var safeName = Uri.EscapeDataString(fileName);
        var blob = _container.GetBlobClient(safeName);
        using var stream = new MemoryStream(content);
        await blob.UploadAsync(stream, overwrite: true);
        return blob.Uri.ToString(); // This is the URL we’ll embed in markdown.
    }
}
```

**Зачем нужен этот помощник?**  
1. **Разделение ответственности** — код конвертации markdown остаётся сосредоточенным на работе с документом, а не на деталях HTTP.  
2. **Повторное использование** — `UploadAsync` можно вызвать из любой части приложения (например, для пользовательских загрузок).  
3. **Подготовка к будущему** — переход на Amazon S3 или Google Cloud Storage потребует лишь новой реализации того же интерфейса.

> **Pro tip:** Установите уровень доступа контейнера в `Blob` (публичный) только если вас устраивает, что любой может просматривать изображения. Для приватных сценариев генерируйте SAS‑токены для каждой загрузки и используйте их URL.

## Шаг 2: Определение обратного вызова сохранения ресурса (Суть загрузки‑во‑время‑конвертации)

Aspose.Words позволяет перехватывать каждый ресурс (изображение, диаграмму и т.д.), который обычно записывался бы на диск при сохранении документа в markdown. Предоставив `ResourceSavingCallback`, мы можем загрузить каждый ресурс в Azure Blob и заменить локальное имя файла облачным URL.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Callback that uploads each extracted image to Azure Blob Storage
/// and tells Aspose.Words to use the resulting URL instead of a file.
/// </summary>
public class CloudResourceSaver : IResourceSavingCallback
{
    private readonly AzureBlobUploader _uploader;

    public CloudResourceSaver(AzureBlobUploader uploader) => _uploader = uploader;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // args.ResourceFileName contains the default file name (e.g., image001.png)
        // args.ResourceStream gives us the raw bytes.
        var fileName = args.ResourceFileName;

        // Convert the stream to a byte[] for uploading.
        using var ms = new MemoryStream();
        args.ResourceStream.CopyTo(ms);
        var bytes = ms.ToArray();

        // NOTE: Aspose.Words calls this synchronously, so we block on the async upload.
        // In a real‑world service you might use .GetAwaiter().GetResult() or redesign.
        var uploadTask = _uploader.UploadAsync(fileName, bytes);
        var url = uploadTask.GetAwaiter().GetResult();

        // Tell Aspose.Words to use the cloud URL.
        args.ResourceFileName = url;

        // Prevent Aspose.Words from creating a local copy.
        args.AlreadyExists = true;
    }
}
```

**Что происходит?**  

- **Extract** — Aspose.Words предоставляет поток для каждой картинки.  
- **Upload** — Мы передаём этот поток в `AzureBlobUploader`.  
- **Replace** — Писатель markdown получает публичный URL и вставляет его в синтаксис изображения markdown (`![](https://…)`).  

Поскольку мы устанавливаем `args.AlreadyExists = true`, временные файлы не захламляют файловую систему — чистая, безсостояния операция, идеальная для серверлесс‑функций.

## Шаг 3: Настройка параметров сохранения Markdown (Связываем всё вместе)

Теперь внедряем обратный вызов в `MarkdownSaveOptions` Aspose.Words. Важные флаги: `ExportImagesAsBase64 = false` (чтобы получать внешние ссылки) и `ResourceSavingCallback = new CloudResourceSaver(uploader)`.

```csharp
using System;
using System.Threading.Tasks;
using Aspose.Words;
using Aspose.Words.Saving;

public class DocxToMarkdownConverter
{
    private readonly AzureBlobUploader _uploader;

    public DocxToMarkdownConverter(AzureBlobUploader uploader) => _uploader = uploader;

    /// <summary>
    /// Converts a .docx to markdown and uploads all images to Azure Blob.
    /// Returns the path to the generated markdown file.
    /// </summary>
    public async Task<string> ConvertAsync(string inputDocxPath, string outputMarkdownPath)
    {
        // Load the source document (convert word to markdown step starts here).
        var doc = new Document(inputDocxPath);

        // Set up the callback that will upload each image.
        var resourceSaver = new CloudResourceSaver(_uploader);

        // Configure markdown options.
        var mdOptions = new MarkdownSaveOptions
        {
            ExportImagesAsBase64 = false,           // Keep images as external links.
            ResourceSavingCallback = resourceSaver, // Hook that uploads to Azure.
            // Optional: you can tweak heading levels, code block fences, etc.
        };

        // Save the markdown file – Aspose.Words will invoke the callback for each image.
        doc.Save(outputMarkdownPath, mdOptions);

        // The method is synchronous because Aspose.Words API is sync.
        // Wrap in Task.Run if you need true async behavior.
        await Task.CompletedTask;
        return outputMarkdownPath;
    }
}
```

**Почему отключаем Base64?**  
Когда `ExportImagesAsBase64` включён, Aspose встраивает каждую картинку прямо в markdown как data URI. Это противоречит цели **upload images to cloud**, потому что файл markdown разрастается, а изображения скрыты от CDN. Отключив эту опцию, мы получаем чистые внешние ссылки, указывающие на Azure Blob — именно то, что ожидает современный генератор статических сайтов.

## Шаг 4: Собираем всё вместе — минимальное консольное приложение

Ниже полностью готовая к запуску консольная программа. Замените заполнители на вашу реальную строку подключения Azure и имя контейнера.

```csharp
using System;
using System.Threading.Tasks;

class Program
{
    // 👉 Replace these with your own Azure storage details.
    private const string AzureConnectionString = "DefaultEndpointsProtocol=https;AccountName=YOUR_ACCOUNT;AccountKey=YOUR_KEY;EndpointSuffix=core.windows.net";
    private const string ContainerName = "images";

    static async Task Main(string[] args)
    {
        // Simple argument validation.
        if (args.Length != 2)
        {
            Console.WriteLine("Usage: dotnet run <input.docx> <output.md>");
            return;
        }

        var inputPath = args[0];
        var outputPath = args[1];

        // 1️⃣ Initialise the uploader.
        var uploader = new AzureBlobUploader(AzureConnectionString, ContainerName);

        // 2️⃣ Create the converter that knows how to upload while converting.
        var converter = new DocxToMarkdownConverter(uploader);

        // 3️⃣ Run the conversion.
        await converter.ConvertAsync(inputPath, outputPath);

        Console.WriteLine($"✅ Conversion complete! Markdown saved to {outputPath}");
        Console.WriteLine("🖼️  Images have been uploaded to Azure Blob and linked in the markdown.");
    }
}
```

### Ожидаемый вывод

Запуск программы с `sample.docx`, содержащим две картинки, даст:

- `output.md` с синтаксисом изображений markdown, например:

  ```markdown
  ![Image 1](https://myaccount.blob.core.windows.net/images/image001.png)
  ![Image 2

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}