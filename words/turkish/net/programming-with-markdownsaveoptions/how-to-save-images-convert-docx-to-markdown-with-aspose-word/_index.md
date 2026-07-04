---
category: general
date: 2026-05-04
description: Aspose.Words kullanarak bir DOCX'i Markdown'a dönüştürürken resimleri
  nasıl kaydedeceğinizi öğrenin. Bu rehber ayrıca Word'ten resimleri nasıl çıkaracağınızı
  ve Word'ü Markdown olarak nasıl kaydedeceğinizi gösterir.
draft: false
keywords:
- how to save images
- convert docx to markdown
- extract images from word
- how to convert docx
- save word as markdown
language: tr
og_description: Aspose.Words kullanarak bir DOCX dosyasını Markdown'a dönüştürürken
  resimleri nasıl kaydedilir? Tam C# kodu ile adım adım rehber.
og_title: Görselleri Kaydetme – Aspose.Words ile DOCX'i Markdown'a Dönüştürme
tags:
- Aspose.Words
- C#
- Markdown conversion
title: Görselleri Kaydetme – Aspose.Words ile DOCX'i Markdown'a Dönüştürme
url: /tr/net/programming-with-markdownsaveoptions/how-to-save-images-convert-docx-to-markdown-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Görselleri Kaydetme – Aspose.Words ile DOCX'i Markdown'a Dönüştürme

Word dosyasını Markdown'a dönüştürürken **görselleri nasıl kaydedeceğinizi** hiç merak ettiniz mi? Tek başınıza değilsiniz. Birçok geliştirici, dönüşüm sırasında resimlerin kırık bağlantılar hâline gelmesi ya da daha da kötüsü tamamen kaybolması sorunuyla karşılaşıyor. İyi haber şu ki, Aspose.Words size ince ayar kontrolü sunar; böylece Word'ten görselleri çıkarabilir, nereye konulacağını belirleyebilir ve hâlâ temiz bir Markdown çıktısı alabilirsiniz.

Bu öğreticide, bir `.docx` dosyasını `.md`'ye dönüştürürken **görselleri ayrı bir klasöre nasıl kaydedeceğinizi** gösteren, çalıştırmaya hazır bir C# örneği üzerinden adım adım ilerleyeceğiz. Ayrıca **convert docx to markdown**, **extract images from word** ve **how to convert docx** konularına da değinecek, **save word as markdown** yaparken hiçbir varlığı kaybetmemenizi sağlayacağız.

## Önkoşullar

- .NET 6.0 veya üzeri (API, .NET Framework 4.7+ üzerinde aynı şekilde çalışır)
- Aktif bir Aspose.Words lisansı ya da ücretsiz deneme sürümü (deneme sürümü çıktıya bir filigran ekler, ancak kod aynı şekilde çalışır)
- İçinde görseller bulunan bir Word belgesi (ör. `DocWithImages.docx`)
- Visual Studio 2022 ya da C# projelerini derleyebilen herhangi bir editör

> **Pro ipucu:** Deneme sürümü kullanıyorsanız, görsel‑kaydetme mantığını hâlâ test edebilirsiniz; sadece son PDF/MD dosyasının deneme filigranı içereceğini unutmayın.

## Çözümün Genel Görünümü

Yüksek seviyede süreç şu şekilde işler:

1. Kaynak `.docx` dosyasını `Document` ile yükleyin.
2. Bir `MarkdownSaveOptions` nesnesi oluşturun ve içine bir `IResourceSavingCallback` bağlayın.
3. Geri çağrıda (callback) her görsel için klasör ve dosya adını belirleyin.
4. Belgeyi Markdown olarak kaydedin; geri çağrı her görseli diske yazar.

Bu, dönüşüm sırasında **görselleri nasıl kaydedeceğinizin** temelidir. Aynı desen, ihtiyacınız olursa (fontlar, CSS vb.) diğer kaynak türleri için de kullanılabilir.

## Adım 1 – Görselleri İçeren DOCX'i Yükleyin

İlk olarak, dönüştürmek istediğiniz Word dosyasına işaret eden bir `Document` örneğine ihtiyacımız var. Burada karmaşık bir şey yok; sadece doğrudan bir yapıcı çağrısı.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Adjust the path to where your .docx lives
string sourcePath = @"C:\Docs\DocWithImages.docx";

Document sourceDoc = new Document(sourcePath);
```

> **Neden önemli:** Belgeyi yüklemek, Aspose'un Word XML'ini ayrıştırdığı tek yerdir; eksik fontlar ya da bozuk bölümler hemen bir istisna fırlatır—görselleri kaydetmeye başlamadan önce.

## Adım 2 – Görsel‑Kaydetme Geri Çağrısı ile MarkdownSaveOptions'ı Ayarlayın

`MarkdownSaveOptions` sınıfı, `ResourceSavingCallback` aracılığıyla kaydetme sürecine müdahale etmenizi sağlar. Bu geri çağrı, Aspose'un yazması gereken her dış kaynak (görseller, CSS vb.) için bir `ResourceSavingArgs` nesnesi alır.

```csharp
// Define where the Markdown file will be written
string markdownPath = @"C:\Docs\Doc.md";

// Create the options object and attach the callback
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This is the heart of how to save images
    ResourceSavingCallback = new ImageSavingCallback()
};
```

### Geri Çağrı (Callback) Uygulaması

Aşağıda `ImageSavingCallback`'in tam uygulaması yer alıyor. Markdown dosyasının yanına bir `Images` alt‑klasörü oluşturur, her resme sıralı bir ad verir (`img_0.png`, `img_1.jpg`, …) ve isteğe bağlı olarak resmi başka bir yere (ör. bir bulut kovasına) akıtmanıza olanak tanır.

```csharp
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only handle images; other resources (like CSS) are ignored here
        if (args.ResourceType != ResourceType.Image)
            return;

        // Build a folder called "Images" right next to the markdown file
        string markdownDir = Path.GetDirectoryName(args.DestinationFileName);
        string imagesFolder = Path.Combine(markdownDir, "Images");
        Directory.CreateDirectory(imagesFolder);

        // Compose a safe file name: img_<index>.<original extension>
        string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
        args.FileName = Path.Combine(imagesFolder, newFileName);

        // If you wanted to push the image to a remote store, you could replace args.Stream here.
        // For now we just let Aspose write to the local file system.
    }
}
```

> **Bu nasıl yardımcı olur:** `args.FileName`'i özelleştirerek **görselleri nasıl kaydedeceğinizi** tam olarak kontrol edersiniz—düz bir klasör, tarih‑bazlı bir hiyerarşi ya da hatta bir veritabanı BLOB'ı olsun. Geri çağrı her görsel için çalıştığından, Markdown dosyasını sonradan işlemek zorunda kalmazsınız.

## Adım 3 – Belgeyi Markdown Olarak Kaydedin

Seçenekler ve geri çağrı hazır olduğunda, gerçek dönüşüm tek bir satırda gerçekleşir.

```csharp
// Save the document; the callback will fire for each image automatically
sourceDoc.Save(markdownPath, markdownOptions);
```

Bu satır tamamlandığında elinizde olacak:

- `Doc.md` – Word içeriğinizin Markdown temsili.
- `Images\img_0.png`, `Images\img_1.jpg`, … – orijinal DOCX'ten çıkarılan tüm resimler.

## Tam, Çalıştırmaya Hazır Örnek

Her şeyi bir araya getirdiğimizde, yeni bir C# projesine kopyalayıp yapıştırabileceğiniz bağımsız bir konsol uygulaması elde edersiniz.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // 1️⃣ Load the source DOCX that contains images
            // -----------------------------------------------------------------
            string sourcePath = @"C:\Docs\DocWithImages.docx";
            Document sourceDoc = new Document(sourcePath);

            // -----------------------------------------------------------------
            // 2️⃣ Prepare Markdown options with a custom image‑saving callback
            // -----------------------------------------------------------------
            string markdownPath = @"C:\Docs\Doc.md";
            MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // -----------------------------------------------------------------
            // 3️⃣ Perform the conversion – this is where we actually learn
            //     how to save images while converting docx to markdown
            // -----------------------------------------------------------------
            sourceDoc.Save(markdownPath, markdownOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {markdownPath}");
            Console.WriteLine("Images folder: " + Path.Combine(Path.GetDirectoryName(markdownPath), "Images"));
        }
    }

    // -----------------------------------------------------------------
    // 4️⃣ Callback that decides where each image ends up
    // -----------------------------------------------------------------
    class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType != ResourceType.Image)
                return;

            string markdownDir = Path.GetDirectoryName(args.DestinationFileName);
            string imagesFolder = Path.Combine(markdownDir, "Images");
            Directory.CreateDirectory(imagesFolder);

            string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
            args.FileName = Path.Combine(imagesFolder, newFileName);

            // Optional: redirect the image stream elsewhere (e.g., cloud storage)
            // args.Stream = new MemoryStream(); // your custom stream here
        }
    }
}
```

### Beklenen Sonuç

Programı çalıştırdıktan sonra:

- `C:\Docs\Doc.md` dosyasını herhangi bir metin editöründe açın. `![](Images/img_0.png)` gibi Markdown görsel bağlantılarını göreceksiniz.
- `Images` klasörü, çıkarılan her resmi sıralı bir adla içerecek.
- Markdown dosyası, yerel görselleri destekleyen herhangi bir görüntüleyicide (VS Code önizleme, GitHub vb.) doğru şekilde render edilecektir.

## Sık Sorulan Sorular (SSS)

### Bu diğer görsel formatları (SVG, TIFF) ile çalışır mı?

Evet. `Path.GetExtension(args.FileName)` orijinal uzantıyı korur, bu yüzden SVG, TIFF, BMP ve hatta EMF değişmeden kaydedilir. Tek sınırlama, bazı Markdown render'larının SVG'yi satır içi gösterememesidir; bu durumda SVG'yi önceden PNG'ye dönüştürmeniz gerekebilir.

### Görselleri ayrı dosyalar yerine Base64 olarak gömmem gerekirse ne yapmalıyım?

`ResourceSaving` içinde fiziksel dosya yazımını bir bellek akışıyla (memory stream) değiştirip, Markdown bağlantısını manuel olarak düzenleyebilirsiniz. Aspose doğrudan bir “Base64 olarak göm” seçeneği sunmaz, ancak geri çağrı `args.Stream` üzerinde tam kontrol sağlar.

### Yerleşik `ExportImages` metodundan farkı nedir?

`ExportImages` tüm görselleri bir klasöre **Markdown üretmeden** çıkarır. Bizim geri çağrımız iki işlemi birleştirir, böylece görsel dosya adları `.md` içindeki referanslarla eşleşir. Bu uyum, dönüşüm sırasında **görselleri nasıl kaydedeceğiniz** konusundaki doğru sonucu elde etmenin anahtarıdır.

### Birden fazla DOCX dosyasını toplu olarak dönüştürebilir miyim?

Kesinlikle. Çekirdek mantığı `foreach (var file in Directory.GetFiles(..., "*.docx"))` döngüsü içinde sarın, çıktı yollarını ayarlayın ve aynı `ImageSavingCallback`'i yeniden kullanın. Tek yapmanız gereken, her belge için yeni bir `MarkdownSaveOptions` oluşturmak; çünkü `args.DestinationFileName` her yinelemede değişir.

## Kenar Durumları & En İyi Uygulamalar

| Durum | Dikkat Edilmesi Gereken | Önerilen Çözüm |
|-----------|----------------------|-----------------|
| **Büyük DOCX (yüzlerce MB)** | Yükleme sırasında bellek baskısı | `LoadOptions` ile `LoadFormat.Docx` kullanın ve parçaları akış‑yüklü (stream‑load) şekilde alın |
| **Görsel adları çakışıyor** | Hedef klasörde aynı isimli `img_0.png` varsa üzerine yazabilir | GUID ekleyin: `newFileName = $"img_{args.Index}_{Guid.NewGuid():N}{Path.GetExtension(args.FileName)}"` |
| **Yazma izni olmayan çıktı klasörü** | Kaydetme `UnauthorizedAccessException` fırlatır | İşlemin yeterli izinlerle çalıştığından emin olun veya yazılabilir bir yol seçin |
| **Görsel olmayan kaynaklar (CSS, fontlar)** | Geri çağrı bunları da alır | `if (args.ResourceType != ResourceType.Image) return;` koşulunu ekleyin (zaten gösterildi) |
| **Unicode dosya adları** | Bazı dosya sistemleri karakterleri hatalı işler | `Path.GetInvalidFileNameChars()` ile `args.FileName`'i temizleyerek atayın |

## Bir Sonraki Kez Keşfedebileceğiniz İlgili Konular

- **convert docx to markdown** özel başlık stilleriyle (satır içi görseller için `MarkdownSaveOptions.ExportImagesAsBase64` kullanın)
- **extract images from word** `Document.GetChildNodes(NodeType.Shape, true)` yöntemiyle

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}