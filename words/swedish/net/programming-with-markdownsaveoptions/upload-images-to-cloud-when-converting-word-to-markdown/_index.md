---
category: general
date: 2026-05-01
description: Ladda upp bilder till molnet medan du konverterar ett Word‑dokument till
  markdown. Lär dig hur du extraherar bilder från docx och lagrar dem i Azure Blob‑lagring.
draft: false
keywords:
- upload images to cloud
- convert word to markdown
- extract images from docx
- convert docx to markdown
- store images azure blob
language: sv
og_description: Ladda upp bilder till molnet medan du konverterar ett Word‑dokument
  till markdown. Den här guiden visar hur du extraherar bilder från docx och lagrar
  dem i Azure Blob Storage.
og_title: Ladda upp bilder till molnet när du konverterar Word till Markdown
tags:
- Aspose.Words
- C#
- Azure Blob Storage
title: Ladda upp bilder till molnet när du konverterar Word till Markdown
url: /sv/net/programming-with-markdownsaveoptions/upload-images-to-cloud-when-converting-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ladda upp bilder till molnet när du konverterar Word till Markdown

Har du någonsin behövt **ladda upp bilder till molnet** medan du omvandlar en Word‑fil till markdown? Du är inte ensam – utvecklare jonglerar ständigt med dokumentkonvertering och resurshantering, och att göra båda i ett smidigt flöde kan kännas som att jaga ett rörligt mål.  

Den goda nyheten? Med Aspose.Words kan du extrahera varje bild, diagram eller figur från en .docx, skicka den direkt till Azure Blob Storage och låta den genererade markdown‑filen referera till dessa moln‑URL:er istället för lokala filer. I den här handledningen går vi igenom hela processen, från att läsa in källdokumentet till att få en ren markdown‑fil som pekar på din Azure‑behållare.

När du är klar med guiden kommer du att kunna **konvertera docx till markdown**, **extrahera bilder från docx** och **lagra bilder i Azure Blob** – allt med bara några rader C#. Inga externa verktyg, ingen manuell kopiering‑och‑klistring och absolut inga trasiga bildlänkar.

## Vad du behöver

- **.NET 6.0** eller senare (koden fungerar även på .NET Core och .NET Framework)  
- **Aspose.Words for .NET** (NuGet‑paket `Aspose.Words`)  
- Ett **Azure Storage‑konto** med en behållare (t.ex. `images`) och en delad åtkomstnyckel – du behöver anslutningssträngen för att ladda upp filer.  
- Grundläggande kunskap om C# och async/await (valfritt men hjälpsamt).  

Om du redan har dessa komponenter på plats, toppen – låt oss hoppa rakt in i lösningen. Om inte, pekar avsnittet “Förutsättningar” i slutet dig åt rätt håll för en snabb installation.

## Steg 1: Skapa en Azure‑Blob‑hjälpare (Varför det är viktigt)

Innan vi ens rör Word‑dokumentet behöver vi en liten hjälparklass som vet hur man skickar en byte‑array till Azure Blob Storage och returnerar en offentlig URL. Denna abstraktion håller konverteringslogiken ren och gör det enkelt att byta lagringsleverantör senare.

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

**Varför den här hjälparen?**  
1. **Separation av ansvar** – markdown‑konverteringskoden fokuserar på dokumenthantering, inte på HTTP‑detaljer.  
2. **Återanvändbarhet** – du kan anropa `UploadAsync` var som helst i din app (t.ex. för användaruppladdade bilder).  
3. **Framtidssäkerhet** – att byta till Amazon S3 eller Google Cloud Storage kräver bara en ny implementation av samma interface.

> **Proffstips:** Ställ in behållarens åtkomstnivå till `Blob` (offentlig) endast om du är okej med att vem som helst kan läsa bilderna. För privata scenarier, generera SAS‑token per uppladdning och bädda in de URL‑erna istället.

## Steg 2: Definiera en Resource‑Saving‑Callback (Kärnan i Upload‑while‑Convert)

Aspose.Words låter dig fånga varje resurs (bild, diagram osv.) som normalt skulle skrivas till disk när du sparar ett dokument som markdown. Genom att tillhandahålla en `ResourceSavingCallback` kan vi ladda upp varje resurs till Azure Blob och ersätta det lokala filnamnet med moln‑URL:en.

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

**Vad händer här?**  

- **Extrahera** – Aspose.Words ger oss en stream för varje bild.  
- **Ladda upp** – Vi överlämnar den streamen till `AzureBlobUploader`.  
- **Ersätt** – Markdown‑skrivaren får den offentliga URL:en och skriver in den i markdown‑bildsyntaxen (`![](https://…)`).  

Eftersom vi sätter `args.AlreadyExists = true` blir inga temporära filer kvar på filsystemet – en ren, tillståndslös operation som är perfekt för serverlösa funktioner.

## Steg 3: Konfigurera Markdown‑Save‑Options (Knyt ihop allt)

Nu väver vi in callback‑en i Aspose.Words `MarkdownSaveOptions`. De viktiga flaggorna är `ExportImagesAsBase64 = false` (så att vi får externa länkar) och `ResourceSavingCallback = new CloudResourceSaver(uploader)`.

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

**Varför vi inaktiverar Base64?**  
När `ExportImagesAsBase64` är true bäddar Aspose in varje bild direkt i markdown‑filen som en data‑URI. Det undergräver syftet med **ladda upp bilder till molnet** eftersom markdown‑filen blir onödigt stor och bilderna hålls gömda från CDN. Genom att stänga av det får vi rena, externa länkar som pekar på Azure Blob – exakt vad en modern static‑site‑generator förväntar sig.

## Steg 4: Sätt ihop allt – En minimal konsolapp

Nedan följer ett komplett, körklart konsolprogram. Byt ut platshållarna mot din faktiska Azure‑anslutningssträng och behållarnamn.

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

### Förväntad output

När du kör programmet med `sample.docx` som innehåller två bilder får du:

- `output.md` som innehåller markdown‑bildsyntax så här:

  ```markdown
  ![Image 1](https://myaccount.blob.core.windows.net/images/image001.png)
  ![Image 2

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}