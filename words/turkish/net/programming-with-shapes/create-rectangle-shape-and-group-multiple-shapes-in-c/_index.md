---
category: general
date: 2026-09-18
description: C# kullanarak bir Word belgesinde dikdörtgen şekli oluşturun. Birden
  fazla şekil eklemeyi, şekilleri bir gruba eklemeyi ve Aspose.Words ile grup şeklini
  eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: tr
lastmod: 2026-09-18
og_description: C# ile bir Word dosyasında dikdörtgen şekli oluşturun. Bu kılavuz,
  birden fazla şekil eklemeyi, şekilleri bir gruba eklemeyi ve Aspose.Words kullanarak
  grup şekli eklemeyi gösterir.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: C#'ta dikdörtgen şekli oluştur ve şekilleri grupla
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: C#'ta dikdörtgen şekli oluştur ve birden çok şekli grupla
url: /tr/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta dikdörtgen şekli oluşturma ve birden fazla şekli gruplama

Bir Word belgesinde **create rectangle shape** oluşturmanız gerekiyorsa, bu öğretici tam bir çözüm sunar. **add multiple shapes**, **add shapes to a group** ve **insert group shape** işlemlerinin Aspose.Words API for .NET kullanarak nasıl yapılacağını göreceksiniz.

Şekillerle çalışmak, raporlar, sözleşmeler veya pazarlama materyallerini programlı olarak oluştururken yaygın bir gereksinimdir. Bu rehberin sonunda, bir dikdörtgen, bir elips ve her iki şekli de içeren bir grup barındıran bir `.docx` dosyası üreten çalıştırılabilir bir C# konsol uygulamanız olacak.

Tek gereksinim, son bir .NET SDK (6.0 veya daha yeni) ve lisanslı bir Aspose.Words for .NET kopyasıdır. Başka bir araç gerekmez.

## Prerequisites

- .NET 6.0 SDK veya daha yeni  
- Aspose.Words for .NET (NuGet paketi `Aspose.Words`)  
- C# sözdizimi hakkında temel aşinalık  

Paketi aşağıdaki komutla kurabilirsiniz:

```bash
dotnet add package Aspose.Words
```

## Adım 1: Aspose.Words ile dikdörtgen şekli oluşturma

İlk adım, `Rectangle` türünde bir `Shape` nesnesi oluşturmaktır. Bu nesne, belgede görünecek görsel dikdörtgeni temsil eder.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Neden önemlidir:** `ShapeType.Rectangle`, Aspose.Words'e geometrik bir dikdörtgen çizmeyi söyler. `Width` ve `Height` ayarlamak, boyutunu puan cinsinden tanımlar (1 point = 1/72 inç). Dolgu ve kenar renkleri eklemek, şeklin ek stil gerektirmeden görünür olmasını sağlar.

## Adım 2: Belgeye birden fazla şekil ekleme

Dikdörtgenden sonra, istediğiniz sayıda ek şekil oluşturabilirsiniz. Bu örnekte, **add multiple shapes** nasıl çalıştığını göstermek için bir elips ekliyoruz.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Neden önemlidir:** `new Shape` her çağrısı bağımsız bir çizim nesnesi oluşturur. Onları sırasıyla ekleyerek, daha sonra gruplanabilir veya ayrı ayrı konumlandırılabilir bir şekil koleksiyonu oluşturursunuz.

## Adım 3: Şekilleri gruba ekleme

Şekilleri gruplamak, grup tek bir düğüm gibi davrandığı için düzen yönetimini basitleştirir. Bu adım, `GroupShape` kullanarak **add shapes to group** nasıl yapılır gösterir.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Neden önemlidir:** `GroupShape`, bir kapsayıcı gibi davranır. Grubu taşıdığınızda, döndürdüğünüzde veya yeniden boyutlandırdığınızda, tüm alt şekiller otomatik olarak izler. Sınırlayıcı kutu (200 × 200 puan), alt şekiller için koordinat alanını tanımlar.

## Adım 4: Grup şekli belgeye ekleme

Grup artık dikdörtgen ve elipsi içerdiğine göre, **insert group shape** işlemini istediğiniz konuma eklemeniz gerekir. Builder zaten boş grubu yerleştirdi, ancak gerekirse başka bir yere de ekleyebilirsiniz.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Neden önemlidir:** `Left` ve `Top` ayarlamak, tüm grubu sayfa içinde hareket ettirir. Belgeyi kaydetmek, şekil hiyerarşisini Microsoft Word, LibreOffice veya herhangi bir uyumlu görüntüleyicide açılabilecek bir `.docx` dosyasına yazar.

## Tam çalıştırılabilir örnek

Aşağıda tüm adımları birleştiren tam program bulunmaktadır. Kodu yeni bir konsol projesine kopyalayın ve `GroupShapeExample.docx` dosyasını oluşturmak için çalıştırın.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Beklenen çıktı:**  
`GroupShapeExample.docx` dosyasını açtığınızda, içinde açık mavi bir dikdörtgen ve açık mercan rengi bir elips bulunan tek bir grup gösterilir; her ikisi de 200 × 200 puanlık bir kapsayıcı içinde konumlandırılmıştır. Grup, Word'de tek bir nesne olarak seçilebilir ve bu da **add shapes to group** işleminin başarılı olduğunu doğrular.

## Yaygın varyasyonlar ve uç durumlar

| Durum | Önerilen ayarlama |
|-----------|------------------------|
| Farklı şekil türleri (ör. `ShapeType.Line`) | İstenen `ShapeType` ile şekli oluşturun ve geometrisini buna göre ayarlayın. |
| Şekli döndürme ihtiyacı | Şekli gruba eklemeden önce `shape.Rotation = 45;` (derece) kullanın. |
| Birçok grup içeren büyük belgeler | Tek bir `DocumentBuilder` örneği yeniden kullanın; bellek yükünü azaltmak için her grup için yeni bir builder oluşturmaktan kaçının. |
| DOCX yerine PDF olarak kaydetme | Grup eklendikten sonra `doc.Save("output.pdf", SaveFormat.Pdf);` çağrısını yapın. |

**Pro ipucu:** Kesin konumlandırma gerektiğinde grup için her zaman açık `Left` ve `Top` değerleri ayarlayın. Bunları atladığınızda, grup builder'ın mevcut imleç konumunu devralır ve bu beklenmedik düzen sonuçlarına yol açabilir.

## Sonuç

Artık C# kullanarak bir Word belgesinde **create rectangle shape**, **add multiple shapes**, **add shapes to group** ve **insert group shape** işlemlerinin nasıl yapılacağını biliyorsunuz. Tam örnek, belge oluşturulmasından son dosyanın kaydedilmesine kadar tam iş akışını gösterir.

Sonra, **positioning shapes relative to text**, **applying text wrapping**, ve **exporting grouped shapes to PDF** gibi ilgili konuları keşfedin. Bu uzantılar, Aspose.Words ile karmaşık, programlı belge düzenleri oluşturmanızı sağlar.

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [C# kullanarak Word'de dikdörtgen şekli oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Word Belgesinde Grup Şekli Oluşturma – Aspose.Words for .NET Kullanarak](/words/english/net/working-with-shapes/add-group-shape/)
- [Gölgelendirilmiş Dikdörtgen Şekilli Boş Word Belgesi Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}