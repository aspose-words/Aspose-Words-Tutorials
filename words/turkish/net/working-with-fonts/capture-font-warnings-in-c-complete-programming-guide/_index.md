---
category: general
date: 2026-02-18
description: Aspose.Words kullanarak C#'de yazı tipi uyarılarını yakalamayı ve eksik
  yazı tiplerini tespit etmeyi öğrenin. Eksik yazı tiplerini verimli bir şekilde ele
  almak için bu adım adım rehberi izleyin.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: tr
og_description: C#'ta yazı tipi uyarılarını yakalayın ve eksik yazı tiplerini tespit
  etmeyi, eksik yazı tiplerini yönetmeyi ve eksik yazı tiplerini tam bir kod örneğiyle
  listelemeyi öğrenin.
og_title: C#'ta Yazı Tipi Uyarılarını Yakalama – Tam Rehber
tags:
- Aspose.Words
- C#
- Font Management
title: C#'de Yazı Tipi Uyarılarını Yakalama – Tam Programlama Rehberi
url: /tr/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta Yazı Tipi Uyarılarını Yakalama – Tam Programlama Rehberi

Bir belgenin sunucuda yüklü olmayan bir yazı tipine referans verdiğinde **yazı tipi uyarılarını yakalamayı** hiç merak ettiniz mi? Tek başınıza değilsiniz. Birçok kurumsal uygulamada eksik yazı tipleri düzen bozukluklarına neden olur ve bunları tespit etmenin tek güvenilir yolu, kütüphanenin fırlattığı uyarıları dinlemektir.  

Bu öğreticide, yalnızca **yazı tipi uyarılarını yakalamak** değil, aynı zamanda **eksik yazı tiplerini tespit etmek**, **eksik yazı tiplerini işlemek** ve hatta **eksik yazı tiplerini listelemek** için hazır‑çalıştır bir çözüm göstereceğiz, böylece değiştirme, gömme veya kullanıcıyı bilgilendirme kararını verebilirsiniz. Harici belgeye gerek yok—sadece kopyalayıp yapıştırın ve çalıştırın.

## Öğrenecekleriniz

- `LoadOptions`'ı yapılandırarak yazı tipi ikame uyarılarını nasıl açacağınızı.  
- Bir DOCX'i yüklemek ve her uyarıyı çıkarmak için gereken tam kod.  
- Her adımın neden önemli olduğunu, performans hususları dahil.  
- Karışık betik yazı tipli belgeler veya özel yazı tipi klasörleri gibi uç durumların nasıl ele alınacağını.  

**Önkoşullar**: .NET 6+ (veya .NET Framework 4.6+), **Aspose.Words** NuGet paketine referans ve C# temel bilgisi. Aspose.Words daha önce kullanmadıysanız endişelenmeyin—bu rehber her ayrıntıyı size gösterir.

![Diagram showing capture font warnings flow](image.png){alt="yazı tipi uyarılarını yakalama diyagramı"}

## Yazı Tipi Uyarılarını Yakalama – Neden Önemli

Aspose.Words bir belgeyi yüklediğinde, mevcut olmayan herhangi bir yazı tipini sessizce bir yedekle değiştirir. Bu yedekleme yükleme işlemini sürdürür, ancak görsel sonuç tamamen kaymış olabilir. **SubstitutionWarningLevel.All** bayrağını etkinleştirerek, kütüphane her eksik yazı tipi için bir `WarningInfo` girdisi ekler, böylece belge işlenmeden veya kaydedilmeden önce **eksik yazı tiplerini tespit** edebilirsiniz.

> **Pro ipucu:** Yüzlerce dosyayı toplu bir işte işliyorsanız, bu uyarıları merkezi bir depoya kaydetmek, daha sonra saatler süren manuel QA’yı kurtarabilir.

## Adım 1: Projenizi Kurun

1. Favori IDE'nizi açın (Visual Studio, Rider, VS Code).  
2. Yeni bir konsol projesi oluşturun:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Aspose.Words paketini ekleyin:

```bash
dotnet add package Aspose.Words
```

Hepsi bu kadar—ekstra DLL gerekmez, COM etkileşimi yok. Kütüphane, **eksik yazı tiplerini işlemek** için ihtiyacınız olan her şeyi içerir.

## Adım 2: Tüm Yazı Tipi İkame Uyarılarını Yakalamak İçin Load Options'ı Hazırlayın

Motorun **yazı tipi uyarılarını yakalaması** için, her ikameyi kaydetmesini söylemelisiniz. Aşağıdaki kod parçacığı bir `LoadOptions` örneği oluşturur, uyarı seviyesini etkinleştirir ve (isteğe bağlı olarak) motoru kullanmak isteyebileceğiniz özel yazı tiplerini içeren bir klasöre yönlendirir.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Neden önemli:**  
- `SubstitutionWarningLevel.All`, **her** eksik‑yazı tipi olayının kaydedildiğinden emin olur, sadece ilkini değil.  
- Bu bayrak olmadan, Aspose.Words sessizce yazı tipini değiştirir ve bir sorunun varlığını asla bilmezsiniz.

## Adım 3: Yapılandırılmış Seçeneklerle Belgeyi Yükleyin

Şimdi dosyayı gerçekten açıyoruz. `DocumentWithMissingFonts.docx` ifadesini test belgenizin yolu ile değiştirin.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Dosya, makinede (veya eklediğiniz isteğe bağlı klasörde) bulunmayan yazı tiplerine referans içeriyorsa, `document.WarningInfoCollection` doldurulacaktır.

## Adım 4: Yazı Tipi İkame Uyarılarını Bulun ve Görüntüleyin

İşte öğreticinin kalbi: `WarningInfoCollection` üzerinde döngü yaparak **eksik yazı tiplerini listelemek**. `WarningType.FontSubstitution` ile filtreleyecek ve dostça bir mesaj yazdıracağız.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Beklenen Çıktı

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Belge yalnızca yüklü yazı tiplerini kullanıyorsa, “✅ No missing fonts detected” satırını göreceksiniz.

## Adım 5: İleri – **Eksik Yazı Tiplerini** Programatik Olarak Nasıl **İşlersiniz**

Sadece bir liste yazdırmak tanı teşhis aracı için yeterli olabilir, ancak birçok üretim sistemi **eksik yazı tiplerini** otomatik olarak **işlemek** zorundadır. Aşağıda iki yaygın strateji bulunmaktadır:

### 5.1 Bilinen Bir Yedekle Değiştir

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Özel Bir Yazı Tipini Anında Göm

Kurumsal bir yazı tipi dosyanız (`MyBrand.ttf`) varsa, eksik bir yazı tipi tespit edildiğinde onu gömebilirsiniz:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Not:** Yazı tiplerini gömmek çıktı dosyasının boyutunu artırabilir, bu yüzden doğruluk ile bant genişliği arasındaki dengeyi göz önünde bulundurun.

## Yaygın Tuzaklar ve Nasıl Kaçınılır

| Semptom | Muhtemel Neden | Çözüm |
|---------|----------------|------|
| Belge hatalı görünüyor ancak hiçbir uyarı görünmüyor | `SubstitutionWarningLevel` `All` olarak ayarlanmamış | Adım 2'de bayrağın tam olarak gösterildiği gibi ayarlandığından emin olun |
| Uyarılar aynı yazı tipini birden çok kez listeliyor | Belge aynı yazı tipini birkaç stil içinde içeriyor | Eğer yalnızca benzersiz bir listeye ihtiyacınız varsa, tekrarı kaldırın: `fontWarnings.Select(w => w.Description).Distinct()` |
| Uygulama büyük DOCX dosyalarında çöküyor | Varsayılan bellek ayarlarıyla yükleme | `LoadOptions.LoadFormat` kullanın veya bellek baskısını azaltmak için dosyayı akış olarak okuyun |

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

`dotnet run` ile programı çalıştırın. Konsola eksik yazı tiplerinin listesinin yazdırıldığını göreceksiniz, bu da **yazı tipi uyarılarını başarıyla yakaladığınızı** doğrular.

## Sonuç

Artık Aspose.Words kullanarak C#'ta **yazı tipi uyarılarını yakalamak**, **eksik yazı tiplerini tespit etmek**, **eksik yazı tiplerini işlemek** ve **eksik yazı tiplerini listelemek** için eksiksiz, üretim‑hazır bir modele sahipsiniz. Yaklaşım hafiftir, sadece birkaç satır kod gerektirir ve mevcut herhangi bir işlem hattına eklenebilir—ister

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}