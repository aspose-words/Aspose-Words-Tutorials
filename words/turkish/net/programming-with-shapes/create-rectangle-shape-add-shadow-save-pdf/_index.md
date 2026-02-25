---
category: general
date: 2026-02-24
description: Aspose.Words kullanarak C#'de dikdörtgen şekil oluşturun, şekle gölge
  ekleyin ve belgeyi PDF olarak kaydedin. Gölge eklemeyi ve PDF kaydetmeyi dakikalar
  içinde öğrenin.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: tr
og_description: Aspose.Words ile C#’ta dikdörtgen şekil oluşturun, ardından şekle
  gölge ekleyin ve belgeyi PDF olarak kaydedin – eksiksiz, adım adım bir kılavuz.
og_title: Dikdörtgen şekli oluştur, gölge ekle ve PDF'yi kaydet
tags:
- Aspose.Words
- C#
- PDF generation
title: Dikdörtgen şekli oluştur, gölge ekle ve PDF'yi kaydet
url: /tr/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

Now ensure we didn't translate any code placeholders or URLs. We kept code placeholders. We didn't translate URLs in image. Good.

Check for any variable names inside text: we kept them.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dikdörtgen şekli oluşturun, gölge ekleyin ve PDF olarak kaydedin

Word belgesinde **dikdörtgen şekli** oluşturmanız ve aynı zamanda güzel bir gölge ile PDF çıktısı almanız gerektiğinde hiç zorlandınız mı? Tek başınıza değilsiniz. Birçok raporlama veya fatura‑oluşturma projesinde görsel incelik—örneğin hafif bir gölge—“sıradan bir dosya” ile “profesyonel‑düzey belge” arasındaki farkı yaratır.  

Bu öğreticide tam olarak bunu adım adım göstereceğiz: **Aspose.Words for .NET** kullanarak bir dikdörtgen şekli oluşturmak, şekle gölge eklemek ve sonunda **belgeyi PDF olarak kaydetmek**. Sonunda gölgeli bir dikdörtgen üreten, çalıştırmaya hazır bir C# konsol uygulamanız olacak ve gölgeyi nasıl ayarlayacağınızı ya da dışa aktarma seçeneklerini nasıl değiştireceğinizi anlayacaksınız.

## Gerekenler

- .NET 6 SDK (veya herhangi bir yeni .NET sürümü) – API, .NET Framework 4.x üzerinde de aynı şekilde çalışır.  
- Aspose.Words for .NET NuGet paketi (`Aspose.Words`) – `dotnet add package Aspose.Words` komutuyla kurun.  
- Bir kod editörü – Visual Studio, VS Code veya Rider yeterli olacaktır.  

Bu örnek için ekstra lisans adımı yok; ücretsiz değerlendirme modu PDF çıktısını görmek için yeterlidir.

## Adım 1: Projeyi kurun ve ad alanlarını içe aktarın

İlk olarak, bir konsol projesi oluşturalım ve ihtiyacımız olan sınıfları içe aktaralım.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Neden önemli:* `Document` ve `DocumentBuilder` bize tuvali sağlar, `Shape` ve `ShadowFormat` ise dikdörtgeni çizmeye ve stil vermeye yarar. Bunları önceden içe aktarmak sonraki kodu düzenli tutar.

## Adım 2: İstenen boyutlarda **dikdörtgen şekli** oluşturun

Şimdi boş bir belge oluşturup içine bir dikdörtgen ekliyoruz. `InsertShape` metodunun bir `Shape` nesnesi döndürdüğüne ve bunu hemen stil verebileceğimize dikkat edin.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Açıklama*: Boyutlar point biriminde ifade edilir (1 pt = 1/72 in). Sayıları düzeninize göre ayarlayın. Ayrıca gölgenin öne çıkması için şekle açık mavi bir dolgu veriyoruz.

## Adım 3: **Şekle gölge ekleyin** – etkiyi ince ayarlayın

Gölge sadece “açık/kapalı” değildir. Rengini, bulanıklığını, mesafesini, yönünü ve hatta şeffaflığını kontrol edebilirsiniz. İşte çoğu rapor için iyi çalışan pratik bir yapılandırma.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Bu değerleri neden değiştirebilirsiniz:*  
- **BlurRadius** – daha rüya gibi bir etki için artırın, keskin kenar için azaltın.  
- **Direction** – 0° sağa, 90° aşağı, 180° sola vb. yön gösterir. Sayfa düzeninize göre döndürün.  
- **Transparency** – katı gölge için `0`, yarı şeffaf için `0.5` vb. olarak ayarlayın.

### Gölge eklemenin yolları – alternatif yaklaşımlar

Eğer **çok katmanlı bir gölge** (örneğin, dışta daha koyu, içte daha açık bir gölge) gerekiyorsa, ikinci bir şekil oluşturup konumunu kaydırabilir ve farklı bir `ShadowFormat` ayarlayabilirsiniz. Ya da hızlı bir “bulanık olmayan” görünüm için `BlurRadius = 0` ayarlayın.

## Adım 4: **Belgeyi PDF olarak kaydedin** – son dışa aktarım

Dikdörtgen ve gölgesi hazır olduğunda, son adım dosyayı PDF olarak kaydetmektir. Aspose.Words dönüşümü dahili olarak yönetir; sadece istediğiniz formatla `Save` metodunu çağırırsınız.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*İpucu*: PDF uyumluluğunu (PDF/A, PDF/X) kontrol etmeniz ya da fontları gömmek istiyorsanız, bir aşırı yükleme (overload) kullanın:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

Bu, **PDF kaydetme** kısmının özetidir.

## Tam, çalıştırılabilir örnek

Aşağıda `Program.cs` dosyasına kopyalayıp yapıştırabileceğiniz tam program yer alıyor. Olduğu gibi derlenir ve çalışır (çıkış klasörünün var olduğundan emin olun).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Beklenen sonuç

`ShadowRectangle.pdf` dosyasını açın. Açık mavi bir dikdörtgen, 45° aşağı‑sağa kaydırılmış yumuşak gri bir gölge ve temiz kenarlar içeren tek bir sayfa göreceksiniz. PDF, modern bir okuyucuda (Adobe Acrobat, Edge, Chrome) görüntülenebilir olmalıdır.

![PDF'de gölgeli dikdörtgen şekli oluşturma](/images/shadow-rectangle.png "PDF'de gölgeli dikdörtgen şekli oluşturma")

*(Görsel alt metni SEO için ana anahtar kelimeyi içerir.)*

## Yaygın sorular & uç‑durum yönetimi

**PDF'de gölge kaybolursa ne olur?**  
Aspose.Words'un (≥23.3) yeni bir sürümünü kullandığınızdan emin olun. Eski sürümlerde bazı gölge özellikleri PDF dönüşümü sırasında göz ardı edilen bir hata vardı.

**Gölge rengini markama uygun olarak değiştirebilir miyim?**  
Elbette—`System.Drawing.Color.Gray` ifadesini istediğiniz herhangi bir `Color` ile değiştirin, örneğin yarı şeffaf bir mavi için `Color.FromArgb(128, 0, 0, 255)`.

**Diğer şekillere (elips, yıldız vb.) nasıl gölge eklerim?**  
Aynı `ShadowFormat` herhangi bir `Shape` nesnesi için çalışır. Şekli oluşturduktan sonra onun `ShadowFormat` nesnesini alıp özellikleri ayarlayın.

**DPI veya ölçekleme sorunları nasıl çözülür?**  
PDF oluşturma, şeklin point boyutuna saygı gösterir. Daha yüksek çözünürlüklü bir çıktı (baskı için) gerekiyorsa, şekil boyutlarını buna göre ayarlayın veya `PdfSaveOptions.ImageResolution` ayarını kullanın.

**PDF dışındaki formatlara, örneğin PNG'ye dışa aktarabilir miyim?**  
Evet—`document.Save("output.png", SaveFormat.Png)` şeklinde çağırın. Gölge aynı şekilde işlenecektir.

## Profesyonel ipuçları & en iyi uygulamalar

- **Builder'ı yeniden kullanın**: Birden fazla şekil ekliyorsanız, tek bir `DocumentBuilder` örneği tutun; birden çok örnek oluşturmaktan daha ucuzdur.
- **Toplu kaydetme**: Döngü içinde birden çok PDF oluştururken, tekrar eden tahsislerden kaçınmak için `PdfSaveOptions` nesnesini yeniden kullanın.
- **Test**: Kaydettikten sonra PDF'yi her zaman açarak gölgenin beklendiği gibi göründüğünü doğrulayın. Bazı PDF okuyucular gölgeleri biraz farklı işler; Adobe Acrobat en güvenilir referanstır.
- **Performans**: Büyük belgelerde, ihtiyacınız yoksa `DocumentBuilder.InsertShape` metodunun otomatik sayfa sonlarını `builder.PageSetup.DifferentFirstPageHeaderFooter = false` ayarıyla devre dışı bırakın.

## Sonuç

Aspose.Words for .NET kullanarak **dikdörtgen şekli oluşturma**, **şekle gölge ekleme** ve **belgeyi PDF olarak kaydetme** konularında ihtiyacınız olan her şeyi ele aldık. Kod kompakt, kavramlar açıklanmış ve artık diğer şekiller, gölge stilleri ve dışa aktarma seçenekleriyle denemeler yapmanız için sağlam bir temele sahipsiniz.  

Sonraki adımlar? Dikdörtgeni yuvarlatılmış bir ... ile değiştirmeyi deneyin

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}