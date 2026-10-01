---
category: general
date: 2026-09-30
description: Aspose.Words kullanarak C#’ta boş bir belge oluşturun ve dikdörtgen şekli,
  elips ekleyin, birden fazla şekli gruplayın. Şekilleri nasıl ekleyeceğinizi ve grubu
  nasıl oluşturacağınızı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: tr
lastmod: 2026-09-30
og_description: C#'de boş belge oluşturun ve Aspose.Words ile şekil eklemeyi ve birden
  fazla şekli gruplamayı öğrenin. Adım adım öğreticiyi izleyin.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: C#'ta boş bir belge oluşturun ve şekilleri gruplayın – Aspose.Words rehberi
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: C#'ta Aspose.Words ile boş belge oluşturma ve şekil ekleme
url: /tr/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile C#'ta Boş Belge Oluşturma ve Şekil Ekleme

Eğer **boş belge oluşturmanız** ve bunu grafiklerle doldurmanız gerekiyorsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. **Dikdörtgen şekil eklemeyi**, diğer çizim nesnelerini eklemeyi ve ardından **birden fazla şekli gruplamayı** göreceksiniz, böylece tek bir birim gibi davranırlar.

Şekillerle çalışmak, sözleşmeler, sertifikalar veya özel raporlar oluştururken yaygın bir gereksinimdir. Bu öğreticide, .NET için Aspose.Words API'sını kullanarak belgeyi başlatmadan son dosyayı kaydetmeye kadar tam iş akışını öğreneceksiniz.

## Prerequisites

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 (veya daha yeni) SDK  
* Geçerli bir Aspose.Words for .NET lisansı (bu örnek için ücretsiz deneme sürümü yeterlidir)  
* Visual Studio 2022 veya Visual Studio Code gibi bir IDE  

`Aspose.Words` dışındaki ek NuGet paketlerine ihtiyaç yoktur.

## How to create blank document and work with shapes

İlk adım, bir `Document` nesnesi oluşturmaktır. Bu nesne, bellek içindeki Word dosyasını temsil eder ve `DocumentBuilder`'a erişim sağlar; bu da içerik eklemek için temel araçtır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** Boş bir belge, size temiz bir tuval sunar. `DocumentBuilder`, geçerli ekleme noktasını tutar, böylece eklediğiniz her şekil otomatik olarak uygun sayfaya yerleştirilir.

## Insert rectangle shape and other shapes

Şimdi bir dikdörtgen ve bir elips ekleyeceğiz. Her iki çağrı da aynı `InsertShape` metodunu kullanır; bu, Aspose.Words'ta **şekil eklemenin** önerilen yoludur.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*`InsertShape` metodu, şekli geçerli imleç konumuna otomatik olarak yerleştirir.* Daha kesin bir konumlandırma gerekiyorsa, eklemeden sonra `Shape.Left` ve `Shape.Top` değerlerini ayarlayabilirsiniz.

## Group multiple shapes into a single object

Şimdi dikdörtgen ve elipsi tek bir mantıksal varlıkta birleştiriyoruz. Gruplama, birden fazla şekli birlikte taşımak veya yeniden boyutlandırmak istediğinizde kullanışlıdır.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**How this works:** `InsertGroupShape` diğer `Shape` nesneleri gibi davranan bir kapsayıcı oluşturur. `AppendChild` çağrısıyla mevcut şekilleri bu kapsayıcıya taşırsınız; böylece göreceli koordinatları otomatik olarak güncellenir.

### Practical tip

Daha sonra iki’den fazla şekil için programlı olarak **grup oluşturmanız** gerektiğinde, her ek `Shape` örneği için `AppendChild`'ı tekrarlamanız yeterlidir. Grup, resimler, metin kutuları veya hatta diğer gruplar gibi herhangi bir sayıda çizim nesnesi içerebilir.

## Full example – how to insert shapes and save the document

Aşağıda, şimdiye kadar tartıştığımız tüm adımları gösteren tam, çalıştırılabilir bir program yer almaktadır. Kodu çalıştırdığınızda, bir dikdörtgen, bir elips ve gruplanmış bir şekil içeren `ShapesDemo.docx` dosyası oluşturulur.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected output:** `ShapesDemo.docx` dosyasını Microsoft Word'de açtığınızda, mavi bir dikdörtgen, yeşil bir elips ve grubu temsil eden gri bir kenarlıkla tek bir sayfa görürsünüz. Grubu hareket ettirmek, iki şekli de birlikte taşır ve **birden fazla şekli gruplama** işleminin başarılı olduğunu doğrular.

## Common questions and edge‑case handling

| Question | Answer |
|----------|--------|
| *What if I need the shapes on a specific page?* | Şekilleri eklemeden önce `builder.MoveToDocumentEnd();` çağırın veya belirli bir bölüme hedeflemek için `builder.MoveToSection(sectionIndex);` kullanın. |
| *Can I add text inside a grouped shape?* | Evet. `ShapeType.TextBox` tipinde bir `Shape` oluşturun, metnini yapılandırın ve ardından `AppendChild` ile `GroupShape` içine ekleyin. |
| *Do shape dimensions use points or pixels?* | Aspose.Words **point** birimini (1 pt = 1/72 inç) kullanır. Bu, yazıcılar ve ekranlar arasında tutarlı boyutlandırma sağlar. |
| *How to change the group’s rotation?* | `groupShape.RotationAngle = 45;` (derece) olarak ayarlayın. Tüm alt şekiller, grup kökeni etrafında döner. |

## Conclusion

Artık **boş belge oluşturmayı**, **dikdörtgen şekil eklemeyi**, **elips gibi şekilleri eklemeyi** ve **birden fazla şekli gruplamayı** Aspose.Words for .NET kullanarak nasıl yapacağınızı biliyorsunuz. Tam kod örneği önerilen yaklaşımı gösteriyor ve yukarıdaki ipuçları, metin kutuları ekleme veya grupları döndürme gibi daha karmaşık senaryolara uyarlamanıza yardımcı olur.

Daha fazlasını keşfetmeye hazır mısınız? Gruba bir resim şekli ekleyin, farklı dolgu renkleriyle deney yapın veya her sayfada kendi gruplandırılmış diyagramı bulunan çok sayfalı bir rapor oluşturun. Aynı prensipler geçerlidir; böylece bu deseni herhangi bir belge‑otomasyon projesine ölçeklendirebilirsiniz.

## What Should You Learn Next?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalarla tam çalışan kod örnekleri içerir; böylece ek API özelliklerini ustalaşabilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Aspose.Words for .NET Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET Kullanarak Word Belgelerine Şekil Ekleme](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words ile Boş Word Belgesi Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}