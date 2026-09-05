---
category: general
date: 2026-09-05
description: Aspose.Words kullanarak C#'te boş bir Word belgesi oluşturmayı ve gizlenebilen
  bir dikdörtgen şekli eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: tr
lastmod: 2026-09-05
og_description: Aspose.Words kullanarak boş Word belgesi oluşturma ve gizli dikdörtgen
  şekil ekleme – C# geliştiricileri için adım adım rehber.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Gizli bir dikdörtgen şekli içeren boş bir Word belgesi oluştur
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Boş bir Word belgesi oluşturun ve bir dikdörtgen şekli ekleyin
url: /tr/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş bir Word belgesi oluşturun ve bir dikdörtgen şekli ekleyin

Eğer **blank word document** oluştururken, düzen içinde görünmesini istemediğiniz bir şekil de eklemek istiyorsanız, bu kılavuz Aspose.Words for .NET ile bunu nasıl yapacağınızı adım adım gösterir. Yeni bir belge oluşturup, bir dikdörtgen şekli ekleyip, bu şekli gizleyip ve dosyayı kaydeden tam, çalıştırılabilir bir örnek göreceksiniz—ekstra bir araç gerektirmez.

Bu öğretici, proje kurulumundan yaygın hataların giderilmesine kadar her şeyi kapsar. Sonunda, okuyucuya boş gibi görünen ancak gizli meta veriler taşıyan bir Word dosyası üretebileceksiniz; bu, filigranlar, özel XML depolama veya düzen ankrajları gibi durumlar için faydalıdır.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 SDK veya daha yeni bir sürüm (kod .NET Framework 4.7+ ile de çalışır)
* Visual Studio 2022 (veya C# destekleyen herhangi bir IDE)
* Aktif bir **Aspose.Words** NuGet lisansı (ücretsiz deneme sürümü test için yeterlidir)
* C# ve belge düğümleri kavramına temel aşinalık

Kütüphaneyi aşağıdaki CLI komutuyla kurabilirsiniz:

```bash
dotnet add package Aspose.Words
```

> **Pro ipucu:** Aspose.Words sürümünüzü güncel tutun; bu öğreticide kullanılan API, 23.10 sürümü itibarıyla kararlıdır.

## Aspose.Words ile boş bir Word belgesi nasıl oluşturulur

İlk adım, bir `Document` nesnesi örneklemektir. Yeni bir `Document`, boş bir **blank word document** temsil eder—paragraf, bölüm yok, sadece dosya konteyneri.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Neden önemli:** Temiz bir belgeyle başlamak, daha sonra ekleyeceğiniz gizli şeklin mevcut içerik veya stillerle çakışmasını önler.

## Belgeye bir dikdörtgen şekli ekleyin

Şimdi bir dikdörtgen şekli oluşturacağız. Aspose.Words içinde bir şekil, belge ağacının herhangi bir yerine yerleştirilebilen bir düğümdür ve boyut, dolgu, çizgi stili ve görünürlük gibi özelliklerle yapılandırılabilir.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

Yukarıdaki kod görünür bir dikdörtgen oluşturur. Bu noktada `builder.InsertNode(rectangle)` ile belgeye ekleyebilirdiniz. Ancak şeklin gizli kalmasını istediğimiz için, eklemeden önce `Hidden` özelliğini ayarlayacağız.

## Word belgesinde şekli nasıl gizlersiniz

Word, şekil düğümleri için bir `Hidden` özniteliği sağlar. `true` olarak ayarlandığında, şekil sayfa düzeninde görünmez, ancak belgenin XML'inin bir parçası olarak kalır. Bu, **how to hide shape** gereksiniminin temelidir.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Açıklama:** `Hidden = true` ayarı, şeklin XML'ine `<w:hide>` özniteliğini ekler. Word işlemcileri şekli render ederken yok sayar, ancak şekle programatik olarak veya Word'ün XML görünümünden hâlâ erişilebilir.

## Gizli şekli boş belgeye ekleyin

Şimdi gizli dikdörtgeni belge ağacına yerleştiriyoruz. Belge hâlâ boş olduğundan, şekil ana hikâyenin ilk düğümü olur.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Dosyayı Microsoft Word'de açtığınızda görünüşte boş bir sayfa göreceksiniz. Şekil oradadır, ancak görünmez.

## Belgeyi kaydedin

Son olarak belgeyi diske yazalım. Desteklenen herhangi bir formatı (`.docx`, `.pdf`, `.odt` vb.) seçebilirsiniz. Bu öğreticide modern DOCX formatını kullanacağız.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Beklenen sonuç

`HiddenRectangle.docx` dosyasını Word'de açın:

* Belge boş görünür (görünür şekil veya metin yok).
* **Open XML SDK** veya **Word XML Viewer** gibi bir araçla dosyayı incelerseniz, `hidden` özniteliğine sahip dikdörtgeni içeren `<w:pict>` öğesini göreceksiniz.

![gizli dikdörtgen şekilli boş Word belgesi](image.png){: .align-center alt="gizli dikdörtgen şekilli boş Word belgesi"}

## Tam, çalıştırılabilir örnek

Aşağıda, bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz tam program yer alıyor. Gerekli tüm `using` yönergeleri, hata yönetimi ve yorumlar dahildir.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Programı (`dotnet run`) çalıştırın ve çıktı dosyasını doğrulayın. Konsol, kaydetme konumunu onaylayacaktır.

## Yaygın sorular ve kenar durumları

### Aynı anda birden fazla şekli gizleyebilir miyim?

Evet. Her şekli oluşturun, `Hidden = true` ayarlayın ve sırasıyla ekleyin. Gizli bayrak düğüm başına çalışır, bu yüzden aynı belgede gizli ve görünür şekiller karıştırılabilir.

### Şeklin sadece yazdırma görünümünde gizli olmasını nasıl sağlarım?

Word, **display** (görünüm) ve **print** (yazdırma) görünürlüğünü `DisplayWhen` özelliğiyle ayırır. Aspose.Words bu bayrak için doğrudan bir API sunmaz, ancak temel XML'i şu şekilde değiştirebilirsiniz:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Bunu yalnızca sadece yazdırma görünürlüğüne ihtiyaç duyduğunuzda kullanın.

### Gizli şekil dosya boyutunu etkiler mi?

Gizli bir şekil, görünür bir şekil ile aynı XML yükünü ekler, bu yüzden dosya boyutu artışı aynıdır. Ancak şekil


## Sonra Ne Öğrenmelisiniz?


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak ilgili konuları ele alır. Her kaynak, adım adım açıklamalar ve tam çalışan kod örnekleri içerir; böylece ek API özelliklerini ustalaşabilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}