---
category: general
date: 2026-11-18
description: C# ile bir Word belgesinde dikdörtgen şekli oluşturmayı öğrenin. Kılavuz
  ayrıca şekil boyutunu ayarlamayı, şekil konumunu ayarlamayı ve Word’de şekilleri
  gruplayıp birleştirmeyi kapsar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: tr
lastmod: 2026-11-18
og_description: C# kullanarak bir Word dosyasında dikdörtgen şekil oluşturun ve şekil
  boyutlarını ayarlamayı, şekil konumunu belirlemeyi ve Word’de şekilleri gruplamayı
  öğrenin.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: C# ile Word'de dikdörtgen şekil oluştur ve şekilleri grupla
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C# kullanarak Word'de dikdörtgen şekli oluşturma ve şekilleri gruplama
url: /tr/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de C# kullanarak dikdörtgen şekli oluşturma ve şekilleri gruplama

Bir Word belgesinde **dikdörtgen şekli oluşturmanız** gerekiyorsa, bu öğretici size tam, çalıştırmaya hazır bir çözüm gösterir. Şekil boyutunu nasıl ayarlayacağınızı, şekil konumunu nasıl belirleyeceğinizi ve şekilleri Word'de tek bir nesne gibi davranacak şekilde nasıl gruplayacağınızı göreceksiniz.

Şekillerle çalışmak, raporlar, faturalar veya diyagramlar programlı olarak oluşturulurken yaygın bir gereksinimdir. Bu kılavuzun sonunda, Aspose.Words for .NET ile oluşturulmuş bir dikdörtgen, bir elips ve gruplanmış bir konteyner içeren bir `.docx` dosyası üretebileceksiniz.

## Önkoşullar

- .NET 6.0 SDK veya daha yenisi (kod .NET Framework 4.7+ ile de çalışır)
- Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`)
- Bir kod editörü veya IDE (Visual Studio, VS Code, Rider, vb.)

Ek bir kütüphane gerekmemektedir.

## Word'de dikdörtgen şekli oluşturma ve şekilleri gruplama

Temel adımlar şunlardır:

1. **Boş bir belge** ve bir `DocumentBuilder` oluşturun.
2. Bireysel şekilleri tutacak bir `GroupShape` **ekleyin**.
3. Bir dikdörtgen şekli **oluşturun**, boyutlarını ayarlayın ve gruba ekleyin.
4. Bir elips şekli **oluşturun**, boyut ve konumunu ayarlayın ve gruba ekleyin.
5. Belgeyi **kaydedin**.

Her adım aşağıda açıklanmıştır ve tam kaynak kodu açıklamadan sonra gelmektedir.

### Adım 1: Belgeyi ve builder'ı başlatma

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document`, tüm Word dosyasını temsil ederken `DocumentBuilder`, içerik eklemek için akıcı bir API sağlar. Şekil ekleyebilmeniz için bunları başlatmak zorunludur.

### Adım 2: Grup şekli ekleme

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

`GroupShape`, bir konteyner gibi çalışır; tüm alt şekiller birlikte hareket eder. Bu, toplu dönüşümler (ör. taşıma, döndürme veya silme) gerektiğinde **Word'de şekilleri gruplamanın** önerilen yoludur.

### Adım 3: Dikdörtgeni oluşturma ve boyutunu ayarlama

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Burada `Width` ve `Height` atayarak **dikdörtgen şekli oluşturuyor** ve **şekil boyutunu ayarlıyoruz**. Aspose.Words'ta boyutlar puan cinsinden ifade edilir (1 pt ≈ 1/72 in). Boyutları açıkça ayarlamak, dikdörtgenin tam olarak istenildiği gibi görünmesini sağlar.

### Adım 4: Elipsi oluşturma, boyutlarını ayarlama ve konumlandırma

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

Elips için **şekil boyutlarını ayarlama** genişlik ve yükseklik açısından aynıdır ve mükemmel bir daire oluşturur. `Left` özelliği **şekil konumunu ayarlamayı** gösterir: elips, grubun orijininin 120 pt sağında başlar, böylece dikdörtgenle çakışmaz.

### Adım 5: Belgeyi kaydetme

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Kaydetme, Word dosyasını diske yazar. `GroupShape.docx` dosyasını Microsoft Word'de açarak dikdörtgen ve elipsin doğru şekilde gruplandığını ve konumlandırıldığını doğrulayabilirsiniz.

## Şekil boyutlarını ve ölçülerini ayarlama – daha derin bakış

- **Puan vs. inç**: 72 pt = 1 in. İnç tercih ederseniz, 72 ile çarpın (ör. 2.5 in için `2.5 * 72`).
- **Otomatik ölçekleme**: `Width` veya `Height` atlamanız durumunda şekil varsayılan boyutunu kullanır. Düzen sürprizlerinden kaçınmak için **şekil boyutunu açıkça ayarlayın**.
- **En‑boy oranı**: `Ellipse` gibi şekillerde `Width` ve `Height` eşit tutulduğunda dairesel görünüm korunur.

## Word'de bir şekli konumlandırma

`Left` ve `Top` özellikleri, şeklin konteyneri (grup veya sayfa) içindeki ofsetini kontrol eder. Pozitif değerler şekli sağa/aşağı hareket ettirir; negatif değerler sola/yukarı kaydırır. Gruplama yapıldığında konumlar, grubun orijinine göre olur ve bu, yerleşim hesaplamalarını basitleştirir.

## Aspose.Words kullanarak Word'de şekilleri gruplama

Gruplama, birden fazla şeklin tek bir birim gibi hareket etmesini istediğinizde esastır. `GroupShape` nesnesi:

- `AppendChild`'ı destekler ve herhangi bir `Shape` (dikdörtgen, elips, resim vb.) ekleyebilir.
- Tek bir çağrı ile tüm grubu taşımanıza, döndürmenize veya silmenize olanak tanır.
- Alt şekil konumlarını gruba göre tutar, böylece karmaşık diyagramları yönetmek daha kolay olur.

**Pro ipucu:** Tüm alt şekilleri ekledikten sonra, grubun `Width`, `Height`, `Left` ve `Top` değerlerini ayarlayarak tüm koleksiyonu tek adımda yeniden konumlandırabilirsiniz.

## Tam çalıştırılabilir örnek

Aşağıda kopyalayıp yapıştırıp çalıştırabileceğiniz tam program yer alıyor. Tüm `using` yönergelerini, bir `Main` metodunu ve her satırı açıklayan yorumları içerir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Beklenen çıktı:** Programı çalıştırdıktan sonra `GroupShape.docx` yürütme klasöründe oluşur. Word'de açtığınızda sol tarafta 100 pt × 50 pt bir dikdörtgen ve sağda 120 pt konumlandırılmış 80 pt × 80 pt bir elips görürsünüz; ikisi de tek bir grup nesnesi içinde.

![Word document with grouped rectangle and ellipse](grouped_shapes.png){: .center alt="C# ile oluşturulmuş bir grup dikdörtgen ve elips şekli gösteren bir Word belgesi ekran görüntüsü" }

*Yukarıdaki görsel son sonucu göstermektedir; dikdörtgen ve elips tek bir grup olarak seçilebilir.*

## Yaygın sorular ve uç durumlar

| Soru | Cevap |
|----------|--------|
| **İki'den fazla şekil ekleyebilir miyim?** | Evet. Her ek şekil için `group.AppendChild(yourShape)` çağırın. |
| **Grubu döndürmem gerekirse ne yapmalıyım?** | Tüm alt öğeler eklendikten sonra `group.RotationAngle = 45;` (derece) kullanın. |
| **Grubun arka plan rengini nasıl değiştiririm?** | `group.FillColor = System.Drawing.Color.LightGray;` olarak ayarlayın. |
| **Bu .doc dosyalarıyla çalışır mı?** | Aspose.Words `.doc` ve `.docx` dosyalarını destekler. Aynı kod çalışır; sadece `Save` içinde dosya uzantısını değiştirin. |
| **Birçok şekli gruplarken bellek etkisi var mı?** | Gruplama kendisi çok az ek yük getirir. Asıl endişe şekil sayısıdır; büyük belgeler için makul sayıda tutun. |

## Sonuç

Bu öğreticide C# kullanarak bir Word dosyasında **dikdörtgen şekli oluşturmayı**, **şekil boyutunu ayarlamayı**, **şekil ölçülerini ayarlamayı**, **şekil konumunu ayarlamayı** ve sonunda Aspose.Words ile **Word'de şekilleri gruplamayı** öğrendiniz. Tam örnek, daha karmaşık diyagramlar, grafikler veya özel görseller için genişletebileceğiniz temiz ve sürdürülebilir bir yaklaşımı gösterir.

Sonraki adımda şunları keşfedebilirsiniz:

- Şekillerin içine metin ekleme (`Shape.TextPath.Text = "Hello"`).
- `GroupShape` içine resim ekleme.
- Gruplanmış şekilleri `doc.Save("output.pdf")` ile PDF olarak dışa aktarma.

Farklı boyutlar, konumlar ve ek şekil tipleriyle denemeler yapmaktan çekinmeyin; projenizin ihtiyaçlarına göre uyarlayın. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words for .NET ile Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}