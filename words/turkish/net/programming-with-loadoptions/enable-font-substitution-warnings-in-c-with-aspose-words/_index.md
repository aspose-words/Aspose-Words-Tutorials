---
category: general
date: 2026-06-20
description: Aspose.Words kullanarak C#'de yazı tipi ikame uyarılarını etkinleştirin.
  LoadOptions nasıl yapılandırılır, uyarılar nasıl yakalanır ve eksik yazı tipleri
  nasıl verimli bir şekilde işlenir öğrenin.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: tr
og_description: C#'ta Aspose.Words ile yazı tipi ikame uyarılarını etkinleştirin.
  Bu kılavuz, LoadOptions'ı nasıl ayarlayacağınızı, WarningInfo'ı nasıl okuyacağınızı
  ve eksik yazı tipi mesajlarını nasıl görüntüleyeceğinizi gösterir.
og_title: C#'de Yazı Tipi Değiştirme Uyarılarını Etkinleştirme – Tam Rehber
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Aspose.Words ile C#'ta Yazı Tipi Değiştirme Uyarılarını Etkinleştirin
url: /tr/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Aspose.Words'de Yazı Tipi Değiştirme Uyarılarını Etkinleştirme

Sunucuda yüklü olmayan bir yazı tipine başvuran bir Word belgesiyle karşılaştığınızda **yazı tipi değiştirme uyarılarını etkinleştirme** konusunda hiç merak ettiniz mi? Tek başınıza değilsiniz. Eksik yazı tipleri, oluşturulan PDF'lerin veya görüntülerin düzenini sessizce bozabilir ve bunu erken yakalamanın tek yolu, Aspose.Words'ün yaydığı uyarıları dinlemektir.

Bu öğreticide, bu uyarıları nasıl açacağınızı, `WarningInfo` koleksiyonundan nasıl çekeceğinizi ve anlamlı mesajları konsola nasıl yazdıracağınızı gösteren uygulamalı bir örnek üzerinden ilerleyeceğiz. Sonuna kadar **Aspose.Words LoadOptions**'ı nasıl yapılandıracağınızı, **C# yazı tipi değiştirme uyarılarını** nasıl ele alacağınızı ve belge‑işleme hattınızı sorunsuz tutacağınızı öğreneceksiniz.

Ayrıca birkaç uç durumdan da bahsedeceğiz—uyarıları bastırırsanız ne olur, ya da uyarıları yazdırmak yerine kaydetmeniz gerekirse ne yapmalısınız—ve en son Aspose.Words for .NET sürümü (24.10 itibarıyla) ile çalışan, tamamen kopyala‑yapıştır hazır bir kod örneği sunacağız.

## Gereksinimler

- .NET 6.0 veya üzeri (kod .NET Framework 4.7+ üzerinde de çalışır)
- `Aspose.Words` için bir NuGet referansı ( `dotnet add package Aspose.Words` komutuyla kurun)
- Yüklü olmayan bir yazı tipine başvuran bir Word dosyası (ör. `DocumentWithMissingFont.docx`)
- İyi bir IDE (Visual Studio, Rider veya VS Code)

Hepsi bu kadar—ekstra hizmet yok, özel araçlar yok. Hazır mısınız? Hadi başlayalım.

## Adım 1: Yazı Tipi Değiştirme Uyarılarını Etkinleştirme

İlk yapmanız gereken, Aspose.Words'e eksik bir yazı tipini değiştirdiğinde bildirim almak istediğinizi söylemektir. Bu, bir `LoadOptions` nesnesinin `FontSettings` özelliği aracılığıyla yapılır. Varsayılan olarak, API'nin sessiz kalması için uyarılar **devre dışı** bırakılmıştır, bu yüzden anahtarı kendimiz açmamız gerekir.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Neden bu çalışıyor:** `FontSettings` `null` olmadığında, kütüphane bir belgeyi yüklerken karşılaştığı tüm `WarningType.FontSubstitution` girişleriyle `Document.WarningInfo`'yu otomatik olarak doldurur. Bunu, yazı tipleri için bir “debug‑modu” açmak gibi düşünün.

## Adım 2: Belgeyi Yapılandırılmış Seçeneklerle Yükleme

Uyarı koleksiyonu artık aktif olduğuna göre, az önce hazırladığımız `LoadOptions` ile belgenizi yükleyin. Belge eksik bir yazı tipi içeriyorsa, Aspose.Words bir yedek yazı tipi kullanacak ve `WarningInfo` listesine bir uyarı ekleyecektir.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Pro ipucu:** Bir döngüde birçok dosya işliyorsanız, aynı `LoadOptions` örneğini yeniden kullanın—bir kez oluşturmak yineleme başına birkaç milisaniye tasarruf sağlar.

## Adım 3: WarningInfo Üzerinde Döngü Yaparak Yazı Tipi Değiştirme Mesajlarını Gösterme

Belge yüklendikten sonra, `WarningInfo` koleksiyonu yükleme sırasında oluşan tüm uyarıları tutar. Biz sadece `WarningType.FontSubstitution` ile ilgileniyoruz, bu yüzden buna göre filtreleme yapıyoruz.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Yukarıdaki kod parçacığını eksik “Papyrus” yazı tipine başvuran bir belgeye çalıştırdığınızda aşağıdaki gibi bir çıktı alabilirsiniz:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

Aradığınız **yazı tipi değiştirme mesajları** budur—net, eyleme geçirilebilir ve kaydedilmeye ya da bir uyarı sistemine gönderilmeye hazır.

## Tam Çalışan Örnek

Aşağıda her şeyi bir araya getiren bağımsız bir konsol programı bulunuyor. Yeni bir `.csproj` dosyasına kopyala‑yapıştır yapın ve **Run** tuşuna basın.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Beklenen Çıktı

Belge yüklü olmayan yazı tiplerine başvuruyorsa, aşağıdakine benzer bir şey göreceksiniz:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Eğer makinede tüm yazı tipleri yüklüyse, program sadece şunu yazdıracaktır:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Yaygın Tuzaklar ve Pro İpuçları

| Sorun | Neden Oluşur | Nasıl Düzeltir / Önlenir |
|-------|----------------|--------------------|
| **Uyarılar kaybolur** | `FontSettings`'i temizlediniz veya `LoadOptions`'ı bunu içermeden kullandınız. | Özellikleri değiştirmeseniz bile her zaman `FontSettings` örneği oluşturun. |
| **Çok fazla uyarı** | Belge birçok egzotik yazı tipi kullanıyor. | Değiştirmeleri azaltmak için `FontSettings`'e `SetFontsFolder` ile özel bir yazı tipi klasörü eklemeyi düşünün. |
| **Sıkı bir döngüde performans düşüşü** | Her yinelemede `LoadOptions` yeniden oluşturulması ek yük getirir. | Tüm belgeler için tek bir `LoadOptions` örneğini yeniden kullanın. |
| **Konsol çıktısı eksik** | `Console.WriteLine`'ın göz ardı edildiği bir GUI uygulamasında çalıştırılıyor. | Uyarıları bir logger'a (`ILogger`) yönlendirin veya bir dosyaya yazın. |

### Gerçek Dünya Servisinde Uyarıların İşlenmesi

Bir web API'sinde muhtemelen konsola yazmak istemezsiniz. Bunun yerine, uyarıları yapılandırılmış bir loga yönlendirin:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

Bu şekilde **belge uyarı yönetimini** korurken servisinizi temiz tutarsınız.

## Örneği Genişletme

- **Diğer uyarı türlerini yakalayın** (ör. `WarningType.UnknownFileFormat`) `if` filtresini kaldırarak.
- Tüm uyarıların bir raporunu JSON olarak kaydedin, sonraki analizler için.
- `FontSettings.SubstitutionSettings.DefaultFontName` ayarlayarak belirli bir yedek yazı tipini zorlayın.

Bunların hepsi, **yazı tipi değiştirme uyarılarını etkinleştirme** konusunda uzmanlaştıktan sonra doğal uzantılardır.

## Sonuç

Aspose.Words kullanarak C#'ta **yazı tipi değiştirme uyarılarını etkinleştirme** yöntemini, `LoadOptions` yapılandırmasından `WarningInfo` üzerinden döngü yapıp dostça mesajlar yazdırmaya kadar gösterdik. Yukarıdaki adımları izleyerek eksik yazı tiplerinden kaynaklanan sessiz düzen değişikliklerine karşı belge‑işleme hatlarınızı koruyabilirsiniz.

Sonra, özel bir yazı tipi klasörü eklemeyi, uyarıları bir dosyaya kaydetmeyi ya da bir izleme panosuna göndermeyi deneyin. Aynı desen, PDF'ye dönüştürme, görüntü oluşturma veya birleştirme (mail‑merge) yaparken **belge uyarı yönetimi** senaryolarının tümünde çalışır.

**C# yazı tipi değiştirme uyarıları** hakkında sorularınız mı var ya da akıllı bir çözüm paylaşmak mı istiyorsunuz? Aşağıya bir yorum bırakın—iyi kodlamalar!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words'de Yazı Tipi Değiştirme Uyarılarını Etkinleştirme – Tam Kılavuz](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Aspose.Words'de Yazı Tiplerini Nasıl Algılayabilirsiniz – Uyarıları ve Ayarları Yönetme](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Java'da Aspose.Words ile Yazı Tipi Değiştirme Uyarılarını Yakalama – Tam Kılavuz](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}