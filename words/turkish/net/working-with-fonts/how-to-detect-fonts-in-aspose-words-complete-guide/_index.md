---
category: general
date: 2026-04-07
description: Aspose.Words kullanarak C#'de eksik yazı tiplerini işlerken yazı tiplerini
  nasıl tespit edeceğinizi ve uyarıları nasıl yakalayacağınızı öğrenin. Adım adım
  kod dahil.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: tr
og_description: Aspose.Words'ta yazı tiplerini nasıl tespit edersiniz? Uyarıları yakalamak
  ve eksik yazı tiplerini zahmetsizce yönetmek için bu öğreticiyi izleyin.
og_title: Aspose.Words'ta Yazı Tiplerini Nasıl Algılayabilirsiniz – Tam Kılavuz
tags:
- Aspose.Words
- C#
- Font handling
title: Aspose.Words'ta Yazı Tiplerini Nasıl Algılayabilirsiniz – Tam Kılavuz
url: /tr/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words'te Yazı Tiplerini Nasıl Algılayabilirsiniz – Tam Kılavuz

Bir Word belgesinde eksik **yazı tiplerini** üretime göndermeden önce tespit etmeyi hiç merak ettiniz mi? Tek başınıza değilsiniz. Birçok kurumsal senaryoda istenmeyen bir yazı tipi, PDF dönüşüm hattını bozabilir veya profesyonel olmayan bir görünüm oluşturan yerleşim hatalarına neden olabilir. İyi haber şu ki Aspose.Words, bu eksik tipografileri tespit etmenizi ve net uyarılar göstermenizi sağlayan yerleşik bir yöntem sunar.

Bu öğreticide **yazı tiplerini nasıl algılayacağınızı**, **uyarıları nasıl yakalayacağınızı** ve **eksik yazı tiplerini nasıl ele alacağınızı** adım adım gösterecek, uygulamanızın dayanıklı kalmasını sağlayacağız. Harici araçlar, tahmin yürütme yok—şu anda projenize ekleyebileceğiniz saf C# kodu.

> **Hızlı ön izleme:** Sonunda, belge yükleme sırasında ortaya çıkan tüm yazı tipi değiştirme mesajlarını toplayan yeniden kullanılabilir bir `FontSubstitutionWarningCollector`'a sahip olacaksınız ve bir yazı tipi bulunamadığında nasıl tepki vereceğinizi öğreneceksiniz.

---

## Öğrenecekleriniz

- `LoadOptions`'ı yazı tipi‑değiştirme uyarılarını dinleyecek şekilde nasıl yapılandıracağınız.  
- Bu uyarıları özel bir toplayıcı sınıfında nasıl yakalayacağınız.  
- Toplanan uyarıları işleyip, iptal edip, kaydedip ya da yazı tiplerini değiştirme kararını nasıl vereceğiniz.  
- Uzaktan veya gömülü yazı tiplerine referans veren belgeler için kenar‑durum yönetimi.  

**Önkoşullar:** .NET 6+ (veya .NET Framework 4.6+), Aspose.Words for .NET (en son sürüm) ve temel C# bilgisi. Aspose.Words ile hiç çalışmadıysanız endişelenmeyin—bu kılavuz sadece birkaç dakikalık kurulum süresi gerektirir.

---

## Aspose.Words LoadOptions Kullanarak Yazı Tiplerini Algılamak

Eksik yazı tiplerini algılamanın ilk adımı, Aspose.Words’a bunları raporlamasını söylemektir. Bu, `LoadOptions.WarningCallback` özelliği aracılığıyla yapılır; bu özellik `IWarningCallback` arayüzünü uygulayan herhangi bir sınıfı kabul eder. Aşağıda, her uyarıyı daha sonra incelemek üzere saklayan küçük bir toplayıcı oluşturuyoruz.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Neden önemli:** Uyarı geri araması olmadan Aspose.Words eksik yazı tiplerini sessizce varsayılan bir yazı tipiyle değiştirir ve sorunun varlığını asla öğrenemezsiniz. `WarningType.FontSubstitution` yakalayarak tam görünürlük elde edersiniz—ev sahibi makinede bulunmayan **yazı tiplerini algılamak** için tam olarak ihtiyacınız olan veri.

Şimdi toplayıcıyı `LoadOptions` içine takıp bir belge yüklüyoruz:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **İpucu:** Bir toplu işlemde birden çok belgeyle çalışıyorsanız aynı `FontSubstitutionWarningCollector` örneğini yeniden kullanın, ancak farklı dosyalardan gelen uyarıların karışmasını önlemek için yüklemeler arasında `Clear()` çağırmayı unutmayın.

---

## Belge Yüklenirken Uyarıları Yakalamak

Belge yüklendikten sonra toplayıcı zaten her yazı tipiyle ilgili uyarıyı tutar. Bir sonraki mantıklı soru: *Uyarıları* kolayca kaydedebileceğim ya da görüntüleyebileceğim bir şekilde nasıl yakalarım?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

Tipik çıktı şu şekildedir:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**Bu ne anlatıyor:** Her satır, orijinal yazı tipi adını ve Aspose.Words’un seçtiği yedek yazı tipini gösterir. Bu bilgilerle, yedek yazı tipinin kabul edilebilir olup olmadığına ya da eksik yazı tipini manuel olarak gömmeniz gerekip gerekmediğine karar verebilirsiniz.

---

## Eksik Yazı Tiplerini Zarifçe Ele Almak

Uyarıları tespit edip yakalamak sadece işin yarısıdır. Gerçek değer, **eksik yazı tiplerini** üretime hazır bir şekilde **ele aldığınızda** ortaya çıkar. Aşağıda üç yaygın strateji yer alıyor:

1. **Kaydet ve Devam Et** – Sadece bir denetim izi gerektiğinde toplu işleme için uygundur.  
2. **Kritik Yazı Tiplerinde İptal Et** – Belirli bir yazı tipi (ör. marka‑özel bir tipografi) eksikse istisna fırlatın.  
3. **Eksik Yazı Tiplerini Otomatik Olarak Göm** – Eksik yazı tipini bilinen bir klasörden yükleyin ve belgeyi yeniden yüklemeden önce Aspose.Words’a kaydedin.

### Örnek: Kritik Bir Yazı Tipinde İptal Et

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### Örnek: Eksik Yazı Tiplerini Otomatik Göm

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Bu kalıplar neden yardımcı:** Bir yazı tipi eksik olduğunda ne yapılacağını açıkça belirleyerek, marka bütünlüğünü veya okunabilirliği tehlikeye atabilecek sessiz yedeklemeleri ortadan kaldırırsınız. Bu, **eksik yazı tiplerini kontrol altında ele almanın** özüdür.

---

## Tam Çalışan Örnek

Her şeyi bir araya getirdiğimizde, **yazı tiplerini nasıl algılayacağınızı**, **uyarıları nasıl yakalayacağınızı** ve eksik yazı tiplerini **loglayarak** ele alacak basit bir politikayı gösteren tek bir, çalıştırılabilir program aşağıdadır.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Beklenen sonuç:** Programı, makinede bulunmayan bir yazı tipine referans veren bir belgeye karşı çalıştırdığınızda, konsol her değiştirme uyarısını listeleyecek. Eğer bir uyarı `critical` kümesindeki bir yazı tipini içeriyorsa, program erken çıkacak ve hatalı bir PDF'nin üretilmesini engelleyecektir.

---

## Sıkça Sorulan Sorular (SSS)

| Soru | Cevap |
|------|-------|
| *Bu kodu kullanmak için Aspose.Words lisansına ihtiyacım var mı?* | Evet, geçerli bir Aspose.Words lisansı değerlendirme filigranlarını kaldırır ve tam işlevselliği açar. |
| *Bu yaklaşım gömülü yazı tiplerini tespit edebilir mi?* | Gömülü yazı tipleri zaten dosyanın bir parçasıdır, bu yüzden Aspose.Words bir değiştirme uyarısı üretmez. Gerekirse `Document.FontInfos` ile gömülü yazı tiplerini listeleyebilirsiniz. |
| *Eksik yazı tipi Windows'ta bir sistem yazı tipi iken Linux'ta yoksa ne olur?* | Linux'ta aynı uyarı tetiklenir çünkü yazı tipi orada yüklü değildir. Gerekli `.ttf` dosyalarını uygulamanızla birlikte dağıtmak için “eksik yazı tiplerini ele al” stratejisini kullanın. |
| *Uyarı toplayıcı iş parçacığı...* |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}