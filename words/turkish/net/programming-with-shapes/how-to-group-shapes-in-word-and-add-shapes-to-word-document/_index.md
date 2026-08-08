---
category: general
date: 2026-08-07
description: Aspose.Words ile Word’de şekilleri nasıl gruplandırılır ve C# kullanarak
  Word belgesine şekiller nasıl eklenir. Temiz, yeniden kullanılabilir kod için bu
  adım adım rehberi izleyin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: tr
lastmod: 2026-08-07
og_description: Aspose.Words for .NET kullanarak Word’de şekilleri nasıl gruplayabilirsiniz.
  Bu öğreticide, bir Word belgesine şekil eklemeyi, bunları gruplamayı ve dosyayı
  net C# kodu ile kaydetmeyi gösteriyoruz.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Word'de şekilleri gruplama – hızlı C# rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Word'de şekilleri gruplama ve Word belgesine şekil ekleme
url: /tr/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de şekilleri gruplama ve Word belgesine şekil ekleme

Eğer **Word'de şekilleri nasıl gruplandıracağınızı** öğrenmeniz gerekiyorsa, bu kılavuz Aspose.Words for .NET kullanarak tam süreci adım adım gösterir. Ayrıca **Word belgesine şekil ekleme**yi birkaç satır C# kodu ile öğreneceksiniz, böylece sonuç herhangi bir raporlama veya şablonlama senaryosu için hazır olur.

Bu öğretici ihtiyacınız olan her şeyi kapsar: gerekli NuGet paketleri, tam bir kaynak dosyası ve her adımın neden önemli olduğuna dair bir açıklama. Sonunda bir dikdörtgen ve bir elipsi tek bir grup şekli içinde birleştiren bir DOCX oluşturabilirsiniz.

## Önkoşullar

* .NET 6.0 SDK veya daha yeni bir sürüm yüklü  
* Visual Studio 2022 (veya .NET'i destekleyen herhangi bir IDE)  
* Aspose.Words for .NET NuGet paketi (`Aspose.Words`) – ücretsiz deneme sürümü test için çalışır, ancak bir lisans değerlendirme filigranlarını kaldırır  

Bu öğeler, **Word belgesine şekil ekleme** için tek dış bağımlılıklardır.

## Word'de şekilleri gruplama

Çözümün temeli, bireysel şekiller oluşturmak, bunları sayfaya yerleştirmek ve ardından bir `GroupShape` içinde sarmalamaktır. Aşağıdaki adımlar kodun mantıksal sırasını yansıtır.

### Adım 1: Bir belge ve bir builder oluşturma

Bir `Document` nesnesi, tüm DOCX dosyasını temsil eder. `DocumentBuilder`, belgeyi düzenlemek için kullanışlı bir API sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Neden önemli*: `Document`, tüm Word öğeleri için kapsayıcıdır. `DocumentBuilder`, mevcut imleç konumunu izler; bu, daha sonra gruplandırılmış şekli eklediğinizde gereklidir.

### Adım 2: Dikdörtgen şekli ekleme

Bir dikdörtgen, `ShapeType.Rectangle` belirterek oluşturulur. Genişlik, yükseklik ve konum, puan cinsinden ayarlanır (1 pt ≈ 1/72 in).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*Neden önemli*: `StrokeColor` ayarlandığında, belge açıldığında şekil görünür olur. Katı bir iç kısım gerekiyorsa, şekli `FillColor` ile de doldurabilirsiniz.

### Adım 3: Elips şekli ekleme

Elips, `ShapeType.Ellipse` kullanır. Boyutu ve konumu dikdörtgenden bağımsızdır, bu da grubun son düzenini kontrol etmenizi sağlar.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*Neden önemli*: Elipsi `Left = 120` konumuna yerleştirerek, dikdörtgenle çakışmaz ve grup görsel olarak ayırt edilebilir olur.

### Adım 4: İki şekli gruplama

`GroupShape`, çocuklarını tek bir nesne gibi davranan bir kapsayıcı görevi görür. Bu, **Word'de şekilleri nasıl gruplandırılır** için temel işlemdir.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*Neden önemli*: Gruplama, iki şekli birlikte taşımanıza, yeniden boyutlandırmanıza veya döndürmenize olanak tanır. `groupShape` üzerine uygulanan herhangi bir dönüşüm, çocuklarına da yayılır.

### Adım 5: Gruplandırılmış şekli belgeye ekleme

`DocumentBuilder.InsertNode`, `GroupShape`'i mevcut imleç konumuna yerleştirir. Builder'ı hareket ettirmediğimiz için grup, ilk sayfanın başında görünür.

```csharp
builder.InsertNode(groupShape);
```

*Neden önemli*: Düğümü doğrudan eklemek, ayrı bir paragraf veya tablo hücresi gerektirmeyi önler. Grup, belge akışının bir parçası haline gelir.

### Adım 6: Belgeyi kaydetme

Son olarak, DOCX dosyasını diske yazın. Uygulamanızın yazabileceği tam bir yol kullanın.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*Neden önemli*: `doc.Save`, tüm değişiklikleri sonlandırır. Oluşan dosya Microsoft Word, LibreOffice veya DOCX destekleyen herhangi bir görüntüleyicide açılabilir.

## Tam kaynak dosyası

Aşağıdaki kodu yeni bir konsol projesine (`dotnet new console`) kopyalayın ve çalıştırın. Program, gruplandırılmış bir dikdörtgen ve elips içeren `GroupShape.docx` adlı bir dosya oluşturur.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### Beklenen çıktı

`GroupShape.docx` dosyasını açın. Sol tarafta mavi bir dikdörtgen, sağ tarafta yeşil bir elips içeren tek bir görsel nesne göreceksiniz. Word'de nesneyi seçtiğinizde her iki şekil aynı anda vurgulanır—bu da **Word'de şekilleri nasıl gruplandırılır** işleminin başarılı olduğunu gösterir.

## Yaygın sorular ve uç durumlar

* **İki'den fazla şekil ekleyebilir miyim?**  
  Evet. Grubu eklemeden önce her ek `Shape` için `groupShape.AppendChild` çağırın.

* **Grubu döndürmem gerekirse ne yapmalıyım?**  
  Grup oluşturulduktan sonra `groupShape.RotationAngle = 45;` (açı derece cinsinden) ayarlayın.

* **`doc.UpdatePageLayout()` çağırmam gerekiyor mu?**  
  Bu senaryo için gerekmez. Düzen, belge kaydedildiğinde otomatik olarak güncellenir.

* **Lisanslama kodu nasıl etkiler?**  
  Geçerli bir Aspose.Words lisansı (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) ile oluşturulan belgede değerlendirme filigranı bulunmaz.

## Sonuç

Artık Aspose.Words for .NET kullanarak **Word'de şekilleri nasıl gruplandırılır** ve **Word belgesine şekil ekleme** konularını biliyorsunuz. Öğreticide bir belge oluşturma, bireysel şekilleri tanımlama, bunları gruplama, grubu ekleme ve dosyayı kaydetme adımları ele alındı.  

Buradan itibaren şunları deneyebilirsiniz:

* Gruba metin kutuları veya resimler ekleme  
* Dolgu renklerini, çizgi stillerini veya gölge efektlerini değiştirme  
* Şekilleri tabloların veya başlıkların içinde gruplama

Bu uzantılar, kodu temiz ve sürdürülebilir tutarak programlı bir şekilde gelişmiş Word şablonları oluşturmanıza olanak tanır. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalar içeren tam çalışan kod örnekleri sunar; böylece ek API özelliklerini öğrenebilir ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}