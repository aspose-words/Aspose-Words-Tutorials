---
category: general
date: 2026-02-10
description: Aspose.Words'ta varsayılan yazı tipini yapılandırırken ve varsayılan
  içe aktarma yazı tipini ayarlarken yazı tipi değişikliklerini izlemek için uyarı
  geri çağrısını ayarlayın. Tam adım adım çözümü öğrenin.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: tr
og_description: Varsayılan yazı tipini yapılandırırken ve varsayılan içe aktarma yazı
  tipini ayarlarken yazı tipi değişikliklerini izlemek için uyarı geri çağrısını ayarlayın.
  Aspose.Words için tam öğreticiyi izleyin.
og_title: C#'ta uyarı geri çağrısını ayarlama – Tam Kılavuz
tags:
- Aspose.Words
- C#
- Document Import
title: C#'ta uyarı geri çağrısını ayarla – Yazı Tipi İşleme İçin Tam Kılavuz
url: /tr/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

CODE_BLOCK_0}} etc. Keep them.

Check for shortcodes: at top and bottom. Keep them.

Now produce final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta Uyarı Geri Çağrısını Ayarlama – Yazı Tipi İşleme İçin Tam Kılavuz

Bir Word belgesi yüklerken **set warning callback**'i ayarlamanız gerektiğinde ve aynı anda *configure default font*'u nasıl yapacağınızı merak ettiğiniz oldu mu? Yalnız değilsiniz. Otomatik rapor oluşturucular veya belge dönüştürme hatları gibi birçok gerçek‑dünya projesinde eksik yazı tipleri sessizce düzeni bozabilir ve bu sorunları yakalamanın tek yolu, bir uyarı geri çağrısı aracılığıyla **monitor font changes** yapmaktır.

Bu öğreticide, Aspose.Words for .NET kullanarak **set warning callback**, **configure default font** ve hatta **set default import font** nasıl yapılacağını gösteren uygulamalı bir örnek üzerinden ilerleyeceğiz. Sonuna kadar çalıştırmaya hazır bir kod parçacığına sahip olacak, her parçanın neden önemli olduğunu anlayacak ve özel yazı tipi klasörleri veya sessiz ikameler gibi uç durumlara nasıl uyarlayacağınızı öğreneceksiniz.

---

## Önkoşullar

- .NET 6.0 veya daha yenisi (kod .NET Framework 4.6+ üzerinde de çalışır)  
- Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`)  
- Kullanmak istediğiniz yedek yazı tipini içeren bir klasör (ör. `fonts/Arial.ttf`)  
- C# konsol uygulamaları hakkında temel bilgi  

Ek bir kütüphane gerekmemektedir.

---

## Adım 1: LoadOptions Oluşturun ve **configure default font**'u ayarlayın

Yazı tipi işleme kontrolünü sağlamak istediğinizde ilk yapmanız gereken bir `LoadOptions` örneği oluşturmaktır. Bu nesne, Aspose.Words'e içe aktarım sırasında eksik yazı tiplerini nasıl ele alacağını söyler.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Neden Önemlidir:**  
Kaynak belge, sunucuda yüklü olmayan bir yazı tipine referans veriyorsa, Aspose.Words sağladığınız klasöre bakar. Bu, **set default import font**'un özüdür—herhangi bir uyarı verilmeden önce kütüphaneye bir ikame bulmasını açıkça söylüyorsunuz.

---

## Adım 2: **Set warning callback**'i **monitor font changes** için ayarlayın

Aspose.Words, bir yazı tipini ikame etmek zorunda kaldığında (ve diğer durumlarda) bir `WarningInfoCollection` yayar. Bir işleyici ekleyerek, her ikameyi kaydedebilir veya ona yanıt verebilirsiniz.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Neden Önemlidir:**  
Sadece **configure default font** yeterli değildir; hangi yazı tiplerinin gerçekten değiştirildiğini denetlemeniz gerekiyorsa. Geri çağrı size gerçek zamanlı bir günlük sağlar, **monitor font changes** gereksinimini karşılar ve CI hattında beklenmeyen ikameleri erken yakalamanıza yardımcı olur.

---

## Adım 3: Belgeyi Hazırlanan Seçeneklerle Yükleyin

Artık yükleme seçenekleri tamamen hazır olduğuna göre, herhangi bir `.docx` dosyasını güvenle yükleyebilirsiniz. Bir ikame gerçekleşirse geri çağrı otomatik olarak tetiklenir.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**Gördükleriniz:**  
Kaynak, mevcut olmayan bir yazı tipi kullanıyorsa, konsol şu benzeri bir şey yazdırır:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Bu çıktı, **set warning callback**'i başarıyla ayarladığınızı ve **default import font**'un etkili olduğunu doğrular.

---

## Adım 4: (İsteğe Bağlı) Yazı Tipi İkame Davranışını İnce Ayar Yapın

Bazen, orijinal isteğe bakılmaksızın *tüm* eksik yazı tiplerini tek bir aileyle değiştirmek isteyebilirsiniz. Aspose.Words, global olarak bir *fallback font* ayarlamanıza izin verir.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**Ne Zaman Kullanılır:**  
Sadece sınırlı bir yazı tipi setine izin veren bir marka için PDF'ler üretiyorsanız, bu kaynak belgenin egzotik bir şey kullanmaya çalışsa bile her belge arasında tutarlılık sağlar.

---

## Adım 5: Belgeyi Kaydedin veya Daha Fazla İşleyin

Yüklemeden sonra, ihtiyacınız olan herhangi bir işleme devam edebilirsiniz—düzenleme, PDF'ye dönüştürme, metin çıkarma vb. İşte ikame edilen yazı tiplerini koruyarak belgeyi PDF olarak kaydetmeye dair hızlı bir örnek.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

Ortaya çıkan PDF, ikame gerçekleşen her yerde yedek yazı tipini gösterecek ve **set warning callback**'in beklendiği gibi çalıştığını görsel olarak doğrulayacaktır.

---

## Yaygın Tuzaklar ve Pro İpuçları

| Tuzak | Neden Olur | Çözüm |
|---------|----------------|-----|
| **Geri çağrı hiç tetiklenmiyor** | `LoadOptions.WarningCallback` belge yüklenmeden *önce* atanmadı. | Her zaman geri çağrıyı `new Document(...)` çağırmadan **önce** ekleyin. |
| **Yanlış yazı tipi klasörü** | Yol yazım hatası veya okuma izinlerinin eksik olması. | Klasörün varlığını ve uygulamanın `Read` erişimine sahip olduğunu doğrulayın. Güvenilirlik için mutlak yollar kullanın. |
| **Birden fazla ikame, gürültülü çıktı** | Birçok eksik yazı tipine sahip büyük belgeler. | `WarningType.FontSubstitution` (gösterildiği gibi) ile uyarıları filtreleyin veya konsol yerine bir günlük dosyasına yazın. |
| **Yedek yazı tipi uygulanmadı** | Yedek yazı tipi makinede yüklü değil. | `.ttf`/`.otf` dosyasını `SetFontsFolder`'a verdiğiniz klasöre yerleştirin. Aspose.Words doğrudan yükler, işletim sistemi kurulumu gerekmez. |

**Pro ipucu:** Bunu bir CI/CD hattında çalıştırırken, konsol çıktısını bir derleme artefaktına yönlendirin. Böylece derleme sırasında gerçekleşen her yazı tipi ikamesinin denetim izini elde edersiniz.

---

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

Aşağıda, yeni bir Console App projesine ekleyebileceğiniz tam program yer alıyor. Gerekli tüm adımları, using ifadelerini ve yorumları içerir.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Beklenen konsol çıktısı** (`Times New Roman` eksik olduğu varsayılırsa):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Programı çalıştırın, `output.pdf` dosyasını açın ve belgeyi gerektiği yerde yedek yazı tipiyle render edilmiş olarak göreceksiniz.

---

## Sonuç

Artık Aspose.Words ile çalışırken C#'ta **set warning callback**'i ayarlamak, **configure default font**, **monitor font changes** ve **set default import font** için sağlam, üretime hazır bir deseniniz var. Yüklemeden önce bir uyarı toplayıcı ekleyerek, `FontSettings`'i güvenilir bir yazı tipi klasörüne yönlendirerek ve isteğe bağlı olarak global bir yedek zorlayarak, yazı tipi ikamesi üzerinde tam görünürlük ve kontrol elde edersiniz—herhangi bir sağlam belge‑işleme hattının tam olarak ihtiyaç duyduğu şey.

Bir sonraki seviyeye hazır mısınız? Bu yaklaşımı şu şeylerle birleştirmeyi deneyin:

- **Dynamic font loading** veritabanından (runtime'da `FontSettings.SetFontsFolder` kullanın).  
- **Custom warning handlers** analiz için yapılandırılmış bir günlük (JSON veya CSV) yazan.  
- **Parallel document processing** her iş parçacığının kendi `LoadOptions`'ını alarak çapraz iletişimi önleyen.  

Denemekten çekinmeyin, kodu kendi mimarinize uyarlayın ve keşiflerinizi yorumlarda paylaşın. Kodlamanın tadını çıkarın!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}