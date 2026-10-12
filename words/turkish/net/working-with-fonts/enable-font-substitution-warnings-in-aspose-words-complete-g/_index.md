---
category: general
date: 2026-01-11
description: .NET belgelerinizde eksik yazı tiplerini tespit etmek için yazı tipi
  ikame uyarılarını etkinleştirin. Eksik yazı tipi adını nasıl alacağınızı ve Aspose.Words
  ile eksik yazı tiplerini nasıl listeleyeceğinizi öğrenin.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: tr
og_description: Eksik yazı tiplerini tespit etmek, eksik yazı tipi adını almak ve
  belgelerinizdeki eksik yazı tiplerini listelemek için Aspose.Words'ta yazı tipi
  ikame uyarılarını etkinleştirin.
og_title: Yazı Tipi Değiştirme Uyarılarını Etkinleştir – Adım Adım C# Öğreticisi
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Words'te Yazı Tipi Değiştirme Uyarılarını Etkinleştirme – Tam Kılavuz
url: /tr/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yazı Tipi Değiştirme Uyarılarını Etkinleştirme – Tam Kılavuz

Sunucuda bir Word belgesini yükledikten sonra belgenin biraz farklı göründüğünü hiç merak ettiniz mi? Muhtemelen orijinal yazarın kullandığı bir yazı tipi makinenizde mevcut değil ve Aspose.Words sessizce en yakın eşleşmeyle değiştirdi. **Yazı tipi değiştirme uyarılarını etkinleştirin** ve eksik olan yazı tiplerini, neyle değiştirildiklerini ve bu bilgilerle nasıl hareket edeceğinizi anında öğrenin.

Bu öğreticide, **eksik yazı tiplerini tespit etmeyi**, **eksik yazı tipi adını almayı** ve raporlama için **eksik yazı tiplerini listelemeyi** gösteren pratik, uçtan uca bir örnek üzerinden ilerleyeceğiz. Gereksiz ayrıntı yok, sadece bugün herhangi bir .NET projesine ekleyebileceğiniz net bir çözüm.

---

## Öğrenecekleriniz

- `LoadOptions`'ı, Aspose.Words'un ayrıntılı uyarılar vermesi için nasıl yapılandıracağınızı.
- Bir belgeyi yüklemek ve yazı tipiyle ilgili uyarıları sıralamak için gereken tam kod.
- Eksik yazı tipi adını ve onun yerine geçen yazı tipini çıkarmanın yolları, ardından düzenli bir rapor oluşturma.
- Onlarca eksik yazı tipine sahip belgeler veya özel yazı tipi klasörleri gibi uç durumları ele almanın ipuçları.

### Önkoşullar

- .NET 6+ (kod ayrıca .NET Framework 4.7+ ile de çalışır)
- Aspose.Words for .NET 23.10 veya daha yeni bir sürüm (NuGet'ten alabilirsiniz)
- Yüklü olmayan bir yazı tipine referans veren örnek bir DOCX (biz ona `MissingFont.docx` diyeceğiz)

Bu temellere sahipseniz, hemen başlayalım.

---

## Adım 1: Yazı Tipi Değiştirme Uyarılarını Etkinleştirmek İçin LoadOptions'ı Ayarlayın  

İlk yapmanız gereken, Aspose.Words'a eksik yazı tiplerine önem verdiğinizi söylemektir. Varsayılan olarak kütüphane yalnızca uyarıları dahili olarak kaydeder. `SubstitutionWarningLevel`'ı `Typical` (veya en ayrıntılı çıktı için `All`) olarak ayarlamak bu anahtarı çevirir.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Neden Önemli:**  
`SubstitutionWarningLevel` ayarlandığında, Aspose.Words bir referans verilen yazı tipini bulamadığında belgeye bir `FontSubstitutionWarning` ekler ve bu uyarı `Warnings` koleksiyonuna konur. Bu koleksiyon, belgeyi manuel olarak ayrıştırmadan **eksik yazı tiplerini tespit etmenin** tek güvenilir yoludur.

> **Pro ipucu:** Bir dizi belgeyle çalışıyorsanız ve her değişikliği kesinlikle yakaladığınızdan emin olmak istiyorsanız `FontSubstitutionWarningLevel.All` kullanın. Biraz daha gürültülü olabilir ama hiçbir uyarının kaçmamasını garantiler.

---

## Adım 2: Yapılandırılmış Seçenekleri Kullanarak Belgeyi Yükleyin  

Uyarı sistemi hazır olduğuna göre, az önce hazırladığımız `LoadOptions` ile DOCX dosyanızı yükleyin. Yol mutlak ya da göreli olabilir; dosyanın mevcut olduğundan emin olun.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**Arka planda neler oluyor?**  
Aspose.Words belgenin XML'ini ayrıştırır, her bir `<w:font>` öğesini çözer ve sistemin yazı tipi kataloğunu (ve `FontSettings`'e eklediğiniz özel klasörleri) kontrol eder. Bir yazı tipi bulunamadığında bir uyarı kaydeder—bu da daha sonra **eksik yazı tiplerini listelemek** için tam olarak ihtiyacımız olan şeydir.

---

## Adım 3: Uyarılar Üzerinde Döngü Oluşturun ve Eksik Yazı Tipi Ayrıntılarını Çıkarın  

Belge bellekteyken, `Warnings` koleksiyonu her `FontSubstitutionWarning` öğesini tutar. Üzerinde döngü kuracağız, doğru türü filtreleyecek ve dostane bir rapor yazdıracağız.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Beklenen çıktı** (kaynak belge `MyCustomFont` adlı bir yazı tipine referans veriyorsa ve bu yüklü değilse):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Her bir girişin hem **eksik yazı tipi adını al** (`MyCustomFont`) hem de yedek yazı tipini (`Arial`) verdiğine dikkat edin. Bu, orijinal yazı tipini gömmek, yazardan bir yedek istemek ya da sadece değişikliği kabul etmek gibi kararları vermeniz için tam olarak ihtiyaç duyduğunuz bilgidir.

---

## Adım 4: İsteğe Bağlı – Verileri Daha Sonraki İşlem İçin Bir Listeye Toplayın  

Raporu CSV'ye aktarmanız, bir API üzerinden göndermeniz veya sadece daha sonra kullanmak üzere bellekte tutmanız gerekiyorsa, uyarıları güçlü tipli bir listede saklayabilirsiniz.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Artık **eksik yazı tiplerini listeleyebiliyorsunuz** ve bu formatı herhangi bir downstream sistem tüketebilir. Bir gösterge tablosuna veri sağlıyor olun ya da bir denetim kaydı oluşturuyor olun, veri hazır.

---

## Adım 5: Kenar Durumlarını ve Yaygın Tuzakları Ele Alma  

### Tek Bir Çalışmada Birden Çok Eksik Yazı Tipi  

Büyük kurumsal şablonlar genellikle onlarca özel yazı tipine referans verir. Uyarı koleksiyonu büyük olabilir, ancak yukarıda gösterilen döngü deseni doğrusal olarak ölçeklenir, bu yüzden performans bir sorun değildir. Çıktıyı okunabilir tutmayı unutmayın—sayfa veya stil bazında gruplamak, daha derin bir analiz gerektiğinde yardımcı olabilir.

### Özel Yazı Tipi Klasörleri  

Yazı tiplerini standart olmayan bir dizinde (ör. paylaşımlı bir ağ klasörü) saklıyorsanız, Aspose.Words'a nerelere bakması gerektiğini söyleyin:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Bu ayarı belgeyi yüklemeden *önce* yapmak, kütüphanenin yazı tiplerini bulma şansı verir ve bu da bazı uyarıların tamamen ortadan kalkmasını sağlayabilir.

### Belirli Uyarıları Bastırma  

Bazen belirli bir değişikliğin kabul edilebilir olduğunu bilirsiniz (ör. değiştirmekten çekinmediğiniz süslü bir yazı tipi). Bu uyarıları sonradan filtreleyebilirsiniz:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Sürüm Uyumluluğu  

`FontSubstitutionWarningLevel` enum'u Aspose.Words 20.12'den beri kararlıdır. Daha eski bir sürüm kullanıyorsanız, uyarı‑seviyesi özelliğine erişmek için yükseltme yapmanız gerekebilir.

---

## Tam Çalışan Örnek  

Aşağıda, yukarıdaki tüm adımları içeren eksiksiz, çalıştırmaya hazır program yer alıyor. Yeni bir console projesine yapıştırın, Aspose.Words NuGet paketini ekleyin ve `docPath` değişkenini eksik bir yazı tipine referans veren bir belgeye yönlendirin.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Bu programı çalıştırdığınızda **yazı tipi değiştirme uyarılarını etkinleştirecek**, **eksik yazı tiplerini tespit edecek**, **eksik yazı tipi adını alacak** ve **eksik yazı tiplerini** hem konsolda hem de bir CSV dosyasında **listeleyecek**.

---

## Sonuç  

Aspose.Words'ta **yazı tipi değiştirme uyarılarını etkinleştirmek** için gereken her şeyi, ilk yapılandırmadan eksik yazı tiplerinin temiz bir listesini çıkarmaya kadar ele aldık. Yukarıdaki adımları izleyerek belgelerinizi denetleyebilir, görsel tutarlılığı sağlayabilir ve sunucuda render alırken kötü sürprizlerden kaçınabilirsiniz.

Sonraki adımda şunları keşfetmek isteyebilirsiniz:

- **Eksik yazı tiplerini** doğrudan çıktı PDF veya DOCX'e gömmek (`FontSettings.EmbeddedFonts` kullanın).
- Oluşturulan rapora dayanarak build ajanlarında **yazı tipi kurulumunu otomatikleştirmek**.
- **CI pipeline'larıyla entegrasyon** yaparak kritik yazı tipleri eksik olduğunda build'leri başarısız kılmak.

Bunları deneyin, ve basit bir uyarı sistemini tam kapsamlı bir yazı tipi yönetim akışına dönüştüreceksiniz.

Kodlamaktan keyif alın, ve tüm yazı tipleriniz bulunsun!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}