---
category: general
date: 2026-03-25
description: C# ile PDF belgesi oluşturun ve sadece birkaç adımda dikdörtgen şekli
  eklemeyi, dolgu rengini ayarlamayı, şekil boyutunu düzenlemeyi ve şekil şeffaflığını
  ayarlamayı öğrenin.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: tr
og_description: C#'ta PDF belgesi oluşturun ve bir dikdörtgen eklemeyi, dolgu rengini,
  boyutunu ve şeffaflığını ayarlamayı, şık bir PDF çıktısı için öğrenin.
og_title: Dikdörtgen Şekilli PDF Belgesi Oluştur – C# Öğretici
tags:
- C#
- PDF
- Aspose.Words
title: Dikdörtgen Şekilli PDF Belgesi Oluşturma – Tam C# Rehberi
url: /tr/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dikdörtgen Şekilli PDF Belgesi Oluştur – Tam C# Kılavuzu

Hiç **PDF belgesi** oluştururken özel bir şekil eklemek istediğinizde nereden başlayacağınızı bilemediniz mi? Yalnız değilsiniz. Bir rapor oluşturucu ya da pazarlama broşürü geliştiriyor olun, programatik olarak bir dikdörtgen çizmek, dolgu rengini ayarlamak, boyutunu düzenlemek ve hatta şeffaflığını kontrol etmek PDF’lerinizi çok daha profesyonel gösterir.

Bu öğreticide, **PDF belgesi oluştur**, **dikdörtgen şekil ekle**, **dolgu rengini ayarla**, **şekil boyutunu tanımla** ve **şekil şeffaflığını ayarla** (hafif bir dış gölge için) adımlarını içeren, çalıştırmaya hazır tam bir C# örneği üzerinden ilerleyeceğiz. Sonunda `shadow.pdf` adlı tek bir PDF dosyanız olacak ve sonucu görebileceksiniz.

> **Pro ipucu:** Aynı yaklaşım diğer şekil tipleri (elips, çizgi vb.) için de çalışır—`ShapeType.RECTANGLE` yerine ihtiyacınız olanı koymanız yeterli.

---

## Gereksinimler

| Önkoşul | Neden Önemli |
|--------------|----------------|
| **.NET 6+** (veya .NET Framework 4.6+) | Aspose.Words kütüphanesi modern çalışma zamanlarını hedefler. |
| **Aspose.Words for .NET** NuGet paketi | `Document`, `Shape`, `ShadowEffect` ve ilgili sınıfları sağlar. |
| **Bir C# IDE** (Visual Studio, Rider, VS Code) | Örneği hata ayıklamayı ve çalıştırmayı sorunsuz hâle getirir. |
| **Temel C# bilgisi** | Derinlemesine bir dalış yapmadan sözdizimini anlayabilirsiniz. |

Kütüphaneyi komut satırından şu şekilde kurabilirsiniz:

```bash
dotnet add package Aspose.Words
```

Hepsi bu—ekstra DLL, yerel bağımlılık yok. Paket yüklendikten sonra aşağıdaki kod derlenecek ve çalışacaktır.

---

## Adım‑Adım Uygulama

Aşağıda süreci beş mantıksal adıma ayırdık. Her adım net bir başlığa sahip (AI modelleri indeksleyebilir) ve doğrudan kopyalayıp yapıştırabileceğiniz kısa bir kod bloğu içerir.

### ## 1. PDF Belgesi Oluştur ve Tuvali Hazırla

İlk yaptığımız şey bir `Document` nesnesi örneklemek. Bunu boş bir tuval gibi düşünün; sonunda PDF dosyanız bu tuval olacak.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Neden?** `Document` tüm bölümleri, paragrafları ve şekilleri tutar. Temiz bir nesneyle başlamak, önceki çalıştırmalardan kalan gizli kalıntıların oluşmasını engeller.

### ## 2. Dikdörtgen Şekil Ekle – Dolgu Rengini ve Şekil Boyutunu Ayarla

Şimdi bir dikdörtgen oluşturup parlak sarı bir dolgu veriyoruz ve boyutlarını tanımlıyoruz. Bu adım **dikdörtgen şekil ekle**, **dolgu rengini ayarla** ve **şekil boyutunu ayarla** işlemlerini kapsar.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Not:** Genişlik/yükseklik puan (point) cinsindendir (1 point = 1/72 inç). Bu sayıları düzenleyerek tasarımınıza uygun hale getirebilirsiniz.

### ## 3. Dış Gölge Uygula ve Şekil Şeffaflığını Ayarla

Gölge derinlik katar ve şeffaflığını kontrol etmek **şekil şeffaflığını ayarla**nın özüdür. Aşağıda %30 şeffaf bir gri dış gölge yapılandırıyoruz.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Neden şeffaflık ayarlansın?** %30 şeffaf bir gölge hafif bir etki yaratır, dikdörtgenin sayfada “düz” görünmesini engeller.

### ## 4. Şekli Belge Gövdesine Yerleştir

Şimdi dikdörtgeni belgenin ilk bölümündeki ilk paragrafın içine ekliyoruz. Bu adım her şeyi bir araya getirir.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Köşe durumu:** Şekli yeni bir sayfada istiyorsanız, şekli eklemeden önce `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` satırını ekleyin.

### ## 5. Belgeyi PDF Dosyası Olarak Kaydet

Son olarak, bellek içindeki yapıyı fiziksel bir PDF dosyasına yazdırıyoruz. Dosya, belirttiğiniz klasöre kaydedilecek.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

Programı çalıştırdığınızda `shadow.pdf` adlı bir dosya oluşur. Açtığınızda 4 puan kaydırılmış hafif gri bir gölgeye sahip sarı bir dikdörtgen görürsünüz—tam da kodumuzun tanımladığı gibi.

> **Beklenen çıktı:** Tek sayfalık bir PDF; dikdörtgen sayfanın sol‑üst köşesine yakın bir konumda, sarı dolgu, 200 × 100 puan boyutunda ve yarı şeffaf bir dış gölgeyle.

---

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

Aşağıda yeni bir konsol projesine bırakabileceğiniz, tüm kaynak dosyası yer alıyor.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **İpucu:** `YOUR_DIRECTORY` kısmını `C:\Temp` gibi mutlak bir yol ya da `.\output` gibi göreli bir yol ile değiştirin. Klasör mevcut değilse program otomatik olarak oluşturur.

---

## Sıkça Sorulan Sorular (SSS)

**S: Dikdörtgenin sayfadaki konumunu değiştirebilir miyim?**  
C: Kesinlikle. Şekli paragrafın içine eklemeden önce `rectangle.Left` ve `rectangle.Top` (ikisi de puan cinsindendir) değerlerini ayarlayın.

**S: Şeffaf bir dolgu, şeffaf bir gölge yerine kullanabilir miyim?**  
C: `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` kodunu kullanın – ilk argüman alfa kanalını (0‑255) temsil eder; 128 yaklaşık %50 şeffaflık verir.

**S: Bu .NET Core ile çalışır mı?**  
C: Evet. Aspose.Words .NET Standard 2.0+ destekler; aynı kodu .NET 6, .NET 7 veya .NET Framework 4.6+ üzerinde çalıştırabilirsiniz.

**S: Birden fazla şekil ekleyebilir miyim?**  
C: Her şekil için adım 2‑4’ü tekrarlayın; şekilleri farklı paragraflara ya da bölümlere ekleyebilirsiniz.

---

## Sonuç

Sıfırdan **PDF belgesi oluştur**, **dikdörtgen şekil ekle**, **dolgu rengini ayarla**, **boyutunu tanımla** ve **şekil şeffaflığını ayarla**arak şık bir gölge efekti elde ettik. Örnek kod bağımsız, bir dakikadan kısa sürede çalışır ve daha karmaşık PDF düzenleri için ihtiyaç duyacağınız temel kavramları gösterir.

Bir sonraki meydan okumaya hazır mısınız? Dikdörtgeni köşeleri yuvarlatılmış bir şekille değiştirin, şeklin içine bir resim gömün ya da otomatik bir içerik tablosu oluşturun. Aynı API metin, resim ve vektör katmanlamanıza izin verir—hayal gücünüz sınırdır.

Bu kılavuzu faydalı bulduysanız GitHub’da yıldız verin, bir ekip arkadaşınızla paylaşın ya da kendi varyasyonlarınızı yorum olarak bırakın. Kodlamanın tadını çıkarın!

---

![create pdf document with rectangle shape example](/images/rectangle-shadow.png "Screenshot showing the created PDF with a yellow rectangle and gray outer shadow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}