---
category: general
date: 2026-04-05
description: Word belgesi yüklenirken eksik yazı tiplerini tespit etmek için Aspose
  yazı tipi ikame rehberi. Yazı tipi ayarlarını yapılandırmayı ve eksik yazı tiplerini
  verimli bir şekilde yönetmeyi öğrenin.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: tr
og_description: Aspose yazı tipi ikame rehberi, Word belgesi yüklenirken eksik yazı
  tiplerini tespit etmenizi sağlar. Yazı tipi ayarlarını yapılandırmayı ve eksik yazı
  tiplerini etkili bir şekilde yönetmeyi öğrenin.
og_title: Aspose Yazı Tipi Değiştirme – Word Belgelerindeki Eksik Yazı Tiplerini Tespit
  Et
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose Yazı Tipi Değiştirme – Word Belgelerindeki Eksik Yazı Tiplerini Tespit
  Et
url: /tr/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Word Belgelerinde Eksik Yazı Tiplerini Algılamak

Bir Word dosyasının bir bilgisayarda mükemmel göründüğünü, başka bir bilgisayarda ise garip yazı tipi değişiklikleri gösterdiğini hiç gördünüz mü? Bu, klasik **aspose font substitution** sorunudur ve genellikle hedef sistemde bazı yazı tiplerinin eksik olduğu anlamına gelir. Bu öğreticide, **Word belgesi yüklerken eksik yazı tiplerini nasıl algılayacağınızı**, **yazı tipi ayarlarını nasıl yapılandıracağınızı** ve **eksik yazı tiplerini nazikçe nasıl ele alacağınızı** adım adım göstereceğiz.

Tamamen çalıştırılabilir bir C# örneği üzerinden ilerleyecek, her satırın neden önemli olduğunu açıklayacak ve beklemeniz gereken konsol çıktısını göstereceğiz. Sonuna kadar, bir belge yüklendiği anda yazı tipi ikamelerini anında görebileceksiniz—tahmin yürütmeye gerek kalmayacak.

## Öğrenecekleriniz

- Aspose.Words’ün yazı tipi uyarıları için tanılayıcı toplayıcısını nasıl etkinleştireceğinizi.  
- Özel **yazı tipi ayarları**yla **Word belgesi** nasıl **yüklenir**.  
- `WarningInfo` nesneleri üzerinde döngü kurarak her ikame edilen yazı tipini nasıl listeleyeceğinizi.  
- İstenmeyen uyarıları nasıl bastıracağınız veya yedek yazı tipleri sağlayacağınız hakkında ipuçları.  
- Visual Studio’ya kopyalayıp yapıştırabileceğiniz hazır bir örnek.

### Önkoşullar

- .NET 6.0 veya üzeri (API, .NET Framework’te aynı şekilde çalışır).  
- Aspose.Words for .NET (NuGet paketi `Aspose.Words`).  
- Yüklü olmayan bir yazı tipine referans veren bir Word dosyası (ör. `MissingFont.docx`).  

Eğer bunlara sahipseniz, başlayalım.

## Adım 1 – Tanılayıcı Toplayıcıyı Etkinleştirin (Yazı Tipi Ayarlarını Yapılandırın)

İlk iş: Aspose.Words yalnızca siz ona söyleseniz yazı tipi ikame uyarılarını kaydeder. Bunun için bir `FontSettings` nesnesi oluşturup bir `LoadOptions` örneğine atamanız gerekir. Bunu, yazı tipi işleme için “debug ışıklarını” açmak gibi düşünün.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**Neden?**  
`FontSettings` nesnesi olmadan uyarı toplayıcı sessiz kalır ve hangi yazı tiplerinin değiştirildiğini asla öğrenemezsiniz. Boş bir şekilde başlatmak, Aspose’un varsayılan sistem yazı tiplerini kullanmasına izin verir *ve* herhangi bir ikameyi izler.

> **İpucu:** Belirli bir klasörün kurumsal yazı tiplerini içerdiğini biliyorsanız, `FontSettings`i `SetFontsFolder("path")` ile o klasöre yönlendirin. Bu, eksik‑yazı‑tipi uyarılarının sayısını azaltabilir.

## Adım 2 – Belgeyi Yapılandırılmış Seçeneklerle Yükleyin (Word Belgesini Yükle)

Toplayıcı aktif olduğuna göre, aynı `LoadOptions` ile `.docx` dosyanızı yükleyin. İşte bu an, Aspose’un belgeyi taradığı, her yazı tipi referansını kontrol ettiği ve ikame gerekip gerekmediğine karar verdiği zamandır.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**Neden önemli?**  
Sadece `new Document("MissingFont.docx")` çağırırsanız, varsayılan ayarlar uygulanır *ve* uyarı listesi boş kalır. `loadOptions` geçmek, tanılayıcı toplayıcının yükleme hattına bağlanmasını garantiler.

## Adım 3 – Yazı Tipi İkame Uyarılarını Alın ve Görüntüleyin (Eksik Yazı Tiplerini Algılayın)

Belge belleğe alındıktan sonra, Aspose uyarıları `document.WarningCallback.Warnings` içinde saklar. Bu koleksiyonu döngüye alıp `WarningType.FontSubstitution` için filtreleyin ve açıklamayı yazdırın. Her açıklama, hangi yazı tipinin eksik olduğunu ve yerine hangi yazı tipinin kullanıldığını söyler.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Beklenen konsol çıktısı**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

Bu çıktı, kodu çalıştıran makinede tam olarak hangi yazı tiplerinin eksik olduğunu gösterir. Artık eksik yazı tiplerini yükleyebilir, belgeye gömebilir veya ikameyi olduğu gibi bırakabilirsiniz.

![Konsol çıktısı, aspose font substitution uyarılarını gösteriyor](/images/aspose-font-substitution-console.png)

*Görsel alt metni:* aspose font substitution – ikame edilen yazı tiplerini listeleyen konsol çıktısı

## Adım 4 – İsteğe Bağlı: İkame Davranışını Özelleştirin (Eksik Yazı Tiplerini Ele Alın)

Bazen sadece bir ikame gerçekleştiğini bilmek yetmez; *nasıl* gerçekleştiğini kontrol etmek istersiniz. Aspose.Words, özel bir `IFontSubstitutionRule` kaydetmenize izin verir. Aşağıda, eksik bir yazı tipinin `Tahoma`ya düşmesini zorlayan hızlı bir örnek bulabilirsiniz.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**Ne zaman kullanılır?**  
Web hizmeti için PDF oluşturuyorsanız ve her istemcinin `Tahoma`yı render edebileceğini biliyorsanız, bu yedekleme görsel tutarlılığı sağlar ve yüzlerce yazı tipi dosyası gönderme ihtiyacını ortadan kaldırır.

## Tam Çalışan Örnek (Tüm Adımlar Birleştirildi)

Yeni bir console projesine yapıştırabileceğiniz tam program aşağıdadır. Aspose.Words NuGet paketini kurduğunuz sürece olduğu gibi derlenir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Programı çalıştırın, konsola bakın ve her eksik‑yazı‑tipi olayının yazdırıldığını göreceksiniz. Bundan sonra eksik yazı tiplerini yükleyebilir, belgeye gömebilir veya yedeklemeyi sürdürmeyi seçebilirsiniz.

## Sık Sorulan Sorular

**S: Bu PDF dönüşümüyle çalışır mı?**  
Evet. Daha sonra `doc.Save("output.pdf")` çağırdığınızda, yükleme sırasında ikame edilen yazı tipleri PDF’e gömülür. Bu yüzden uyarıları erken yakalamak, final PDF’inde sürpriz yazı tipi değişikliklerini önlemeye yardımcı olur.

**S: İşlem yapmam gereken çok sayıda belge varsa ne yapmalıyım?**  
Yükleme mantığını bir try‑catch bloğuna sarın ve bir `FontSettings` örneğini belgeler arasında yeniden kullanın. Bu, yükleme süresini azaltır ve her dosya için uyarı toplayıcısını aktif tutar.

**S: Uyarıları tamamen bastırabilir miyim?**  
`loadOptions.WarningCallback = null;` satırını yüklemeden önce ayarlayabilirsiniz, ancak **eksik yazı tiplerini algılamayı** kaybedersiniz—ki bu genellikle istenmeyen bir durumdur.

## Sonuç

**aspose font substitution** konusunda ihtiyacınız olan her şeyi kapsadık: tanılayıcı toplayıcıyı etkinleştirme, özel **yazı tipi ayarları**yla bir Word dosyasını yükleme, eksik yazı tiplerinin listesini çıkarma ve varsayılan ikame kuralını **eksik yazı tiplerini** kendi yolunuzla ele alacak şekilde geçersiz kılma. Sadece birkaç C# satırıyla, aksi takdirde ince düzen değişikliklerinin arkasında gizlenen yazı tipi sorunlarına tam görünürlük kazandırırsınız.

Sonraki adımlar? Orijinal yazı tiplerini belgeye `FontSettings.SetFontsFolder` ile gömmeyi deneyin ya da `FontSourceBase`i kullanarak yazı tiplerini bir veritabanından yükleyin. Ayrıca `Document.BuiltInStyle` koleksiyonunu inceleyerek stil‑seviyesi yazı tipi değişikliklerinin nasıl yayıldığını görebilirsiniz.

Aspose.Words veya yazı tipi yönetimi hakkında daha fazla sorunuz mu var? Yorum bırakın, resmi Aspose belgelerini keşfedin veya yeni bir proje başlatıp yukarıdaki kodla oynayın. İyi kodlamalar, ve belgeleriniz her zaman istediğiniz gibi render olsun!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}