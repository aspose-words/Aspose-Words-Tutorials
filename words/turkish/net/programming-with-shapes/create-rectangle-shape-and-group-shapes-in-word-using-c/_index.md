---
category: general
date: 2026-09-08
description: C# ile bir Word belgesinde dikdörtgen şekil oluşturun. Şekil boyutunu
  ayarlamayı, birden fazla şekli gruplamayı ve programlı olarak boş bir Word belgesi
  oluşturmayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: tr
lastmod: 2026-09-08
og_description: C# ile bir Word belgesine dikdörtgen şekli oluşturun. Bu rehber, şekil
  boyutunu nasıl ayarlayacağınızı, birden fazla şekli nasıl gruplayacağınızı ve programlı
  olarak boş bir Word belgesi nasıl oluşturacağınızı gösterir.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: C# ile Word’de dikdörtgen şekli oluşturun ve şekilleri gruplayın
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# kullanarak Word'de dikdörtgen şekli oluşturun ve şekilleri gruplayın
url: /tr/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# kullanarak Word'de dikdörtgen şekli oluşturma ve şekilleri gruplama

Bir Word dosyası içinde **dikdörtgen şekli oluşturmanız** gerekiyorsa, bu öğretici size eksiksiz, çalıştırmaya hazır bir çözüm sunar. Şekil boyutunu nasıl ayarlayacağınızı, birden fazla şekli nasıl gruplayacağınızı ve sıfırdan boş bir Word belgesi nasıl oluşturacağınızı göreceksiniz — tüm bunlar Aspose.Words for .NET kütüphanesi ile.

Word belgeleriyle programatik olarak çalışmak genellikle birçok küçük detayı jonglör gibi yönetmek gibi hissettirir. Bu rehberin sonunda, bir dikdörtgen ve bir elipsi birlikte gruplayan bir `.docx` dosyası üreten tek bir yönteme sahip olacaksınız; bu dosya daha fazla düzenleme veya yazdırma için hazır.

## Önkoşullar

* .NET 6.0 veya daha yenisi (kod ayrıca .NET Framework 4.6+ ile de çalışır)
* **Aspose.Words for .NET**'in lisanslı bir kopyası (ücretsiz bir değerlendirme anahtarı kullanabilirsiniz)
* Visual Studio 2022 veya Visual Studio Code gibi bir IDE
* C# sözdizimiyle temel aşinalık

`Aspose.Words` dışındaki ek NuGet paketlerine ihtiyaç yoktur.

## Adım 1: Boş bir Word belgesi oluşturma

İlk adım, şekilleri barındıracak boş bir belge oluşturmaktır. Bu, *boş word belgesi oluştur* gereksinimini karşılar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Boş bir belge oluşturmak size temiz bir tuval sağlar. `Document` nesnesi tüm `.docx` dosyasını temsil eder ve `FirstSection.Body.FirstParagraph` yeni düğümler için varsayılan ekleme noktasını oluşturur.

## Adım 2: Dikdörtgen şekli oluşturma

Şimdi dikdörtgeni ekleyebilirsiniz. **dikdörtgen şekli oluştur** işleminin gerçekleştiği yerdir.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Boyutları doğrudan ayarlamak **şekil boyutunu ayarla** anahtar kelimesine yanıt verir. Tüm boyut değerleri puan (point) cinsinden ifade edilir; bu, şeklin nihai belgede nasıl görüneceği üzerinde hassas kontrol sağlar.

## Adım 3: Ek bir şekil oluşturma (elips)

Tipik bir kullanım senaryosu birkaç şekli birleştirmektir. Burada daha sonra aynı kapsayıcıyı paylaşacak bir elips ekliyoruz.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Her iki şekil de bu noktada hâlâ bağımsızdır. Bir sonraki adım, **birden fazla şekli gruplama** nasıl yapılır gösterir.

## Adım 4: Word'de şekilleri gruplama

Şekilleri gruplamak, onları tek bir birim olarak taşımanıza, yeniden boyutlandırmanıza veya biçimlendirmenize olanak tanır. Bu, **word'de şekilleri gruplama** ve **birden fazla şekli gruplama** gereksinimlerini karşılar.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

`GroupShape.Bounds` özelliği, alt şekiller için koordinat sistemini belirler. Dikdörtgeni ve elipsi aynı `GroupShape` içine yerleştirerek, daha sonra tek bir çağrı ile birlikte taşıyabilir veya döndürebilirsiniz.

## Adım 5: Belgeyi kaydetme

Son olarak, belgeyi diske yazın. Dosya, az önce oluşturduğunuz gruplanmış şekilleri içerecek.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

Programı çalıştırdıktan sonra, `GroupedShapes.docx` dosyasını Microsoft Word'de açın. Bir dikdörtgen ve bir elipsin birlikte gruplandığını görmelisiniz; bir şekli seçmek diğerini de seçer, bu da grubun başarılı olduğunu doğrular.

## Tam kaynak kodu

Aşağıdaki tam programı yeni bir console‑app projesine kopyalayın ve çalıştırın. Ek bir koda gerek yok.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Beklenen çıktı

Programı çalıştırmak `GroupedShapes.docx` dosyasını üretir. Dosyayı Word'de açtığınızda şunlar görülür:

* Mavi kenarlık ve açık gri dolguya sahip bir **dikdörtgen** (100 pt × 50 pt).
* Koyu yeşil kenarlık ve açık sarı dolguya sahip bir **elips** (80 pt × 80 pt).
* Her iki şekil de tek bir grup içinde, bu yüzden birini hareket ettirmek diğerini de hareket ettirir.

## Yaygın sorular ve uç durumlar

| Soru | Cevap |
|----------|--------|
| **Gruba iki'den fazla şekil ekleyebilir miyim?** | Evet. Ek `Shape` nesneleri oluşturun ve her biri için `group.AppendChild(yourShape)` metodunu çağırın. |
| **Grubu döndürmem gerekirse ne yapmalıyım?** | `group.RotationAngle = 45;` (derece) olarak ayarlayın. Tüm alt şekiller birlikte döner. |
| **Belge kaydedildikten sonra şekilleri gruplayabilir miyim?** | Gruplamayı kaydetmeden önce belge yapısını değiştirmeniz gerekir; aksi takdirde dosyayı yükleyip şekilleri bulup grubu yeniden oluşturmanız gerekir. |
| **Herhangi bir nesneyi dispose etmem gerekiyor mu?** | Aspose.Words kendi kaynaklarını yönetir, ancak akışları manuel olarak açarsanız `FileStream` nesnelerini dispose etmelisiniz. |
| **Kod .doc (ikili) formatında çalışır mı?** | Evet, `doc.Save("output.doc")` olarak değiştirin. Grup davranışı aynı kalır. |

## Sonuç

Artık C# kullanarak bir Word dosyası içinde **dikdörtgen şekli oluşturma**, **şekil boyutunu ayarlama** ve **birden fazla şekli gruplama** konularını biliyorsunuz. Bu yaklaşım, manuel düzenleme yapmadan programatik olarak karmaşık diyagramlar, filigranlar veya şablon‑tabanlı raporlar oluşturmanıza olanak tanır.

### Sonraki adımlar

* **Word'de şekilleri gruplama** konusunu, aynı gruba metin kutuları veya resimler ekleyerek daha fazla keşfedin.
* `SetShapeSize` desenini, sayfa düzenine göre boyutları dinamik olarak hesaplamak için kullanın.
* Bu tekniği posta birleştirme alanlarıyla birleştirerek ölçekli kişiselleştirilmiş belgeler oluşturun.

Farklı şekil tipleri, renkler ve grup dönüşümleriyle denemeler yapmaktan çekinmeyin. İyi kodlamalar!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for .NET Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)
- [Gölgelendirilmiş Dikdörtgen Şekilli Boş Word Belgesi Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Gölgelendirilmiş Dikdörtgenli Word Belgesi Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}