---
category: general
date: 2025-12-29
description: Aspose.Words C# kullanarak bir Word belgesinde dikdörtgen şekil oluşturun.
  Şekil şeffaflığını ayarlamayı, gölge rengini belirlemeyi öğrenin ve Word belgesini
  zahmetsizce kaydedin.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: tr
og_description: Aspose.Words C# ile bir Word belgesine dikdörtgen şekil oluşturun.
  Bu kılavuz, şekil şeffaflığını ayarlamayı, gölge rengini belirlemeyi ve Word belgesini
  kaydetmeyi gösterir.
og_title: Word'de dikdörtgen şekli oluşturma – Tam Aspose.Words Eğitimi
tags:
- Aspose.Words
- C#
- Word Automation
title: Aspose.Words ile Word'de dikdörtgen şekli oluşturma – Adım adım rehber
url: /tr/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Dikdörtgen Şekli Oluşturma – Tam Aspose.Words Öğreticisi

Bir Word belgesinde **dikdörtgen şekli oluşturma** ihtiyacı hiç duydunuz mu, ama nereden başlayacağınızı bilemediniz mi? Yalnız değilsiniz; birçok geliştirici raporlar veya faturalar otomatikleştirirken bu engelle karşılaşıyor. Bu rehberde, bir dikdörtgen şekli oluşturma, şekil şeffaflığını ayarlama, gölge rengini belirleme ve sonunda Aspose.Words for .NET kullanarak **Word belgesini kaydetme** adımlarını adım adım göstereceğiz.  

İlk belge nesnesinden diskteki son `.docx` dosyasına kadar her şeyi ele alacağız, böylece sonunda **Word belgesi oluşturma** işlemini tahmin etmeden programatik olarak yapabileceksiniz. Harici referanslar yok, sadece projenize kopyalayıp yapıştırabileceğiniz bağımsız bir çözüm.

## Gereksinimler

- .NET 6.0 veya üzeri (kod .NET Framework 4.7+ ile de çalışır)
- Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`)
- C# sözdizimi hakkında temel bilgi
- Tercih ettiğiniz bir IDE (Visual Studio, Rider, VS Code vb.)

> **Pro ipucu:** Aspose.Words ücretsiz deneme sürümünü kullanıyorsanız, kütüphane çıktı dosyasına bir filigran ekleyecektir. Üretim ortamında geçerli bir lisansa ihtiyacınız olacak.

## 1. Adım: Belge ve Builder'ı Başlatma

İlk olarak boş bir Word belgesi ve içerik eklememizi sağlayan bir `DocumentBuilder` oluşturuyoruz. Builder, sayfada çizen sanal bir kalem gibi düşünülebilir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Neden önemli:** Bir `DocumentBuilder` olmadan düşük seviyeli düğüm ağacını doğrudan manipüle etmeniz gerekir; bu hataya açık ve okunması zor bir yöntemdir.

## 2. Adım: Dikdörtgen Şekli Oluşturma

Şimdi **dikdörtgen şekli oluşturuyoruz**. `InsertShape` yöntemi bir `ShapeType` enum’u, genişlik ve yükseklik (puan cinsinden) alır. Dönen `Shape` nesnesi, görsel özellikleri daha sonra ayarlamamıza olanak tanır.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Bu aşamada dikdörtgen, mevcut paragrafın içine sabitlenmiş katı siyah bir kutudur. İsterseniz daha sonra taşıyabilir, yeniden boyutlandırabilir veya döndürebilirsiniz.

![gölge ile dikdörtgen şekli oluştur](/images/rectangle-shadow.png "Gri gölge ile bir dikdörtgen şekli gösteren bir Word belgesi")

*Görsel alt metni: Word belgesinde gölge ile dikdörtgen şekli oluşturma*

## 3. Adım: Şekil Şeffaflığını Ayarlama

Şeffaflık, şeklin dolgusunun “görünürlük” seviyesidir. Aspose.Words, `0.0` (opak) ile `1.0` (tamamen şeffaf) arasında bir `Transparency` özelliği kullanır. Burada **şekil şeffaflığını** %40 olarak ayarlıyoruz, böylece altındaki metin okunabilir kalıyor.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Köşe durumu:** Şekli tamamen görünmez ama gölgenin görünür olmasını istiyorsanız, `Transparency` değerini `1.0` yapın ve şekle sıfır olmayan bir kontur genişliği verin.

## 4. Adım: Gölgeyi Yapılandırma

Hafif bir gölge derinlik katar. **Gölge rengini** orta gri olarak ayarlayacağız, bulanıklık yarıçapını düzenleyecek ve hem yatay hem de dikey olarak birkaç puan kaydıracağız.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Neden önemli:** Çok keskin veya çok koyu bir gölge, baskı hatası gibi görünebilir. `Blur` ve `Transparency` değerlerini doğal bir görünüm elde edene kadar ayarlayın.

## 5. Adım: Word Belgesini Kaydetme

Son olarak **Word belgesini** diske kaydediyoruz. `Save` yöntemi uzantıya göre dosya formatını otomatik belirler; `.docx` modern OpenXML formatıdır.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Klasör mevcut değilse, Aspose.Words bir `ArgumentException` fırlatır. Yolun geçerli olduğundan emin olun veya klasörü önceden oluşturun.

## Tam Çalışan Örnek

Aşağıda tüm adımları bir araya getiren, çalıştırmaya hazır tam program yer alıyor. Yeni bir konsol projesine yapıştırın ve **F5** tuşuna basın.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Beklenen Sonuç

`ShadowRectangle.docx` dosyasını Microsoft Word’de açın. %40 şeffaflıkta, hafifçe kaydırılmış yumuşak bir gölgeye sahip açık gri bir dikdörtgen görmelisiniz. Şekil boş bir sayfada durur, ek içerik eklemeye hazırdır.

## Sık Sorulan Sorular & Varyasyonlar

**Farklı bir şekle ihtiyacım olursa?**  
`ShapeType.Rectangle` yerine başka bir enum değeri (`Ellipse`, `Triangle`, `Star` vb.) kullanın. Kodun geri kalanı aynı kalır.

**Kontur rengini değiştirebilir miyim?**  
Evet—`rectangleShape.StrokeColor = System.Drawing.Color.Blue;` satırını ekleyin ve isteğe bağlı olarak `rectangleShape.StrokeWeight = 1.5;` ayarlayın.

**Şekli sayfada belirli bir konuma nasıl yerleştiririm?**  
`rectangleShape.WrapType = WrapType.None;` yapın ve ardından `rectangleShape.Left` ve `rectangleShape.Top` özelliklerini (puan cinsinden) ayarlayın.

**Dikdörtgenin içine metin ekleyebilir miyim?**  
Kesinlikle. Şekli oluşturduktan sonra `rectangleShape.AppendChild(new Paragraph(document))` çağırıp bir `Run` ekleyerek metninizi yerleştirebilirsiniz. Daha zengin biçimlendirme isterseniz `rectangleShape.TextBox` özelliklerini ayarlamayı unutmayın.

## Pro İpuçları & Tuzaklar

- **Erken lisanslayın:** Lisans eklemeyi unutursanız, Aspose.Words ilk sayfaya bir filigran ekler; bu test aşamasında kafa karıştırıcı olabilir.
- **Performans ipucu:** Döngü içinde çok sayıda belge üretirken tek bir `Document` örneğini yeniden kullanın ve her kaydetmeden sonra `document.RemoveAllChildren();` çağırarak gereksiz GC baskısını önleyin.
- **Gölge görünürlüğü:** Düşük çözünürlüklü ekranlarda ince bir gölge görünmez olabilir. Hata ayıklama sırasında `Blur` veya `OffsetX/Y` değerlerini artırın, ardından üretim için geri düşürün.

## Sonraki Adımlar

Artık **dikdörtgen şekli oluşturma**, **şekil şeffaflığını ayarlama**, **gölge rengini belirleme** ve **Word belgesini kaydetme** konularını biliyorsunuz; şimdi öğreticiyi genişletmeyi düşünün:

- Birden fazla şekil ekleyip gruplayın.
- Rapor düzeni için dikdörtgeni bir tablo hücresinin içine yerleştirin.
- Şekli `DocumentBuilder.InsertHtml` ile birleştirerek HTML‑styled içerik üst üste bindirin.
- `Glow` veya `Reflection` gibi diğer görsel efektleri keşfederek daha zengin UI‑benzeri belgeler oluşturun.

Deneyin, hatalar yapın ve ardından iyileştirin—programatik belge üretimi, görsel tasarımın kodla buluştuğu bir oyun alanıdır.

---

*Kodlamanın tadını çıkarın! Herhangi bir sorunla karşılaşırsanız, aşağıya yorum bırakın; birlikte çözüm bulalım.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}