---
category: general
date: 2026-03-14
description: Eksik yazı tiplerini Aspose.Words ile hızlı bir şekilde yönetin. Yazı
  tipi ikame uyarılarını yakalamayı, LoadOptions'ı yapılandırmayı ve render sorunlarından
  kaçınmayı öğrenin.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: tr
og_description: Aspose.Words'ta eksik yazı tiplerini bir uyarı toplayıcı kullanarak
  yönetin. Bu öğretici, yazı tipi ikamelerini nasıl tespit edip kaydedeceğinizi adım
  adım gösterir.
og_title: Aspose.Words'ta Eksik Yazı Tiplerini Yönet – Tam C# Rehberi
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Aspose.Words'ta Eksik Yazı Tiplerini Yönetme – Tam C# Rehberi
url: /tr/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words'ta Eksik Yazı Tiplerini Yönetme – Tam C# Kılavuzu

Bir Word belgesi yüklerken **eksik yazı tiplerini yönetmeniz** gerektiğinde ve PDF ya da görüntü çıktınızın neden bozuk göründüğünü merak ettiğiniz oldu mu? Tek başınıza değilsiniz. Eksik yazı tipi dosyaları, mükemmel tasarlanmış bir raporu karışık bir karmaşaya dönüştürebilen sessiz bir sorun kaynağıdır.  

İyi haber? Aspose.Words, bu yazı tipi‑değiştirme olaylarını yakalamanız, kaydetmeniz ve isterseniz bir yedek yazı tipiyle değiştirmeniz için temiz bir yol sunar. Bu öğreticide, uyarı toplayıcısını nasıl kuracağınızı, `LoadOptions` içine nasıl bağlayacağınızı ve eksik yazı tipleri içerebilecek bir belgeyi nasıl yükleyeceğinizi tam ve çalıştırılabilir bir örnekle adım adım göstereceğiz.

Bu kılavuzun sonunda şunları yapabileceksiniz:

* Belge yüklenmesi sırasında gerçekleşen her yazı tipi değişimini tespit etmek.  
* Her eksik yazı tipi için dostça bir konsol mesajı (veya bir logger’a yönlendirme) çıkarmak.  
* Gerektiğinde çözümü yazı tiplerini değiştirecek şekilde genişletmek.  

**Önkoşullar** – şunlara ihtiyacınız olacak:

* .NET 6.0 veya daha yeni bir sürüm (kod .NET Core ve .NET Framework ile de çalışır).  
* Aspose.Words for .NET NuGet paketi (güncel sürüm 23.11).  
* Bilerek yüklü olmayan bir yazı tipine referans veren bir Word dosyası – buna `doc-with-missing-font.docx` adını vereceğiz.  

Eğer C# konusunda zaten rahatsanız ve bir projeniz kuruluysa, doğrudan koda geçebilirsiniz. Aksi takdirde, okumaya devam edin; önce küçük kurulum adımlarını ele alacağız.

---

## Eksik Yazı Tiplerini Yönetmenin Önemi

Aspose.Words bir belgeyi yüklediğinde, her glifi makinede yüklü bir yazı tipine eşleştirmeye çalışır. Tam yazı tipini bulamazsa, sessizce en yakın eşleşmeyi kullanır. Bu değişim satır yüksekliklerini, harf aralıklarını (kerning) değiştirebilir ve hatta karakterlerin kaybolmasına neden olabilir. `WarningType.FontSubstitution` olayını yakalayarak **ne**yin değiştirildiğini ve **neden** değiştirildiğini şeffaf bir şekilde görebilirsiniz; bu şu amaçlar için kritiktir:

* Marka tutarlılığını korumak (kurumsal yazı tipiniz tasarlandığı gibi görünmelidir).  
* PDF dönüşüm sorunlarını ayıklamak—çoğu zaman suçlu eksik bir yazı tipidir.  
* Sorunlu dosyaları manuel inceleme için işaretlemeniz gereken otomatik belge iş akışları oluşturmak.  

Şimdi “neden”in net olduğuna göre, **nasıl** yapacağımıza dalalım.

## Adım 1 – Uyarı Toplayıcıyı Kurma

İlk ihtiyacımız, Aspose.Words uyarılarını dinleyebilecek bir nesnedir. `DocumentWarnings`, `IWarningCallback` arayüzünü uygular ve kütüphane bir uyarı verdiğinde tepki vermemizi sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**Ne oluyor?**  
* `DocumentWarnings`, geri çağırma arayüzünün ince bir sarmalayıcısıdır.  
* Lambda, `e.WarningType`'ı kontrol eder, böylece alakasız uyarıları (örneğin kullanımdan kaldırılmış özellikler) görmezden geliriz.  
* `e.WarningInfo` eksik yazı tipinin adını içerir ve biz bunu konsola yazdırırız.  

*İpucu*: Üretimde `Console.WriteLine` yerine yapılandırılmış bir logger (Serilog, NLog) kullanın—bu sayede zaman damgaları ve log seviyeleri otomatik elde edilir.

## Adım 2 – Toplayıcıyı LoadOptions'a Bağlama

`LoadOptions`, Aspose.Words ile açtığınız her belgenin geçidi gibidir. `fontWarnings` örneğimizi onun `WarningCallback` özelliğine atayarak, toplama işleminin yükleme sürecinde aktif olmasını sağlarız.

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**Neden LoadOptions kullanmalı?**  
Uyarıların yanı sıra, `LoadOptions` şifre yönetimi, kodlama ve hatta özel kaynak yüklemeyi kontrol etmenizi sağlar. Burada uyarı kısmına odaklandık, ancak aynı desen diğer geri çağırmalar için de çalışır.

## Adım 3 – Belgeyi Yapılandırılmış Seçeneklerle Yükleme

Şimdi belgeyi belleğe alıyoruz. Eğer herhangi bir yazı tipi eksikse, toplama aracımız tetiklenecek ve her değişim için bir konsol satırı göreceksiniz.

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

Eğer bu kod parçasını, örneğin *Calibri Light* referans veren ancak test makinenizde sadece *Calibri* yüklü olan bir belgeyle çalıştırırsanız, aşağıdakine benzer bir çıktı alırsınız:

```
Font 'Calibri Light' was substituted.
```

Bu, tüm algılama döngüsüdür—basit ama güçlü.

## Adım 4 – (İsteğe Bağlı) Eksik Yazı Tiplerini Bilinen Bir Yedekle Değiştirme

Bazen sadece sorunu kaydetmek istemezsiniz; işlenmiş çıktının tutarlı görünmesi için bir yedek yazı tipi zorlamak istersiniz. Aspose.Words, eksik yazı tiplerini bir yedekle eşleyen özel bir `FontSettings` nesnesi sağlamanıza izin verir.

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**Açıklama**  
* `"*"` joker karakteri, Aspose.Words'e *her* eksik yazı tipini aynı şekilde ele almasını söyler.  
* İnce ayar gerektiğinde belirli yazı tiplerini tek tek eşleyebilirsiniz.  
* `document.FontSettings` ayarlandıktan sonra, sonraki tüm render işlemleri (PDF, görüntü, HTML) bu değişikliği dikkate alır.

## Tam Çalışan Örnek

Aşağıda, bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz tam program bulunmaktadır. Gerekli tüm `using` ifadelerini, hata yönetimini ve açıklamaları içerir.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**Beklenen çıktı** (eksik bir yazı tipi tespit edildiğinde):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

Eğer kaynak belge zaten tüm gerekli yazı tiplerini içeriyorsa, uyarı satırı hiç görünmez—endişelenecek bir şey yok.

## Yaygın Sorular & Kenar Durumları

| Soru | Cevap |
|----------|--------|
| **Yalnızca kaydetmek, yazı tiplerini değiştirmek istemezsem ne olur?** | `FontSettings` bloğunu tamamen atlayın; sadece uyarı toplayıcısı yeterlidir. |
| **Uyarıları bir dosyaya yönlendirebilir miyim?** | Evet—`Console.WriteLine` yerine `File.AppendAllText("font-warnings.log", …)` kullanın. |
| **Bu DOC, DOCX ve ODT için çalışır mı?** | Kesinlikle. `LoadOptions`, Aspose.Words tarafından desteklenen tüm formatlara uygulanır. |
| **Belgeye gömülü özel yazı tipleri ne olur?** | Gömülü yazı tipleri değiştirme mekanizmasını atlar; olduğu gibi kullanılır. |
| **Performans kaybı var mı?** | Ek yük çok azdır—her eksik yazı tipi için yalnızca bir geri çağırma. Büyük partilerde, her olay için yazmak yerine uyarıları toplamak daha iyidir. |

## Sonuç

Aspose.Words'ta `DocumentWarnings` toplayıcısını `LoadOptions`'a bağlayarak, isteğe bağlı olarak bir yedek yazı tipi değiştirerek ve sonucu kaydederek **eksik yazı tiplerini nasıl yöneteceğinizi** gösterdik. Bu desen, yazı tipi‑değiştirme olaylarını tam olarak görmenizi sağlar ve PDF, görüntü veya HTML dönüşümlerinde görsel bütünlüğü korumanıza yardımcı olur.

İleride keşfedebileceğiniz adımlar:

* Uyarı toplayıcısını merkezi bir logging çerçevesiyle entegre edin.  
* Eksik yazı tipli belgeleri toplu işleme için listeleyen bir UI kontrol paneli oluşturun.  
* Bu yaklaşımı Aspose.PDF ile birleştirerek oluşturulan PDF'lerin gerçekten yedek yazı tipini kullandığını doğrulayın.  

Denemekten çekinmeyin—`"Arial"` yerine `"Tahoma"` kullanın ya da farklı bir belge seti yükleyin. Temel fikir aynı kalır: uyarıyı yakalayın, üzerine işlem yapın ve belgelerinizin tam olarak istediğiniz gibi görünmesini sağlayın.

Kodlamanın tadını çıkarın! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}