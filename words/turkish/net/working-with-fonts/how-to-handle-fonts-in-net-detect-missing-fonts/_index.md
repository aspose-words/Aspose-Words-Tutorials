---
category: general
date: 2026-06-02
description: .NET’te yazı tiplerini nasıl yönetilir – eksik yazı tiplerini tespit
  edin ve LoadOptions ile FontSettings kullanarak yazı tipi değişikliklerini izleyin.
  Tam, çalıştırılabilir bir çözüm öğrenin.
draft: false
keywords:
- how to handle fonts
- detect missing fonts
- track font changes
language: tr
og_description: .NET'te yazı tiplerini nasıl yöneteceğinizi öğrenin – eksik yazı tiplerini
  tespit edin ve yazı tipi değişikliklerini izleyin. Tam ve çalıştırmaya hazır bir
  çözüm için bu adım adım rehberi izleyin.
og_title: .NET'te fontları nasıl yönetilir – eksik fontları tespit et
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: how to handle fonts in .NET – detect missing fonts and track font changes
    using LoadOptions and FontSettings. Learn a complete, runnable solution.
  headline: how to handle fonts in .NET – detect missing fonts
  type: TechArticle
tags:
- .NET
- Aspose.Words
- FontSettings
title: .NET'te yazı tiplerini nasıl yönetilir – eksik yazı tiplerini tespit et
url: /tr/net/working-with-fonts/how-to-handle-fonts-in-net-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# .NET’te Yazı Tiplerini Nasıl Yönetilir – Eksik Yazı Tiplerini Algılamak

Bir Word belgesi, makinede yüklü olmayan bir yazı tipine başvurduğunda **yazı tiplerini nasıl yönetirsiniz** diye hiç merak ettiniz mi? Tek başınıza değilsiniz. Eksik yazı tipleri, cilalı bir raporu karışık bir hâle getirebilir ve uygun uyarılar olmadan neyin değiştiğini asla öğrenemeyebilirsiniz.  

Bu öğreticide, **yazı tiplerini nasıl yönetirsiniz** sorusunu eksik yazı tiplerini **algılayarak** ve çalışma zamanında yazı tipi değişikliklerini izleyerek tam olarak göstereceğiz. Sonunda, her bir değişimi kaydeden bağımsız bir konsol uygulamanız olacak; böylece Times New Roman olması gereken yerde gizemli bir Helvetica ile şaşırmayacaksınız.

> **Neler elde edeceksiniz:** kopyala‑yapıştır‑hazır bir kod örneği, her satırın açıklaması, gerçek dünya projeleri için ipuçları ve karşılaşabileceğiniz uç durumların hızlı bir incelemesi.

## Ön Koşullar

- .NET 6.0 veya üzeri (örnek, kısalık açısından üst‑seviye bir `Program.cs` kullanıyor)  
- Aspose.Words for .NET 23.9 veya daha yeni bir sürüm – `dotnet add package Aspose.Words` komutuyla NuGet’ten alabilirsiniz  
- Bilerek eksik bir yazı tipine başvuran bir Word belgesi (ör. `MissingFont.docx`)  

Başka bir kütüphane gerekmez.

![Diagram showing how the LoadOptions flow into FontSettings and the substitution warning event – how to handle fonts in .NET example](https://example.com/images/font‑handling‑flow.png "how to handle fonts in .NET example")

## Adım 1: FontSettings ile LoadOptions Ayarlayın  

İlk olarak, Aspose.Words’un yazı tipi sorunlarını izlemesini sağlayan bir `LoadOptions` nesnesine ihtiyacımız var.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

// Create LoadOptions and attach a fresh FontSettings instance.
var loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

**Neden önemli:** `LoadOptions`, bir belge diskte okunurken kapıyı kontrol eder. Özel bir `FontSettings` sağlayarak, yalnızca **eksik yazı tiplerini algılamak** için iç font‑çözümleme motoruna bir kanca eklemiş oluruz.

## Adım 2: SubstitutionWarning Olayına Abone Olun  

Aspose.Words, istediğiniz tam yazı tipini bulamadığında bir `SubstitutionWarning` olayı tetikler. Detayları loglayacağız, böylece hangi yazı tiplerinin istendiğini ve hangi yazı tiplerinin gerçekten kullanıldığını görebileceksiniz.

```csharp
// Hook into the warning event – this is where we “track font changes”.
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.RequestedFontName – the name the document asked for.
    // e.SubstitutedFontName – the name Aspose.Words fell back to.
    // e.WarningType – tells you why the substitution happened.
    Console.WriteLine(
        $"[Font Substitution] Requested: {e.RequestedFontName}, " +
        $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
};
```

**Neden dinliyoruz:** Bu dinleyici olmadan bir ikame gerçekleştiğini asla bilemezsiniz. Olay, “yazı tipi değişikliklerini izleme” gereksinimini karşılayan tam bir denetim izi sağlar.

## Adım 3: Belgeyi Yapılandırılmış Seçeneklerimizle Yükleyin  

Şimdi dosyayı gerçekten okuyacağız. `loadOptions`’ı geçirdiğimiz için Aspose.Words, karşılaştığı her eksik yazı tipi için uyarı olayını tetikleyecek.

```csharp
// Replace the path with the location of your test document.
string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

Document doc = new Document(docPath, loadOptions);
```

Hepsi bu – belge artık yüklendi ve tüm yazı tipi sorunları zaten konsola yazdırıldı.

## Adım 4: (İsteğe Bağlı) Belgedeki İkame Edilen Yazı Tiplerini Doğrulayın  

Son PDF ya da DOCX’te hangi yazı tiplerinin sonlandığını iki kez kontrol etmek isterseniz, belgenin yazı tipi koleksiyonunu gezebilirsiniz:

```csharp
Console.WriteLine("\n--- Fonts actually used in the document ---");
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
}
```

Yüklemeden hemen sonra çalıştırmak, motorun gömmeye ya da referans vermeye karar verdiği her yazı tipini listeler. QA ekipleri için rapor oluştururken çok işe yarar.

## Tam Çalışan Örnek  

Aşağıdaki bloğu yeni bir konsol projesine (`dotnet new console`) kopyalayın ve çalıştırın. Program her ikamayı ve ardından yüklemeden sonra hayatta kalan yazı tiplerini listeleyecek.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions with FontSettings.
        // -------------------------------------------------
        var loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Step 2: Hook the substitution warning event.
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"[Font Substitution] Requested: {e.RequestedFontName}, " +
                $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
        };

        // -------------------------------------------------
        // Step 3: Load the document (this triggers warnings).
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // Step 4 (optional): List fonts actually used.
        // -------------------------------------------------
        Console.WriteLine("\n--- Fonts actually used in the document ---");
        foreach (FontInfo fontInfo in doc.FontInfos)
        {
            Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
        }

        Console.WriteLine("\nDone. Press any key to exit.");
        Console.ReadKey();
    }
}
```

### Beklenen Çıktı  

`MissingFont.docx` “Comic Sans MS” (yüklü olmayan) isterse, aşağıdakine benzer bir şey görürsünüz:

```
[Font Substitution] Requested: Comic Sans MS, Used: Arial, Reason: FontNotFound
[Font Substitution] Requested: Times New Roman, Used: Times New Roman, Reason: None

--- Fonts actually used in the document ---
Arial – Regular
Times New Roman – Regular
```

İlk satır **eksik yazı tiplerini algıladığımızı** ve **yazı tipi değişikliklerini izlediğimizi** kanıtlar. İkinci satır, gerçekleşmemesi gereken bir ikameyi (yazı tipi mevcut olduğu için uyarı yok) gösterir.

## Yaygın Tuzaklar ve Profesyonel İpuçları  

| Sorun | Ne Olur | Nasıl Düzeltir / Kaçınılır |
|---------|--------------|--------------------|
| **Uyarı olayları tetiklenmiyor** | API’nın bozuk olduğunu düşünebilirsiniz. | `FontSettings`’i `LoadOptions`’a **belgeyi yüklemeden önce** atadığınızdan emin olun. Olay kancası **`new Document(...)` çağrısından önce** eklenmelidir. |
| **İkame edilen yazı tipleri hâlâ hatalı görünüyor** | Aspose.Words, stil ile eşleşmeyen genel bir yazı tipine geri dönüyor. | `fontSettings.SetFontsFolder(@"C:\MyFonts", true)` ile özel bir yazı tipi klasörü sağlayın. Bu, motorun genel bir yazı tipine geçmeden önce daha fazla seçenek bulmasını sağlar. |
| **Büyük belgelerde performans düşüşü** | Her yazı tipinin taranması birkaç milisaniye ekleyebilir. | Birden çok belgeyi art arda yüklüyorsanız `FontSettings` nesnesini önbelleğe alın. Aynı örneği yeniden kullanmak, sistem font tablolarını yeniden okumayı önler. |
| **Konsol çıktısı GUI uygulamalarda kayboluyor** | Uyarıları göremezsiniz. | Olayı bir logger’a (ör. `Serilog`) yönlendirin ya da bir dosyaya yazın: `File.AppendAllText("font-warnings.log", …)`. |

## Çözümü Genişletmek  

- **PDF’ye gömülü yazı tipleriyle dışa aktar** – yüklemeden sonra `doc.Save("output.pdf", SaveOptions.CreateSaveOptions(SaveFormat.Pdf));` çağırın ve `PdfSaveOptions.FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll;` ayarını yaptığınızdan emin olun.  
- **Toplu işleme** – yükleme mantığını bir klasördeki DOCX dosyaları üzerinde `foreach` ile sarın. Her dosyanın uyarılarını denetim amaçlı bir CSV’ye kaydedin.  
- **Kullanıcı dostu UI** – aynı mantığı bir WinForms/WPF uygulamasındaki bir butona bağlayın, uyarıları bir `ListBox` içinde gösterin.

## Sonuç  

`LoadOptions` yapılandırarak, `SubstitutionWarning` olayına abone olarak ve ardından belgeyi yükleyerek **.NET’te yazı tiplerini nasıl yönetirsiniz** sorusunu adım adım gösterdik. Örnek, sadece **eksik yazı tiplerini algılamak**la kalmayıp aynı zamanda **yazı tipi değişikliklerini izlemek** için de tam bir denetim sunar.  

Kendi belgelerinizle deneyin, yazı tipi klasör yolunu ayarlayın ve bir daha beklenmedik bir yazı tipi ikamesiyle şaşırmayın. Bu rehberi faydalı bulduysanız, *“Aspose.Words ile PDF’ye özel yazı tipleri gömme”* ya da *“.NET çok platformlu uygulamalar için yazı tipi geri dönüş stratejisi oluşturma”* gibi ilgili konuları keşfetmeyi düşünün.  

İyi kodlamalar, ve belgeleriniz her zaman istediğiniz gibi render olsun!

## Sonra Ne Öğrenmelisiniz?


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [DOCX Yükleme ve Eksik Yazı Tiplerini Algılama – Tam C# Kılavuzu](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Aspose.Words’ta Yazı Tiplerini Algılamak – Uyarıları ve Ayarları Yönetmek](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Aspose.Words’ta LoadOptions Kullanımı – Tam Kılavuz](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}