---
category: general
date: 2026-09-14
description: Aspose.Words kullanarak C#'ta etiket eklemeyi, şekil eklemeyi, grup oluşturmayı
  ve belgeyi DOCX olarak kaydetmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert tag
- save document as docx
- how to create group
- how to add shapes
- how to save docx
language: tr
lastmod: 2026-09-14
og_description: Aspose.Words kullanarak etiket ekleme, şekil ekleme, grup oluşturma
  ve belgeyi DOCX olarak kaydetme. Adım adım rehberi izleyin.
og_image_alt: Diagram showing how to insert tag inside a grouped shape before saving
  as DOCX
og_title: C# ile bir DOCX dosyasına etiket ekleme ve gruplanmış şekil oluşturma
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to insert tag, add shapes, create a group, and save document
    as DOCX using Aspose.Words in C#.
  headline: How to insert tag and create a group shape in a DOCX
  type: TechArticle
tags:
- Aspose.Words
- C#
- DOCX manipulation
title: DOCX'te etiket ekleme ve grup şekli oluşturma
url: /tr/net/programming-with-shapes/how-to-insert-tag-and-create-a-group-shape-in-a-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX'te etiket ekleme ve grup şekli oluşturma

Karmaşık bir düzen oluştururken **etiket eklemenin nasıl yapılacağını** öğrenmeniz gerekiyorsa, bu rehber size eksiksiz, çalıştırılabilir bir çözüm gösterir. Şekilleri nasıl ekleyeceğinizi, bir grup nasıl oluşturacağınızı ve sonunda Aspose.Words for .NET ile **belgeyi DOCX olarak kaydetmeyi** göreceksiniz.

Belge oluşturma genellikle metin etiketlerini grafik öğelerle karıştırmayı gerektirir. Bu öğreticide **etiket eklemenin nasıl yapılacağını**, **şekil eklemeyi**, **grup oluşturmayı** ve **docx'i kaydetmenin** doğru yolunu öğrenecek ve dosyanın Word'de kalite kaybı olmadan açılmasını sağlayacaksınız.

## Önkoşullar

- .NET 6.0 veya üzeri (kod .NET Framework 4.7+ ile de çalışır)
- Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`)
- C# sözdizimi hakkında temel bilgi
- Visual Studio veya VS Code gibi bir IDE

Ek bir kütüphane gerekmez; tüm örnek tek bir NuGet referansı ile çalışır.

## Grup oluşturma ve şekil ekleme

İlk mantıksal adım, birden fazla şekli tutacak bir **grup** oluşturmaktır. Gruplama, şekilleri daha sonra taşıdığınızda veya döndürdüğünüzde birlikte kalmalarını sağlar.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

// 1️⃣ Create an empty document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// 2️⃣ Build a GroupShape (200 × 200 points) and set its bounds
GroupShape groupShape = new GroupShape(document, 200, 200);
groupShape.Bounds = new RectangleF(50, 50, 200, 200);

// 3️⃣ Add a rectangle shape
groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
{
    Width = 80,
    Height = 80,
    Left = 0,
    Top = 0
});

// 4️⃣ Add an ellipse shape next to the rectangle
groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
{
    Width = 80,
    Height = 80,
    Left = 100,
    Top = 0
});
```

**Neden önemli?**  
`GroupShape` bir kapsayıcı gibi davranır. Grubu daha sonra taşıdığınızda, dikdörtgen ve elips birlikte hareket eder ve göreceli konumlarını korur. Bu, aynı mantıksal bloğa ait birden fazla grafiği yönetmenin önerilen yoludur.

## Belge içinde etiket ekleme

Grup hazır olduğuna göre, **etiket ekleyebilir** (StructuredDocumentTag, aynı zamanda SDT olarak da bilinir) gruptan hemen sonra. Etiket düz metin, zengin metin veya hatta yinelenen içerik tutabilir.

```csharp
// 5️⃣ Insert the group at the current builder position
builder.InsertNode(groupShape);

// 6️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and write content
builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
builder.Writeln("Content inside the SDT");
```

**Neden StructuredDocumentTag kullanmalısınız:**  
Bir SDT, Word'ün içerik denetimleri, veri bağlama veya form doldurma senaryoları için tanıyabileceği anlamsal bir işaretçi sağlar. `InsertStructuredDocumentTag` kullanarak **etiket eklemenin nasıl yapılacağını** açıkça belirtir ve bu, Microsoft Word'de sonraki düzenlemelere dayanıklı bir şekilde kalır.

## docx'i kaydetme ve sonucu doğrulama

Son adım belgeyi kalıcı hale getirmektir. Aşağıdaki kod, **belgeyi docx olarak kaydetmenin** doğru yolunu ve çıktı dosyasının nerede bulunacağını gösterir.

```csharp
// 7️⃣ Save the document to the file system
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "GroupAndSDT.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Word'de *GroupAndSDT.docx* dosyasını açtığınızda, bir grup dikdörtgen‑elips grafiği ve ardından **MyTag** başlıklı düz metin içerik denetimi görmelisiniz; bu denetim “Content inside the SDT” satırını içerir.

### Beklenen çıktı

- Sayfanın (50, 50) konumunda 200 × 200 puan bir grup.
- Grup içinde: solda mavi bir dikdörtgen ve sağda bir elips (varsayılan renkler).
- Grubun hemen altında: **MyTag** etiketiyle bir içerik denetimi ve “Content inside the SDT” metni.

## Tam, çalıştırılabilir örnek

Aşağıda, bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz eksiksiz program yer almaktadır. Gerekli tüm `using` yönergelerini, hata yönetimini ve her adımı açıklayan yorumları içerir.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeWordsGroupAndTag
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document and a DocumentBuilder to work with it
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Build a GroupShape (200x200) and define its bounds
            GroupShape groupShape = new GroupShape(document, 200, 200);
            groupShape.Bounds = new RectangleF(50, 50, 200, 200);

            // Add a rectangle to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
            {
                Width = 80,
                Height = 80,
                Left = 0,
                Top = 0
            });

            // Add an ellipse to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
            {
                Width = 80,
                Height = 80,
                Left = 100,
                Top = 0
            });

            // Insert the group into the document at the current builder position
            builder.InsertNode(groupShape);

            // Insert a plain‑text StructuredDocumentTag (SDT) and write some content inside it
            builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
            builder.Writeln("Content inside the SDT");

            // Save the resulting document
            string outputPath = Path.Combine(
                Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
                "GroupAndSDT.docx");

            document.Save(outputPath);
            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

Programı çalıştırın, Masaüstünüzdeki konuma gidin ve *GroupAndSDT.docx* dosyasına çift tıklayarak grup ve etiketin açıklandığı gibi göründüğünü doğrulayın.

## Yaygın sorular ve kenar durumları

| Soru | Cevap |
|----------|--------|
| **Gruba iki şekilden fazla ekleyebilir miyim?** | Evet. Grubu eklemeden önce her ek şekil için `groupShape.AppendChild(new Shape(...))` çağırın. |
| **Düz metin yerine zengin metin etiketine ihtiyacım olursa ne yapmalıyım?** | `InsertStructuredDocumentTag` içinde `StructuredDocumentTagType.RichText` kullanın. |
| **Dikdörtgenin veya elipsin rengini nasıl değiştiririm?** | Her `Shape` örneğinde `FillColor` özelliğini ayarlayın, örn. `shape.FillColor = Color.LightBlue;`. |
| **Tüm grubu döndürmek mümkün mü?** | Düğümü eklemeden önce `groupShape.Rotation = 45;` (derece) ayarlayın. |
| **Herhangi bir nesne üzerinde `Dispose()` çağırmam gerekiyor mu?** | Aspose.Words çoğu kaynağı dahili olarak yönetir; kısa ömürlü bir konsol uygulamasında `Document`'i dispose etmek isteğe bağlıdır. |

## DOCX dosyalarını kaydetme için en iyi uygulamalar

- **Her zaman mutlak bir yol** (veya iyi tanımlanmış bir göreli yol) kullanın `document.Save` çağırırken. Bu, belirsiz çalışma dizinlerinden kaynaklanabilecek “dosya bulunamadı” hatasını önler.
- Belgeyi HTTP üzerinden göndermeniz veya bir veritabanına kaydetmeniz gerekiyorsa, **akış kabul eden `Save` aşırı yüklemelerini** tercih edin.
- Eski Word sürümlerine (ör. Word 2003) hedeflemeniz gerekiyorsa **`CompatibilityOptions` ayarlayın**. Çoğu modern senaryo için varsayılan ayarlar yeterlidir.

## Sonraki adımlar

Artık **etiket eklemenin nasıl yapılacağını**, **şekil eklemeyi**, **grup oluşturmayı** ve **docx'i kaydetmeyi** bildiğinize göre, daha gelişmiş senaryoları keşfedebilirsiniz:

- Birden fazla grubu birleştirerek karmaşık diyagramlar oluşturun.
- Word şablonlarında veri bağlama için `StructuredDocumentTag` kullanın.
- Gruplanmış grafikleri koruyarak aynı belgeyi PDF olarak dışa aktarın (`document.Save("output.pdf")`).
- SDT içeriğini programlı olarak ayarlayarak form doldurmayı otomatikleştirin (`builder.MoveToDocumentEnd(); builder.Write("New value");`).

`ShapeType` değerleriyle (ör. `ShapeType.Polygon`, `ShapeType.Line`) deney yaparak bir `GroupShape` içinde nasıl davrandıklarını görün. Aynı desen tablolar, görseller veya birlikte tutmak istediğiniz diğer düğümler için de çalışır.

---

**Özet:** Bu öğreticide, bir grup şekil içinde **etiket eklemenin nasıl yapılacağını**, **şekil eklemeyi**, **grup oluşturmayı** ve Aspose.Words for .NET kullanarak **belgeyi docx olarak kaydetmenin** doğru yöntemini gösterdik. Artık programlı olarak zengin, etkileşimli DOCX dosyaları oluşturmak için sağlam bir temele sahipsiniz.

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [DOCX'ten Markdown Kaydetme – Adım Adım Kılavuz](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [DOCX Kurtarma – Aspose.Words Kullanarak Tam Kılavuz](/words/english/net/programming-with-loadoptions/how-to-recover-docx-complete-guide-using-aspose-words/)
- [DOCX'te Dilbilgisi Kontrolü – Aspose.Words ile gpt-4 turbo Kullanımı](/words/english/net/ai-powered-document-processing/how-to-check-grammar-in-docx-with-aspose-words-use-gpt-4-tur/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}