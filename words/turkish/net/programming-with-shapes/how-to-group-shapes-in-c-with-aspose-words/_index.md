---
category: general
date: 2026-08-23
description: Aspose.Words kullanarak C#’te şekilleri nasıl gruplayacağınızı öğrenin.
  Kılavuz ayrıca dikdörtgen şekli eklemeyi ve karmaşık belgeler için şekil eklemeyi
  de kapsar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: tr
lastmod: 2026-08-23
og_description: Aspose.Words ile C#’ta şekilleri nasıl gruplayabilirsiniz. Dikdörtgen
  şekli eklemek, kelimeye şekil eklemek ve birden fazla şekli verimli bir şekilde
  gruplamak için bu kapsamlı öğreticiyi izleyin.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: C#'de şekilleri gruplama – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: C#'ta Aspose.Words ile şekilleri nasıl gruplandırılır
url: /tr/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Aspose.Words'te şekilleri nasıl gruplayabilirsiniz

Eğer bir Word belgesinde programlı olarak **how to group shapes** yapmanız gerekiyorsa, bu eğitim Aspose.Words for .NET kullanarak tam adımları gösterir. Rapor oluşturucu, şablon motoru ya da diyagram aracı geliştiriyor olun, bir grup başlatmayı, bir dikdörtgen şekli eklemeyi ve kodunuzdan çıkmadan şekillere kelime‑seviyesi içerik eklemeyi öğreneceksiniz.

Ayrıca **group multiple shapes** nasıl bir araya getireceğinizi göreceksiniz; bu, nesneler koleksiyonunu tek bir varlık olarak taşıma, döndürme veya stil verme ihtiyacınız olduğunda çok önemlidir. Aşağıdaki örnek en yeni Aspose.Words 24.x sürümüyle çalışır ve yalnızca .NET 6 veya üzeri gerektirir.

## Gereksinimler

- .NET 6 SDK (veya Aspose.Words tarafından desteklenen herhangi bir .NET sürümü)
- Visual Studio 2022 veya VS Code
- Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`)
- C# ve Aspose.Words nesne modeli hakkında temel bilgi

> **Pro ipucu:** Test aşamasında filigran sınırlamalarından kaçınmak için Aspose'un ücretsiz değerlendirme lisansını kullanın.

## Aspose.Words ile şekilleri nasıl gruplayabilirsiniz

Aşağıda **how to start group** gösteren, bir dikdörtgen ekleyen ve grubu sonlandıran tam, çalıştırılabilir bir program bulunmaktadır. Kod, sağladığınız snippet ile aynı mantıksal akışı izler, ancak bağlam, hata yönetimi ve açıklamalar ekler.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Her adımın önemi

| Adım | Amaç | Anahtar kelimelerle ilişkisi |
|------|------|------------------------------|
| **Create a new blank document** | Şekil işlemleri için temiz bir tuval sağlar. | Daha sonra **add shapes word** için zemin hazırlar. |
| **Initialize DocumentBuilder** | Builder, nesneleri eklemek için birincil API'dir. | **how to start group** yapabilmek için gereklidir. |
| **StartGroupShape** | Mantıksal bir kapsayıcı başlatır; sonraki tüm şekiller bu grubun üyesi olur. | **how to start group** sorusuna doğrudan yanıt verir. |
| **InsertShape** (rectangle, ellipse, text) | Şekilleri grup içinde tek tek yerleştirir. Dikdörtgen çağrısı **insert rectangle shape**; metin şekli **add shapes word** anahtar kelimelerini karşılar. | **group multiple shapes** gösterir. |
| **EndGroupShape** | Grubu sonlandırır, böylece bir bütün olarak taşıyabilir veya stil verebilirsiniz. | **how to group shapes** iş akışını tamamlar. |

## Dikdörtgen şekli ekleme – derinlemesine

`InsertShape` yöntemi bir `ShapeType` enum, genişlik ve yükseklik alır. Özel stil ile **insert rectangle shape** yapmak için örneği şu şekilde genişletebilirsiniz:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Neden stil verilir?** Stil, grup daha sonra yeniden konumlandırıldığında dikdörtgenin öne çıkmasını sağlar. Ayrıca şekil özelliklerinin grup kapanmadan önce ayarlanabileceğini gösterir.

## Word‑seviyesi şekiller ekleme (add shapes word)

Bir şeklin içine doğrudan metin yerleştirmeniz gerekiyorsa—genellikle “WordArt” ya da “metin kutusu” olarak adlandırılır—`ShapeType.TextPlainText` kullanın. Ekledikten sonra şekle `DocumentBuilder.Writeln` ile ya da şeklin `TextBox` özelliğine erişerek metin yazabilirsiniz:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

Bu, **add shapes word** anahtar kelimesini karşılar ve metnin grup ile birlikte taşınabileceğini gösterir.

## Birden fazla şekli gruplama – pratik senaryolar

**group multiple shapes** yaptığınızda, konumlandırma, döndürme veya ölçekleme gibi işlemleri tek bir nesne gibi ele alabilirsiniz. Örneğin, grup kapatıldıktan sonra tüm grubu şu şekilde taşıyabilirsiniz:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Veya grubu döndürün:

```csharp
group.Rotation = 45; // degrees
```

Bu işlemler, şekillerin aynı üst grup içinde olmasından dolayı mümkündür.

## Kenar durumlarını ele alma

1. **Nested groups** – Aspose.Words, grup içinde grup oluşturmanıza izin verir. İç grup için `EndGroupShape` çağırmadan önce tekrar `StartGroupShape` çağırarak iç içe bir grup oluşturabilirsiniz.  
2. **Empty groups** – Bir grup başlatıp hiç şekil eklemezseniz, `EndGroupShape` hâlâ boş bir kapsayıcı oluşturur. Bu zararsızdır ancak dosya boyutunu biraz artırabilir.  
3. **Compatibility** – Oluşturulan DOCX, Word 2010 ve sonrası ile çalışır. Daha eski sürümler grup meta verilerini göz ardı edebilir; bu yüzden hedef Word sürümüyle her zaman test edin.

## Referans için tam kaynak dosyası

Aşağıdakileri bir .NET konsol projesinde `Program.cs` olarak kaydedin. Kod, değişiklik yapmadan derlenir ve çalıştırılır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Beklenen çıktı

`GroupedShapes.docx` dosyasını Microsoft Word'de açtığınızda şunlar görülür:

- Açık‑koral bir dikdörtgen, bir elips ve bir metin kutusu—hepsi görsel olarak bir arada bağlanmıştır.  
- Grubun herhangi bir parçasını seçmek, tüm grubu (tek bir sınırlama kutusu görünür) seçer.  
- Grubu taşıma veya döndürme, üç şekli de birlikte hareket ettirir.

## Sıkça sorulan sorular

**S: Belgede zaten var olan şekilleri gruplayabilir miyim?**  
C: Evet. Mevcut `Shape` nesnelerini alın, `builder.StartGroupShape()` çağırın, `builder.InsertShape(existingShape)` ile yeniden ekleyin ve ardından `EndGroupShape()` çağırın.

**S: Grup oluşturma, altındaki XML'i etkiler mi?**  
C: Aspose.Words, her şeklin `<w:sp>` düğümünü içeren bir `<w:grpSp>` elementi ekler. Bu, Office Open XML spesifikasyonuna tamamen uygundur.

**S: Daha sonra grubu çözmek (ungroup) istersem ne yapmalıyım?**  
C: Doğrudan bir “ungroup” API'si yoktur, ancak grup içindeki alt şekilleri (`group.GroupShape.Children`) dolaşarak belge gövdesine kopyalayabilirsiniz.

## Sonraki adımlar

Artık **how to group shapes** bildiğinize göre, aşağıdaki ilgili konuları keşfetmeyi düşünün:

- **Apply complex formatting to grouped shapes** – degrade dolgu, gölge efektleri ve çizgi stillerini nasıl ayarlayacağınızı öğrenin.  
- **Export grouped shapes as images** – bir grubu rasterleştirmek için `Shape.GetShapeRenderer().Save(...)` kullanın.  
- **Create dynamic diagrams** – veri‑tabanlı konumlandırmayı grup oluşturmayla birleştirerek akış şemalarını otomatik oluşturun.

Bu konular, burada ele alınan temelin üzerine inşa edilir ve daha zengin, etkileşimli Word belgeleri oluşturmanıza yardımcı olur.

---

*Kodlamanın tadını çıkarın! Bu kılavuzu faydalı bulduysanız, ekip arkadaşlarınızla paylaşın veya örnek projeyi barındıran depoyu yıldızlayın.*

## Bir sonraki öğrenmeniz gerekenler

Aşağıdaki eğitimler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}