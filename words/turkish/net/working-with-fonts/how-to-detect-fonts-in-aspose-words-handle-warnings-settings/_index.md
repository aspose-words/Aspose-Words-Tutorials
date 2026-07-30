---
category: general
date: 2026-01-03
description: Aspose.Words'ta yazı tiplerini nasıl tespit eder ve uyarıları Aspose
  yazı tipi ayarlarıyla nasıl yönetirsiniz – geliştiriciler için adım adım bir rehber.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: tr
og_description: Aspose.Words'ta yazı tiplerini nasıl tespit eder ve Aspose yazı tipi
  ayarlarıyla uyarıları nasıl yapılandırırsınız. Tam iş akışını dakikalar içinde öğrenin.
og_title: Aspose.Words'ta Yazı Tiplerini Nasıl Algılayabilirsiniz – Uyarıları İşleyin
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Words'ta Yazı Tiplerini Nasıl Algılayabilirsiniz – Uyarıları ve Ayarları
  Yönetme
url: /tr/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile Yazı Tiplerini Nasıl Algılayabilirsiniz – Uyarıları ve Ayarları Yönetme

Üretime geçmeden önce bir Word belgesindeki **yazı tiplerini nasıl algılayacağınızı** hiç merak ettiniz mi? Tek başınıza değilsiniz. Eksik yazı tipleri düzen felaketlerine yol açabilir ve uygun uyarılar olmadan bozuk bir PDF ya da DOCX dosyasını fark etmeden gönderebilirsiniz.  

Bu öğreticide **yazı tiplerini nasıl algılayacağınızı** Aspose.Words kullanarak gösterecek, **uyarıları nasıl yöneteceğinizi** anlatacak ve **Aspose yazı tipi ayarlarını** ihtiyacınıza göre **uyarıları yapılandıracak** şekilde nasıl ayarlayacağınızı göstereceğiz. Sonunda, Aspose’un gerçekleştirdiği her ikameyi yazdıran hazır‑çalıştır bir kod parçacığına sahip olacaksınız ve bunu kendi projelerinizde nasıl uyarlayacağınızı öğreneceksiniz.

## Önkoşullar

- .NET 6+ (veya .NET Framework 4.6+).  
- NuGet üzerinden kurulan Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Bilerek eksik bir yazı tipine referans veren bir Word dosyası (ör. *DocumentWithMissingFonts.docx*).  

Eğer bunlara sahipseniz, harika—hadi başlayalım.

![yazı tiplerini algıla ekran görüntüsü](https://example.com/detect-fonts.png "yazı tiplerini algıla örnek çıktısı")

## Aspose.Words ile Yazı Tiplerini Algılamak

İlk adım, Aspose.Words’e yazı tipi ikame olaylarına ilgi duyduğunuzu söylemektir. Bu, **Aspose yazı tipi ayarları** aracılığıyla özel bir uyarı geri çağrısı (callback) sağlayarak yapılır. Geri çağrı, her ikame için bir `WarningInfo` nesnesi alır ve size çalışma zamanında **yazı tiplerini algılamanızı** sağlar.

### Adım 1: Bir Uyarı Geri Çağrı Sınıfı Oluşturun

`IWarningCallback` arayüzünü uygulayın. `Warning` metodunun içinde `WarningType.FontSubstitution` için filtreleyin ve ayrıntıları kaydedin.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **İpucu:** `info.Description` dizesi hem eksik yazı tipi adını hem de Aspose’un seçtiği ikameyi içerir. Yapılandırılmış bir rapor istiyorsanız bunu ayrıştırabilirsiniz.

### Adım 2: Aspose Yazı Tipi Ayarlarıyla LoadOptions’u Yapılandırın

Bir `LoadOptions` örneği oluşturun, yeni bir `FontSettings` nesnesi ekleyin ve `WarningCallback`i az önce oluşturduğunuz işleyiciye yönlendirin. Bu, Aspose’a **uyarıları nasıl yapılandıracağını** söyler.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Özel bir yazı tipi klasörünüz varsa, şöyle ekleyebilirsiniz:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Bu satır, **aspose yazı tipi ayarları**nın bir başka yönünü gösterir—Aspose’un ikame yapmadan önce yazı tiplerini arayacağı yerleri tam olarak kontrol edersiniz.

### Adım 3: Belgeyi Yükleyin ve Geri Çağrıyı Tetikleyin

Şimdi hedef belgeyi `loadOptions` ile yükleyin. Aspose dosyayı ayrıştırdıkça, eksik bir yazı tipi herhangi bir uyarı işleyicisini tetikler ve **yazı tiplerini anında algılar**.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

Programı çalıştırdığınızda aşağıdaki gibi bir çıktı görürsünüz:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Adım 4: (İsteğe Bağlı) Uyarıları Daha Sonra Kullanmak İçin Toplayın

İkame verilerini bir rapor için saklamanız gerekiyorsa, işleyiciyi mesajları bir listede biriktirecek şekilde değiştirin.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Daha sonra `handler.Substitutions`ı bir JSON dosyasına yazabilir, bir günlük hizmetine gönderebilir ya da bir UI’da gösterebilirsiniz.

### Adım 5: Sonucu Programatik Olarak Doğrulayın

Bazen (ör. bir CI derlemesinde) **hiç ikame olmadığını** doğrulamak istersiniz. İşte hızlı bir kontrol:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Bu kod parçacığı, **uyarıları nasıl yöneteceğinizi** belirli bir şekilde gösterir ve derleme hattı üzerinde tam kontrol sağlar.

## Sık Sorulan Sorular (ve Kenar Durumlar)

**Bazı ikameleri yok saymam gerekirse ne olur?**  
`Warning` içinde koşullu mantık ekleyebilir ve kabul edilebilir bulduğunuz yazı tipleri için sadece geri dönerek kaydetmeyi atlayabilirsiniz.

**Tüm uyarıları bastırıp sadece bir boolean sonuç almak istersem?**  
Evet—`loadOptions.WarningCallback = null` yapın ve ardından yükleme sonrası `doc.FontInfo`u inceleyin (ancak ayrıntılı günlük kaybını da alırsınız).

**Bu PDF dönüşümüyle de çalışır mı?**  
Kesinlikle. Aynı uyarı mekanizması `doc.Save("out.pdf")` çağrıldığında da devreye girer. Geri çağrı, dönüşüm adımı sırasında gerçekleşen tüm yazı tipi değişimlerini yakalar.

**Performans üzerinde bir etkisi var mı?**  
Etkisi çok az—eksik her yazı tipi için birkaç ek metod çağrısı olur. Büyük toplu işlemlerde sonuçları önbelleğe almayı düşünebilirsiniz.

## Özet: Neler Kaptık

- Özel bir `IWarningCallback` uygulayarak **yazı tiplerini nasıl algılayacağınızı**.  
- `LoadOptions.WarningCallback` üzerinden **uyarıları nasıl yöneteceğinizi**.  
- **Aspose yazı tipi ayarlarını** (özel yazı tipi klasörleri ekleme, uyarıları açma/kapama) ayarlama.  
- **Uyarıları hem anlık konsol çıktısı hem de sonradan analiz** için nasıl yapılandıracağınızı.  

Bu parçalarla Word belgelerini güvenle işleyebilir, eksik yazı tiplerinin işaretlendiğinden emin olabilir ve çıktılarınızın ortamlar arasında tutarlı kalmasını sağlayabilirsiniz.

## Sonraki Adımlar

- Daha ince ayar için `FontSettings.SubstitutionSettings`i keşfedin (ör. belirli eksik yazı tiplerini seçtiğiniz ikamelerle eşleştirme).  
- Bu yaklaşımı Aspose.PDF ile birleştirerek tipografiyi tam olarak koruyan PDF’ler üretin.  
- Uyarı kontrolünü bir CI/CD boru hattına otomatikleştirerek font sorunları içeren sürümleri engelleyin—kalite kapıları olarak **uyarıları yönetmek** isteyen ekipler için mükemmel.

**aspose font settings** hakkında daha fazla sorunuz varsa ya da bunu daha büyük bir servise entegre etme konusunda yardıma ihtiyacınız olursa, aşağıya yorum bırakın. İyi kodlamalar!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}