---
category: general
date: 2026-06-08
description: Aspose.Words'ta LoadOptions kullanarak belge içe aktarımı sırasında eksik
  yazı tiplerini nasıl tespit edeceğinizi öğrenin. Kod, açıklamalar ve en iyi uygulamalarla
  adım adım rehber.
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: tr
og_description: Aspose.Words'ta LoadOptions nasıl kullanılır ve bir belge yüklenirken
  eksik yazı tipleri nasıl tespit edilir. Kod ve pratik ipuçlarıyla tam rehber.
og_title: Eksik Yazı Tiplerini Tespit Etmek İçin LoadOptions Nasıl Kullanılır
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: Eksik Yazı Tiplerini Tespit Etmek İçin LoadOptions Nasıl Kullanılır
url: /tr/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# LoadOptions Kullanarak Eksik Yazı Tiplerini Tespit Etme

Aspose.Words ile bir Word belgesi yüklerken **LoadOptions nasıl kullanılır** diye hiç merak ettiniz mi? Bu öğreticide size tam olarak **LoadOptions nasıl kullanılır** ve **eksik yazı tiplerini tespit eder** ve bunları sorunsuz bir şekilde nasıl ele alırsınız göstereceğiz. İster bir belge dönüştürme hizmeti ister bir raporlama motoru oluşturuyor olun, eksik yazı tipleri düzen sürprizlerine yol açabilir, bu yüzden onları erken yakalamak şarttır.

Uyarı geri çağrısını bağlamaktan sonuçları yorumlamaya kadar her adımı adım adım göstereceğiz—böylece herhangi bir .NET projesine ekleyebileceğiniz tam çalışan bir C# örneğiyle bitireceksiniz. Harici dokümanlar yok, sadece kendi içinde çalışan bir çözüm. Sonunda uyarı sisteminin neden var olduğunu, nasıl etkinleştirileceğini ve geri çağrı tetiklendiğinde ne yapılacağını öğreneceksiniz.

## Ön Koşullar

Before we dive in, make sure you have:

- **Aspose.Words for .NET** (herhangi bir yeni sürüm; kullandığımız API 2022'den beri kararlı).
- .NET geliştirme ortamı (Visual Studio, Rider veya C# uzantılı VS Code).
- Bir örnek Word dosyası (`input.docx`) ve içinde makinede yüklü olmayan bir yazı tipine referans veren bir dosya.

Hepsi bu—Aspose.Words dışındaki ekstra NuGet paketlerine gerek yok.

## Aspose.Words ile LoadOptions Kullanımı

**LoadOptions** sınıfı, bir belgenin okunma şeklini özelleştirmenin kapısıdır. İçine bir uyarı geri çağrısı ekleyerek, Aspose.Words dosyayı ayrıştırdığı anda **eksik yazı tiplerini tespit edebilirsiniz**. Şimdi adım adım inceleyelim.

### Adım 1: Uyarı İşleyicisi Oluşturma

Aspose.Words, `IWarningCallback` arayüzünü, yazı tipi ikamesi gibi kritik olmayan sorunları size bildirmek için kullanır. Bu arayüzü uygulayın ve bir uyarı geldiğinde ne yapılacağına karar verin.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**Neden Önemli:**  
Bir geri çağrı olmadan, Aspose.Words eksik yazı tiplerini sessizce varsayılan bir yazı tipiyle (genellikle Arial) değiştirir. `FontSubstitution` uyarısını yakalayarak sorunu kaydedebilir, kullanıcıyı uyarabilir veya eksik yazı tipini özel bir yedekle değiştirebilirsiniz.

### Adım 2: İşleyiciyi LoadOptions'a Bağlama

Şimdi bir `LoadOptions` örneği oluşturup ona `FontWarningHandler`'ımızı kullanmasını söylüyoruz. İşte **LoadOptions nasıl kullanılır** sorusunun gerçekten parladığı nokta.

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**Neden Önemli:**  
`LoadOptions`, birçok içe aktarma zamanı ayarı (kodlama, şifre vb.) için tek durak noktasıdır. `WarningCallback` ayarlanarak, bu seçeneklerle yüklediğiniz herhangi bir belge için hafif, olay‑tabanlı bir mekanizma etkinleştirirsiniz.

### Adım 3: Belgeyi Yapılandırılmış Seçeneklerle Yükleme

Son olarak, `LoadOptions`'ı `Document` yapıcısına geçiriyoruz. Kaynak dosya yüklü olmayan bir yazı tipine referans veriyorsa, Aspose.Words uyarıyı tetikleyecek ve işleyiciniz bir mesaj yazdıracaktır.

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Gördükleriniz:**  
`input.docx` dosyasının makinede bulunmayan *“MyCustomFont”* adlı bir yazı tipi kullandığını varsayarsak, konsol çıktısı şu şekilde görünecektir:

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

Tüm yazı tipleri mevcutsa, geri çağrı sessiz kalır—çıkış yok, performans kaybı yok.

## Uyarı Geri Çağrısı ile Eksik Yazı Tiplerini Tespit Etme (İkincil Anahtar Kelime Eylemde)

**detect missing fonts** ifadesi yukarıdaki başlıkta doğal olarak yer alıyor ve ikincil anahtar kelimeyi pekiştiriyor. Gerçek projelerde karşılaşabileceğiniz birkaç varyasyonu inceleyelim.

### Döngüde Birden Çok Belge

Genellikle bir dosya topluluğunu işlersiniz. Aynı `LoadOptions` örneği yeniden kullanılabilir, ancak `WarningCallback` yüklemeler arasında kalıcıdır. Belge başına izole etme ihtiyacınız varsa, her yineleme için yeni bir `LoadOptions` oluşturun.

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### Özel Yazı Tipi İkamesi Mantığı

Sadece kaydetmek yerine, belirli bir eksik yazı tipini şirket onaylı bir alternatifle değiştirmek isteyebilirsiniz. İşleyiciyi genişletin:

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

Artık sadece **eksik yazı tiplerini tespit** etmiyor, aynı zamanda nasıl değiştirileceğine de karar veriyorsunuz.

### İstenmeyen Uyarıları Sessize Alma

Sadece yazı tipi sorunlarıyla ilgileniyor ve diğer her şeyi bastırmak istiyorsanız, gösterildiği gibi `WarningType` ile filtreleyin. Aksine, *tüm* uyarıları kaydetmek için `if` kontrolünü kaldırın ve `info.WarningType` ile birlikte `info.Description`'ı çıktıya verin.

## Tam, Çalıştırılabilir Örnek

Hepsini bir araya getirerek, derleyip çalıştırabileceğiniz tam bir program burada. `"YOUR_DIRECTORY/input.docx"` ifadesini test dosyanızın yolu ile değiştirin.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Beklenen konsol çıktısı (bir yazı tipi eksik olduğunda):**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Eğer hiçbir yazı tipi eksik değilse, sadece şunu göreceksiniz:

```
Document loaded successfully.
```

## Yaygın Tuzaklar ve Uzman İpuçları

- **Tüzak:** `WarningCallback` ayarlamayı unutmak. API yine de yazı tiplerini ikame eder, ancak bunun gerçekleştiğini asla bilmezsiniz.  
  **Uzman ipucu:** Yazı tipi doğruluğuna ihtiyaç duyduğunuzda her zaman bir işleyici ekleyin; neredeyse hiç maliyeti yok.

- **Tüzak:**


## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words'ta Yazı Tiplerini Nasıl Tespit Edebilirsiniz – Uyarıları ve Ayarları Yönetme](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Aspose.Words'ta Yazı Tiplerini Nasıl Yakalarız – Tam Kılavuz](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [DOCX'i Yükleyip Eksik Yazı Tiplerini Tespit Etme – Tam C# Kılavuzu](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}