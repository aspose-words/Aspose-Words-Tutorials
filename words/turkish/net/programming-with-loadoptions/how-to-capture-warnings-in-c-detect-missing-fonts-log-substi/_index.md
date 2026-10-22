---
category: general
date: 2026-04-04
description: Aspose.Words LoadOptions kullanarak C#'ta uyarıları yakalamayı, eksik
  yazı tiplerini tespit etmeyi ve değiştirme olaylarını nasıl kaydedeceğinizi öğrenin.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: tr
og_description: Uyarıları yakalama, eksik yazı tiplerini tespit etme ve Aspose.Words
  LoadOptions kullanarak C#'ta ikame olaylarını kaydetme.
og_title: C#'de Uyarıları Nasıl Yakalarız – Eksik Yazı Tiplerini Tespit Edin ve Değiştirmeyi
  Günlüğe Kaydedin
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: C#'ta Uyarıları Nasıl Yakalarız – Eksik Yazı Tiplerini Tespit Et ve Değiştirmeyi
  Günlüğe Kaydet
url: /tr/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta Uyarıları Yakalama – Eksik Yazı Tiplerini Algıla ve Değiştirmeleri Günlüğe Kaydet

Eksik yazı tipleri içeren bir Word belgesi yüklediğinizde ortaya çıkan **uyarıları nasıl yakalayacağınızı** hiç merak ettiniz mi? Yalnız değilsiniz. Birçok gerçek dünya projesinde, yazı tipleri taşıma sırasında kaybolur ve sessiz yedekleme düzeninizi bozabilir. İyi haber? Aspose.Words, bu uyarıları dinlemenin, eksik yazı tiplerini tespit etmenin ve hatta her değişikliği günlüğe kaydetmenin temiz bir yolunu sunar, böylece kaynağı daha sonra düzeltebilirsiniz.

Bu öğreticide, **uyarıları nasıl yakalayacağınızı** gösteren, **eksik yazı tiplerini algılayacağınızı** gösteren ve **değiştirme olaylarını nasıl günlüğe kaydedeceğinizi** açıklayan eksiksiz, çalıştırmaya hazır bir çözüm üzerinden adım adım ilerleyeceğiz. Sonunda, yeniden kullanılabilir bir uyarı işleyiciniz, tam yapılandırılmış bir `LoadOptions` nesneniz ve doğrulayabileceğiniz örnek bir konsol çıktısı olacak.

> **Önkoşul:** NuGet üzerinden yüklü Aspose.Words for .NET (v24.x veya daha yeni) ve temel bir C# geliştirme ortamına (Visual Studio 2022 veya VS Code yeterlidir) ihtiyacınız var.

---

## Belgeleri Yüklerken Uyarıları Nasıl Yakalarız

Çözümün çekirdeği, `IWarningCallback` arayüzünü uygulayan bir sınıftır. Aspose.Words, belge yükleme sırasında üretilen her uyarı için bu geri aramayı otomatik olarak çağırır; buna yazı tipi değiştirme uyarıları da dahildir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Bu adım neden?**  
> `WarningType.FontSubstitution` üzerine filtreleme yaparak alakasız uyarılardan (örneğin, kullanımdan kaldırılmış özellikler) kaynaklanan gürültüyü önleriz. Bu, günlüğün sadece sizin ilgilendiğiniz – eksik yazı tipleri – soruna odaklanmasını sağlar.

---

## Aspose.Words ile Eksik Yazı Tiplerini Algılamak

Bir belge, makinede yüklü olmayan bir yazı tipine referans verdiğinde, Aspose.Words en yakın eşleşmeyi kullanarak değiştirir ve bir uyarı oluşturur. Yukarıdaki işleyicimiz her oluşumu yakalar ve **eksik yazı tiplerini etkili bir şekilde algılar**.

Bunu çalıştırmak için `LoadOptions` yapılandırmalı ve işleyiciyi eklemeliyiz:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **İpucu:** Uyarıları daha sonra işlemek (ör. bir dosyaya yazmak) istiyorsanız, `Console.WriteLine` ifadesini mesajı bir `List<string>`'e ekleyen kodla değiştirin.

---

## Değiştirme Olaylarını Günlüğe Kaydetme

Günlüğe kaydetmek, uyarı çıktısını kalıcı bir depoya yönlendirmek kadar basittir. Aşağıda, her değiştirme uyarısını `font-warnings.log` adlı bir metin dosyasına yazan hızlı bir örnek bulabilirsiniz.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Neden bir dosyaya kaydedilir?**  
> Kalıcı günlükler, yazı tipi sorunlarını birden çok çalıştırma boyunca denetlemenizi, uyarıları otomatikleştirmenizi veya verileri bir derleme‑boru hattı kontrolüne beslemenizi sağlar.

---

## Tam Çalışan Örnek

Her şeyi bir araya getirerek, kopyalayıp yapıştırıp çalıştırabileceğiniz bağımsız bir konsol uygulaması sunuyoruz. Bu örnek **uyarıları nasıl yakalayacağınızı**, **eksik yazı tiplerini nasıl algılayacağınızı** ve **değiştirmeleri nasıl günlüğe kaydedeceğinizi** tek seferde gösterir.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Beklenen Konsol Çıktısı

`input.docx` bir yüklü olmayan yazı tipine referans veriyorsa, aşağıdaki gibi bir çıktı görürsünüz:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

`FileLoggingWarningHandler`'a geçtiyseniz, aynı satırlar zaman damgalarıyla birlikte `font-warnings.log` içinde yer alır.

![uyarıları yakalama konsol çıktısı](image-placeholder.png)

---

## Yaygın Sorular ve Kenar Durumları

### Tüm uyarıları, sadece yazı tipi değiştirmelerini değil, yakalamam gerekirse ne yapmalıyım?

`if (info.Type == WarningType.FontSubstitution)` kontrolünü tamamen kaldırın. Geri arama, her uyarı türünü (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent` vb.) alacaktır. Daha sonra `info.Type` üzerine dallanarak her durumu farklı şekilde işleyebilirsiniz.

### Bu sadece Word belgeleriyle mi, PDF'lerle de çalışır mı?

`LoadOptions` ve `IWarningCallback` Aspose.Words'in bir parçasıdır, bu yüzden Word‑uyumlu formatlara (`.docx`, `.doc`, `.rtf`, `.html`) uygulanır. PDF'ler için Aspose.PDF'in kendi uyarı mekanizmalarını kullanmanız gerekir.

### Uyarıları günlüğe kaydetmek yerine nasıl bastırabilirim?

`LoadOptions.WarningCallback = null` olarak ayarlayın veya geri aramayı uygulayın ancak metodun gövdesini boş bırakın. Kütüphane yine de değişikliği sessizce yapar.

### İş parçacığı güvenliği (thread‑safety) hakkında ne söyleyebilirsiniz?

Geri arama örneği, belgeyi yükleyen aynı iş parçacığında çalıştırılır; bu yüzden paralel yüklemeler arasında işleyiciyi paylaşmadığınız sürece ek senkronizasyona ihtiyaç yoktur. Eğer paylaşıyorsanız, ortak kaynakları (ör. günlük dosyası) bir kilitle koruyun veya eşzamanlı koleksiyonlar kullanın.

---

## Sonuç

Aspose.Words'tan **uyarıları nasıl yakalayacağınızı** ele aldık, **eksik yazı tiplerini nasıl algılayacağınızı** gösterdik ve **değiştirme olaylarını nasıl günlüğe kaydedeceğinizi** açıklamış olduk. Basit bir `IWarningCallback` uygulamasını `LoadOptions` içine takarak, kod tabanınızı kirletmeden yazı tipiyle ilgili sorunları tam olarak görebilirsiniz.

Sonraki adımlar? Günlüğü e‑posta gönderecek şekilde genişletin, Azure Monitor ile bütünleştirin veya bir derleme sunucusunda eksik yazı tiplerini otomatik olarak kurun. Ayrıca diğer uyarı türlerini de keşfedebilirsiniz – `WarningType.DegradedDocument`, dönüşüm sürecinde hayatta kalmayan özellikleri size bildirebilir.

Yazı tipi yönetimi veya Aspose.Words hakkında daha fazla sorunuz mu var? Bir yorum bırakın ya da Aspose forumlarında yeni bir konu açın. İyi kodlamalar, ve belgeleriniz her zaman doğru tipografiyle görüntülensin!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}