---
category: general
date: 2026-07-23
description: C#'ta boş bir Word belgesi oluşturun ve dikdörtgen şekil ekleyin. Aspose.Words
  kullanarak şekilleri eklemeyi ve şekilleri gruplamayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: tr
lastmod: 2026-07-23
og_description: C#'ta boş bir Word belgesi oluşturun ve şekilleri eklemeyi, dikdörtgen
  şekli eklemeyi ve şekilleri gruplamayı Aspose.Words ile öğrenin.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: Gruplanmış dikdörtgenlerle boş bir Word belgesi oluştur – C# öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Gruplandırılmış dikdörtgenlerle boş Word belgesi oluşturma – C# rehberi
url: /tr/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gruplandırılmış dikdörtgenlerle boş Word belgesi oluşturma – C# rehberi

Hiç **create blank word document** içeren, zaten bir dizi şekil bulunan bir boş Word belgesi oluşturmanız gerekti, ama bunları düzgün bir şekilde gruplandırmanın nasıl yapılacağından emin değildiniz mi? Tek başınıza değilsiniz. Birçok raporlama veya şablon‑oluşturma senaryosunda, yer tutucu olarak işlev gören birkaç dikdörtgenle temiz bir tuval istersiniz ve bunların tek bir birim olarak birlikte hareket etmesini istersiniz.

Bu öğreticide, Aspose.Words kütüphanesini kullanarak **create blank word document**, **add rectangle shape** ve ardından **group shapes word** adımlarını ayrıntılı olarak göstereceğiz. Sonunda, iki dikdörtgenin bir grup içinde olduğu, böylece daha sonraki konumlandırma veya yeniden boyutlandırmanın her ikisini aynı anda etkilediği kullanıma hazır bir `.docx` dosyanız olacak.  

Ayrıca forumlarda ve Stack Overflow'da sıkça sorulan “**how to insert shapes**” ve “**how to group shapes**” sorularına da yanıt vereceğiz. Harici belgelere gerek yok—gereken her şey burada.

---

## Prerequisites

- .NET 6 veya daha yenisi (kod .NET Core ile de derlenir)  
- Aspose.Words for .NET (NuGet paketi `Aspose.Words`)  
- C# sözdizimi hakkında temel bir anlayış (eğer “Hello World” yazdıysanız, hazırsınız)  

If you haven’t installed Aspose.Words yet, run:

```bash
dotnet add package Aspose.Words
```

Hepsi bu—ekstra DLL yok, COM interop yok, sadece temiz bir NuGet referansı.

## Step 1: Create blank word document ve builder'ı başlatma

İlk yaptığımız şey, boş bir `Document` nesnesi oluşturmak. Bunu taze bir kağıt parçası gibi düşünün. Ardından, içerik eklemek için Aspose'un sağladığı kullanışlı araç `DocumentBuilder`'ı ekliyoruz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Neden önemli:** Bir `DocumentBuilder` olmadan düşük seviyeli düğüm ağacını manuel olarak manipüle etmeniz gerekir, bu da hataya açıktır. Builder, bir `.docx` dosyasının XML karmaşıklığını soyutlar.

## Step 2: How to insert shapes – önce bir grup kapsayıcı ekleyin

Aspose, daha sonra diğer şekilleri tutabilecek bir *group shape* eklemenize izin verir. Bu, **group shapes word** için temeldir.  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Pro ipucu:** Grup, çocuk şekiller eklenene kadar görünmez, bu yüzden sonraki adıma kadar ortaya çıkan belgede herhangi bir artefakt görmezsiniz.

## Step 3: Add rectangle shape – gerçek görünür nesneler

Şimdi **add rectangle shape** iki kez ekleyeceğiz, her biri kendi boyutuyla. `InsertShape` yöntemi bir `ShapeType` ve puan cinsinden boyutlar alır (1 pt ≈ 1/72 inç).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **Neden dikdörtgenler?** En basit geometrik şekildir, yer tutucular, düğme‑gibi UI taklitleri veya basit grafik öğeleri için mükemmeldir.

## Step 4: How to group shapes – dikdörtgenleri gruba ekleyin

Dikdörtgenler oluşturulduğunda, şimdi **how to group shapes**'i, daha önce eklediğimiz grup şeklinin çocuğu olarak ekleyerek yapıyoruz.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **Altında ne oluyor?** Grup şekli, belgenin XML ağacında ebeveyn düğüm haline gelir. Grubu hareket ettirmek, iki dikdörtgeni birlikte hareket ettirir ve göreceli konumlarını korur.

## Step 5: Save the document – artık gruplandırılmış‑şekilli bir Word dosyanız var

Son olarak, belgeyi diske kaydediyoruz. Yolu, makinenizde mevcut bir konuma değiştirin.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

Bu tüm programdır. Çalıştırın, `GroupShape.docx` dosyasını açın ve iki dikdörtgenin birlikte durduğunu göreceksiniz. Birini seçerseniz, tüm grup vurgulanır—tam olarak **group shapes word**'ün yapması gereken şey.

## Full source code in one place

Kolaylık olması için, işte tam, kopyala‑yapıştır hazır örnek:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Beklenen çıktı:** `GroupShape.docx` dosyasını açmak, iki dikdörtgenin birlikte gruplandığı boş bir sayfa gösterir. Bir dikdörtgeni seçmek, diğerini otomatik olarak seçer ve grubun başarılı olduğunu doğrular.

## Common questions & edge‑case handling

### İki'den fazla şekle ihtiyacım olsaydı?

Her yeni şekil için `builder.InsertShape(...)` ve `group.AppendChild(...)` çağırmaya devam edin. Grup, istediğiniz sayıda çocuğu tutabilir.

### Dikdörtgenlerin dolgu rengi veya kenarlığını ayarlayabilir miyim?

Kesinlikle. Bir dikdörtgen oluşturduktan sonra `FillColor`, `OutlineColor` ve `LineWidth` özelliklerini ayarlayabilirsiniz:

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### Oluşturulduktan sonra tüm grubu nasıl hareket ettirebilirim?

Grubun `Left` ve `Top` özelliklerini kullanın, puan cinsinden ölçülür:

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### Grubu ölçeklendirme hakkında ne söyleyebiliriz?

`group.Width` ve `group.Height` ayarlayın veya `group.ScaleX` / `group.ScaleY` kullanın. Çocuk dikdörtgenler, gruba göre oranlarını korur.

### Bu eski .doc dosyalarıyla çalışır mı?

Aspose.Words dosya formatını soyutlar, bu yüzden aynı kod `.doc` ve `.docx` için çalışır. Tek sınırlama, bazı yeni şekil özelliklerinin eski ikili formata kaydedilirken aşağı örneklenebilmesidir.

## Pro tips for production‑ready code

- **Dispose of resources** – Büyük dosyalarla çalışıyorsanız, belleği hızlıca serbest bırakmak için `Document`'i bir `using` bloğu içinde sarın.  
- **Error handling** – Özel yazı tipleri eklemeyi planlıyorsanız `Aspose.Words.Fonts.FontSettingsException` yakalayın.  
- **Performance** – Birçok şekil eklerken, geçici olarak `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` ile yerleşim güncellemelerini devre dışı bırakın ve ardından yeniden etkinleştirin.

## Conclusion

Artık Aspose.Words ile C#'ta **how to create blank word document**, **add rectangle shape** ve **group shapes word**'i nasıl yapacağınızı biliyorsunuz. Örnek, temel “**how to insert shapes**” ve “**how to group shapes**” adımlarını kapsar, her satırın neden var olduğunu açıklar ve özelleştirme, uç durumlar ve en iyi uygulamalara da değinir.

Sonra **how to insert images**, **add text inside grouped shapes** veya **export the document to PDF** gibi konuları keşfedebilirsiniz—hepsi `DocumentBuilder` ve şekil manipülasyonu aynı desenini izler. Denemeye devam edin; Aspose API, hayal edebileceğiniz hemen hemen her Word otomasyon senaryosunu yönetebilecek kadar zengindir.

Kodlamaktan keyif alın ve bir sorunla karşılaşırsanız yorum bırakmaktan çekinmeyin!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}