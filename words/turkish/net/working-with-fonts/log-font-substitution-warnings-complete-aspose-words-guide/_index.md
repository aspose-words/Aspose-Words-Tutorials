---
category: general
date: 2026-01-14
description: Aspose.Words ile Word belgelerini yüklerken yazı tipi ikame uyarılarını
  günlüğe kaydedin. Eksik yazı tiplerini nasıl tespit edeceğinizi ve C#'ta eksik yazı
  tiplerini nasıl yakalayacağınızı öğrenin.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: tr
og_description: Aspose.Words ile Word belgelerini yüklerken yazı tipi ikame uyarılarını
  günlüğe kaydedin. Eksik yazı tiplerini nasıl tespit edeceğinizi ve C#’ta eksik yazı
  tiplerini yakalayacağınızı keşfedin.
og_title: Yazı Tipi Değiştirme Uyarılarını Günlüğe Kaydet – Aspose.Words Tam Kılavuzu
tags:
- Aspose.Words
- C#
- Document Processing
title: Yazı Tipi Değişimi Uyarılarını Günlüğe Kaydet – Aspose.Words Tam Rehberi
url: /tr/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yazı Tipi Değiştirme Uyarılarını Günlüğe Kaydetme – Aspose.Words Tam Kılavuzu

Yazı tipi değiştirme uyarılarını günlüğe kaydetmek, bir Word belgesinin Aspose.Words tarafından yüklendikten sonra tam olarak aynı göründüğünden emin olmanız gerektiğinde çok önemlidir. **Eksik yazı tiplerini tespit etme** ya da **eksik yazı tiplerini yakalama** hakkında merak ettiyseniz, doğru yerdesiniz.  

Bu öğreticide gerçek bir senaryoyu adım adım inceleyecek, tam C# kodunu gösterecek ve her satırın neden önemli olduğunu açıklayacağız. Sonunda her yazı tipi değiştirme olayını günlüğe kaydedebilecek ve buna göre hareket edebileceksiniz—artık gizemli uyarılar kalmayacak.

![Yazı tipi değiştirme uyarıları örneği](/images/font-warnings.png "Konsol çıktısını gösteren ekran görüntüsü: yazı tipi değiştirme uyarıları")

## Öğrenecekleriniz

- Aspose.Words'in yazı tipi değiştirme için tipli uyarılar üretmesi için `LoadOptions` nasıl yapılandırılır.  
- Belge yüklenirken **eksik yazı tiplerini tespit** etmek için tam adımlar.  
- **Eksik yazı tiplerini yakalamanın** temiz bir yolu ve bunları kendi günlüğünüze ya da izleme sisteminize yazmak.  
- Köşe durumları yönetimi (ör. bir belgenin sunucuda yüklü olmayan bir yazı tipi içermesi).  

### Önkoşullar

- .NET 6.0 veya üzeri (kod .NET Framework 4.6+ ile de çalışır).  
- Geçerli bir Aspose.Words for .NET lisansı (veya ücretsiz deneme).  
- C# ve konsol uygulamalarıyla temel aşinalık.  

Eğer bunlara sahipseniz, başlayalım.

## Adım 1 – Tipli Uyarılar Üretmek İçin LoadOptions'ı Ayarlama

Çözümün kalbi `LoadOptions.FontSubstitutionWarning` içinde yatar. Bunu `RaiseTypedWarnings` olarak değiştirerek Aspose.Words'e istediğiniz tam yazı tipini bulamadığında **her seferinde** bir olay tetiklemesini söylersiniz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Neden bu önemli:**  
> Varsayılan davranış, eksik bir yazı tipini sessizce en yakın eşleşmeyle değiştirir ve bu, farkına varmadığınız düzen hatalarına yol açabilir. Tipli uyarılar üretmek size tam görünürlük sağlar.

## Adım 2 – Uyarı Olayına Abone Olma

Şimdi `loadOptions.FontSubstitutionWarning`'a bağlanıyoruz. Lambda, eksik olan yazı tipini ve yerine kullanılanı tam olarak belirten bir `e` nesnesi alır.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Pro ipucu:** Bunu bir web sunucusunda çalıştırıyorsanız, `Console.WriteLine`'ı yapılandırılmış bir logger (Serilog, NLog vb.) ile değiştirin, böylece verileri daha sonra sorgulayabilirsiniz.

## Adım 3 – Belgeyi Yapılandırılmış Seçeneklerle Yükleme

Uyarı mekanizması kurulduğunda, belgeyi normal yaptığınız gibi basitçe yükleyin. Olay, her eksik yazı tipi için otomatik olarak tetiklenir.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Beklenen Konsol Çıktısı

`input.docx` bir *MyFancyFont* adlı yazı tipine referans veriyorsa ve bu yüklü değilse, şunu göreceksiniz:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Her satır bir **eksik yazı tiplerini tespit** olayına karşılık gelir ve size tam bir denetim izi sağlar.

## Adım 4 – Köşe Durumları ve İleri Senaryoları Ele Alma

### 4.1 Değiştirme Olmadığında

Bazen bir belge yalnızca zaten mevcut olan sistem yazı tiplerini kullanır. Bu durumda uyarı olayı hiç tetiklenmez ve çıktısız temiz bir konsol alırsınız. Bu iyi bir işarettir—ortamınızda zaten tüm gerekli yazı tipleri bulunuyor.

### 4.2 Uyarıların Daha Sonra Analiz İçin Yakalanması

Uyarıları gece raporu için saklamanız gerekiyorsa, bir listede toplayın:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Yükleme sonrası, `missingFonts`'ı JSON'a serileştirebilir, bir veritabanına yazabilir ya da bir özet e-posta gönderebilirsiniz.

### 4.3 PDF'ler veya Diğer Formatlarla Çalışma

Aynı `LoadOptions` yaklaşımı PDF, RTF ve hatta HTML dosyalarındaki `Load` çağrıları için de çalışır. Aynı seçenek örneğini geçin ve Aspose.Words eşleşemediği herhangi bir yazı tipi için uyarı üretir.

## Adım 5 – Sonucu Programatik Olarak Doğrulama

Konsola bakmak yerine otomatik bir test tercih ediyorsanız, listenin beklenen girdileri içerdiğini doğrulayın:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Bu kod parçacığı, **eksik yazı tiplerini nasıl yakalayacağınızı** sadece loglarda değil, kod içinde de gösterir.

## Yaygın Tuzaklar ve Nasıl Kaçınılır

| Tuzak | Neden Olur | Çözüm |
|-------|------------|-------|
| `RaiseTypedWarnings` ayarlamayı unutmak | Varsayılan `DoNotRaise` olduğundan hiçbir olay tetiklenmez. | Adım 1'de gösterildiği gibi `FontSubstitutionWarning`'ı açıkça ayarlayın. |
| Web uygulamasında `Console.WriteLine` kullanmak | Konsol çıktısı IIS/ASP.NET Core'da kaybolur. | Kalıcı bir logger'a geçin (örn., Serilog). |
| Belgeyi göreceli bir yol ile yüklemek | Çalışma dizini çalışma zamanında farklı olabilir. | Mutlak yollar kullanın veya `Path.Combine(AppContext.BaseDirectory, "input.docx")` kullanın. |
| `SubstitutedFontName`'i görmezden gelmek | Hangi yedek yazı tipinin seçildiği bilgisini kaybedersiniz. | Her zaman hem `FontName` hem de `SubstitutedFontName`'i günlüğe kaydedin. |

## Bonus: Yazı Tipi Kurulumunu Otomatikleştirme

Dağıtım ortamını kontrol ediyorsanız, eksik yazı tiplerini bir PowerShell betiği ile önceden kurabilirsiniz:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Uygulamanız başlamadan bunu çalıştırmak, çoğu **eksik yazı tiplerini tespit** uyarısını tamamen ortadan kaldırır.

## Sonuç

Aspose.Words ile Word belgelerini yüklerken **yazı tipi değiştirme uyarılarını günlüğe kaydetmek** için ihtiyacınız olan her şeyi ele aldık. `LoadOptions`'ı yapılandırarak, uyarı olayına abone olarak ve isteğe bağlı olarak sonuçları kalıcı hale getirerek, güvenilir bir şekilde **eksik yazı tiplerini tespit** edebilir ve herhangi bir .NET projesi için **eksik yazı tiplerini nasıl yakalayacağınızı** anlayabilirsiniz.

Kodu alın, logger'ı ortamınıza göre ayarlayın ve bir daha sessiz bir yazı tipi değişimiyle şaşırmayın. Sonraki adımlar şunları içerebilir:

- Uyarı listesini CI/CD hattınıza entegre ederek kritik yazı tipleri eksik olduğunda derlemeleri başarısız kılmak.  
- Bu yaklaşımı, bir dizi belge boyunca yazı tipi kullanımını izlemek için genişletmek.  
- Özel yedek yazı tipleri sağlamak için Aspose.Words’ `FontSettings` API'sini keşfetmek.

Sorularınız veya zor bir senaryonuz mu var? Bir yorum bırakın, birlikte sorun giderelim. İyi kodlamalar!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}