---
category: general
date: 2026-03-30
description: Aspose.Words kullanarak markdown'ten resimleri çıkarırken ve belgeyi
  markdown olarak kaydederken C#'ta markdown dosyalarını nasıl kaydederiz.
draft: false
keywords:
- how to save markdown
- extract images from markdown
- save document as markdown
- markdown resource handling
- C# markdown export
language: tr
og_description: Markdown'ı hızlı bir şekilde nasıl kaydedilir? Markdown'tan resimleri
  çıkarmayı ve belgeyi tam bir kod örneğiyle markdown olarak kaydetmeyi öğrenin.
og_title: Markdown Nasıl Kaydedilir – Tam C# Rehberi
tags:
- C#
- Markdown
- Aspose.Words
title: Markdown Nasıl Kaydedilir – Görsel Çıkarma ile Tam Rehber
url: /tr/net/programming-with-markdownsaveoptions/how-to-save-markdown-full-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Markdown Nasıl Kaydedilir – Tam C# Rehberi

Hiç **markdown nasıl kaydedilir** diye merak ettiniz mi ve gömülü tüm resimlerin bozulmadan kalmasını istediniz mi? Tek başınıza değilsiniz. Birçok geliştirici, kütüphanelerinin resimleri rastgele bir klasöre atması ya da daha da kötüsü hiç eklememesiyle karşılaşıyor. İyi haber? Birkaç C# satırı ve Aspose.Words ile bir belgeyi markdown olarak dışa aktarabilir, tüm resimleri çıkarabilir ve her dosyanın tam olarak nereye kaydedileceğini kontrol edebilirsiniz.

Bu öğreticide gerçek bir senaryoyu adım adım inceleyeceğiz: bir `Document` nesnesi alıp, `MarkdownSaveOptions` yapılandırması yaparak kaydediciyi her resmi nereye koyacağını söyleyeceğiz. Sonunda **belgeyi markdown olarak kaydet**, **markdown'tan resimleri çıkar** ve yayınlamaya hazır düzenli bir klasör yapısına sahip olacaksınız. Belirsiz referanslar yok—sadece kopyala‑yapıştır yapabileceğiniz tam, çalıştırılabilir bir örnek.

## Gerekenler

- **.NET 6+** (herhangi bir yeni SDK çalışır)
- **Aspose.Words for .NET** (NuGet paketi `Aspose.Words`)
- C# sözdizimi hakkında temel bir anlayış (basit tutacağız)
- Mevcut bir `Document` örneği (demo amaçlı bir tane oluşturacağız)

Eğer bunlara sahipseniz, hemen başlayalım.

## Adım 1: Projeyi Kurun ve Ad Alanlarını İçe Aktarın

İlk olarak yeni bir konsol uygulaması oluşturun (veya mevcut çözümünüze entegre edin). Ardından Aspose.Words paketini ekleyin:

```bash
dotnet add package Aspose.Words
```

Şimdi gerekli ad alanlarını içe aktarın:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

> **Pro tip:** `using` ifadelerinizi dosyanın en üstünde tutun; bu, kodun hem insanlar hem de AI ayrıştırıcıları tarafından daha kolay taranmasını sağlar.

## Adım 2: Örnek Bir Belge Oluşturun (veya Kendi Belgenizi Yükleyin)

Demonstrasyon için bir paragraf ve gömülü bir resim içeren küçük bir belge oluşturacağız. Eğer zaten bir kaynak dosyanız varsa bu bölümü `Document.Load("YourFile.docx")` ile değiştirin.

```csharp
// Step 2: Build a simple document with an image
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Add some text
builder.Writeln("Hello, Markdown world!");

// Insert an image from disk (make sure the path exists)
string imagePath = @"YOUR_DIRECTORY/sample-image.png";
builder.InsertImage(imagePath);
```

> **Neden önemli:** Resmi atlayarsanız, daha sonra *çıkarılacak* bir şey kalmaz ve geri çağırmanın çalıştığını görmezsiniz.

## Adım 3: MarkdownSaveOptions'ı Resource‑Saving Callback ile Yapılandırın

İşte çözümün kalbi. `ResourceSavingCallback` **her** dış kaynağa—resimler, yazı tipleri, CSS vb.—tetiklenir. Bunu, özel bir `Resources` alt klasörü oluşturmak ve her dosyaya benzersiz bir ad vermek için kullanacağız.

```csharp
// Step 3: Define markdown save options and attach a callback
var markdownSaveOptions = new MarkdownSaveOptions
{
    // This delegate runs for each resource the saver wants to write out
    ResourceSavingCallback = (sender, args) =>
    {
        // Ensure the Resources folder exists (creates it only once)
        string resourcesFolder = @"YOUR_DIRECTORY/Resources/";
        Directory.CreateDirectory(resourcesFolder);

        // Build a unique filename: img_0.png, img_1.jpg, etc.
        string resourceFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";

        // Tell the saver where to place the file
        args.SavePath = Path.Combine(resourcesFolder, resourceFileName);
    }
};
```

**Ne oluyor?**  
- `args.Index` sıfır‑tabanlı bir sayıcıdır, benzersizliği garanti eder.  
- `Path.GetExtension(args.FileName)` orijinal dosya türünü (PNG, JPG vb.) korur.  
- `args.SavePath` ayarlanarak varsayılan konumu geçersiz kılar ve her şeyi düzenli tutar.

## Adım 4: Belgeyi Markdown Olarak Kaydedin

Seçenekler ayarlandığında, dışa aktarma tek bir satır kodla yapılır:

```csharp
// Step 4: Export to markdown using the configured options
string outputMarkdown = @"YOUR_DIRECTORY/Doc.md";
doc.Save(outputMarkdown, markdownSaveOptions);
```

Çalıştırdıktan sonra şunları bulacaksınız:

- `Doc.md` içinde resimlere referans veren markdown metni bulunur.  
- `Resources` klasörü, yanındaki `img_0.png`, `img_1.jpg` vb. dosyaları tutar.  

Bu, **markdown nasıl kaydedilir** akışıdır ve kaynak çıkarımıyla tamamlanır.

## Adım 5: Sonucu Doğrulayın (İsteğe Bağlı ama Önerilir)

Herhangi bir metin düzenleyicide `Doc.md` dosyasını açın. Şuna benzer bir şey görmelisiniz:

```markdown
Hello, Markdown world!

![image](Resources/img_0.png)
```

Ve `Resources` klasörü, eklediğiniz orijinal resmi içerecek. Markdown dosyasını bir görüntüleyicide (ör. VS Code, GitHub) açarsanız resim doğru şekilde görüntülenir.

> **Sık sorulan soru:** *Resimleri markdown dosyasıyla aynı klasöre koymak istersem ne olur?*  
> `resourcesFolder` değerini `Path.GetDirectoryName(outputMarkdown)` olarak değiştirin ve markdown resim yollarını buna göre ayarlayın.

## Markdown'tan Resimleri Çıkarma – İleri Düzey Ayarlamalar

Bazen adlandırma kuralları üzerinde daha fazla kontrol gerekir ya da belirli kaynak türlerini atlamak istersiniz. Aşağıda işinize yarayabilecek birkaç varyasyon bulabilirsiniz.

### 5.1 Görüntü Olmayan Kaynakları Atla

```csharp
ResourceSavingCallback = (sender, args) =>
{
    // Only process images; ignore CSS, fonts, etc.
    if (!args.ContentType.StartsWith("image/", StringComparison.OrdinalIgnoreCase))
        return; // Let the default handling continue

    // ...same folder creation logic as before...
};
```

### 5.2 Orijinal Dosya Adlarını Koru

Orijinal dosya adlarını `img_0` yerine tercih ediyorsanız, sadece `args.Index` kısmını kaldırın:

```csharp
string resourceFileName = args.FileName; // uses the name from the source document
```

### 5.3 Belge Başına Özel Bir Alt Klasör Kullan

```csharp
string docName = Path.GetFileNameWithoutExtension(outputMarkdown);
string resourcesFolder = $@"YOUR_DIRECTORY/{docName}_Resources/";
Directory.CreateDirectory(resourcesFolder);
```

Bu kod parçacıkları, **markdown'tan resimleri çıkar** işlemini esnek bir şekilde gösterir ve farklı proje konvansiyonlarına uyum sağlar.

## Sıkça Sorulan Sorular (SSS)

| Soru | Cevap |
|----------|--------|
| **Bu .NET Core ile çalışır mı?** | Kesinlikle—Aspose.Words çapraz platformdur, bu yüzden aynı kod Windows, Linux veya macOS'ta çalışır. |
| **SVG resimler hakkında ne?** | SVG'ler resim olarak ele alınır; geri çağırma bir `.svg` uzantısı alır. Markdown görüntüleyicinizin SVG'yi desteklediğinden emin olun. |
| **Markdown sözdizimini değiştirebilir miyim (ör. HTML `<img>` etiketleri kullanmak)?** | `markdownSaveOptions.ExportImagesAsBase64 = false` olarak ayarlayın ve ham HTML etiketlerine ihtiyacınız varsa `ExportImagesAsHtml`'ı ayarlayın. |
| **Birçok belgeyi toplu işleyebilir miyim?** | Yukarıdaki mantığı bir dosya koleksiyonu üzerinde `foreach` döngüsüyle sarın—her belgeye kendi kaynak klasörünü vermeyi unutmayın. |

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a document and add an image
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, Markdown world!");
        string imagePath = @"YOUR_DIRECTORY/sample-image.png"; // <-- change this
        builder.InsertImage(imagePath);

        // 2️⃣ Configure save options with a callback to extract images
        var markdownSaveOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (sender, args) =>
            {
                string resourcesFolder = @"YOUR_DIRECTORY/Resources/";
                Directory.CreateDirectory(resourcesFolder);

                string resourceFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
                args.SavePath = Path.Combine(resourcesFolder, resourceFileName);
            }
        };

        // 3️⃣ Save as markdown
        string outputPath = @"YOUR_DIRECTORY/Doc.md";
        doc.Save(outputPath, markdownSaveOptions);

        Console.WriteLine("Markdown saved successfully!");
        Console.WriteLine($"Check {outputPath} and the Resources folder for images.");
    }
}
```

Programı çalıştırın (`dotnet run`) ve başarıyı onaylayan konsol mesajlarını göreceksiniz. Tüm resimler artık düzenli bir şekilde depolanmış ve markdown dosyası onlara doğru şekilde işaret ediyor.

## Sonuç

Şimdi **markdown nasıl kaydedilir** ve **markdown'tan resimleri çıkar** öğrendiniz ve belgenin **belgeyi markdown olarak kaydetme** kaynak konumları üzerinde tam kontrolle sağlayabilirsiniz. Ana çıkarım `ResourceSavingCallback`'dir—bu, dışa aktarıcının ürettiği her dış dosya üzerinde ayrıntılı yetki verir.

Buradan itibaren şunları yapabilirsiniz:

- Bu akışı, kullanıcı‑yüklediği DOCX dosyalarını anında markdown'a dönüştüren bir web servisine entegre edin.  
- Callback'i, CMS'inize uyan bir adlandırma kuralına göre dosyaları yeniden adlandıracak şekilde genişletin.  
- Diğer Aspose.Words özellikleriyle, örneğin `ExportImagesAsBase64` ile satır içi‑resim markdown'u birleştirin.

Deneyin, klasör mantığını projenize göre ayarlayın ve markdown çıktısının dokümantasyon hattınızda parlamasını sağlayın.

![markdown kaydetme örneği](/assets/how-to-save-markdown.png "markdown kaydetme örneği")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}