---
category: general
date: 2026-08-07
description: Aspose.Words kullanarak C#'de dikdörtgen şekli ekleyin ve şekli gizlemeyi,
  dolgu rengini ayarlamayı ve dikdörtgen şekli bir Word belgesine verimli bir şekilde
  eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: tr
lastmod: 2026-08-07
og_description: C# ile bir Word belgesine dikdörtgen şekli ekleyin. Şekli gizlemeyi,
  dolgu rengini ayarlamayı ve Aspose.Words kullanarak dikdörtgen şekli eklemeyi öğrenin.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: C#'ta dikdörtgen şekli ekleme – eksiksiz Aspose.Words öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Aspose.Words ile C#'ta Dikdörtgen Şekli Ekleme – Adım Adım Rehber
url: /tr/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Aspose.Words kullanarak dikdörtgen şekli ekleme – adım adım rehber

Bir Word belgesine **dikdörtgen şekli eklemeniz** gerektiğinde, bu rehber tam olarak nasıl yapılacağını gösterir. Dolgu rengini nasıl ayarlayacağınızı, şekli son düzenlemede görünmemesi için nasıl gizleyeceğinizi ve dosyayı nasıl kaydedeceğinizi sadece birkaç satır kodla öğreneceksiniz.

Aşağıdaki bölümlerde ihtiyacınız olan her şeyi ele alıyoruz: ön koşullar, tam kod listesi, her adımın açıklamaları ve şekli tekrar görünür hâle getirme ya da farklı bir renk kullanma gibi yaygın varyasyonlar için ipuçları. Sonunda **dikdörtgen şekli** ekleyebileceksiniz.

## Ön Koşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* **Aspose.Words for .NET** (sürüm 23.10 veya daha yeni). NuGet üzerinden kurabilirsiniz:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK veya daha yeni bir sürüm.
* C# ve Visual Studio (veya tercih ettiğiniz herhangi bir IDE) hakkında temel bilgi.

Ek bir kütüphane gerekmez – şekil‑ile ilgili API’ler Aspose.Words paketinin çekirdeğinde yer alır.

## Aspose.Words ile dikdörtgen şekli ekleme

Çözümün çekirdeği, boş bir belge oluşturup içine bir dikdörtgen ekleyen, rengini ayarlayan, gizleyen ve ardından dosyayı kaydeden kısa, bağımsız bir programdır. Aşağıda, her satırın *neden* yapıldığını açıklayan satır içi yorumlarla birlikte tam kaynak kodu yer alıyor.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Her adım ne işe yarar

| Adım | Nedeni |
|------|--------|
| **Yeni bir belge oluştur** | Temiz bir tuval sağlar; `new Document(path)` ile mevcut bir .docx dosyasını da yükleyebilirsiniz. |
| **DocumentBuilder başlat** | `DocumentBuilder`, düşük seviyeli düğüm ağaçlarıyla uğraşmadan metin, tablo ve şekil eklemenizi sağlayan yüksek seviyeli bir yardımcıdır. |
| **Dikdörtgen şekli ekle** | `InsertShape` metodu, daha sonra özelleştirilebilecek bir `Shape` nesnesi döndürür (boyut, konum, kenarlık vb.). |
| **Dolgu rengini ayarla** | `FillColor` özelliği iç renk kontrol eder; istediğiniz herhangi bir `Color` değerini kullanabilirsiniz (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)` vb.). |
| **Şekli gizle** | `Hidden = true` Word’e şekli yerleşim sırasında yok saymasını söyler, ancak belge XML’inde kalır. Bu, görünmez nesneleri saklamanın standart yoludur. |
| **Belgeyi kaydet** | Değişiklikleri bir .docx dosyasına yazar. Kaydedilen dosya gizli dikdörtgen şekli içerir. |

## Bir şeklin dolgu rengini nasıl ayarlarsınız

Dolgu rengini değiştirmek, `FillColor` özelliğine bir `System.Drawing.Color` atamaktan ibarettir. Özel bir ton istiyorsanız `Color.FromArgb` kullanın:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Neden önemli*: Dolgu rengi şeklin XML’inde (`<w:fill>` özniteliği) saklanır. Şekil gizli olsa bile renk hâlâ vardır; bu, renk kodlarına göre meta veri çıkarma gibi sonraki işlemler için faydalı olabilir.

## Şekli son belgede nasıl gizlersiniz

`Hidden` bayrağı, `Shape` sınıfındaki bir boolean özelliktir. `true` olarak ayarlandığında şekil Word yerleşim motoru tarafından yok sayılır.

```csharp
rectangleShape.Hidden = true;
```

**Yaygın tuzaklar**

* **Hidden vs. Visible** – Şeklin daha sonra görünür olması gerekiyorsa sadece `Hidden = false` yapın.
* **Uyumluluk** – Word’ün eski sürümleri (2007 öncesi) gizli çizim nesnelerini farklı işleyebilir. Aspose.Words, bayrağı uygun OOXML öğesinde tutarak uyumluluğu sağlar.

## Şekli programatik olarak nasıl eklersiniz

Örnekte bir dikdörtgen kullanılmış olsa da aynı `InsertShape` metodu birçok başka şekil için de çalışır (elips, üçgen, çizgi vb.). İlk parametre bir `ShapeType` enum değeridir:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**İpucu**: Şekli sayfanın belirli bir konumuna yerleştirmeniz gerekiyorsa, `InsertShape` çağırmadan önce `builder.MoveTo` ile ekleme noktasını ayarlayın.

## Mevcut bir belgeye dikdörtgen şekli ekleme

Genellikle bir şablonu baştan oluşturmak yerine geliştireceksiniz. 1. adımı aşağıdaki kodla değiştirin:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Sonraki adımlar aynı kalır ve dikdörtgen, builder’ın imlecinin bulunduğu yere (varsayılan olarak belgenin sonuna) eklenir.

## Kenar durumları ve varyasyonlar

### 1. Şekli tekrar görünür hâle getirme

İş akışınızın ilerleyen bir aşamasında gizli dikdörtgeni ortaya çıkarmak isterseniz bayrağı şu şekilde değiştirin:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Kenarlık (çizgi) ekleme

Gizli bir şekil, gösterildiğinde hâlâ görünür bir kenarlığa sahip olabilir. `LineColor` ve `LineWidth` özelliklerini ayarlayın:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Dikdörtgeni mutlak konumlandırma

Kesin yerleşim kontrolü için şeklin `WrapType` özelliğini `WrapType.Inline` (varsayılan) ya da `WrapType.TopBottom` olarak değiştirin ve `Left`/`Top` değerlerini ayarlayın:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Farklı ölçü birimi kullanma

Aspose.Words puan (point) cinsinden çalışır (1 pt = 1/72 inç). Santimetre tercih ediyorsanız önce dönüştürün:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Tam çalıştırılabilir örnek

Aşağıda, kopyalayıp yapıştırıp çalıştırabileceğiniz *tam* program yer alıyor. Gerekli tüm `using` yönergelerini içerir ve ortamınıza göre ayarlamanız gereken mutlak yolları gösterir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Beklenen sonuç**: `HiddenRectangleShape.docx` dosyasını Microsoft Word’de açtığınızda *görünür bir şekil* yoktur, ancak gizli dikdörtgen belge XML’inde bulunur. .docx’i zip arşivi olarak açıp `word/document.xml` içinde `w:fill="yellow"` ve `w:hidden="true"` özniteliklerine sahip bir `<w:shape>` öğesi arayarak varlığını doğrulayabilirsiniz.

## Sonuç

Artık C# ve Aspose.Words kullanarak bir Word belgesine **dikdörtgen şekli eklemeyi**, **dolgu rengini ayarlamayı** ve **şekli gizleyerek son düzenlemede görünmez hâle getirmeyi** biliyorsunuz. Aynı desen diğer şekil tipleri, özel renkler ve mevcut şablonlar için de geçerlidir. Kenarlıklar, mutlak konumlandırma ve farklı ölçü birimleriyle deney yaparak şekli tam gereksinimlerinize göre özelleştirin.

### Sonraki adımlar

* **Şekli tablo içinde veya başlık/footer içinde** ekleyerek su işareti (watermark) oluşturma.
* **Dikdörtgen ekleme** işlemini içerik denetimleriyle birleştirerek dinamik yer tutucular yaratma.
* Aspose.Words’ün **şekil manipülasyonu** API’sini inceleyerek döndürme, degrade dolgu ve SVG içe aktarma gibi gelişmiş özellikleri keşfetme.

Kodu kendi projenize uyarlamaktan çekinmeyin ve yorumlarda bir sonraki şekil‑ile ilgili sorununuzu bizimle paylaşın!

## Bir sonraki öğrenmeniz gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayalı olarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımları keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}