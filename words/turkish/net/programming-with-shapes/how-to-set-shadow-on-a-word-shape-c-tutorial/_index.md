---
category: general
date: 2026-03-30
description: C# kullanarak bir Word şekline gölge ayarlamayı öğrenin. Bu kılavuz ayrıca
  şekil gölgesi eklemeyi, şekil şeffaflığını ayarlamayı ve dikdörtgen gölgesi eklemeyi
  gösterir.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: tr
og_description: C#'ta bir Word şekline gölge nasıl eklenir? Şekil gölgesi eklemek,
  şekil şeffaflığını ayarlamak ve dikdörtgen gölgesi eklemek için bu adım adım rehberi
  izleyin.
og_title: Word Şekline Gölge Nasıl Ayarlanır – C# Öğreticisi
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Word Şekline Gölge Nasıl Ayarlanır – C# Öğreticisi
url: /tr/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Şekline Gölge Ayarlama – C# Öğreticisi

Word belgesi içinde bir şekle **gölge nasıl ayarlanır** diye hiç merak ettiniz mi, UI ile uğraşmadan? Tek başınıza değilsiniz. Birçok rapor ya da pazarlama sunumunda ince bir drop‑shadow bir dikdörtgeni öne çıkarır ve bunu programlı olarak yapmak saatler tasarruf sağlar.

Bu rehberde, sadece **gölge nasıl ayarlanır** göstermekle kalmayıp, aynı zamanda **add shape shadow**, **adjust shape transparency**, ve hatta klasik açıklama kutuları için **add rectangle shadow** konularını da kapsayan eksiksiz, çalıştırmaya hazır bir örnek üzerinden ilerleyeceğiz. Sonunda, şık görünen bir Word dosyasına (`output.docx`) sahip olacaksınız ve her özelliğin neden önemli olduğunu anlayacaksınız.

## Önkoşullar

- .NET 6+ (veya .NET Framework 4.7.2) C# derleyicisi ile  
- Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`)  
- C# ve Word nesne modeli hakkında temel bilgi  

Ek bir kütüphane gerekmez—her şey Aspose.Words içinde bulunur.

---

## Word Şekline Gölge Ayarlama – C# ile

Aşağıda tam kaynak dosyası yer alıyor. `Program.cs` olarak kaydedin ve IDE'nizden ya da `dotnet run` komutuyla çalıştırın. Kod mevcut bir `.docx` dosyasını yükler, ilk şekli (varsayılan olarak bir dikdörtgen) bulur, gölgesini etkinleştirir, birkaç görsel parametreyi ayarlar ve sonucu kaydeder.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **Gördükleriniz** – Dikdörtgen artık %30 şeffaf bir siyah drop‑shadow'a sahip, 5 pt sağa ve aşağı kaydırılmış, hafif bir bulanıklıkla. `output.docx` dosyasını Word'de açarak doğrulayın.

## Şekil Şeffaflığını Ayarlama – Neden Önemli

Şeffaflık sadece estetik bir ayar değildir; okunabilirliği etkiler. 0.0 değeri gölgeyi tamamen opak yapar, 1.0 ise tamamen gizler. Yukarıdaki kod parçasında `0.3` kullandık ve bu, hem açık hem koyu arka planlarda çalışan ince bir etki sağladı. İstediğiniz gibi denemekten çekinmeyin:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Unutmayın, **adjust shape transparency** şeklin dolgu rengine de uygulanabilir, eğer yarı şeffaf bir dikdörtgene ihtiyacınız varsa.

## Farklı Nesnelere Şekil Gölgesi Ekleme

Kullandığımız kod bir `Shape` nesnesini hedef alır, ancak aynı `ShadowFormat` özellikleri **Image**, **Chart** ve hatta **TextBox** nesnelerinde de bulunur. İşte kopyalayıp yapıştırabileceğiniz hızlı bir örüntü:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

Dolayısıyla bir logoya ya da dekoratif bir ikona **add shape shadow** ekliyor olun, yaklaşım aynı kalır.

## Herhangi Bir Şekle Gölge Ekleme – Kenar Durumları

1. **Shape without a bounding box** – Bazı Word şekilleri (örneğin serbest çizimler) gölgeyi desteklemez. `ShadowFormat.Visible` ayarlamaya çalışmak sessizce başarısız olur. Güvenlik için `shape.IsShadowSupported` kontrol edin.  
2. **Older Word versions** – Gölge özellikleri Word 2007+ özelliklerine karşılık gelir. Word 2003'ü desteklemeniz gerekiyorsa, dosya açıldığında gölge yok sayılır.  
3. **Multiple shadows** – Aspose.Words şu anda bir şekil başına tek bir gölgeyi destekler. Çift katmanlı bir etki istiyorsanız, şekli kopyalayın, konumunu kaydırın ve farklı gölge ayarları uygulayın.

## Dikdörtgen Gölgesi Ekleme – Gerçek Dünya Kullanım Durumu

Düşünün ki üç aylık bir rapor oluşturuyorsunuz ve her bölüm başlığı renkli bir dikdörtgen. **add rectangle shadow** eklemek sayfaya “kart‑gibi” bir görünüm kazandırır. Adımlar temel örnekle aynı; sadece hedeflediğiniz şeklin gerçekten bir dikdörtgen olduğundan emin olun (`shape.ShapeType == ShapeType.Rectangle`). Eğer dikdörtgeni sıfırdan oluşturmanız gerekiyorsa, aşağıdaki kod parçasına bakın:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

Bu eklemeyle tam programı çalıştırdığınızda, istenen **add rectangle shadow** etkisini zaten taşıyan yeni bir dikdörtgen elde edeceksiniz.

![Word shape with shadow](placeholder-image.png){alt="Word'de bir şekle gölge nasıl ayarlanır"}

*Şekil: Gölge ayarları uygulandıktan sonra dikdörtgen.*

## Hızlı Özet (Madde‑Madde Hızlı Kılavuz)

- **Yükle** the document with `new Document(path)`.  
- **Bul** the shape via `doc.GetChild(NodeType.Shape, index, true)`.  
- **Etkinleştir** shadow: `shape.ShadowFormat.Visible = true;`.  
- **Renk ayarla** with any `System.Drawing.Color`.  
- **Şeffaflığı ayarla** (`0.0–1.0`) to control opacity.  
- **OffsetX / OffsetY** move the shadow horizontally/vertically (points).  
- **BlurRadius** softens the edge—higher values = fuzzier shadow.  
- **Kaydet** the file and open it in Word to see the result.

## Sonraki Denemeler

- **Dynamic colors** – Gölge rengini bir temadan ya da kullanıcı girişinden alın.  
- **Conditional shadows** – Şeklin genişliği bir eşiği aştığında yalnızca gölge uygula.  
- **Batch processing** – Bir belgedeki tüm şekiller üzerinde döngü yaparak **add shape shadow** otomatik olarak ekle.  

Eğer adımları izlediyseniz, artık **how to set shadow**, **adjust shape transparency** ve **add rectangle shadow** nasıl yapılır biliyorsunuz ve profesyonel bir parlaklık elde edersiniz. Denemekten, hatalar yapmaktan ve ardından düzeltmekten çekinmeyin—kodlama en iyi öğretmendir.

---

*Kodlamanın keyfini çıkarın! Bu öğretici size yardımcı olduysa, bir yorum bırakın ya da kendi gölge ipuçlarınızı paylaşın. Ne kadar çok birbirimizden öğrenirsek, Word belgelerimiz o kadar güzel olur.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}