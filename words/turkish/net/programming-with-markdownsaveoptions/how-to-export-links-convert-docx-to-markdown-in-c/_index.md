---
category: general
date: 2026-03-24
description: Word dosyasından bağlantıları nasıl dışa aktaracağınızı ve Word'ü markdown
  olarak nasıl kaydedeceğinizi öğrenin. Bu rehber, docx'i markdown'a nasıl dönüştüreceğinizi
  ve Word'den hızlı bir şekilde markdown oluşturmayı gösterir.
draft: false
keywords:
- how to export links
- convert docx to markdown
- how to convert docx
- save word as markdown
- create markdown from word
language: tr
og_description: DOCX'ten bağlantıları nasıl dışa aktarılır ve Word'ü markdown olarak
  kaydedilir. Docx'i markdown'a dönüştürmek ve Word'den markdown oluşturmak için adım
  adım rehber.
og_title: 'Bağlantıları Dışa Aktarma: DOCX''i C#''ta Markdown''a Dönüştürme'
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: 'Bağlantıları Nasıl Dışa Aktarırsınız: C#''ta DOCX''i Markdown''a Dönüştürme'
url: /tr/net/programming-with-markdownsaveoptions/how-to-export-links-convert-docx-to-markdown-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bağlantıları Dışa Aktarma: DOCX'i C#'ta Markdown'a Dönüştürme

Word belgesindeki bağlantıların URL'lerini kaybetmeden **bağlantıları dışa aktarma** yöntemini hiç merak ettiniz mi? Belki içeriği bir static‑site jeneratörüne itmeniz gerekiyor, ya da sadece doğru yerlere işaret eden temiz bir Markdown dosyası istiyorsunuz. Bu öğreticide, bir *.docx* dosyasını nasıl yükleyeceğinizi, link‑export davranışını nasıl yapılandıracağınızı ve **Word'ü markdown olarak kaydet** adımlarını göstereceğiz. Sonunda **docx'i markdown'a dönüştür** yöntemini her proje için bilecek ve **word'den markdown oluştur** dosyaları için hızlı bir desen göreceksiniz.

> **Neden önemli:** Markdown, modern dokümantasyon, blog ve read‑me dosyalarının ortak dili. Word'den Markdown'a geçerken hiperlinklerinizi korumak, saatler süren manuel düzeltmelerden sizi kurtarır.

## Gereksinimler

- .NET 6+ (veya .NET Framework 4.7+)
- **Aspose.Words for .NET** NuGet paketi (versiyon 23.5 veya daha yeni)
- Birkaç hiperlink içeren örnek `input.docx`
- Rahat olduğunuz bir IDE veya editör (Visual Studio, VS Code, Rider…)

Hepsi bu—ekstra kütüphane, dış hizmet yok. Hadi başlayalım.

---

## Word'den Markdown'a Bağlantı Dışa Aktarma

Aşağıda, **bağlantıları dışa aktarma** sırasında bir DOCX dosyasını Markdown belgesine dönüştüren tam, çalıştırılabilir kod yer alıyor.

```csharp
// ------------------------------------------------------------
// Step 0: Add required namespaces
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // ------------------------------------------------------------
        // Step 1: Load the source document
        // ------------------------------------------------------------
        // Replace YOUR_DIRECTORY with the actual folder path.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // ------------------------------------------------------------
        // Step 2: Configure Markdown save options
        // ------------------------------------------------------------
        // LinkExportMode determines how hyperlinks are written:
        //   Absolute – full URL (e.g., https://example.com/page)
        //   Relative – relative path based on the document location
        //   PlainText – only the link text, no URL
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // For most web‑centric workflows we want absolute URLs.
            LinkExportMode = LinkExportMode.Absolute
        };

        // ------------------------------------------------------------
        // Step 3: Save the document as a Markdown file
        // ------------------------------------------------------------
        doc.Save(@"YOUR_DIRECTORY\Links.md", mdOptions);

        Console.WriteLine("✅ Conversion complete! Links have been exported.");
    }
}
```

### Üç temel adımın açıklaması

1. **DOCX'i Yükle** – `Document` Aspose.Words'ün giriş noktasıdır. `.docx` dosyasını ayrıştırır, bellek içi bir nesne modeli oluşturur ve her paragraf, tablo ve hiperlinke erişim sağlar.  
2. **`MarkdownSaveOptions`'ı Yapılandır** – `LinkExportMode` enum'u **bağlantıları nasıl dışa aktaracağınız** konusunda kilit rol oynar.  
   - `Absolute` tam URL'yi yazar; Markdown farklı bir domain'de barındırılacaksa idealdir.  
   - `Relative` Markdown dosyasının yanındaki site içi linkler için kullanışlıdır.  
   - `PlainText` URL'yi tamamen kaldırır, sadece görüntü metnini bırakır.  
3. **Markdown Olarak Kaydet** – `Save` metodu, başlıklar, madde işaretli listeler ve **dışa aktarılan linkler** dahil, orijinal Word yapısını yansıtan bir `.md` dosyası yazar.

> **Pro ipucu:** Birden çok belgeyi toplu olarak dönüştürüyorsanız, tekrar eden tahsislerden kaçınmak için tek bir `MarkdownSaveOptions` örneğini yeniden kullanın.

---

## DOCX'i Markdown'a Dönüştür – Hızlı Bir Özet

Yukarıdaki kod zaten **docx'i markdown'a dönüştür**, şimdi daha geniş iş akışını parçalayalım ki diğer bağlamlarda da kullanabilelim:

| Aşama | Ne Yaparsınız | Neden Önemli |
|-------|---------------|--------------|
| **Oku** | `new Document(path)` | Word dosyasını belleğe yükler. |
| **Yapılandır** | `MarkdownSaveOptions`'ı ayarla (link modu, resim işleme vb.) | Çıktı Markdown'un tam kontrolünü sağlar. |
| **Yaz** | `doc.Save(outputPath, options)` | Son `.md` dosyasını üretir. |

Bağlantı modunu `Relative` olarak değiştirerek **save word as markdown** işlemini göreceli linklerle yapabilir, ya da sadece link metnine ihtiyacınız varsa `PlainText` seçebilirsiniz. Aynı desen, `SaveOptions` sınıfını değiştirerek (HTML, PDF vb.) diğer formatlar için de çalışır.

---

## Opsiyonel: Resimler ve Gömülü Kaynakların İşlenmesi

Word belgenizde resimler varsa, Aspose.Words varsayılan olarak bunları Markdown içinde base‑64 string olarak gömer. Bu dosyayı taşınabilir kılar ancak boyutunu şişirebilir. Resimleri dış dosyalar olarak tutmak için:

```csharp
mdOptions.ExportImagesAsBase64 = false;   // Store images as separate files
mdOptions.ImagesFolder = @"YOUR_DIRECTORY\Images"; // Folder for extracted images
```

Şimdi her resim `Images` klasörüne kaydedilir ve Markdown, bunları göreceli bir yol ile referans alır—statik‑site jeneratörlerinin varlıkları içerikle aynı konumda beklediği durumlar için mükemmeldir.

---

## Kenar Durumları & Yaygın Tuzaklar

| Durum | Dikkat Edilmesi Gereken | Önerilen Çözüm |
|-------|------------------------|----------------|
| **Hiperlink hedefi eksik** | Aspose.Words boş bir URL bırakabilir, Markdown'da `[]()` oluşur. | `LinkExportMode`'u doğrulayın ve dönüştürmeden önce kaynak Word dosyasındaki kırık linkleri kontrol edin. |
| **Çok uzun URL'ler** | Markdown satırları zorlayıcı hâle gelebilir. | Mümkünse `LinkExportMode.Relative` kullanın veya `.md` dosyasını sonradan URL'leri satır sonuna taşıyacak şekilde işleyin. |
| **URL'lerde ASCII dışı karakterler** | Bazı ayrıştırıcılar yüzde‑kodlu karakterleri yanlış yorumlayabilir. | Belgenizin UTF-8 kodlamasını (Aspose.Words varsayılanı) kullandığından emin olun ve çıktıyı hedef renderlayıcınızda test edin. |
| **Büyük belgeler (>100 MB)** | Bellek tüketimi artar. | `LoadOptions` ile `LoadFormat.Docx` kullanarak belgeyi akış (stream) şeklinde yükleyin ve sayfaları parçalar halinde işlemeyi düşünün. |

---

## Sonucu Doğrulama

Programı çalıştırdıktan sonra `Links.md` dosyasını açın. Şuna benzer bir içerik görmelisiniz:

```markdown
# Sample Document

Welcome to our guide. Visit the [Aspose website](https://www.aspose.com) for more info.

Check out the [GitHub repo](https://github.com/aspose-words/Aspose.Words-for-.NET) for source code.
```

Her hiperlink, orijinal DOCX'te göründüğü gibi tam korunur. `Relative`'a geçerseniz URL'ler göreceli yollar olur.

---

## Sık Sorulan Sorular

**S: .doc (eski Word formatı) dosyalarıyla da çalışır mı?**  
C: Evet. Aspose.Words formatı otomatik algılar, bu yüzden `.doc` yolunu `new Document()`'a verebilirsiniz ve aynı `MarkdownSaveOptions` geçerli olur.

**S: Bir klasördeki tüm DOCX dosyalarını tek seferde dönüştürebilir miyim?**  
C: Kesinlikle. Kodu `foreach (var file in Directory.GetFiles(folder, "*.docx"))` döngüsüyle sarın, aynı `mdOptions` nesnesini yeniden kullanın.

**S: Orijinal satır sonlarını korumam gerekiyor, ne yapmalıyım?**  
C: `mdOptions.ExportHeadersFooters = true` ve `mdOptions.ExportTableStructure = true` ayarlarını etkinleştirerek düzen nüanslarını koruyabilirsiniz.

---

## Sonraki Adımlar: Markdown'tan Statik Siteye

Artık **word'den markdown oluştur** yeteneğine sahipsiniz; çıktıyı Hugo ya da Jekyll gibi bir static‑site jeneratörüne itmek isteyebilirsiniz. İşte hızlı bir kontrol listesi:

- Oluşturulan `.md` dosyalarını Hugo sitenizin `content/` dizinine yerleştirin.  
- Kullanılan `Images` klasörünün `static/` altında olduğundan emin olun; böylece site bu varlıkları sunabilir.  
- `hugo server` komutunu çalıştırarak siteyi yerel olarak önizleyin; tüm linklerin doğru çözüldüğünü göreceksiniz.  

Daha gelişmiş dönüşümler (özel stillerin korunması, tabloların HTML'e dönüştürülmesi vb.) için `MarkdownSaveOptions` üzerindeki diğer özelliklere göz atın.

---

## Sonuç

**Bağlantıları dışa aktarma** yöntemini ele aldık, **docx'i markdown'a dönüştür** için temiz bir yol gösterdik ve Aspose.Words for .NET kullanarak **save word as markdown** işlemini adım adım gösterdik. Sadece üç satır kodla **word'den markdown oluştur**abilir, hiperlinklerinizi bozulmadan tutabilir ve sonucu modern dokümantasyon akışınıza entegre edebilirsiniz. Kendi raporlarınızda deneyin, `LinkExportMode`'u ihtiyacınıza göre ayarlayın; Word'den Markdown'a geçişin ne kadar sorunsuz olabileceğini göreceksiniz. Bir öneriniz mi var? Yorum bırakın, iyi kodlamalar!

---

![bağlantıları dışa aktarma örneği]()

*Image alt text contains the primary keyword for SEO.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}