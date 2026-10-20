---
category: general
date: 2026-05-01
description: वर्ड दस्तावेज़ को मार्कडाउन में बदलते समय छवियों को क्लाउड पर अपलोड करें।
  जानिए कैसे docx से छवियों को निकालें और उन्हें Azure Blob स्टोरेज में संग्रहित करें।
draft: false
keywords:
- upload images to cloud
- convert word to markdown
- extract images from docx
- convert docx to markdown
- store images azure blob
language: hi
og_description: वर्ड दस्तावेज़ को मार्कडाउन में बदलते समय छवियों को क्लाउड पर अपलोड
  करें। यह गाइड दिखाता है कि कैसे docx से छवियों को निकालें और उन्हें Azure Blob स्टोरेज
  में संग्रहित करें।
og_title: वर्ड को मार्कडाउन में बदलते समय छवियों को क्लाउड पर अपलोड करें
tags:
- Aspose.Words
- C#
- Azure Blob Storage
title: वर्ड को मार्कडाउन में बदलते समय छवियों को क्लाउड पर अपलोड करें
url: /hi/net/programming-with-markdownsaveoptions/upload-images-to-cloud-when-converting-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word को Markdown में बदलते समय इमेजेज़ को क्लाउड पर अपलोड करना

क्या आपको कभी Word फ़ाइल को Markdown में बदलते समय **इमेजेज़ को क्लाउड पर अपलोड** करने की ज़रूरत पड़ी है? आप अकेले नहीं हैं—डेवलपर्स लगातार डॉक्यूमेंट कन्वर्ज़न और एसेट मैनेजमेंट को संभालते रहते हैं, और दोनों को एक ही सुगम प्रक्रिया में करना कभी‑कभी चलती हुई लक्ष्य को पकड़ने जैसा लगता है।  

अच्छी खबर? Aspose.Words के साथ आप .docx से हर तस्वीर, चार्ट या डायग्राम निकाल सकते हैं, उसे सीधे Azure Blob Storage में पुश कर सकते हैं, और जेनरेटेड Markdown को उन क्लाउड URLs की ओर इशारा करने दे सकते हैं बजाय लोकल फ़ाइलों के। इस ट्यूटोरियल में हम पूरे प्रोसेस को देखेंगे, स्रोत डॉक्यूमेंट को लोड करने से लेकर एक साफ़ Markdown फ़ाइल बनाने तक जो आपके Azure बकेट की ओर इशारा करती है।

इस गाइड के अंत तक आप **docx को markdown में बदल** सकेंगे, **docx से इमेजेज़ निकाल** सकेंगे, और **इमेजेज़ को Azure Blob में स्टोर** कर सकेंगे—सिर्फ कुछ ही C# लाइनों के साथ। कोई बाहरी टूल नहीं, कोई मैनुअल कॉपी‑पेस्ट नहीं, और निश्चित रूप से कोई टूटे हुए इमेज लिंक नहीं।

## आपको क्या चाहिए

- **.NET 6.0** या बाद का (कोड .NET Core और .NET Framework पर भी काम करता है)  
- **Aspose.Words for .NET** (NuGet पैकेज `Aspose.Words`)  
- एक **Azure Storage account** जिसमें एक कंटेनर हो (जैसे `images`) और एक शेयरड एक्सेस की – फ़ाइलें अपलोड करने के लिए आपको कनेक्शन स्ट्रिंग चाहिए होगी।  
- C# और async/await की बुनियादी समझ (वैकल्पिक लेकिन उपयोगी)।  

यदि आपके पास ये सभी चीज़ें पहले से हैं, तो बढ़िया—चलिए सीधे समाधान की ओर बढ़ते हैं। यदि नहीं, तो अंत में दिया गया “Prerequisites” सेक्शन आपको तेज़ सेटअप स्टेप्स की ओर निर्देशित करेगा।

## चरण 1: Azure Blob हेल्पर सेट अप करें (यह क्यों महत्वपूर्ण है)

Word डॉक्यूमेंट को छूने से पहले, हमें एक छोटा हेल्पर चाहिए जो बाइट एरे को Azure Blob Storage में पुश करना और एक पब्लिक URL रिटर्न करना जानता हो। यह एब्स्ट्रैक्शन कन्वर्ज़न लॉजिक को साफ़ रखता है और बाद में स्टोरेज प्रोवाइडर बदलना आसान बनाता है।

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

**इस हेल्पर की आवश्यकता क्यों?**  
1. **Separation of concerns** – markdown कन्वर्ज़न कोड डॉक्यूमेंट हैंडलिंग पर केंद्रित रहता है, HTTP विवरणों पर नहीं।  
2. **Reusability** – आप अपने ऐप में कहीं भी `UploadAsync` को कॉल कर सकते हैं (जैसे, यूज़र‑अपलोडेड तस्वीरों के लिए)।  
3. **Future‑proofing** – Amazon S3 या Google Cloud Storage में स्विच करने के लिए केवल उसी इंटरफ़ेस की नई इम्प्लीमेंटेशन चाहिए होगी।

> **Pro tip:** कंटेनर का एक्सेस लेवल `Blob` (पब्लिक) तभी सेट करें जब आप चाहते हों कि कोई भी इमेज देख सके। प्राइवेट परिस्थितियों में, प्रत्येक अपलोड के लिए SAS टोकन जेनरेट करें और उन URLs को एम्बेड करें।

## चरण 2: Resource‑Saving Callback परिभाषित करें (Upload‑While‑Convert का कोर)

Aspose.Words आपको हर रिसोर्स (इमेज, चार्ट, आदि) को इंटरसेप्ट करने देता है जो सामान्यतः डॉक्यूमेंट को Markdown के रूप में सेव करने पर डिस्क पर लिखा जाता। `ResourceSavingCallback` प्रदान करके, हम प्रत्येक रिसोर्स को Azure Blob में अपलोड कर सकते हैं और लोकल फ़ाइलनाम को क्लाउड URL से बदल सकते हैं।

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

- **Extract** – Aspose.Words प्रत्येक इमेज के लिए हमें एक स्ट्रीम देता है।  
- **Upload** – हम उस स्ट्रीम को `AzureBlobUploader` को देते हैं।  
- **Replace** – Markdown राइटर पब्लिक URL प्राप्त करता है और उसे markdown इमेज सिंटैक्स (`![](https://…)`) में लिखता है।  

क्योंकि हमने `args.AlreadyExists = true` सेट किया है, कोई टेम्पररी फ़ाइलें फ़ाइल सिस्टम को गंदा नहीं करतीं—एक साफ़, स्टेटलेस ऑपरेशन जो सर्वरलेस फ़ंक्शन्स के लिए परफेक्ट है।

## चरण 3: Markdown Save Options कॉन्फ़िगर करें (सब कुछ जोड़ें)

अब हम कॉलबैक को Aspose.Words के `MarkdownSaveOptions` में जोड़ते हैं। महत्वपूर्ण फ़्लैग्स हैं `ExportImagesAsBase64 = false` (ताकि हमें एक्सटर्नल लिंक मिलें) और `ResourceSavingCallback = new CloudResourceSaver(uploader)`।

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

**हम Base64 को क्यों डिसेबल करते हैं?**  
जब `ExportImagesAsBase64` true होता है, Aspose हर तस्वीर को सीधे markdown में डेटा URI के रूप में एम्बेड कर देता है। यह **इमेजेज़ को क्लाउड पर अपलोड** करने के उद्देश्य को नष्ट कर देता है क्योंकि markdown फ़ाइल का आकार बढ़ जाता है और इमेजेज़ CDN से छिपी रहती हैं। इसे बंद करके हमें साफ़, एक्सटर्नल लिंक मिलते हैं जो Azure Blob की ओर इशारा करते हैं—बिल्कुल वही जो एक आधुनिक static‑site जेनरेटर की अपेक्षा होती है।

## चरण 4: सब कुछ मिलाएँ – एक मिनिमल कंसोल ऐप

नीचे एक पूर्ण, तैयार‑चलाने योग्य कंसोल प्रोग्राम दिया गया है। प्लेसहोल्डर्स को अपने वास्तविक Azure कनेक्शन स्ट्रिंग और कंटेनर नाम से बदलें।

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

### अपेक्षित आउटपुट

जब आप प्रोग्राम को `sample.docx` के साथ चलाते हैं जिसमें दो तस्वीरें हैं, तो यह उत्पन्न करेगा:

- `output.md` जिसमें markdown इमेज सिंटैक्स होगा जैसे:

  ```markdown
  ![Image 1](https://myaccount.blob.core.windows.net/images/image001.png)
  ![Image 2
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}