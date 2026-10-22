---
category: general
date: 2026-09-05
description: Aspose.Words kullanarak bir Word belgesine dikdörtgen şekli oluşturun,
  ardından daha zengin düzenler için Word'de elips eklemeyi ve şekilleri gruplamayı
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: tr
lastmod: 2026-09-05
og_description: Aspose.Words ile bir Word belgesine dikdörtgen şekli oluşturun, ardından
  karmaşık düzenler için Word’de elips eklemeyi ve şekilleri gruplamayı görün.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Word'de dikdörtgen şekli oluşturma ve şekilleri gruplama – Aspose.Words
  rehberi
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words ile Word'de dikdörtgen şekil oluşturma ve şekilleri gruplama
url: /tr/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Aspose.Words ile dikdörtgen şekli oluşturma ve şekilleri gruplama

Bir Word belgesinde **dikdörtgen şekli oluşturmanız** gerekiyorsa, bu rehber Aspose.Words for .NET ile tam adımları gösterir. Ayrıca kelime elipsi eklemeyi, Word'de şekilleri gruplamayı ve sonucu bir DOCX dosyası olarak kaydetmeyi göreceksiniz. Çözüm, herhangi bir .NET 6+ projesinde çalışır ve sunucuda Microsoft Office yüklü olmasını gerektirmez.

Bu öğretici, proje kurulumundan yaygın düzen hatalarının ele alınmasına kadar her şeyi kapsar, böylece kodu kopyalayıp hemen çalıştırabilirsiniz.

## Önkoşullar

* .NET 6 SDK veya daha yeni bir sürüm yüklü  
* NuGet uyumlu bir IDE (Visual Studio, Rider veya VS Code)  
* Aspose.Words for .NET lisansı (veya geçici bir değerlendirme anahtarı)  
* C# ve Word belge yapısı hakkında temel bilgi  

Bu öğeler kodun derlenmesini ve şekillerin doğru şekilde render edilmesini sağlar.

## Adım 1: Projeyi kurun ve Aspose.Words ekleyin

Yeni bir konsol projesi oluşturun ve Aspose.Words paketini ekleyin:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Paket, bu öğreticide kullanılan `Document`, `DocumentBuilder`, `Shape` ve `GroupShape` sınıflarını sağlar.

## Adım 2: Boş bir belge ve bir builder başlatın

`Document` nesnesi tüm Word dosyasını temsil ederken, `DocumentBuilder` içerği programlı olarak eklemenizi sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Belgeyi önce oluşturmak, sonraki tüm şekil işlemlerinin geçerli bir kapsayıcıya sahip olmasını garanti eder.

## Adım 3: **Dikdörtgen şekli oluştur** ve boyutlarını ayarlayın

Dikdörtgen, metin veya görseller için en yaygın kapsayıcıdır. Boyutunu puan cinsinden tanımlarsınız (1 pt ≈ 1/72 inç).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Bu adımın önemi: `Shape` sınıfı geometriyi, doldurmayı ve çizgi özelliklerini kapsar. Eklemeden önce `Width` ve `Height` ayarlamak, şeklin beklenen boyutta görünmesini garanti eder.

## Adım 4: **Elips kelimesi ekleme** – bir elips şekli ekleyin

Elips, simgeler, işaretçiler veya dekoratif öğeler için kullanılabilir. Kod, sadece `ShapeType` değişen dikdörtgen oluşturmayı yansıtır.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

`FillColor` ve `Line.Color` özellikleri, dış görüntüler olmadan görünümü nasıl özelleştireceğinizi gösterir.

## Adım 5: **Word'de şekilleri gruplama** – dikdörtgen ve elipsi birleştirin

Gruplama, birden fazla şekli tek bir birim olarak taşımanıza, yeniden boyutlandırmanıza veya döndürmenize olanak tanır. Bu, birleşik bir grafik (ör. etiketli bir simge) gerektiğinde önemlidir.

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

`AppendChild` çağırdığınızda, orijinal şekiller ana belge akışından kaldırılır ve `GroupShape`'in çocuğu olur. Grup, tek bir şekil gibi davranır, bu da sonraki düzen ayarlamalarını basitleştirir.

## Adım 6: Belgeyi kaydedin

Son olarak, belgeyi diske yazın. Desteklenen herhangi bir formatı (`.docx`, `.pdf`, `.html`, vb.) seçebilirsiniz. Bu öğreticide yerel Word formatını koruyoruz.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Programı çalıştırdıktan sonra, *GroupShape.docx* dosyasını Microsoft Word'de açın. Belirttiğiniz koordinatlarda bir arada gruplanmış dikdörtgen ve elips göreceksiniz.

## Yaygın varyasyonlar ve kenar durumları

| Durum | Ne değiştirilmeli | Sebep |
|-----------|----------------|--------|
| **Farklı boyut birimleri** | `ConvertUtil.InchToPoint(2.5)` inç için, `ConvertUtil.MillimeterToPoint(30)` milimetre için kullanın. | Puan dışı ölçü birimleriyle çalışırken kodun okunabilirliğini korur. |
| **Dikdörtgenin içine metin ekleme** | `Paragraph` düğümü oluşturun, `Text` özelliğini ayarlayın ve `AppendChild` ile `rectangleShape`'e ekleyin. | Şekli ayrı metin kutuları olmadan etiketlemenizi sağlar. |
| **Grubu döndürme** | `groupShape.Rotation = 45;` (derece) olarak ayarlayın. | Diyagonal rozetler veya filigranlar oluşturmak için faydalıdır. |
| **PDF olarak kaydetme** | `doc.Save("GroupShape.pdf");` metodunu çağırın. | Aspose.Words PDF çıktısı için vektör şekilleri otomatik olarak rasterleştirir. |
| **Birden fazla grup** | Ek `GroupShape` örnekleri oluşturun ve ekleme/insert adımlarını tekrarlayın. | Birden fazla bağımsız birleşimle karmaşık sayfa düzenleri oluşturmanıza olanak tanır. |

### Pro ipucu

Şekilleri her zaman **gruplamadan önce** ekleyin. Zaten başka bir grubun parçası olan bir şekli gruplamaya çalışırsanız, Aspose.Words bir `ArgumentException` fırlatır. Grubu tek bir yöntemde oluşturmak bu çalışma zamanı hatasını önler.

### Dikkat edilmesi gerekenler

* **Koordinat sistemi** – `Left` ve `Top`, sayfanın sol ve üst kenar boşluklarından ölçülür, belge kenarından değil. Bunu yanlış anlamak şekilleri sayfa dışına yerleştirebilir.  
* **Lisanslama** – Geçerli bir lisans olmadan, kaydedilen belge “Aspose.Words for .NET Evaluation” yazan bir filigran içerir. Bunu önlemek için lisansınızı kodun başında uygulayın (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).

## Tam kaynak kodu (çalıştırılabilir)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Bu programı çalıştırmak, *GroupShape.docx* dosyasını açıklanan şekilde gruplanmış şekillerle üretir.

## Sonuç

Artık Aspose.Words kullanarak **dikdörtgen şekli oluşturmayı**, **elips kelimesi eklemeyi** ve **Word'de şekilleri gruplamayı** biliyorsunuz. Tam örnek, belgeyi başlatmadan son dosyayı kaydetmeye kadar tüm iş akışını gösterir; böylece şekil işleme yeteneğini herhangi bir otomatik raporlama veya belge‑oluşturma çözümüne entegre edebilirsiniz.

### Sıradaki adım?

* Daha karmaşık geometri için **aspose.words create shapes**'i keşfedin, örneğin `Polygon` veya `Freeform`.  
* Gruplanmış şekilleri **content controls** ile birleştirerek dinamik şablonlar oluşturun.  
* DOCX'i PDF veya HTML'ye dönüştürerek vektör şekillerinin farklı formatlarda nasıl render edildiğini görün.  

Farklı boyutlar, renkler ve dönüşlerle denemeler yapmaktan çekinmeyin. Şekil gruplamayı ustalaştığınızda, Word belgeleri içinde doğrudan karmaşık diyagramlar, rozetler ve özel UI öğeleri oluşturabilirsiniz.

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for .NET kullanarak Word belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET kullanarak Word belgelerine Şekil Ekleme](/words/english/net/working-with-shapes/insert-shape/)
- [C# kullanarak Word'de dikdörtgen şekli oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}