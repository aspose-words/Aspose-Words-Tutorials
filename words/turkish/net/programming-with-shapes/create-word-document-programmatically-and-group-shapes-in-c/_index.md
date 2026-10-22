---
category: general
date: 2026-08-10
description: Aspose.Words kullanarak programlı bir şekilde Word belgesi oluşturun,
  birden fazla şekli Word'de nasıl gruplayacağınızı, Word'e dikdörtgen eklemeyi ve
  C#'ta grup şekli oluşturmayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: tr
lastmod: 2026-08-10
og_description: Aspose.Words ile programlı olarak Word belgesi oluşturun. Bu rehber,
  birden fazla şekli Word içinde gruplamayı, Word’e dikdörtgen eklemeyi ve düz metin
  içerik denetimini C# ile gömmeyi gösterir.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Word belgesini programlı olarak oluştur – C#'ta şekilleri grupla
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Programlı olarak Word belgesi oluştur ve C#'ta şekilleri grupla
url: /tr/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programlı olarak Word belgesi oluşturma ve C#'ta şekilleri gruplama

Programlı olarak **create word document programmatically** ihtiyacınız varsa, bu öğretici Aspose.Words ile bir DOCX dosyası oluşturmayı ve **group multiple shapes word** birlikte gruplamayı gösterir. Ayrıca **add rectangle to word** ve **how to create group shape** konularını da ele alacağız; bu, bir dikdörtgen ve bir elips içeren bir grup şekli ve kullanıcı girişi için düz metin StructuredDocumentTag içerir.

Kod çalıştıktan sonra, bir grup dikdörtgen‑elips şekli ve kullanıcının bir isim yazabileceği bir içerik denetimi içeren, kullanıma hazır bir Word dosyası elde edeceksiniz. Word'de manuel düzenleme yapmanız gerekmez.

## Gereksinimler

- .NET 6.0 veya üzeri (örnek .NET 6 hedefli, ancak herhangi bir yeni .NET sürümü çalışır)
- Aspose.Words for .NET lisansı (ücretsiz deneme sürümü test için çalışır)
- Visual Studio 2022 veya tercih ettiğiniz herhangi bir C# IDE'si
- C# sözdizimi hakkında temel bilgi

## Programlı olarak Word belgesi oluşturma – genel iş akışı

İşlem üç mantıksal aşamadan oluşur:

1. **Initialize** bir `Document` ve bir `DocumentBuilder` – oluşturduğunuz her Word dosyasının temeli.
2. **Build a group shape** bir dikdörtgen ve bir elips tutan – **group multiple shapes word** ve **how to create group shape** gösterir.
3. **Insert a StructuredDocumentTag (SDT)** – son kullanıcıların veri girmesine izin veren düz metin içerik denetimi, **add rectangle to word**'i genel belge düzeninin bir parçası olarak gösterir.

Aşağıda tam, çalıştırılabilir kod ve ardından adım adım açıklama yer almaktadır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Adım 1 – Belgeyi ve builder'ı başlatma
`Document` nesnesi tüm DOCX dosyasını temsil eder, `DocumentBuilder` ise içerik eklemek için kullanışlı bir API sağlar. Bunları başlatmak, **create word document programmatically** yaptığınızda ilk gerekliliktir.

> **Pro tip:** Aynı belgeyi birden fazla işlemde yeniden kullanmayı planlıyorsanız, gereksiz nesne oluşturmayı önlemek için tek bir `DocumentBuilder` örneği tutun.

### Adım 2 – Grup şekil kapsayıcısı oluşturma
`ShapeType.Group` özelliğine sahip bir `Shape`, diğer şekilleri tutabilen bir tuval görevi görür. `Width` ve `Height` ayarları, grup için sınırlayıcı kutuyu tanımlar. Bu, Aspose.Words'te **how to create group shape**'in temelidir.

> **Köşe durumu:** Grubun genişliği, içindeki öğelerin toplam genişliğinden küçükse, öğeler kırpılır. Grubu, her bir alt şekli barındıracak kadar büyük tutun.

### Adım 3 – Word'e bir dikdörtgen ekleme
Bir dikdörtgen `ShapeType.Rectangle` ile oluşturulur. `Left` ve `Top` özellikleri, dikdörtgeni grubun orijinine göre konumlandırır. Bu adım **add rectangle to word**'i gösterir ve kesin yerleşimi nasıl kontrol edebileceğinizi gösterir.

> **Yaygın hata:** `Left`/`Top` ayarlamayı unutmak, dikdörtgenin grubun varsayılan orijini (0,0) de görünmesine neden olur; bu da diğer öğelerle çakışabilir.

### Adım 4 – Gruba bir elips (daire) ekleme
Elips, dikdörtgen gibi aynı şekilde eklenir, ancak `ShapeType.Ellipse` kullanılır. `Left = 210` değeri, elipsi dikdörtgenin sağına kaydırır ve aynı grup içinde görsel olarak ayrı bir şekil çifti oluşturur.

> **Neden grup kullanılır?** Gruplama, iki şekli daha sonra tek bir işlemle birlikte taşımanıza, döndürmenize veya yeniden boyutlandırmanıza olanak tanır ve birbirlerine göre konumlarını korur.

### Adım 5 – Tamamlanmış grup şekli belgeye ekleme
`builder.InsertNode(groupShape)` tüm grubu mevcut imleç konumuna yerleştirir. Grup zaten alt öğelerini içerdiği için, dikdörtgen veya elips için ek ekleme çağrıları yapmanıza gerek yoktur.

### Adım 6 – Düz metin StructuredDocumentTag (SDT) oluşturma
StructuredDocumentTag, belge Word'de açıldığında son kullanıcıların doldurabileceği bir içerik denetimidir. `Title = "CustomerName"` ayarı, denetime anlamlı bir tanımlayıcı verir; bu, daha sonraki veri çıkarma işlemleri için faydalıdır.

> **Neden düz metin SDT?** Girişi yalnızca düz metinle sınırlayarak, sonraki işlemleri bozabilecek yanlışlıkla biçimlendirmeyi önler.

### Adım 7 – Belgeyi kaydetme
`doc.Save("GroupAndSDT.docx")` dosyayı diske yazar. Oluşan DOCX, grup şekilleri ve SDT'yi içerir. Dosyayı Microsoft Word'de açtığınızda, bir dikdörtgenin yanında bir daire göreceksiniz; ikisi tek bir nesne olarak seçilebilir ve ardından “Enter name here …” yer tutucu metni gelir.

#### Beklenen çıktı
- Çalışma klasöründe **GroupAndSDT.docx** adlı bir dosya.
- Word'de: tek bir birim olarak hareket ettirebileceğiniz grup şekli (dikdörtgen + elips).
- Grubun hemen altında, kullanıcıdan isim girmesini isteyen gri tonlu bir içerik denetimi.

## Ek varyasyonlar ve en iyi uygulamalar

### Farklı şekil tipleri kullanma
`ShapeType.Rectangle` veya `ShapeType.Ellipse` yerine herhangi bir `ShapeType` (ör. `ShapeType.Polygon`, `ShapeType.Line`) kullanabilirsiniz. Grup mantığı aynı kalır.

### Setting fill color and borders
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Dolgu ve kenar eklemek, özellikle belge teknik olmayan paydaşlarla paylaşıldığında görsel ayrımı iyileştirir.

### Rotating the entire group
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Grubu döndürmek, her bir alt öğeyi ayrı ayrı döndürmekten daha verimlidir.

### PDF'ye dışa aktarma
If you need a PDF version, simply call:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Tüm grup şekilleri ve SDT (metin alanı olarak render edilmiş) PDF'de görünecektir.

## Yaygın tuzaklar ve nasıl kaçınılır

| Semptom | Neden | Çözüm |
|---------|-------|-------|

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}