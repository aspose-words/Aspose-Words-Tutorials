---
category: general
date: 2026-03-01
description: Aspose.Words kullanarak PDF'ye hızlıca dikdörtgen ekleyin. Şekil PDF
  eklemeyi, PDF'ye grafik eklemeyi öğrenin ve özel bir gölgeyle programlı olarak PDF
  belgesi oluşturun.
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: tr
og_description: Aspose.Words kullanarak PDF'ye dikdörtgen ekleyin. Bu öğreticide PDF'ye
  şekil ekleme, PDF'ye grafik ekleme ve C#'ta programlı olarak PDF belgesi oluşturma
  gösterilmektedir.
og_title: Aspose.Words ile PDF'ye Dikdörtgen Ekleme – Tam Kılavuz
tags:
- pdf
- aspnet
- csharp
- graphics
title: Aspose.Words ile PDF'ye Dikdörtgen Ekle – Adım Adım Kılavuz
url: /tr/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile PDF'e Dikdörtgen Ekle – Tam Kılavuz

Hiç **PDF'e dikdörtgen eklemek** istediğinizde hangi API çağrısının işe yaradığını bilemediniz mi? Tek başınıza değilsiniz—geliştiriciler sürekli olarak “PDF'e şekil nasıl eklerim ve dosya hâlâ hafif kalır?” sorusunu soruyor. İyi haber şu ki Aspose.Words bu işi çocuk oyuncağı haline getiriyor. Bu öğreticide, PDF belgesini programlı olarak oluşturmaktan dikdörtgene gölge eklemeye kadar tüm süreci adım adım inceleyeceğiz.

Ayrıca birkaç ekstra fayda da sunacağız: **PDF'e grafik eklemeyi** öğrenecek, **PDF'e şekil ekleme** adımlarını görecek ve **şekilli PDF oluşturma** örneğiyle bitireceksiniz. Harici referanslar yok, sadece bugün kopyala‑yapıştır yapabileceğiniz bağımsız bir çözüm.

## Gereksinimler

- .NET 6.0 veya üzeri (Aspose.Words .NET Standard 2.0+ ile çalışır)
- Geçerli bir Aspose.Words for .NET lisansı veya geçici bir değerlendirme anahtarı
- Visual Studio 2022 (veya tercih ettiğiniz herhangi bir IDE)
- Temel C# bilgisi—konsol uygulaması çalıştırabilecek düzeyde

Hepsi bu. Bu koşullara sahipseniz, hazırsınız.

## 1. Adım: PDF belgesini programlı olarak oluşturun

**PDF'e dikdörtgen eklemek** istediğinizde ilk yapmanız gereken boş bir belge oluşturmak. `Document` sınıfını boş bir tuval gibi düşünün; daha sonra ekleyeceğiniz her şey bu tuvalin içinde yer alır.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

Neden boş bir belgeyle başlıyoruz? Çünkü bu sayede her öğe üzerinde tam kontrol sahibi olursunuz—daha sonra uğraşmanız gereken gizli sayfa başlıkları veya altbilgiler olmaz.

## 2. Adım: Şekil eklemek için DocumentBuilder'ı başlatın

`DocumentBuilder`, çizim fırçanızdır. Metin, resim ve bizim için kritik olan şekilleri yerleştirmeyi bilir. Onsuz, düşük seviyeli düğüm ağacını kendiniz manipüle etmeniz gerekir ki bu çoğu geliştirici için kabus olur.

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Henüz sayfa eklemediğimize dikkat edin. Builder, bir şey eklediğinizde otomatik olarak bir sayfa oluşturur, bu da kodunuzu düzenli tutar.

## 3. Adım: Dikdörtgen şekli ekleyin – “PDF'e dikdörtgen ekleme”nin özü

Şimdi eğlenceli kısma geliyoruz: dikdörtgeni eklemek. `InsertShape` metodu onlarca `ShapeType` değerini destekler; biz `ShapeType.Rectangle` seçip 200 × 100 puan boyutunu vereceğiz.

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Bu aşamada PDF zaten sade bir dikdörtgen içeriyor. Dosyayı şimdi açarsanız, ilk sayfanın sol‑üst köşesinde basit bir kutu göreceksiniz. Bu, **PDF'e grafik ekleme** için temel oluşturur.

## 4. Adım: Dikdörtgene stil verin – özel gölge ekleme

Stilsiz bir dikdörtgen sıkıcıdır. PDF render edildiğinde *dikkat çekmesi* için hafif bir düşürülmüş gölge ekleyelim. `ShadowFormat` nesnesi, bulanıklık yarıçapından opaklığa kadar her şeyi kontrol eder.

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

Neden gölge ekleyelim? Estetik artının yanı sıra, gölge üst üste gelen grafiklerin ayırt edilmesine yardımcı olur—daha karmaşık raporlarda **PDF'e grafik ekleme** ihtiyacınız olduğunda işinize yarar.

## 5. Adım: Dosyayı kaydedin – “şekilli PDF oluşturma” iş akışını tamamlayın

Son satır her şeyi diske yazar. Aspose.Words otomatik olarak doğru PDF sürümünü seçer ve gerekli kaynakları gömer.

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

`ShapeWithShadow.pdf` dosyasını açtığınızda, sayfada gururla duran gölgeli bir dikdörtgen göreceksiniz. Bu, **programlı olarak pdf belgesi oluşturma** akışının tamamı, 30 satırın altında kodla.

## Baştan Sona Çalışan Örnek – şekilli PDF oluşturma

Aşağıda yeni bir Console App projesine kopyala‑yapıştır yapabileceğiniz tam program yer alıyor. Tüm `using` ifadeleri, `Main` metodu ve gelecekteki referanslar için kısa bir yorum başlığı içerir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**Beklenen sonuç:** 200 × 100 puanlık bir dikdörtgenin sayfanın sol‑üst köşesine yakın bir konumda, 45 derece açıyla yumuşak bir gölgeyle süslendiği tek sayfalık PDF. Dosyayı herhangi bir PDF görüntüleyicide açarak doğrulayabilirsiniz.

## Yaygın Sorular & Kenar Durumları

### Bu diğer şekil tipleriyle de çalışır mı?
Kesinlikle. `ShapeType.Rectangle` yerine `ShapeType.Ellipse`, `ShapeType.Triangle` veya Aspose.Words'un desteklediği 150+ seçenekten herhangi birini kullanabilirsiniz. Aynı `ShadowFormat` özellikleri geçerli olur.

### Dikdörtgeni belirli bir sayfaya eklemem gerekirse ne yapmalıyım?
Şekli ekledikten sonra, `InsertShape` çağrısını yapmadan önce builder’ın `CurrentPage` özelliğini ayarlayarak şekli farklı bir sayfaya taşıyabilirsiniz. Örneğin:

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### Dikdörtgenin dolgu rengini değiştirebilir miyim?
Tabii ki. `FillColor` özelliğini kullanın:

```csharp
rect.FillColor = Color.LightBlue;
```

### Bu dosya boyutunu nasıl etkiler?
Basit bir şekil ve gölge sadece birkaç kilobayt ekler. Çok sayıda grafik eklemeye başlarsanız, PDF’i hafif tutmak için resimleri sıkıştırmayı veya vektör‑tabanlı şekilleri tercih etmeyi düşünün.

### Üretim ortamında lisans gerekli mi?
Aspose.Words değerlendirme modunda çalışır, ancak çıkış PDF’si bir filigran içerir. Sınırsız kullanım ve filigranı kaldırmak için bir lisans satın alın.

## İpuçları & Püf Noktaları (Profesyonel Seviye)

- **Toplu ekleme:** Yüzlerce dikdörtgen eklemeniz gerekiyorsa, koordinat koleksiyonunu döngüye alın ve aynı `DocumentBuilder`ı yeniden kullanın—performans lineer kalır.
- **Katmanlama:** Dikdörtgenin metinle akmasını istiyorsanız `rect.WrapType = WrapType.Inline`, metnin etrafında dolanmasını istiyorsanız `WrapType.Square` ayarlayın.
- **PDF/A uyumluluğu:** Arşiv dostu bir PDF gerekiyorsa, kaydetmeden önce `doc.CompatibilityOptions.OptimizeForPdfA = true;` satırını ekleyin.

## Görsel Özet

![PDF'e dikdörtgen ekleme örneği](https://example.com/rectangle-shadow.png "PDF'e dikdörtgen ekleme örneği")

Görsel, nihai PDF düzenini gösterir: temiz bir dikdörtgen ve hafif bir gölge—kodumuzun ürettiği tam olarak bu.

## Sonuç

Artık Aspose.Words kullanarak **PDF'e dikdörtgen eklemeyi**, **PDF'e şekil eklemeyi** ve **PDF'e grafik eklemeyi** özel stil ile nasıl yapacağınızı biliyorsunuz; tüm bunları **programlı olarak PDF belgesi oluşturma** ve **şekilli PDF oluşturma** örneğiyle bir arada gerçekleştirebiliyorsunuz.  

Şimdi dikdörtgeni bir logoyla değiştirin ya da birden fazla şekil birleştirerek basit bir diyagram oluşturun. Metin sarma, döndürme veya şeklin içine bir hiperlink ekleme gibi özellikleri de keşfedebilirsiniz. API, statik bir PDF’i etkileşimli, grafik‑zengin bir rapora dönüştürmenize C#’dan çıkmadan izin verecek kadar zengindir.

Denemeler yapmaktan çekinmeyin; bir sorunla karşılaşırsanız aşağıya yorum bırakın. Mutlu kodlamalar!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}