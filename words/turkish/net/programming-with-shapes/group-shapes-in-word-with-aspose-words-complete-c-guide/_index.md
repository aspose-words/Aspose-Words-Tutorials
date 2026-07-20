---
category: general
date: 2026-07-19
description: Aspose.Words kullanarak Word’de şekilleri gruplayın. Dikdörtgen şekli
  eklemeyi, elips şekli tanımlamayı ve şekli Word belgelerine eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: tr
lastmod: 2026-07-19
og_description: Aspose.Words ile Word’de şekilleri gruplayın. Dikdörtgen şekli ekleme,
  elips şekli tanımlama ve şekli Word belgelerine ekleme.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Word'de Şekilleri Gruplama – Adım Adım C# Öğretici
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Aspose.Words ile Word'de Grup Şekilleri – Tam C# Rehberi
url: /tr/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Şekilleri Gruplama – Tam C# Rehberi

Hiç **Word'de şekilleri gruplama** işlemini arayüzle uğraşmadan nasıl yapabileceğinizi merak ettiniz mi? Tek başınıza değilsiniz. Sözleşmeler, broşürler veya diyagramları programlı olarak oluşturuyorsanız, **dikdörtgen şekil ekleme**, **elips şekli tanımlama** ve ardından **Word'de şekilleri gruplama** yeteneği saatlerce manuel işi tasarruf ettirebilir.

Bu öğreticide **Aspose.Words for .NET** kullanarak gerçek bir örnek üzerinden ilerleyeceğiz. Sonunda **Word'e şekil ekleme**, bunları birleştirme ve müşterilere ya da ekip arkadaşlarınıza gönderebileceğiniz şık bir belge üretme konusunda tam bilgi sahibi olacaksınız.

---

## Gereksinimler

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

- **Aspose.Words for .NET** (en son sürüm, ör. 24.9). NuGet üzerinden `Install-Package Aspose.Words` komutuyla alabilirsiniz.
- .NET geliştirme ortamı (Visual Studio 2022 veya C# uzantılı VS Code yeterli).
- C# sözdizimi hakkında temel bilgi—farklı bir şey değil, sadece normal `using` ifadeleri ve nesne oluşturma.

Hepsi bu. Ek kütüphane, COM interop yok, sadece saf yönetilen kod.

---

## Aspose.Words Kullanarak Word'de Şekilleri Nasıl Gruplarsınız

Aşağıda, zaten sahip olduğunuz kodu yansıtan adım‑adım bir açıklama yer alıyor. Her adım, **neden** yaptığımızı, sadece **ne** yaptığımızı değil, açıklıyor; böylece istediğiniz herhangi bir şekil için deseni uyarlayabilirsiniz.

### Adım 1: Belge ve Builder'ı Ayarlama

Boş bir `Document` ve bir `DocumentBuilder` oluşturuyoruz. Builder, içerikleri istediğimiz yere eklememizi sağlayan “kalem”imizdir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Neden?** `Document` nesnesi tüm .docx dosyasını temsil ederken, `DocumentBuilder` alt düğüm ağacıyla uğraşmadan (şekiller gibi) düğüm eklemek için kullanışlı bir API sunar.

### Adım 2: Dikdörtgen Şekil Ekleme (add rectangle shape)

Şimdi **dikdörtgen şekil** ekliyoruz. Boyutunu, konumunu ve dolgu rengini ayarlayarak öne çıkmasını sağlıyoruz.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **İpucu:** `FillColor` değerini istediğiniz herhangi bir `System.Drawing.Color` ile değiştirebilirsiniz. Bu, raporda renk‑kodlu bölümler gerektiğinde faydalıdır.

### Adım 3: Elips Şekli Tanımlama (define ellipse shape)

Sonra **elips şekli** tanımlıyoruz. Farklı `ShapeType` ve ofset (`Left = 120`) sayesinde elips, dikdörtgenin yanına oturur.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Neden önemli?** Şekilleri açıkça konumlandırarak, gruplamadan önce nasıl görüneceklerini kontrol edersiniz. Otomatik yerleşime güvenirseniz, grup ortalanmamış görünebilir.

### Adım 4: (İsteğe Bağlı) Ön İzleme İçin Tek Tek Şekilleri Ekleme

Şekilleri gruplamadan önce her birini görmek isterseniz, **Word'e şekil ekleme** işlemini ayrı ayrı yapabilirsiniz. Bu adım isteğe bağlıdır ancak hata ayıklama için kullanışlıdır.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Pro ipucu:** Şekillerin doğru göründüğünden emin olduğunuzda bu iki satırı yorum satırı haline getirin; aksi takdirde grup sonrası çift görsellerle karşılaşırsınız.

### Adım 5: Şekilleri Gruplama – GroupShape Oluşturma

İşte öğretinin özü: **şekilleri gruplama**. Bir `GroupShape` oluşturuyor, dikdörtgen ve elipsimizi ekliyor ve grubun çevredeki metinle nasıl davranacağını belirliyoruz.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Açıklama:** `GroupShape`, diğer şekilleri tutan bir mini‑tuval gibidir. `WrapType` değerini `Inline` yaparak, grup bir bütün olarak metin eklenip silindiğinde tek bir birim gibi hareket eder.

### Adım 6: Gruplanmış Şekli Belgeye Ekleme (insert shape into word)

Şimdi **Word'e şekil ekleme**—ama bu sefer tek tek parçalar değil, gruplandırılmış konteyner.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **Arka planda ne oluyor?** `InsertNode` çağrısı, `GroupShape`'i belgenin düğüm koleksiyonuna ekler. Grup zaten dikdörtgen ve elipsi içerdiği için, bunlar tek bir nesne olarak görünür.

### Adım 7: Belgeyi Kaydetme

Son olarak dosyayı diske yazıyoruz. Proje yapınıza uygun şekilde yolu değiştirebilirsiniz.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Sonuç:** `GroupShape.docx` dosyasını Microsoft Word'de açtığınızda, yan yana duran açık mavi bir dikdörtgen ve mercan renkli bir elipsi birlikte kilitlenmiş olarak göreceksiniz. Birini sürüklemek diğerini de hareket ettirir—tam da “Word'de şekilleri gruplama” vaat ettiği gibi.

---

## Görsel Doğrulama

Aşağıda, Word dosyası içinde gruplanmış şekillerin nasıl göründüğüne dair bir taslak yer alıyor.  

![Aspose.Words ile oluşturulmuş bir Word belgesindeki gruplanmış şekillerin ekran görüntüsü](grouped_shapes_placeholder.png "Word'de şekilleri gruplama")

*Görselin alt metni, erişilebilirlik ve SEO için anahtar kelimeyi içerir.*

---

## Yaygın Sorular & Kenar Durumları

### Daha fazla şekle ihtiyacım olursa ne yapmalıyım?

`groupShape.AppendChild(yourNewShape);` satırını grup eklemeden önce istediğiniz kadar çağırabilirsiniz. API, çocuk şekil sayısı konusunda bir sınırlama getirmez.

### Tüm grubu döndürebilir ya da yeniden boyutlandırabilir miyim?

Kesinlikle. `GroupShape`, `Shape` sınıfından türediği için `RotationAngle`, `Width` veya `Height` gibi özellikleri grup üzerinde ayarlayabilirsiniz; tüm çocuk şekiller bu değişiklikleri takip eder.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### Grubun arka plan rengini nasıl değiştiririm?

`groupShape.FillColor` özelliğini kullanın. Bu, görünmez sınırlayıcı kutuyu doldurur; vurgulama amacıyla işe yarayabilir.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### Bu eski Word formatlarıyla (.doc) çalışır mı?

`Aspose.Words` `.doc` formatına da kaydedebilir—sadece `Save` içinde dosya uzantısını değiştirin. Ancak, grup oluşturma gibi bazı gelişmiş şekil özellikleri yalnızca OOXML `.docx` formatında tam desteklenir.

---

## Tam Çalışan Örnek

Aşağıdaki bloğu yeni bir konsol uygulamasına kopyalayıp yapıştırın; tüm süreci bir arada göreceksiniz. Eksik bir parça yok; **tam, çalıştırılabilir bir örnek**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Beklenen çıktı:** `GroupShape.docx` dosyasını açtığınızda, yan yana hizalanmış açık mavi bir dikdörtgen ve açık mercan bir elipsten oluşan tek bir grup nesnesi göreceksiniz.

---

## Özet

Word'de Aspose.Words ile **şekilleri gruplama** konusunda ihtiyacınız olan her şeyi ele aldık:

1. Belge ve builder oluşturma.  
2. **Dikdörtgen şekil** ve **elips şekli** ekleme, boyutları açıkça tanımlama.  
3. (İsteğe bağlı) **Word'e şekil ekleme** ile hızlı ön izleme.  
4. `GroupShape` kullanarak **şekilleri gruplama**—her çocuğu ekleyin, sarma ayarını yapın ve ekleyin.  
5. Dosyayı kaydedin ve doğrulayın.

## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayalı olarak yakın konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım‑adım kod örnekleri içerir.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}