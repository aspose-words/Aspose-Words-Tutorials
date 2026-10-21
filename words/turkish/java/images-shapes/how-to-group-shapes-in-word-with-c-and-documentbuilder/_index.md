---
category: general
date: 2026-10-04
description: C# kullanarak Word’de şekilleri nasıl gruplayacağınızı öğrenin. Bu kılavuz,
  dikdörtgen şekli eklemeyi, birden fazla şekli gruplamayı ve programlı olarak boş
  bir Word dosyası oluşturmayı gösterir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: tr
lastmod: 2026-10-04
og_description: C# kullanarak Word'de şekilleri gruplayın. Dikdörtgen şekli eklemek,
  birden fazla şekli gruplaymak ve DocumentBuilder ile boş bir Word dosyası oluşturmak
  için bu adım adım rehberi izleyin.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: C# ile Word’de Şekilleri Gruplama – Tam DocumentBuilder Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: C# ve DocumentBuilder ile Word’te şekilleri nasıl gruplandırılır
url: /tr/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ve DocumentBuilder ile Word'de Şekilleri Nasıl Gruplandırılır

If you need to **group shapes in Word** from a C# application, this tutorial shows you exactly how to do it. You’ll see how to *insert rectangle shape*, combine several drawings into a single group, and finally **create a blank Word file** that contains the grouped objects.

C# uygulamasından **Word'de şekilleri gruplandırmanız** gerekiyorsa, bu öğretici tam olarak nasıl yapılacağını gösterir. *Dikdörtgen şekli eklemeyi* görecek, birkaç çizimi tek bir grup içinde birleştirecek ve sonunda **gruplandırılmış nesneleri içeren boş bir Word dosyası oluşturacaksınız**.

Working with shapes is a common requirement when generating reports, invoices, or custom templates programmatically. By the end of this guide you’ll have a reusable code snippet that you can drop into any .NET project that references Aspose.Words.

Şekillerle çalışmak, raporlar, faturalar veya özel şablonlar programlı olarak oluşturulurken yaygın bir gereksinimdir. Bu rehberin sonunda, Aspose.Words başvuran herhangi bir .NET projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız.

## What you’ll learn

## Öğrenecekleriniz

- Create a blank Word document from scratch.  
- Insert a rectangle shape and an ellipse using `DocumentBuilder`.  
- **Group multiple shapes** into a `GroupShape`.  
- Use **append child to group** to build the hierarchy.  
- Save the file to disk and verify the result.

- Sıfırdan boş bir Word belgesi oluşturun.  
- `DocumentBuilder` kullanarak bir dikdörtgen şekli ve bir elips ekleyin.  
- **Birden fazla şekli** `GroupShape` içine **gruplandırın**.  
- Hiyerarşiyi oluşturmak için **append child to group** kullanın.  
- Dosyayı diske kaydedin ve sonucu doğrulayın.

No prior experience with Aspose.Words is required, but you should have a basic understanding of C# and .NET development.

Aspose.Words ile ilgili önceden bir deneyime sahip olmanız gerekmez, ancak C# ve .NET geliştirme hakkında temel bir anlayışa sahip olmalısınız.

## Prerequisites

## Önkoşullar

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 or later | Provides the runtime for the C# code. |
| Aspose.Words for .NET (latest version) | Supplies `Document`, `DocumentBuilder`, and shape classes. |
| An IDE such as Visual Studio 2022 (or VS Code) | Makes it easy to compile and run the sample. |
| Write permission to a folder on your machine | Needed for the `doc.save` call. |

| Gereksinim | Sebep |
|------------|-------|
| .NET 6.0 or later | C# kodu için çalışma zamanını sağlar. |
| Aspose.Words for .NET (latest version) | `Document`, `DocumentBuilder` ve şekil sınıflarını sağlar. |
| An IDE such as Visual Studio 2022 (or VS Code) | Örneği derlemek ve çalıştırmak kolay olur. |
| Write permission to a folder on your machine | `doc.save` çağrısı için gereklidir. |

Install Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Group shapes in Word – step‑by‑step guide

## Word'de Şekilleri Gruplandırma – adım adım kılavuz

Below is the full, runnable program. Each section is explained in detail so you understand **why** the code is written this way, not just **what** it does.

Aşağıda tam, çalıştırılabilir program yer almaktadır. Her bölüm detaylı olarak açıklanmıştır, böylece kodun **neden** bu şekilde yazıldığını, sadece **ne** yaptığını değil, anlamanızı sağlar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Why each step matters

### Her adımın önemi

1. **Create a blank Word file** – Starting with a clean document guarantees that no hidden formatting interferes with shape positioning.  
2. **Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level node manipulation, letting you focus on layout.  
3. **Insert individual shapes** – You first need separate objects (`insert rectangle shape` and an ellipse) before you can group them. Adjusting `Left` and `Top` ensures they appear side‑by‑side.  
4. **Group multiple shapes** – By creating a `GroupShape` and using **append child to group**, you turn two independent drawings into a single logical unit. Moving or resizing the group will affect both children simultaneously.  
5. **Save the document** – The final file, `GroupedShapes.docx`, can be opened in Microsoft Word to verify that the rectangle and ellipse are indeed grouped (select one, and both move together).

1. **Boş bir Word dosyası oluştur** – Temiz bir belgeyle başlamak, gizli biçimlendirmelerin şekil konumlandırmasını etkilememesini garantiler.  
2. **DocumentBuilder'ı başlat** – `DocumentBuilder`, düşük seviyeli düğüm manipülasyonunu soyutlayarak, odaklanmanızı düzen üzerine getirir.  
3. **Tek tek şekilleri ekle** – Gruplamadan önce ayrı nesnelere (`insert rectangle shape` ve bir elips) ihtiyacınız var. `Left` ve `Top` ayarlamak, yan yana görünmelerini sağlar.  
4. **Birden fazla şekli grupla** – `GroupShape` oluşturarak ve **append child to group** kullanarak iki bağımsız çizimi tek bir mantıksal birime dönüştürürsünüz. Grubu taşıma veya yeniden boyutlandırma, her iki çocuğu aynı anda etkiler.  
5. **Belgeyi kaydet** – Son dosya `GroupedShapes.docx`, şeklin ve elipsin gerçekten gruplandığını doğrulamak için Microsoft Word'de açılabilir (birini seçin, ikisi birlikte hareket eder).

### Expected output

### Beklenen çıktı

Open `GroupedShapes.docx` in Microsoft Word:

- You’ll see a rectangle and an ellipse placed next to each other.  
- Selecting either shape highlights both, confirming they belong to the same group.  
- The group can be dragged, resized, or formatted as a single object.

- Yan yana bir dikdörtgen ve bir elips göreceksiniz.  
- Herhangi bir şekli seçmek, ikisini de vurgular ve aynı gruba ait olduklarını onaylar.  
- Grup, tek bir nesne gibi sürüklenebilir, yeniden boyutlandırılabilir veya biçimlendirilebilir.

![Word belgesi içinde gruplandırılmış dikdörtgen ve elips diyagramı](https://example.com/grouped-shapes.png){: .center-image alt="Word belgesi içinde gruplandırılmış dikdörtgen ve elips diyagramı"}

*Ekran görüntüsü, son gruplandırılmış şekilleri gösterir.*

---

## Insert rectangle shape – customizing size and style

## Dikdörtgen şekli ekleme – boyut ve stil özelleştirme

If you need a rectangle with a specific fill color or border, modify the `Shape` object after insertion:

Belirli bir dolgu rengi veya kenarlığı olan bir dikdörtgene ihtiyacınız varsa, eklemeden sonra `Shape` nesnesini değiştirin:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

These properties are part of the `Shape` class, and they work for any shape type, not just rectangles. Adjusting the style before you **append child to group** ensures the group inherits the visual properties you set.

`Shape` sınıfının bir parçası olan bu özellikler, sadece dikdörtgenler için değil, tüm şekil türleri için çalışır. Stili **append child to group**'dan önce ayarlamak, grubun belirlediğiniz görsel özellikleri devralmasını sağlar.

---

## Group multiple shapes – handling more than two objects

## Birden fazla şekli gruplandırma – iki objeden fazla ile çalışmak

The example groups a rectangle and an ellipse, but you can add any number of shapes:

Örnek bir dikdörtgen ve bir elipsi gruplandırıyor, ancak istediğiniz sayıda şekil ekleyebilirsiniz:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Pro tip:** After you have built a complex group, you can lock its layout to prevent accidental changes:

**İpucu:** Karmaşık bir grup oluşturduktan sonra, istem dışı değişiklikleri önlemek için düzenini kilitleyebilirsiniz:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – ordering matters

## Append child to group – sıralama önemlidir

The order in which you call `AppendChild` defines the Z‑order (which shape appears on top). In the sample, the rectangle is added first, then the ellipse, so the ellipse overlays the rectangle if they intersect. Re‑ordering is as simple as calling `RemoveChild` and re‑adding:

`AppendChild`'ı çağırma sırası Z‑order'ı (hangi şeklin üstte görüneceğini) belirler. Örnekte, önce dikdörtgen eklenir, ardından elips, bu yüzden elips kesişiyorsa dikdörtgenin üzerine gelir. Yeniden sıralama, `RemoveChild` çağırıp yeniden eklemek kadar basittir:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Create blank Word file – reusable helper method

## Boş Word dosyası oluşturma – yeniden kullanılabilir yardımcı yöntem

If your application frequently needs a fresh document, encapsulate the creation logic:

Uygulamanız sık sık yeni bir belgeye ihtiyaç duyuyorsa, oluşturma mantığını kapsülleyin:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

You can then replace the `new Document()` line in the main program with `CreateBlankWordFile()`. This demonstrates the **create blank word file** concept in a reusable way.

Ardından ana programdaki `new Document()` satırını `CreateBlankWordFile()` ile değiştirebilirsiniz. Bu, **boş word dosyası oluştur** konseptini yeniden kullanılabilir bir şekilde gösterir.

---

## Common pitfalls and how to avoid them

## Yaygın tuzaklar ve nasıl önlenir

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| Shapes appear off‑page | Default `Left`/`Top` values are 0, which places the shape at the margin. | Explicitly set `Left` and `Top` after insertion. |
| Group loses formatting | Changing a child shape after it’s added to a group can break the group’s layout. | Apply all visual properties **before** calling `AppendChild`. |
| Saved file is empty | `DocumentBuilder` was never used to add a node, or `doc.Save` was called on a different `Document` instance. | Verify you are saving the same `Document` you built. |
| Compatibility warnings in Word | Using newer shape features not supported

| Sorun | Neden olur | Çözüm |
|-------|------------|-------|
| Şekiller sayfadan dışarı çıkıyor | Varsayılan `Left`/`Top` değerleri 0'dır, bu da şekli kenara yerleştirir. | `Left` ve `Top` değerlerini eklemeden sonra açıkça ayarlayın. |
| Grup biçimlendirmesini kaybeder | Bir çocuğu gruba ekledikten sonra şekli değiştirmek, grubun düzenini bozabilir. | Tüm görsel özellikleri **AppendChild**'ı çağırmadan **önce** uygulayın. |
| Kaydedilen dosya boş | `DocumentBuilder` hiçbir zaman bir düğüm eklemek için kullanılmadı veya `doc.Save` farklı bir `Document` örneği üzerinde çağrıldı. | Oluşturduğunuz aynı `Document`'ı kaydettiğinizden emin olun. |
| Word'de uyumluluk uyarıları | Desteklenmeyen yeni şekil özelliklerini kullanmak |  |

## What Should You Learn Next?

## Sonra Ne Öğrenmelisiniz?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words for .NET kullanarak Word Belgesinde Grup Şekli Oluştur](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET kullanarak Word Belgelerine Şekil Ekle](/words/english/net/working-with-shapes/insert-shape/)
- [C# kullanarak Word'de dikdörtgen şekli oluştur – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}