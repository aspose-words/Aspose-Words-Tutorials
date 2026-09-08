---
category: general
date: 2026-09-08
description: DocumentBuilder ile Word’de şekilleri nasıl gruplayacağınızı öğrenin,
  boş bir Word belgesi oluşturun ve sadece birkaç satır C# kodu ile bir dikdörtgen
  şekli ekleyin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: tr
lastmod: 2026-09-08
og_description: DocumentBuilder kullanarak Word’de şekilleri gruplayın. Bu öğreticide
  boş bir Word belgesi oluşturma, bir dikdörtgen şekli ekleme ve şekilleri bir GroupShape
  içinde birleştirme gösterilmektedir.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: DocumentBuilder ile Word’de Şekilleri Gruplama – tam C# örneği
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: DocumentBuilder ile Word’de Şekilleri Gruplama – Adım Adım Kılavuz
url: /tr/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de DocumentBuilder Kullanarak Şekilleri Gruplama – adım adım rehber

If you need to **group shapes in Word** programmatically, this tutorial shows a complete solution in C#. You’ll see how to **create a blank Word doc**, use **DocumentBuilder**, and **insert a rectangle shape** before grouping it with an ellipse. The result is a single `GroupShape` that you can move, resize, or style as one object.

Bu rehber, Aspose.Words for .NET kütüphanesini kullanarak gruplanmış grafiklerle bir Word belgesi oluşturmak için bilmeniz gereken her şeyi kapsar. Makalenin sonunda, bir dikdörtgen ve bir elipsi tek bir şekil içinde birleştiren `GroupedShapes.docx` dosyasını üreten çalıştırılabilir bir projeye sahip olacaksınız.

## Önkoşullar

- .NET 6.0 veya daha yenisi (kod .NET Framework 4.7.2+ ile de çalışır)
- Aspose.Words for .NET NuGet paketi (`Aspose.Words`) – sürüm 23.12 veya daha yeni
- Visual Studio 2022 veya Visual Studio Code gibi bir C# IDE'si
- C# sözdizimi ve nesne‑yönelimli programlama hakkında temel bilgi

> **İpucu:** NuGet paketini komut satırından kurarak projenizi düzenli tutun:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Adım 1: Boş bir Word belgesi oluşturma

İlk işlem, boş bir Word dosyasını temsil eden bir `Document` nesnesi ve içerik eklemenizi sağlayan bir `DocumentBuilder` örneği oluşturmaktır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Neden önemli:** `Document`, dosya konteynerini sağlar, `DocumentBuilder` ise metin, resim ve şekil eklemek için akıcı bir API sunar. `DocumentBuilder` olmadan belge ağacını manuel olarak manipüle etmeniz gerekir ki bu hata yapmaya açıktır.

## Adım 2: Dikdörtgen şekli ekleme

Dikdörtgen, diyagramlar için yaygın bir yapı taşır. `InsertShape` yöntemini `ShapeType.Rectangle` ile kullanın ve genişlik ve yüksekliği puan cinsinden belirtin (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Neden önemli:** `Left` ve `Top` ayarları, dikdörtgeni sayfada tam olarak konumlandırır; bu, daha sonra diğer şekillerle grupladığınızda çok önemlidir. `InsertShape` yöntemi şekli otomatik olarak geçerli paragrafa ekler.

## Adım 3: Elips şekli ekleme

Sonra, dikdörtgenin yanına oturacak bir elips ekleyin.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Neden önemli:** Farklı bir `ShapeType` kullanmak, aynı `DocumentBuilder` API'sinin çeşitli grafikler oluşturabileceğini gösterir. Elipsi dikdörtgenle çakışacak şekilde konumlandırmak, gruplama etkisini belirgin kılar.

## Adım 4: İki şekli gruplama

`GroupShape`, bir kapsayıcı gibi davranır. Dikdörtgen ve elipsi çocuk olarak ekleyerek, tek bir nesne gibi hareket ederler.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Neden önemli:** `Bounds` özelliği, Word'e grubun sayfada nerede bulunduğunu söyler. Çocuk şekilleri ekleyerek, bireysel biçimlendirmelerini korur ve toplu dönüşümler (taşıma, döndürme, yeniden boyutlandırma) yapmanıza olanak tanır.

## Adım 5: Belgeyi kaydetme

Son olarak, belgeyi diske yazın. Yolu istediğiniz herhangi bir klasöre değiştirebilirsiniz.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

`GroupedShapes.docx` dosyasını Microsoft Word'de açtığınızda, bir dikdörtgen ve bir elipsin birlikte gruplandığını göreceksiniz. Grubu seçmek, her iki şekli de vurgular ve onları tek bir birim olarak sürüklemenize veya yeniden boyutlandırmanıza izin verir.

### Beklenen çıktı

- **GroupedShapes.docx** adlı bir Word dosyası
- İlk sayfa, konumu (50, 50) olan bir **dikdörtgen** (100 pt × 50 pt) içerir
- Konumu (200, 70) olan bir **elips** (80 pt × 80 pt)
- Her iki şekil de 300 pt × 200 pt boyutunda bir sınırlama kutusuna sahip **GroupShape**'ın parçasıdır

## Yaygın varyasyonlar ve kenar durumları

| Senaryo | Ayarlama |
|----------|------------|
| **Farklı sayfa boyutu** | Şekilleri eklemeden önce `document.Sections[0].PageSetup.PageWidth` ve `PageHeight` ayarlayın. |
| **İkiden fazla şekil** | Ek `Shape` nesneleri oluşturun ve her biri için `groupShape.AppendChild(newShape)` çağırın. |
| **Dolgu rengi uygula** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Grubu döndür** | `groupShape.Rotation = 45;` (derece) |
| **PDF olarak dışa aktar** | DOCX'i kaydettikten sonra `document.Save("GroupedShapes.pdf");` çağırın. |

## Tam kaynak kodu (çalıştırmaya hazır)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Kodu yeni bir konsol projesine kopyalayın, Aspose.Words NuGet paketini geri yükleyin ve çalıştırın. Konsol dosya konumunu onaylayacak ve dosyayı açtığınızda gruplanmış grafikleri gösterecektir.

## Sonuç

Artık Aspose.Words `DocumentBuilder` ile **Word'de şekilleri nasıl gruplayacağınızı** biliyorsunuz. Öğretici, bir **boş Word belgesi** oluşturmayı, **dikdörtgen şekli eklemeyi**, bir elips eklemeyi ve bunları bir `GroupShape` içinde birleştirmeyi adım adım gösterdi. Bu temelle, C#'tan doğrudan daha zengin diyagramlar, akış şemaları veya özel grafikler oluşturabilirsiniz.

### Sıradaki adım?

- **DocumentBuilder**'ı tablolar, başlıklar ve altbilgiler için nasıl kullanacağınızı keşfedin.
- **Insert rectangle shape Word** tekniklerini metin kutuları ile birleştirerek açıklamalı diyagramlar oluşturun.
- **Create blank word doc**'u otomatik rapor oluşturma için bir şablon olarak kullanın.

Renkler, degradeler ve ek şekillerle denemeler yapmaktan çekinmeyin. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for .NET Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET Kullanarak Word Belgelerine Şekil Ekleme](/words/english/net/working-with-shapes/insert-shape/)
- [C# ile Word'de Dikdörtgen Şekli Oluşturma – Adım Adım Rehber](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}