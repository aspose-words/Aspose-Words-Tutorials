---
category: general
date: 2026-10-20
description: Boş bir Word belgesi oluşturmayı, Word'de şekilleri gruplamayı, şekil
  dolgu rengini ayarlamayı ve tam bir C# örneğiyle satır içi sarma tipini kullanmayı
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: tr
lastmod: 2026-10-20
og_description: Aspose.Words ve C# kullanarak boş bir Word belgesi oluşturun, Word’de
  şekilleri gruplayın ve sarma türü satır içi olacak şekilde şekil dolgu rengini ayarlayın.
  Tam öğreticiyi izleyin.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Boş bir Word belgesi oluşturun ve Word’de şekilleri gruplayın – adım adım
  rehber
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words kullanarak boş bir Word belgesi oluşturma ve Word’de şekilleri
  gruplama
url: /tr/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş bir Word belgesi oluşturma ve Word'de şekilleri gruplama

Eğer **boş bir Word belgesi oluşturmanız** gerekiyorsa ve içinde birden fazla şekli tek bir birim gibi davranacak şekilde içeriyorsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. **Word'de şekilleri gruplamayı**, bir şeklin dolgu rengini ayarlamayı ve **wrap type inline** uygulamayı göreceksiniz—hepsi kısa ve çalıştırılabilir bir C# programı ile.

Bu öğretici, kodun her satırını adım adım anlatır, her adımın neden önemli olduğunu açıklar ve yaygın hataları vurgular. Sonunda, bir dikdörtgen ve bir metin kutusunun birlikte gruplandığı bir .docx dosyanız olacak ve bu dosya daha fazla otomasyon için hazır olacak.

## Öğrenecekleriniz

* Aspose.Words ile boş bir Word dosyasını nasıl başlatacağınız.
* **GroupShape** oluşturmanın ve alt şekilleri eklemenin doğru yolu.
* **set shape fill color** teknikleri ve konumlandırma kontrolü.
* **wrap type inline** kullanarak grubun tek bir satır içi nesne gibi davranmasını sağlamak.
* Sonucu kaydetme ve doğrulama.

Aspose.Words ile daha önce bir deneyiminiz olmasa da, temel C# sözdizimine aşina olmalı ve Visual Studio (veya başka bir IDE) kurulu olmalıdır.

## Gereksinimler

| Gereksinim | Sebep |
|------------|-------|
| .NET 6.0 veya üzeri | C# projesi için çalışma zamanını sağlar. |
| Aspose.Words for .NET (en son sürüm) | Örnekte kullanılan `Document`, `DocumentBuilder` ve şekil sınıflarını sağlar. |
| Yazılabilir bir klasör yolu | `doc.Save` çağrısının çıktıyı yazacağı geçerli bir dizin gerektirir. |
| Temel C# bilgisi | Kodu takip etmenizi ve kendi senaryolarınıza göre değiştirmenizi sağlar. |

Aspose.Words’u NuGet üzerinden kurun:

```bash
dotnet add package Aspose.Words
```

---

## 1. Adım: Boş bir Word belgesi oluşturma

İlk işlem **boş bir Word belgesi oluşturmak**tır. Aspose.Words’un `Document` sınıfı bellekte bir Word dosyasını temsil eder ve `DocumentBuilder` bu dosyayı düzenlemek için kullanışlı bir API sunar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters*: Temiz bir belgeyle başlamak, eklediğiniz grup şeklinin tek içerik olmasını garantiler ve doğrulamayı basitleştirir.

## 2. Adım: Wrap type inline ile bir grup şekil tanımlama

**GroupShape**, diğer şekiller için bir kapsayıcı görevi görür. `WrapType` özelliğini `Inline` olarak ayarlamak, grubun paragraf akışında tek bir satır içi nesne gibi davranmasını sağlar.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Why this matters*: **wrap type inline** kullanmak, grubun çevredeki metinden uzaklaşarak süzülmesini engeller; bu, grubun bir bütün olarak hareket etmesini istediğinizde kritiktir.

## 3. Adım: Bir dikdörtgen ekleyin ve şekil dolgu rengini ayarlayın

Dikdörtgen yaygın bir görsel öğedir. `Shape` yapıcısı bir `ShapeType` alır; ardından boyutları ve dolgu rengini belirleriz.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Why this matters*: `FillColor` özelliği, **set shape fill color** uygulamasını pratikte gösterir ve dikdörtgene, son belgede öne çıkan açık mavi bir arka plan verir.

## 4. Adım: Bir metin kutusu ekleyin – şekilleri etkili bir şekilde gruplama

Metin kutusu, grup içinde düzenlenebilir metin sağlar. `Top` özelliğini ayarlayarak metin kutusunu grup koordinat sistemine göre konumlandırın.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Why this matters*: Bu adım, **how to group shapes** sorusuna yanıt verir—her alt şekli aynı `GroupShape` örneğine ekleyerek. `Top` kaydırması, metin kutusunun dikdörtgenin altında görünmesini sağlar ve kesin yerleşim kontrolünü gösterir.

## 5. Adım: Tamamlanmış grup şekli belgeye ekleyin

Grup artık iki alt şekli içerdiğine göre, mevcut builder konumuna ekleyin.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Why this matters*: Grubu tek bir düğüm olarak eklemek, Word’ün dikdörtgen ve metin kutusunu tek bir mantıksal nesne olarak ele almasını garantiler; böylece düzenleme sırasında göreceli konumları korunur.

## 6. Adım: Belgeyi kaydedin ve çıktıyı doğrulayın

Son olarak, belgeyi diske yazın. `YOUR_DIRECTORY` kısmını makinenizdeki gerçek bir yol ile değiştirin.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

`GroupShape.docx` dosyasını Microsoft Word’de açtığınızda, “Grouped text” etiketiyle bir metin kutusunun doğrudan altında bulunan açık mavi bir dikdörtgen görmelisiniz. Her iki şekilden birini seçtiğinizde tüm grup seçilir; bu da **group shapes in Word** işlevinin beklendiği gibi çalıştığını doğrular.

### Beklenen sonuç

* Tek bir paragraf içeren bir .docx dosyası.
* Paragraf içinde, tek bir birleşik nesne gibi görünen satır içi bir grup.
* Dikdörtgen açık mavi ile doldurulmuş ve metin kutusu “Grouped text” metnini gösteriyor.

![Screenshot of the generated Word document](grouped_shapes.png){.center width=600 alt="Aspose.Words kullanılarak oluşturulmuş, gruplandırılmış dikdörtgen ve metin kutusu içeren boş bir Word belgesinin ekran görüntüsü"}

## Yaygın sorular ve kenar‑durum yönetimi

### Grupun satır içi yerine süzülmesini (float) istersem ne yapmalıyım?

`WrapType.Inline` yerine `WrapType.TopBottom` (veya başka bir `WrapType` enum değeri) kullanın. Süzülen gruplar paragraf akışından bağımsız olarak konumlandırılabilir, ancak otomatik satır içi hizalamayı kaybederler.

### Daireler veya resimler gibi daha fazla şekil ekleyebilir miyim?

Evet. `ShapeType.Ellipse` veya `ShapeType.Image` ile ek `Shape` nesneleri oluşturun, özelliklerini yapılandırın ve `group.AppendChild(newShape)` çağrısını yapın. Grup, `group.Bounds` değerini buna göre güncellediğinizde yeni sınırları otomatik olarak genişletecektir.

### Çocuk şekilleri ekledikten sonra grubun genel boyutunu nasıl değiştiririm?

Tüm çocuklar eklendikten sonra `group.Bounds` özelliğini ayarlayın veya programlı olarak çocuk sınırlarının birleşimini hesaplayın. Bu, grup çarpma‑test alanının görsel içeriğe eşleşmesini sağlar.

### Çıktı klasörü mevcut değilse ne olur?

Aspose.Words bir `DirectoryNotFoundException` fırlatır. Önce klasörü oluşturun:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### .NET Core yerine .NET Framework ile çalışır mı?

Kullanılan tüm API’ler (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) Aspose.Words’un .NET Framework sürümünde de mevcuttur; bu nedenle aynı kod değişiklik yapmadan çalışır.

## Pro ipuçları

* **Performance tip** – Birçok grup eklerken tek bir `DocumentBuilder` örneğini yeniden kullanın; grup başına yeni bir builder oluşturmak ek yük getirir.
* **Görsel tutarlılık** – `rectangle.StrokeColor` değerini `FillColor` ile eşleştirerek sorunsuz bir görünüm elde edin veya kenarı gizlemek için `rectangle.LineWidth = 0` ayarlayın.
* **Debugging** – Çok sayıda şekil değiştirdiğinizde kaydetmeden önce `doc.UpdatePageLayout()` çağırın; bu, Word’ün yerleşimi yeniden hesaplamasını zorlayarak beklenmedik kırpılmaları önleyebilir.

## Sonuç

Artık **boş bir Word belgesi oluşturma**, **Word'de şekilleri gruplama**, **şekil dolgu rengini ayarlama** ve **wrap type inline** uygulama konularında Aspose.Words for .NET kullanarak bilgi sahibisiniz. Tam örnek, Word’de tek bir nesne gibi davranan birleşik grafikler oluşturmanın standart yaklaşımını gösteriyor.

Bundan sonra şunları keşfedebilirsiniz:

* Resim veya grafik gibi ek şekiller eklemek.
* Süzülen gruplar için farklı `WrapType` değerleri denemek.
* Birden çok belgeye grup diyagramları toplu olarak üretmek için otomasyon.

Kodunuzu kendi otomasyon senaryolarınıza göre uyarlamaktan çekinmeyin ve sonuçlarınızı yorumlarda paylaşın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, tam çalışan kod örnekleri ve adım adım açıklamalar içerir; böylece ek API özelliklerini öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [How to Save PDF from Word with Inline Shapes – Complete Guide](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}