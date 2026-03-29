---
category: general
date: 2026-03-28
description: Aspose.Words ile bir DOCX yüklerken uyarıları nasıl yakalarsınız ve eksik
  yazı tipleri için uyarı mesajları alırsınız. Eksik yazı tiplerini verimli bir şekilde
  nasıl yönetebileceğinizi öğrenin.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: tr
og_description: Aspose.Words ile bir DOCX yüklerken uyarıları yakalama, uyarı mesajlarını
  alma ve eksik yazı tiplerini pratik kod örnekleriyle ele alma.
og_title: Aspose.Words'ta Uyarıları Yakalama – Tam C# Rehberi
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Words'ta Uyarıları Yakalama – Tam C# Rehberi
url: /tr/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words'ta Uyarıları Yakalama – Tam C# Kılavuzu

Aspose.Words ile bir Word belgesi yüklerken ortaya çıkan **uyarıları nasıl yakalayacağınızı** hiç merak ettiniz mi? Belki garip yazı tipi değişiklikleri görüyorsunuz ve tam olarak nedenini bilmek istiyorsunuz. Kısacası, kütüphanenin uyarı sistemine bağlanabilir, **uyarı mesajlarını alabilir** ve hatta **eksik yazı tiplerini** düzeninizi bozmasından önce ele alabilirsiniz.  

Bu öğreticide gerçek bir senaryoyu adım adım inceleyeceğiz: bir DOCX dosyasını yüklemek, motorun ürettiği tüm uyarıları toplamak ve gerçekleşen herhangi bir yazı tipi ikamesi hakkında ayrıntıları yazdırmak. Sonuna geldiğinizde çalıştırmaya hazır bir kod örneğine sahip olacak, her adımın “neden”ini anlayacak ve yaklaşımı kendi projeleriniz için nasıl genişleteceğinizi bileceksiniz.

## Öğrenecekleriniz

- `LoadOptions`'ı uyarıların otomatik olarak yakalanacak şekilde nasıl yapılandıracağınızı.  
- `WarningInfoCollection`'dan **uyarı mesajlarını** tam olarak nasıl alacağınızı.  
- `WarningType.FontSubstitution` bayrağıyla **eksik yazı tiplerini** nasıl tanımlayıp yanıt vereceğinizi.  
- Gömülü yazı tiplerine sahip belgeler veya özel yazı tipi klasörleri gibi uç durumları çözmek için ipuçları.  

Harici referanslara gerek yok – ihtiyacınız olan her şey burada.

---

## Önkoşullar

- .NET 6.0 veya daha yenisi (kod .NET Framework 4.7+ üzerinde de çalışır).  
- Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`).  
- Bazı yazı tipleri eksik olan veya makinenizde yüklü olmayan yazı tipleri kullanan bir örnek DOCX (`input.docx`).  

Hepsi bu. C# ve Visual Studio konusunda zaten rahatsanız, kodu kopyalayıp hemen çalıştırabilirsiniz.

---

## Adım 1: Load Options'ı ve Bir Uyarı Geri Çağrısını Hazırlama

Aspose.Words, `new Document(path, loadOptions)` çağrısı yapıldığında ilk olarak dosyayı ayrıştırır. Ayrıştırma sırasında eksik yazı tipleri, desteklenmeyen özellikler veya kullanımdan kaldırılmış işaretlemelerle karşılaşabilir. Bu olayları yakalamak için bir **uyarı geri çağrısı** nesnesine ihtiyacınız var.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Neden önemli:** Bir geri çağrı olmadan, Aspose.Words uyarıları sessizce konsola kaydeder (veya yok sayar), böylece düzeni etkileyebilecek yazı tipi ikamelerini görmezsiniz. Ayrı bir `WarningInfoCollection` sağlayarak tam görünürlük elde edersiniz.

> **Pro ipucu:** Yalnızca yazı tipiyle ilgili uyarılarla ilgileniyorsanız, daha sonra filtreleyebilirsiniz – ancak *tüm* uyarıları toplamak gelecekteki sorunlar için bir güvenlik ağı sağlar.

---

## Adım 2: Belgeyi Yapılandırılmış Seçeneklerle Yükleme

Geri çağrı hazır olduğuna göre, dosyayı yükleyin. `Document` yapıcı, bulduğu herhangi bir sorun için otomatik olarak geri çağrıyı tetikleyecektir.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**Arka planda neler oluyor?** Aspose.Words Open XML'i ayrıştırır, stilleri çözer ve her yazı tipi referansını sistemde yüklü bir yazı tipine eşlemeye çalışır. Eşleşme bulunamazsa, `FontSubstitution` türünde bir `WarningInfo` girdisi oluşturur.

---

## Adım 3: Toplanan Uyarıları Almak ve İncelemek

Yükleme tamamlandıktan sonra, `warningCollector` artık gerçekleşen tüm uyarıları içerir. Şimdi onları alalım ve yazı tipi ikamesi mesajlarına odaklanalım.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Örnek çıktı** (konsolunuz şu şekilde bir şey gösterebilir):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Eğer *tüm* uyarıları istiyorsanız, sadece `if` kontrolünü kaldırın veya her giriş için `warning.Type`'ı kaydedin.

---

## Adım 4: Eksik Yazı Tiplerini Ele Alma – Sadece Günlüğe Kaydetmenin Ötesinde

Uyarıları yakalamak faydalıdır, ancak çoğu zaman **eksik yazı tiplerini** programlı olarak **ele almanız** gerekir. İşte iki yaygın strateji:

### 4.1 Eksik Yazı Tiplerini Belirli Bir Yedekle Değiştirme

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Artık eksik herhangi bir yazı tipi, kütüphanenin varsayılan yedeği yerine *Calibri* ile değiştirilecektir.

### 4.2 Yedek Yazı Tipini Dinamik Olarak Gömme

Eğer özel bir yazı tipi dosyanız (ör. `MyFallback.ttf`) varsa, bunu çalışma zamanında kaydedebilirsiniz:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Bu yaklaşım, uygulamanızla birlikte belirli bir kurumsal yazı tipini dağıttığınızda kullanışlıdır.

> **Köşe durum:** Gerekli yazı tipini zaten gömen belgeler, sistem ikame kurallarını görmezden gelecektir. Bu senaryoda, o yazı tipi için uyarı koleksiyonu boş olur; bu da tam olarak istediğiniz şeydir.

---

## Adım 5: Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

Aşağıda, baştan sona her şeyi gösteren bağımsız bir program bulunuyor. `YOUR_DIRECTORY/input.docx` ifadesini test dosyanızın yolu ile değiştirmeniz yeterli.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Beklenenler**

- Konsol, görünürlük için bir uyarı emojisiyle ön eklenmiş her font‑ikamesi uyarısını yazdırır.  
- Çıktı DOCX (`output.docx`), eksik bir yazı tipi tespit edilen her yerde *Calibri* kullanır.  
- Herhangi bir işlenmemiş istisna yok – uyarı sistemi bilinmeyen yazı tiplerini sorunsuz bir şekilde ele alır.

---

## Yaygın Sorular & Cevaplar

**S: Bu, Word'den oluşturulan PDF'lerle çalışır mı?**  
C: Evet. Aspose.Words PDF'leri başka bir çıktı formatı olarak ele alır. Uyarı yakalama *yükleme* aşamasında gerçekleşir, bu yüzden nihai dışa aktarmadan bağımsızdır.

**S: **Tüm** belge işlemleri (kaydetme, dönüştürme vb.) için uyarı yakalamam gerekirse?**  
C: Belge oluşturulduktan sonra `Document.WarningCallback`'e atayarak aynı `WarningInfoCollection`'ı yeniden kullanabilirsiniz. Sonraki her işlem, aynı koleksiyona yeni girdiler ekleyecektir.

**S: Uyarı geri çağrısı performansı etkiler mi?**  
C: Önemsiz bir etkisi vardır. Koleksiyon sadece nesneleri depolar; sıkı bir döngüde binlerce uyarı işlenmediği sürece bir yavaşlama fark etmeyeceksiniz.

**S: İlgilenmediğim uyarıları nasıl bastırırım?**  
C: `IWarningCallback`'i miras alan özel bir sınıf uygulayın ve `Warning` metodunda filtreleme yapın. Yerleşik `WarningInfoCollection` sadece depolar, filtreleme yapmaz.

---

## Pro İpuçları & Tuzaklar

- **Pro ipucu:** Her zaman `Warning.Description`'ı inceleyin – eksik olan tam yazı tipi adını içerir. Bu, yazı tipini uygulamanızla birlikte dağıtıp dağıtmamaya karar vermenize yardımcı olabilir.  
- **Gömülü yazı tiplerine dikkat:** Kaynak DOCX zaten gereken yazı tipini gömüyorsa, Aspose.Words yerel olarak yüklü olmasa bile ikame uyarısı üretmez.  
- **İş parçacığı güvenliği:** `WarningInfoCollection` iş parçacığı‑güvenli değildir. Aynı anda birden fazla belge yüklüyorsanız, her iş parçacığına kendi koleksiyonunu verin.  
- **Sürüm kontrolü:** Uyarı API'si Aspose.Words 20.8'den beri kararlıdır. Yeni uyarı türlerini kaçırmamak için güncel bir sürüm kullandığınızdan emin olun.

---

## Sonuç

Aspose.Words'tan **uyarıları nasıl yakalayacağınızı** ele aldık, **uyarı mesajlarını nasıl alacağınızı** gösterdik ve eksik yazı tiplerini yedek yazı tipleri veya özel yazı tipi klasörleriyle **ele almanın** pratik yollarını sunduk. Tam örnek, herhangi bir .NET projesine eklemeye hazır ve kavramlar daha büyük otomasyon hatlarına ölçeklenebilir.

Sonra şunları keşfedebilirsiniz:

- **save** işlemleri sırasında uyarıları yakalamak için `Document.WarningCallback` kullanmak.  
- Uyarıları üretim izleme için bir dosyaya veya telemetri sistemine kaydetmek.  
- Geri çağrıyı, eksik yazı tiplerini marka‑özel tipografilerle otomatik olarak değiştirecek şekilde genişletmek.

Denemekten çekinmeyin—yedek yazı tipini değiştirin, toplu işleme daha fazla belge ekleyin veya uyarı toplayıcıyı font‑ile ilgili gerilemeleri işaretleyen bir CI hattına entegre edin. İyi kodlamalar, ve belgeleriniz her zaman beklediğiniz gibi render olsun!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}