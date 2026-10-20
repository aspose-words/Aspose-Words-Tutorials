---
category: general
date: 2026-03-16
description: Aspose.Words'ta FontSettings'i eksik yazı tiplerini sorunsuz bir şekilde
  ele almak için nasıl kullanacağınızı öğrenin—tam kod, olay işleme ve en iyi uygulama
  ipuçları.
draft: false
keywords:
- how to use fontsettings
- handle missing fonts
- Aspose.Words font substitution
- missing font detection C#
- document loading options
language: tr
og_description: Eksik yazı tiplerini yönetmek için Aspose.Words'ta FontSettings nasıl
  kullanılır—tam C# örneği ve pratik ipuçlarıyla adım adım rehber.
og_title: Aspose.Words'te Eksik Yazı Tiplerini Yönetmek için FontSettings Nasıl Kullanılır
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose.Words'ta Eksik Yazı Tiplerini Yönetmek için FontSettings Nasıl Kullanılır
url: /tr/net/working-with-fonts/how-to-use-fontsettings-to-handle-missing-fonts-in-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words'ta Eksik Yazı Tiplerini Yönetmek İçin FontSettings Nasıl Kullanılır

Word belgelerinizde sunucuda yüklü olmayan yazı tiplerine referans verildiğinde **FontSettings**'i nasıl kullanacağınızı hiç merak ettiniz mi? Tek başınıza değilsiniz. Eksik yazı tipleri çirkin yedeklemelere yol açabilir ya da istisna fırlatabilir ve çoğu geliştirici bu sorunu üretimde ortaya çıkana kadar görmezden gelir.  

Bu öğreticide **FontSettings**'i **eksik yazı tiplerini yönetmek** için **nasıl kullanacağınızı** gösterecek, ayrıntılı uyarıları yakalayacak ve belge render'ını öngörülebilir tutacaksınız. Sonunda çalıştırmaya hazır bir C# örneği, her satırın neden önemli olduğu ve çözümü daha büyük projelere nasıl uyarlayacağınız hakkında bilgi sahibi olacaksınız.

## Bu Kılavuzda Neler Ele Alınıyor

- **FontSettings**'i kurma ve `SubstitutionWarning` olayına abone olma.  
- Ayarları `LoadOptions`'a ekleyerek belgenin yüklenmesi sırasında dikkate alınmasını sağlama.  
- Bilerek eksik yazı tiplerine sahip bir test belgesi çalıştırma ve konsol çıktısını okuma.  
- Günlükleme, otomatik yedeklemeyi devre dışı bırakma ve birden fazla eksik yazı tipi gibi kenar durumlarını ele alma ipuçları.  

Harici bir dokümantasyona ihtiyaç yok—gereken her şey burada.

## Önkoşullar

- .NET 6+ (veya .NET Framework 4.6.2+).  
- Aspose.Words for .NET 23.9 veya daha yeni bir sürüm (kullandığımız API, son sürümlerde sabittir).  
- Yüklü olmadığını bildiğiniz bir yazı tipine referans veren basit bir `.docx` dosyası (ör. Linux konteynerinde *Comic Sans MS*).  

Hepsi bu—Aspose.Words dışındaki ekstra NuGet paketlerine gerek yok.

## Eksik Yazı Tiplerini Yönetmenin Önemi

Bir belge, çalışma zamanının bulamadığı bir yazı tipine referans verdiğinde Aspose.Words otomatik olarak en yakın eşleşmeyi yedekler. Bu yedekleme çoğu zaman kabul edilebilir, ancak bazen **hangi yazı tiplerinin eksik olduğunu** (uyumluluk için) **günlüğe kaydetmeniz** veya yedeklemeyi tamamen **engellemeniz** (ör. marka‑özel PDF'ler) gerekir. `FontSettings.SubstitutionWarning` olayına bağlanarak tam görünürlük ve kontrol elde edersiniz.

## Adım 1: FontSettings Oluşturun ve Substitution‑Warning Olayına Abone Olun

İlk yapmanız gereken `FontSettings` nesnesini örneklemektir. Bu nesne, kütüphane için tüm yazı tipi yapılandırmalarını tutar. Kritik kısım, Aspose.Words istenen bir yazı tipini bulamadığında **her seferinde** tetiklenen `SubstitutionWarning` olayını bağlamaktır.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – Initialise FontSettings and listen for missing‑font warnings
FontSettings fontSettings = new FontSettings();

// The lambda receives detailed info about the missing font and the chosen substitute.
fontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.MissingFontName  → the name Aspose.Words tried to load.
    // e.SubstitutedFontName → the font that was actually used instead.
    // e.WarningType → the enum describing why the warning was raised.
    Console.WriteLine($"Missing font: {e.MissingFontName}");
    Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
    Console.WriteLine($"Reason: {e.WarningType}");
};
```

**Neden Önemli:**  
- **Görünürlük:** Hangi yazı tiplerinin eksik olduğunu anında öğrenirsiniz.  
- **Denetlenebilirlik:** Konsol (veya bir logger) dosyaya yönlendirilerek uyumluluk raporları hazırlanabilir.  
- **Kontrol:** Daha sonra yedeklemeyi kendi özel yazı tipinizle değiştirebilirsiniz.

> **Pro ipucu:** Bir günlükleme çerçevesi (Serilog, NLog, vb.) kullanıyorsanız `Console.WriteLine` çağrılarını `logger.Information(...)` ile değiştirin.

## Adım 2: FontSettings'i LoadOptions'a Ekleyin

`LoadOptions`, Aspose.Words'e dosyanın yükleme aşamasında nasıl davranması gerektiğini söyleyen araçtır. `FontSettings` nesnesini atayarak uyarı işleyicisinin *içerik ayrıştırılmadan* önce aktif olmasını sağlarsınız.

```csharp
// Step 2 – Bind FontSettings to LoadOptions so the loader knows about our event handler
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Neden Önemli:**  
- `LoadOptions` geçirmeden belge yüklerseniz, varsayılan yazı tipi işleme devreye girer ve uyarıları kaçırırsınız.  
- Bu yaklaşım aynı nesne içinde diğer yükleme davranışlarını (ör. parola koruması) da ayarlamanıza olanak tanır.

## Adım 3: Belgeyi Yapılandırılmış Seçeneklerle Yükleyin

Şimdi Word dosyasını okuyalım. Yol mutlak ya da göreli olabilir; Aspose.Words az önce hazırladığımız `LoadOptions`'ı dikkate alacaktır.

```csharp
// Step 3 – Load the document while applying our FontSettings
string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";   // <-- adjust to your environment
Document document = new Document(docPath, loadOptions);
```

Belge, yüklü olmayan bir yazı tipine sahipse `SubstitutionWarning` olayı tetiklenir ve aşağıdaki örnek gibi bir çıktı görürsünüz.

### Beklenen Konsol Çıktısı

```
Missing font: Comic Sans MS
Substituted with: Arial
Reason: FontSubstitution
```

Tam yedekleme, işletim sisteminin yazı tipi yedekleme zincirine bağlı olarak değişebilir, ancak **eksik‑yazı tipi adı** her zaman raporlanır.

## Adım 4: Sonucu Doğrulayın (İsteğe Bağlı Render)

Çoğu zaman yedeklemeden sonra belgenin hâlâ düzgün göründüğünden emin olmak istersiniz. Hızlı bir yol, belgeyi PDF olarak kaydedip sonucu açmaktır.

```csharp
// Optional: Save as PDF to visually confirm the substitution
document.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
Console.WriteLine("Document saved as PDF – check the rendering.");
```

Yedeklemeyi tamamen **engellemek** isterseniz, yüklemeden önce `FontSettings.SubstitutionSettings.TableSubstitution = false` ayarlayın. Böylece Aspose.Words eksik yazı tipleri için bir istisna fırlatır; bu istisnayı yakalayıp işleyebilirsiniz.

```csharp
// Disable automatic substitution – will raise an exception on missing fonts
fontSettings.SubstitutionSettings.TableSubstitution = false;
```

## Tam Çalışan Örnek

Aşağıda tamamen çalıştırılabilir program yer alıyor. Bir konsol uygulamasına yapıştırın, dosya yolunu ayarlayın ve **F5** tuşuna basın.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create FontSettings and hook the warning event
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionWarning += (sender, e) =>
            {
                Console.WriteLine($"Missing font: {e.MissingFontName}");
                Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
                Console.WriteLine($"Reason: {e.WarningType}");
            };

            // 2️⃣ Attach FontSettings to LoadOptions
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings
                // Uncomment the next line to *disable* substitution and force an exception
                // , FontSettings = { SubstitutionSettings = { TableSubstitution = false } }
            };

            // 3️⃣ Load the document
            string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save as PDF to see the visual result
            doc.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
            Console.WriteLine("Processing complete. Check the console for missing‑font warnings.");
        }
    }
}
```

### Beklenen Sonuç

- Konsol, her eksik yazı tipini seçilen yedekleme ile birlikte yazdırır.  
- (İsteğe bağlı kaydetmeyi tutmuşsanız) oluşan PDF, belgeyi yedekleme yazı tipiyle gösterir ve düzen bütünlüğü korunur.

## Yaygın Sorular & Kenar Durumları

| Soru | Cevap |
|------|-------|
| **Birden fazla yazı tipi eksik olduğunda ne olur?** | Olay, eksik olan her yazı tipi için bir kez tetiklenir; böylece her biri için ayrı bir günlük satırı alırsınız. |
| **Yedeklemeyi özel bir yazı tipiyle değiştirebilir miyim?** | Evet. Olay işleyicisinde `e.SubstitutedFont = new FontInfo("MyCustomFont")` çağırabilirsiniz. |
| **Gömülü yazı tipleri yüklenemediğinde uyarı verilir mi?** | Kesinlikle—yazı tipi dışsal olsun ya da gömülü, uyarı aynı şekilde ortaya çıkar. |
| **`Document` nesnesini dispose etmeli miyim?** | `Document` `IDisposable` uygular. Döngü içinde çok sayıda dosya yüklüyorsanız `using` bloğu içinde kullanın. |
| **Linux konteynerlerinde çalışır mı?** | Aspose.Words sistem yazı tiplerini (ör. `fontconfig` aracılığıyla) bulabildiği sürece aynı olay mekanizması çalışır. |

## En İyi Uygulamalar & Pro İpuçları

- **Günlüklemeyi merkezileştirin:** Konsola ve kalıcı bir log dosyasına aynı anda yazan bir yardımcı yöntem oluşturun.  
- **Toplu işleme:** Yüzlerce belge dönüştürürken aynı `FontSettings` örneğini yeniden kullanarak tekrar eden olay aboneliklerinden kaçının.  
- **Performans:** SubstitutionWarning uyarıları çok az ek yük getirir; ancak binlerce dosya işliyorsanız doğrulama sonrası bunları devre dışı bırakmayı düşünün.  
- **Sürüm güvenliği:** `SubstitutionWarning` API'si Aspose.Words 16.0'dan beri sabittir; gelecekteki yükseltmelerde de güvenle kullanabilirsiniz.

## Sonuç

Aspose.Words'ta **FontSettings**'i **eksik yazı tiplerini** şık bir şekilde **yönetmek** için nasıl kullanacağınızı adım adım gösterdik. Bir `FontSettings` nesnesi oluşturup `SubstitutionWarning` olayına abone olarak ve belgeleri `LoadOptions` ile yükleyerek, yazı tipi sorunları hakkında tam görünürlük elde eder, bunları günlüğe kaydedebilir, değiştirebilir ya da eksik olduğunda işlemi durdurabilirsiniz.  

Basit bir konsol çıktısından özel yedekleme mantığına kadar bu desen, büyük ölçekli belge iş akışlarına ölçeklenebilir, çıktınızın tutarlı ve denetlenebilir kalmasını sağlar.

**Sonraki adımlar:**  

- Olay içinde `e.SubstitutedFont` atayarak **özel yazı tipi yedeklemesi** keşfedin.  
- **Belgeyi görüntülere render** ederek küçük resim oluşturma senaryolarına bu yaklaşımı entegre edin.  
- Son PDF'ye yedekleme yazı tiplerini doğrudan gömmek isterseniz **Aspose.PDF**'yi inceleyin.

Keyifli kodlamalar, ve belgeleriniz bir daha asla kayıp bir yazı tipine maruz kalmasın!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}