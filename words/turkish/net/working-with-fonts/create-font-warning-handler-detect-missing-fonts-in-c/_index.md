---
category: general
date: 2026-02-12
description: Aspose.Words'ta eksik yazı tiplerini tespit etmek ve izlemek için Yazı
  Tipi uyarı işleyicisi oluşturun. Uyarıları verimli bir şekilde nasıl kaydedeceğinizi
  öğrenin.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: tr
og_description: C#'ta eksik fontları tespit etmek için Font uyarı işleyicisi oluşturun
  ve Aspose.Words fontları değiştirdiğinde uyarıların nasıl kaydedileceğini öğrenin.
og_title: Yazı Tipi Uyarı İşleyicisi Oluştur – Eksik Yazı Tiplerini Tespit Et
tags:
- Aspose.Words
- C#
- Document Processing
title: Yazı Tipi Uyarı İşleyicisi Oluştur – C#'ta Eksik Yazı Tiplerini Tespit Et
url: /tr/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Font Uyarı İşleyicisi Oluşturma – C#'ta Eksik Yazı Tiplerini Algılamak

Hiç **font warning handler** oluşturmanız gerektiğinde, bir Word belgesinin sessizce beklemediğiniz bir yazı tipini değiştirdiği bir durumla karşılaştınız mı? Tek başınıza değilsiniz. Aspose.Words, sunucuda bulunmayan bir yazı tipine referans veren bir DOCX dosyasını yüklediğinde, sessizce varsayılan bir yazı tipine geri döner—ve düzeniniz hafifçe bozulur.  

Bu öğreticide **eksik yazı tiplerini algılamayı**, **eksik yazı tiplerini izlemeyi** ve **uyarıları nasıl kaydedeceğinizi** adım adım göstereceğiz, böylece bu yerine koymaları sizi yakalamadan önce fark edebilirsiniz. Sonunda, her yazı tipi‑yerine koyma olayını konsola (veya tercih ettiğiniz herhangi bir logger'a) yazdıran yeniden kullanılabilir bir uyarı işleyiciniz olacak. Gizem yok, sadece net ve uygulanabilir kod.

## Önkoşullar

- .NET 6.0 veya üzeri (API, .NET Framework 4.6+ için aynı)
- Aspose.Words for .NET yüklü (`dotnet add package Aspose.Words`)
- Makinenizde yüklü olmayan bir yazı tipine referans veren bir Word dosyası (ör. `MissingFont.docx`)

Bu gereksinimlere zaten sahipseniz, harika—hadi başlayalım.

## Adım 1: Uyarı Geri Çağrımıyla LoadOptions Ayarlama  

Bir **font warning handler** oluşturmak istediğinizde ilk yapmanız gereken, Aspose.Words'e bir sorunla karşılaştığında bir geri çağrı (callback) tetiklemesini söylemektir. `LoadOptions` bu yapılandırmanın konteyneridir.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Neden önemli:**  
`LoadOptions`, bir `IWarningCallback` takabileceğiniz tek yerdir. Olmasaydı, Aspose.Words uyarıları dahili olarak kaydeder ama siz hiç görmezsiniz. `FontWarningHandler` atayarak, eksik bir yazı tipi yerine konulduğunda neler olacağını tam kontrol altına alırız.

## Adım 2: FontWarningHandler Sınıfını Uygulama  

Şimdi gerçekten **font warning handler** kodunu oluşturuyoruz. Sınıf, `IWarningCallback` arayüzünü uygular ve Aspose.Words her uyarı oluşturduğunda bir `WarningInfo` nesnesi alır.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Açıklama:**  
- `info.Type`, uyarının kategorisini bize bildirir. `WarningType.FontSubstitution` ile ilgileniyoruz çünkü bu, eksik bir yazı tipini gösterir.  
- `info.Description`, *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* gibi insan tarafından okunabilir bir mesaj içerir.  
- `Console.WriteLine` ile yazdırarak **uyarıları anında kaydederiz**. Gerçek bir uygulamada bunu `ILogger`, bir dosya yazıcı ya da bir telemetri servisi ile değiştirebilirsiniz.

> **Pro ipucu:** Daha sonra raporlamak için tüm eksik yazı tiplerini toplamanız gerekiyorsa, `info.Description` değerini `List<string>` içine kaydedin, ekrana yazdırmak yerine.

## Adım 3: Yapılandırılmış LoadOptions ile Belgeyi Yükleme  

Geri çağrı yerinde olduğunda, bir belgeyi yüklemek eksik bir yazı tipi olduğunda otomatik olarak işleyicimizi tetikler.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Gördükleriniz:**  
Programı çalıştırdığınızda aşağıdakine benzer bir çıktı alırsınız:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Bu satır, **eksik yazı tiplerini başarıyla algıladığınızı** ve artık gerçek zamanlı olarak **eksik yazı tiplerini izlediğinizi** doğrular.

## Adım 4: İşleyicinin Farklı Senaryolarda Çalıştığını Doğrulama  

İşleyicinin yalnızca DOCX dosyaları için çalıştığını varsaymak kolaydır, ancak Aspose.Words birçok formatı destekler. Gömülü bir yazı tipine referans veren bir PDF ya da eski bir `.doc` dosyası yüklemeyi deneyin. Yazı tipi çözümleme hattından geçen herhangi bir format için aynı geri çağrı tetiklenir.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

PDF, yüklü olmayan bir yazı tipine referans veriyorsa aynı konsol çıktısını alırsınız. Bu, **font warning handler** çözümünüzün format bağımsız olduğunu gösterir.

## Adım 5: İşleyiciyi Genişletme – Dosyaya Günlükleme  

Konsol çıktısı demo için kullanışlıdır, ancak üretim kodu genellikle bir günlük dosyasına yazar. İşte hızlı bir değişiklik.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Artık bir yazı tipi yerine konduğunda mesaj `font-warnings.log` dosyasına eklenir. Bu, **uyarıları nasıl kaydedeceğiniz** kısmını karşılar ve kalıcı bir denetim izi sağlar.

## Adım 6: Hepsini Bir Araya Getirme – Tam, Çalıştırılabilir Örnek  

Aşağıda, bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz eksiksiz program yer alıyor. Eksik bir şey yok; sadece dosya yolunu kendi belgenizle değiştirin.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Beklenen sonuç:**  

- Konsol, her bir yerine koyma satırını yazdırır.  
- `font-warnings.log` artık her eksik‑yazı tipi olayının zaman damgalı kaydını içerir.  
- `output.pdf` dosyası, yerine konulan yazı tipleri kullanılarak oluşturulur; böylece orijinal yazı tipleri mevcut olmasa bile dönüşüm başarılı olur.

## Yaygın Sorular ve Kenar Durumları  

| Soru | Cevap |
|------|-------|
| *Belirli yazı tiplerini yok saymak istersem ne olur?* | `Warning` içinde `info.Description`'ı kontrol edip, kabul edilebilir bulduğunuz yazı tipleri için `return;` yaparak erken çıkabilirsiniz. |
| *İşleyici gömülü yazı tipleri için tetiklenir mi?* | Hayır—gömülü yazı tipleri belgeye her zaman dahil olduğundan, yerine koyma uyarısı oluşmaz. |
| *Diğer uyarı türlerini (ör. görüntü‑çözünürlük sorunları) yakalayabilir miyim?* | Kesinlikle. `if (info.Type == WarningType.FontSubstitution)` koşulunu kaldırın ya da `WarningType.ImageResolution` için ek `if` blokları ekleyin. |
| *İşleyici çoklu iş parçacığı (thread‑safe) mi?* | Gösterilen varsayılan uygulama dosyaya senkronizasyon olmadan yazar. Çok iş parçacıklı senaryolarda dosya yazmalarını bir kilit (lock) içinde tutun ya da eşzamanlı bir logger kullanın. |

## Sonraki Adımlar  

Artık **eksik yazı tiplerini nasıl kaydedeceğinizi** bildiğinize göre, şunları yapabilirsiniz:

- Bir toplu içe aktarma sürecinde **eksik yazı tiplerini algılayıp** özet bir rapor oluşturmak.  
- Birden çok belgede **eksik yazı tiplerini izleyip**, belirli bir yazı tipi sıkça göründüğünde e‑posta uyarısı göndermek.  
- **Bir izleme sistemiyle (ör. Azure Application Insights)** entegrasyon sağlayarak zaman içinde yazı tipi‑yerine koyma trendlerini ortaya çıkarmak.  

Tüm bu uzantılar, oluşturduğumuz aynı `IWarningCallback` temeli üzerine inşa edilir.

---

*Kodlamanın tadını çıkarın! Eğer özel bir yazı tipi klasörü ya da ağ paylaşımı gibi tuhaflıklarla karşılaşırsanız, aşağıya yorum bırakın. Topluluk (ve ben) font‑uyarı stratejinizi ince ayarlamanıza her zaman yardımcı olmaktan mutluluk duyar.* 

![font uyarı işleyicisi örneği oluşturma](image-placeholder.png "font uyarı işleyicisi örneği oluşturma")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}