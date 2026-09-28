---
category: general
date: 2026-01-08
description: DOCX'i markdown'a dönüştürürken resimleri nasıl yeniden adlandırılır.
  Docx'ten resimleri çıkarın, Word'ü markdown olarak kaydedin ve Aspose.Words kullanarak
  kaynaklarınızı düzenli tutun.
draft: false
keywords:
- how to rename images
- convert docx to markdown
- extract images from docx
- save word as markdown
- how to extract images
language: tr
og_description: DOCX'i markdown'a dönüştürürken resimleri nasıl yeniden adlandırılır.
  DOCX'ten resimleri nasıl çıkaracağınızı ve Word'ü temiz bir klasör yapısıyla markdown
  olarak nasıl kaydedeceğinizi öğrenin.
og_title: DOCX'ten Markdown'a Dönüştürürken Görselleri Nasıl Yeniden Adlandırılır
tags:
- Aspose.Words
- C#
- Document Conversion
title: DOCX'i Markdown'a Dönüştürürken Görselleri Nasıl Yeniden Adlandırılır
url: /tr/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX'i Markdown'a Dönüştürürken Görüntüleri Yeniden Adlandırma

**Görselleri yeniden adlandırma**, bir Word belgesini (DOCX) Markdown'a dönüştürdüğünüzde sık karşılaşılan bir engeldir. Oluşturulan bir `.md` dosyasını açıp `image1.png`, `image2.jpeg` gibi kaotik bir görüntü adı seti gördünüz mü ve onlara anlamlı adlar vermeyi düşündünüz mü?  

Bu öğreticide, bir DOCX dosyasından görselleri çıkarmanın, her görseli kaydedilirken yeniden adlandırmanın temiz ve tekrarlanabilir bir yolunu öğrenecek ve yeni dosya adlarına referans veren düzenli bir Markdown belgesi elde edeceksiniz. Ayrıca **convert docx to markdown**, **extract images from docx**, ve **save word as markdown** işlemlerine güçlü Aspose.Words .NET kütüphanesini kullanarak değineceğiz.

> **Pro tip:** Zaten diğer belge görevleri için Aspose.Words kullanıyorsanız, aynı `Document` nesnesini yeniden kullanabilirsiniz – ekstra bağımlılık gerektirmez.

## İhtiyacınız Olanlar

- **.NET 6+** (veya .NET Framework 4.7.2+ – kod aynı şekilde çalışır)
- **Aspose.Words for .NET** NuGet paketi (`Install-Package Aspose.Words`)
- En az bir görsel içeren örnek bir `input.docx`
- Markdown ve çıkarılan görsellerin bulunmasını istediğiniz bir klasör  

Ek araç gerekmez, harici dönüştürücü yok. Sadece birkaç satır C#.

![Görsellerin yeniden adlandırılması diyagramı](https://example.com/placeholder.png "Görsellerin nasıl yeniden adlandırıldığını ve kaydedildiğini gösteren diyagram")

## Adım 1: Resource‑Saving Callback'i Ayarlayın (Primary Keyword Here)

Çözümün kalbi, `IResourceSavingCallback`'in özel bir uygulamasıdır. Bu callback, gömülü her kaynağın dosya adı ve konumu üzerinde tam kontrol sağlar—tam da **rename images** anında yapmak istediğiniz şey.

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Custom callback that renames each extracted image and places it in a dedicated folder.
/// </summary>
class MyImageRenamer : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the folder exists – creates it if missing.
        string resourceFolder = "output/markdown_resources";
        Directory.CreateDirectory(resourceFolder);

        // Build a deterministic, readable name: img_0.png, img_1.jpg, …
        string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";

        // Combine folder and new name, then hand it back to Aspose.
        args.FileName = Path.Combine(resourceFolder, newFileName);

        // (Optional) If you need to modify the stream, you can replace args.Stream here.
    }
}
```

**Neden önemli:**  
Aspose'un rastgele GUID tabanlı dosya adları üretmesine izin vermek yerine, callback size daha sonra anlaşılması kolay bir adlandırma şeması uygulama imkanı verir—sürüm kontrolü veya dokümantasyon akışları için mükemmeldir.

## Adım 2: Callback'i Kullanmak İçin MarkdownSaveOptions'ı Yapılandırın

Şimdi Aspose'a bir belgeyi Markdown olarak kaydettiğinde `MyImageRenamer`'ı çağırmasını söylüyoruz.

```csharp
// Create save options and plug in the callback.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyImageRenamer()
};
```

Diğer seçeneklere dokunmadığımızı fark edin. Başlık seviyelerini veya kod bloğu stilini ayarlamanız gerekiyorsa, `MarkdownSaveOptions` sınıfının onlarca özelliği var—keşfetmekten çekinmeyin.

## Adım 3: DOCX'i Yükleyin ve Dönüştürmeyi Gerçekleştirin

Callback bağlandığında, dönüşüm tek satırda gerçekleşir.

```csharp
// Load the source Word document that contains images.
Document doc = new Document("input/input.docx");

// Save as Markdown; images are automatically renamed and stored.
doc.Save("output/output.md", markdownOptions);
```

Bu çalıştıktan sonra şunları bulacaksınız:

- `output/output.md` – `![Image](markdown_resources/img_0.png)` gibi görüntü bağlantılarına sahip Markdown dosyası
- `output/markdown_resources/` – `img_0.png`, `img_1.jpg` vb. dosyaları tutan bir klasör

Bu, **save word as markdown** iş akışının tam halidir, görüntü yeniden adlandırma dahildir.

## Adım 4: Sonucu Doğrulayın (How to Extract Images)

Oluşturulan `output.md` dosyasını herhangi bir metin düzenleyicide açın. Yeniden adlandırılmış dosyalara işaret eden markdown görüntü sözdizimini görmelisiniz:

```markdown
![Image](markdown_resources/img_0.png)
![Diagram](markdown_resources/img_1.jpg)
```

`markdown_resources` klasörünü açarsanız, görseller `img_#` deseninde olacaktır. Bu, **extracted images from docx** işlemini başarılı bir şekilde gerçekleştirdiğimizi ve onlara öngörülebilir adlar verdiğimizi gösterir.

## Yaygın Sorular ve Kenar Durumları

### Orijinal görüntü adlarına ihtiyacım olsaydı ne olur?

`newFileName` oluşturan satırı, `args.FileName` (orijinal ad) ya da mevcutsa görüntünün ALT metninden türetilen bir şeyle değiştirin:

```csharp
string cleanName = Path.GetFileNameWithoutExtension(args.FileName)
                     .Replace(" ", "_")
                     .ToLowerInvariant();
string newFileName = $"{cleanName}{Path.GetExtension(args.FileName)}";
```

### Çift isimleri nasıl ele alırım?

`args.Index`'i ek bir son ek olarak ekleyin, ya da benzersizliği sağlamak için callback içinde bir `HashSet<string>` tutun.

### Görüntü formatını değiştirebilir miyim (ör. PNG → JPEG)?

Evet. `args.Stream`'i okuyabilir, görüntüyü `System.Drawing` veya `ImageSharp` ile dönüştürebilir, ardından yeni bir akışı `args.Stream`'e atayabilir ve `args.FileName`'i buna göre ayarlayabilirsiniz.

### Bu, SVG veya diğer vektör formatlarıyla çalışır mı?

Aspose.Words SVG'yi bir görüntü kaynağı olarak ele alır, bu yüzden aynı callback geçerlidir. Yeniden adlandırırken dosya uzantısına dikkat edin.

### Performans hususları?

Callback her kaynak için bir kez çalışır, bu yüzden ek yük minimaldir. Binlerce görüntü işliyorsanız, hedef klasörü callback dışına toplu olarak oluşturmayı düşünün; böylece tekrar eden `Directory.CreateDirectory` çağrılarından kaçınırsınız (yöntem zaten ucuzdur).

## Tam Çalışan Örnek (Kopyala-Yapıştır Hazır)

Aşağıda, bir console uygulamasına ekleyebileceğiniz tüm program bulunmaktadır. Tüm using ifadelerini, callback sınıfını ve dönüşüm mantığını içerir.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace DocxToMarkdownRenamer
{
    /// <summary>
    /// Callback that renames each extracted image and stores it in a subfolder.
    /// </summary>
    class MyImageRenamer : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourceFolder = "output/markdown_resources";
            Directory.CreateDirectory(resourceFolder);

            // Example naming scheme: img_0.png, img_1.jpg, …
            string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
            args.FileName = Path.Combine(resourceFolder, newFileName);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the DOCX that contains images.
            Document doc = new Document("input/input.docx");

            // 2️⃣ Set up Markdown options with our renamer.
            MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyImageRenamer()
            };

            // 3️⃣ Save as Markdown – images are renamed automatically.
            doc.Save("output/output.md", markdownOptions);

            Console.WriteLine("Conversion complete! Check the 'output' folder.");
        }
    }
}
```

Programı çalıştırın, dönüşümü onaylayan bir konsol mesajı göreceksiniz. `output/output.md` dosyasını açın ve temiz görüntü referanslarını hemen fark edeceksiniz.

## Sonuç

Aspose.Words kullanarak **docx to markdown** dönüştürürken **how to rename images** (görselleri nasıl yeniden adlandırılır) sürecini adım adım inceledik. Özel bir `IResourceSavingCallback` kullanarak, görüntü dosya adları, klasör organizasyonu ve gerekirse görüntü formatı dönüşümü üzerinde tam kontrol elde edersiniz.

Kısaca:

- Her görüntüyü yeniden adlandırmak ve yeniden konumlandırmak için bir callback uygulayın.  
- Callback'i `MarkdownSaveOptions` içine bağlayın.  
- Word belgenizi yükleyin ve Markdown olarak kaydedin.  

Artık güvenle **extract images from docx** yapabilir, markdown'unuzu düzenli tutabilir ve süreci daha büyük otomasyon hatlarına entegre edebilirsiniz.  

**Sonraki adımlar:**  
- Adlandırma şemasını, orijinal başlık metnini içerecek şekilde özelleştirmeyi deneyin (`doc.GetChildNodes` kullanın).  
- Aynı callback desenini yeniden kullanarak HTML veya PDF gibi diğer Aspose çıktı formatlarını keşfedin.  
- Bunu bir CI/CD hattı ile birleştirerek kaynak Word dosyalarından otomatik olarak dokümantasyon üretin.  

Görsel işleme, diğer belge formatları veya Aspose ipuçları hakkında daha fazla sorunuz mu var? Aşağıya yorum bırakın—mutlu kodlamalar!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}