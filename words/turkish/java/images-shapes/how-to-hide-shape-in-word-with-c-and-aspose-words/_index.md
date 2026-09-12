---
category: general
date: 2026-09-11
description: C# kullanarak Word’de şekli nasıl gizleyeceğinizi öğrenin. Bu kılavuz
  ayrıca bir dikdörtgen şekli nasıl ekleyeceğinizi ve Aspose.Words ile Word belgesine
  şekil eklemeyi gösterir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: tr
lastmod: 2026-09-11
og_description: C# ve Aspose.Words kullanarak Word'de şekli nasıl gizlersiniz. Dikdörtgen
  şekli eklemek ve bir Word belgesindeki şekilleri yönetmek için adım adım öğreticiyi
  izleyin.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Word'de şekli gizleme – tam C# rehberi
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: C# ve Aspose.Words ile Word’de şekli gizleme
url: /tr/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Şekli Gizleme C# ve Aspose.Words ile

Word'de bir şekli belge yapısında tutarken gizlemeniz gerekiyorsa, bu eğitim tam olarak nasıl yapılacağını gösterir. Aspose.Words for .NET kullanarak bir dikdörtgen şekli ekleyebilir, gizleyebilir ve konumunu daha sonraki işlemler için koruyabilirsiniz.

Word otomasyonu genellikle şekiller üzerinde ayrıntılı kontrol gerektirir—şablonlar oluşturuyor, raporlar hazırlıyor veya bir belge‑düzenleme hizmeti inşa ediyor olsanız da. Bu rehberin sonunda şunları yapabilecek duruma geleceksiniz:

* Bir Word belgesine dikdörtgen şekli ekleyin (`insert rectangle shape`).
* Şekli silmeden gizleyin (`how to hide shape in word`).
* Sonucu kaydedin ve gizli şeklin render edilen görünümde görünmediğini doğrulayın (`insert shape into word document`).

Örnek, Aspose.Words 24.10 veya daha yeni sürümlerle çalışır ve .NET 6.0+ hedef alır, ancak kavramlar daha eski sürümlere de uygulanabilir.

## Önkoşullar

* **Aspose.Words for .NET** ≥ 24.10. Aspose web sitesinden ücretsiz geçici bir lisans alabilirsiniz.
* **.NET SDK** 6.0 veya daha yeni bir sürüm makinenizde kurulu.
* Visual Studio 2022, VS Code veya Rider gibi bir geliştirme ortamı.
* C# ve Word Open XML kavramına temel aşinalık (isteğe bağlı ancak faydalı).

## Aspose.Words ile Word'de Şekli Gizleme

Aşağıda, bir belge oluşturulmasından dikdörtgen şeklinin eklenmesine ve son olarak gizlenmesine kadar tüm iş akışını gösteren eksiksiz, çalıştırılabilir bir program bulunmaktadır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Her adımın açıklaması

1. **Yeni bir belge oluşturun** – `Document`, bellek içindeki Word dosyasını temsil eder. `DocumentBuilder`, içerik eklemek için akıcı bir API sağlar.
2. **Dikdörtgen şekli ekleyin** – `InsertShape`, `Rectangle` tipinde bir çizim nesnesi oluşturur. Boyutlar puan cinsinden ifade edilir (1 pt ≈ 1/72 in). Bu, `insert rectangle shape` gereksinimini karşılar.
3. **Şekli gizleyin** – `Shape.Hidden = true` ayarı, şekli Word işaretlemesinde (`<w:hidden/>`) gizli olarak işaretler. Şekil belge ağacının bir parçası olarak kalır, böylece daha sonra gizini kaldırabilir veya programmatically referans alabilirsiniz. Bu, `how to hide shape in word` konusunun özüdür.
4. **Dosyayı kaydedin** – Belge `output.docx` dosyasına yazılır. Microsoft Word'de açıldığında dikdörtgen görünmez, ancak XML içinde hâlâ vardır ve bir ZIP görüntüleyici veya Open XML SDK ile incelenebilir.

### Beklenen sonuç

Microsoft Word'de `output.docx` dosyasını açın:

* Belge boş görünür—görünür bir şekil yok.
* Altındaki XML'i (`word/document.xml`) incelerseniz, `<w:hidden/>` özniteliğine sahip bir `<w:pict>` öğesi bulursunuz; bu, şeklin mevcut ancak gizli olduğunu doğrular.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

Gizli şekil, `Hidden = false` olarak ayarlanıp belge yeniden kaydedildiğinde tekrar görünür hâle getirilebilir.

## Word Belgesine Dikdörtgen Şekli Ekleme

Ana hedef bir şekli gizlemek olsa da, birçok senaryo önce bir şekil ekleyerek başlar. `InsertShape` yöntemi, `Rectangle`, `Ellipse`, `Line` ve özel görüntüler gibi birçok `ShapeType` değerini destekler.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Neden dikdörtgen kullanılır?**  
Dikdörtgen, metin, görüntü veya diğer iç içe şekilleri tutabilen temiz, eksen‑hizalı bir kapsayıcı sağlar. Genellikle tablolar veya grafikler gibi dinamik içerikler için yer tutucu olarak kullanılır. Dikdörtgeni önce ekleyerek, daha sonra gizleseniz bile düzen tutarlılığını korursunuz.

## Word Belgesine Şekil Ekleme – En İyi Uygulamalar

`insert shape into word document` işlemini yaparken aşağıdakileri göz önünde bulundurun:

* **Açık boyutlar belirleyin** – Otomatik boyutlandırmaya güvenmeyin; genişlik ve yüksekliği puan cinsinden belirterek platformlar arasında tutarlı bir düzen sağlayın.
* **Konumlandırmayı tanımlayın** – Varsayılan olarak şekil mevcut paragrafın üzerine bağlanır. Kesin konumlandırma için `builder.MoveTo` veya `builder.StartBookmark` kullanın.
* **Stili erken uygulayın** – Dolgu rengi, çizgi stili ve metin kaydırma son görünümü etkiler. Gizli şekiller bile işaretleme değişmediği için uygun stil uygulamasından fayda sağlar.
* **Sürüm uyumluluğu** – `Hidden` özelliği yalnızca Aspose.Words 24.10 ve sonrası sürümlerde mevcuttur. Daha eski bir sürüm hedefliyorsanız, `Node` API'si ile `<w:hidden/>` özniteliğini manuel olarak ekleyebilirsiniz.

### Gizli özniteliği manuel ekleme (yedek çözüm)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Tam uçtan uca örnek

Her şeyi bir araya getirerek, aşağıda tek bir program bulunmaktadır:

1. Bir dikdörtgen şekli ekler.
2. Şekli gizler.
3. Kontrast oluşturmak için görünür bir elips ekler.
4. Belgeyi kaydeder.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

Programı çalıştırdığınızda `demo_output.docx` oluşturulur. Açıldığında sadece mercan elipsi göreceksiniz; yeşil dikdörtgen XML içinde mevcut ancak görünümden gizlidir.

## Yaygın sorular ve uç durumlar

**S: Bir şekli gizlemek sayfalama üzerinde etkili olur mu?**  
**C: Hayır. Gizli şekiller yerleşim motoru tarafından yok sayılır, bu yüzden alan tüketmezler. Bu, sayfa sonlarını etkilememesi gereken yer tutucu içerik için faydalıdır.**

**S: Başlık veya altbilgi içinde bulunan bir şekli gizleyebilir miyim?**  
**C: Evet. Aynı `Hidden` özelliği, başlıklar, altbilgiler ve hatta tablolar içinde dahil olmak üzere belge ağacının herhangi bir yerindeki şekillerde çalışır.**

**S: Aynı anda birden fazla şekli gizlemem gerekirse?**  
**C: `Document.GetChildNodes(NodeType.Shape, true)` koleksiyonunda döngü yaparak hedef her şekil için `Hidden = true` ayarlayın.**

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**S: PDF'ye dönüştürürken gizli öznitelik korunur mu?**  
**C: PDF'ye dönüştürürken gizli şekiller varsayılan olarak atlanır, bu da Word'ün render davranışıyla eşleşir. PDF'de görünmelerini istiyorsanız, dönüştürmeden önce gizliliğini kaldırmanız gerekir.

## İpuçları ve tuzaklar

* **Pro ipucu:** Şekli daha sonra çevre metni etkilemeden gizini kaldırmayı planlıyorsanız, gizlemeden önce `shape.WrapType = WrapType.None` ayarlayın.
* **Eski Aspose.Words sürümlerine dikkat edin:** `Hidden` özelliği 24.10 öncesinde `NotSupportedException` fırlatır. Bu durumda manuel XML yaklaşımını kullanın.
* **Test:** Oluşturulan `.docx` dosyasını her zaman Word'de açın ve “Show XML markup” (Geliştirici sekmesi) seçeneğini kullanarak `<w:hidden/>` özniteliğinin mevcut olduğunu doğrulayın.

## Sonuç

Artık C# ve Aspose.Words kullanarak Word'de şekli nasıl gizleyeceğinizi, ayrıca dikdörtgen şekli eklemeyi ve şekli Word belgesine eklemeyi görünürlük üzerinde tam kontrol sağlayarak nasıl yapacağınızı biliyorsunuz. `Hidden` özelliğini kullanarak şekilleri belge modelinde tutabilir, daha sonraki işlemler için saklayabilir ve son kullanıcılara temiz bir görünüm sunabilirsiniz.

Sonraki adımda, **çalışma zamanında şekil özelliklerini güncelleme**, **gizli şekilleri görüntülere dönüştürme** veya **gizli öğeleri doğrudan manipüle etmek için Open XML SDK kullanma** gibi ilgili konuları keşfedin. Bu uzantılar derinleştirecek

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki eğitimler, bu rehberde gösterilen teknikler üzerine inşa edilen yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}