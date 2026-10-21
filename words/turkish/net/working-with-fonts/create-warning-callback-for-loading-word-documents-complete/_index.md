---
category: general
date: 2026-03-25
description: Word belgesini yüklemek ve eksik yazı tiplerini tespit etmek için uyarı
  geri aramasını oluşturun. Aspose.Words for .NET’te yazı tipi ayarlarını nasıl yapılandıracağınızı
  öğrenin.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: tr
og_description: Eksik yazı tiplerini tespit ederken Word belgesini yüklemek için uyarı
  geri çağrısı oluşturun. Bu kılavuz, Aspose.Words'ta yazı tipi ayarlarını nasıl yapılandıracağınızı
  gösterir.
og_title: Uyarı geri çağrısı oluştur – Word belgesini yükle ve eksik yazı tiplerini
  tespit et
tags:
- Aspose.Words
- C#
- Font handling
title: Word belgelerini yüklerken uyarı geri çağrısı oluşturma – Tam Kılavuz
url: /tr/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uyarı geri araması oluştur – Word belgesi yükle & eksik yazı tiplerini tespit et

Hiç **uyarı geri araması oluşturma** ihtiyacı hissettiniz mi ve bazı yazı tiplerinin neden aniden kaybolduğunu merak ettiniz mi? Tek başınıza değilsiniz. Birçok kurumsal uygulamada eksik yazı tipleri düzen felaketlerine yol açar ve uygun bir geri arama olmadan sorunu fark etmeyebilirsiniz.  

İyi haber? Aspose.Words for .NET ile **Word belgesi yükleyebilir**, **eksik yazı tiplerini tespit edebilir** ve **yazı tipi ayarlarını yapılandırabilirsiniz**; hepsi birkaç temiz kod satırıyla. Bu öğreticide tam, çalıştırılabilir bir örnek üzerinden geçecek, her parçanın neden önemli olduğunu açıklayacak ve uyarı geri aramasının görevini nasıl yerine getirdiğini nasıl doğrulayacağınızı göstereceğiz.

> **Ne kazanacaksınız**  
> * DOCX dosyasını yükleyen, herhangi bir yazı tipi ikamesini raporlayan ve yazı tipi arama yollarını özelleştirmenizi sağlayan tam bir C# programı.  
> * `FontSettings`, `LoadOptions` ve `IWarningCallback` sınıflarının anlaşılması.  
> * Gömülü yazı tipleri veya sistem genelindeki yazı tipi klasörleri gibi uç durumları ele alma ipuçları.

---

## Önkoşullar

- .NET 6+ (veya .NET Framework 4.7.2+) ve bir C# derleyicisi.  
- Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`).  
- En az bir yazı tipi makinede yüklü olmayan bir örnek Word dosyası (`input.docx`) (ör. minimal Windows konteynerinde *Calibri Light*).  
- C# konsol uygulamaları hakkında temel bilgi.

Ek bir kütüphane gerekmez; her şey Aspose.Words içinde bulunur.

---

## Adım 1: Eksik yazı tiplerini tespit etmek için uyarı geri araması oluşturun

Bu bulmacanın **ana** parçası, `IWarningCallback` arayüzünü uygulayan bir sınıftır. Aspose.Words, bir uyarı gerektiren bir durumla karşılaştığında – en yaygın olanı yazı tipi ikamesi – bu geri aramayı tetikler.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Neden önemli** – Bir geri arama olmadan, logları sonradan incelemek zorunda kalırsınız. Uyarıları gerçek zamanlı işleyerek yüklemeyi iptal etmeye, eksik yazı tipini bir yedekle değiştirmeye ya da sorunu daha sonra gözden geçirmek için kaydetmeye karar verebilirsiniz.

---

## Adım 2: Özel yazı tipi işleme için FontSettings’i yapılandırın

Belgeyi gerçekten yüklemeden önce, sistemde bulunmayan yazı tiplerini Aspose.Words’un nerede arayacağını söylemek isteyebiliriz. İşte `FontSettings` burada devreye girer.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Neden önemli** – Eksik yazı tiplerini içeren bir klasöre işaret ederek ikameleri çoğu zaman önleyebilirsiniz. Bu mümkün olmadığında, mantıklı bir varsayılan (ör. *Arial*) belgenin okunabilirliğini korur.

---

## Adım 3: Yapılandırılmış uyarı geri aramasıyla Word belgesini yükleyin

Şimdi her şeyi bir araya getiriyoruz: `LoadOptions` oluşturuyor, `FontSettings` ve `FontWarningHandler`’ı takıyor ve sonunda belgeyi yüklüyoruz.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Neden önemli** – `LoadOptions`, bir belgenin *nasıl* okunacağını yapılandırdığınız tek yerdir. Hem yazı tipi yapılandırmasını hem de uyarı geri aramasını sağlayarak eksik bir yazı tipinin doğru yerlerde aranmasını **ve** anında raporlanmasını garantileriz.

---

## Adım 4: Çıktıyı doğrulayın – ne görmelisiniz?

Programı bir konsoldan çalıştırın. `input.docx` yüklü olmayan ve ayrıca `C:\SharedFonts` içinde de bulunmayan bir yazı tipi kullanıyorsa, aşağıdakine benzer bir çıktı alırsınız:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Tüm yazı tipleri mevcutsa, uyarı satırı hiç görünmez. Bu anlık geri bildirim döngüsü, sessiz yazı tipi değişimlerinin marka yönergelerini bozabileceği otomatik belge işleme hatlarında paha biçilmezdir.

---

## Adım 5: Yaygın tuzaklar ve en iyi uygulama ipuçları

| Tuzak | Nasıl önlenir |
|---------|-----------------|
| **`Aspose.Words.Fonts` referansı eklenmemiş** | Dosyanın en üstüne `using Aspose.Words.Fonts;` eklediğinizden emin olun; aksi takdirde derleyici eksik tipler hakkında şikayet eder. |
| **Yazı tipi klasör yolu hatalı** | Yolu iki kez kontrol edin ve alt klasörleriniz varsa `recursive: true` ayarlayın. Hata ayıklamak için `Path.GetFullPath` kullanın. |
| **Birden fazla uyarı geri araması** | Aspose.Words yalnızca atanan son `WarningCallback`’i dikkate alır. Daha karmaşık bir mantık gerekiyorsa, tek bir işleyici içinde delegasyon yapın. |
| **UI’siz bir sunucuda çalıştırma** | Konsol yazıları yeterli, ancak web uygulamaları için `Console.WriteLine` yerine bir dosyaya ya da izleme sistemine loglamayı tercih edebilirsiniz. |
| **Büyük belgeler performans düşüşüne neden olur** | Birden çok yükleme için aynı `FontSettings` örneğini yeniden kullanın; tekrar tekrar oluşturmak maliyetli olabilir. |

**Pro ipucu:** Uyarıları daha sonra analiz etmek için toplamanız gerekiyorsa, işleyicide doğrudan yazdırmak yerine `List<string>` içinde saklayın.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Daha sonra belge yüklendikten `handler.Messages` koleksiyonunu inceleyebilirsiniz.

---

## Adım 6: Çözümü genişletmek – yedek bir yazı tipi gömmem gerekse ne olur?

Bazen eksik yazı tipinin çıktıda PDF’e *gömülmesini* istersiniz, böylece sonraki görüntüleyiciler tam görünümü görür. Belgeyi yükledikten sonra gömme zorlayabilirsiniz:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Bu snippet, aynı **yazı tipi ayarlarını yapılandırma** yaklaşımının yalnızca yükleme aşamasının ötesine nasıl genişletilebileceğini gösterir.

---

## Tam çalıştırılabilir örnek

Aşağıda yeni bir Console App projesine kopyalayıp yapıştırabileceğiniz tam program yer alıyor. Yukarıda tartıştığımız tüm parçalar dahildir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Beklenen çıktı** (eksik bir yazı tipi mevcutsa):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

İkame gerçekleşmezse, yalnızca başarı mesajları görünür.

---

## Sonuç

**Uyarı geri araması** oluşturarak **Word belgesi yüklenirken eksik yazı tiplerini güvenilir bir şekilde tespit ettik**, ayrıca **yazı tipi ayarlarını** yapılandırarak kütüphanenin yazı tiplerini nerede arayacağını ve hangi yedek yazı tipini kullanacağını kontrol ettik. `FontSettings` ve `LoadOptions`’ı birleştirerek yazı tipiyle ilgili sorunlara tam görünürlük kazandınız—artık sessiz düzen bozulmaları yok.

Sonraki adımlar? `FontWarningHandler`’ı bir veritabanına yazan bir logger ile değiştirin ya da **yazı tipi ikame kuralları**yla belirli eksik yazı tiplerini marka‑onaylı alternatiflere eşleyin. Uygulamanız konteyner ortamında çalışıyorsa **bulut depolamadan dinamik yazı tipi yükleme**yi de keşfedebilirsiniz.

Belirli bir uç durum hakkında sorularınız var mı—ör. OpenType özelliklerini işleme ya da şifreli DOCX dosyalarıyla başa çıkma? Aşağıya yorum bırakın, kodlamanın tadını çıkarın!  

---

![Uyarı geri araması diyagramı](https://example.com/images/create-warning-callback.png "Uyarı geri araması diyagramı")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}