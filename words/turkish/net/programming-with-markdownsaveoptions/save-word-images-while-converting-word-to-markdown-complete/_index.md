---
category: general
date: 2026-02-20
description: Word görüntülerini kaydetmeyi ve Word'ü C#'ta markdown’a dönüştürmeyi
  öğrenin. Bu adım adım rehber, ayrıca Word’ten görüntüleri çıkarmayı ve görüntülerle
  markdown dışa aktarmayı da gösterir.
draft: false
keywords:
- save word images
- convert word to markdown
- extract images from word
- convert docx to md
- export markdown with images
language: tr
og_description: Bu rehberde, Aspose.Words kullanarak Word görsellerini nasıl kaydedeceğinizi
  ve Word'ü markdown'a nasıl dönüştüreceğinizi gösteriyoruz. Görsellerle birlikte
  markdown dışa aktarmak için adımları izleyin.
og_title: Word görsellerini kaydet, Word'ü Markdown'a dönüştürürken – Tam C# Öğreticisi
tags:
- Aspose.Words
- C#
- Markdown
title: Word'ten Markdown'a çevirirken Word resimlerini kaydet – Tam C# Rehberi
url: /tr/net/programming-with-markdownsaveoptions/save-word-images-while-converting-word-to-markdown-complete/
---

but keep technical terms in English. "save word images" is a phrase; maybe keep as is? It's not a standard term. Could translate "kelime resimlerini kaydet". I'll translate.

Also keep code block placeholders unchanged.

Let's go through each section.

First shortcodes lines remain.

Then title.

Then paragraph.

Translate each sentence.

Make sure to keep markdown formatting.

Also tables: translate column headers and content? Keep property names unchanged. Translate "Typical value", "When to change". Keep property names unchanged.

Also bullet points.

Let's craft.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'ü Markdown'a dönüştürürken kelime resimlerini kaydet – Tam C# Rehberi

Bir Word belgesini Markdown'a dönüştürürken **kelime resimlerini kaydetmeniz** gerektiğinde hiç zorlandınız mı? Tek başınıza değilsiniz—geliştiriciler sık sık `convert docx to md` işlemi sonrası resimlerin kaybolması sorunuyla karşılaşıyor. Bu öğreticide, **kelime resimlerini kaydetme**, **kelimeyi markdown'a dönüştürme** ve tüm resimlerin hâlâ göründüğü bir Markdown dosyası elde etme sürecini temiz ve üretim‑hazır bir şekilde adım adım göstereceğiz.

Diyelim ki `input.docx` adlı bir kullanıcı kılavuzunuz var ve bunu statik bir sitede yayınlamak istiyorsunuz. Metni Markdown olarak, ekran görüntülerini, diyagramları ve logoları da tam olarak bulundukları yerde görmek istiyorsunuz. Çözümümüz bu sorunu dış araçlar, manuel kopyala‑yapıştırma olmadan, sadece birkaç C# satırı ve Aspose.Words ile halledecek.

Bu rehberin sonunda şunları yapabilecek duruma geleceksiniz:

* Aspose.Words ile bir `.docx` dosyasını yüklemek.  
* `MarkdownSaveOptions` yapılandırmasını, **kelime resimlerini dışa aktarmasını** sağlayacak şekilde ayarlamak.  
* Her resmi benzersiz bir adla belirli bir klasöre yazan bir geri çağırma (callback) uygulamak.  
* Oluşturulan `.md` dosyasının resim referanslarını doğru şekilde gösterdiğini doğrulamak; yani **markdown'ı resimlerle dışa aktarma** işlemini başarıyla tamamlamış olacaksınız.

> **Önkoşullar** – .NET 6+ (veya .NET Framework 4.6+), geçerli bir Aspose.Words lisansı (veya ücretsiz deneme sürümü) ve temel C# bilgisi gerekir. Aspose ile hiç çalışmadıysanız endişelenmeyin; API basit ve aşağıdaki kod tamamen bağımsızdır.

---

## Word'ü Markdown'a dönüştürürken kelime resimlerini nasıl kaydederiz

İlk adım, dönüşüm sürecinde **kelime resimlerini kaydetmek**tir. Aspose.Words, dış kaynaklar (resimler, grafikler, SVG'ler vb.) için çalışan bir `ResourceSavingCallback` sunar. Kendi uygulamamızı takarak her resmin diskte nereye kaydedileceğini tam olarak belirleyebiliriz.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source Word document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Configure Markdown save options and attach a callback that will handle external resources
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image, letting us control the file name and folder
    ResourceSavingCallback = new MyResourceCallback()
};

// Save the document as Markdown; the callback will store images in a custom folder
document.Save("YOUR_DIRECTORY/output.md", markdownOptions);

// -----------------------------------------------------------------
// Callback implementation – stores each image in a dedicated folder with a unique name
class MyResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Define the folder where resources will be saved
        string resourceFolder = "YOUR_DIRECTORY/MarkdownResources";
        Directory.CreateDirectory(resourceFolder);

        // Generate a unique file name while preserving the original extension
        string uniqueFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // Tell Aspose.Words where to write the resource
        args.ResourceFileName = Path.Combine(resourceFolder, uniqueFileName);
    }
}
```

Hepsi bu kadar—çalıştırın ve `output.md` ile birlikte içinde resim dosyaları bulunan bir `MarkdownResources` klasörünüz olacak. Markdown dosyası, `![](MarkdownResources/7f3c2a1e-...png)` gibi linkler içerecek ve **kelime resimlerini kaydetme** ile **markdown'ı resimlerle dışa aktarma** işlemini tek seferde tamamlamış olacaksınız.

---

## Markdown seçeneklerini docx'ten md'ye dönüştürmek için yapılandırma

Neden bir geri çağırma (callback) kullanıyoruz? Varsayılan olarak Aspose.Words, resimleri Markdown içinde base‑64 string olarak gömer; bu da dosya boyutunu şişirir ve sürüm kontrolünü zorlaştırır. `ResourceSavingCallback` ayarlamak, kütüphaneye **docx'ten md'ye dönüştürme** sırasında her resmi diske yazmasını söyler, satır içi (inline) eklemek yerine.

### Ayarlayabileceğiniz temel özellikler

| Property | Typical value | When to change |
|----------|---------------|----------------|
| `ExportImagesAsBase64` | `false` (default) | Resimleri ayrı dosyalar olarak tutmak istediğinizde. |
| `ImagesFolder` | `null` (callback kullanıldığında yok sayılır) | Dinamik adlandırma ihtiyacınız yoksa sabit bir klasör belirleyebilirsiniz. |
| `ExportHeadersFooters` | `true` | Header/footer içinde resim olabilecek içerikleri korur. |
| `EncodeUrls` | `true` | Yol adlarında boşluk veya ASCII dışı karakterler varsa gerekir. |

> **Pro ipucu:** Çok dilli dokümantasyon üretiyorsanız, `resourceFolder`a bir dil kodu eklemeyi düşünün (ör. `MarkdownResources/tr`) böylece resim yolları düzenli kalır.

---

## Kelime resimlerini dışa aktarmak için bir kaynak geri çağırması (resource callback) uygulama

Önceki kod bloğundaki geri çağırma (callback) işi halleder, ancak biraz daha detaylandıralım. `IResourceSavingCallback` her dış kaynak için bir `ResourceSavingArgs` nesnesi alır. En önemli alanlar şunlardır:

* `ResourceFileName` – dosyanın yazılacağı yol.  
* `ResourceFileExtension` – orijinal uzantı (`.png`, `.jpg` vb.).  
* `ResourceType` – kaynağın resim, grafik vb. olduğunu belirtir.

Sadece resimlerle ilgileniyorsanız, resim olmayan kaynakları filtreleyebilirsiniz:

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    // Skip non‑image resources – we only want to save pictures
    if (args.ResourceType != ResourceType.Image)
        return;

    string resourceFolder = "YOUR_DIRECTORY/MarkdownResources";
    Directory.CreateDirectory(resourceFolder);

    string uniqueFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
    args.ResourceFileName = Path.Combine(resourceFolder, uniqueFileName);
}
```

### Kenar‑durum (edge‑case) yönetimi

1. **Çift (duplicate) resimler** – Aynı resim birden fazla kez göründüğünde, geri çağırma her seferinde yeni bir dosya yazar. Tekilleştirme (deduplication) isterseniz, resim baytlarının hash'ini mevcut dosya adıyla eşleyen bir `Dictionary<string, string>` tutabilirsiniz.  
2. **Desteklenmeyen formatlar** – Aspose.Words PNG, JPEG, GIF, BMP ve TIFF dışa aktarabilir. Eğer egzotik bir formatla karşılaşırsanız, kendiniz dönüştürmeniz gerekir (ör. `System.Drawing` kullanarak).  
3. **Büyük belgeler** – Çok büyük PDF veya DOCX dosyaları için çıktıyı akış (stream) olarak kaydetmeyi düşünün; böylece bellek tükenmez. `MarkdownSaveOptions` `SaveOptions.UseMemoryCache = false` ayarını destekler.

---

## Belgeyi kaydedin ve resimlerle dışa aktarılan markdown'ı doğrulayın

Kodu çalıştırdıktan sonra `output.md` dosyasını herhangi bir metin editöründe açın. Şuna benzer bir içerik görmelisiniz:

```markdown
# Chapter 1

Here is a diagram:

![](MarkdownResources/2c7f9a3e-9b4d-4f6a-8d12-5e9f2c7a1b3c.png)

And another screenshot:

![](MarkdownResources/7a1d4e2f-3c9b-4a5d-9e8f-6b2c3d4e5f6a.jpg)
```

Resim linkleri doğru görünüyorsa, Markdown dosyasını bir görüntüleyicide (VS Code önizlemesi, GitHub veya bir statik‑site jeneratörü) açın. Resimler otomatik olarak render edilecek ve **kelime resimlerini kaydetme** ile **markdown'ı resimlerle dışa aktarma** işlemini başarıyla tamamladığınız doğrulanacaktır.

### Hızlı doğrulama betiği

Kontrolü otomatikleştirmek isterseniz, aşağıdaki snippet oluşturulan Markdown içinde eksik dosyaları tarar:

```csharp
using System;
using System.IO;
using System.Text.RegularExpressions;

string mdPath = "YOUR_DIRECTORY/output.md";
string mdFolder = Path.GetDirectoryName(mdPath)!;
string[] lines = File.ReadAllLines(mdPath);

foreach (var line in lines)
{
    var match = Regex.Match(line, @"!\[.*?\]\((.+?)\)");
    if (match.Success)
    {
        string imgPath = Path.Combine(mdFolder, match.Groups[1].Value);
        if (!File.Exists(imgPath))
            Console.WriteLine($"Missing image: {imgPath}");
    }
}
Console.WriteLine("Verification complete.");
```

Dönüştürmeden sonra çalıştırın; eksik bir resim varsa konsola yazdırılacaktır.

---

## Word'ü markdown'a dönüştürürken yaygın tuzaklar ve en iyi uygulamalar

| Pitfall | Why it hurts | Fix |
|---------|--------------|-----|
| **Images end up with long GUID names** | Kaynak kontrolünde okunması zor. | Klasörü, orijinal `args.ResourceFileName` gibi anlamlı başlıklarla yeniden adlandırın. |
| **Relative paths break after moving the Markdown file** | `![]()` linkleri `.md` dosyasının konumuna göre görecelidir. | Resim klasörünü Markdown dosyasının yanına koyun veya statik site konfigürasyonunda tutarlı bir temel yol (base path) kullanın. |
| **Missing images when `ExportImagesAsBase64` is `true`** | Geri çağırma hiç çalışmaz çünkü resimler satır içinde gömülüdür. | `ExportImagesAsBase64 = false` (varsayılan) olduğundan emin olun. |
| **Large documents cause `OutOfMemoryException`** | Aspose tüm belgeyi RAM'e yükler. | `LoadOptions` ile `LoadFormat.Docx` ayarlayın ve mümkünse `MemoryOptimization` bayraklarını kullanın. |
| **Non‑ASCII file names break on some platforms** | URL kodlaması başarısız olabilir. | ASCII karakterler kullanın veya `EncodeUrls = true` ayarlayın. |

---

## Özet

Aspose.Words kullanarak **kelime resimlerini kaydetme** ve **kelimeyi markdown'a dönüştürme** sürecinde ihtiyacınız olan her şeyi ele aldık. Temel fikir basit: bir `ResourceSavingCallback` ekleyin, kontrol ettiğiniz bir klasöre yönlendirin ve kütüphane geri kalanını yapsın. Çalıştırdıktan sonra temiz bir `.md` dosyanız ve düzenli bir resim varlığı setiniz olacak—yayınlamak veya sürüm kontrolüne almak için mükemmel.

Resimleri başka amaçlarla **kelime dışa aktarma** (ör. bir galeri oluşturma) istiyorsanız, Markdown kaydetme adımını atıp sadece geri çağırma kodunu yeniden kullanabilirsiniz. Aynı desen, toplu işler için **docx'ten md'ye dönüştürme** işlemlerinde de işe yarar; sadece bir klasördeki `.docx` dosyalarını döngüyle işleyip aynı mantığı uygulayın.

**İleride keşfedebileceğiniz adımlar:**

* Dönüştürmeyi bir ASP.NET Core API içine entegre ederek kullanıcıların DOCX yükleyip indirilebilir bir Markdown paketi almasını sağlamak.  
* Tablo desteği eklemek ve

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}