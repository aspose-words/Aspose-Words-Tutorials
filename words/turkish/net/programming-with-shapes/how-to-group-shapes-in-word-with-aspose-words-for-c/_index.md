---
category: general
date: 2026-09-21
description: Aspose.Words for C# kullanarak Word'de şekilleri nasıl gruplayacağınızı
  öğrenin. Bu adım adım kılavuz, grup şekilleri oluşturmayı, konumlandırmayı ve kaydetmeyi
  kapsar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: tr
lastmod: 2026-09-21
og_description: Aspose.Words for C# kullanarak Word’de şekilleri gruplayın. Bu kısa
  öğreticide, gruplanmış şekilleri programlı olarak oluşturmayı, konumlandırmayı ve
  kaydetmeyi öğrenin.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Aspose.Words ile Word’de Şekilleri Gruplama – Tam C# Kılavuzu
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words for C# ile Word'de şekilleri nasıl gruplayabilirsiniz
url: /tr/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Aspose.Words for C# ile Şekilleri Nasıl Gruplandırılır

Word'de **şekilleri programlı olarak gruplandırmanız** gerekiyorsa, Aspose.Words bunu oldukça basit hale getirir. Bu öğreticide iki dikdörtgen şekil oluşturmayı, yan yana yerleştirmeyi, bunları bir `GroupShape` içine birleştirmeyi ve sonucu bir DOCX dosyası olarak kaydetmeyi gösteriyoruz.

Tam bir çalıştırılabilir örnek, her adımın neden önemli olduğuna dair açıklamalar ve üst üste binen şekiller ya da dinamik boyutlandırma gibi yaygın kenar durumlarını ele almanız için ipuçları göreceksiniz. Bu rehberin sonunda şekil gruplandırmayı herhangi bir Word otomasyon projesine entegre edebilirsiniz.

## Önkoşullar

* .NET 6.0 (veya daha yeni) yüklü olmalı – Aspose.Words .NET Standard 2.0+, .NET Core ve .NET Framework'ü destekler.
* Geçerli bir Aspose.Words for .NET lisansı (veya geçici değerlendirme anahtarı) – kütüphane lisanssız çalışır ancak filigran ekler.
* Visual Studio 2022 (veya herhangi bir C# IDE) örnek kodu derlemek ve çalıştırmak için.

`Aspose.Words` dışındaki ek NuGet paketlerine ihtiyaç yok.

## Aspose.Words Kullanarak Word'de Şekilleri Nasıl Gruplandırılır

Çözümün çekirdeği, bireysel şekiller için bir kapsayıcı görevi gören **`GroupShape`** nesnesidir. Aşağıda süreci net adımlara ayırıyoruz.

### Adım 1: Boş bir belge ve bir `DocumentBuilder` oluşturun

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Bu adım neden?*  
`Document`, tüm DOCX dosyasını temsil ederken, `DocumentBuilder` akıcı metodlar (ör. `InsertShape`) sağlar ve yeni öğeleri mevcut imleç konumuna otomatik olarak ekler.

### Adım 2: İlk dikdörtgen şekli ekleyin

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

`InsertShape` çağrısı şekli belgeye ekler ve daha fazla yapılandırabileceğiniz bir `Shape` nesnesi döndürür (renk, kenarlık vb.). Boyut, puan cinsinden ifade edilir (1 pt ≈ 1/72 in).

### Adım 3: İkinci dikdörtgeni ekleyin ve konumunu ayarlayın

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

`Left` ayarı, şekli sayfa kenar boşluğuna göre konumlandırır. Üst üste binmeyi önlemek için ofset, ilk şeklin genişliğinden (100 pt) büyük olmalıdır; küçük bir boşluk bırakmak için 120 pt kullanıyoruz.

### Adım 4: İki dikdörtgeni kapsayacak kadar büyük bir `GroupShape` oluşturun

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape`, sahip `Document` ve kapsayıcı boyutlarını alır. Kapsayıcının genişliği, en uzak şeklin sağ kenarını aşmalıdır; aksi takdirde ikinci şekil kesilir.

### Adım 5: Bireysel şekilleri gruba ekleyin

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

Eklemek, şekilleri grubun iç koleksiyonuna taşır. Bu çağrıdan sonra şekiller belge ağacında bağımsız nesneler olmaz; gruba ait olurlar.

### Adım 6: Gruplanmış şekli belgeye geri ekleyin

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode`, tüm `GroupShape`'i imlecin şu an bulunduğu konuma yerleştirir. Grubu belirli bir paragrafta istiyorsanız, önce builder'ı o paragrafın konumuna taşıyın.

### Adım 7: Belgeyi kaydedin

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

Ortaya çıkan dosya, tek bir nesne gibi davranan iki dikdörtgen içerir—Microsoft Word'de bunları birlikte taşıyabilir, yeniden boyutlandırabilir veya silebilirsiniz.

## Tam kaynak kodu

Tüm adımları birleştirerek bağımsız bir program elde edersiniz:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Beklenen çıktı:** Microsoft Word'de *GroupedShapes.docx* dosyasını açtığınızda yan yana iki dikdörtgen görürsünüz; bunlar tek bir seçilebilir nesne olarak kabul edilir. Grubu sürüklemek, iki dikdörtgeni birlikte hareket ettirir.

## Yaygın varyasyonlar ve kenar durumları

| Durum | Önerilen ayar |
|-----------|------------------------|
| **İkiden fazla şekil** | Ek `Shape` nesneleri oluşturun, uygun şekilde konumlandırın ve her birini aynı `GroupShape` içine ekleyin. |
| **Dinamik boyut** | Grup genişliğini/yüksekliğini, alt şekillerin maksimum `Right` ve `Bottom` değerlerine göre hesaplayın. |
| **Farklı şekil türleri** | `ShapeType.Ellipse`, `ShapeType.Triangle` vb. aynı şekilde eklenebilir; grup kapsayıcısı türle ilgilenmez. |
| **Döndürülmüş şekiller** | Eklenmeden önce `shape.Rotation = 45;` ayarlayın; döndürme grup içinde korunur. |
| **PDF olarak kaydetme** | `doc.Save("GroupedShapes.pdf");` çağrısını yapın – grup PDF render'ında korunur. |

**Pro ipucu:** Gruplandırmadan sonra, `group.GetChildNodes(NodeType.Shape, true)` ile bireysel şekilleri hâlâ değiştirebilirsiniz. Bu, grubu bozmadan bir dikdörtgenin dolgu rengini değiştirmeniz gerektiğinde kullanışlıdır.

## Gruplandırmayı Programlı Olarak Nasıl Doğrularsınız

Şekillerin doğru şekilde gruplandığını (ör. birim testlerinde) doğrulamanız gerekiyorsa, belge düğüm hiyerarşisini inceleyin:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

Çıktı şu şekilde olmalıdır:

```
Number of groups: 1
Children in first group: 2
```

Bu, **Word'de grup şekillerinin** beklendiği gibi oluşturulduğunu doğrular.

## Sonuç

Artık Aspose.Words for C# ile **Word'de şekilleri gruplandırmanın** nasıl yapılacağını biliyorsunuz. Süreç, bireysel şekiller oluşturmayı, konumlandırmayı, bunları bir `GroupShape` içinde sarmayı ve grubu belgeye geri eklemeyi içerir. Yukarıdaki tam örnekle bu tekniği istediğiniz sayıda şekle, farklı tiplere ya da hatta metin kutuları ve görüntülerle birleştirebilirsiniz.

Sonraki adımda, **Aspose.Words şekil gruplandırma**, **C# Word şekil manipülasyonu** ve **DocumentBuilder insert shape** gibi ilgili konuları keşfederek daha gelişmiş belge otomasyon senaryolarına göz atın. Dinamik boyutlandırma, koşullu gruplandırma ve PDF'ye dışa aktarma deneyerek Aspose.Words'un gücünden tam anlamıyla yararlanın.

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for .NET Kullanarak Word Belgelerine Şekil Ekleme](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words ile Word'de Dikdörtgen Şekil Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Şekil Gölge Öğreticisi – C#'ta Word Şekline Gölge Ekleme](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}