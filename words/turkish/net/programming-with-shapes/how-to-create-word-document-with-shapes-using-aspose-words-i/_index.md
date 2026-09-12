---
category: general
date: 2026-09-11
description: Aspose.Words ile Word belgesi oluşturmayı, dikdörtgen şekli eklemeyi
  ve şekil boyutlarını ayarlamayı öğrenin. Hassas şekil boyutlandırma için adım adım
  C# rehberi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: tr
lastmod: 2026-09-11
og_description: Aspose.Words ile C#'ta Word belgesi oluşturun. Bu rehber, dikdörtgen
  şekli eklemeyi, şekil boyutunu ayarlamayı ve şekil boyutlarını programlı olarak
  yönetmeyi gösterir.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Şekillerle Word belgesi oluşturma – Aspose.Words C# öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Aspose.Words kullanarak C#'ta şekiller içeren Word belgesi nasıl oluşturulur
url: /tr/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile C# kullanarak şekiller içeren Word belgesi nasıl oluşturulur

Özel grafikler içeren bir **create word document** oluşturmanız gerekiyorsa, bunu tamamen kod içinde yapabilirsiniz. Bu öğretici, bir Word dosyası oluşturma, bir dikdörtgen şekli ekleme ve şeklin her boyutunu kontrol etme sürecinde size rehberlik eder. Sonunda, herhangi bir .NET projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız.

Aspose.Words 13.9 örneği kullanılmıştır, ancak kavramlar daha sonraki sürümlerde de geçerlidir. Aspose drawing API'si ile ilgili önceden bir deneyim gerekmiyor—sadece temel C# bilgisi yeterlidir.

## Önkoşullar

- .NET 6.0 veya daha yeni bir sürüm yüklü  
- Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`)  
- Visual Studio 2022 gibi bir IDE (C# destekleyen herhangi bir editör çalışır)  

Bu araçları hazır bulundurmak, ek yapılandırma gerektirmeden kodu hemen çalıştırmanızı sağlar.

## Adım 1: Belgeyi ve builder'ı başlatma – word document temel oluşturma

İlk işlem, bir `Document` nesnesi ve bir `DocumentBuilder` örneği oluşturmaktır. `Document`, dosyanın kendisini temsil ederken, `DocumentBuilder` içerik eklemek için akıcı bir API sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Neden Önemlidir:**  
Belgeyi önceden oluşturmak, size temiz bir tuval sağlar. Builder'ın imleci ilk paragrafta başlar; burada daha sonra **create shapes in word** işlemini gerçekleştireceğiz.

## Adım 2: Birden fazla grafik tutmak için GroupShape oluşturma

`GroupShape`, bir konteyner gibi davranır; tüm grubu tek bir birim olarak taşıyabilir, döndürebilir veya yeniden boyutlandırabilirsiniz. Burada, konteynerin genişliğini ve yüksekliğini puan cinsinden tanımlıyoruz (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Neden Önemlidir:**  
Şekilleri gruplamak, yerleşim yönetimini basitleştirir. Daha sonra daha fazla şekil eklemeniz (örneğin, daireler veya metin kutuları) gerekirse, bunlar grubun konumunu ve ölçeklendirmesini miras alır.

## Adım 3: Bir dikdörtgen şekli oluşturma ve boyutlarını yapılandırma

Şimdi gerçek dikdörtgeni ekliyoruz. `Shape` yapıcı metodu, belge referansını ve şekil tipini gerektirir. Oluşturduktan sonra açıkça **set shape size** ve **set shape dimensions** ayarları yapılır.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Neden Önemlidir:**  
Genişlik, yükseklik, sol ve üst değerlerini belirlemek, şekil üzerinde piksel‑tam kontrol sağlar. Bu, belgenin bir tasarım spesifikasyonuna veya basılı bir forma uyması gerektiğinde çok önemlidir.

## Adım 4: Dikdörtgeni ekleyerek grubu birleştirme

Dikdörtgeni `GroupShape`'a eklemek, onu bir çocuk düğüm yapar. Grubu belgeye eklemeden önce ihtiyacınız kadar çocuk ekleyebilirsiniz.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**İpucu:** İkinci bir şekil eklemeyi planlıyorsanız, aynı şekilde oluşturup `group.AppendChild(secondShape)` çağırın. Tüm çocuklar, grubun koordinat sistemini paylaşır.

## Adım 5: Gruplandırılmış şekli belgeye ekleme ve kaydetme

Grup tamamen oluşturulduğunda, onu mevcut paragraf içine yerleştiririz. Builder'ın `CurrentParagraph` özelliği, temel düğüm ağacına doğrudan erişim sağlar.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Neden Önemlidir:**  
Grubu bir paragrafa eklemek, şeklin metin akışı içinde satır içi görünmesini sağlar. Belgeyi kaydetmek, **create word document** işlemini tamamlar.

## Ortak varyasyonlar ve uç durumlar

| Senaryo | Ayarlama |
|----------|------------|
| **Farklı sayfa yönlendirmesi** | Grubu oluşturmadan önce `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` ayarlayın. |
| **Birden fazla dikdörtgen** | Ek `Shape` nesneleri oluşturun ve her biri için `group.AppendChild(newRect)` çağırın. |
| **İçeriğe göre dinamik boyut** | Genişlik/yüksekliği görüntü boyutlarından veya metin ölçümlerinden hesaplayın, ardından `rectangle.Width` / `rectangle.Height` değerlerine atayın. |
| **PDF olarak dışa aktar** | `doc.Save` işleminden sonra `doc.Save("GroupShape.pdf", SaveFormat.Pdf);` çağırın. |
| **Eski Word sürümleriyle uyumluluk** | Word 97‑2003 uyumluluğu için `Docx` yerine `SaveFormat.Doc` kullanarak kaydedin. |

## Tam, çalıştırılabilir örnek

Aşağıda, kopyalayıp yapıştırıp çalıştırabileceğiniz tam program bulunmaktadır. Tüm `using` yönergelerini, bir `Main` giriş noktasını ve her satırı açıklayan yorumları içerir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Beklenen çıktı:**  
*GroupShape.docx* dosyasını açtığınızda, ilk sayfa sol/üst kenardan 50 pt uzaklıkta konumlandırılmış gri kenarlı bir dikdörtgen gösterir; dikdörtgen kendisi grup içinde 10 pt içeri kaydırılmıştır. Boyutlar, kodda ayarlanan değerlerle eşleşir.

## Sonuç

Artık Aspose.Words kullanarak **create word document**, **add rectangle shape** ve tam olarak **set shape size** ve **set shape dimensions** nasıl yapılacağını biliyorsunuz. Gruplandırılmış şekil yaklaşımı, yerleşiminizi esnek tutar ve ek grafikler veya metin kutuları gibi gelecekteki genişletmelere hazır hale getirir.

Sonraki adımda, daireler, oklar veya özel SVG yolları için **create shapes in word** gibi ilgili konuları keşfedin ve **set shape fill color** veya **apply rotation** nasıl yapılacağını öğrenin. Farklı ölçü birimleriyle deney yaparak Word'ün puanları santimetrelere göre nasıl işlediğini görün ve kodu daha büyük belge‑oluşturma hatlarına entegre edin.

Kodlamaktan keyif alın ve bu deseni karşılaştığınız herhangi bir otomatik raporlama veya form doldurma senaryosuna uyarlamaktan çekinmeyin!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalarla tam çalışan kod örnekleri içerir ve ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olur.

- [C# kullanarak Word'de dikdörtgen şekli oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Gölgelendirilmiş Dikdörtgen Şekilli Boş Word Belgesi Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Şekil Gölge Öğreticisi – C#'ta Word Şekline Gölge Ekleme](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}