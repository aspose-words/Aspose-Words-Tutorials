---
category: general
date: 2026-04-21
description: Aspose.Words ile C#’ta yazı tiplerini nasıl tespit edeceğinizi, uyarıları
  nasıl yakalayacağınızı, geri aramayı nasıl yapılandıracağınızı ve uyarıları nasıl
  listeleyeceğinizi öğrenin. Güvenilir yazı tipi yönetimi için adım adım rehber.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: tr
og_description: Aspose.Words'ta yazı tiplerini nasıl tespit edersiniz? Bu öğreticide,
  uyarıları nasıl yakalayacağınızı, bir geri aramayı (callback) nasıl yapılandıracağınızı
  ve C#'ta uyarıları nasıl listeleyeceğinizi gösteriyor.
og_title: Aspose.Words'ta Fontları Nasıl Algılayabilirsiniz – Tam Rehber
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Words'ta Yazı Tiplerini Nasıl Algılayabilirsiniz – Tam Rehber
url: /tr/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words’ta Yazı Tiplerini Nasıl Algılayabilirsiniz – Tam Kılavuz

Bir Word belgesi yüklendiğinde eksik olan **yazı tiplerini nasıl algılayacağınızı** hiç merak ettiniz mi? Bu, özellikle eski dosyalarla veya çapraz‑platform dağıtımlarıyla çalışırken sıkça karşılaşılan bir durum. Bu öğreticide, **uyarıları yakalama**, **geri çağırma (callback) yapılandırma** ve **uyarıları sıralama** adımlarını içeren, çalıştırılabilir tam bir örnek üzerinden ilerleyeceğiz; böylece hangi yazı tiplerinin değiştirildiğini her zaman bileceksiniz.

Aspose.Words for .NET (yazım anında v24.9) ve sade C# kullanacağız. Harici hizmet yok, sihir yok—sadece API ve birkaç satır kod. Sonuna geldiğinizde, her yazı tipi değişimini görebilecek, kaydedebilecek ve kritik bir yazı tipi eksikse yüklemeyi iptal etmeyi bile seçebileceksiniz.  

### Gereksinimler
- **Aspose.Words for .NET** (NuGet üzerinden kurun: `Install-Package Aspose.Words`)
- .NET 6.0 veya üzeri (kod .NET Framework’te de çalışır)
- Makinede bulunmayan bir yazı tipine referans veren örnek bir DOCX (ör. “MyCustomFont.ttf”)
- Visual Studio, Rider veya tercih ettiğiniz herhangi bir C# editörü

> **Pro ipucu:** Eksik yazı tipli bir belgeniz yoksa, sisteminizdeki bir yazı tipi dosyasının adını değiştirin ya da DOCX XML’ini düzenleyerek var olmayan bir yazı tipi ailesine referans verin.

---

## Aspose.Words ile Yazı Tiplerini Nasıl Algılayabilirsiniz

Temel fikir, Aspose.Words’ün uyarı sistemine takılmak. Kütüphane istenen bir yazı tipini bulamadığında `WarningType.FontSubstitution` uyarısı üretir. Özel bir `IWarningCallback` uygulayarak **yazı tiplerini** yükleme sırasında değiştirilenleri **algılayabilirsiniz**.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Neden işe yarıyor:** Aspose.Words, kritik olmayan her sorun için `Warning` metodunu çağırır. `WarningInfo` nesnelerini saklayarak, tür, mesaj ve bağlam gibi tüm bilgilere tam erişim elde edersiniz; bu da **değiştirilen yazı tiplerini** algılamak için tam olarak ihtiyacınız olan şeydir.

---

## Belge Yüklerken Uyarıları Nasıl Yakalarsınız

Artık bir toplayıcıya (collector) sahibiz, `LoadOptions`’a bunu kullanmasını söylememiz gerekiyor. İşte **uyarıları yakalama** kısmı.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Köşe durumu:** Belgeyi bir akıştan (`new Document(stream, loadOptions)`) yüklerseniz aynı geri çağırma (callback) çalışır—sadece dosya yolunu akışla değiştirin.

Bu noktada belge tamamen yüklendi, ancak tüm yazı tipi değişim uyarıları `warningCollector.Warnings` içinde güvenli bir şekilde saklandı.

---

## Uyarıları Nasıl Sıralar ve Yazı Tipi Değişimlerini Raporlarsınız

Son olarak, toplanan uyarılar üzerinden geçip **yazı tipi değişimi** ile ilgili olanları **sıralarız**. Bu adım ham veriyi okunabilir bir rapora dönüştürür.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Beklenen çıktı** (örnek):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Belge eksik bir yazı tipine sahip değilse, döngü hiçbir çıktı üretmez—endişelenecek bir şey yoktur.

---

## Tam Çalışan Örnek (Tüm Adımlar Tek Dosyada)

Aşağıda, bir konsol projesine kopyalayıp yapıştırabileceğiniz tam program yer alıyor. **Yazı tiplerini nasıl algılayacağınızı**, **uyarıları nasıl yakalayacağınızı**, **geri çağırmayı nasıl yapılandıracağınızı** ve **uyarıları nasıl sıralayacağınızı** tek bir akışta birleştirir.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Bu programı çalıştırdığınızda**, Aspose.Words’ün değiştirmek zorunda kaldığı her yazı tipini yazdırır. Çıktıyı bir log dosyasına yönlendirebilir, bir uyarı oluşturabilir ya da kritik bir yazı tipi eksikse yüklemeyi iptal edebilirsiniz.

---

## Yaygın Sorular & Dikkat Edilmesi Gerekenler

### Gerekli bir yazı tipi eksik olduğunda yüklemeyi durdurmam gerekirse ne yapmalıyım?
Geri çağırma (callback) içinde `WarningInfo` nesnelerini inceleyebilir ve belirli bir yazı tipi adı göründüğünde bir istisna fırlatabilirsiniz. İstisna, yüklemeyi durdurur ve tam kontrol sizde olur.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Bu PDF’ler veya diğer formatlarla da çalışır mı?
Evet. Aspose.Words, PDF, RTF ve HTML için aynı uyarı altyapısını kullanır. Sadece dosya uzantısını değiştirin, kodun geri kalanı aynı kalır.

### Uyarıları konsol yerine bir dosyaya nasıl kaydederim?
`Console.WriteLine` ifadesini tercih ettiğiniz herhangi bir kayıt (logging) çerçevesiyle (`Serilog`, `NLog` vb.) değiştirin. `WarningInfo` sınıfı, ayrıntılı loglar için `Message`, `Source` ve `Exception` özelliklerini sunar.

### Performansa etkisi olur mu?
Ek yük ihmal edilebilir—Aspose.Words zaten uyarıları dahili olarak üretir. Bir geri çağırma eklemek sadece uyarıları bir listeye saklar, bu da uyarı sayısına göre O(n) zaman alır. Tipik belgeler için etkisi toplam yük süresinin %1’inden çok daha azdır.

---

## Görsel Özet

![Aspose.Words’ta Yazı Tiplerini Nasıl Algılayabilirsiniz – uyarı akış diyagramı](https://example.com/images/font-detection-diagram.png "yazı tiplerini nasıl algılayabilirsiniz")

*Alt metin:* **yazı tiplerini nasıl algılayabilirsiniz** – uyarı geri çağırması, toplama ve sıralama adımlarını gösteren diyagram.

---

## Sonuç

Aspose.Words’te **yazı tiplerini nasıl algılayacağınızı**, **uyarıları yakalayarak**, **geri çağırma yapılandırarak** ve **uyarıları sıralayarak** ele aldık. Tam kod örneği, herhangi bir .NET uygulamasına ekleyebileceğiniz üretim‑hazır bir deseni gösteriyor.  

İleriye dönük olarak şunları keşfedebilirsiniz:

- **Diğer sorunlar** için uyarı yakalama (ör. görüntü dönüşüm problemleri)
- **Özel kayıt çerçeveleri** için geri çağırma yapılandırma
- **Toplu işlerde** birden çok belgeye uyarı sıralama
- **Aspose.Words.Fonts.FontSettings** kullanarak yedek yazı tipi klasörleri sağlama; bu, başlangıçta değişim sayısını azaltabilir.

Deneyin, toplayıcıyı log stilinize göre uyarlayın ve bir daha beklenmedik yazı tipi değişimiyle şaşırmayın. Herhangi bir sorunla karşılaşırsanız, aşağıya yorum bırakın—iyi kodlamalar!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}