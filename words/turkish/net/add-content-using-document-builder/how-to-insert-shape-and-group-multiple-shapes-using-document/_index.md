---
category: general
date: 2026-11-15
description: Aspose.Words DocumentBuilder ile bir Word belgesine şekil eklemeyi ve
  birden fazla şekli gruplamayı öğrenin. Dikdörtgen şekil ekleme ve birden fazla şekil
  ekleme örneklerini içerir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: tr
lastmod: 2026-11-15
og_description: Aspose.Words kullanarak bir Word dosyasına şekil ekleme. Bu kılavuz,
  birden fazla şeklin gruplanmasını, dikdörtgen şeklin eklenmesini ve birden fazla
  şeklin verimli bir şekilde eklenmesini kapsar.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: DocumentBuilder ile şekil ekleme ve birden fazla şekli gruplama
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: C#'ta DocumentBuilder kullanarak şekil ekleme ve birden fazla şekli gruplama
url: /tr/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DocumentBuilder kullanarak C#'ta şekil ekleme ve birden fazla şekli gruplama

Aspose.Words ile bir Word belgesine **how to insert shape** nasıl yapılacağını öğrenmeniz gerekiyorsa, bu kılavuz size tam adımları gösterir. Ayrıca **group multiple shapes** nasıl yapılacağını, bu şekillerin tek bir nesne gibi davranmasını ve **insert rectangle shape** nasıl yapılacağını diğer grafiklerin yanında öğreneceksiniz.

Belge otomasyonu genellikle birden fazla grafik eklemeyi—grafikler, logolar, açıklamalar—gerektirir ve bunları düzenli tutar. Bu öğreticinin sonunda **insert multiple shapes** yapabilecek, bunları bir grup içinde yerleştirebilecek ve temiz, yeniden kullanılabilir bir düzen kaydedebileceksiniz.

## Önkoşullar

* .NET 6.0 veya daha yeni bir sürüm yüklü  
* Visual Studio 2022 (veya herhangi bir C# IDE)  
* Aspose.Words for .NET lisansı veya ücretsiz değerlendirme anahtarı  
* C# ve Aspose.Words `DocumentBuilder` sınıfına temel aşinalık  

Başka herhangi bir üçüncü taraf kütüphaneye **ihtiyacınız** yok; gereken her şey Aspose.Words içinde yer alır.

## Adım 1: NuGet üzerinden Aspose.Words'i Yükleyin

Visual Studio'da projenizi açın ve Package Manager Console'da aşağıdaki komutu çalıştırın:

```powershell
Install-Package Aspose.Words
```

Paket, bu öğreticide kullanılan `DocumentBuilder`, `Shape` ve `GroupShape` sınıflarını içerir.

## Adım 2: DocumentBuilder örneği oluşturun – **how to insert shape** için temel

İlk uygulanabilir kod satırı bir `DocumentBuilder` oluşturmaktır. Bu nesne, belge ağacına doğrudan erişim sağlar ve şekilleri tam istediğiniz yere yerleştirmenize olanak tanır.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Neden önemli*: `DocumentBuilder` bir imleç ("ekleme noktası") tutar. Sonraki her `Insert...` çağrısı bu imleci kullanır; bu yüzden daha sonra tüm şekilleri bir arada tutmak için imleci bir `GroupShape` içine taşıyoruz.

## Adım 3: **Insert rectangle shape** – ekleyeceğiniz ilk grafik

Dikdörtgen, tablolar, görseller veya açıklamalar için yaygın bir yer tutucudur. `InsertShape`'i `ShapeType.Rectangle` ile kullanın ve genişlik ile yüksekliği puan cinsinden belirtin (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Dikdörtgen, mevcut imleç konumunda görünür. Gerektiğinde dolgusunu, çizgi stilini veya metnini daha sonra özelleştirebilirsiniz.

## Adım 4: Başka bir şekil ekleyin – görsel çeşitlilik için bir elips

Birden fazla şekil eklemek, **insert multiple shapes** gösterir. Elips, belge akışında dikdörtgenden sonra yer alacaktır.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Bu noktada belge iki bağımsız şekil içerir. İmleci hareket ettirirseniz veya metin eklerseniz, şekiller eklenme konumlarında kalır.

## Adım 5: **Group multiple shapes** – tek bir birim gibi davranmaları için

Birden fazla grafiği birlikte taşımak, döndürmek veya biçimlendirmek gerektiğinde gruplama esastır. Aşağıdaki kod bir `GroupShape` oluşturur, builder'ın imlecini içine taşır ve aynı şekilleri tekrar ekler—bu sefer grupun alt öğeleri olurlar.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Neden grup kullanılır?

- **Single‑point transformation** – tek bir çağrıyla tüm grubu döndürün veya yeniden boyutlandırın.  
- **Logical organization** – Word belge ağacı gruplamayı yansıtır, sonraki düzenlemeleri kolaylaştırır.  
- **Consistent layout** – grubu taşımak, alt öğelerinin göreceli konumlarını korur.

### Daha fazla şekil ekleme – grup içinde **insert multiple shapes** genişletme

İmleç `GroupShape` içinde kaldığı sürece `InsertShape` çağrısını yapmaya devam edebilirsiniz. Örneğin, bir üçgen eklemek için:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Her çağrı grup bağlamına saygı gösterir, bu yüzden üçgen otomatik olarak aynı gruplu setin parçası olur.

## Adım 6: Belgeyi kaydedin ve sonucu doğrulayın

Tüm şekiller yerleştirildikten sonra belgeyi bir `.docx` dosyasına kaydedin. Dosyayı Microsoft Word'de (veya uyumlu bir görüntüleyicide) açtığınızda iki ayrı şekil ve ardından aynı dikdörtgen, elips ve üçgeni içeren bir grup seti görmelisiniz.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Beklenen çıktı

- **First two shapes** – sayfada bağımsız olarak yerleştirilen bir dikdörtgen ve bir elips.  
- **Grouped block** – Word'de herhangi birine tıkladığınızda birlikte hareket eden bir dikdörtgen, bir elips ve bir üçgen.

Grubu test etmek için grup içindeki herhangi bir şekli seçebilirsiniz; Word tüm koleksiyonu vurgulayacak ve **group multiple shapes** işleminin başarılı olduğunu onaylayacaktır.

## Yaygın tuzaklar ve profesyonel ipuçları

| Sorun | Neden oluşur | Çözüm |
|-------|----------------|-----|
| Şekiller hedef sayfanın dışında görünüyor | Builder'ın imleci, eklemeden önce `GroupShape` içine taşınmamıştı. | Gruba ait herhangi bir `InsertShape` çağrısından **önce** her zaman `builder.MoveTo(group)` çağırın. |
| Grup kaydedildikten sonra kayboluyor | Grup, belgenin düğüm koleksiyonuna eklenmeden eklenmişti. | `GroupShape` oluşturulduktan hemen sonra `builder.InsertNode(group)` kullanın. |
| Belge DPI'sı nedeniyle beklenmeyen boyut | Aspose.Words puan (point) kullanır; piksel olarak düşünürseniz boyutlar uyuşmayabilir. | Pikseli puana dönüştürün (`points = pixels * 72 / 96`) veya doğrudan puan cinsinden çalışın. |
| Şekiller istem dışı üst üste geliyor | Açık bir konumlandırma ayarlanmamıştı; Word şekilleri sırasıyla yerleştirir. | Tam konumu kontrol etmek için eklemeden sonra `Shape.Left` ve `Shape.Top` değerlerini ayarlayın. |

**Pro ipucu:** Gruplamadan sonra, grupun `Shapes` koleksiyonunu (`group.Shapes`) alabilir, üzerinde döngü kurabilir, yeniden adlandırabilir veya toplu biçimlendirme uygulayabilirsiniz.

## Adım 7: Örneği genişletmek – sonraki adım ne?

Artık **how to insert shape**, **insert rectangle shape** ve **group multiple shapes** bildiğinize göre, şunları keşfedebilirsiniz:

- **Animating grouped shapes** – grupta dönüş veya çevirme özelliklerini ayarlayın.  
- **Applying styles** – etiket eklemek için `Shape.FillColor`, `Shape.LineFormat` veya `Shape.TextBox` kullanın.  
- **Exporting to PDF** – aynı gruplu düzen, `doc.Save("output.pdf")` çağrıldığında doğru şekilde oluşturulur.

Bu uzantıların tümü aynı `DocumentBuilder` iş akışını yeniden kullanır, kodunuzu temiz ve sürdürülebilir tutar.

## Sonuç

Bu öğretici, Aspose.Words ile bir Word belgesine **how to insert shape** nasıl yapılacağını, **insert rectangle shape** nasıl ekleneceğini ve **group multiple shapes** nasıl yapılacağını, şekillerin tek bir nesne gibi davranmasını gösterdi. Adım adım kodu izleyerek güvenilir bir şekilde **insert multiple shapes** yapabilir, bunları gruplara düzenleyebilir ve programlı olarak profesyonel düzeyde belgeler üretebilirsiniz.

Farklı şekil tipleri, renkler ve grup dönüşümleriyle denemeler yapmaktan çekinmeyin. Hazır olduğunuzda, bu deseni daha büyük raporlama veya şablon çözümlerine entegre ederek karmaşık belge düzenlerini otomatikleştirin. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [How to group shapes in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}