---
category: general
date: 2026-01-06
description: Aspose.Words kullanarak belgeleri yüklerken uyarıların nasıl alınacağını
  ve yazı tiplerini nasıl izleyebileceğinizi öğrenin. Bu kılavuz, uyarı geri aramaları
  ve yazı tipi ikame takibini kapsar.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: tr
og_description: Aspose.Words'ta uyarıları nasıl alabilirsiniz? Belgeleri yüklerken
  yazı tiplerini izlemek ve ikame mesajlarını yakalamak için bu adım adım öğreticiyi
  izleyin.
og_title: Aspose.Words'ta Uyarıları Almak – Yazı Tiplerini İzleme
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Aspose.Words'te Uyarıları Nasıl Alırsınız – C#'ta Yazı Tiplerini İzleme
url: /tr/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words'ta Uyarıları Nasıl Alırsınız – C#'ta Yazı Tiplerini İzleme

Bir Word belgesinde yüklü olmayan yazı tipleri bulunduğunda **uyarıları nasıl alırsınız**? Bu yaygın bir sorun—uygulamanız eksik yazı tiplerini sessizce değiştirir ve neyin değiştiğini asla bilmezsiniz. İyi haber şu ki, Aspose.Words'ün uyarı sistemine bağlanabilir ve **yazı tiplerini izleyebilirsiniz** gerçek zamanlı olarak.

> **Pro ipucu:** Belge‑dönüştürme hattı oluşturuyorsanız, eksik yazı tiplerini erken kaydetmek, sonraki aşamalarda ortaya çıkabilecek kötü düzen sürprizlerinden sizi korur.

## İhtiyacınız Olanlar

- **Aspose.Words for .NET** (en son sürüm; API v23.10'dan beri değişmedi)
- .NET geliştirme ortamı (Visual Studio, Rider veya C# uzantılı VS Code)
- Yüklü olmayan bir yazı tipine referans veren örnek bir `.docx` (ör. **“NonExistentFont”**)

Hepsi bu—Aspose.Words dışında ekstra bir NuGet paketi gerekmez.

## Adım 1 – Uyarı Toplayıcıyı Kurun (Başlıkta Birincil Anahtar Kelime)

İlk olarak, uyarıların gerçekleştiği anda saklanacağı bir yere ihtiyacınız var. Aspose.Words, bu amaçla `LoadOptions` üzerindeki `WarningCallback` özelliğini sunar.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Neden önemli:**  
Kütüphane eksik bir yazı tipiyle karşılaştığında istisna fırlatmaz; bir `WarningInfo` nesnesi üretir. Bir toplayıcı bağlayarak her değiştirme olayını tam olarak görebilir, **yazı tiplerini izleyebilir** ve konsolunuzu alakasız mesajlarla kirletmezsiniz.

## Adım 2 – Uyarı‑Etkin Seçeneklerle Belgeyi Yükleyin

Şimdi dosyayı gerçekten okuyoruz. Önceki adımda hazırladığımız `LoadOptions`, yazı tipiyle ilgili tüm uyarıların yakalanmasını sağlar.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**Arka planda ne oluyor?**  
Aspose.Words Word dosyasını ayrıştırır, yazı tiplerini çözer ve istenen bir yazı tipini bulamadığında, genellikle Arial olan bir yedek yazı tipine geçer. Bu yedekleme, `WarningType.FontSubstitution` uyarısını tetikler ve bu uyarı `warningCollector` içine düşer.

## Adım 3 – Toplanan Uyarıları İnceleyin (Birincil Anahtar Kelime Tekrar Görünür)

Belge yüklendikten sonra, sadece `warningCollector` üzerinde döngü kurar ve tüm yazı tipi‑değiştirme mesajlarını yazdırırız.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Beklenen çıktı** (eksik yazı tipi *“FancyScript”* varsayıldığında):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Belge birden fazla bilinmeyen yazı tipi içeriyorsa, her bir değiştirme için bir satır göreceksiniz—kayıt tutma veya uyarı için mükemmel.

## Adım 4 – İsteğe Bağlı: Uyarı Bilgilerini Günlüğe Kaydetme veya Saklama

Üretim ortamında muhtemelen sadece bir `Console.WriteLine`'dan daha fazlasını istersiniz. İşte uyarıları daha sonra analiz için bir JSON dosyasına yazan hızlı bir örnek.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Artık izleme panosuna besleyebileceğiniz kalıcı bir kaydınız var, hatta eksik yazı tipleri için otomatik bir istek tetikleyebilirsiniz.

## Adım 5 – Sonucu Doğrulayın ve Temizleyin

Programı çalıştırın. Değiştirme mesajlarını görürseniz, başarıyla **uyarıları aldınız** ve artık aktif olarak **yazı tiplerini izliyorsunuz** demektir. Hiçbir şey görünmezse, test belgesinin gerçekten makinede yüklü olmayan bir yazı tipine referans verdiğini iki kez kontrol edin.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

Sıfır sayısı genellikle şunu gösterir:

1. Tüm yazı tipleri çözüldü (belki yazı tipi yerel olarak *yüklüdür*), ya da
2. Belge, değiştirme gerektiren herhangi bir yazı tipi referansı içermiyordu.

## Yaygın Tuzaklar ve Nasıl Kaçınılır

| Tuzak | Neden Oluşur | Çözüm |
|---------|----------------|-----|
| **Uyarı görünmüyor** | Yazı tipi aslında sistemde mevcut veya belge yalnızca yerleşik yazı tiplerini kullanıyor. | Kaynak dosyadaki yazı tipini imkânsız bir isimle (ör. `XYZ123`) yeniden adlandırın ve tekrar deneyin. |
| **Çok fazla uyarı (gürültü)** | Toplayıcıyı temizlemeden bir döngü içinde birçok belge yüklüyorsunuz. | Her belge için `WarningInfoCollection`'ı yeniden oluşturun veya işlem sonrası `warningCollector.Clear()` çağırın. |
| **Performans etkisi** | Disk'e aşırı günlükleme toplu işleme yavaşlatabilir. | Uyarıları bellekte biriktirin ve toplu olarak yazın, ya da asenkron dosya I/O kullanın. |
| **Eksik `using Aspose.Words.Loading;`** | `LoadOptions` sınıfı bu ad alanında bulunur. | Adım 1'de gösterildiği gibi eksik `using` yönergesini ekleyin. |

## Çözümü Genişletme – Diğer Uyarı Türlerini İzleme

Yazı tipi değiştirme en belirgin olsa da, Aspose.Words şu durumlar için uyarı üretebilir:

- **Kullanımdan kaldırılmış özellikler** (`WarningType.Deprecated`),
- **Olası veri kaybı** (`WarningType.DataLoss`),
- **Desteklenmeyen dosya formatları** (`WarningType.UnsupportedFileFormat`).

Bu uyarıları da yakalamak için Adım 3'teki filtreyi genişletebilirsiniz:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

Bu sayede sadece **yazı tiplerini nasıl izlersiniz** değil, aynı zamanda uygulamanızın karşılaşabileceği herhangi bir senaryo için **uyarıları nasıl alırsınız** da bilirsiniz.

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Çalıştırın:** Projeyi derleyin, çalıştırın ve uyarıların yazdırıldığını ve kaydedildiğini göreceksiniz. Bu, Aspose.Words ile **uyarıları nasıl alırsınız** ve **yazı tiplerini nasıl izlersiniz** sorularının tam yanıtıdır.

## Sonuç

Artık Aspose.Words'tan, özellikle yazı tipi‑değiştirme senaryoları için **uyarıları nasıl alacağınızı** ve belge‑yükleme sürecinde **yazı tiplerini nasıl izleyebileceğinizi** biliyorsunuz. Bir `WarningCallback` ekleyerek, toplanan `WarningInfo` nesnelerini döngüye alarak ve isteğe bağlı olarak verileri kalıcı hale getirerek, eksik‑yazı tipi olayları üzerinde tam şeffaflık elde edersiniz—herhangi bir belge‑işleme hattı için temel bir yetenek.

Sonraki adımlar? Uyarı filtresini veri‑kaybı veya kullanımdan kaldırılmış‑özellik uyarılarını kapsayacak şekilde genişletmeyi deneyin veya JSON kaydını Grafana gibi bir izleme panosuna entegre edin. Aynı desen tüm uyarı türleri için çalışır, böylece Aspose.Words'ün size fırlattığı herhangi bir sorunu izlemek için iyi donanımlı olursunuz.

Kodlamaktan keyif alın ve belgelerinizin her zaman beklediğiniz gibi render edilmesini dileriz! 

<img src="font-warnings.png" alt="Aspose.Words'ta uyarıları nasıl alırsınız" style="max-width:100%;">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}