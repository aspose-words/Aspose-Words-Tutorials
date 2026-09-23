---
category: general
date: 2026-02-18
description: Aspose.Words kullanarak Word'ü Markdown'a dönüştürün ve docx'ten görselleri
  çıkarın. Word'ten markdown oluşturmayı eksiksiz bir C# örneğiyle öğrenin.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- generate markdown from word
- how to convert docx to markdown
language: tr
og_description: Aspose.Words ile Word'ü Markdown'a dönüştürün ve docx'ten görselleri
  çıkarın. Bu rehber, Word'ten markdown oluşturmayı adım adım gösterir.
og_title: Word'ü Markdown'a Dönüştür – C#'da Görselleri Çıkar
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: Word'ü Markdown'a Dönüştür – C#'ta Görselleri Çıkar
url: /tr/net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-in-c/
---

links: there are none besides image.

There are markdown links? Not in this content.

Proceed.

Let's produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'ü Markdown'a Dönüştür – Görselleri C# ile Çıkar

Her zaman **Word'ü Markdown'a dönüştürürken** bir `.docx` dosyasındaki tüm resimleri çıkarmak ister misiniz? Tek başınıza değilsiniz. Bir sözleşme, bir blog gönderisi ya da teknik bir spesifikasyon gibi Word'de hazırlanmış bir içeriğin temiz bir markdown sürümüne ihtiyacınız olduğunda birçok geliştirici takılıp kalıyor. İyi haber? Aspose.Words for .NET ile bunu birkaç satır kodla yapabilirsiniz ve sonuç olarak bir markdown dosyası *artı* orijinal görsellerin bulunduğu bir klasör elde edersiniz.

Bu öğreticide, **Word'den markdown üreten**, docx'ten görselleri çıkaran ve her şeyi diske kaydeden tam, çalıştırılabilir bir C# programını adım adım inceleyeceğiz. Sonunda **docx'i markdown'a dönüştürmeyi**, **docx'ten görselleri çıkarmayı** ve süreci kendi projeleriniz için nasıl özelleştireceğinizi tam olarak öğreneceksiniz.

## Gereksinimler

- **Aspose.Words for .NET** (v23.10 veya daha yeni). `Install-Package Aspose.Words` komutuyla ücretsiz deneme NuGet paketini alabilirsiniz.
- .NET 6+ SDK (herhangi bir güncel sürüm yeterlidir).
- En az bir resim içeren bir örnek `input.docx`.
- Markdown ve görsel varlıkların kaydedileceği bir klasör.

Başka üçüncü‑taraf kütüphane gerekmez. Aşağıdaki kod, ihtiyacınız olan tüm `using` yönergelerini içerir; bu yüzden bir console uygulamasına kopyalayıp **F5** tuşuna basabilirsiniz.

![Convert Word to Markdown example](/images/convert-word-to-markdown.png "convert word to markdown")

*Görsel alt metni: Word dosyasının görsellerle birlikte bir Markdown dosyasına dönüşümünü gösteren bir illüstrasyon.*

---

## Adım 1: Kaynak Word Belgesini Yükleyin

İlk iş, Aspose.Words'ü dönüştürmek istediğiniz dosyaya yönlendirmektir. `Document` sınıfı, `.docx` içindeki metin, tablo, resim gibi her şeye erişim sağlayan bir kapıdır.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 👉 Step 1: Load the Word document that contains images.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document document = new Document(inputPath);
```

> **Neden önemli:** Belgeyi bir kez yüklemek bellek kullanımını düşük tutar ve kütüphanenin iç paket yapısını incelemesine olanak tanır; bu da daha sonra görselleri çıkarmak için gereklidir.

---

## Adım 2: Aspose.Words'e Markdown Olarak Kaydetmesini Söyleyin

Aspose.Words, `MarkdownSaveOptions` sınıfı ile birlikte gelir. Bu sınıf, satır sonlarından dış kaynakların (örneğin görsellerin) kaydedileceği klasöre kadar her şeyi kontrol etmenizi sağlar.

```csharp
        // 👉 Step 2: Configure Markdown save options with a resource‑saving callback.
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
        {
            // The callback fires for each external resource (e.g., an image) that needs a file.
            ResourceSavingCallback = new ResourceSavingCallback(args =>
            {
                // 👉 Step 3 inside the callback: decide where and how to store each image.
                string resourceFolder = @"YOUR_DIRECTORY\markdown-resources";
                Directory.CreateDirectory(resourceFolder); // creates if it doesn’t exist

                // Give each image a unique name to avoid collisions.
                string uniqueFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
                args.FileName = Path.Combine(resourceFolder, uniqueFileName);

                // Optional: you could compress PNGs here by manipulating args.Stream.
            })
        };
```

> **Neden bir geri çağırma (callback) gerekir?** `ResourceSavingCallback`, her çıkarılan görselin dosya adı ve konumu üzerinde tam kontrol sağlar. Bu geri çağırma olmadan Aspose, tüm dosyaları aynı klasöre genel isimlerle döker; bu da büyük projelerde karışıklığa yol açar.

---

## Adım 3: Belgeyi Markdown Olarak Kaydedin

Seçenekler ayarlandığında, kaydetme tek satırlık bir işlem olur. Kütüphane, paragrafları, başlıkları, listeleri, tabloları ve—geri çağırma sayesinde—her resmi belirttiğiniz klasöre yazar.

```csharp
        // 👉 Step 4: Save the document as a Markdown file.
        string outputPath = @"YOUR_DIRECTORY\output.md";
        document.Save(outputPath, markdownOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputPath}");
        Console.WriteLine($"Images extracted to: {Path.GetDirectoryName(outputPath)}\\markdown-resources");
    }
}
```

### Beklenen Sonuç

- `output.md` markdown sözdizimini içerir (ör. `![Image](markdown-resources/img_1234.png)`).
- `markdown-resources` klasörü, orijinal Word dosyasındaki tüm görselleri, her biri benzersiz bir adla saklar.

`output.md` dosyasını herhangi bir markdown görüntüleyicide (VS Code, GitHub veya statik site jeneratörü) açtığınızda, metin ve görsellerin orijinal Word düzeniyle aynı olduğunu, ancak daha hafif ve web‑dostu bir formatta olduğunu göreceksiniz.

---

## Adım 4: Yaygın Varyasyonlar ve Kenar Durumları

### 4.1 Mevcut Kaynak Klasörlerini Yönetme

Dönüştürmeyi birden fazla kez çalıştırırsanız, eski görseller kalabilir. Her çalışmadan önce klasörü temizleyen basit bir koruma ifadesi ekleyebilirsiniz:

```csharp
if (Directory.Exists(resourceFolder))
{
    foreach (var file in Directory.GetFiles(resourceFolder))
        File.Delete(file);
}
else
{
    Directory.CreateDirectory(resourceFolder);
}
```

### 4.2 Görsel Formatlarını Değiştirme

Bazen tüm görselleri web optimizasyonu için JPEG olarak almak isteyebilirsiniz. Geri çağırma içinde akışı yeniden kodlayabilirsiniz:

```csharp
using (var img = System.Drawing.Image.FromStream(args.Stream))
{
    var jpegStream = new MemoryStream();
    img.Save(jpegStream, System.Drawing.Imaging.ImageFormat.Jpeg);
    jpegStream.Position = 0;
    args.Stream = jpegStream;
    args.FileName = Path.ChangeExtension(args.FileName, ".jpg");
}
```

> **Pro ipucu:** `System.Drawing.Common` Windows'ta çalışır; Linux/macOS'ta çapraz platform güvenliği için `ImageSharp` tercih edilebilir.

### 4.3 Tablo Stillerini Koruma

Word belgeniz tablo biçimlendirmesine çok bağımlıysa, `MarkdownSaveOptions` içinde şu ayarları yapabilirsiniz:

```csharp
markdownOptions.ExportTableColumnWidths = true;   // keeps column widths
markdownOptions.ExportTableBorders = true;       // adds markdown border syntax
```

### 4.4 Farklı Bir Çıktı Dizini Kullanma

`Save` yöntemi, mutlak ya da göreli herhangi bir yolu kabul eder. CI pipeline'ları için geçici bir derleme klasörüne yönlendirebilirsiniz:

```csharp
document.Save(Path.Combine(Path.GetTempPath(), "doc.md"), markdownOptions);
```

---

## Sık Sorulan Sorular

**S: Bu yöntem `.doc` (ikili) dosyalarıyla da çalışır mı?**  
C: Evet. `new Document("file.doc")` formatı otomatik olarak algılar; aynı kod hem `.doc` hem de `.docx` için geçerlidir.

**S: Word dosyası gömülü SVG görseller içeriyorsa ne olur?**  
C: Aspose.Words, SVG'leri orijinal formatlarıyla çıkarır. Raster versiyonlara ihtiyacınız varsa, geri çağırma içinde SVG akışını dönüştürmeniz gerekir (ör. `Svg.Skia` kullanarak).

**S: Görsel çıkarımını tamamen atlamak istersem?**  
C: `markdownOptions.ExportImagesAsBase64 = true;` ayarını yaparak görselleri markdown içinde veri URI'ları olarak gömebilirsiniz—tek dosyalı README oluşturma için faydalıdır.

---

## Özet ve Sonraki Adımlar

Tam **Word'ü markdown'a dönüştürme** iş akışını şu şekilde özetleyebiliriz:

1. `.docx` dosyasını yükleyin.
2. `MarkdownSaveOptions` içinde bir `ResourceSavingCallback` yapılandırın.
3. Belgeyi kaydedin; geri çağırma her resmi ayrı bir klasöre yazar.

Bu çözüm, 50 satırın altında C# kodu ile tamamlanır.

İleriye dönük olarak şunları düşünebilirsiniz:

- **Statik site oluşturma:** Markdown'ı Hugo ya da Jekyll gibi bir jeneratöre besleyin.
- **Toplu işleme:** Kodu bir `foreach` döngüsü içinde sararak yüzlerce dosyayı otomatik olarak işleyin.
- **Gelişmiş görsel işleme:** Geri çağırma içinde görselleri yeniden boyutlandırın, filigran ekleyin veya formatlarını dönüştürün.

Denemeler yapmaktan çekinmeyin—geri çağırma mantığını değiştirin, kaydetme seçeneklerini ayarlayın veya bu kodu daha büyük bir belge‑akışına entegre edin. İmkanlar sınırsız ve artık **Word'den markdown üretme** projeleriniz için sağlam bir temele sahipsiniz.

İyi kodlamalar, markdown'ınız her zaman temiz, görselleriniz ise her zaman bulunur olsun!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}