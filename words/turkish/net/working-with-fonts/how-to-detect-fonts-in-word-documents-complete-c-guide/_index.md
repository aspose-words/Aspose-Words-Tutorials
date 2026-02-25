---
category: general
date: 2026-02-24
description: Aspose.Words kullanarak bir Word belgesindeki yazı tiplerini nasıl tespit
  edebileceğinizi öğrenin. Geri aramayı (callback) nasıl ayarlayacağınızı ve tam kod
  örneğiyle Word belgesini nasıl yükleyeceğinizi keşfedin.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: tr
og_description: Uyarı geri araması kullanarak bir Word belgesindeki yazı tiplerini
  nasıl tespit edebileceğinizi gösteren bu kılavuz, geri aramayı nasıl ayarlayacağınızı
  ve Aspose.Words ile Word belgesini nasıl yükleyeceğinizi anlatır.
og_title: Word Belgelerinde Yazı Tiplerini Nasıl Tespit Edilir – Adım Adım C# Öğreticisi
tags:
- C#
- Aspose.Words
- Document Processing
title: Word Belgelerinde Yazı Tiplerini Nasıl Tespit Edilir – Tam C# Rehberi
url: /tr/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

LoadOptions`, `FontWarningCollector`, etc. Not translated.

Check headings: we translated.

Now produce final content with all translations.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgelerinde Yazı Tiplerini Nasıl Algılayabilirsiniz – Tam C# Kılavuzu

Bir Word dosyasını yüklediğinizde eksik olan **yazı tiplerini nasıl algılayacağınızı** hiç merak ettiniz mi? Belki editörde sorunsuz görünen bir belgeyle karşılaştınız, ancak oluşturduğunuz PDF arka planda birkaç yazı tipini değiştiriyor. Bu, yazı tipi ikamesinin klasik bir belirtisidir ve bunu erken yakalamak, kötü tasarım sürprizlerinden sizi kurtarabilir.

Bu öğreticide, pratik bir çözüm üzerinden ilerleyeceğiz: **Aspose.Words** kullanarak bir `.docx` dosyasını yüklemek, bir uyarı geri çağrısı eklemek ve **her yazı tipi ikamesini raporlayan geri çağrının nasıl ayarlanacağını** göstereceğiz. Sonunda sadece **yazı tiplerini programlı olarak nasıl algılayacağınızı** bilmekle kalmayacak, aynı zamanda **geri çağrının nasıl ayarlanacağını** doğru bir şekilde anlayacak ve **Word belgesini nasıl güvenli bir şekilde yükleyeceğinizi** öğreneceksiniz — tek bir çalıştırılabilir C# örneği içinde.

> **Ne elde edeceksiniz**
> * Tam, kopyala‑yapıştır hazır kod örneği  
> * Her satırın adım adım açıklaması  
> * Birden fazla eksik yazı tipi veya özel yazı tipi klasörleri gibi uç durumları ele almak için ipuçları  
> * Her şeyin çalıştığını doğrulamanız için beklenen konsol çıktısı

---

## Önkoşullar

- .NET 6.0 veya daha yenisi (kod .NET Core ile de çalışır)  
- Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`)  
- Bilerek yüklü olmayan bir yazı tipine referans veren bir Word dosyası (ör. `MissingFont.docx`)  
- Visual Studio, Rider veya istediğiniz herhangi bir editör  

Başka bir kütüphane gerekmez; geri kalan her şey standart .NET çalışma zamanı içinde yer alır.

## Word Belgesinde Yazı Tiplerini Nasıl Algılayabilirsiniz

### Adım 1: Yükleme Seçeneklerini Oluşturun ve Bir Uyarı Geri Çağrısı Ekleyin

İlk yaptığımız şey, Aspose.Words'e dosyayı yüklerken ortaya çıkan herhangi bir sorun hakkında bildirim almak istediğimizi söylemektir. İşte **geri çağrının nasıl ayarlanacağını** burada devreye girer.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Neden önemli:**  
`LoadOptions`, yükleme sürecini özelleştirmenin kapısıdır. `WarningCallback`'e bir `FontWarningCollector` örneği atayarak, Aspose.Words eksik bir yazı tipini bir yedekle değiştirirken her seferinde bizim `Warning` metodumuzu çağıracaktır. Bu, makinede bulunmayan **yazı tiplerini nasıl algılayacağınızın** temelidir.

### Adım 2: LoadOptions Örneğini Hazırlayın

Şimdi `LoadOptions`'ı örnekleyip geri çağrımızı bağlıyoruz.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Pro ipucu:** Aspose'un yedek yazı tiplerini nerede arayacağını kontrol etmeniz gerekiyorsa, burada `loadOptions.FontSettings`'i de ayarlayabilirsiniz. Bu, sunucuda özel bir yazı tipi klasörünüz olduğunda faydalıdır.

### Adım 3: Word Belgesini Yükleyin

Seçenekler hazır olduğunda, nihayet **Word belgesini yüklüyoruz**. Bu, Aspose'un DOCX'i ayrıştırdığı ve eksik bir yazı tipi varsa geri çağrımızın tetiklendiği anıdır.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**Arka planda ne oluyor?**  
Aspose.Words DOCX'in XML bölümlerini okur, her bir `<w:font>` referansını çözer ve sistemin yazı tipi koleksiyonunu kontrol eder. Bir referans karşılanamadığında, ilk eşleşen yedek yazı tipini ikame eder ve bir `FontSubstitution` uyarısı oluşturur.

### Adım 4: Çıktıyı Doğrulayın

Programı çalıştırın ve konsola bakın. Her eksik yazı tipi için şu şekilde bir satır göreceksiniz:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

Belge eksik yazı tipi içermiyorsa, konsol sessiz kalır — bu da **yazı tiplerini nasıl algılayacağınızın** hiçbir sonuç döndürmediği anlamına gelir.

### Adım 5: Tam Çalışan Örnek (Konsol Uygulaması)

Aşağıda, yeni bir konsol projesine ekleyebileceğiniz bağımsız bir `Program.cs` dosyası bulunuyor. Tartıştığımız tüm parçaları ve hata ayıklama sırasında konsol penceresini açık tutmak için küçük bir yardımcıyı içerir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Beklenen konsol çıktısı** (örnek):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

`MissingFont.docx` dosyasını yalnızca yüklü yazı tipleri kullanan bir dosyayla değiştirirseniz, sadece “Press any key…” satırını göreceksiniz — bu da algılama mantığının amaçlandığı gibi çalıştığını doğrular.

## Yaygın Sorular ve Uç Durumlar

### Tüm uyarıları, sadece yazı tipi ikamesini değil, yakalamam gerekirse ne yapmalıyım?

Sadece `if (info.Type == WarningType.FontSubstitution)` koşulunu kaldırın. `WarningInfo` nesnesi, diğer senaryolar için (ör. `DocumentStructure`, `ImageLoading`) geçiş yapabileceğiniz bir `Type` enum'ı içerir.

### Uyarıları konsola yerine bir dosyaya kaydedebilir miyim?

Kesinlikle. `Console.WriteLine`'ı herhangi bir kayıt çerçevesi çağrısıyla (`Serilog`, `NLog` vb.) değiştirin. Geri çağrı, belgeyi yükleyen aynı iş parçacığında çalışır, bu yüzden kaydedicinizin çok iş parçacıklı güvenli olduğundan emin olun.

### Bu bir web uygulamasında nasıl davranır?

ASP.NET Core'da genellikle bir singleton `IWarningCallback` uygulamasını enjekte eder ve `LoadOptions` aracılığıyla geçirirsiniz. Yanıt akışına doğrudan yazmaktan kaçının — bir veritabanına veya daha sonra bir API uç noktası üzerinden sunabileceğiniz bir bellek içi koleksiyona kaydedin.

### Sistem dışı bir klasörde depolanan özel yazı tipleri ne olur?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Şimdi Aspose.Words, OS yazı tiplerine geri dönmeden önce `C:\MyCustomFonts` klasörünü arayacak, böylece gördüğünüz ikame uyarılarının sayısını azaltacaktır.

## Görsel Özet

![Aspose.Words'ta yazı tipleri uyarı geri çağrısı](/images/font-warning-callback.png "Uyarı geri çağrısı kullanarak yazı tiplerini nasıl algılayabilirsiniz")

*Ekran görüntüsü, eksik bir yazı tipi ikame edildiğinde konsol çıktısını gösterir. Alt metin, SEO için anahtar kelimeyi içerir.*

## Sonuç

Artık Aspose.Words ile yüklediğiniz herhangi bir Word dosyasında **yazı tiplerini nasıl algılayacağınız** konusunda sağlam, üretime hazır bir deseniniz var. **Geri çağrının nasıl ayarlanacağını** kullanarak eksik veya ikame edilen yazı tipleri hakkında gerçek zamanlı bilgi ediniyorsunuz ve kodunuzu temiz ve sürdürülebilir tutarken **Word belgesini nasıl yükleyeceğinizi** doğru bir şekilde öğrendiniz.

Sonraki adımlar? Geri çağrıyı genişleterek uyarıları bir listeye toplayın, ardından bir UI'da veya otomatik bir raporda gösterin. Ayrıca yedek olarak seçilecek *hangi* yazı tiplerinin belirleneceğini kontrol etmek için `FontSettings.SubstitutionSettings`'i keşfedebilirsiniz.

Denemekten çekinmeyin — belgeyi değiştirin, daha fazla eksik yazı tipi ekleyin veya mantığı daha büyük bir belge‑işleme hattına entegre edin. Herhangi bir sorunla karşılaşırsanız, aşağıya bir yorum bırakın ya da GitHub'da bana mesaj atın.

Kodlamaktan keyif alın ve belgelerinizin her zaman beklediğiniz yazı tipleriyle render edilmesini dileriz!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}