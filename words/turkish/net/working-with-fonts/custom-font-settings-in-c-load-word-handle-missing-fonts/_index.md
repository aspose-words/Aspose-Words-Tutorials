---
category: general
date: 2026-03-08
description: Özel yazı tipi ayarları, yazı tipi ayarlarını belirlemenizi, Word belgesini
  güvenli bir şekilde yüklemenizi ve Aspose.Words ile eksik yazı tiplerini yönetmenizi
  sağlar.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: tr
og_description: Özel yazı tipi ayarları, yazı tipi ayarlarını belirlemenizi, Word
  belgesini güvenli bir şekilde yüklemenizi ve Aspose.Words ile eksik yazı tiplerini
  yönetmenizi sağlar.
og_title: C#'ta Özel Yazı Tipi Ayarları – Word'ü Yükle ve Eksik Yazı Tiplerini Yönet
tags:
- Aspose.Words
- C#
- Font Management
title: C#'ta Özel Yazı Tipi Ayarları – Word'ü Yükle ve Eksik Yazı Tiplerini Yönet
url: /tr/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta Özel Yazı Tipi Ayarları – Word'ü Yükle ve Eksik Yazı Tiplerini Ele Al

Bir Word dosyası yüklü olmayan yazı tiplerine referans verdiğinde **custom font settings** nasıl çalıştığını hiç merak ettiniz mi? Bu yaygın bir sorun—belgeniz bir makinede düzgün görünür, ancak başka bir makinede aniden tüm paragraflar bir yedek yazı tipine geçer.  

İyi haber? Aspose.Words ile **set font settings**, **load Word document** içeriğini ve **handle missing fonts** işlemlerini tek bir düzenli akışta yapabilirsiniz. Aşağıda, tam olarak nasıl yapılacağını gösteren, çalıştırmaya hazır bir örnek ve her adımın “neden”ini bulacaksınız.

## Neler Öğreneceksiniz

Bu rehberde şunları ele alacağız:

* `LoadOptions` nesnesi oluşturma ve bir `FontSettings` örneği ekleme.  
* Hangi yazı tiplerinin değiştirildiğini görebilmeniz için bir uyarı geri araması (callback) kaydetme.  
* Eksik yazı tipleri olabilecek bir DOCX dosyasını yükleme ve değişim ayrıntılarını konsola yazdırma.  

Sonunda, her eksik‑yazı tipi senaryosunun kaydedildiğini ve daha sonra ele alınabileceğini bilerek C# uygulamanızı güvenle dağıtabileceksiniz.

> **Önkoşul:** NuGet üzerinden kurulu Aspose.Words for .NET (v23.12 veya daha yeni) ve C# konsol uygulamaları hakkında temel bir aşinalık.

---

## Özel Yazı Tipi Ayarları – LoadOptions Yapılandırması

İlk olarak bir `LoadOptions` nesnesine ihtiyacınız var. Bu, Aspose.Words'e gelen dosyayı nasıl işleyeceğini söyler. Yeni bir `FontSettings` örneği atayarak kütüphaneye özel yazı tiplerini arayacağı bir yer sağlarız.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Neden Önemli:**  
`FontSettings`'i atladığınızda, Aspose.Words sistemin varsayılan yazı tipi koleksiyonuna geri döner. Bu, eksik bir yazı tipinin sessizce değiştirileceği ve hangi yazı tiplerinin değiştirildiğini bilmeyeceğiniz anlamına gelir. Açık bir `FontSettings` konteyneri oluşturarak arama süreci üzerinde tam kontrol elde edersiniz.

---

## LoadOptions Üzerinde Yazı Tipi Ayarlarını Belirleme

Artık bir `FontSettings` nesnemiz olduğuna göre, ona nereye işaret edeceğinizi merak edebilirsiniz. Genellikle uygulamanızla birlikte gönderdiğiniz yazı tiplerini içeren bir klasör eklersiniz:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Özel bir klasörünüz yoksa bu bloğu atlayabilirsiniz—Aspose.Words yine de uyarı geri araması (warning callback) aracılığıyla eksik yazı tiplerini raporlayacaktır.*

**Pro ipucu:** Yazı tipleriniz alt klasörlerde dağılmışsa `recursive: true` bayrağını kullanın. Böylece her yolu manuel olarak eklemek zorunda kalmazsınız.

---

## Özel Yazı Tipi Ayarlarıyla Word Belgesi Yükleme

Seçenekler hazır olduğunda, belgeyi yüklemek çok kolaydır. `Document` yapıcı (constructor) dosya yolunu ve az önce oluşturduğumuz `LoadOptions`'ı kabul eder.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**Arka planda ne oluyor?**  
Aspose.Words DOCX'i ayrıştırır, her `<w:font>` referansını kontrol eder ve sağladığınız `FontSettings`'e başvurur. Bir yazı tipi bulunamazsa, `FontSubstitution` türünde bir uyarı tetikler. Bir sonraki gösterilen özel işleyicimiz bu uyarıları yakalar.

---

## Uyarı Geri Aramasıyla Eksik Yazı Tiplerini Ele Alma

`IWarningCallback` arayüzü, yükleme sırasında ortaya çıkan herhangi bir soruna yanıt vermenizi sağlar. Uygulaması basittir:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Belge yüklendiğinde, her eksik yazı tipi aşağıdaki gibi bir satır oluşturur:

```
Font substituted: Arial -> Liberation Sans
```

**Bunu neden kaydetmelisiniz:**  
Üretim ortamında bu mesajları bir dosyaya veya telemetri sistemine yönlendirebilir, hangi yazı tiplerini paketlemeniz veya lisanslamanız gerektiğini kolayca görebilirsiniz.

---

## Tam Çalışan Örnek

Aşağıda her şeyi bir araya getiren bağımsız bir konsol programı var. Yeni bir .NET Core konsol projesine kopyalayıp yapıştırın ve **Run** (Çalıştır) tuşuna basın.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Beklenen çıktı** (`input.docx`'in sahip olmadığınız bir yazı tipi kullandığını varsayarsak):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Tüm yazı tipleri mevcutsa, yalnızca son onay satırını göreceksiniz.

---

## Sık Sorulan Sorular & Kenar Durumları

| Question | Answer |
|----------|--------|
| **Eksik yazı tiplerini PDF'e gömmem gerekirse ne olur?** | Yükleme sonrasında, `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` kodunu çağırın ve ardından gömme özelliğini `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;` ile etkinleştirin. |
| **Uyarıları kaydetmek yerine bastırabilir miyim?** | Evet—`loadOptions.WarningCallback = null;` olarak ayarlayın veya geri aramayı (callback) yazı tipi dışı uyarıları yok sayacak şekilde uygulayın. |
| **Bu `.doc` ve `.rtf` dosyalarıyla çalışır mı?** | Kesinlikle. Aynı `LoadOptions` nesnesi, Aspose.Words tarafından desteklenen herhangi bir formatta geçerlidir. |
| **Geri arama (callback) iş parçacığı güvenli mi?** | Geri arama, belgeyi yükleyen aynı iş parçacığında çalışır, bu yüzden konsola güvenle yazabilirsiniz. Çok iş parçacıklı senaryolarda, eşzamanlı bir koleksiyon veya bir kayıt (logging) çerçevesi kullanın. |

---

## Pro İpuçları & Tuzaklar

* **Pro ipucu:** Hedef makinede yüklü olmayan bir yazı tipini gönderiyorsanız, onu `SetFontsFolder`'a verdiğiniz klasöre ekleyin. Bu, belirleyici (deterministik) bir render garantiler.
* **Lisanslamaya dikkat edin:** Bazı yazı tiplerinin gömme için ticari lisansları gerekir. Paketlemeden önce her zaman yazı tipinin EULA'sını doğrulayın.
* **Performans notu:** Büyük yazı tipi kütüphanelerini yüklemek belge ayrıştırmayı yavaşlatabilir. Klasörü hafif tutun—yalnızca gerçekten ihtiyacınız olan yazı tiplerini ekleyin.
* **Kenar durumu:** Bir belge, yazı tipini aile adı yerine *PostScript adı* ile referans aldığında, yazı tipi dosyası arama yolunda bulunduğu sürece Aspose.Words yine de çözer.

---

## Sonuç

Artık C#'ta **custom font settings** kullanmak için eksiksiz, üretim‑hazır bir deseniniz var. `LoadOptions`'ı yapılandırarak, bir uyarı geri araması (warning callback) kaydederek ve isteğe bağlı olarak özel bir yazı tipi klasörüne işaret ederek, **set font settings**, **load Word document** içeriğini güvenilir bir şekilde yükleyebilirsiniz.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}