---
category: general
date: 2026-03-27
description: 'Aspose Font Değiştirme kolaylaştırıldı: yazı tipi ayarlarını yapılandırmayı,
  uyarıları yakalamayı ve .NET uygulamalarınızda eksik yazı tiplerini yönetmeyi öğrenin.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: tr
og_description: Aspose Yazı Tipi Değişimini, yazı tipi ayarlarını yapılandırarak ve
  eksik yazı tiplerini bir uyarı geri çağrısı ile ele alarak ustalaşın. Tam C# rehberi.
og_title: Aspose Yazı Tipi Değiştirme – C#'ta Yazı Tipi Ayarlarını Yapılandırma
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose Yazı Tipi Değiştirme – C#'ta Yazı Tipi Ayarlarını Nasıl Yapılandırılır
url: /tr/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Font Ayarlarını Yapılandırma İçin Tam Kılavuz

Hiç bir belgenin aniden özel yazı tipinizi genel bir şeyle değiştirdiğine rastladınız mı? Bu, **aspose font substitution** işini yapıyor—eksik yazı tiplerini bulabildiği en yakın eşleşmeyle değiştiriyor. Bu kullanışlı, ancak hangi yazı tipinin *tam olarak* değiştirildiğini bilmeniz gerekiyorsa, kütüphanenin uyarı sistemine erişmeli ve font ayarlarını kendiniz yapılandırmalısınız.

Bu öğreticide gerçek bir senaryoyu adım adım inceleyeceğiz: eksik bir yazı tipine referans veren bir DOCX dosyasını yüklemek, değişim olayını yakalamak ve konsola dostça bir mesaj yazdırmak. Sonunda **configure font settings** konusunda rahat olacak, bir **Aspose.Words warning callback** bağlayacak ve örneği herhangi bir iş akışına uyacak şekilde genişletebileceksiniz.

> **İhtiyacınız olanlar**  
> • .NET 6+ (or .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (latest NuGet)  
> • A DOCX that references a missing font (we’ll call it `MissingFont.docx`)  

Hadi başlayalım.

---

## Adım 1: Aspose.Words'ı Yükleyin ve Projeyi Hazırlayın

Herhangi bir kod yazmadan önce, Aspose.Words paketinin referans alındığından emin olun:

```bash
dotnet add package Aspose.Words
```

> **Pro ipucu:** En son kararlı sürümü kullanın; Mart 2026 itibarıyla 23.11.0 sürümüdür. Daha yeni sürümler font eşleştirme algoritmalarını iyileştirir ve ek uyarı türleri ekler.

Yeni bir konsol uygulaması oluşturun (veya kodu mevcut bir projeye ekleyin) ve tipik `using` yönergelerini ekleyin:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Bu ad alanları, ihtiyacımız olan `Document`, `LoadOptions` ve font‑ile ilgili sınıflara erişim sağlar.

## Adım 2: LoadOptions ile Font Ayarlarını Yapılandırın

**aspose font substitution** kontrolünün kalbi `LoadOptions.FontSettings` içinde yer alır. Boş bir `FontSettings` nesnesi sağlayarak Aspose'a varsayılan arama yollarını *ve* herhangi bir değişimi bir uyarı geri çağrısı aracılığıyla raporlamasını söyleriz.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

Neden sadece varsayılanlara güvenmeyelim? Çünkü bir uyarı geri çağrısı (sonraki adım) yalnızca `FontSettings` özelliği null olmayan bir durumda çalışır. Bu küçük satır, gerçek font arama davranışını değiştirmeden değişim sürecine bir kanca sağlar.

## Adım 3: Değişimleri Yakalamak İçin Bir Uyarı Geri Çağrısı Ekleyin

Aspose.Words, `IWarningCallback` arayüzünü uygular. Eksik bir font gibi dikkat çekici bir şey olduğunda, `Warning` metodumuzu çağırır. `WarningType.FontSubstitution` için filtreleyen ve açıklamayı yazdıran küçük bir işleyici uygulayacağız.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

İşte işleyicinin kendisi:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Neden önemli** – Geri çağrı olmadan, Aspose sessizce fontları değiştirir ve hangi fontun kullanıldığını asla öğrenemezsiniz. Geri çağrı, süreci şeffaf hâle getirir; bu, uyumluluk raporlaması veya düzen sorunlarını ayıklama için esastır.

## Adım 4: Belgeyi Yapılandırılmış Seçeneklerle Yükleyin

Şimdi nihayet belgeyi, az önce hazırladığımız `loadOptions` ile yüklüyoruz. Kaynak dosya yüklü olmayan bir fonta referans veriyorsa, işleyicimiz tetiklenecek.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

`YOUR_DIRECTORY` ifadesini `MissingFont.docx` dosyasının bulunduğu gerçek yol ile değiştirin. Programı çalıştırdığınızda aşağıdaki gibi bir çıktı görmelisiniz:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Bu satır, eksik olan fontun ve Aspose'un seçtiği yedek fontun tam olarak hangisi olduğunu size bildirir.

## Adım 5: (İsteğe Bağlı) Font Arama Yollarını İnce Ayarlayın

Kurumsal fontların bulunduğu özel bir klasörünüz varsa, Aspose'a sistem fontlarına dönmeden önce nerelere bakacağını söyleyebilirsiniz. Bu, **configure font settings**'in gelişmiş bir kullanım örneğidir:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

`recursive: true` ayarı, Aspose'un alt klasörleri de taramasını sağlar. Böylece kütüphane önce özel fontlarınızı deneyecek ve istenmeyen değişim olasılığını azaltacaktır.

## Tam Çalışan Örnek

Her şeyi bir araya getirerek, işte tam ve çalıştırmaya hazır program:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Beklenen çıktı** (eksik bir fontla karşılaşıldığında):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Tüm fontlar mevcutsa, program sessizce çalışır (uyarı yok) ve yine de PDF üretir.

## Sık Sorulan Sorular & Kenar Durumları

### Değişimi tamamen *önlemek* istersem ne olur?

`FontSettings.SubstitutionSettings` özelliğini `null` olarak ayarlayın veya davranışı kontrol etmek için `FontSettings.FontSubstitutionSettings` kullanın. Örneğin:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Artık Aspose, sessizce değiştirmenin yerine bir istisna fırlatacak; bu istisna yakalanıp işlenebilir.

### Bu, diğer dosya formatlarıyla (ör. .doc, .rtf) çalışır mı?

Kesinlikle. Aynı `LoadOptions` nesnesi, dosya yolu kabul eden herhangi bir `Document` yapıcısına geçirilebilir. Uyarı geri çağrısı, fontlara bağımlı tüm formatlar için tetiklenecektir.

### *Tam* yedek font adını yakalayabilir miyim?

Evet. `info.Description` dizesi hem eksik fontu hem de yerine geçen fontu içerir. Programa göre adı almanız gerekiyorsa, dizeyi ayrıştırabilir veya `FontInfo` nesnesini (yeni sürümlerde mevcut) kullanabilirsiniz.

### Bu, çok‑iş parçacıklı bir ortamda nasıl davranır?

`FontSettings` **thread‑safe** değildir. Her iş parçacığı için ayrı bir `LoadOptions` (kendi `FontSettings` ile) oluşturun veya erişimi bir kilitle koruyun.

## Sonuç

**aspose font substitution** ve **configure font settings** konularında C# uygulamasında ustalaşmak için gereken her şeyi ele aldık:

1. Aspose.Words'ı kurun ve gerekli `using` ifadelerini ekleyin.  
2. Yeni bir `FontSettings` ile bir `LoadOptions` nesnesi oluşturun.  
3. Değişim olaylarını ortaya çıkarmak için özel bir `IWarningCallback` ekleyin.  
4. Belgeyi yükleyin, geri çağrının eksik fontları rapor etmesine izin verin.  
5. (İsteğe bağlı) Arama yolunu genişletin veya değişimi tamamen devre dışı bırakın.

Bu desenle donanmış olarak, uyumluluk için eksik fontları kaydedebilir, bir UI'da kullanıcıları uyarabilir veya yayınlamadan önce yedek fontları otomatik olarak gömebilirsiniz. Sonraki adımda **Aspose.Words font substitution policies**'i keşfedebilir veya iş akışını daha büyük bir belge‑işleme hattına entegre edebilirsiniz.

Kodlamaktan keyif alın, ve belgeleriniz her zaman doğru yazı tipiyle görüntülensin!  

---  

![Aspose.Words'un bir belgeyi yüklediğini, FontSettings'i çağırdığını, bir uyarı geri çağrısını tetiklediğini ve değişim bilgilerini çıktıladığını gösteren diyagram](image-placeholder.png "aspose font substitution iş akışı")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}