---
category: general
date: 2026-03-01
description: C#'ta FontSettings oluşturun, eksik yazı tiplerini tespit edin, yazı
  tipi mesajlarını yakalayın ve Aspose.Words ile eksik yazı tiplerini yönetin. Geliştiriciler
  için adım adım kılavuz.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: tr
og_description: C#'ta FontSettings oluşturun, eksik yazı tiplerini tespit edin, yazı
  tipi mesajlarını yakalayın ve Aspose.Words kullanarak eksik yazı tiplerini yönetin.
  Kodlu eksiksiz öğretici.
og_title: C#'ta FontSettings Oluşturun – Eksik Fontları Tespit Edin ve Font Mesajlarını
  Yakalayın
tags:
- Aspose.Words
- C#
- Font Management
title: C#'ta FontSettings Oluşturun – Eksik Yazı Tiplerini Algılayın ve Yazı Tipi
  Mesajlarını Yakalayın
url: /tr/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta FontSettings Oluşturma – Eksik Yazı Tiplerini Algıla ve Yazı Tipi Mesajlarını Yakala

Hiç **create FontSettings**'i bir .NET projesinde oluşturmanız gerektiğinde, hedef makinede yüklü olmayan yazı tiplerini nasıl tespit edeceğinizden emin olmadınız mı? Yalnız değilsiniz. Birçok gerçek‑dünya uygulamasında—otomatik rapor oluşturucularını veya belge dönüştürücülerini düşünün—eksik yazı tipleri sessizce düzeni bozabilir ve PDF garip göründüğünde bunu fark edersiniz.  

Eğer **detect missing fonts**, **capture font messages** ve **handle missing fonts** işlemlerini çıktınızı bozmasından önce yapabilseydiniz? İyi haber, Aspose.Words bunu çocuk oyuncağı haline getiriyor. Bu öğreticide, `FontSettings` nesnesini kurmaktan, hangi gliflerin değiştirildiğini tam olarak söyleyen bir uyarı geri çağrısı bağlamaya kadar tüm süreci adım adım göstereceğiz.

> **TL;DR:** Sonunda, her yazı tipi değişimini kaydeden, bir yedek ekleyip eklemeyeceğinize ya da kullanıcıyı bilgilendireceğinize karar vermenizi sağlayan, çalıştırmaya hazır bir C# konsol uygulamanız olacak.

## Önkoşullar

- .NET 6 SDK (veya herhangi bir yeni .NET sürümü)  
- Visual Studio 2022 veya VS Code, C# uzantılarıyla  
- Aspose.Words for .NET lisansı (ücretsiz deneme bu demo için çalışır)  
- Yüklü olmayan bir yazı tipine referans veren örnek bir DOCX (ör. Linux kutusunda *Comic Sans MS*).

`Aspose.Words` dışındaki özel bir NuGet paketi gerekmez.

## Adım 1 – Aspose.Words'ı Yükleyin ve Projeyi Kurun

İlk olarak, yeni bir konsol projesi oluşturun ve Aspose.Words kütüphanesini projeye ekleyin.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro ipucu:** Zaten bir çözümünüz varsa, paketi NuGet Package Manager UI üzerinden ekleyin—sürüm takibini kolaylaştırır.

## Adım 2 – FontSettings Oluşturma (Ana Anahtar Kelime Burada Görünür)

**create FontSettings** adımı, herhangi bir yazı tipiyle ilgili iş akışının temel taşıdır. `FontSettings`, Aspose.Words'a yazı tiplerini nerede arayacağını, sistem klasörlerini kullanıp kullanmayacağını ve bir şey eksik olduğunda nasıl geri dönüş yapılacağını söyler.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Bu neden önemli? Uygun şekilde yapılandırılmış bir `FontSettings` olmadan, motor eksik glifleri varsayılan sistem yazı tipiyle sessizce değiştirir ve hiçbir uyarı görmezsiniz.

## Adım 3 – LoadOptions'ı FontSettings ile Bağlayın

`LoadOptions`, `FontSettings`'i belge yükleyicisine geçirmenizi sağlar. Bu, motorun `Document` oluşturma aşamasında **detect missing fonts** yapmasını sağlayan köprüdür.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Artık `loadOptions` ile bir DOCX yüklediğinizde, Aspose.Words daha önce yapılandırdığımız `FontSettings`'i kullanacaktır.

## Adım 4 – **Capture Font Messages** için Bir Uyarı Geri Çağrısı Ekleyin

Aspose.Words, çeşitli koşullar için uyarılar üretir—yazı tipi değişimi yaygın bir örnektir. `IWarningCallback`'in bir uygulamasını sağlayarak, **capture font messages**'ı gerçek zamanlı olarak yakalayabilirsiniz.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### Uyarı İşleyici Sınıfı

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

`info.Description` alanı, *“Font 'Comic Sans MS' bulunamadı. 'Arial' ile değiştirildi.”* gibi insan tarafından okunabilir bir mesaj içerir. Bu, **handle missing fonts** işlemini zarif bir şekilde yapmanız için tam olarak ihtiyaç duyduğunuz çıktıdır.

## Adım 5 – Belgeyi Yükleyin ve Geri Çağrının İşini Yapmasına İzin Verin

Her şey bağlandığında, belgeyi yüklemek basittir. Kaynak dosya sistemde bulunmayan bir yazı tipine referans veriyorsa, uyarı işleyicimiz tetiklenecektir.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

Programı çalıştırdığınızda, aşağıdaki gibi bir konsol çıktısı göreceksiniz:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Bu çıktı, iş akışımızın **capture font messages** kısmıdır. İşleyiciyi bir dosyaya kaydetmek, telemetri göndermek ya da kritik yazı tipleri eksikse dönüşümü iptal etmek için genişletebilirsiniz.

## Adım 6 – Tam Çalışan Örnek (Tüm Parçalar Bir Arada)

Aşağıda, tamamen kopyala‑yapıştır hazır bir program bulunmaktadır. `Program.cs` dosyasına yapıştırın, dosya yollarını ayarlayın ve `dotnet run` komutunu çalıştırın.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Beklenen Çıktı

*Comic Sans MS*'i olmayan bir makinede programı çalıştırmak, aşağıdaki gibi bir şey yazdıracaktır:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

Ayrıca, değiştirilen yazı tiplerini kullanan `Result.pdf` dosyasına da sahip olacaksınız; bu, dönüşümün asla çökmesini engeller.

## Sık Sorulan Sorular & Kenar Durumları

| Question | Answer |
|----------|--------|
| **Dönüşümün değişim yerine başarısız olmasını istersem ne olur?** | `FontSubstitutionWarningHandler` içinde, `info.Description` kritik bir yazı tipi adı içerdiğinde bir istisna fırlatın. |
| **Yerine bir yazı tipini otomatik olarak gömebilir miyim?** | Evet. Eksik bir yazı tipi tespit edildikten sonra, bilinen bir yoldan bir yedek `FontInfo` yükleyebilir ve `fontSettings.SetFontsFolder` aracılığıyla `fontSettings`'e ekleyebilirsiniz. |
| **Bu Linux/macOS'ta çalışır mı?** | Kesinlikle. `FontSettings` çapraz platform çalışır; sadece yedek klasörün uygun `.ttf` veya `.otf` dosyalarını içerdiğinden emin olun. |
| **Uyarı geri çağrısı thread‑safe mi?** | Geri çağrı, belgeyi yükleyen aynı thread üzerinde çalışır, bu yüzden konsol kaydı için ek senkronizasyona gerek yoktur. Çok‑thread'li senaryolarda, paylaşılan kaynakları koruyun. |
| **Uyarıları bir dosyaya nasıl kaydederim?** | `Console.WriteLine`'ı `File.AppendAllText("font_warnings.log", ...)` ile değiştirin veya herhangi bir kayıt çerçevesi (Serilog, NLog) kullanın. |

## Üretim‑Hazır Yazı Tipi Yönetimi için Pro İpuçları

1. **Cache Font Lookups** – Aynı `FontSettings` örneğini birden fazla belge yüklemede yeniden kullanmak, dosya sistemi taramalarını tekrarlamaktan kaçınır.  
2. **Whitelist Critical Fonts** – Markanız belirli bir yazı tipine ihtiyaç duyuyorsa, varlığını erken doğrulayın ve net bir hata mesajıyla iptal edin.  
3. **Use `SetFontFolder` Recursively** – `recursive: true` ayarı, alt klasörlerin taranmasını sağlar; bu, tüm bir yazı tipi koleksiyonunu gönderdiğinizde kullanışlıdır.  
4. **Combine with `FontSubstitutionSettings`** – Değişim kurallarını ince ayar yapabilirsiniz (ör. aynı aile adına sahip yazı tiplerini tercih edin).  

## Sonuç

Şimdi **created FontSettings**'i oluşturduk, `LoadOptions`'ı **detect missing fonts** yapacak şekilde yapılandırdık, **captures font messages** yapan bir geri çağrı ekledik ve **handle missing fonts**'i temiz, üretim‑hazır bir şekilde nasıl yapacağınızı gösterdik. Tüm akış, birkaç düzine C# satırına sığar, ancak işlediğiniz herhangi bir DOCX'in yazı tipi ortamı hakkında tam görünürlük sağlar.

Sonra, aşağıdakileri keşfedebilirsiniz:

- **Embedding fallback fonts**'i doğrudan çıktı PDF'ye (`PdfSaveOptions.FontEmbeddingMode`) gömebilirsiniz.  
- **Programmatically substituting fonts**'i kurumsal marka kurallarına göre yapabilirsiniz.  
- **Integrating with a CI pipeline**'ı, yetkisiz yazı tipleri kullanan belgeleri otomatik olarak işaretlemek için entegre edebilirsiniz.

Deneyin, uyarı işleyicisini ihtiyaçlarınıza göre ayarlayın ve belge hatlarınızın güvenle çalışmasını sağlayın—görünmez yazı tipi değişimleri nedeniyle ortaya çıkan gizemli düzen hatalarına son.

İyi kodlamalar! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}