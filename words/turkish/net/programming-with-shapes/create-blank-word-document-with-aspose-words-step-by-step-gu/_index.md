---
category: general
date: 2026-02-23
description: C# ve Aspose.Words kullanarak boş bir Word belgesi oluşturun. Dikdörtgen
  şekil eklemeyi, kelimeye gölge eklemeyi öğrenin ve dakikalar içinde şekilli Word
  belgesini kaydedin.
draft: false
keywords:
- create blank word document
- add rectangle shape
- how to add shape
- add shadow word
- save word with shape
language: tr
og_description: Boş bir Word belgesini hızlıca oluşturun. Bu kılavuz, dikdörtgen şekli
  eklemeyi, kelimeye gölge eklemeyi ve şekilli Word belgesini Aspose.Words kullanarak
  kaydetmeyi gösterir.
og_title: Boş Word belgesi oluştur – Tam C# Öğreticisi
tags:
- Aspose.Words
- C#
- Document Automation
title: Aspose.Words ile Boş Word Belgesi Oluşturma – Adım Adım Kılavuz
url: /tr/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş Word belgesi oluşturma – Tam C# Öğreticisi

Microsoft Word'ü açmadan programlı bir şekilde **create blank word document** oluşturmanın nasıl olduğunu hiç merak ettiniz mi? Tek başınıza değilsiniz. Birçok otomasyon projesinde yeni bir .docx dosyasına ihtiyacımız var, üzerine bir şekil yerleştiriyoruz, o şekle güzel bir gölge veriyoruz ve ardından **save word with shape**'i daha sonra kullanmak üzere kaydediyoruz.  

Bu rehberde tam olarak bunu adım adım göstereceğiz—boş bir belgeden başlayarak, **adding a rectangle shape** ekleyerek, bir **add shadow word** etkisi yapılandırarak ve sonunda dosyayı kalıcı hale getirerek. Sonunda, herhangi bir .NET konsol uygulamasına yapıştırabileceğiniz eksiksiz, çalıştırılabilir bir kod parçacığına sahip olacaksınız. Hiçbir gizem yok, eksik parça yok.

## Gereksinimler

- **Aspose.Words for .NET** (herhangi bir yeni sürüm, ör. 24.10).  
- .NET 6 veya daha yenisi (kod .NET Framework 4.7+ ile de çalışır).  
- Temel bir C# IDE—Visual Studio, Rider veya hatta C# uzantılı VS Code.  

Hepsi bu. Aspose.Words dışındaki ekstra NuGet paketlerine gerek yok ve Word kurulumu da gerekmiyor.

---

## Adım 1: Boş bir Word belgesi oluşturma

**create blank word document** oluşturmak istediğinizde ilk yaptığınız şey `Document` sınıfını örneklemektir. Bunu, Aspose.Words'in size sunduğu temiz bir tuval olarak düşünün.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1 – initialize an empty document
Document document = new Document();   // this is a brand‑new, blank Word file
```

> **Neden önemli:** `Document` nesnesi tüm bölümleri, paragrafları ve şekilleri tutar. Boş bir örnekle başlamak, daha sonra eklenen her öğe üzerinde kontrol sahibi olmanızı sağlar.

---

## Adım 2: Belgeye bir dikdörtgen şekli ekleme

Şimdi temiz bir belgemiz olduğuna göre, **add rectangle shape** yapalım. Dikdörtgen, `ShapeType.Rectangle` ile tanımlanan basit bir `Shape`'dır. Elbette başka tipler de seçebilirsiniz, ancak gösterim için dikdörtgen çok uygundur.

```csharp
// Step 2 – create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width = 200,   // width in points (≈2.78 inches)
    Height = 100   // height in points (≈1.39 inches)
};
```

> **Pro ipucu:** **how to add shape**'in bir dikdörtgen olmadığını merak ederseniz, sadece `ShapeType.Rectangle`'ı `ShapeType.Ellipse` veya `ShapeType.Polygon` gibi başka bir enum değeriyle değiştirin. Kodun geri kalanı aynı kalır.

---

## Adım 3: Şekil için özel bir gölge yapılandırma

Düz bir dikdörtgen biraz cansız görünür, bu yüzden **add shadow word** ekleyerek daha çarpıcı hâle getireceğiz. Aspose.Words, birçok özelliğe sahip bir `ShadowFormat` nesnesi sunar.

```csharp
// Step 3 – enable and style the shadow
rectangleShape.ShadowFormat.Enabled = true;                // turn on the shadow
rectangleShape.ShadowFormat.Color = Color.Gray;           // shadow color
rectangleShape.ShadowFormat.OffsetX = 5;                  // horizontal offset (points)
rectangleShape.ShadowFormat.OffsetY = 5;                  // vertical offset (points)
rectangleShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
rectangleShape.ShadowFormat.BlurRadius = 4;               // soft edge blur
```

> **Neden önemli:** Gölge, özellikle belge ekranda görüntülenecekse, hafif bir derinlik hissi verir. `OffsetX`, `OffsetY` ve `BlurRadius` değerlerini tasarım dilinize göre ayarlayın.

---

## Adım 4: Şekli belgeye ekleme

Şekil hazır olduğunda, onu bir yere yerleştirmemiz gerekir. En basit yer, ilk bölümün ilk paragrafıdır. Belgenin henüz paragrafı yoksa, Aspose otomatik olarak bir tane oluşturur.

```csharp
// Step 4 – put the rectangle into the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Köşe durumu:** Şekli belirli bir konuma (ör. belirli bir başlıktan sonra) eklemeyi planlıyorsanız, hedef `Paragraph`'ı `document.GetChildNodes(NodeType.Paragraph, true)` ile bulun ve buna göre `InsertAfter` ya da `InsertBefore` kullanın.

---

## Adım 5: Şekilli Word belgesini kaydetme

Son olarak, **save word with shape**'i diske kaydediyoruz. `Save` yöntemi dosya uzantısından formatı otomatik olarak belirler.

```csharp
// Step 5 – persist the document
string outputPath = @"C:\Temp\shadowedRectangle.docx";
document.Save(outputPath);
```

> **Gördükleriniz:** `shadowedRectangle.docx` dosyasını Word'de (veya uyumlu bir görüntüleyicide) açın ve ilk sayfanın üst kısmında yumuşak bir gölgeye sahip gri bir dikdörtgen göreceksiniz.

---

## Tam Çalışan Örnek

Aşağıda, bir konsol uygulamasına kopyalayıp‑yapıştırabileceğiniz tam program bulunmaktadır. Tüm using yönergelerini, yorumları ve tartıştığımız adımları içerir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeWordShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank word document
            Document document = new Document();

            // 2️⃣ Add a rectangle shape
            Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100
            };

            // 3️⃣ Configure a custom shadow (add shadow word)
            rectangleShape.ShadowFormat.Enabled = true;
            rectangleShape.ShadowFormat.Color = Color.Gray;
            rectangleShape.ShadowFormat.OffsetX = 5;
            rectangleShape.ShadowFormat.OffsetY = 5;
            rectangleShape.ShadowFormat.Transparency = 0.3;
            rectangleShape.ShadowFormat.BlurRadius = 4;

            // 4️⃣ Insert the shape into the first paragraph
            document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

            // 5️⃣ Save the document (save word with shape)
            string outputFile = @"YOUR_DIRECTORY\shadow.docx";
            document.Save(outputFile);

            // Confirmation
            System.Console.WriteLine($"Document saved to {outputFile}");
        }
    }
}
```

Programı çalıştırın, `YOUR_DIRECTORY` konumuna gidin ve oluşturulan `shadow.docx` dosyasını açın. Dikdörtgeni hafif gri bir gölgeyle göreceksiniz—tam da ulaşmak istediğimiz şey.

---

## Sık Sorulan Sorular & İpuçları

### Şeklin rengini nasıl değiştiririm?

```csharp
rectangleShape.FillColor = Color.LightBlue;
```
Şekli eklemeden önce sadece `FillColor`'ı ayarlayın.

### Aynı sayfada birden fazla şekle ihtiyacım olursa?

Ek `Shape` nesneleri oluşturup her birini aynı paragraf ya da farklı paragraflara ekleyin. `WrapType` ve `RelativeHorizontalPosition` kullanarak yerleşimi de kontrol edebilirsiniz.

### Gölgeyi koruyarak PDF'ye dışa aktarabilir miyim?

Kesinlikle. `document.Save("output.pdf")` kullanın—Aspose.Words, PDF dönüşümünde gölge etkisini korur.

### Bu .NET Core'da çalışıyor mu?

Evet. Aspose.Words çapraz platformdur; aynı kod .NET Core, .NET 5+ ve .NET Framework üzerinde çalışır.

### Paragraf olmadan şekil nasıl eklenir?

`Run`'a ya da bir `Story`'ye doğrudan şekil ekleyebilirsiniz. Daha kesin konumlandırma için `rectangleShape.RelativeHorizontalPosition = RelativeHorizontalPosition.Page` ayarlayın ve `Left`/`Top` özelliklerini düzenleyin.

---

## Görsel Sonuç

![Word belgesinde gri gölgeli dikdörtgen şekil – add shadow word örneği](https://example.com/placeholder-image.png "add shadow word örneği")

*Görsel alt metni, SEO'yu karşılamak için ikincil anahtar kelime **add shadow word** içerir.*

---

## Sonuç

Az önce **create blank word document**, **add rectangle shape** yapmayı, bir **add shadow word** etkisi uygulamayı ve sonunda Aspose.Words for .NET kullanarak **save word with shape**'i göstermiş olduk. İşlem basittir: bir `Document` örnekleyin, bir `Shape` oluşturun, `ShadowFormat`'unu ayarlayın, ekleyin ve `Save` çağırın.  

Buradan deneyler yapabilirsiniz—farklı şekil tiplerini deneyin, renklerle oynayın ya da birden fazla şekli katmanlayın. Bu belgeyi mevcut içerikle birleştirmeniz gerekiyorsa, `new Document("existing.docx")` ile mevcut dosyayı yükleyin ve aynı adımları izleyin.  

Daha fazla sorunuz mu var? Bir yorum bırakın, iyi kodlamalar!

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}