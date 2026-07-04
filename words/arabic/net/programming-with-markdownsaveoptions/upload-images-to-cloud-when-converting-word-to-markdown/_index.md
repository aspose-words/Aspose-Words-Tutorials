---
category: general
date: 2026-05-01
description: قم بتحميل الصور إلى السحابة أثناء تحويل مستند Word إلى markdown. تعلم
  كيفية استخراج الصور من ملف docx وتخزينها في Azure Blob storage.
draft: false
keywords:
- upload images to cloud
- convert word to markdown
- extract images from docx
- convert docx to markdown
- store images azure blob
language: ar
og_description: حمّل الصور إلى السحابة أثناء تحويل مستند Word إلى markdown. يوضح هذا
  الدليل كيفية استخراج الصور من ملف docx وتخزينها في Azure Blob storage.
og_title: رفع الصور إلى السحابة عند تحويل Word إلى Markdown
tags:
- Aspose.Words
- C#
- Azure Blob Storage
title: رفع الصور إلى السحابة عند تحويل Word إلى Markdown
url: /ar/net/programming-with-markdownsaveoptions/upload-images-to-cloud-when-converting-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# رفع الصور إلى السحابة عند تحويل Word إلى Markdown

هل احتجت يومًا إلى **رفع الصور إلى السحابة** أثناء تحويل ملف Word إلى markdown؟ لست وحدك—المطورون يتعاملون باستمرار مع تحويل المستندات وإدارة الأصول، والقيام بالأمرين في تدفق سلس واحد قد يشعر كأنك تطارد هدفًا متحركًا.  

الأخبار السارة؟ باستخدام Aspose.Words يمكنك استخراج كل صورة، رسم بياني، أو مخطط من ملف .docx، وإرسالها مباشرة إلى Azure Blob Storage، والسماح للـ markdown المُولد بالإشارة إلى عناوين URL السحابية بدلاً من الملفات المحلية. في هذا البرنامج التعليمي سنستعرض العملية بالكامل، بدءًا من تحميل المستند المصدر وصولاً إلى الحصول على ملف markdown نظيف يشير إلى حاوية Azure الخاصة بك.

بنهاية هذا الدليل ستكون قادرًا على **تحويل docx إلى markdown**، **استخراج الصور من docx**، و**تخزين الصور في Azure Blob**—كل ذلك ببضع أسطر فقط من C#. لا أدوات خارجية، لا نسخ‑لصق يدوي، وبالتأكيد لا روابط صور مكسورة.

## ما ستحتاجه

- **.NET 6.0** أو أحدث (الكود يعمل على .NET Core و .NET Framework أيضًا)  
- **Aspose.Words for .NET** (حزمة NuGet `Aspose.Words`)  
- حساب **Azure Storage** مع حاوية (مثال: `images`) ومفتاح وصول مشترك – ستحتاج إلى سلسلة الاتصال لتحميل الملفات.  
- فهم أساسي لـ C# و async/await (اختياري لكنه مفيد).  

إذا كان لديك هذه المكونات بالفعل، رائع—لننتقل مباشرة إلى الحل. إذا لم يكن كذلك، سيشير قسم “المتطلبات المسبقة” في النهاية إلى خطوات إعداد سريعة.

## الخطوة 1: إعداد مساعد Azure Blob (لماذا هو مهم)

قبل أن نتعامل مع مستند Word، نحتاج إلى مساعد صغير يعرف كيفية إرسال مصفوفة بايت إلى Azure Blob Storage وإرجاع عنوان URL عام. هذه التجريدية تحافظ على نظافة منطق التحويل وتسهّل استبدال مزودي التخزين لاحقًا.

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

**لماذا هذا المساعد؟**  
1. **فصل المسؤوليات** – يبقى كود تحويل markdown مركّزًا على معالجة المستند، وليس على تفاصيل HTTP.  
2. **قابلية إعادة الاستخدام** – يمكنك استدعاء `UploadAsync` من أي مكان آخر في تطبيقك (مثال: للصور التي يرفعها المستخدم).  
3. **التحضير للمستقبل** – استبدال Azure بـ Amazon S3 أو Google Cloud Storage يتطلب فقط تنفيذًا جديدًا لنفس الواجهة.

> **نصيحة احترافية:** اضبط مستوى وصول الحاوية إلى `Blob` (عام) فقط إذا كنت لا تمانع في أن يقرأ أي شخص الصور. في السيناريوهات الخاصة، أنشئ رموز SAS لكل عملية رفع وضمّن تلك الروابط بدلاً من ذلك.

## الخطوة 2: تعريف رد نداء حفظ الموارد (جوهر الرفع أثناء التحويل)

يتيح لك Aspose.Words اعتراض كل مورد (صورة، رسم بياني، إلخ) كان سيُكتب عادةً إلى القرص عند حفظ المستند كـ markdown. من خلال توفير `ResourceSavingCallback`، يمكننا رفع كل مورد إلى Azure Blob واستبدال اسم الملف المحلي بعنوان URL السحابة.

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

**ما الذي يحدث هنا؟**  

- **استخراج** – Aspose.Words يزودنا بتدفق (stream) لكل صورة.  
- **رفع** – نسلم ذلك التدفق إلى `AzureBlobUploader`.  
- **استبدال** – كاتب markdown يتلقى عنوان URL العام ويكتبها في صيغة صورة markdown (`![](https://…)`).  

نظرًا لأننا عيّننا `args.AlreadyExists = true`، لا توجد ملفات مؤقتة تملأ نظام الملفات—عملية نظيفة ولا حالة لها مثالية للوظائف بدون خادم.

## الخطوة 3: تكوين خيارات حفظ Markdown (ربط كل شيء معًا)

الآن نقوم بدمج رد النداء في `MarkdownSaveOptions` الخاص بـ Aspose.Words. العلامات الحاسمة هي `ExportImagesAsBase64 = false` (للحصول على روابط خارجية) و `ResourceSavingCallback = new CloudResourceSaver(uploader)`.

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

**لماذا نُعطّل Base64؟**  
عندما تكون `ExportImagesAsBase64` مفعلة، يقوم Aspose بدمج كل صورة مباشرةً في markdown كـ data URI. هذا يُفقد الهدف من **رفع الصور إلى السحابة** لأن ملف markdown يزداد حجماً وتظل الصور مخفية عن CDN. بإيقافها نحصل على روابط خارجية نظيفة تشير إلى Azure Blob—بالضبط ما يتوقعه مولد المواقع الثابتة الحديث.

## الخطوة 4: جمع كل شيء معًا – تطبيق Console بسيط

فيما يلي برنامج console كامل وجاهز للتنفيذ. استبدل القيم النائبة بسلسلة الاتصال الفعلية لـ Azure واسم الحاوية.

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

### الناتج المتوقع

تشغيل البرنامج مع `sample.docx` الذي يحتوي على صورتين سيُنتج:

- `output.md` يحتوي على صيغة صورة markdown مثل:

  ```markdown
  ![Image 1](https://myaccount.blob.core.windows.net/images/image001.png)
  ![Image 2
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}