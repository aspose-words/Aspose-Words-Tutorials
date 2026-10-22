---
category: general
date: 2026-06-17
description: Aspose.Words'te yazı tipi ikamesini yönetin ve .NET geliştiricileri için
  bu adım adım öğreticiyle eksik yazı tiplerini hızlıca tespit edin.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: tr
og_description: Aspose.Words'te yazı tipi ikamesini yönetin ve belgelerinizde eksik
  yazı tiplerini nasıl tespit edeceğinizi net kod örnekleriyle öğrenin.
og_title: Aspose.Words'ta Yazı Tipi Değişimini Yönetme – Tam Kılavuz
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Aspose.Words'ta Yazı Tipi Değişimini Yönetme – Tam Programlama Rehberi
url: /tr/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words’te Yazı Tipi Değişimini Yönetme – Tam Programlama Kılavuzu

Bir Word belgesi, sunucuda yüklü olmayan bir yazı tipine başvurduğunda **yazı tipi değişimini nasıl yönetirsiniz**? Tek başınıza değilsiniz. Gerçek dünyadaki birçok uygulamada—örneğin fatura oluşturucular veya otomatik rapor servisleri—eksik yazı tipleri, düzeni bozan sessiz geri dönüşlere neden olur.  

İyi haber şu ki Aspose.Words, **eksik yazı tiplerini algılamanızı** ve istediğiniz şekilde yanıt vermenizi sağlayan yerleşik bir uyarı sistemi sunar. Bu öğreticide bir uyarı işleyicisi kaydetmeyi, bir belge yüklemeyi ve bilmeniz gereken tam yazı tipi değişim olaylarını nasıl çıkaracağınızı adım adım göstereceğiz. Sonunda, “**eksik yazı tiplerini nasıl tespit ederim**?” sorusuna temiz, üretime hazır bir kodla yanıt verebileceksiniz.

## Bu Öğreticide Neler Ele Alınıyor

* Her yazı tipi değişiminde uyarı üretecek şekilde Aspose.Words’ü yapılandırma.
* Bu uyarıları özel bir işleyicide yakalayarak kaydetme, değiştirme veya iptal etme.
* Yakalanan verileri **eksik yazı tiplerini** belge kaydedilmeden veya render edilmeden önce tespit etmek için kullanma.
* Sessizce bir yedek yazı tipi seçildiğinde ortaya çıkan kenar durumlarını giderme ipuçları.
* Herhangi bir .NET konsol uygulamasına ekleyebileceğiniz tam, çalıştırılabilir bir örnek.

> **Önkoşullar** – .NET SDK (6.0+ önerilir), geçerli bir Aspose.Words for .NET lisansı (veya geçici bir değerlendirme anahtarı) ve kasıtlı olarak yüklü olmayan bir yazı tipine başvuran bir DOCX örneği gerekir. Başka üçüncü‑taraf kütüphane gerekmez.

---

## ## Özel Bir Uyarı İşleyicisiyle Yazı Tipi Değişimini Yönetme

Aspose.Words, istenen bir yazı tipini bulamadığında her seferinde bir `WarningInfo` nesnesi oluşturur. Varsayılan olarak bu uyarılar göz ardı edilir, bu yüzden çoğu zaman bir değişim fark etmezsiniz. **Yazı tipi değişimini yönetmek** için varsayılan uyarı işleyicisini, gerçekten bir şey yapan bir işleyiciyle değiştirirsiniz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### Neden Bu Şekilde Çalışır

* `FontSettings.DefaultWarningHandler` global bir statik özelliktir—bir kez ayarlandığında, **şu anki AppDomain** içindeki **her** Aspose.Words işlemi sizin temsilcinizi (delegate) kullanır.
* `WarningInfoCollectionHandler`, `WarningType` ve okunabilir bir `Description` içeren bir `WarningInfo` nesnesi alır. `WarningType.FontSubstitution` üzerine filtreleme yaparak yalnızca ilgilendiğiniz olayları görürsünüz.
* `doc.Save` çağrısı, kütüphanenin tüm yazı tiplerini çözmesini zorlar ve bu da uyarıların tetiklenmesini sağlar. Sadece belgeyi incelemeniz gerekiyorsa, `doc.UpdatePageLayout()` çağrısını da kullanabilirsiniz.

**Beklenen konsol çıktısı** (eksik yazı tipi “Papyrus” ise):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

Bu satır, kütüphanenin **eksik yazı tiplerini tespit ettiğini** ve bir yedek seçtiğini kanıtlar.

---

## ## Render Etmeden Önce Eksik Yazı Tiplerini Tespit Etme

Bazen bir gereksinim yazı tipi eksikse süreci tamamen durdurmak isteyebilirsiniz—örneğin marka yönergeleri tam tipografi talep ediyorsa. Uyarı işleyicisi, tüm eksik‑yazı tipi mesajlarını bir listeye toplayacak şekilde genişletilebilir, ardından bir karar verilir.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### “Eksik yazı tiplerini nasıl tespit ederim?” sorusuna yanıtı

* `missingFonts` listesi, her değişim olayının bir kaydı olarak görev yapar.
* `UpdatePageLayout` sonrasında listeyi inceleyebilir ve devam edip etmeyeceğinize, loglayacağınıza veya bir istisna fırlatacağınıza karar verebilirsiniz.
* Bu desen, uyarı sisteminin format‑bağımsız olması nedeniyle (PDF, HTML, resimler vb.) herhangi bir çıktı formatı için çalışır.

---

## ## İleri Düzey İpucu: Eksik Yazı Tiplerini Belirli Bir Yedekle Değiştirme

Kullanmanız gereken kurumsal bir yazı tipiniz varsa, Aspose.Words’e eksik bir yazı tipiyle karşılaştığında otomatik olarak sizin yedek yazı tipinizi kullanmasını söyleyebilirsiniz. Bu, belgenin manuel işlem gerektirmeden hâlâ kabul edilebilir görünmesini istediğinizde çok işe yarar.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

Yukarıdaki kodu **belgeyi yüklemeden önce** yerleştirin. Artık eksik olan her yazı tipi—orijinal adı ne olursa olsun—“Calibri” (Calibri yoksa “Arial”) ile değiştirilecektir. Yine uyarı alırsınız, ancak belge sizin kontrol ettiğiniz yazı tipiyle render edilir.

---

## ## Yaygın Tuzaklar ve Kaçınma Yöntemleri

| Tuzak | Neden Oluşur | Çözüm |
|---------|----------------|-----|
| **Uyarılar ilk çağrıdan sonra kaybolur** | Statik `DefaultWarningHandler` daha sonra uygulamada üzerine yazılır. | İşleyiciyi **uygulama başlangıcında bir kez** ayarlayın veya bir referans saklayıp gerektiğinde yeniden atayın. |
| **Sadece ilk eksik yazı tipi raporlanır** | Bazı API’ler uyarıları toplu gönderir; kuyruğu boşaltmak için `UpdatePageLayout` veya `Save` çağırmanız gerekir. | Layout güncellemesi yapın veya üretmek istediğiniz formatta kaydedin. |
| **İptal ettikten sonra hâlâ değişim gerçekleşir** | Uyarı işleyicisi, değişim zaten gerçekleştikten sonra çalışır. | İşleyicide **loglayın** ve ardından bir istisna fırlatarak daha fazla işleme engel olun. |
| **Linux konteynerlerinde eksik yazı tipleri** | Linux, Windows yazı tipi kataloğuna sahip değildir, bu da çok sayıda değişime yol açar. | Gerekli yazı tiplerini konteynere monte edin veya `FontSettings.SetFontsFolder` ile özel bir yazı tipi dizini gösterin. |

---

## ## Web API Senaryosunda Yazı Tipi Değişimini Tespit Etme

ASP.NET Core üzerinden belge hizmeti sunuyorsanız, konsola yazmak yerine uyarıları toplayıp HTTP yanıtının bir parçası olarak döndürmek isteyebilirsiniz.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

Artık API, **eksik yazı tiplerini tespit eder** ve PDF oluşturulmadan önce net bir JSON yükü döndürür. Bu, üretim‑düzeyinde bir serviste “eksik yazı tiplerini nasıl tespit ederim?” sorusunun pratik bir örneğidir.

---

## ## Uygulamanızı Test Etme

1. **Test DOCX’i oluşturun**; içinde makinede bulunmayan bir yazı tipine (ör. “Comic Sans MS”) başvursun (minimal Docker imajı gibi).  
2. Konsol uygulamasını veya API uç noktasını çalıştırın.  
3. Konsol (veya HTTP yanıtı) değişim uyarısını listeliyor mu kontrol edin.  
4. İsterseniz oluşan PDF’i açıp yazı tipi özelliklerini inceleyin—Aspose.Words, yapılandırdığınız yedek yazı tipini göstermelidir.

Uyarıyı gördünüz ama PDF hâlâ beklenmedik bir yazı tipi kullanıyorsa, `SubstitutionSettings` sırasını tekrar kontrol edin; ilk eşleşme kazanır.

---

## ## Sonuç

Aspose.Words’te **yazı tipi değişimini** yönetmek için bir uyarı işleyicisi kaydetmekten, programatik olarak **eksik yazı tiplerini tespit etmeye** ve hatta bunları kurumsal bir yazı tipiyle değiştirmeye kadar ihtiyacınız olan her şeyi ele aldık. Yerleşik uyarı sistemine bağlanarak her “yazı tipi bulunamadı” olayını tam olarak görebilir, bu da geliştiricilerin belge üretiminde sıkça sorduğu “**eksik yazı tiplerini nasıl tespit ederim**?” sorusuna doğrudan yanıt verir.

Sırada ne var? Bu mantığı **dinamik yazı tipi yükleme** (`FontSettings.SetFontsFolder`) ile birleştirerek kullanıcı‑yüklemeli yazı tiplerini anlık destekleyebilir ya da uyarı işleyicisini Serilog gibi merkezi bir günlük hizmetine kayıt yapacak şekilde genişletebilirsiniz. Font yönetimini ne kadar çok izlerseniz, belge hattınız o kadar güvenilir olur.

Zor bir yazı tipi‑değişim senaryonuz mu var? Aşağıya yorum bırakın, birlikte çözümleyelim. İyi kodlamalar!

## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakın konuları kapsayan kaynaklardır. Her biri, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımları keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım‑adım açıklamalar içerir.

- [Aspose.Words’te Yazı Tiplerini Algılamak – Uyarıları ve Ayarları Yönetme](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Aspose.Words’te Yazı Tipi Değişim Uyarılarını Etkinleştirme – Tam Kılavuz](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [DOCX Yükleyip Eksik Yazı Tiplerini Tespit Etme – Tam C# Kılavuzu](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}