---
category: general
date: 2026-02-21
description: Uyarıları nasıl etkinleştireceğinizi, eksik yazı tiplerini nasıl tespit
  edeceğinizi ve Aspose.Words kullanarak C#’ta docx dosyalarını güvenli bir şekilde
  nasıl yükleyeceğinizi öğrenin. Adım adım rehberi izleyin.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: tr
og_description: Uyarıları nasıl etkinleştirirsiniz, eksik yazı tiplerini nasıl tespit
  edersiniz ve Aspose.Words ile docx dosyalarını doğru şekilde nasıl yüklersiniz.
  Tam kod örneği dahil.
og_title: DOCX yüklerken uyarıları etkinleştirme ve eksik fontları tespit etme
tags:
- C#
- Aspose.Words
- Document processing
title: DOCX dosyalarını yüklerken uyarıları nasıl etkinleştirir ve eksik fontları
  nasıl tespit edersiniz
url: /tr/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX dosyaları yüklenirken uyarıları etkinleştirme ve eksik yazı tiplerini tespit etme

Hiç **uyarıları nasıl etkinleştireceğinizi** eksik yazı tipleri için, belgelerinizin render edilmesini sessizce bozmasından önce merak ettiniz mi? Yalnız değilsiniz—çoğu geliştirici kütüphanenin sadece “doğru şeyi” yapacağını varsayar, ancak daha sonra bir yazı tipinin hiçbir ipucu olmadan değiştirildiğini keşfeder.

Bu öğreticide tam olarak **uyarıları nasıl etkinleştireceğinizi**, **eksik yazı tiplerini nasıl tespit edeceğinizi** ve Aspose.Words for .NET kullanarak **docx nasıl yükleyeceğinizi** doğru şekilde göstereceğiz. Sonunda, her yazı tipi değiştirme uyarısını konsola yazdıran hazır‑çalıştır örnek bir kodunuz olacak, böylece dosyanın içinde ne olduğuna bir daha tahmin yürütmek zorunda kalmayacaksınız.

## Önkoşullar

- .NET 6.0 veya daha yeni (kod .NET Framework 4.7+ üzerinde de çalışır)  
- Visual Studio 2022 veya tercih ettiğiniz herhangi bir C# IDE  
- **Aspose.Words** NuGet paketi (`Install-Package Aspose.Words`)  
- Makinenizde yüklü olmayan yazı tipleri içerebilecek bir DOCX dosyası (`input.docx` olarak adlandıracağız)

> **Pro tip:** Test dosyanız yoksa, özel bir kurumsal yazı tipi kullanan bir Word belgesi açın ve `input.docx` olarak kaydedin. Bu, yakalamak istediğimiz uyarıyı tetikleyecektir.

## Çözümün Genel Bakışı

1. **Create** bir `LoadOptions` nesnesi oluşturun ve `FontSubstitutionWarnings` özelliğini etkinleştirin.  
2. **Load** DOCX dosyasını bu seçeneklerle yükleyin.  
3. **Inspect** `WarningCallback` koleksiyonunu `FontSubstitution` girişleri için inceleyin.  
4. **React** – eksik yazı tipini günlüğe kaydedebilir, gösterebilir veya programatik olarak bile değiştirebilirsiniz.

Aşağıda her adımı ayrıntılı olarak açıklıyor, *neden* önemli olduğunu belirtiyor ve size tam, çalıştırılabilir bir kod parçacığı sunuyoruz.

---

## Adım 1: Aspose.Words'ü Yükleyin ve Projeyi Ayarlayın

Uyarıları **nasıl etkinleştireceğimizi** yapabilmeden önce, onları gerçekten destekleyen kütüphaneye ihtiyacımız var.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Veya, Visual Studio Paket Yöneticisi Konsolu'nda:

```powershell
Install-Package Aspose.Words
```

> **Neden bu adım?**  
> Paket olmadan `LoadOptions`, `Document` ve uyarı altyapısı mevcut değildir. NuGet referansını eklemek, en son kararlı sürümü (bu yazının yazıldığı tarih itibarıyla 24.5) almanızı sağlar.

---

## Adım 2: Yazı tipi değiştirme uyarılarını etkinleştiren yükleme seçeneklerini oluşturun

**Uyarıları nasıl etkinleştireceğimizin** kalbi `LoadOptions` sınıfında bulunur. `FontSubstitutionWarnings` özelliğini `true` olarak ayarlamak, motorun eksik bir yazı tipini her değiştirdiğinde bunu kaydetmesini sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Bu bayrağı neden etkinleştiriyoruz?**  
> Varsayılan olarak Aspose.Words eksik yazı tiplerini sessizce bir yedekle (genellikle Arial) değiştirir. Bu, düzen kaymaları, görünmez karakterler veya marka ihlallerine yol açabilir. Bayrağı açmak tam görünürlük sağlar.

---

## Adım 3: Yapılandırılmış seçenekleri kullanarak DOCX dosyasını yükleyin

Şimdi **docx nasıl yükleyeceğimizi** uyarılar açıkken bildiğimize göre, yüklemeyi gerçekte gerçekleştiriyoruz.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **Arka planda ne oluyor?**  
> DOCX dosyasını ayrıştırırken Aspose.Words her `<w:rFonts>` öğesini kontrol eder. Belirtilen yazı tipi yüklü değilse, bir `FontSubstitution` uyarısı kaydeder ve varsayılan bir yazı tipine geçer. Uyarıları etkinleştirdiğimiz için bu girişler `document.WarningCallback.Warnings` içinde yer alır.

---

## Adım 4: Yazı tipi değiştirme uyarılarını al ve göster

`WarningCallback` özelliği bir `WarningInfoCollection` tutar. Üzerinde döngü kurun, `WarningType.FontSubstitution` için filtreleyin ve mesajları çıktıya yazdırın.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Beklenen çıktı** (örnek):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **Bu mesajlarla ne yapmalı?**  
> Bunları bir dosyaya kaydedebilir, bir UI’da gösterebilir veya özel bir yazı tipi yedekleme rutini tetikleyebilirsiniz. Önemli olan, artık *eksik yazı tiplerini* tahmin etmek yerine tespit edebiliyorsunuz.

---

## Adım 5: (İsteğe Bağlı) Eksik yazı tiplerini belirli bir yedekle değiştir

Uygulamak istediğiniz kurumsal bir yazı tipiniz varsa, uyarıları yakalayıp anında değiştirebilirsiniz.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Bunu neden düşünmeliyiz?**  
> Tüm oluşturulan belgelerde görsel tutarlılığı garanti eder; bu da marka uyumluluğu için kritiktir.

---

## Tam, çalıştırılabilir örnek

Aşağıda bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz tek bir C# dosyası bulunuyor. Paketi yüklemekten uyarıları yazdırmaya kadar her şeyi kapsar.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Run it**: `dotnet run` from the project folder. If any fonts are missing, you’ll see the warnings printed, and the optional replacement will be applied before the file is saved.

---

## Sıkça Sorulan Sorular

### Bu PDF dönüşümüyle de çalışır mı?

Evet. Uyarıları işledikten sonra `doc.Save("output.pdf")` çağrısını yapabilirsiniz; değiştirilmiş yazı tipleri PDF’de de DOCX gibi görünecektir.

### Belirli bir yazı tipi için uyarıları nasıl bastırabilirim?

Döngü içinde filtreleyebilirsiniz—yani `Message` içinde görmezden gelmek istediğiniz yazı tipi adını içeren `WarningInfo` öğesini atlayın.

### `FontSubstitutionWarnings` eski Aspose.Words sürümlerinde mevcut mu?

Bu özellik sürüm 20.5'te tanıtıldı. Daha eski bir sürüm kullanıyorsanız, NuGet üzerinden yükseltin; API değişikliği geriye dönük uyumludur.

---

## Sonuç

**Uyarıları nasıl etkinleştireceğimizi** adım adım gösterdik, **eksik yazı tiplerini nasıl tespit edeceğinizi** gösterdik ve Aspose.Words ile **docx nasıl yükleyeceğinizi** tam görünürlük sağlayarak doğru şekilde uyguladık. `document.WarningCallback.Warnings`'ı inceleyerek güvenilir bir denetim izi elde edersiniz—artık sessiz yedeklemeler yok.

Sonraki adımlar? Uyarı mantığını Serilog gibi bir günlükleme çerçevesine bağlamayı deneyin veya belgeyi kullanıcılara göndermeden önce eksik yazı tiplerini vurgulayan bir UI oluşturun. Ayrıca `FontSettings` sınıfını inceleyerek yazı tipi değiştirme politikaları üzerinde daha ince ayar yapabilirsiniz.

Keyifli kodlamalar, ve belgeleriniz her zaman istediğiniz gibi render olsun!

![DOCX dosyası yüklemeden yazı tipi değiştirme uyarılarını yakalamaya kadar akışı gösteren diyagram – Aspose.Words'ta uyarıları nasıl etkinleştireceğiniz](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}