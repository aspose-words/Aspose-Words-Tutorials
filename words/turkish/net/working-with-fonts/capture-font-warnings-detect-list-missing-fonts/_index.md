---
category: general
date: 2025-12-31
description: Aspose.Words'ta yazı tipi uyarılarını yakalayarak eksik yazı tiplerini
  tespit edin ve .NET uygulamanızda eksik yazı tiplerini listeleyin. Adım adım bir
  C# çözümünü öğrenin.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: tr
og_description: Aspose.Words'ta yazı tipi uyarılarını yakalayarak eksik yazı tiplerini
  tespit edin ve eksik yazı tiplerini listeleyin. Kod ve ipuçlarıyla tam C# rehberi.
og_title: Yazı Tipi Uyarılarını Yakala – Eksik Yazı Tiplerini Tespit Et ve Listele
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Yazı Tipi Uyarılarını Yakala – Eksik Yazı Tiplerini Algıla ve Listele
url: /tr/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Font Uyarılarını Yakalama – Eksik Fontları Algıla ve Listele

Bir Word belgesi yüklerken **font uyarılarını yakalamanız** gerektiğinde, eksik‑font ayrıntılarını nasıl ortaya çıkaracağınızı bilemediniz mi? Yalnız değilsiniz. Gerçek‑dünya projelerinde eksik fontlar düzen bozulmalarına yol açar ve uygun uyarılar olmadan hayalet hataların peşine düşersiniz.  

Bu öğreticide **eksik fontları algılamayı** ve **eksik fontları listelemeyi** Aspose.Words for .NET kullanarak göstereceğiz. Sonunda, her bir ikame uyarısını yazdıran, çalıştırmaya hazır bir C# kod parçacığına sahip olacaksınız; böylece uyarıları kaydedebilir, alarm verebilir veya fontları otomatik olarak bile değiştirebilirsiniz.

---

## Font Uyarılarını Yakalamanın Önemi

Aspose.Words bir DOCX dosyasını açtığında, sunucuda yüklü olmayan bir fonta referans verildiğinde sessizce bir yedek font ikame eder. Belge düzgün görünür, ancak görsel bütünlük bozulur—örneğin bir kurumsal marka logosu yanlış tipografiyle gösterilir.  

Bu uyarıları yakalamak şunları sağlar:

* **Marka tutarlılığını koruma** – hangi fontların eksik olduğunu tam olarak bilirsiniz.  
* **Otomatik düzeltme** – eksik fontları programatik olarak değiştirebilirsiniz.  
* **Uyumluluk denetimi** – yasal veya tasarım incelemeleri için raporlar oluşturabilirsiniz.  

Kısacası, **font uyarılarını yakalama**, sessiz font ikamesine karşı ilk savunma hattıdır.

---

## Eksik Fontları Algılamak İçin LoadOptions Ayarlama

Uyarıları ortaya çıkarmanın anahtarı `LoadOptions.FontSubstitutionWarning` özelliğidir. Varsayılan olarak `None` ayarlanmıştır; bu da Aspose.Words mesajları yutar. Bunu `All` olarak değiştirmek, kütüphanenin her ikame olayını kaydetmesini sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Pro ipucu:** Zaten özel bir font klasörünüz varsa, belgeyi yüklemeden önce `FontSettings.SetFontsFolder("path")` ile atayın. Böylece sistem dizininde bulunmayan **eksik fontları algılayabilirsiniz**.

---

## Belgeyi Yükleyin ve Eksik Fontları Listeleyin

`LoadOptions` hazır olduğuna göre, bir sonraki adım Word dosyasını yüklemektir. Yapıcı (constructor) seçenek nesnesini kabul eder ve herhangi bir ikame, belgenin `WarningInfoCollection` içinde kaydedilir.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Dosya, mevcut olmayan fontlara referans veriyorsa, her eksik font bir `WarningInfo` girdisi oluşturur. Bu koleksiyonu döngüyle gezerek **eksik fontları listeleyebilirsiniz**.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Tipik çıktı şu şekildedir:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Her satır, eksik olan fontu tam olarak bildirir ve **eksik fontları listeleme** gereksinimini karşılar.

---

## WarningInfoCollection’ı Okuma ve Yorumlama

`WarningInfoCollection` farklı uyarı türleri içerebilir (ör. `DocumentStructure`, `ImageLoading`). Sadece font sorunlarına odaklanmak için `WarningType.FontSubstitution` ile filtreleyin.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Neden filtreleyelim? Büyük bir belge, bozuk görseller veya desteklenmeyen özellikler hakkında da uyarılar üretebilir. Koleksiyonu daraltarak gürültüyü önler ve **font uyarılarını yakalama** çıktısını temiz tutarsınız.

---

## Tam Çalışan Örnek – Font Uyarılarını Yakalama

Aşağıda, herhangi bir .NET konsol projesine ekleyebileceğiniz, tamamen bağımsız bir program yer alıyor. `LoadOptions` yapılandırmasından eksik fontların düzenli bir listesini yazdırmaya kadar tüm adımları gösterir.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Beklenen konsol çıktısı**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Belgede eksik font yoksa şunu görürsünüz:

```
All referenced fonts are available – no warnings captured.
```

---

## Yaygın Kenar Durumları ve Çözüm Önerileri

| Durum | Neden Oluşur | Önerilen Çözüm |
|-----------|----------------|-----------------|
| **Belge gömülü bir OpenType font kullanıyor** | Aspose.Words gömülü fontları okuyabilir, ancak dosya bozuk değilse. | Önce DOCX’i Word’de kontrol edin; gerekirse fontu yeniden gömün. |
| **Uyarıların sayısı çok fazla** (ör. 200+ eksik font) | Eski sistemlerden gelen toplu ithalatlar geniş bir font paletine referans verir. | Uyarıları toplu işleyin: bir veritabanına kaydedin, ardından bir font‑kurulum betiği çalıştırın. |
| **WarningInfoCollection boş** | Ya belgede tüm fontlar mevcut, ya da `FontSubstitutionWarning` `None` olarak bırakılmış. | `LoadOptions` yapılandırmanızı tekrar kontrol edin ve doğru dosya yolunu yüklediğinizden emin olun. |
| **Özel fontlar bir ağ paylaşımında** | Ağ gecikmesi, font arama sırasında zaman aşımına neden olabilir. | Fontları `FontSettings` içine `SetFontsFolder` ile önceden yükleyin ve `CacheFontData = true` ayarlayın. |

Bu ipuçları, **eksik fontları algılamanızı** karmaşık ortamlarda bile güvenilir kılar.

---

## Görsel Açıklama

![capture font warnings example](https://example.com/images/capture-font-warnings.png "capture font warnings example")

*Ekran görüntüsü, iki eksik fontun raporlandığı bir konsol çalıştırmasını gösterir.*

---

## Sonraki Adımlar – Basit Raporlamanın Ötesine Geçmek

Artık **font uyarılarını yakalayabildiğinize** göre, iyileştirme otomasyonu düşünün:

1. **Otomatik Font İkamesi** – `FontSettings.SubstitutionSettings`i değiştirerek eksik fontları şirket onaylı bir yedekle değiştirin.  
2. **Bir İzleme Sistemine Günlükleme** – Uyarı mesajlarını Serilog, ELK veya Azure Application Insights’a yönlendirin.  
3. **Kullanıcı‑Odaklı Raporlar** – Tasarımcıların hangi fontların kurulması gerektiğini incelemesi için HTML veya PDF özetleri oluşturun.  

Tüm bu uzantılar, ele aldığımız temeller üzerine kuruludur: `LoadOptions` yapılandırması, belgeyi yükleme ve `WarningInfoCollection` okuma.

---

## Sonuç

Aspose.Words’ta **font uyarılarını yakalama**, **eksik fontları algılama** ve **eksik fontları listeleme** konularını, temiz bir konsol‑dostu çıktı ile öğrendiniz. Yaklaşım basit, sadece birkaç satır C# gerektirir ve Aspose.Words 23.x veya daha yeni bir .NET sürümüyle çalışır.  

Bilerek bir fontu kaldırdığınız bir DOCX üzerinde deneyin – uyarılar anında görünecek. Ardından eksik tipografileri kurmaya, programatik olarak ikame etmeye veya sadece daha sonra incelemek üzere kaydetmeye karar verebilirsiniz.

Kodlamanın tadını çıkarın, belgeleriniz her zaman doğru fontlarla görüntülensin!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}