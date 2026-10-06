---
category: general
date: 2026-03-04
description: Dikdörtgen şekil oluşturmayı, şekle gölge eklemeyi ve bir Word belgesinde
  gölge etkisi uygulamayı öğrenin, ardından Word belgesini otomatik olarak kaydedin.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: tr
og_description: Create rectangle shape, add shadow to shape and apply shadow effect
  in a Word document using C#. Follow this guide to save Word document effortlessly.
og_title: Word'de dikdörtgen şekli oluştur – Tam C# Öğreticisi
tags:
- C#
- Aspose.Words
- Document Automation
title: Create rectangle shape in Word with C# – Step‑by‑Step Guide
url: /tr/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Word'de Dikdörtgen Şekli Oluşturma – Tam Programlama Öğreticisi

Word dosyasında **create rectangle shape** oluşturmanız gerektiğinde ama nereden başlayacağınızı bilemediğiniz oldu mu? Yalnız değilsiniz—birçok geliştirici programatik belge oluşturma sürecine ilk adım attıklarında bu engelle karşılaşıyor. İyi haber şu ki, birkaç satır C# kodu ile bir dikdörtgen ekleyebilir, **add shadow to shape** ekleyebilir ve **apply shadow effect** uygulayabilirsiniz; Word'ü hiç açmanıza gerek kalmaz. Bu rehberde, yeni bir **create blank document** oluşturulmasından son **save word document**'in diske kaydedilmesine kadar tüm süreci adım adım anlatacağız.

İhtiyacınız olan her şeyi ele alacağız: gerekli NuGet paketi, kesin API'ler, her özelliğin neden önemli olduğu ve en yaygın hatalardan kaçınmak için birkaç ipucu. Sonunda, herhangi bir .NET projesine ekleyebileceğiniz tamamen çalıştırılabilir bir örnek elde edeceksiniz.

## Önkoşullar

- .NET 6.0 veya daha yenisi (kod .NET Framework 4.7+ ile de çalışır)
- Visual Studio 2022 veya tercih ettiğiniz herhangi bir IDE
- **Aspose.Words for .NET** NuGet üzerinden yüklü (`Install-Package Aspose.Words`)
- C# sözdizimi hakkında temel bilgi

Ek Word interop kütüphanelerine gerek yok—Aspose.Words her şeyi bellekte yönetir.

## Adım 1 – Boş bir belge oluşturma

İlk yaptığımız şey **create blank document** oluşturmak. Bunu, daha sonra **create rectangle shape** ekleyeceğimiz boş bir tuval olarak düşünün.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Neden önemli:** Temiz bir `Document` nesnesiyle başlamak, gizli stillerin veya bölümlerin daha sonra şekil konumlandırmasını etkilememesini garanti eder.

## Adım 2 – Belgeye bir dikdörtgen şekli ekleme

Şimdi gerçekten **create rectangle shape** yapıyoruz. Boyutunu, konumunu ayarlayacağız ve Word'e metni etrafına sarmamasını söyleyeceğiz.

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Pro ipucu:** Dikdörtgenin bir tablo hücresinin içinde durması gerekiyorsa, `WrapType` değerini `WrapType.Inline` olarak değiştirin. Çoğu rapor için, `None` şeklin metnin üzerinde süzülmesini sağlar.

## Adım 3 – Şekle gölge ekleme ve görünümünü yapılandırma

İşte sihrin gerçekleştiği yer: **add shadow to shape** ekliyoruz ve **apply shadow effect** uyguluyoruz. Gölge, dikdörtgenin sayfada öne çıkmasını sağlar, özellikle yazdırıldığında.

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **Bu değerler neden?**  
> - **BlurRadius** kenarların ne kadar bulanık göründüğünü kontrol eder; `5` civarında bir değer ince, profesyonel bir görünüm verir.  
> - **Transparency** altındaki metnin okunabilir kalmasını sağlar.  
> - **OffsetX/Y** gölgeyi şekilden uzaklaştırarak derinlik oluşturur.  
> - **Mavi** bir ton kullanmak sadece bir örnek—herhangi bir `System.Drawing.Color` çalışır.

## Adım 4 – Yapılandırılmış şekli belge gövdesine ekleme

Dikdörtgen tamamen biçimlendirildiğinde, şimdi **add rectangle shape** belge'nin ilk bölümüne ekliyoruz. Bu adım şekli dosyaya yerleştirir.

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Köşe durumu:** Belgenizde zaten bölümler varsa, belirli bir bölümü hedeflemek isteyebilirsiniz (`doc.Sections[2]` gibi). Yukarıdaki kod tek‑bölümlü bir belge için çalışır; bu, hızlı raporlar için yaygındır.

## Adım 5 – Word belgesini kaydetme

Son olarak, **save word document**'i diske kaydediyoruz. Dosya, gölgesiyle birlikte dikdörtgeni içerecek ve Microsoft Word'de açılmaya hazır olacak.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **İpucu:** Formatı açıkça belirtmeniz gerekiyorsa `doc.Save(outputPath, SaveFormat.Docx)` kullanın. `Save` yöntemi uzantıyı otomatik olarak algılar, ancak açık olmak, yol programatik olarak oluşturulduğunda karışıklığı önleyebilir.

## Tam, Çalıştırılabilir Örnek

Aşağıda, bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz tam program yer alıyor. Tüm `using` ifadelerini ve `Main` metodunu içerir, böylece hemen çalıştırabilirsiniz.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Beklenen Sonuç

Microsoft Word'de *shadowed_rectangle.docx* dosyasını açtığınızda, ilk sayfanın üst kısmına yakın bir konumda mavi kenarlı bir dikdörtgenin, sağa ve aşağıya 8 pt kaydırılmış yumuşak mavi bir gölgeyle süzüldüğünü göreceksiniz. `WrapType.None` ayarladığımız için etrafında ekstra metin bulunmaz.

## Sık Sorulan Sorular & Varyasyonlar

| Question | Answer |
|----------|--------|
| **Şekli bir elipse olarak değiştirebilir miyim?** | Evet—`ShapeType.Rectangle` yerine `ShapeType.Ellipse` kullanın. Tüm gölge özellikleri aynı kalır. |
| **Birden fazla şekle ihtiyacım olursa ne olur?** | Her yeni `Shape` örneği için Adım 2‑4'ü tekrarlayın, çakışmayı önlemek için `OffsetX/Y` veya `Left/Top` değerlerini ayarlayın. |
| **Gölge rengini şeklin dolgu rengine eşitlemenin bir yolu var mı?** | Kesinlikle. Önce `rectangle.FillColor` ayarlayın, ardından `rectangle.ShadowFormat.Color = rectangle.FillColor;` atayın. |
| **Şekli bir tablo hücresine nasıl eklerim?** | İstenen `Cell` nesnesini bulduktan sonra `cell.FirstParagraph.AppendChild(rectangle);` kullanın. |
| **Bu .NET Core'da çalışır mı?** | Evet—Aspose.Words çapraz platformdur. Sadece .NET Core/5/6 için uygun NuGet paket sürümüne referans verdiğinizden emin olun. |

## Yaygın Tuzaklar & Pro İpuçları

- **Pitfall:** `ShadowFormat.Visible = true` ayarlamayı unutmak. Gölge özellikleri sessizce yok sayılır.  
  **Fix:** Diğer gölge parametrelerini ayarlamadan önce her zaman görünürlüğü etkinleştirin.

- **Pitfall:** Çok büyük bir `BlurRadius` (ör. 20) kullanmak, gölgenin bulanık ve profesyonel olmayan görünmesine neden olabilir.  
  **Fix:** Çoğu iş belgesi için `3` ile `8` arasında değerler kullanın.

- **Pro tip:** Şeklin daha sonra seçilebilir olmasını (ör. son kullanıcı düzenlemesi) istiyorsanız, `WrapType.Inline` ayarlamaktan kaçının. Yüzen şekiller (`WrapType.None`) programatik olarak hareket ettirmeyi kolaylaştırır.

- **Pro tip:** Bir döngüde çok sayıda belge oluştururken, tek bir `Document` örneğini yeniden kullanın ve her yineleme için `doc.Clone(true)` çağırarak performansı artırın.

## Sonraki Keşfedebileceğiniz İlgili Konular

- **Add text inside a rectangle shape** – etiketler için `Shape.TextPath` kullanımını öğrenin.  
- **Create complex diagrams** – birden fazla şekil, bağlayıcı ve gruplamayı birleştirin.  
- **Export to PDF** – aynı belgeyi tek bir `doc.Save("output.pdf")` ile PDF'ye dönüştürün.  
- **Apply different fill styles** – şekiller içinde degrade, doku veya hatta resimler gibi farklı dolgu stilleri uygulayın.

## Sonuç

C# kullanarak bir Word dosyasında **create rectangle shape**, **add shadow to shape** ve **apply shadow effect** gerçekleştirdik. Beş kısa adımı izleyerek artık herhangi bir belge‑otomasyon senaryosu için yeniden kullanılabilir bir deseniniz var ve **save word document**'i güvenilir bir şekilde nasıl yapacağınızı biliyorsunuz. Boyutları, renkleri değiştirmekten veya dikdörtgeni başka bir geometriyle değiştirmekten çekinmeyin—Aspose.Words her şeyi basit hale getirir.

Bu öğreticiyi faydalı bulduysanız, GitHub'da yıldız verin veya yorumlarda kendi varyasyonlarınızı paylaşın. İyi kodlamalar, ve belgeleriniz her zaman bu gölgeli dikdörtgen kadar cilalı görünsün!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}