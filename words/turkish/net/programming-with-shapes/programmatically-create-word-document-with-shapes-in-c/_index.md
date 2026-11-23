---
category: general
date: 2026-11-22
description: C#'ta programlı olarak Word belgesi oluşturun, dikdörtgen şekli ekleyin,
  birden fazla şekil ekleyin ve şekilleri Aspose.Words kullanarak Word'e yazın.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: tr
lastmod: 2026-11-22
og_description: C#'ta dikdörtgen şekil ekleyerek, birden fazla şekil ekleyip, Aspose.Words
  kullanarak şekilleri Word'e yazarak programlı bir şekilde Word belgesi oluşturun.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: C#'ta şekiller içeren Word belgesini programlı olarak oluşturma
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: C#'ta şekillerle Word belgesini programlı olarak oluşturma
url: /tr/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile şekiller içeren Word belgesi programlı olarak oluşturma

Eğer **programlı olarak Word belgesi** oluşturmanız ve içinde özel grafikler bulunması gerekiyorsa, bu kılavuz Aspose.Words for .NET ile bunu nasıl yapacağınızı gösterir. Bir dikdörtgen şekli eklemeyi, ek şekiller eklemeyi, bunları gruplamayı ve sonunda şekilleri Word'e yazmayı birkaç satır C# koduyla öğreneceksiniz.

Grafik içeren bir Word dosyası oluşturmak artık manuel düzenleme veya makro betikleri gerektirmiyor. Bu öğreticinin sonunda, bir dikdörtgen ve bir elipsi birlikte gruplandıran, `.docx` dosyası üreten yeniden kullanılabilir bir metoda sahip olacaksınız; bu dosya sonraki işleme veya raporlamada kullanılabilir.

## Gereksinimler

- .NET 6.0 veya daha yeni bir sürüm (kod .NET Framework 4.6+ ile de çalışır)
- Aspose.Words for .NET (NuGet paketi `Aspose.Words`)
- Visual Studio 2022 gibi bir IDE (C# derleyebilen herhangi bir editör yeterlidir)

> **Pro ipucu:** Kodlamaya başlamadan önce `dotnet add package Aspose.Words` CLI komutuyla paketi kurun.

## Programlı olarak Word belgesi oluşturma – genel bakış

Genel akış üç mantıksal aşamadan oluşur:

1. Yeni bir `Document` ve bir `DocumentBuilder` **başlatma**.  
2. Bir `GroupShape` içinde **birden fazla şekil** (dikdörtgen ve elips) **ekleme**.  
3. `Document`i `.docx` dosyasına kaydederek **şekilleri Word'e yazma**.

Her aşama aşağıda ayrı bir adım olarak açıklanmıştır; kodu doğrudan projenize kopyalayıp yapıştırabilirsiniz.

![Programmatically create Word document with grouped shapes](grouped-shapes.png){: .align-center alt="Gruplandırılmış şekillerle programlı olarak Word belgesi oluşturma"}

## Adım 1: Belge ve builder'ı başlatma

`Document` sınıfı tüm Word dosyasını temsil ederken, `DocumentBuilder` içerik eklemek için akıcı bir API sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Neden önemli:* Önce `Document` oluşturmak temiz bir tuval sağlar. `DocumentBuilder` mevcut ekleme noktasını izler; bu, daha sonra şekilleri bir paragraf hiyerarşisine eklerken kritiktir.

## Adım 2: Grup şekil kapsayıcısını ekleme

`GroupShape`, birkaç ayrı şekli tek bir birim olarak ele almanızı sağlar. Bu, şekilleri birlikte taşımak veya yeniden boyutlandırmak istediğinizde kullanışlıdır.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Açıklama:* `InsertGroupShape` boş bir kapsayıcı ekler ve otomatik olarak bunu geçerli şekil yapar. Grup kapanana kadar yapılan tüm sonraki şekil eklemeleri bu kapsayıcıya eklenir.

## Dikdörtgen şekli ekleme

Şimdi ilk grafiğimizi—bir dikdörtgeni—ekliyoruz. Bu, **dikdörtgen şekli ekleme** gereksinimini karşılar.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Dikdörtgen, grubun biçimlendirme bağlamını devralır, bu yüzden `GroupShape` içinde görünür. İsterseniz daha sonra çizgi rengi, dolgu veya metin de ayarlayabilirsiniz.

## Birden fazla şekil ekleme

**Birden fazla şekil ekleme** yeteneğini göstermek için, dikdörtgenden hemen sonra bir elips ekliyoruz. Grup kapanmadan önce istediğiniz sayıda şekil (ör. üçgen, yıldız) ekleyebilirsiniz.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Bu noktada grup iki ayrı şekil içeriyor: bir dikdörtgen ve bir elips. Aynı üst öğeyi paylaştıkları için bunları bir bütün olarak taşıyabilirsiniz.

## Adım 3: Grup şekli paragraf hiyerarşisine ekleme

Word belgeleri içeriği bir paragraf ağacında saklar. Grubu son dosyada görünür kılmak için mevcut paragrafın içine eklememiz gerekir.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Neden gerekli:* Grup bir paragrafın içine eklenmezse, şekiller yalnızca bellek içinde kalır ve belge kaydedildiğinde dışarı atılır.

## Adım 4: Belgeyi kaydetme – şekilleri Word'e yazma

Son olarak, bellek içindeki `Document`i diske kalıcı olarak kaydediyoruz. Bu, **şekilleri Word'e yazma** hedefini yerine getirir.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`GroupShape.docx` dosyasını Microsoft Word’de açtığınızda, kodun eklediği gibi bir dikdörtgen ve bir elipsin birlikte gruplandığını göreceksiniz.

### Beklenen çıktı

- Projenin çıktı klasöründe **GroupShape.docx** adlı bir dosya.
- Word dosyası içinde: bir paragraf içinde gruplandırılmış bir dikdörtgen (100 pt × 50 pt) ve bir elips (80 pt × 40 pt). Şekillerden birini seçtiğinizde tüm grup seçilir.

## Yaygın kenar durumlarını ele alma

| Durum | Öneri |
|-----------|----------------|
| **Farklı DPI veya sayfa boyutu** | Şekilleri eklemeden önce `builder.PageSetup.PaperSize` değerini açıkça ayarlayarak beklenmedik ölçeklendirmeleri önleyin. |
| **Şekilleri tam olarak konumlandırma ihtiyacı** | Eklemeyi taşımak için `builder.MoveTo` kullanın, ardından `groupShape.Left` ve `groupShape.Top` özelliklerini (değerler puan cinsindendir) ayarlayın. |


## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalarla tam çalışan kod örnekleri içerir.

- [Create Word Document – Insert Rectangle Shape & Shadow in C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Create word document programmatically and group shapes in C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programmatically create a Word document with a group shape](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}