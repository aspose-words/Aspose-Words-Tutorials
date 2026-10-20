---
category: general
date: 2026-08-04
description: C# ile bir Word belgesine dikdörtgen şekli ekleyin. Word'de şekilleri
  nasıl gruplayacağınızı öğrenin, belgeyi docx olarak kaydedin ve gelişmiş düzenler
  için DocumentBuilder'ı kullanın.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: tr
lastmod: 2026-08-04
og_description: C# kullanarak bir Word dosyasına dikdörtgen şekli ekleyin ve ardından
  gelişmiş düzenler için şekilleri gruplayın. Bu öğreticide ayrıca belgeyi docx olarak
  kaydetme ve DocumentBuilder'ı verimli bir şekilde kullanma konuları ele alınmaktadır.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Word'de Dikdörtgen Şekli Ekleme – C# Adım Adım Rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# kullanarak Word'e dikdörtgen şekli ekleme – tam rehber
url: /tr/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# kullanarak Word'e dikdörtgen şekli ekleme – tam kılavuz

C# kullanarak bir Word belgesine **dikdörtgen şekli eklemeniz** gerekiyorsa, bu öğretici tam olarak nasıl yapılacağını gösterir. Ayrıca **Word'de şekilleri gruplama**, **belgeyi docx olarak kaydetme** ve **temiz, sürdürülebilir kod için Builder kullanma** konularını da öğreneceksiniz.

Şekillerle çalışmak, raporlar, sertifikalar veya özel düzenler programlı olarak oluşturulurken yaygın bir gereksinimdir. Bu kılavuzun sonunda, bir dikdörtgen oluşturan, bir elips ekleyen, bunları gruplayan ve sonucu bir DOCX dosyası olarak kaydeden tamamen çalıştırılabilir bir örnek elde edeceksiniz.

## Önkoşullar

* .NET 6.0 veya daha yeni bir sürüm yüklü  
* Visual Studio 2022 (veya C# destekleyen herhangi bir IDE)  
* **Aspose.Words for .NET** kütüphanesi (NuGet üzerinden temin edilebilir)  

Kütüphaneyi aşağıdaki komutla ekleyebilirsiniz:

```bash
dotnet add package Aspose.Words
```

## DocumentBuilder ile dikdörtgen şekli ekleme

İlk adım, yeni bir `Document` ve bir `DocumentBuilder` oluşturmaktır. Builder, şekiller dahil içerik eklemek için akıcı bir API sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` örneği, **dikdörtgen şekli eklemek** ve diğer öğeleri eklemek için kullanacağınız temel nesnedir. Belge içindeki mevcut imleç konumunu izler, böylece eklemeler tam olarak ihtiyacınız olan yere yapılır.

## Dikdörtgen şekli nasıl eklenir

Builder hazır olduğunda, `InsertShape` metodunu çağırın. `ShapeType`, genişlik ve yüksekliği puan cinsinden belirtirsiniz (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Neden önemli*: `FillColor` ve `StrokeColor` ayarlamak, dikdörtgeni görsel olarak ayırt edilebilir kılar; bu, daha sonra diğer şekillerle grupladığınızda yardımcı olur.

## Word'de şekilleri nasıl gruplarsınız

Şekilleri gruplamak, birden fazla nesneyi tek bir varlık gibi taşımanıza, döndürmenize veya biçimlendirmenize olanak tanır. Dikdörtgeni ekledikten sonra, başka bir şekil (bu örnekte bir elips) ekleyin ve ardından bir `GroupShape` oluşturun.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

`InsertGroupShape` çağrısı, herhangi bir sayıda alt şekil tutabilen bir yer tutucu oluşturur. Dikdörtgeni ve elipsi ekleyerek, etkili bir şekilde **Word'de şekilleri gruplarsınız**. Grup, tek bir şekil gibi davranır—konumunu yeniden ayarlayabilir, kenarlık ekleyebilir veya boyutunu değiştirebilirsiniz; bu, her bir alt şeklin iç düzenini etkilemez.

### Pro ipucu

Grupladıktan sonra, grubun sayfaya göre konumunu değiştirebilirsiniz:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Belgeyi docx olarak kaydetme

Şekiller düzenlendikten sonra, dosyayı kalıcı hale getirmeniz gerekir. `Document.Save` yöntemi, dosya uzantısından formatı otomatik olarak belirler. **Belgeyi docx olarak kaydetmek** için, `.docx` ile biten bir yol verin.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

Programı çalıştırmak `output.docx` dosyasını oluşturur. Dosyayı Microsoft Word'de açtığınızda, birlikte gruplanmış açık mavi bir dikdörtgen ve açık mercan bir elips göreceksiniz. Gruba tıklayarak tek bir nesne gibi taşıyabilirsiniz.

## DocumentBuilder'ı etkili bir şekilde nasıl kullanırsınız

`DocumentBuilder`, sadece bir şekil ekleyici değildir; aynı zamanda metin, tablolar, başlıklar ve altbilgileri de yönetir. Şekil oluşturmayı metinle birleştirirken, içeriği başka bir yere eklemeniz gerektiğinde imleci sıfırlamayı unutmayın:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Builder'ın durumunu açık tutmak, yanlışlıkla üzerine yazılmaları önler ve kodun bakımını kolaylaştırır.

## Kenar durumları ve varyasyonlar

| Durum | Önerilen yaklaşım |
|-----------|----------------------|
| **İki'den fazla şekil** | Her şekli ekleyin, ardından kaydetmeden önce her şekil için `AppendChild` çağırın. |
| **İç içe gruplar** | Bir grup oluşturun, şekilleri ekleyin, ardından bu grubu başka bir `GroupShape` içine ekleyin. |
| **Farklı ölçüm birimleri** | `builder.ConvertPixelsToPoints` kullanın, eğer boyutlar piksel cinsindense. |
| **Eski Word sürümleriyle uyumluluk** | Uzantıyı değiştirerek `.doc` olarak kaydedin; çoğu şekil özelliği hâlâ çalışır. |

## Tam çalışan örnek

Aşağıda, yeni bir konsol projesine kopyalayıp yapıştırabileceğiniz tam program bulunmaktadır. Ek bir kod parçacığı gerekmez.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Beklenen sonuç**: `output.docx` dosyasını açtığınızda, birlikte gruplanmış açık mavi bir dikdörtgen ve açık mercan bir elips görürsünüz; sol kenar boşluğundan 150 pt, üstten 100 pt konumlandırılmıştır. Başlık, grubun altında görünür.

## Sonuç

Artık C# kullanarak bir Word dosyasına **dikdörtgen şekli eklemeyi**, **Word'de şekilleri gruplamayı** ve Aspose.Words `DocumentBuilder` ile **belgeyi docx olarak kaydetmeyi** biliyorsunuz. Bu adımları ustalıkla uygulayarak, tamamen kod aracılığıyla karmaşık düzenler—sertifikalar, raporlar veya özel formlar—oluşturabilirsiniz.

Sonra, **metin kutuları ekleme**, **tablolarla çalışma** veya **PDF'ye dışa aktarma** gibi ilgili konuları keşfedin. Bunların her biri, az önce uyguladığınız aynı `DocumentBuilder` temellerine dayanır.

Word belgelerinizi otomatikleştirmeye hazır mısınız? Örneği daha fazla şekil ekleyerek, degrade uygulayarak veya veriler üzerinde döngü kurarak tek bir çalıştırmada tam bir rapor üretmeyi deneyin. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for .NET Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET Kullanarak Word Belgelerine Şekil Ekleme](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words ile Word'de Dikdörtgen Şekli Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}