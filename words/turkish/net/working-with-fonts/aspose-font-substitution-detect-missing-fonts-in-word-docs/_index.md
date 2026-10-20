---
category: general
date: 2026-05-04
description: Aspose font ikamesini kullanarak bir Word belgesi yüklediğinizde eksik
  fontları tespit etmeyi ve eksik font ayrıntılarını almayı öğrenin—adım adım rehber.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: tr
og_description: Aspose font ikamesini ustalaştırarak bir Word belgesi yüklerken eksik
  fontları tespit edin ve eksik font bilgilerini tam C# kodu ile alın.
og_title: Aspose Yazı Tipi Değiştirme – Word Belgelerindeki Eksik Yazı Tiplerini Tespit
  Edin
tags:
- Aspose.Words
- C#
- Font Management
title: 'Aspose Yazı Tipi Değiştirme: Word Belgelerinde Eksik Yazı Tiplerini Tespit
  Et'
url: /tr/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Word Belgelerinde Eksik Yazı Tiplerini Algıla

Farklı bir makinede bir Word belgesinin neden yanlış göründüğünü hiç merak ettiniz mi? Çoğu zaman suçlu eksik bir yazı tipidir ve **Aspose font substitution** bu boşlukları görsel bir felakete dönüşmeden tespit etmenizi sağlayan araçtır. Bu öğreticide, **detect missing fonts** işlemini **load a Word document** anında nasıl yapacağınızı ve ardından **retrieve missing font** ayrıntılarını nasıl alıp düzeltebileceğinizi veya değiştirebileceğinizi adım adım göstereceğiz.

Uyarı geri aramasını (warning callback) ayarlamaktan eksik yazı tiplerinin temiz bir listesini çekmeye kadar her şeyi ele alacağız. Sonunda, hangi yazı tiplerinin seçilmediğini tam olarak söyleyen, çalıştırmaya hazır bir C# kod parçacığına sahip olacaksınız ve bunun belge bütünlüğü için neden önemli olduğunu anlayacaksınız.

---

## Ön Koşullar – Başlamadan Önce Nelere İhtiyacınız Var

- **Aspose.Words for .NET** (v23.12 veya daha yeni sürüm önerilir).  
- .NET geliştirme ortamı (Visual Studio, Rider veya `dotnet` CLI).  
- Bilerek eksik bir yazı tipi kullanan örnek bir DOCX—`DocumentWithMissingFont.docx` olarak adlandırın.  
- Temel C# bilgisi—fantezi bir şey yok, sadece bir konsol uygulaması çalıştırabilme yeteneği.

Eğer bunlardan herhangi biri size yabancı geliyorsa, durun ve NuGet paketini kurun:

```bash
dotnet add package Aspose.Words
```

Hepsi bu. Ekstra yazı tipine, harici servislere gerek yok.

## Adım 1: Word Belgesini Yükle (ve Yazı Tipi Kontrollerini Tetikle)

İlk yapmanız gereken **load a Word document** işlemidir. Aspose.Words dosyayı ayrıştırır ve eğer referans verilen bir yazı tipini bulamazsa bir *FontSubstitution* uyarısı kuyruğa ekler. İşte yüklemeyi yapan kod:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Neden önemli:** Belgeyi erken yüklemek, Aspose'a her metin akışını, stili ve gömülü nesneyi tarama fırsatı verir. Sisteminizde veya özel yazı tipi klasöründe bir yazı tipi bulunamazsa daha sonra bir uyarı alırsınız.

## Adım 2: Değiştirme Olaylarını Yakalamak İçin Bir Uyarı Geri Araması (Warning Callback) Ekle

Aspose.Words, eksik yazı tipleri gibi sorunları size bildirmek için bir geri arama mekanizması kullanır. `IWarningCallback` uygulamasını `doc.WarningCallback`'e atayarak, her uyarıyı gerçekleştiği anda yakalayabilirsiniz.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Pro ipucu:** Birden fazla geri aramayı (ör. günlükleme, UI güncellemeleri) birleştirilmiş desenle sararak ekleyebilirsiniz, ancak bu öğreticide tek bir geri arama işleri net tutar.

## Adım 3: Font Substitution Uyarı Geri Aramasını Uygula

Şimdi işi gerçekten yapan sınıfı tanımlıyoruz. Geri arama bir `WarningInfo` nesnesi alır; `WarningType.FontSubstitution` için filtreleme yapar ve açıklamayı daha sonra kullanmak üzere saklar.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Ne oluyor:** Aspose eksik bir yazı tipiyle karşılaştığında, “Font substitution: 'Comic Sans MS' bulunamadı, yerine 'Arial' kullanılıyor.” gibi bir uyarı oluşturur. Geri aramamız bu satırı yazdırır ve kaydeder.

## Adım 4: Belgeyi İşle (İsteğe Bağlı) ve Eksik Yazı Tiplerini Topla

Sadece **detect missing fonts** yapmanız gerekiyorsa, yükleme adımı yeterlidir—uyarılar otomatik olarak tetiklenir. Ancak, birçok geliştirici bazı işlemler (ör. kaydetme, dönüştürme) yaptıktan sonra **retrieve missing font** bilgisine de ihtiyaç duyar. Aşağıda tüm uyarıların yayılmasını sağlamak için küçük bir işlem—PDF olarak kaydetme—zorlayıp, toplanan mesajları alıyoruz.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Beklenen konsol çıktısı** (örnek):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Her satırın orijinal yazı tipini ve Aspose'un seçtiği yedek yazı tipini açıkça belirttiğine dikkat edin. Bu, **aspose font substitution** raporlamasının özüdür.

## Adım 5: İleri Düzey – Değiştirmeleri Azaltmak İçin Özel Yazı Tipi Kaynaklarını Kullanma

Bazen eksik yazı tiplerine *sahipsiniz*, sadece varsayılan sistem klasöründe değiller. Aspose.Words, `FontSettings` aracılığıyla özel bir dizine işaret etmenizi sağlar. Bu adımı eklemek, değişim uyarılarının sayısını büyük ölçüde azaltabilir.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Neden ekleyelim?** Belgeleri makineler arasında dağıtıyorsanız, gerekli yazı tiplerini bilinen bir klasörde paketlemek her yerde aynı görsel görünümü sağlar. Ayrıca Aspose, geri dönmeden önce bu klasörü kontrol ettiği için **detect missing fonts** rutininiz daha doğru olur.

## Tam Çalışan Örnek

Hepsini bir araya getirerek, tek bir kopyala‑yapıştır‑hazır konsol programı burada. `Program.cs` olarak kaydedin ve `dotnet run` ile çalıştırın.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Görmeniz gereken:** Kaynak DOCX, sahip olmadığınız yazı tiplerine referans veriyorsa, konsol her değişim satırını ardından kısa bir özetle yazdırır. Tüm yazı tipleri mevcutsa, “No missing fonts were detected.” mesajını alırsınız.

## Yaygın Tuzaklar ve Nasıl Kaçınılır

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **Uyarı görünmüyor** | Belge yalnızca sistem yazı tiplerini kullanıyor veya eksik yazı tiplerini içeren bir özel klasör zaten eklediniz. | DOCX'in gerçekten mevcut olmayan bir yazı tipine referans verdiğini doğrulayın. Word'de bir paragrafı nadir bir yazı tipine (ör. “Papyrus”) değiştirebilirsiniz. |
| **Yinelenen mesajlar** | Aynı yazı tipi birden fazla çalışmada kullanılıyor, bu da birden fazla uyarıya neden oluyor. | Eğer yalnızca benzersiz bir küme gerekiyorsa, listeyi `Distinct()` ile tekilleştirin. |
| **Büyük belgelerde performans düşüşü** | Her uyarı UI iş parçacığında işlenir. | Yüklemeyi bir arka plan görevinde çalıştırın veya son‑işlem için `Parallel.ForEach` kullanın. |
| **Yanlış yedek yazı tipi** | Aspose'un varsayılan yedek yazı tipi markanızla uyuşmayabilir. | `FontSettings.SubstitutionSettings.DefaultFontName` değerini tercih ettiğiniz bir yedek (ör. “Calibri”) olarak ayarlayın. |

## Çözümü Genişletme – Eksik Yazı Tiplerini JSON’a Aktarma

Eğer eksik yazı tiplerini bir istemciye rapor etmesi gereken bir web servisi oluşturuyorsanız, listenin serileştirilmesi çok basittir:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Artık API'niz, başka bir sistemin tüketebileceği temiz bir JSON yükü döndürebilir.

## Sonuç

Bu rehberde **Aspose font substitution**'ı baştan sona gösterdik: bir Word belgesini yükleme, bir uyarı geri araması ekleme, her *detect missing fonts* olayını yakalama ve sonunda raporlama veya düzeltme için **retrieve missing font** bilgilerini elde etme. İsteğe bağlı özel yazı tipi klasörleri ekleyerek değişim listesini küçültebilir ve birkaç ek satırla sonuçları JSON olarak dışa aktarabilirsiniz.

Unutmayın, belgelerinizin görsel bütünlüğü kullandıkları yazı tiplerine bağlıdır. Burada gösterilen teknikle, beklenmedik bir yedekle karşılaşmazsınız.  
Bir sonraki adıma hazır mısınız? Bu mantığı daha büyük bir belge‑işleme hattına entegre etmeyi deneyin veya Aspose.Words'un yazı tipi gömme (`doc.FontSettings.EmbeddedFonts`) gibi diğer özelliklerini keşfedin. Olanaklar sınırsızdır ve kullanıcılarınız düzgün çıktınız için size teşekkür edecektir.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}