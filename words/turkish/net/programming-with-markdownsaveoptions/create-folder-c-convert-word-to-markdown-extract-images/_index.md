---
category: general
date: 2026-02-26
description: Word'ü markdown'a dönüştürmeyi, docx'ten resimleri çıkarmayı ve akışı
  dosyaya kopyalamayı tek adımda gösteren bir C# öğretici klasörü oluştur.
draft: false
keywords:
- create folder c#
- convert word to markdown
- extract images from docx
- copy stream to file
language: tr
og_description: Create folder C# öğreticisi, Word'ü markdown'a dönüştürmeyi, docx
  dosyasından resimleri çıkarmayı ve akışı dosyaya kopyalamayı net kod örnekleriyle
  adım adım gösterir.
og_title: C# ile Klasör Oluştur – Word'ü Markdown'a Dönüştür ve Görselleri Çıkar
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: C# ile Klasör Oluştur – Word'ü Markdown'a Dönüştür ve Görselleri Çıkar
url: /tr/net/programming-with-markdownsaveoptions/create-folder-c-convert-word-to-markdown-extract-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Klasör Oluştur C# – Word'ü Markdown'a Dönüştür ve Görselleri Çıkar

Hiç **create folder C#** yaparken bir Word belgesini markdown'a dönüştürüp içindeki tüm resimleri çıkarmak zorunda kaldınız mı? Bu konuda yalnız değilsiniz. Birçok otomasyon hattında dosya sistemi görevlerini, format dönüşümünü ve ikili veri işleme işlemlerini bir arada yürütmek zorunda kalırsınız.  

Bu rehberde tam olarak bunu yapan eksiksiz, çalıştırılabilir bir çözümü adım adım inceleyeceğiz: hedef bir dizin oluşturur, bir `.docx` dosyasını markdown'a dönüştürür, gömülü her resmi çıkarır ve **copy stream to file** mantığını kullanarak resimlerin istediğiniz yere kaydedilmesini sağlar. Harici betikler yok, manuel adımlar yok. Sadece saf C# ve Aspose.Words kütüphanesi.

> **Neler elde edeceksiniz**  
> * Markdown ve varlıklar için hazır, net bir klasör yapısı  
> * Çıkarılan resimlere doğru şekilde referans veren bir markdown dosyası  
> * Herhangi bir .NET projesine ekleyebileceğiniz tam kaynak kodu  

Before we dive, make sure you have:

* .NET 6.0 (veya daha yenisi) SDK yüklü olmalı – kod modern dil özelliklerini kullanıyor.  
* **Aspose.Words for .NET** lisansı (ücretsiz deneme sürümü test için çalışır).  
* Visual Studio 2022 veya tercih ettiğiniz editör.  

Neden gömülü resimler yerine resimleri çıkarmak isteyebileceğinizi merak ediyorsanız, statik site jeneratörlerini düşünün: relatif resim yolları içeren markdown'u severler ve varlıkları ayrı bir klasörde tutmak işleri düzenli ve önbellek‑dostu tutar.

---

## Klasör Oluştur C# ve Çıktı Yapısını Hazırla

İlk olarak, her şeyin saklanacağı bir disk konumuna ihtiyacımız var. Bu adım **create folder C#** eyleminin gerçekleştiği yerdir ve `Directory.CreateDirectory` sayesinde şaşırtıcı derecede basittir. Metot idempotenttir—klasör zaten mevcutsa hata vermez, bu da ekstra kontrollerden tasarruf sağlar.

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

**Neden Önemlidir:**  
Klasörleri önceden oluşturmak, sonraki kaydetme adımlarının `DirectoryNotFoundException` hatasıyla karşılaşmasını engeller. Ayrıca size öngörülebilir bir düzen sağlar: `.md` dosyası için `output/markdown` ve çıkardığımız her resim için `output/MyImages`.

> **Pro tip:** Programı tekrar tekrar çalıştırıyorsanız, eski dosyaları önlemek için önce resim klasörünü temizlemek isteyebilirsiniz (`Directory.GetFiles(imagesFolder).ToList().ForEach(File.Delete);`).

## Aspose.Words Kullanarak Word'ü Markdown'a Dönüştür

Dizin ağacı hazır olduğuna göre, Word belgesini markdown'a dönüştürelim. Aspose.Words işi ağır kaldırıyor—OpenXML ya da üçüncü‑taraf dönüştürücülerle uğraşmaya gerek yok.

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

**Arka planda ne oluyor?**  
`MarkdownSaveOptions`, Aspose'ye markdown sözdizimini üretmesini söyler. Varsayılan olarak, kütüphane resimleri markdown dosyasıyla aynı klasöre otomatik oluşturulmuş adlarla koyar. Bir `ResourceSavingCallback` sağlayarak bu davranışı yakalar ve **copy stream to file** işlemini istediğimiz bir konuma yönlendiririz.

## DOCX'ten Görselleri Çıkar ve Kaydet

Geri çağırma sınıfı `IResourceSavingCallback`'i uygular. İçinde, orijinal resim akışını ve önerilen dosya adını içeren bir `ResourceSavingArgs` nesnesi alırız. Daha sonra bu akışı diske yazar, isterseniz dosyayı yeniden adlandırır ve Aspose'a işlemi tamamladığımızı bildiririz.

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

### Markdown Nasıl Görünecek

Dönüştürmeden sonra, oluşturulan `output.md` şu gibi satırlar içerecek:

```markdown
![Image 1](MyImages/img_picture1.png)
```

`args.ResourceFileName`'i relatif bir yola değiştirdiğimiz için markdown doğrudan oluşturduğumuz klasöre işaret eder. Bu, statik site jeneratörlerinin tam olarak beklediği şeydir.

**Köşe durumları yönetimi:**  
*Belge aynı resim adlarını içeriyorsa*, `img_` öneki ve orijinal ad genellikle çakışmaları önler, ancak mutlak benzersizlik için bir GUID (`Guid.NewGuid()`) da ekleyebilirsiniz.

## Copy stream to file – Görüntü Verisini İşleme

Neden sadece `File.WriteAllBytes` çağırmadığımızı merak edebilirsiniz. Cevap **stream esnekliğinde** yatıyor. `args.Stream` bir memory stream, network stream veya başka bir implementasyon olabilir. `CopyTo` kullanarak tarafsız kalır ve .NET'in tampon boyutlamasını verimli bir şekilde yapmasına izin veririz.

Herhangi bir yerde genel bir stream'i kopyalamanız gerekirse işte kompakt bir yardımcı metot:

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

`ImageSavingCallback` içindeki satır içi kopyayı, tek sorumluluk yaklaşımını tercih ediyorsanız `CopyStreamToFile` çağrısıyla değiştirebilirsiniz.

## Tam Çalıştırılabilir Örnek

Tüm parçaları bir araya getirerek komut satırından çalıştırabileceğiniz bağımsız bir program elde edersiniz:

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

**Beklenen sonuç**

* `output/markdown/output.md` – `![Alt text](MyImages/img_picture1.png)` gibi görüntü referanslarına sahip bir markdown dosyası.  
* `output/MyImages/` – `input.docx` içinde orijinal olarak bulunan her resim için bir PNG/JPEG dosyası.  

Markdown dosyasını herhangi bir görüntüleyicide (VS Code, GitHub veya bir statik site jeneratörü) açın ve resimlerin orijinal Word dosyasındaki konumlarında tam olarak render edildiğini göreceksiniz.

## Sıkça Sorulan Sorular & Sorun Giderme

| Soru | Cevap |
|----------|--------|
| **Hedef klasör zaten dosyalar içeriyorsa ne olur?** | `Directory.CreateDirectory` üzerine yazmaz. Temiz bir çalıştırma ihtiyacınız varsa, silin

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}