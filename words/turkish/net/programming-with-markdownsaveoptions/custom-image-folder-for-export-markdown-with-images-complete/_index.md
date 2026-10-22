---
category: general
date: 2026-06-20
description: Özel resim klasörü, markdown dosyalarını resimlerle kolayca dışa aktarmanızı
  sağlar. Resimleri belirli bir dizine nasıl kaydedeceğinizi ve .NET'te markdown resimlerini
  nasıl kaydedeceğinizi öğrenin.
draft: false
keywords:
- custom image folder
- export markdown with images
- save images specific directory
- save markdown images
language: tr
og_description: Özel resim klasörü, resimlerle markdown dışa aktarmayı basitleştirir.
  Resimleri belirli bir dizine kaydetmek ve markdown resimlerini kaydetmek için bu
  adım adım kılavuzu izleyin.
og_title: özel resim klasörü – Görsellerle Markdown Dışa Aktar
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: custom image folder lets you export markdown with images easily. Learn
    how to save images specific directory and save markdown images in .NET.
  headline: custom image folder for export markdown with images – Complete Guide
  type: TechArticle
- description: custom image folder lets you export markdown with images easily. Learn
    how to save images specific directory and save markdown images in .NET.
  name: custom image folder for export markdown with images – Complete Guide
  steps:
  - name: Guarantees **atomicity** – images and markdown are written together, preventing
      broken links.
    text: Guarantees **atomicity** – images and markdown are written together, preventing
      broken links.
  - name: Eliminates a second file‑system scan, which can be costly for large docs.
    text: Eliminates a second file‑system scan, which can be costly for large docs.
  - name: Gives you the flexibility to rename or compress images on the fly.
    text: Gives you the flexibility to rename or compress images on the fly.
  type: HowTo
tags:
- Aspose.Words
- Markdown
- .NET
title: Görsellerle Markdown Dışa Aktarma İçin Özel Resim Klasörü – Tam Kılavuz
url: /tr/net/programming-with-markdownsaveoptions/custom-image-folder-for-export-markdown-with-images-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# özel resim klasörü – .NET'te Görsellerle Markdown Dışa Aktarma

Markdown'i görsellerle dışa aktarırken **özel bir resim klasörüne** ihtiyaç duydunuz mu? Bu sorunu yalnızca siz yaşamıyorsunuz. Dokümantasyon, blog gönderileri veya API kılavuzları oluşturuyor olun, görsellerinizi ayrı bir dizinde düzenli tutmak, ileride karışık bir dosya ağacından sizi kurtarır.

Bu öğreticide, markdown dosyası oluştururken **görselleri belirli bir dizine kaydetmenin** nasıl yapılacağını gösteren eksiksiz, çalıştırmaya hazır bir çözümü adım adım inceleyeceğiz. Neden bir geri çağırma (callback) kullanmanın en temiz yol olduğunu göreceksiniz ve rehberi, herhangi bir .NET projesine ekleyebileceğiniz tam bir kod örneğiyle tamamlayacaksınız.

## Öğrenecekleriniz

- Aspose.Words (veya benzer bir kütüphane) yapılandırarak görüntü kaydetmeyi yönlendirin.
- Her bir görüntüyü **özel bir resim klasörüne** yazan bir geri çağırma (callback) uygulayın.
- `MarkdownSaveOptions` kullanarak her şeyi birleştirin ve **markdown görsellerini** doğru şekilde kaydedin.
- Çift isimler veya büyük dosyalar gibi kenar durumlarını ele almak için ipuçları.

### Önkoşullar

| Gereksinim | Neden Önemli |
|------------|--------------|
| .NET 6+ (or .NET Framework 4.7+) | Kod `FileStream` ve `Guid` kullanır. |
| Aspose.Words for .NET (or a comparable markdown exporter) | `MarkdownSaveOptions` ve geri çağırma arayüzünü sağlar. |
| Basic C# knowledge | Sınıfları ve akışları (streams) anlamanız gerekir. |
| An existing `Document` object (`doc`) | Öğretici, zaten doldurulmuş bir belgeye sahip olduğunuzu varsayar. |

Bunların dışında dış araçlara gerek yok—her şey yerel olarak çalışır.

## Adım 1: Her Görüntüyü Özel Bir Resim Klasöründe Saklayan Bir Geri Çağırma Tanımlayın

Çözümün kalbi, `IResourceSavingCallback` arayüzünü uygulayan bir sınıftır. `ResourceSaving` içinde benzersiz bir dosya adı oluşturur, seçtiğiniz klasör içinde tam yolu oluşturur ve ardından kütüphaneyi görüntüyü oraya yazdırır.

```csharp
// Step 1: Define a callback that stores each image in a custom folder
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique file name for the image
        var fileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // Build the full path inside the desired resources directory
        var fullPath = Path.Combine("YOUR_DIRECTORY", fileName);

        // Redirect the saving stream to the new location
        args.Stream = new FileStream(fullPath, FileMode.Create);
        args.KeepResourceStreamOpen = false;   // close after save

        // Update the markdown reference to point to the new file name
        args.ResourceFileName = fileName;
    }
}
```

**Neden bu çalışır:**  
- `Guid.NewGuid()` benzersiz bir ad garantiler, kaynak belgede aynı orijinal dosya adına sahip birden fazla görüntü olduğunda çakışmaları önler.  
- `args.Stream`'i değiştirerek, dışa aktarıcıya ikili veriyi tam olarak nereye yazacağını söyleriz.  
- `args.ResourceFileName`'i güncelleyerek markdown referansının (`![](img_…​)`) artık **özel resim klasörünüzde** bulunan dosyaya işaret etmesini sağlarız.

> **Pro tip:** `"YOUR_DIRECTORY"` ifadesini, klasörün markdown dosyanızın yanına otomatik olarak yerleştirilmesini istiyorsanız `Path.Combine(Environment.CurrentDirectory, "Images")` ile oluşturulan bir yol ile değiştirin.

## Adım 2: Geri Çağırmayı Markdown Kaydetme Seçeneklerine Bağlayın

Sonra bir `MarkdownSaveOptions` örneği oluşturur ve geri çağırmamızı atarız. Bu, dışa aktarıcıya karşılaştığı her gömülü kaynak için `ImageSavingCallback`'i çağırmasını söyler.

```csharp
// Step 2: Configure Markdown save options to use the callback
var markdownOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new ImageSavingCallback()
};
```

**Arka planda ne oluyor?**  
`doc.Save` çalıştığında, Aspose.Words belgenin düğüm ağacında dolaşır. Her görüntüyle karşılaştığında `ResourceSaving` tetiklenir. Geri çağırmamız bu olayı yakalar, görüntü akışını yeniden yönlendirir ve markdown bağlantısını günceller. Sonuç? Tüm görüntüler belirttiğiniz klasöre yerleşir ve markdown dosyası bunlara doğru şekilde referans verir.

## Adım 3: Belgeyi Markdown Olarak Kaydedin – Görseller Geri Çağırma ile Kaydedilir

Son olarak, `Save` metodunu seçenek nesnesiyle çağırırız. Kütüphane ağır işi yapar; geri çağırmamız dosya yerleştirmesini gerçekleştirir.

```csharp
// Step 3: Save the document as Markdown; images are saved via the callback
doc.Save("YOUR_DIRECTORY/DocWithImages.md", markdownOptions);
```

Eğer `"YOUR_DIRECTORY"` `C:\Docs\MyProject` ise şunu göreceksiniz:

```
C:\Docs\MyProject\DocWithImages.md
C:\Docs\MyProject\img_3f2a1c4e‑b5d6‑4a7b‑9c8d‑e9f0a1b2c3d4.png
C:\Docs\MyProject\img_7e8f9a0b‑c1d2‑3e4f‑5g6h‑7i8j9k0l1m2n.jpg
```

Markdown dosyası şu satırları içerir:

```markdown
![Image](img_3f2a1c4e‑b5d6‑4a7b‑9c8d‑e9f0a1b2c3d4.png)
```

Bu, **markdown görsellerini** öngörülebilir bir konumda kaydetmek için tam olarak ihtiyacınız olan şeydir.

## Tam Çalışan Örnek

Aşağıda, Visual Studio'ya kopyalayıp yapıştırabileceğiniz, kendi içinde bağımsız bir konsol uygulaması bulunmaktadır. Bu uygulama bir görüntülü basit bir belge oluşturur ve ardından özel klasör yaklaşımını kullanarak dışa aktarır.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, markdown with images!");
        builder.InsertImage("sample.jpg"); // Ensure sample.jpg exists next to the exe

        // 2️⃣ Define the callback (same as earlier)
        var options = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback()
        };

        // 3️⃣ Choose output folder (feel free to change)
        string outputDir = Path.Combine(Environment.CurrentDirectory, "Exported");
        Directory.CreateDirectory(outputDir); // creates if missing

        // 4️⃣ Save markdown and images
        string mdPath = Path.Combine(outputDir, "Document.md");
        doc.Save(mdPath, options);

        Console.WriteLine($"Markdown saved to: {mdPath}");
        Console.WriteLine("Images stored in the same folder.");
    }
}

// Callback class – identical to the earlier snippet
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        var fileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
        var fullPath = Path.Combine("Exported", fileName);
        args.Stream = new FileStream(fullPath, FileMode.Create);
        args.KeepResourceStreamOpen = false;
        args.ResourceFileName = fileName;
    }
}
```

**Beklenen çıktı**

Programı çalıştırdığınızda aşağıdakine benzer bir şey yazdırır:

```
Markdown saved to: C:\MyApp\Exported\Document.md
Images stored in the same folder.
```

`Document.md` dosyasını açtığınızda markdown görüntü referansının `img_…​`'ye işaret ettiğini göreceksiniz. Görüntü dosyası markdown dosyasının hemen yanında bulunur, tam da **özel resim klasörü** tasarımının belirttiği gibi.

## Yaygın Kenar Durumlarını Ele Alma

| Durum | Çözüm |
|-------|-------|
| **Duplicate filenames** | `Guid` zaten çakışmaları önler; okunabilir isimler isterseniz bir sayaç ekleyin (`img_001.png`, `img_002.png`). |
| **Large image sets** | Görüntüyü doğrudan diske akıtın; tüm görüntüyü belleğe yüklemekten kaçının. |
| **Different output directories per run** | Hedef klasörü `ImageSavingCallback`'e bir yapıcı argümanı olarak geçirin, `"Exported"` gibi sabit kodlamaktan kaçının. |
| **Missing write permissions** | Uygulamanın yeterli izinle çalıştığından emin olun veya `%TEMP%` gibi kullanıcı yazabilir bir klasör seçin. |
| **Non‑image resources (e.g., CSS)** | Geri çağırma herhangi bir kaynak için tetiklenir; `args.ResourceType`'ı inceleyerek yalnızca görüntüleri işleyebilirsiniz. |

## Neden Geri Çağırma Kullanmalı, Sonradan İşleme Yerine?

Şöyle düşünebilirsiniz: “Önce markdown'i oluşturup ardından görüntüleri taşımak neden olmaz?” Geri çağırma yaklaşımı:

1. **atomiklik** garantiler – görüntüler ve markdown birlikte yazılır, kırık bağlantıların önüne geçilir.  
2. İkinci bir dosya sistemi taramasını ortadan kaldırır, bu büyük belgeler için maliyetli olabilir.  
3. Görüntüleri anında yeniden adlandırma veya sıkıştırma esnekliği sağlar.

Kısacası, her şeyi **özel bir resim klasöründe** tutarken **görsellerle markdown dışa aktarmanın** en **güçlü yoludur**.

## Sonuç

Bir **özel resim klasörü** stratejisi kullanarak **görselleri belirli bir dizine kaydetme** ve **markdown görsellerini kaydetme** için ihtiyacınız olan her şeyi ele aldık. `IResourceSavingCallback`'i uygulayarak, `MarkdownSaveOptions`'ı yapılandırarak ve `doc.Save`'i çağırarak temiz bir klasör düzeni ve güvenilir markdown referansları elde edersiniz—hepsi sadece birkaç düzine kod satırıyla.

Bir sonraki adımda şunları keşfedebilirsiniz:

- Geri çağırma içinde görüntü sıkıştırması eklemek.  
- `README.md` oluşturarak klasöre otomatik bağlantı vermek.  
- Geri çağırmayı CSS veya script gibi diğer kaynak türlerini işlemek için genişletmek.

Bir sonraki dokümantasyon akışınızda bunu deneyin—gelecekteki kendiniz düzenli klasör yapısı için size teşekkür edecek.

Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [save docx as markdown – Full C# Guide with Image Extraction](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}