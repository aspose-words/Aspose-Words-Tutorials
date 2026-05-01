---
category: general
date: 2026-05-01
description: Bir Word belgesini markdown’a dönüştürürken görüntüleri buluta yükleyin.
  Docx’ten görüntüleri nasıl çıkaracağınızı ve Azure Blob depolama alanına nasıl kaydedeceğinizi
  öğrenin.
draft: false
keywords:
- upload images to cloud
- convert word to markdown
- extract images from docx
- convert docx to markdown
- store images azure blob
language: tr
og_description: Bir Word belgesini markdown'a dönüştürürken görüntüleri buluta yükleyin.
  Bu kılavuz, docx dosyasından görüntüleri nasıl çıkaracağınızı ve Azure Blob depolama
  alanına nasıl kaydedeceğinizi gösterir.
og_title: Word'ü Markdown'a Dönüştürürken Görselleri Buluta Yükle
tags:
- Aspose.Words
- C#
- Azure Blob Storage
title: Word'ü Markdown'a Dönüştürürken Görselleri Buluta Yükle
url: /tr/net/programming-with-markdownsaveoptions/upload-images-to-cloud-when-converting-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'ten Markdown'e Dönüştürürken Görselleri Buluta Yükleme

Bir Word dosyasını markdown'a çevirirken **görselleri buluta yükleme** ihtiyacı hiç duydunuz mu? Tek başınıza değilsiniz—geliştiriciler sürekli belge dönüşümü ve varlık yönetimini aynı anda halletmeye çalışıyor ve ikisini de sorunsuz bir akışta yapmak, hareketli bir hedefi yakalamaya çalışmak gibi hissettirebiliyor.  

İyi haber? Aspose.Words ile bir .docx dosyasındaki her resim, grafik veya diyagramı çıkarabilir, doğrudan Azure Blob Storage'a itebilir ve oluşturulan markdown'un bu bulut URL'lerine yerel dosyalar yerine referans vermesini sağlayabilirsiniz. Bu öğreticide, kaynak belgeyi yüklemekten temiz bir markdown dosyası elde etmeye kadar tüm süreci adım adım inceleyeceğiz; markdown dosyanız Azure klasörünüze işaret edecek.

Bu rehberi tamamladığınızda **docx'i markdown'a dönüştürebilecek**, **docx'ten görselleri çıkarabilecek** ve **görselleri Azure Blob'a depolayabilecek** olacaksınız—hepsi sadece birkaç C# satırıyla. Harici araçlar, manuel kopyala‑yapıştırma ve kesinlikle kırık görsel linkleri yok.

## Gereksinimler

- **.NET 6.0** veya daha yeni bir sürüm (kod .NET Core ve .NET Framework üzerinde de çalışır)  
- **Aspose.Words for .NET** (NuGet paketi `Aspose.Words`)  
- Bir **Azure Storage hesabı** ve içinde bir konteyner (ör. `images`) ve paylaşılan erişim anahtarı – dosyaları yüklemek için bağlantı dizesine ihtiyacınız olacak.  
- C# ve async/await hakkında temel bilgi (isteğe bağlı ama faydalı).  

Bu bileşenler elinizdeyse harika—doğrudan çözüme geçelim. Yoksa, son bölümdeki “Önkoşullar” kısmı sizi hızlı kurulum adımlarına yönlendirecek.

## Adım 1: Azure Blob Yardımcısını Kurun (Neden Önemli)

Word belgesine dokunmadan önce, bir bayt dizisini Azure Blob Storage'a itebilen ve herkese açık bir URL döndüren küçük bir yardımcıya ihtiyacımız var. Bu soyutlama, dönüşüm mantığını temiz tutar ve ileride depolama sağlayıcısını değiştirmeyi kolaylaştırır.

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

**Bu yardımcı neden?**  
1. **Sorumlulukların ayrılması** – markdown dönüşüm kodu belge işleme üzerine odaklanır, HTTP detaylarıyla uğraşmaz.  
2. **Yeniden kullanılabilirlik** – `UploadAsync` metodunu uygulamanızın başka yerlerinden (ör. kullanıcı‑yüklediği resimler) çağırabilirsiniz.  
3. **Geleceğe hazırlık** – Amazon S3 veya Google Cloud Storage’a geçiş sadece aynı arayüzün yeni bir implementasyonu ile mümkün olur.

> **İpucu:** Konteynerin erişim seviyesini `Blob` (herkese açık) olarak ayarlayın, ancak bu ayar herkesin görselleri okuyabileceği anlamına gelir. Özel senaryolar için her yükleme başına SAS token üretip bu URL'leri gömmek daha güvenli bir yaklaşımdır.

## Adım 2: Kaynak‑Kaydetme Geri Çağrısını Tanımlayın (Dönüştürürken Yükleme Çekirdeği)

Aspose.Words, bir belgeyi markdown olarak kaydettiğinizde normalde diske yazılacak her kaynağı (resim, grafik vb.) yakalamanıza izin verir. Bir `ResourceSavingCallback` sağlayarak, her kaynağı Azure Blob'a yükleyebilir ve yerel dosya adını bulut URL'siyle değiştirebiliriz.

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

**Burada ne oluyor?**  

- **Çıkarma** – Aspose.Words her resim için bir akış (stream) verir.  
- **Yükleme** – Bu akışı `AzureBlobUploader`'a göndeririz.  
- **Değiştirme** – Markdown yazıcı, gelen herkese açık URL'yi alır ve markdown resim sözdizimine (`![](https://…)`) yazar.  

`args.AlreadyExists = true` ayarladığımız için geçici dosyalar dosya sisteminde birikir; bu, sunucusuz fonksiyonlar için temiz ve durumsuz bir işlemdir.

## Adım 3: Markdown Kaydetme Seçeneklerini Yapılandırın (Her Şeyi Birleştirin)

Şimdi geri çağırmayı Aspose.Words `MarkdownSaveOptions` içine ekliyoruz. Önemli bayraklar `ExportImagesAsBase64 = false` (dış linkler alıyoruz) ve `ResourceSavingCallback = new CloudResourceSaver(uploader)`.

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

**Base64 neden devre dışı bırakılıyor?**  
`ExportImagesAsBase64` true olduğunda, Aspose her resmi doğrudan markdown içine bir data URI olarak gömer. Bu, **görselleri buluta yükleme** amacını boşa çıkar; markdown dosyası şişer ve görseller CDN'den ayrılamaz. Devre dışı bırakarak, Azure Blob'a işaret eden temiz dış linkler elde ederiz—modern bir static‑site jeneratörünün tam olarak beklediği şey.

## Adım 4: Hepsini Bir Araya Getirin – Minimal Bir Konsol Uygulaması

Aşağıda, çalıştırmaya hazır tam bir konsol programı bulunuyor. Yer tutucuları gerçek Azure bağlantı dizesi ve konteyner adıyla değiştirin.

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

### Beklenen Çıktı

`sample.docx` içinde iki resim bulunan bir dosyayla programı çalıştırdığınızda şu çıktı oluşur:

- `output.md` içinde aşağıdaki gibi markdown resim sözdizimi bulunur:

  ```markdown
  ![Image 1](https://myaccount.blob.core.windows.net/images/image001.png)
  ![Image 2

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}