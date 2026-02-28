---
category: general
date: 2026-02-28
description: C# kullanarak Aspose.Words'te font uyarılarını nasıl ele alacağınızı
  ve eksik fontları nasıl tespit edeceğinizi öğrenin. Tam kodlu adım adım rehber.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: tr
og_description: Aspose.Words'ta yazı tipi uyarılarını yönetin ve çalıştırmaya hazır
  bir C# örneğiyle eksik yazı tiplerini tespit edin. Adımları izleyin ve çıktıyı görün.
og_title: Aspose.Words'ta Yazı Tipi Uyarılarını Ele Alın – Tam Kılavuz
tags:
- Aspose.Words
- C#
- Document Loading
title: Aspose.Words'ta Yazı Tipi Uyarılarını Yönet – Eksik Yazı Tiplerini Tespit Et
url: /tr/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words’te Yazı Tipi Uyarılarını Yönetme – Eksik Yazı Tiplerini Tespit Etme

Bir Word belgesi yüklerken **yazı tipi uyarılarını yönetmek** gerektiğinde ve bazı metinlerin neden garip göründüğünü merak ettiğiniz oldu mu? Tek başınıza değilsiniz. Eksik yazı tipleri, görsel düzeni sessizce bozabilen ikame uyarılarına neden olur ve **eksik yazı tiplerini tespit etmezseniz** neyin yanlış gittiğini asla öğrenemezsiniz.

Bu öğreticide, Aspose.Words’ün `IWarningCallback` özelliğini kullanarak **yazı tipi uyarılarını yönetmenin** pratik bir yolunu göstereceğiz. Rehberin sonunda, her yazı tipi ikamesi olayını görebilecek, kaydedebilecek ve hatta yüklemeyi iptal etmeye karar verebileceksiniz. Harici belgeler yok, sadece tek bir kopyala‑yapıştır‑hazır örnek.

## Neler Öğreneceksiniz

- Yalnızca yazı tipi ikamesi uyarılarına yanıt veren özel bir uyarı işleyicisi oluşturma.  
- İşleyiciyi `LoadOptions`’a ekleyerek her belge yüklemesinin bu işleyiciden geçmesini sağlama.  
- Çıktıyı konsolda doğrulama ve her uyarının ne anlama geldiğini anlama.  

**Önkoşullar**

- .NET 6.0 veya üzeri (kod .NET Framework 4.6+ ile de çalışır).  
- NuGet üzerinden kurulan Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Makinenizde yüklü olmayan bir yazı tipine referans veren bir Word dosyası (ör. özel bir kurumsal yazı tipi).  

Eğer bunlardan birine sahip değilseniz, şimdi edinin—aksi takdirde, başlayalım.

## Aspose.Words’te Yazı Tipi Uyarılarını Nasıl Yönetirsiniz

Aşağıda tam, çalıştırılabilir program yer alıyor. `using` ifadelerinden `Main` metoduna kadar her şeyi içeriyor, böylece bir konsol uygulamasına yapıştırıp **F5** tuşuna basabilirsiniz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Beklenen konsol çıktısı** (belge, yüklü olmayan bir yazı tipi kullanıyorsa):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Belge **eksik yazı tipi içermiyorsa**, uyarı satırı hiç görünmez—yani **eksik yazı tiplerini yalnızca gerektiğinde** tespit etmiş olursunuz.

### Bunun Neden İşlediği

Aspose.Words, bir dosyayı ayrıştırırken karşılaştığı her kritik olmayan sorun için bir `WarningInfo` fırlatır. `IWarningCallback` uygulayarak bu akışa bir kanca eklemiş olursunuz. `WarningType.FontSubstitution` bayrağı, kütüphanenin istenen bir yazı tipini bir yedekle değiştirmek zorunda kaldığını tam olarak bildirir. Bu, **yazı tipi uyarılarını yönetmenin** en güvenilir yoludur çünkü yükleme sırasında, belge nesne modeline dokunmadan önce çalışır.

## Uygulamanızı Bozmadan Eksik Yazı Tiplerini Tespit Etme

Bazen eksik bir yazı tipini ölümcül bir hata olarak ele almak isteyebilirsiniz—belki marka yönergeleriniz hiçbir ikameyi yasaklıyor. İşleyiciyi yalnızca kaydetmek yerine bir istisna fırlatacak şekilde değiştirebilirsiniz:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Artık `new Document(...)` etrafındaki `try…catch` bloğu sorunu yakalayacak ve iptal edip etmeyeceğinize, yedekleme yapıp yapmayacağınıza ya da kullanıcıyı bilgilendireceğinize karar verebileceksiniz.

## Bonus: UI Uygulamasında Uyarıları Görselleştirme

WinForms veya WPF uygulaması geliştiriyorsanız, `Console.WriteLine` yerine UI‑dostu bir çağrı ile değiştirin:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

Böylece son kullanıcılar uyarıyı anında görür ve **yazı tipi uyarılarını** tüm platformlarda tutarlı bir şekilde yönetmeye devam edersiniz.

## Yaygın Tuzaklar & Uzman İpuçları

- **Tuzak:** `WarningCallback`’i ayarlamamak. Varsayılan davranış yazı tipi uyarılarını yok saymaktır, bu yüzden hiç görmezsiniz.  
  **Uzman ipucu:** Uyarı işleyicisine sadece ihtiyacınız olsa bile bir `LoadOptions` örneği oluşturun. Bu ucuz ve açıktır.  

- **Tuzak:** Windows dışı bir işletim sisteminde yanlış yol ayırıcı kullanmak.  
  **Uzman ipucu:** `Path.Combine` ya da ham string literal (`@"C:\Docs\MissingFont.docx"` Windows’da çalışır; Linux’da `"/home/user/docs/MissingFont.docx"` kullanın).  

- **Tuzak:** Uyarının gömülü yazı tipleri için tetikleneceğini varsaymak.  
  **Uzman ipucu:** Gömülü yazı tipleri mevcut kabul edilir, bu yüzden ikame uyarısı çıkmaz. Gerçekten *eksik* yazı tipleriyle test edin, işleyicinin çalıştığını görün.  

- **Tuzak:** Her uyarı tipini aşırı kaydetmek.  
  **Uzman ipucu:** Gösterildiği gibi `WarningType.FontSubstitution` ile filtreleyin—bu, konsolu temiz tutar ve **eksik yazı tiplerini tespit etme** senaryosuna odaklanır.  

## Tam Çalışan Örnek Özeti

Yorum satırları olmadan, temiz bir görünüm tercih edenler için programın tamamı tekrar:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Kopyala, yapıştır, çalıştır—konsolunuz artık **yazı tipi uyarılarını** otomatik olarak **yönetip eksik yazı tiplerini tespit edecektir**.

## Sonraki Adımlar

- **Dosyaya kaydet:** Üretim ortamı izleme için `Console.WriteLine` yerine bir logger (ör. NLog) kullanın.  
- **Toplu işleme:** Bir klasördeki belgeleri döngüye alarak tüm yazı tipi ikamesi olaylarını CSV raporunda toplayın.  
- **Otomatik yazı tipi kurulumu:** Uyarı işleyicisine, yükleme devam etmeden önce eksik yazı tiplerini kurumsal bir depodan indirme mantığını ekleyin.  

Bu uzantıların her biri, **yazı tipi uyarılarını** temiz ve yeniden kullanılabilir bir şekilde yönetme temel fikri üzerine inşa edilmiştir.

---

*İyi kodlamalar! **Eksik yazı tiplerini tespit ederken** herhangi bir tuhaflıkla karşılaşırsanız, aşağıya yorum bırakın. Sorunları çözmenize memnuniyetle yardımcı olurum.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}