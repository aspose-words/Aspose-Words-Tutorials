---
category: general
date: 2026-09-21
description: Aspose.Words kullanarak boş bir Word belgesi oluşturun, şekil boyutunu
  ayarlayın, şekil konumunu ayarlayın, şekil rengini ayarlayın ve tek bir adımda docx
  dosyasını kaydedin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: tr
lastmod: 2026-09-21
og_description: Boş bir Word belgesi oluşturun, şekil boyutunu ayarlayın, şekil konumunu
  ayarlayın, şekil rengini ayarlayın ve docx dosyasını Aspose.Words ile dakikalar
  içinde kaydedin.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Boş bir Word belgesi oluşturun ve renkli şekiller ekleyin – Aspose.Words
  rehberi
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Boş bir Word belgesi oluşturun ve Aspose.Words ile renkli şekiller ekleyin
url: /tr/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş bir Word belgesi oluşturun ve renkli şekiller ekleyin (Aspose.Words)

Programatik olarak **boş bir Word belgesi oluşturmanız** gerektiğinde, bu kılavuz Aspose.Words ile nasıl yapılacağını gösterir. **Şekil boyutunu ayarlama**, **şekil konumunu ayarlama**, **şekil rengini ayarlama** ve sonunda **docx dosyasını kaydetme** işlemlerini IDE’nizden çıkmadan öğrenmiş olacaksınız.

C#’ta Word dosyalarıyla çalışmak genellikle düşük seviyeli OpenXML çağrılarını yönetmek anlamına gelir, ancak Aspose.Words bu karmaşıklığı soyutlar. Bu öğreticinin sonunda iki renkli dikdörtgenden oluşan bir grup şekli içeren tam işlevsel bir `.docx` dosyanız olacak—raporlar, sertifikalar veya özel şablonlar için mükemmel.

## Önkoşullar

- .NET 6.0 veya üzeri (kod .NET Framework 4.7+ ile de çalışır)
- Aspose.Words for .NET 23.9 veya daha yeni bir sürüm (NuGet üzerinden kurun: `Install-Package Aspose.Words`)
- C# ve Visual Studio (veya herhangi bir C# editörü) hakkında temel bilgi

Mevcut bir Word dosyasına ihtiyaç yok; öğretici **boş bir Word belgesi oluşturma** ile başlar.

## Aspose.Words ile boş bir Word belgesi oluşturma

İlk adım bir `Document` nesnesi örneklemektir. Bu nesne bellekte boş bir Word dosyasını temsil eder.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` başlangıçta boştur; bu da **boş bir Word belgesi oluşturma** ihtiyacınız için tam olarak gereklidir. `builder` daha sonra şekil grubunu geçerli imleç konumuna eklemek için kullanılacaktır.

## Şekil boyutunu ayarlama ve bir GroupShape oluşturma

`GroupShape`, birden fazla ayrı şekli tutabilen bir kapsayıcı gibi çalışır. Öncelikle kapsayıcının genel boyutlarını tanımlayın.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Burada grup için **şekil boyutunu ayarlıyoruz** (300 × 200). Aynı özellik adları (`Width`, `Height`) her bir alt şekil için de kullanılır; böylece her öğe üzerinde ince ayar yapabilirsiniz.

## İlk dikdörtgeni ekleyin ve şekil rengini ayarlayın

Şimdi gruba bir dikdörtgen ekleyin ve arka plan rengini belirleyin.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

`FillColor` özelliği **şekil rengini ayarlar**. `System.Drawing.Color` kullanarak önceden tanımlı ya da özel ARGB değerlerinden birini seçebilirsiniz.

## İkinci dikdörtgeni ekleyin, boyutunu, konumunu ve rengini ayarlayın

İkinci dikdörtgen, **şekil konumunu** grup içinde nasıl ayarlayacağınızı ve rengini nasıl değiştireceğinizi gösterir.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Grubun genişliği 300 puan olduğu için iki 120 puanlık dikdörtgen, 30 puanlık bir boşlukla rahatça sığar. Farklı bir düzen isterseniz `Left` ve `Top` değerlerini ayarlayın.

## GroupShape’i belgeye ekleme

Grup tamamen yapılandırıldıktan sonra, geçerli imleç konumuna yerleştirin.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode`, şekli doğrudan belgenin gövdesine yazar ve daha önce tanımladığınız **şekil konumunu** tam olarak korur.

## docx dosyasını kaydetme

Son adım, belgeyi diske kalıcı olarak kaydetmektir. Bu, **docx dosyasını kaydet** işlemini gösterir.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

Programı çalıştırdıktan sonra `GroupShape.docx` dosyasını Microsoft Word’de açın. Boş bir sayfada yan yana iki renkli dikdörtgen içeren bir grup şekil görmelisiniz.

### Beklenen çıktı

- Tek sayfalık bir `.docx` dosyası.
- Sayfa, sol ve üst kenarlardan 100 pt uzaklıkta bir grup şekil içerir.
- Grup içinde, sol tarafta açık mavi bir dikdörtgen, sağ tarafta açık mercan bir dikdörtgen bulunur; her biri 120 × 80 pt boyutundadır.

## Tam, çalıştırılabilir örnek

Aşağıda bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz tam program yer alıyor. Ek bir dosyaya ihtiyaç yok.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Bu programı çalıştırdığınızda, önceki bölümde açıklanan belge tam olarak oluşturulur; dört hedef gerçekleşir: **boş word belgesi oluşturma**, **şekil boyutunu ayarlama**, **şekil konumunu ayarlama**, **şekil rengini ayarlama** ve **docx dosyasını kaydetme**.

## Yaygın varyasyonlar ve kenar durumları

| Senaryo | Ne değiştirilmeli | Neden önemlidir |
|----------|-------------------|-----------------|
| **Farklı şekil tipleri** | `ShapeType.Rectangle` yerine `ShapeType.Ellipse`, `ShapeType.Triangle` vb. kullanın | Harici görsellere ihtiyaç duymadan daha karmaşık grafikler oluşturmanızı sağlar. |
| **Dinamik boyutlar** | `Width` ve `Height` değerlerini kullanıcı girişi ya da yapılandırma dosyasından hesaplayın | Çözümün birden çok belge şablonunda yeniden kullanılabilir olmasını sağlar. |
| **PDF olarak kaydetme** | `document.Save("output.pdf", SaveFormat.Pdf);` çağrısını ekleyin | Alıcıların düzenlenemez bir format ihtiyacı varsa PDF güvenli bir tercihtir. |
| **Şekil içine metin ekleme** | Bir `TextBox` şekli oluşturup `TextBox.Text` özelliğini ayarlayın | Etiketli rozetler veya açıklama kutuları oluşturmak için kullanışlıdır. |
| **Tek sayfada birden çok grup** | Farklı `Left`/`Top` değerleriyle adım 2‑5’i tekrarlayın | Panolar veya çok bölümlü düzenler oluşturmanıza olanak tanır. |

### Pro ipucu

Şekilleri tam olarak hizalamanız gerektiğinde, grubu eklemeden önce `ShapeBase.WrapType = WrapType.Inline` özelliğini ayarlayın. Bu, grubun bir paragraf gibi davranmasını sağlar ve etrafındaki metnin beklenmedik şekilde akmasını engeller.

## Sonuç

Artık Aspose.Words ile **boş bir Word belgesi oluşturma**, **şekil boyutunu ayarlama**, **şekil konumunu ayarlama**, **şekil rengini ayarlama** ve **docx dosyasını kaydetme** konularını biliyorsunuz. Tam örnek, herhangi bir Word otomasyon projesine grup grafik eklemek için temiz ve yeniden kullanılabilir bir desen sunar.

Bundan sonra keşfedebilecekleriniz:

- Aynı `GroupShape` içine daha fazla şekil veya resim ekleme (**şekil boyutunu ayarlama**, **şekil rengini ayarlama** varyasyonları).
- Dekoratif etkiler için `ShapeBase.Rotation` kullanarak dikdörtgenleri döndürme.
- Aynı belgeyi PDF veya HTML olarak dışa aktararak dağıtım kapsamını genişletme (**docx dosyasını kaydetme** alternatifleri).

Farklı renkler, boyutlar ve düzen mantıklarıyla deneyler yaparak raporlama veya şablon ihtiyaçlarınıza tam uyum sağlayın. İyi kodlamalar!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımları keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}