---
category: general
date: 2026-03-17
description: C#'ta Aspose.Words ve bir uyarı geri araması kullanarak yazı tiplerini
  nasıl tespit edebileceğinizi öğrenin. Belgeleri yüklerken eksik yazı tipi ikamelerini
  yakalamak için geri aramayı nasıl kullanacağınızı keşfedin.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: tr
og_description: C#'ta Aspose.Words kullanarak yazı tiplerini nasıl tespit edebileceğinizi
  öğrenin. Bu kılavuz, bir belge yüklenirken eksik yazı tipi uyarılarını yakalamak
  için geri aramayı (callback) nasıl kullanacağınızı gösterir.
og_title: C#'ta Yazı Tiplerini Nasıl Algılayabilirsiniz – Aspose.Words ile Geri Çağrı
  Kullanımı
tags:
- Aspose.Words
- C#
- Document Processing
title: C#'ta Yazı Tiplerini Nasıl Algılayabilirsiniz – Aspose.Words ile Geri Çağrı
  Kullanma
url: /tr/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta Yazı Tiplerini Nasıl Algılayabilirsiniz – Aspose.Words ile Geri Çağrı Kullanımı

Programlı olarak bir Word belgesinde **yazı tiplerini nasıl algılayacağınızı** hiç merak ettiniz mi ve dönüşüm sonrası bazı karakterlerin garip göründüğünü düşündünüz mü? Yalnız değilsiniz. Gerçek dünyadaki birçok projede—fatura oluşturucular, rapor dışa aktarıcıları veya toplu işleme hatları—eksik yazı tipleri, hata ayıklaması zor sessiz düzen bozukluklarına neden olur.  

İyi haber? Aspose.Words bu sorunları bir uyarı geri çağrısı ile ortaya çıkarmanın temiz bir yolunu sunar. Bu öğreticide **geri çağrının nasıl kullanılacağını** göreceksiniz; Aspose bir belgeyi yüklerken gerçekleştirdiği her yazı tipi ikamesini yakalayacak ve eksik yazı tiplerinin net bir raporunu yazdıran, çalıştırmaya hazır bir örnek elde edeceksiniz.

Şunları kapsayacağız:

* Minimum önkoşullar (.NET projesi ve Aspose.Words NuGet paketi).  
* `WarningType.FontSubstitution` için dinleme yapacak şekilde `IWarningCallback` nasıl uygulanır.  
* Geri çağrıyı `LoadOptions` içine nasıl bağlayıp bir belgeyi nasıl yüklersiniz.  
* Çıktının nasıl göründüğü ve üretim kodu için birkaç pratik ipucu.

Sonunda, herhangi bir DOCX, DOC veya RTF dosyasında **yazı tiplerini otomatik olarak algılayabilecek** ve eksik yazı tipi bilgisine göre hareket edebileceksiniz—ister günlük kaydı, ister kullanıcı uyarısı, ister yedek bir yazı tipi ikamesi.

![Aspose.Words uyarı geri çağrısı kullanarak bir Word belgesinde yazı tiplerini nasıl algılayabilirsiniz](https://example.com/images/detect-fonts.png "bir Word belgesinde yazı tiplerini nasıl algılayabilirsiniz")

## Gereksinimler

* **.NET 6.0** veya daha yeni (örnek .NET Framework 4.6+ ile de derlenir).  
* **Aspose.Words for .NET** – NuGet üzerinden kurun: `Install-Package Aspose.Words`.  
* Yüklü olmayan bir yazı tipine kasıtlı olarak referans veren örnek bir Word dosyası (ör. `MissingFont.docx`).  

Ek kütüphanelere gerek yok; her şey Aspose ad alanı içinde bulunur.

## Uyarı Geri Çağrısı ile Yazı Tiplerini Nasıl Algılayabilirsiniz

### Adım 1: Bir uyarı‑geri çağrı sınıfı oluşturun

Geri çağrı `IWarningCallback` arayüzünü uygular. Aspose.Words bulunamayan bir yazı tipiyle karşılaştığında, `WarningType.FontSubstitution` ile bir `WarningInfo` oluşturur. Sınıfımız sadece konsola dostça bir satır yazar.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Neden önemli:** `WarningType.FontSubstitution` üzerinden filtreleme yaparak gürültülü uyarılardan (ör. kullanımdan kaldırılmış özellikler) kaçınır ve günlüğü, makinede bulunmayan **yazı tiplerini algılamaya** odaklarız.

### Adım 2: Geri çağrıyı `LoadOptions` içine bağlayın

`LoadOptions` bir belgenin nasıl ayrıştırılacağını özelleştirmenizi sağlar. `FontWarningCollector` sınıfımızı `WarningCallback` özelliğine atamak, Aspose'a eksik bir yazı tipiyle karşılaşıldığında onu çağırmasını söyler.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**İpucu:** Burada programlı olarak bir yedek yazı tipi sağlamak isterseniz `LoadOptions.FontSettings` de ayarlayabilirsiniz. Bu, daha sonra bahsedeceğimiz gelişmiş bir senaryodur.

### Adım 3: Belgeyi yükleyin ve çıktıyı izleyin

Şimdi dosyayı gerçekten yüklüyoruz. Aspose belgeyi ayrıştırır ayrıştırmaz, bulamadığı her yazı tipi geri çağrımızı tetikler.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Beklenen konsol çıktısı** (belge *Comic Sans MS* yazı tipine referans veriyorsa ve bu yüklü değilse):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Belge birden fazla eksik yazı tipi içeriyorsa, her bir yazı tipi için bir satır göreceksiniz—tam da ihtiyacınız olan **yazı tiplerini nasıl algılayacağınız** bilgisi.

## Daha Karmaşık Senaryolar için Geri Çağrıyı Nasıl Kullanabilirsiniz

### Konsol yerine bir dosyaya günlük kaydı

Üretim ortamında muhtemelen kalıcı bir günlük istersiniz. `Console.WriteLine` yerine bir `StreamWriter` kullanın:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Daha Sonra Analiz İçin Uyarıları Toplamak

Bazen belge yüklendikten sonra eksik yazı tiplerinin listesini, belki bir UI iletişim kutusunda göstermek için ihtiyaç duyarsınız. Uyarıları bir `List<string>` içinde saklayın ve dışa aktarın:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Programlı Olarak Bir Yedek Yazı Tipi Sağlamak

Uygulamak istediğiniz bir kurumsal yazı tipiniz varsa, yüklemeden önce onu `FontSettings`'e ekleyebilirsiniz:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Şimdi Aspose eksik yazı tiplerini *Arial Unicode MS* ile ikame ederken, ikameyi geri çağrı aracılığıyla raporlamaya devam eder. Bu, **geri çağrının nasıl kullanılacağını** hem algılama hem de otomatik düzeltme için şık bir yoldur.

## Yaygın Tuzaklar ve Profesyonel İpuçları

| Tuzak | Neden Oluşur | Nasıl Önlenir |
|--------|----------------|--------------|
| **`Aspose.Words.Warnings` referansını eklemeyi unutmak** | `IWarningCallback` arayüzü orada bulunur. | En üstte `using Aspose.Words.Warnings;` ekleyin. |
| **`LoadOptions` olmadan bir belge yüklemek** | Varsayılan yükleyici, bildirim olmadan sessizce yazı tiplerini ikame eder. | Her zaman bir `LoadOptions` örneği oluşturun ve geri çağrınızı atayın. |
| **Sınırlı izinlere sahip bir sunucuda çalışmak** | Bir günlük dosyasına yazma `UnauthorizedAccessException` hatasına neden olabilir. | Yazılabilir bir klasör kullanın (ör. uygulamanın veri dizini) veya bellek içi koleksiyonları tercih edin. |
| **Birden fazla iş parçacığının aynı toplayıcıyı paylaşması** | `FontWarningCollector` varsayılan olarak iş parçacığı güvenli değildir. | Her iş parçacığı için ayrı bir toplayıcı oluşturun veya listeyi bir kilit ile koruyun. |
| **Geri çağrının gömülü yazı tipleri için tetiklendiğini varsaymak** | Gömülü yazı tipleri zaten belgede bulunur; uyarı oluşturulmaz. | Gömülü yazı tipi bütünlüğünü doğrulamanız gerekiyorsa, `FontSettings` aracılığıyla `FontInfo`'yu inceleyin. |

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Görmeniz gereken** (dosyanın iki eksik yazı tipine referans verdiğini varsayarsak):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Dosya yalnızca yüklü yazı tipleri kullanıyorsa, konsol sadece şunu yazdırır:

```
Document loaded successfully.

No missing fonts detected.
```

## Sonuç

Word belgesinde **yazı tiplerini nasıl algılayacağınızı** özel bir uyarı geri çağrısını Aspose.Words'e bağlayarak adım adım gösterdik. Yaklaşım hafif, gerektirdiği

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}