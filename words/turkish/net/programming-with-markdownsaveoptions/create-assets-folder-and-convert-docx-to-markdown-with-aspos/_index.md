---
category: general
date: 2026-03-21
description: DOCX'i Markdown'a dönüştürürken assets klasörü oluşturun. Word'ten resimleri
  nasıl çıkaracağınızı ve Word'ü C# ile Markdown olarak nasıl kaydedeceğinizi öğrenin.
draft: false
keywords:
- create assets folder
- convert docx to markdown
- extract images from word
- extract embedded images
- save word as markdown
language: tr
og_description: DOCX'i Markdown'a dönüştürürken assets klasörü oluşturun. Bu öğreticide,
  Word'ten resimleri nasıl çıkaracağınızı ve Word'ü C# kullanarak Markdown olarak
  nasıl kaydedeceğinizi gösteriyor.
og_title: Varlıklar klasörü oluşturun ve DOCX'i Markdown'a dönüştürün – Tam Kılavuz
tags:
- Aspose.Words
- C#
- Document Conversion
title: Varlıklar klasörü oluştur ve Aspose.Words ile DOCX'i Markdown'a dönüştür
url: /tr/net/programming-with-markdownsaveoptions/create-assets-folder-and-convert-docx-to-markdown-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Assets klasörü oluşturma ve DOCX'i Aspose.Words ile Markdown'a dönüştürme

Bir Word dosyasını Markdown'a dönüştürürken **assets klasörü oluşturma** ihtiyacınız oldu mu? Tek başınıza değilsiniz—geliştiriciler sürekli olarak *docx'i markdown'a dönüştürürken* görüntüleri düzenli tutmanın yolunu soruyor. İyi haber, Aspose.Words size her ikisini tek bir geçişte temiz, programatik bir şekilde yapma imkanı sunuyor.

Bu öğreticide tüm süreci adım adım inceleyeceğiz: bir `.docx` dosyasını yükleme, Markdown dışa aktarıcısını yapılandırma, gömülü görüntüleri çıkarma ve sonunda sonucu bir `assets` dizinine referans veren `.md` dosyası olarak kaydetme. Sonunda *Word'den görüntü çıkarma* ve *Word'ü markdown olarak kaydetme* işlemlerini manuel kopyala‑yapıştırmadan yapabilen yeniden kullanılabilir bir kod parçacığına sahip olacaksınız.

## Gereksinimler

- **Aspose.Words for .NET** (en son sürüm, örn. 24.10).  
- .NET geliştirme ortamı (Visual Studio, Rider veya VS Code).  
- En az bir resim içeren örnek bir `input.docx`—aksi takdirde *gömülü görüntüleri çıkarma* adımını göremezsiniz.

Başka üçüncü‑taraf kütüphane gerekmez; her şey Aspose.Words içinde bulunur.

---

## Assets klasörü oluşturma ve Markdown dönüşümünü ayarlama

İlk olarak istediğimiz, Word belgesinden çıkarılan her görüntünün konulacağı özel bir klasördür. Bunu, statik site jeneratörlerinde sıkça gördüğünüz “assets” kovası olarak düşünün. Dosya adını Aspose.Words'in belirlemesine izin vereceğiz, ardından klasör yolunu başına ekleyeceğiz.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// 1️⃣ Load the source Word document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// 2️⃣ Prepare Markdown save options with a callback that decides where resources go
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new ResourceSavingCallback(info =>
    {
        // 👉 Define the folder that will hold every extracted image
        string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
        Directory.CreateDirectory(assetsFolder); // creates it if it doesn't exist

        // 👉 Tell Aspose to place the current resource inside that folder
        info.FileName = Path.Combine(assetsFolder, info.FileName);
    })
};
```

> **Neden bir geri arama?**  
> `ResourceSavingCallback`, her gömülü nesne (görseller, OLE nesneleri vb.) için tetiklenir. Bunu yakalayarak **Word'den görüntü çıkarma** işlemini anında yapabiliriz, böylece görüntüleri başka bir yere kaydedip daha sonra taşımak zorunda kalmayız. Bu, *save word as markdown* adımını atomik tutar ve I/O yükünü azaltır.

---

## Adım 1: DOCX belgesini yükleme  

*docx'i markdown'a dönüştürmeden* önce bir `Document` örneğine ihtiyacımız var. Yapıcı (constructor) bir yol, bir akış (stream) veya hatta bir bayt dizisi alabilir—iş akışınıza uyanı seçin.

```csharp
// Example using a relative path; adjust for your environment
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **İpucu:** Bir web API'sinde yüklemeleri işliyorsanız, geçici bir dosya yazmaktan kaçınmak için yüklenen `Stream`'i doğrudan geçirin.

## Adım 2: MarkdownSaveOptions'ı yapılandırma – çıkarımın kalbi  

`MarkdownSaveOptions`, dönüşümün nasıl davranacağını ince ayarlarla kontrol etmenizi sağlar. Hedefimiz için en önemli özellik `ResourceSavingCallback`, ki bunu zaten ayarlamıştık. Görüntü formatını, bağlantı stilini ve daha fazlasını da ayarlayabilirsiniz.

```csharp
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    // Ensure images are saved as PNG by default (you can change this)
    ImageSavingFormat = ImageSaveOptions.SaveFormat.Png,

    // The callback defined earlier handles the assets folder creation
    ResourceSavingCallback = new ResourceSavingCallback(info =>
    {
        string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
        Directory.CreateDirectory(assetsFolder);
        info.FileName = Path.Combine(assetsFolder, info.FileName);
    })
};
```

> **İki görüntü aynı adı paylaşırsa ne olur?**  
> Aspose otomatik olarak sayısal bir ek ekler (`image.png`, `image_1.png`, …) böylece dosyaları kaybetmezsiniz.

## Adım 3: Assets klasörünü tanımlama ve görüntü yollarını işleme  

Geri arama *her kaynak için bir kez* çalışır. İçinde şu adımları yaparız:

1. `Path.Combine` kullanarak `assets` klasörünün mutlak yolunu oluştururuz.  
2. `Directory.CreateDirectory` çağrısı—bu, tekrar tekrar çağrılabilir; klasör yalnızca ilk çağrıda oluşturulur.  
3. `info.FileName`'i tam yol ile değiştiririz, böylece Markdown yazıcısı doğru göreli bağlantıyı yazar.

```csharp
ResourceSavingCallback = new ResourceSavingCallback(info =>
{
    string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
    Directory.CreateDirectory(assetsFolder);
    info.FileName = Path.Combine(assetsFolder, info.FileName);
})
```

> **Pro ipucu:** Markdown dosyasının görüntülere web‑dostu bir URL (örnek: `/static/assets/`) ile referans vermesini istiyorsanız, `Path.Combine`'ı istediğiniz göreli URL'yi oluşturan bir string ile değiştirin.

## Adım 4: Belgeyi Markdown olarak kaydetme  

Artık her şey bağlandığına göre, son satır basit bir `Save` işlemidir. Aspose, Word DOM'unu dolaşacak, `output.md` dosyasına Markdown sözdizimini yazacak ve her görüntüyü oluşturduğumuz `assets` dizinine dökecek.

```csharp
// 5️⃣ Perform the conversion – this writes both the .md file and the images
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

İşlem tamamlandığında aşağıdaki gibi bir klasör yapısı göreceksiniz:

```
YOUR_DIRECTORY/
├─ input.docx
├─ output.md
└─ assets/
   ├─ image1.png
   └─ image2.png
```

*Şekil 1: Dönüştürmeden sonraki klasör düzeni (alt metin: “assets klasörü oluşturma diyagramı”).*  

Markdown dosyası `![](assets/image1.png)` gibi bağlantılar içerecek, bu da çoğu statik site jeneratörünün beklediği şeydir.

## Tam Çalışan Örnek  

Aşağıda, bir konsol uygulaması olarak çalıştırabileceğiniz kopyala‑yapıştır hazır bir program bulunmaktadır. `YOUR_DIRECTORY` ifadesini kaynak dosyanızın bulunduğu yol ile değiştirin.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

class Program
{
    static void Main()
    {
        // 👉 Step 1 – Load the DOCX you want to convert
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 👉 Step 2 – Set up Markdown options and the assets folder callback
        MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
        {
            // Optional: force PNG output for all images
            ImageSavingFormat = ImageSaveOptions.SaveFormat.Png,

            // This callback runs for each extracted resource (image, etc.)
            ResourceSavingCallback = new ResourceSavingCallback(info =>
            {
                // 👉 Define where the extracted images will live
                string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
                Directory.CreateDirectory(assetsFolder);

                // 👉 Save each image inside that folder
                info.FileName = Path.Combine(assetsFolder, info.FileName);
            })
        };

        // 👉 Step 3 – Save as Markdown; assets are created automatically
        document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);

        // 🎉 Done! Check YOUR_DIRECTORY for output.md and the assets folder.
    }
}
```

### Beklenen Sonuç

- `output.md`, orijinal Word başlıklarını, madde işaretli listeleri ve tabloları yansıtan Markdown metni içerir.  
- `input.docx` içindeki her resim, Markdown dosyasında `![](assets/<imageName>.png)` olarak görünür.  
- `assets` klasörü gerçek PNG dosyalarını tutar ve herhangi bir statik‑site sunucusu tarafından sunulmaya hazırdır.

---

## Sık Sorulan Sorular & Kenar Durumları

| Soru | Cevap |
|----------|--------|
| **DOCX'in içinde resim yoksa ne olur?** | Geri arama hiç tetiklenmez, bu yüzden `assets` klasörü boş kalır. Bir sorun oluşmaz. |
| **Görüntü formatını JPEG'e değiştirebilir miyim?** | Evet—`MarkdownSaveOptions` içinde `ImageSavingFormat = ImageSaveOptions.SaveFormat.Jpeg` olarak ayarlayın. |
| **Sonraki çalıştırmalarda assets klasörünü temizlemem gerekiyor mu?** | Aynı Markdown dosyasını yeniden oluşturuyorsanız eski dosyaları silmek veya üzerine yazmak iyi bir uygulamadır, aksi takdirde sahipsiz görüntüler birikebilir. |
| **Farklı işletim sistemlerinde göreli bağlantı nasıl çalışır?** | Fiziksel yol için `Path.Combine` kullandığımız ve Aspose'in *göreli* bir bağlantı (`assets/image.png`) yazdığı için Markdown Windows, macOS ve Linux'ta aynı şekilde çalışır. |
| **Assets klasörünü bir zip içine gömebilir miyim?** | Kesinlikle—dönüştürmeden sonra `output.md` dosyasını `assets` diziniyle birlikte zipleyin. Klasör yapısı korunduğu sürece Markdown bağlantıları geçerli kalır. |

---

## Sonraki Adımlar

Artık **assets klasörü oluşturma**, **docx'i markdown'a dönüştürme** ve **Word'den görüntü çıkarma** konularını bildiğinize göre, aşağıdakileri keşfetmek isteyebilirsiniz:

- **Markdown stilini özelleştirme** – `MarkdownSaveOptions` içinde `ExportHeadersAsBold`, `ExportTableHeaders` ve diğer bayrakları değiştirin.  
- **Toplu işleme** – bir dizindeki `.docx` dosyaları üzerinde döngü kurarak eşleşen Markdown/asset çiftleri oluşturun.  
- **Hugo veya Jekyll gibi statik site jeneratörleriyle entegrasyon** – az önce oluşturduğumuz tam klasör düzenini bekleyen jeneratörler.

Daha gelişmiş senaryolarla ilgileniyorsanız—örneğin Word dipnotlarını koruma veya gömülü OLE nesnelerini işleme—resmi Aspose.Words belgelerine göz atın (“MarkdownSaveOptions” ve “ResourceSavingCallback” arayın).

## Sonuç

Aspose.Words for .NET kullanarak **assets klasörü oluşturma**, **gömülü görüntüleri çıkarma** ve **Word belgesini Markdown olarak kaydetme** konularını kapsayan tam, uçtan uca bir çözüm üzerinden geçtik. Ana çıkarım, `ResourceSavingCallback`'in her görüntünün nereye kaydedileceği üzerinde tam kontrol sağlamasıdır; bu sayede Markdown dosyanızı düzenli tutar ve yayınlamaya hazır hâle getirirsiniz.

Bunu deneyin, görüntü formatını değiştirin ya da mantığı yeniden kullanılabilir bir servise sarın—ne seçerseniz seçin, artık *docx'i markdown'a dönüştürme* iş akışı için *Word'den görüntü çıkarma* ve *Word'ü markdown olarak kaydetme* ihtiyacı olan sağlam bir temele sahipsiniz.

Kodlamanın tadını çıkarın! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}