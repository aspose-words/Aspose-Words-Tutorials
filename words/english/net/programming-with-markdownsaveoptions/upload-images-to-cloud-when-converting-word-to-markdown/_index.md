---
category: general
date: 2026-05-01
description: Upload images to cloud while converting a Word document to markdown.
  Learn how to extract images from docx and store them in Azure Blob storage.
draft: false
keywords:
- upload images to cloud
- convert word to markdown
- extract images from docx
- convert docx to markdown
- store images azure blob
language: en
og_description: Upload images to cloud while converting a Word document to markdown.
  This guide shows how to extract images from docx and store them in Azure Blob storage.
og_title: Upload Images to Cloud When Converting Word to Markdown
tags:
- Aspose.Words
- C#
- Azure Blob Storage
title: Upload Images to Cloud When Converting Word to Markdown
url: /net/programming-with-markdownsaveoptions/upload-images-to-cloud-when-converting-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Upload Images to Cloud When Converting Word to Markdown

Ever needed to **upload images to cloud** while turning a Word file into markdown? You're not the only one—developers constantly juggle document conversion and asset management, and doing both in one smooth flow can feel like chasing a moving target.  

The good news? With Aspose.Words you can extract every picture, chart, or diagram from a .docx, push it straight to Azure Blob Storage, and let the generated markdown reference those cloud URLs instead of local files. In this tutorial we’ll walk through the whole process, from loading the source document to ending up with a clean markdown file that points at your Azure bucket.

By the end of this guide you’ll be able to **convert docx to markdown**, **extract images from docx**, and **store images Azure Blob**—all with just a few lines of C#. No external tools, no manual copy‑pasting, and certainly no broken image links.

## What You’ll Need

- **.NET 6.0** or later (the code works on .NET Core and .NET Framework as well)  
- **Aspose.Words for .NET** (NuGet package `Aspose.Words`)  
- An **Azure Storage account** with a container (e.g., `images`) and a shared access key – you’ll need the connection string to upload files.  
- A basic understanding of C# and async/await (optional but helpful).  

If you already have these pieces in place, great—let’s jump straight into the solution. If not, the “Prerequisites” section at the end will point you to quick setup steps.

## Step 1: Set Up Azure Blob Helper (Why It Matters)

Before we even touch the Word document, we need a tiny helper that knows how to push a byte array to Azure Blob Storage and return a public URL. This abstraction keeps the conversion logic clean and makes it easy to swap storage providers later.

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

**Why this helper?**  
1. **Separation of concerns** – the markdown conversion code stays focused on document handling, not on HTTP details.  
2. **Reusability** – you can call `UploadAsync` from anywhere else in your app (e.g., for user‑uploaded pictures).  
3. **Future‑proofing** – swapping to Amazon S3 or Google Cloud Storage only requires a new implementation of the same interface.

> **Pro tip:** Set the container’s access level to `Blob` (public) only if you’re okay with anyone reading the images. For private scenarios, generate SAS tokens per upload and embed those URLs instead.

## Step 2: Define a Resource‑Saving Callback (The Core of Upload‑While‑Convert)

Aspose.Words lets you intercept every resource (image, chart, etc.) that would normally be written to disk when you save a document as markdown. By providing a `ResourceSavingCallback`, we can upload each resource to Azure Blob and replace the local filename with the cloud URL.

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

**What’s happening here?**  

- **Extract** – Aspose.Words gives us a stream for each image.  
- **Upload** – We hand that stream to `AzureBlobUploader`.  
- **Replace** – The markdown writer receives the public URL and writes it into the markdown image syntax (`![](https://…)`).  

Because we set `args.AlreadyExists = true`, no temporary files clutter the filesystem—a clean, stateless operation perfect for serverless functions.

## Step 3: Configure Markdown Save Options (Tie Everything Together)

Now we stitch the callback into the Aspose.Words `MarkdownSaveOptions`. The crucial flags are `ExportImagesAsBase64 = false` (so we get external links) and `ResourceSavingCallback = new CloudResourceSaver(uploader)`.

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

**Why we disable Base64?**  
When `ExportImagesAsBase64` is true, Aspose embeds every picture directly into the markdown as a data URI. That defeats the purpose of **upload images to cloud** because the markdown file balloons in size and the images stay hidden from the CDN. By turning it off we get clean, external links that point at Azure Blob—exactly what a modern static‑site generator expects.

## Step 4: Put It All Together – A Minimal Console App

Below is a complete, ready‑to‑run console program. Replace the placeholders with your actual Azure connection string and container name.

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

### Expected Output

Running the program with `sample.docx` that contains two pictures will produce:

- `output.md` containing markdown image syntax like:

  ```markdown
  ![Image 1](https://myaccount.blob.core.windows.net/images/image001.png)
  ![Image 2

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}