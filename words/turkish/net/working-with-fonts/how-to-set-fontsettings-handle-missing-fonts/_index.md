---
category: general
date: 2026-05-29
description: Aspose.Words'ta FontSettings'i nasıl ayarlayacağınızı ve eksik yazı tiplerini
  sorunsuz bir şekilde nasıl yöneteceğinizi öğrenin. Tam kod ve en iyi uygulamalarla
  adım adım rehber.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: tr
og_description: Aspose.Words'ta FontSettings nasıl ayarlanır ve eksik yazı tipleri
  hızlıca nasıl ele alınır. Tam ve çalıştırılabilir bir çözüm için bu rehberi izleyin.
og_title: FontSettings Nasıl Ayarlanır – Eksik Yazı Tiplerini Yönet
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: FontSettings Nasıl Ayarlanır – Eksik Yazı Tipleriyle Baş Etme
url: /tr/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# FontSettings Nasıl Ayarlanır – Eksik Yazı Tipleri Nasıl Ele Alınır

Aspose.Words ile çalışırken **FontSettings nasıl ayarlanır** diye hiç merak ettiniz mi ve aniden yüklü olmayan bir yazı tipine referans veren bir belgeyle karşılaştınız mı? Bu, özellikle sunucuda sadece sınırlı bir yazı tipi seti bulunan bir Linux konteynerinde istemci‑taraflı dosyalar işlenirken sıkça karşılaşılan bir sorundur. İyi haber? Bu boşlukları yakalayabilir ve **eksik yazı tiplerini** uygulamanızın çökmesi ya da çirkin PDF’ler üretmesi olmadan **ele alabilirsiniz**.

Bu öğreticide gerçek bir senaryoyu adım adım inceleyeceğiz: “Calibri” isteyen bir DOCX dosyasını, yalnızca “DejaVu Sans” içeren Linux konteynerinizde nasıl yükleyeceğinizi göreceksiniz. FontSettings’i nasıl yapılandıracağınızı, ikame uyarılarına nasıl abone olacağınızı ve yedek yazı tipleri sağlayarak belgenin yazarının istediği gibi render edilmesini nasıl sağlayacağınızı öğreneceksiniz. Gereksiz ayrıntı yok—bugün projenize ekleyebileceğiniz kod.

## Önkoşullar

- .NET 6.0 veya üzeri (API, .NET Framework 4.7+’de aynı şekilde çalışır)
- Aspose.Words for .NET 23.10 veya daha yeni (NuGet paket adı `Aspose.Words`)
- Temel bir C# geliştirme ortamı (Visual Studio, Rider veya VS Code)

Bu koşullara sahipseniz, başlayalım.

## Adım 1: FontSettings Oluşturun ve İkame Olaylarını Dinleyin

Çözümün kalbi `FontSettings` nesnesidir. `FontSubstitutionWarning` olayına bir işleyici ekleyerek Aspose.Words’un eksik bir yazı tipini değiştirmek zorunda kaldığı her anı canlı olarak raporlayabilirsiniz.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**Neden önemli:**  
Motor *Calibri* yazı tipini bulamadığında sessizce *Arial*’a düşebilir. Uyarıyı dinleyerek şeffaf bir denetim izi oluşturursunuz—hata ayıklama veya uyumluluk raporlaması için mükemmeldir.

> **İpucu:** Bu kodu bir CI sunucusunda çalıştırıyorsanız, çıktıyı bir log dosyasına yönlendirerek toplu çalıştırma sonrası hangi yazı tiplerinin eksik olduğunu gözden geçirebilirsiniz.

## Adım 2: FontSettings’i LoadOptions’a Bağlayın

`LoadOptions`, bir belgenin nasıl ayrıştırılacağını kontrol etmenin kapısıdır. Az önce yapılandırdığımız `FontSettings`’i atayarak, sonraki her `Document` yüklemesinin ikame mantığımızı dikkate almasını sağlarız.

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Arka planda ne oluyor?**  
`Document` yapıcısı çalışırken Aspose.Words DOCX’in XML’ini okur, yazı tipi referanslarını çözer ve bir yazı tipi bulunamazsa daha önce kurduğumuz uyarıyı tetikler. Bu kanca olmadan bir ikamenin gerçekleştiğini asla öğrenemezsiniz.

## Adım 3: Belgeyi Yükleyin ve (İsteğe Bağlı) Yedek Yazı Tipi Klasörünü Tanımlayın

Şimdi dosyayı belleğe alıyoruz. Eğer uygulamanızla birlikte gelen bir OpenType yazı tipi klasörünüz (ör. bir yedek font dizini) varsa, `FontSettings`’e bu klasörü söyleyin. Bu adım isteğe bağlıdır ancak genellikle *eksik yazı tiplerini* ele almanın en temiz yoludur.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**Köşe durum uyarısı:**  
Belge, ikame gerektirmeyen bir ikili akış olarak gömülü özel bir yazı tipi içeriyorsa, Aspose.Words bunu otomatik olarak kullanır. Uyarı yalnızca *eksik* sistem yazı tipleri için tetiklenir.

### Sonucu Doğrulama

Yüklemeden sonra belgeyi PDF ya da Word olarak kaydedip her şeyin doğru göründüğünden emin olabilirsiniz.

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

Programı çalıştırdığınızda konsol şu tür satırlar üretir:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

Bu mesajları görüyorsanız, **eksik yazı tiplerini** başarıyla **ele aldınız** ve hangi ikamelerin gerçekleştiğini tam olarak biliyorsunuz.

## Adım 4: İleri Seviye – Özel Yazı Tipi İkame Kuralları (İsteğe Bağlı)

Bazen deterministik bir eşleme gerekir; örneğin *Times New Roman* her zaman *Liberation Serif* ile değiştirilir. Bunu `FontSettings.SubstitutionTable` ile yapabilirsiniz.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**Neden uğraşmalı?**  
Açık kurallar tipografiye tam kontrol sağlar, özellikle pazarlama materyalleri üretirken marka tutarlılığını korur.

## Yaygın Tuzaklar ve Çözümleri

| Tuzak | Belirti | Çözüm |
|---------|---------|-----|
| **Uyarı çıktısı yok** | Yazı tiplerinin sorunsuz olduğunu düşünüyorsunuz ama belge hatalı görünüyor. | `FontSubstitutionWarning`’ı **belgeyi yüklemeden önce** eklediğinizden emin olun. |
| **Yedek klasör taranmıyor** | İkameler hâlâ sistem varsayılanlarına düşüyor. | `SetFontsFolder(path, true)` çağrısında ikinci argüman `true` olarak alt‑klasörleri taramayı etkinleştirin. |
| **Büyük partilerde performans düşüşü** | 10 000 belge yüklemek yavaşlıyor. | Tek bir `FontSettings` örneğini önbelleğe alın ve yüklemeler arasında yeniden kullanın; her seferinde yeni oluşturmayın. |
| **Gömülü yazı tipleri göz ardı ediliyor** | Özel gömülü bir yazı tipinin kullanılmasını bekliyorsunuz ama ikame gerçekleşiyor. | Kaynak DOCX’in gerçekten yazı tipini gömdüğünü doğrulayın (Word → Dosya → Bilgi → Yazı Tipleri). |

## Tam Çalışan Örnek

Aşağıda, olay işleme, ikame ayarları ve son PDF’nin kaydedilmesini kapsayan, kopyala‑yapıştır‑hazır bir program yer alıyor.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**Beklenen konsol çıktısı** (örnek):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

Programı çalıştırın, `Output.pdf` dosyasını açın; metnin yedek yazı tipleriyle render edildiğini göreceksiniz—eksik karakter kareleri, çökme yok.

## Sonuç

Artık Aspose.Words’ta **FontSettings nasıl ayarlanır** ve **eksik yazı tipleri nasıl zarifçe ele alınır** konusunda üretim‑hazır bir deseniniz var. `FontSubstitutionWarning` olayını bağlayarak, yedek bir yazı tipi dizini belirterek ve (gerekirse) açık ikame kuralları tanımlayarak, otomatik belge iş akışlarınızda tipografi üzerinde tam görünürlük ve kontrol elde edersiniz.

Sırada ne var? Marka‑özel tipografileriniz için özel bir yazı tipi koleksiyonu ekleyin ya da `FontSourceBase` API’sini keşfederek yazı tiplerini bir veritabanı ya da bulut depolamadan yükleyin. Aynı prensipler geçerli—tek yapmanız gereken `FontSettings` içine farklı bir kaynak takmak.

Sağ‑sol (RTL) betikler ya da emoji yazı tipleri gibi köşe durumlarıyla ilgili sorularınız mı var? Aşağıya yorum bırakın, mutlu kodlamalar!

## Bir Sonraki Öğrenmeniz Gerekenler

- [Aspose.Words’ta Yazı Tiplerini Yakalama – Tam Kılavuz](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [Aspose.Words’ta Yazı Tiplerini Algılama – Uyarılar ve Ayarlar](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [DOCX Yükleme ve Eksik Yazı Tiplerini Algılama – Tam C# Kılavuzu](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}