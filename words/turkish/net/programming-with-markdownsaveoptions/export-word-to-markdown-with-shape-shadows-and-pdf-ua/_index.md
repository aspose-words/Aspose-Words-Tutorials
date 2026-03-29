---
category: general
date: 2026-03-28
description: Aspose.Words ile C#’ta Word belgesini markdown formatına nasıl dışa aktaracağınızı,
  şekil gölgesi ekleyeceğinizi ve PDF/UA olarak nasıl kaydedeceğinizi adım adım öğrenin
  – rehber.
draft: false
keywords:
- export word to markdown
- add shape shadow
- save pdf ua
- Aspose.Words markdown
- C# document conversion
language: tr
og_description: Word dosyasını markdown formatına aktar, şekil gölgesi ekle ve Aspose.Words
  ile C# kullanarak PDF/UA olarak kaydet. Kod ve ipuçlarıyla eksiksiz bir öğretici.
og_title: Word'ü Markdown'a Dışa Aktar – Şekil Gölgesi Ekle & PDF/UA Kaydet
tags:
- Aspose.Words
- C#
- Markdown
- PDF/UA
title: Word'ü Şekil Gölgelendirmeleri ve PDF/UA ile Markdown'a Dışa Aktar
url: /tr/net/programming-with-markdownsaveoptions/export-word-to-markdown-with-shape-shadows-and-pdf-ua/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'ü Markdown'a Şekil Gölgelendirmeleri ve PDF/UA ile Dışa Aktarma

Word'ü **markdown'a dışa aktarmak** isterken bu şık şekil gölgelerini korumak ve aynı zamanda PDF/UA uyumluluğunu sağlamak mı istediniz? Yalnız değilsiniz. Birçok geliştirici, formatları değiştirirken görsel bütünlüğü korumaya çalışırken, özellikle erişilebilirlik (PDF/UA) bir zorunluluk olduğunda, bir duvara çarpar.

Bu rehberde, **Word'ü markdown'a dışa aktarma**, bir çizime **şekil gölgesi ekleme** ve sonunda **PDF/UA olarak kaydetme** işlemlerini gösteren tam, çalıştırılabilir bir örnek üzerinden adım adım ilerleyeceğiz. .NET için Aspose.Words'ü kullanacağız; bu, sağlam belge dönüşümü için başvurulan kütüphanedir. Harici betikler, el yapımı ayrıştırıcılar yok—sadece bugün bir konsol uygulamasına ekleyebileceğiniz temiz C# kodu.

> **Pro tip:** Henüz Aspose.Words'ü kurmadıysanız, en son NuGet paketini (`Install-Package Aspose.Words`) alın – .NET 6+, .NET Framework 4.8 ve hatta .NET Core ile çalışır.

## Gereksinimler

- **Visual Studio 2022** (veya .NET 6+ destekleyen herhangi bir IDE)
- **Aspose.Words for .NET** (NuGet sürümü 23.8 veya daha yeni)
- En az bir şekil (ör. bir dikdörtgen) içeren örnek bir `input.docx`
- Temel C# bilgisi – sözdizimini basit tutacağız

Bu ön koşulları tamamladıktan sonra, başlayalım.

![Word'den markdown'a dışa aktarma akışını gösteren diyagram](export_word_to_markdown_diagram.png){alt="export word to markdown örneği"}

## Adım 1: Word Belgesini Kurtarma Modunda Yükleme  

Herhangi bir şeyi değiştirmeden önce belgeyi belleğe almamız gerekir. **RecoveryMode.Recover** ile yüklemek, kaynakta yüklü olmayan fontlar kullanıldığında ortaya çıkan font‑değiştirme uyarılarını yakalar; bu, eksik fontlarla çalışırken oldukça kullanışlıdır.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

// 1️⃣ Load the document while collecting warnings
var loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover,
    WarningCallback = new WarningInfoCollection()
};

Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Neden RecoveryMode?*  
Orijinal dosya eksik fontlara referans veriyorsa, Aspose bunları değiştirir ve bir uyarı verir. Bu uyarıları yakalayarak daha sonra kaydedebiliriz—hata ayıklama ve uyumluluk raporları için faydalıdır.

## Adım 2: Şekil Gölgesi Ekleme  

Belge yüklendiğine göre, bir şeklin görünümünü geliştirelim. İlk `Shape` düğümünü alıp hafif bir gölge ekleyeceğiz.

```csharp
// 2️⃣ Find the first shape and enable its shadow
Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
shape.ShadowFormat.Visible = true;
shape.ShadowFormat.BlurRadius = 4;   // soft edges
shape.ShadowFormat.Distance = 2;    // how far the shadow is from the shape
shape.ShadowFormat.Angle = 30;      // direction of the light source
```

*Neden gölge ayarlanıyor?*  
Gölge, derinlik katarak şeklin Word içinde ve dışa aktarılan markdown görüntüsünde (şekli daha sonra bir görüntüye dönüştürürseniz) öne çıkmasını sağlar. Ayrıca görsel özelliklerin dönüşüm sürecinden geçip geçmediğini hızlıca test etmenin bir yoludur.

## Adım 3: Belgeyi Markdown'a Dışa Aktarma (LaTeX Matematiği ile)  

Aspose.Words bir Word dosyasını temiz markdown'a dönüştürebilir. Burada ayrıca OfficeMath denklemlerini LaTeX olarak dışa aktarmasını söylüyoruz; bu, bilimsel belgeler için de‑facto standarttır.

```csharp
// 3️⃣ Configure markdown export options
var markdownOptions = new MarkdownSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
    // Store all extracted images in a dedicated folder
    ResourceSavingCallback = (s, e) =>
    {
        string assetsFolder = "YOUR_DIRECTORY/assets";
        Directory.CreateDirectory(assetsFolder);
        e.FileName = Path.Combine(assetsFolder, e.FileName);
    }
};

// Save as markdown
doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);
```

*Gördükleriniz:*  
- `output.md` dosyası standart markdown sözdizimiyle.  
- Tüm gömülü görüntüler (gölge eklediğimiz şekil dahil) `assets/` altında kaydedilir.  
- Tüm denklemler `$…$` LaTeX blokları olarak görünür, MathJax veya KaTeX ile render edilmeye hazır.

## Adım 4: Aynı Belgeyi PDF/UA Olarak Kaydetme  

PDF/UA (PDF/Universal Accessibility), PDF'nin ISO 14289‑1 standardına uygun olmasını sağlar. Ayrıca, yüzen şekilleri satır içi etiketler olarak kaydetmeye zorlayacağız; bu, erişilebilirlik etiketlemeyi basitleştirir.

```csharp
// 4️⃣ Set up PDF/UA compliance and inline floating shapes
var pdfOptions = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfUAX2,
    ExportFloatingShapesAsInlineTag = true
};

// Save the PDF/UA file
doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*Neden PDF/UA?*  
Eğer hedef kitleniz ekran okuyucu kullanıcılarını içeriyorsa veya yasal erişilebilirlik standartlarını karşılamanız gerekiyorsa, PDF/UA doğru seçimdir. `ExportFloatingShapesAsInlineTag` bayrağı, yüzen nesnelerin mantıksal okuma sırasını bozulmasını önler.

## Adım 5: Font‑Değiştirme Uyarılarını İnceleme  

Dönüştürme adımlarından sonra, **Adım 1**'de yakaladığımız font‑ile ilgili uyarıları göstermek iyi bir uygulamadır.

```csharp
// 5️⃣ List font‑substitution warnings (if any)
var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
foreach (var warning in warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"⚠️ {warning.Description}");
}
```

Eğer *“Font 'Calibri' 'Arial' ile değiştirildi”* gibi mesajlar görürseniz, hangi fontların eksik olduğunu tam olarak bilirsiniz ve bir yedek ekleyecek misiniz yoksa eksik fontu uygulamanızla birlikte mi dağıtacaksınız karar verebilirsiniz.

## Tam Çalışan Örnek  

Hepsini bir araya getirerek, yeni bir konsol projesine kopyalayıp yapıştırabileceğiniz tam program aşağıdadır:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load with recovery mode and capture warnings
        var loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Recover,
            WarningCallback = new WarningInfoCollection()
        };
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Add a shadow to the first shape
        Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.BlurRadius = 4;
        shape.ShadowFormat.Distance = 2;
        shape.ShadowFormat.Angle = 30;

        // Export to Markdown with LaTeX math and custom assets folder
        var markdownOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ResourceSavingCallback = (s, e) =>
            {
                string assetsFolder = "YOUR_DIRECTORY/assets";
                Directory.CreateDirectory(assetsFolder);
                e.FileName = Path.Combine(assetsFolder, e.FileName);
            }
        };
        doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);

        // Save as PDF/UA, forcing floating shapes inline
        var pdfOptions = new PdfSaveOptions
        {
            Compliance = PdfCompliance.PdfUAX2,
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // Print any font‑substitution warnings
        var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
        foreach (var warning in warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ {warning.Description}");
        }
    }
}
```

### Beklenen Sonuç  

- `output.md` temiz markdown, LaTeX‑kodlu denklemler ve `![Shape](assets/shape0.png)` gibi görüntü bağlantıları içerir.  
- `output.pdf` Adobe Acrobat erişilebilirlik denetleyicisinden geçen PDF/UA‑uyumlu bir dosyadır.  
- Konsol çıktısı, eksik fontları takip etmenize yardımcı olacak tüm font‑değiştirme uyarılarını listeler.

## Yaygın Sorular ve Kenar Durumları  

**Belgemde birden fazla şekil olursa ne olur?**  
`doc.GetChildNodes(NodeType.Shape, true)` ile döngü yapın ve gölge ayarlarını her öğeye uygulayın.  

**Gölge rengini değiştirebilir miyim?**  
Evet—kaydetmeden önce `shape.ShadowFormat.Color = Color.Gray;` olarak ayarlayın.  

**Web dağıtımları için assets klasör yolunu ayarlamam gerekir mi?**  
Kesinlikle. Görüntüleri verimli sunmak için göreceli bir yol kullanın veya `ResourceSavingCallback` içinde bir CDN URL'si yapılandırın.  

**Markdown dışa aktarımı Word‑özel özelliklerini kaybeder mi?**  
İzlenen değişiklikler, yorumlar veya karmaşık SmartArt gibi özellikler markdown'da temsil edilmez. Bunlara ihtiyacınız varsa, yedek olarak bir PDF/UA sürümü tutun.  

## Sonuç  

Artık Aspose.Words kullanarak C# ile **Word'ü markdown'a dışa aktarma**, **şekil gölgesi ekleme** ve **PDF/UA kaydetme** konularını öğrendiniz. Tam kod örneği, font uyarılarını, kaynak yönetimini ve erişilebilirlik uyumluluğunu tek bir okunması kolay betikte ele alan üretim‑hazır bir iş akışını gösteriyor.

Sıradaki adımlar? Gölge parametrelerini değiştirin, farklı `MarkdownSaveOptions` (ör. `ExportImagesAsBase64`) ile deneyler yapın veya bu iş akışını, kullanıcıların yüklediği Word dosyalarını anında dönüştüren bir ASP.NET Core API'sine entegre edin. Ayrıca diğer çıktı formatlarıyla ilgileniyorsanız, Aspose'un **HTML**, **EPUB** veya **TIFF** dışa aktarma seçeneklerine göz atın—her biri benzer bir desen izler.

Kodlamaktan keyif alın, ve belgeleriniz her zaman istediğiniz gibi görüntülensin!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}