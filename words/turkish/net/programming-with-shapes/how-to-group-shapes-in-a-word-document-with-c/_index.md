---
category: general
date: 2026-08-14
description: C# kullanarak bir Word belgesinde şekilleri nasıl gruplayacağınızı öğrenin.
  Word belgesi oluşturmayı, dikdörtgen şekli eklemeyi, Word’de şekilleri gruplamayı
  ve belgeyi docx olarak kaydetmeyi keşfedin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: tr
lastmod: 2026-08-14
og_description: C# kullanarak bir Word belgesinde şekilleri nasıl gruplayacağınızı
  öğrenin. Word dosyası oluşturmak, dikdörtgen şekli eklemek, Word’de şekilleri gruplamak
  ve sonucu docx olarak kaydetmek için bu kapsamlı öğreticiyi izleyin.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: C# ile bir Word belgesindeki şekilleri gruplama – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: C# ile bir Word belgesindeki şekilleri nasıl gruplayabilirsiniz
url: /tr/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile bir Word belgesinde şekilleri nasıl gruplayabilirsiniz?

Bir Word belgesinde **şekilleri gruplama** ihtiyacınız varsa, bu rehber C# ve Aspose.Words kütüphanesini kullanarak tam adımları gösterir. Word belgesi oluşturma, dikdörtgen şekil ekleme, Word’de şekilleri gruplama ve sonunda **belgeyi docx olarak kaydetme** işlemlerini tek bir çalıştırılabilir programda göreceksiniz.

Şekilleri oluşturmak ve manipüle etmek, raporlar, sözleşmeler veya pazarlama broşürleri gibi belgeleri programlı olarak üretirken yaygın bir gereksinimdir. Bu öğreticinin sonunda, herhangi bir .NET projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

- .NET 6.0 veya daha yeni bir sürüm  
- Visual Studio 2022 (veya .NET destekleyen herhangi bir IDE)  
- Aspose.Words for .NET lisansı (veya ücretsiz deneme)  
- C# sözdizimi hakkında temel bilgi  

`Aspose.Words` dışındaki ek NuGet paketlerine ihtiyaç yoktur.

## Word belgesinde şekilleri nasıl gruplarsınız

Çözümün temeli beş adımlı bir süreçtir. Her adım ayrıntılı olarak açıklanmıştır ve makalenin sonunda tam kaynak kodu verilmiştir.

### Adım 1: Yeni boş bir belge oluşturun

Programlı olarak **Word belgesi oluşturmak** istediğinizde ilk yaptığınız şey bir `Document` nesnesi örneklemektir. Bu nesne, bellekteki tüm .docx dosyasını temsil eder.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Neden önemli:** `DocumentBuilder`, alttaki düğüm ağacını manuel olarak yönetmeden metin, tablo ve şekil eklemenizi sağlayan yüksek seviyeli bir yardımcıdır.

### Adım 2: Dikdörtgen şekil ekleyin

**Dikdörtgen şekil ekleme** işlemini göstermek için `InsertShape` metodunu kullanıyoruz. Dikdörtgen, grubun ilk üyesi olacaktır.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Neden önemli:** Şekiller ekleme noktasına göre konumlandırılır. Dolgu rengi ayarlamak, oluşturulan belgeyi açtığınızda şekli görmenizi sağlar.

### Adım 3: Elips şekil ekleyin

Şimdi **elips şekil ekleme** (API’da adı `Ellipse`) yapıyoruz. Bu, grubun ikinci üyesi olacaktır.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Neden önemli:** Elipsi dikdörtgenin hemen ardından ekleyerek, iki şekil aynı paragrafta yer alır ve bu da daha sonraki gruplamayı basitleştirir.

### Adım 4: Dikdörtgen ve elipsi gruplayın

Şimdi, Word belgesinde **şekilleri nasıl gruplayabilirsiniz** sorusunun merkezine cevap veriyoruz. Aspose.Words, bir grup kapsayıcısı oluşturmak için `AppendGroupShape` sağlar ve ardından bu kapsayıcı üzerinde `Group()` metodunu çağırırsınız.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Neden önemli:** Gruplandıktan sonra, `groupedShape` üzerine uygulanan herhangi bir dönüşüm (taşıma, yeniden boyutlandırma, döndürme) otomatik olarak hem dikdörtgeni hem de elipsi etkiler. Bu, oluşturulan belgelerde düzen tutarlılığını sağlamak için kritiktir.

### Adım 5: Belgeyi DOCX dosyası olarak kaydedin

Son adım **belgeyi docx olarak kaydetmek**tir. İstediğiniz herhangi bir yolu seçebilirsiniz; örnek `"YOUR_DIRECTORY"` adlı bir yer tutucu kullanır; bunu gerçek bir klasörle değiştirmeniz gerekir.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Neden önemli:** DOCX olarak kaydetmek, grup meta verilerini korur; böylece dosyayı Microsoft Word’de açtığınızda dikdörtgen ve elips tek bir nesne gibi görünür.

## Tam, çalıştırılabilir örnek

Aşağıda beş adımı birleştiren tam program yer almaktadır. Yeni bir console projesine kopyalayın, Aspose.Words NuGet paketini geri yükleyin ve çalıştırın.

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
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### Beklenen çıktı

`groupedShapes.docx` dosyasını Microsoft Word’de açtığınızda, hafif mavi bir dikdörtgen ve hafif mercan renginde bir elipsin birlikte kilitlenmiş olduğunu göreceksiniz. Her iki şekle de tıkladığınızda ikisi birden seçilir; böylece tek bir birim gibi taşıyabilir veya yeniden boyutlandırabilirsiniz.

## Yaygın sorular ve kenar durumları

| Soru | Cevap |
|----------|--------|
| **İki şekilden daha fazlasını gruplayabilir miyim?** | Evet. `AppendGroupShape` metoduna istediğiniz sayıda `Shape` nesnesi geçebilirsiniz. Metod bir dizi kabul eder, bu yüzden koleksiyonu dinamik olarak oluşturabilirsiniz. |
| **Grubu bir tablo hücresine bağlamam gerekirse?** | Şekilleri hücrenin paragrafına ekleyin, ardından o paragrafta `AppendGroupShape` çağırın. Grup, hücrenin bağlamasını devralır. |
| **Gruplama alttaki XML’i etkiler mi?** | Aspose.Words, çocuk şekilleri içeren bir `<w:grpSp>` öğesi yazar. Word bu öğeyi bir grup olarak tanır ve göreceli konumlandırmayı korur. |
| **Daha sonra grubu nasıl çözebilirim?** | `groupedShape.Ungroup()` metodunu çağırın; metod, ayrı ayrı manipüle edebileceğiniz bireysel şekilleri döndürür. |
| **Çok sayıda şekli gruplarken performans etkisi olur mu?** | Gruplama kendisi pahalı değildir, ancak yüzlerce şekli içeren çok büyük grupların işlenmesi dosya boyutunu artırabilir. Boyut sorunu ortaya çıkarsa görüntüleri düzleştirmeyi düşünün. |

## Profesyonel ipuçları

- **Kesin konumları ayarlayın** (`Left`, `Top`); gruplamadan önce hassas hizalama gerekiyorsa bu faydalıdır.  
- **`Shape.WrapType = WrapType.Inline`** kullanın; grup bir paragraf öğesi gibi davranır, yüzen bir nesne olmaz.  
- **Gruba bir çizgi stili uygulayın** (`groupedShape.LineFormat`) ve tüm koleksiyona kenarlık ekleyin.  
- **Grubu yeniden kullanın**: `Group()` metodundan sonra `groupedShape`’i klonlayabilir ve klonu belge içinde başka bir yere ekleyebilirsiniz.

## Sonraki adımlar

Artık **Word belgesinde şekilleri nasıl gruplayacağınızı** bildiğinize göre, aşağıdaki ilgili konuları keşfedebilirsiniz:

- **Dikdörtgen şekil ekleme** ve şeklin içine özel metin veya resim yerleştirme.  
- **Grupları iç içe geçirerek** karmaşık diyagramlar oluşturma (grubu grup içinde).  
- **Belgeyi PDF olarak dışa aktarma** ve şekil gruplamasını koruma (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

Bu konular, burada ele aldığımız temeller üzerine inşa edilmiştir; böylece Word otomasyon araç setinizi genişletmek için iyi bir konumdasınız.

## Sonuç

Bu öğreticide, C# kullanarak **şekilleri nasıl gruplayacağınızı** Word belgesinde gösterdik. **Word belgesi oluşturma**, **dikdörtgen şekil ekleme**, **Word’de şekilleri gruplama** ve sonunda **belgeyi docx olarak kaydetme** konularını öğrendiniz. Tam, çalıştırılabilir örnek ve pratik ipuçları sayesinde, şekil gruplamayı herhangi bir belge‑oluşturma iş akışına entegre edebilirsiniz. İyi kodlamalar!

## Bir sonraki öğrenmeniz gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan yakın konuları kapsar. Her kaynak, adım adım açıklamalar ve tam çalışan kod örnekleri içerir; böylece API özelliklerini daha iyi kavrayabilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Word Belgesinde Grup Şekli Oluşturma Aspose.Words for .NET Kullanarak](/words/english/net/working-with-shapes/add-group-shape/)
- [Word Belgelerine Şekil Ekleme Aspose.Words for .NET Kullanarak](/words/english/net/working-with-shapes/insert-shape/)
- [C# ile Word'de Dikdörtgen Şekil Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}