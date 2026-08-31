---
category: general
date: 2026-01-03
description: Word'ü Markdown'a dönüştür ve görselleri tek seferde base64 olarak göm.
  Word'ü markdown olarak kaydetmeyi, Word'den markdown üretmeyi ve base64 görüntü
  veri URI'sini kullanmayı öğren.
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: tr
og_description: Word'ü Markdown'a dönüştürün ve görselleri base64 veri URI'ları olarak
  gömün. Bu adım adım öğretici, Word'ü markdown olarak kaydetmeyi ve Word'den markdown
  üretmeyi gösterir.
og_title: Word'ü Markdown'a Dönüştür – Base64 Görüntü Gömme Rehberi
tags:
- Aspose.Words
- C#
- Markdown
title: Word'ü Markdown'a Dönüştür – Görselleri Base64 Olarak Göm
url: /tr/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'ü Markdown'a Dönüştür – Görselleri Base64 Olarak Göm

Word'ü **markdown'a dönüştürmek** istediğinizde ama görsellerle ilgili sorunlar yaşadığınız oldu mu? Tek başınıza değilsiniz. Word, resimleri ayrı dosyalar olarak saklamayı severken, markdown tek bir dosyada her şeyi düzenli tutan `data:image/...;base64,` dizelerini tercih eder.  

Bu öğreticide, **Word'ü markdown olarak kaydeden**, **görselleri base64 olarak gömen** ve hatta Aspose.Words for .NET kullanarak **Word'den markdown üretmeyi** gösteren tamamen çalışır bir çözümü adım adım inceleyeceğiz. Sonunda, dış klasörlere ihtiyaç duymadan orijinal belgeyle aynı şekilde görüntülenen tek bir `.md` dosyanız olacak.

## Gereksinimler

- **.NET 6.0 veya üzeri** (NuGet paketi referanslayabilen herhangi bir sürüm)
- **Aspose.Words for .NET** (ücretsiz deneme sürümü test için yeterli)
- Birkaç resim içeren basit bir `.docx` dosyası (biz `input.docx` diye adlandıracağız)
- Sevdiğiniz IDE (Visual Studio, Rider, VS Code—hangisini tercih ederseniz)

Eğer bunlara sahipseniz harika—hadi başlayalım. Yoksa, NuGet paketini kurmak tek bir satır:

```bash
dotnet add package Aspose.Words
```

## Adım 1: Word Belgesini Yükle — **convert word to markdown** için başlangıç noktası

İlk olarak `.docx` dosyasını belleğe almamız gerekiyor. Dönüştürme sihrinin burada başladığını unutmayın.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Neden önemli:**  
> Belgeyi yüklemek, Aspose'a metin, stiller ve gömülü tüm kaynaklara tam erişim sağlar. Bu adım olmadan dönüştürülecek bir şey kalmaz.

## Adım 2: Resource‑Saving Callback ile MarkdownSaveOptions'ı Ayarla

Aspose, normalde diske yazılacak her kaynağı (örneğin resimleri) yakalamanıza izin verir. Özel bir `IResourceSavingCallback` sağlayarak, dosya‑tabanlı kaydetmeyi **base64 resim veri URI'sı** ile değiştirebiliriz.

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### Özel İşleyici – Resimleri Base64'e Dönüştürmek

Aşağıda tam uygulama yer alıyor. `args.ResourceType == ResourceType.Image` kontrolünü gördüğünüzde:

1. Resmi bir `MemoryStream`'e yazın.
2. Bayt dizisini Base64 stringine çevirin.
3. `data:image/jpeg;base64,` URI'sını oluşturup `args.Uri`'ye atayın.

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **İpucu:** Kaynak Word belgeniz PNG kullanıyorsa, `ImageSaveOptions.DefaultJpeg` yerine `ImageSaveOptions.DefaultPng` kullanın ve MIME tipini (`image/png`) buna göre değiştirin.

## Adım 3: Belgeyi Markdown Olarak Kaydet – son **save word as markdown** adımı

Callback hazır olduğuna göre, gerçek kaydetme tek satırda yapılır.

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

`output.md` dosyasını herhangi bir markdown görüntüleyicide (VS Code önizlemesi, GitHub vb.) açtığınızda, metnin orijinal Word dosyasıyla aynı olduğunu ve resimlerin ayrı dosya olmadan satır içinde göründüğünü göreceksiniz.

## Beklenen Çıktı

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

`![Embedded Image]` satırı bir **base64 resim veri URI'sı**dır—tüm resim burada kodlanmıştır. Ek klasör yok, kırık link de yok.

## Kenar Durumları ve Çözümleri

| Durum | Ne Yapmalı |
|-----------|------------|
| **Büyük Resimler** – Base64 boyutu yaklaşık %33 artırır | Dönüştürmeden önce yeniden boyutlandırmayı düşünün: `args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`. |
| **JPEG Olmayan Resimler (PNG, GIF) | Orijinal formatı `args.ResourceData.ImageType` ile tespit edin ve doğru MIME tipini (`image/png`, `image/gif`) ayarlayın. |
| **Çok Uzun Belgeler** (yüzlerce resim) | Bellek kullanımına dikkat edin; işlem RAM yetersiz kalırsa her resmi geçici olarak diske akıtabilirsiniz. |
| **Ayrı Resim Dosyalarına İhtiyaç** (ör. statik site) | İstediğiniz resimler için callback'ten `false` döndürün ve Aspose'un onları bir klasöre yazmasına izin verin. |

## Sık Sorulan Sorular (Önceden Yanıtlandı)

- **.doc dosyalarıyla da çalışır mı?** Evet—Aspose.Words, eski `.doc` dosyalarını da aynı şekilde `new Document("myfile.doc")` ile yükleyebilir.
- **Tablolar ve dipnotlar nasıl ele alınır?** Markdown aktarımcısı tarafından tam desteklenir. Tablolar markdown tablolarına, dipnotlar satır içi referanslara dönüşür.
- **Markdown çeşidini değiştirebilir miyim?** `MarkdownSaveOptions` içinde bir `MarkdownVersion` özelliği vardır (CommonMark, GitHub vb.). İhtiyacınıza göre kaydetmeden önce ayarlayın.

## Tam, Hazır‑Çalıştır Örnek

Aşağıda bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz tam program yer alıyor. Tüm `using` ifadeleri, işleyici sınıfı ve hata yönetimi dahildir.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

Programı çalıştırın, oluşturulan `output.md` dosyasını açın ve Word belgenizin mükemmel bir markdown kopyasını görün—**convert word to markdown** hiç bu kadar kolay olmamıştı.

## Özet

**convert word to markdown** sorununun resimleri satır içinde tutma ihtiyacını ele aldık. Belgeyi yükleyerek, bir `MarkdownSaveOptions` callback'i yapılandırarak ve dosyayı kaydederek temiz bir **save word as markdown** çözümü elde ettik; bu da **base64 image data uri** dizeleri üretir. Artık **embed images as base64**, kenar durumlarını yönetme ve farklı resim tipleri için ayarlama konularını da biliyorsunuz.

## Sıradaki Adımlar

- **Markdown yerine HTML üret** – `MarkdownSaveOptions` yerine `HtmlSaveOptions` kullanın ve aynı callback'i yeniden kullanın.
- **Birden çok dosyayı toplu dönüştür** – Mantığı bir klasör üzerindeki `foreach` döngüsüyle sarın.
- **CI pipeline'ına entegre et** – Statik site dokümantasyonunu otomatikleştirin.

Denemeler yapmaktan, resim kalitesini ayarlamaktan veya kendi özel kaynak işleyicilerinizi (ör. CDN'ye yükleyip URL eklemek) eklemekten çekinmeyin. Aspose.Words ve biraz C# yaratıcılığıyla sınır yok.

İyi kodlamalar, ve markdown'unuz her zaman kusursuz render olsun! 

![convert word to markdown akışını gösteren diyagram – embed images as base64](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "convert word to markdown flow diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}