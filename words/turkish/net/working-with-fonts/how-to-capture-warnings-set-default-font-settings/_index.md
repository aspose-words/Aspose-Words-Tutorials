---
category: general
date: 2026-03-19
description: Aspose.Words'ta uyarıları yakalamayı, varsayılan yazı tipi ayarlarını
  belirlemeyi ve bir Word belgesi yüklerken eksik yazı tiplerini tespit etmeyi öğrenin.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: tr
og_description: Aspose.Words'ta uyarıları yakalama, varsayılan yazı tipi ayarlarını
  belirleme ve bir Word belgesi yüklerken eksik yazı tiplerini tespit etme.
og_title: Uyarıları Yakalama – Varsayılan Yazı Tipi Ayarlarını Belirleme
tags:
- Aspose.Words
- C#
- Document Processing
title: Uyarıları Yakalama – Varsayılan Yazı Tipi Ayarlarını Belirleme
url: /tr/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uyarıları Yakalama – Varsayılan Yazı Tipi Ayarlarını Belirleme

**How to capture warnings** Aspose.Words ile çalışırken yaygın bir ihtiyaçtır, özellikle belgeleriniz belirli yazı tiplerine dayanıyorsa ve bu yazı tipleri hedef makinede bulunmayabilir. Hiç bir DOCX açıp düzenin neden bozuk göründüğünü merak ettiniz mi? Cevap genellikle eksik bir yazı tipiyle ilgili bir uyarının içinde gizlidir.  

Bu rehberde **how to capture warnings** sırasında **load word document** işlemini yaparken, **set default font settings** yapılandırmasını ve sonunda **detect missing fonts** işlemini gerçekleştirerek programatik olarak yanıt verebilirsiniz. Gereksiz ayrıntı yok—sadece eksiksiz, çalıştırılabilir bir örnek ve her satırın mantığı.

> *İpucu:* Uyarıları erken yakalamak, daha sonra gizemli düzen hatalarını ayıklamaktan sizi kurtarır.

---

## İhtiyacınız Olanlar

- **Aspose.Words for .NET** (2026 itibarıyla en son sürüm).  
- Bir .NET geliştirme ortamı (Visual Studio, Rider veya VS Code).  
- Yüklü olmayan bir yazı tipine referans veren örnek bir DOCX (ör. Linux makinede *Comic Sans MS*).  

Hepsi bu. Aspose.Words dışındaki ek NuGet paketlerine gerek yok.

---

## Adım 1 – Neden Uyarıları Yakalamanız Gerektiğini Anlayın

Aspose.Words bir belgeyi ayrıştırdığında, ana bilgisayarda bulunmayan yazı tipleriyle karşılaşabilir. Varsayılan olarak kütüphane sessizce bir yedek yazı tipi kullanır; bu, satır sonlarını, boşlukları değiştirebilir ve hatta metnin kaybolmasına neden olabilir.  

**WarningCallback** ile **FontSettings** nesnesini birlikte kullanmak size iki şey sağlar:

1. **Visibility** – her bir ikame için bir `WarningInfo` girdisi alırsınız.  
2. **Control** – görsel sürprizleri en aza indirmek için varsayılan bir yazı tipini önceden yapılandırabilirsiniz.  

Bunu, motorun kapağı altında bir parçayı değiştirdiğinde bağıran bir “watchdog” (gözetleyici) kurmak gibi düşünün.

---

## Adım 2 – Varsayılan Yazı Tipi Ayarlarını Belirleme

İlk ikincil anahtar kelime, **set default font settings**, burada ortaya çıkıyor. Bir `FontSettings` örneği oluşturur ve isteğe bağlı olarak yedek yazı tiplerinizi içeren bir klasöre işaret edersiniz.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Neden?**  
> Bir yedek belirtmezseniz, Aspose.Words stili eşleşen ilk sistem yazı tipini seçer; bu çok farklı olabilir. Bilinen bir varsayılan ayarlayarak, makineler arasında tutarlı render almayı garantilersiniz.

---

## Adım 3 – Uyarıları Yakalamak İçin Bir Warning Callback Hazırlayın

Şimdi **how to capture warnings** işlemini, `WarningInfoCollection`'ı yükleme seçeneklerine ekleyerek yapacağız. Bu koleksiyon, yükleme sürecinde ortaya çıkan tüm uyarıları saklayacak.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

`WarningInfoCollection` `IWarningCallback` arayüzünü uygular, bu yüzden Aspose.Words otomatik olarak her uyarıyı `warningInfos` içine gönderir. Anket (polling) gerekmez.

---

## Adım 4 – Yapılandırılmış Seçeneklerle Word Belgesini Yükleyin

İşte ikinci ikincil anahtar kelime, **load word document**, parladığı yer. `FontSettings` ve `WarningCallback`'i bir `LoadOptions` örneği aracılığıyla geçiririz.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Belge yüklü olmayan bir yazı tipine referans veriyorsa, uyarı geri çağrısı bir `WarningType.FontSubstitution` girdisini yakalar.

---

## Adım 5 – Toplanan Uyarılardan Eksik Yazı Tiplerini Tespit Edin

Son olarak, topladığımız uyarıları döngüyle işleyerek üçüncü ikincil anahtar kelime olan **detect missing fonts** sorusuna yanıt veriyoruz.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Tipik çıktı şu şekildedir:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Bu satır, hangi yazı tipinin eksik olduğunu ve hangi yedek yazı tipinin kullanıldığını tam olarak gösterir—bu bilgiyi kaydedebilir, kullanıcıya gösterebilir veya hatta özel bir yazı tipi kurulum rutinini tetikleyebilirsiniz.

---

## Tam Çalıştırılabilir Örnek

Aşağıda, bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz tam program bulunmaktadır. Bu program **how to capture warnings**, **set default font settings**, **load word document** ve **detect missing fonts** işlemlerini tek bir akışta gösterir.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Beklenen sonuç:** Belirtilen DOCX yüklü olmayan bir yazı tipine referans veriyorsa, konsol her ikame için bir uyarı yazdırır. Tüm yazı tipleri yüklüyse, döngü hiçbir çıktı üretmez.

---

## Yaygın Tuzaklar ve Kenar Durumları

| Durum | Neden Oluşur | Nasıl Ele Alınır |
|-----------|----------------|------------------|
| **Uyarı çıkmaz** ancak düzen yanlış görünüyor | Belge *gömülü* yazı tipleri kullanıyor olabilir; Aspose.Words bunları ikame etmeden render eder. | `Document.HasEmbeddedFonts` kontrol edin ve gerekirse gömülü yazı tiplerini başka bir makinede kullanmak için çıkarın. |
| **Multiple warnings for the

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}