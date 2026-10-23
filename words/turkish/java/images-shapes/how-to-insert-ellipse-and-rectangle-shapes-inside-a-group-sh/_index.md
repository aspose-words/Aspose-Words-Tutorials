---
category: general
date: 2026-10-23
description: Aspose.Words kullanarak Word'de elips eklemeyi ve dikdörtgen şekli eklemeyi
  öğrenin. İmleci şekle taşıma ve grup şekli oluşturma konularını içerir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: tr
lastmod: 2026-10-23
og_description: Aspose.Words ile Word’e elips ekleme ve dikdörtgen şekli ekleme. İmleci
  şekle taşıma ve grup şekli oluşturma adım adım kılavuzunu izleyin.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Word grup şekline elips ve dikdörtgen şekilleri nasıl eklenir
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words ile bir grup şeklin içine elips ve dikdörtgen şekilleri nasıl
  eklenir
url: /tr/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile bir grup şekil içinde elips ve dikdörtgen şekilleri nasıl eklenir

Programlı olarak bir Word belgesine **elips nasıl eklenir** bilmeniz gerekiyorsa, bu kılavuz tam süreci gösterir. Ayrıca **dikdörtgen nasıl eklenir** şeklini görecek, **imleci şekle taşıma** yöntemini öğrenecek ve birden fazla çizim nesnesi tutan **grup şekil nasıl oluşturulur** keşfedeceksiniz.

Word otomasyonu genellikle çizim nesnelerinin hassas konumlandırılmasını gerektirir. Bu öğreticinin sonunda, daha fazla stil uygulama veya dışa aktarma için hazır, grup içinde bir dikdörtgen ve elips içeren bir `.docx` dosyası oluşturabilirsiniz. Aspose.Words for .NET kütüphanesi ve bir .NET geliştirme ortamı dışındaki dış araçlara gerek yoktur.

## Önkoşullar

* .NET 6.0 veya daha yeni bir sürüm yüklü.
* Aspose.Words for .NET (NuGet paketi `Aspose.Words`) projenize eklenmiş.
* C# sözdizimi ve Visual Studio (veya herhangi bir IDE) hakkında temel bilgi.

Bu gereksinimler, kodun ek yapılandırma olmadan derlenmesini sağlar.

## Word'de grup şekil nasıl oluşturulur

Bir grup şekil, birkaç şekli tek bir birim olarak taşımanıza, döndürmenize veya biçimlendirmenize olanak tanıyan bir kapsayıcı görevi görür. Aşağıdaki kod, belirli bir boyutta (300 × 200 nokta) bir grup oluşturur ve belgeyi sonraki çizim işlemleri için hazırlar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Bu adımın önemi*: Grup şekil, yerel bir koordinat sistemi tanımlar. İmleç grup içine taşındıktan sonra eklenen tüm şekiller, grubun orijiniyle ilişkili konumlandırılır; bu da yerleşim hesaplamalarını basitleştirir.

## Word'de dikdörtgen şekil nasıl eklenir

Grup artık mevcut olduğuna göre, içine **dikdörtgen şekil ekleyebilirsiniz**. Dikdörtgen, diğer içerikler için bir arka plan veya görsel yer tutucu olarak hizmet eder.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Açıklama*: `MoveTo(group)` builder'a aktif ekleme noktasının grup şekil olduğunu söyler. İmleç taşınmazsa, `InsertShape` dikdörtgeni grup yerine belge gövdesine ekler.

## Elips nasıl eklenir

Dikdörtgen yerleştirildiğine göre, şimdi **elips nasıl eklenir** gösterebilirsiniz. Elips, aynı grup içinde ortalanacak ve istenirse dikdörtgenin üzerine binecektir.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*İmlecin neden taşınması gerektiği*: `InsertShape` her çağrısı mevcut imleç konumunu dikkate alır. `MoveTo(group)` tekrar çağrılması, elipsin de grupun bir çocuğu olmasını sağlar ve istenen hiyerarşiyi korur.

## Ek nesneler eklemeden önce imleci şekle taşıma

Daha sonra daha fazla şekil eklemeniz gerekirse, her eklemeden önce her zaman **imleci şekle taşıyın**. Bu desen, grup dışına yanlışlıkla yerleştirmeyi önler.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*İpucu*: `MoveTo(group)` tekrar kullanmak maliyet açısından düşük ve kod okunabilirliğini artırır. Ayrıca ekleme bağlamı açık olduğu için gelecekteki bakım daha kolay olur.

## Belgeyi kaydet

Son olarak, belgeyi diske kaydedin. Örnek, dosyayı belirttiğiniz bir klasörde `GroupShape.docx` olarak kaydeder.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Kaydedilen dosyayı Microsoft Word'de açtığınızda, içinde bir dikdörtgen ve bir elips bulunan tek bir grup göreceksiniz; her ikisi de doğru konumlandırılmış olacaktır.

### Beklenen çıktı

* `GroupShape.docx` adlı bir `.docx` dosyası.
* Belge içinde, 300 × 200 nokta boyutunda bir grup çizim nesnesi.
* Grup içinde:
  * Grubun orijini konumunda bulunan bir dikdörtgen (100 × 50 nokta).
  * Dikdörtgenin üzerine binen bir elips (80 × 80 nokta).
  * İmleci taşıdıktan sonra eklediğiniz diğer şekiller.

## Yaygın varyasyonlar ve kenar durumları

| Durum | Önerilen yaklaşım |
|-----------|----------------------|
| **Different unit sizes** | Aspose.Words uses points (1 pt = 1/72 in). Convert centimeters or inches to points before calling `InsertShape`. |
| **Rotating shapes inside the group** | After inserting a shape, retrieve its `ShapeBase` object and set `ShapeBase.RotationAngle`. |
| **Adding text inside a shape** | Use `ShapeBase.AppendChild(new Paragraph(document))` and then add a `Run` with the desired text. |
| **Saving to PDF instead of DOCX** | Call `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – the group hierarchy is preserved in the PDF output. |

Bu varyasyonlar, aynı **elips nasıl eklenir** mantığının birçok gerçek dünya senaryosuna uyarlanabileceğini gösterir.

## Profesyonel ipuçları

* **Aynı `DocumentBuilder` örneğini yeniden kullanın** – bellek yükünü azaltır ve belge durumunun tutarlı kalmasını sağlar.
* **Şekil boyutlarını doğrulayın** – aşırı büyük genişlik veya yükseklikler eski Word sürümlerinde render sorunlarına yol açabilir.
* **Stil uygulamadan önce gruplandırın** – tüm çocuklar eklendikten sonra gruba dolgu renkleri veya çizgi stilleri uygulamak, tutarlı bir görünüm sağlar.

## Sonuç

Artık Aspose.Words kullanarak bir Word belgesinde grup içinde **elips nasıl eklenir** ve **dikdörtgen nasıl eklenir** şekli hakkında bilgi sahibisiniz. Her eklemeden önce tutarlı bir şekilde **imleci şekle taşıma** işlemini yaparak temiz bir hiyerarşi korur ve yanlış yerleştirmeleri önlersiniz. Tam örnek derlenir, çalışır ve daha fazla özelleştirilebilecek veya dışa aktarılabilecek bir grup şekil üretir.

Daha fazlasını keşfetmeye hazır mısınız? Bu tekniği **grup şekil nasıl oluşturulur** ile birleştirerek karmaşık diyagramlar deneyin veya **dikdörtgen şekil ekle word** ile metin kutularını bir arada kullanarak zengin raporlar oluşturun. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words ile Word'de dikdörtgen şekil ve grup şekilleri nasıl oluşturulur](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Boş Word belgesi oluşturma ve C#'ta gizli bir elips şekli ekleme](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [C#'ta grup şekil docx oluşturma ve etkileşimli denetimler ekleme](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}