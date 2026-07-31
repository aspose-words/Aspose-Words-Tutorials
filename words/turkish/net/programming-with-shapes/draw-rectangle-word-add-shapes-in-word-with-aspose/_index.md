---
category: general
date: 2026-07-29
description: Aspose.Words kullanarak dikdörtgen kelime çizin. Dikdörtgen şekli eklemeyi,
  çizgi şekli eklemeyi ve tek bir belgede birden fazla şekli yönetmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: tr
lastmod: 2026-07-29
og_description: Aspose.Words ile dikdörtgen çizin. Bu adım adım rehberi izleyerek
  dikdörtgen şekli ekleyin, çizgi şekli ekleyin ve birden fazla şekille Word’de sorunsuz
  bir şekilde çalışın.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: Word'de Dikdörtgen Çiz – Şekil Eklemeyi Ustalaş
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Word'de Dikdörtgen Çiz – Aspose ile Word'e Şekil Ekle
url: /tr/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Word'de Şekil Ekleme Tam Kılavuzu

Her seferinde UI'yi açmadan **draw rectangle word** belgeleri nasıl çizeceğinizi hiç merak ettiniz mi? Yalnız değilsiniz. Birçok geliştirici, Word dosyalarını anında oluşturmak zorunda ve en kolay yol, bir kütüphanenin ağır işi üstlenmesine izin vermektir. Bu öğreticide, Aspose.Words for .NET kullanarak **şekil ekleme**—özellikle bir dikdörtgen ve bir çizgi—nasıl ekleyeceğinizi tam olarak göstereceğiz ve *draw rectangle word* ifadesine odaklanarak asla kaybolmayacaksınız.

Bunu kodunuz içinde yaşayan mini bir sanat stüdyosu gibi düşünün. Sonunda **add rectangle shape**, **add line shape** ekleyebilecek ve hatta bunları **multiple shapes word** gruplarına birleştirebileceksiniz. UI yok, manuel uğraş yok, sadece temiz, tekrarlanabilir C#.

## Öğrenecekleriniz

- Aspose.Words ile yeni bir Word belgesi oluşturun.  
- Birden fazla nesneyi tutabilen bir **GroupShape** oluşturun.  
- **Add rectangle shape** ve **add line shape** bu gruba ekleyin.  
- Gruplanmış şekilleri belge gövdesine ekleyin.  
- Dosyayı kaydedin ve sonucu anında görün.  

Temel C#'a hâkimseniz ve bir Aspose.Words kopyanız varsa hazırsınız. Çekirdek kütüphanenin ötesinde ekstra NuGet paketlerine gerek yok.

> **Pro tip:** Aspose.Words .NET 6, .NET 7 ve .NET Framework 4.6+ ile çalışır. Projenize uygun çalışma zamanını seçin.

![draw rectangle word örneği](https://example.com/placeholder-image.png "draw rectangle word – Word dosyasında gruplanmış şekiller")

## draw rectangle word – Belgeyi Kurma

draw rectangle word** yapabilmeden önce temiz bir tuvale ihtiyacımız var. `Document` sınıfı bu tuval; `DocumentBuilder` ise fırçamız.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Yukarıdaki iki satır bize yeni, bellek içi bir `.docx` sağlar. Henüz diske bir şey yazılmadığı için dosya sistemini kirletmeden deney yapabiliriz.

## Şekil Ekleme – GroupShape Kapsayıcı Oluşturma

**multiple shapes word**'in tek bir birim gibi davranmasını—birlikte hareket etmesini, birlikte döndürülmesini—istediğinizde, onları bir `GroupShape` içinde sararsınız. Bir grubu, diğer şekilleri tutan bir klasör gibi düşünün.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Neden bir grup? Çünkü ileride **add rectangle shape** ve **add line shape** ekleyip ardından birlikte hareket ettirmek isteyebilirsiniz. Grup olmadan, her şekli ayrı ayrı yeniden konumlandırmanız gerekir.

## add rectangle shape – Gruba Dikdörtgen Ekleme

Kapsayıcı artık mevcut, **add rectangle shape** ekleyelim. Dikdörtgen, `ShapeType`'ı `Rectangle` olan bir `Shape`'dur.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

`Left` ve `Top` değerlerinin sayfaya değil, grubun orijinine göre olduğunu fark edin. Bu, şekilleri hassas bir şekilde hizalamayı kolaylaştırır. Dikdörtgen, grubun sol‑üst köşesine yakın bir yerde görünecektir.

## add line shape – Aynı Gruba Çizgi Ekleme

Bir çizgi sadece başka bir `Shape`'dir, ancak `ShapeType`'ı `Line`'dır. Çizgiyi dikdörtgenin altına konumlandıracağız.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Çizginin yüksekliği sıfır olduğu için, `Top` özelliği çizginin dikey konumunu belirler. `Width` ise çizginin yatay olarak ne kadar uzanacağını kontrol eder.

## multiple shapes word – Grubu Belge Gövdesine Ekleme

Artık **add rectangle shape** ve **add line shape** içeren bir grubumuz var. Son adım, tüm bu öğeyi belgeye eklemek.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode`, grubu `DocumentBuilder`'ın şu anda konumlandığı yere tam olarak yerleştirir. Belirli bir paragrafta ihtiyacınız varsa, önce `builder.MoveToParagraph(index)` ile builder'ı hareket ettirin.

## Sonucu Kaydetme – draw rectangle word Çıktısını Görme

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Oluşturulan dosyayı Microsoft Word'de açın ve içinde bir dikdörtgen ve bir çizgi bulunan tek bir grup göreceksiniz. Grubu tıklayabilir, sürükleyebilir veya yeniden boyutlandırabilirsiniz—tüm şekiller birlikte hareket eder. İşte **multiple shapes word**'ün gücü.

### Beklenen Çıktı

- `GroupShape.docx` adlı bir `.docx` dosyası.  
- Sol‑üst köşeye yakın, gruplanmış bir dikdörtgen (120 × 80 pt) içeren bir sayfa.  
- Dikdörtgenin hemen altında konumlandırılmış yatay bir çizgi (150 pt uzunluğunda).  
- Her iki şekil de tek bir nesne olarak seçilebilir.

Grubu çift tıkladığınızda, Word her bir şekli ayrı ayrı düzenlemenize izin verir—ince ayarlar için mükemmeldir.

## Yaygın Sorular & Kenar Durumları

**İki'den fazla şekle ihtiyacım olursa ne olur?**  
Her ek nesne için `group.AppendChild(yourShape)` çağrısını sürdürün. Grup, herhangi bir sayıda şekil tutabilir, bu da karmaşık diyagramlar için idealdir.

**Dikdörtgenin dolgu rengini değiştirebilir miyim?**  
Kesinlikle. Dikdörtgeni oluşturduktan sonra `rectangle.FillColor = System.Drawing.Color.LightBlue;` şeklinde ayarlayın. Bu, doldurma destekleyen tüm şekillerde çalışır.

**Çizgi için `Height = 0` ayarlamalı mıyım?**  
Evet, düz bir yatay çizgi için yükseklik sıfır olmalıdır. Dikey bir çizgi için `Width = 0` ayarlayın ve `Height`'a pozitif bir değer verin.

**Bu .doc dosyaları (Word 97‑2003) ile çalışır mı?**  
Aspose.Words eski `.doc` formatına kaydedebilir, ancak bazı modern şekil özellikleri sınırlı olabilir. Tam doğruluk için `.docx` kullanın.

**Tüm grubu nasıl döndürürüm?**  
Eklemeye başlamadan önce `group.Rotation = 45;` (derece) ayarlayabilirsiniz. Döndürme, her alt şekle uygulanır.

## Özet – Word'de Şekilleri Programlı Olarak Nasıl Ekleriz

- **draw rectangle word**, bir `Document` ve `DocumentBuilder` oluşturarak başlar.  
- **multiple shapes word** tutacak bir **GroupShape** oluşturun.  
- **add rectangle shape** ve **add line shape** gruba eklenir.  
- Grubu `builder.InsertNode` ile gövdeye ekleyin.  
- Dosyayı kaydedin ve görsel sonucu doğrulamak için açın.

Bu, tek bir, okunması kolay kod listesinde özetlenmiş tam iş akışıdır.

## Sonraki Adımlar & İlgili Konular

Artık **şekil ekleme** konusunu bildiğinize göre, aşağıdakileri keşfetmeyi düşünün:

- Yuvarlatılmış köşeli **add rectangle shape** (`ShapeType.Rectangle` + `CornerRadius`).  
- Farklı kesik desenlerine sahip çizgileri stillendirme (`line.LineFormat.DashStyle`).  
- Şekillerin yanına resim ekleyerek daha zengin raporlar oluşturma.  
- **multiple shapes word** kullanarak akış şemaları veya basit UML diyagramları oluşturma.  

Bu konuların her biri, burada oluşturduğumuz temelin üzerine doğal olarak inşa edilir ve hepsi şekil oluşturma, yapılandırma ve gerektiğinde gruplama aynı desenini izler.

---

Kodlamaktan keyif alın! Eğer tuhaflıklarla karşılaşırsanız veya paylaşacak harika bir kullanım senaryonuz varsa, aşağıya yorum bırakın. Geri bildiriminiz, hepimizin **draw rectangle word** ve ötesindeki sanatını ustalaşmasına yardımcı olur.

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanıza ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [C# ile Word'de dikdörtgen şekli oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words ile Word'de dikdörtgen şekli oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words for .NET Kullanarak Word Belgelerine Şekil Ekleme](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}