---
category: general
date: 2026-04-07
description: Word'ü Markdown olarak kaydedin ve docx'ten görselleri bir geri arama
  (callback) kullanarak çıkarın. Geri aramayı (callback) kullanarak markdown görseller
  klasörünü verimli bir şekilde nasıl depolayacağınızı öğrenin.
draft: false
keywords:
- save word as markdown
- extract images from docx
- how to use callback
- markdown images folder
language: tr
og_description: Word'ü Markdown olarak kaydedin ve docx'ten görselleri bir geri arama
  (callback) kullanarak çıkarın. Bu rehber, geri arama kullanarak bir markdown görseller
  klasörü oluşturmayı gösterir.
og_title: Word'ü Markdown olarak kaydedin – Tam Adım Adım Kılavuz
tags:
- Aspose.Words
- C#
- Markdown
- Image Extraction
title: Word'ü Özel Resim Klasörüyle Markdown Olarak Kaydet – Tam Kılavuz
url: /tr/net/programming-with-markdownsaveoptions/save-word-as-markdown-with-custom-image-folder-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'ü Markdown Olarak Kaydet – Tam Adım‑Adım Kılavuz

Hiç **Word'ü Markdown olarak kaydetmek** gerektiğinde gömülü resimlerle ne yapacağınızdan emin olmadınız mı? Tek başınıza değilsiniz. Birçok projede markdown çıktısı harika görünür—*ta ki* resim bağlantılarının bozuk olduğunu fark edene kadar, çünkü dosyalar Word paketinden hiç çıkmamıştır.  

İyi haber, Aspose.Words size **docx'ten resimleri çıkarmanın** temiz bir yolunu sunar ve istediğiniz yere yerleştirmenizi sağlar; markdown resim klasörünü kontrol etmenizi sağlayan bir **callback** kullanarak. Bu öğreticide, bir `.docx` dosyasını yüklemekten, düzenli bir PNG (veya sahip olduğunuz herhangi bir format) klasörü ve onlara işaret eden bir markdown dosyası elde etmeye kadar tüm süreci adım adım göstereceğiz.

Bu kılavuzun sonunda şunları yapabilecek:

* Tek bir kod satırıyla herhangi bir Word belgesini Markdown'a dönüştürmek.  
* Her resmi otomatik olarak ayrı bir `images` alt klasörüne dökmek.  
* Dosya adlarını özelleştirerek çakışma olmamasını sağlamak, kaynakta onlarca resim olsa bile.  

Harici betikler yok, manuel kopyala‑yapıştır yok—sadece saf C# ve Aspose.Words.

## Önkoşullar

İlerlemeye başlamadan önce şunların olduğundan emin olun:

* **Aspose.Words for .NET** (en son kararlı sürüm; yazı zamanı 24.9).  
* .NET geliştirme ortamı (Visual Studio, Rider veya `dotnet` CLI).  
* En az bir resim içeren bir Word belgesi (`.docx`) — örnek olarak `DocWithImages.docx`.  

Aspose.Words'ı daha önce hiç kullanmadıysanız endişelenmeyin. Kütüphane tamamen yönetilen bir yapıya sahiptir, COM interop gerektirmez ve .NET 6+ ile .NET Framework 4.8'de çalışır.

## 1. Adım – Projeyi Kurun ve Paketi Yükleyin

İlk olarak, yeni bir console uygulaması oluşturun (veya kodu mevcut bir projeye ekleyin).

```bash
dotnet new console -n WordToMarkdownDemo
cd WordToMarkdownDemo
dotnet add package Aspose.Words
```

> **Pro ipucu:** .NET 6 hedefliyorsanız, varsayılan `Program.cs` zaten üst‑seviye ifadeler kullanır, bu da örneği kısa tutar.

## 2. Adım – Resim Kaydetmeyi Kontrol Eden Bir Callback Oluşturun

Aspose.Words, yazması gereken her dış kaynağı (resimler, CSS, vb.) için `IResourceSavingCallback.ResourceSaving` metodunu çağırır. Bu arayüzü uygulayarak **markdown resim klasörünün** nasıl oluşturulacağı üzerinde tam yetki elde ederiz.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Handles the saving of resources (e.g., images) when a document is converted to Markdown.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    // Folder where we want to dump the images.
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        // Ensure the folder exists before the first write.
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique filename: img_<guid>.<originalExtension>
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";

        // Full path where the image will be saved.
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        // Copy the incoming stream to our file.
        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        // Tell Aspose we’ve handled the write; skip its default behavior.
        args.Cancel = true;
    }
}
```

### Neden bir callback kullanmalı?

* **Granüler kontrol** – klasör yapısını ve adlandırma şemasını siz belirlersiniz.  
* **Performans** – akışı bir kez yazarak kütüphanenin çift‑yazma geri dönüşünü önlersiniz.  
* **Esneklik** – bu noktada loglama, resim‑optimizasyonu ekleyebilir veya bulut depolamaya yükleyebilirsiniz.  

## 3. Adım – Word Belgesini Yükleyin

Callback hazır olduğuna göre, Aspose.Words'ı kaynak dosyaya yönlendirmemiz yeterli.

```csharp
// Path to the source .docx (adjust as needed).
string sourcePath = Path.Combine("YOUR_DIRECTORY", "DocWithImages.docx");

// Load the document into memory.
Document doc = new Document(sourcePath);
```

> **Dosya bulunamazsa ne olur?**  
> `Document` bir `FileNotFoundException` fırlatır. Dinamik yollar bekliyorsanız yüklemeyi bir `try/catch` bloğuna alın.

## 4. Adım – MarkdownSaveOptions'ı Bağlayın

`MarkdownSaveOptions` sınıfı, az önce oluşturduğumuz callback'i bağlamamıza izin verir. Ayrıca resimlerin markdown dosyasına göre konumlanacağı klasörü ayarlarız.

```csharp
// Define where we want the images folder to sit.
string markdownFolder = Path.Combine("YOUR_DIRECTORY", "markdown-output");
string imagesSubFolder = Path.Combine(markdownFolder, "images");

// Ensure the markdown output directory exists.
Directory.CreateDirectory(markdownFolder);

// Create the save options and attach the callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image.
    ResourceSavingCallback = new MyMarkdownResourceCallback(imagesSubFolder),

    // Optional: keep image references relative to the markdown file.
    ImagesFolder = "images"
};
```

`ImagesFolder` özelliği, Aspose'ye `![Alt text](images/img_123.png)` gibi markdown linkleri oluşturmasını söyler. Callback içinde `ResourceFileName`'i de ayarladığımız için gerçek dosya tam olarak oraya kaydedilir.

## 5. Adım – Markdown Olarak Kaydedin ve Sonucu Doğrulayın

Son olarak, markdown dosyasını yazarız. Callback zaten `images` alt‑klasörünü doldurmuş olacaktır.

```csharp
// Destination markdown file.
string markdownPath = Path.Combine(markdownFolder, "Doc.md");

// Save the document.
doc.Save(markdownPath, mdOptions);

// Quick sanity check – list the generated files.
Console.WriteLine("Markdown saved to: " + markdownPath);
Console.WriteLine("Extracted images:");
foreach (var img in Directory.GetFiles(imagesSubFolder))
{
    Console.WriteLine("  • " + Path.GetFileName(img));
}
```

### Beklenen çıktı

Programı çalıştırdığınızda aşağıdakine benzer bir çıktı almanız gerekir:

```
Markdown saved to: C:\Project\markdown-output\Doc.md
Extracted images:
  • img_5c2a1f8b-3e7b-4d9a-9c1f-2b6e5f9d9a3c.png
  • img_a7d4c9e2-1f55-4c2b-8f6a-9e1b2c3d4e5f.jpg
```

`Doc.md` dosyasını herhangi bir markdown görüntüleyicide açın; `images` klasörüne doğru işaret eden resim linklerini göreceksiniz.

---

## Sık Sorulan Sorular (SSS)

### **docx'ten resimleri çıkarmak** için markdown'a dönüştürmeden nasıl yapılır?

Aynı `MyMarkdownResourceCallback`'i yeniden kullanabilir, ancak `doc.Save("images.zip", SaveFormat.Zip)` ile besleyebilirsiniz. Callback her resim için hâlâ tetiklenir ve resimleri istediğiniz yere yerleştirmenizi sağlar.

### Farklı **resim formatlarına** ihtiyacım olsaydı ne olur?

`args.FileName` zaten orijinal uzantıyı (`.png`, `.jpg`, vb.) içerir. Tüm resimleri tek bir formata dönüştürmeniz gerekiyorsa, akışı yazmadan önce `ResourceSaving` içinde bir dönüşüm adımı ekleyin.

### Her belge için **markdown resim klasörünü** özelleştirebilir miyim?

Kesinlikle. Callback, klasör yolunu yapıcı (constructor) aracılığıyla alır, bu yüzden toplu işlemde her belge için farklı bir klasörle yeni bir callback örneği oluşturabilirsiniz.

### Bu, **büyük belgeler** (yüzlerce resim) ile çalışır mı?

Evet. Callback, resmi doğrudan diske akıtarak bellek kullanımını düşük tutar. Yeterli disk alanı olduğundan ve işletim sisteminin dosya‑handle sınırlarına takılmadığınızdan emin olun.

## Tam Çalışan Örnek

Aşağıda, tamamen kopyala‑yapıştır‑hazır program yer almaktadır. `YOUR_DIRECTORY` ifadesini ortamınıza uygun mutlak ya da göreli bir yol ile değiştirin.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        args.Cancel = true;
    }
}

class Program
{
    static void Main()
    {
        // Adjust these paths.
        string baseDir = Path.Combine(Environment.CurrentDirectory, "demo");
        string sourceDoc = Path.Combine(baseDir, "DocWithImages.docx");
        string markdownDir = Path.Combine(baseDir, "markdown-output");
        string imagesDir = Path.Combine(markdownDir, "images");
        string markdownFile = Path.Combine(markdownDir, "Doc.md");

        // Load the document.
        Document doc;
        try
        {
            doc = new Document(sourceDoc);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // Configure save options with our callback.
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyMarkdownResourceCallback(imagesDir),
            ImagesFolder = "images"
        };

        // Ensure output folder exists.
        Directory.CreateDirectory(markdownDir);

        // Save as markdown.
        doc.Save(markdownFile, mdOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownFile}");
        Console.WriteLine("🖼️ Extracted images:");
        foreach (var file in Directory.GetFiles(imagesDir))
            Console.WriteLine($"   - {Path.GetFileName(file)}");
    }
}
```

Programı çalıştırın (`dotnet run`) ve `images` alt‑klasörünü içeren yeni oluşturulmuş bir `Doc.md` dosyasını göreceksiniz.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}