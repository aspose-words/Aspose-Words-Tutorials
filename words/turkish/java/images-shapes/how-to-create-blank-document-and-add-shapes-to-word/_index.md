---
category: general
date: 2026-09-18
description: Aspose.Words ile boş belge oluşturun ve Word’e şekiller ekleyin – bir
  üçgen şekli ve daha fazlasını nasıl ekleyeceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: tr
lastmod: 2026-09-18
og_description: Aspose.Words kullanarak Word'de boş belge oluşturun ve bir üçgen şekli
  eklemeyi, şekilleri gruplamayı ve diğer grafikleri öğrenin. Bu kapsamlı rehberi
  izleyin.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Boş bir belge oluşturun ve Word'e şekil ekleyin – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Boş belge oluşturma ve Word'e şekil ekleme
url: /tr/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş belge oluşturma ve Word'e şekil ekleme

If you need to **create blank document** and then enrich it with graphics, this guide shows you exactly how. We'll walk through creating a Word file from scratch and **add shapes to Word**, including **how to insert triangle** shape, using Aspose.Words for Java.

You’ll finish the tutorial with a ready‑to‑use *.docx* file that contains a grouped shape holding a triangle. The steps cover everything from project setup to saving the final **create word document**. No external tools are required beyond Aspose.Words.

## Önkoşullar

* Java 17 veya daha yeni bir sürüm yüklü  
* Bağımlılık yönetimi için Maven veya Gradle  
* Aspose.Words for Java lisansı (ücretsiz deneme sürümü bu demo için çalışır)  

If you prefer a different build system, adjust the dependency syntax accordingly. The code works on any platform that supports Java.

## Aspose.Words ile boş belge oluşturma

The first operation is to **create blank document** in memory. Aspose.Words provides a `Document` class that represents a Word file without any content.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

`new Document()` yapıcı, daha sonra paragraflar, tablolar veya grafiklerle doldurabileceğiniz boş bir *.docx* yapısı oluşturur. Belge boş olduğu için eklediğiniz her öğe üzerinde tam kontrol sizde olur.

## Word'e şekil ekleme – grup şekli ekleme

A group shape lets you treat several graphics as a single unit. This is useful when you want to move or resize multiple shapes together.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder`, içerik eklemek için birincil API'dir. `insertGroupShape` çağrısı, 300 × 300 puan (yaklaşık 4 × 4 inç) boyutunda bir kapsayıcı oluşturur. Bu çağrının ardından imleç, ek şekiller eklemeye hazır bir şekilde grubun *içine* konumlanır.

### Neden grup şekli kullanmalı?

Gruplama, ilgili grafikleri hizalı tutar ve tutarlı biçimlendirme uygulamayı kolaylaştırır. Daha sonra üçgeni taşımaya karar verirseniz, tüm grup birlikte hareket eder ve düzen korunur.

## Grup içinde üçgen şekli ekleme

Now we address **how to insert triangle** shape. The triangle is one of the built‑in `ShapeType` values.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

`moveTo` çağrısı, builder'ın ekleme noktasının grubun ilk paragrafı olmasını sağlar. `insertShape` daha sonra 60 × 60 puan boyutunda bir üçgen ekler. İmleç grup içinde olduğu için üçgen, grup şeklinin bir çocuğu haline gelir.

**Add triangle shape** ipuçları:

* Boyut, puan cinsinden ölçülür; 72 puan bir inçe eşittir. Boyutları düzeninize uygun şekilde ayarlayın.  
* Farklı bir yönlendirme gerekiyorsa, şekli grup içinde hizalamak için `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` kullanın.  
* Üçgen, `shape.getFillColor()` veya `shape.getStrokeColor()` ile geçersiz kılmadığınız sürece grupun dolgu ve çizgi stillerini devralır.

## Belgeyi kaydet – create word document

After constructing the graphics, you save the file. This step finalizes the **create word document** operation.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save`, bellekteki temsili standart bir Word belgesi olarak diske yazar. `ExtendedGroup.docx` dosyasını Microsoft Word, LibreOffice veya OOXML formatını destekleyen herhangi bir görüntüleyicide açabilirsiniz. Dosya, kod tarafından oluşturulduğu gibi bir üçgen içeren gruplanmış bir şekli gösterir.

## Tam çalıştırılabilir örnek

Putting all pieces together, here is the complete program you can copy, compile, and run:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Beklenen sonuç

When you open `ExtendedGroup.docx`, you will see a single group shape occupying the center of the page. Inside that group, a small triangle appears at the default position. The triangle can be selected and moved as part of the group, confirming that **add shapes to word** worked as intended.

`ExtendedGroup.docx` dosyasını açtığınızda, sayfanın ortasını kaplayan tek bir grup şekli göreceksiniz. Bu grubun içinde, varsayılan konumda küçük bir üçgen belirecek. Üçgen, grupun bir parçası olarak seçilip taşınabilir; bu da **add shapes to word** işleminin amaçlandığı gibi çalıştığını doğrular.

## Sık sorulan sorular ve uç durumlar

| Question | Answer |
|----------|--------|
| *Grup içinde birden fazla şekil ekleyebilir miyim?* | Evet. Üçgeni ekledikten sonra, imleci grup içinde tutun ve farklı bir `ShapeType` ile `builder.insertShape` metodunu tekrar çağırın. |
| *Üçgenin kırmızı olması gerektiğinde ne yapmalıyım?* | `insertShape` tarafından döndürülen `Shape` nesnesini alın ve `shape.getFillColor().setColor(Color.RED)` metodunu çağırın. |
| *Bu, eski .doc dosyalarıyla çalışır mı?* | Aspose.Words, belirttiğiniz formatta kaydeder. Eski bir Word belgesi oluşturmak için `doc.save("file.doc", SaveFormat.DOC)` kullanın. |
| *Grubun kenarlığını nasıl değiştiririm?* | Kenarlığı özelleştirmek için `group.getStrokeColor().setColor(Color.BLUE)` ve `group.setLineWeight(2.0)` kullanın. |
| *Üçgeni döndürmenin bir yolu var mı?* | Derece cinsinden bir açı ayarlamak için `shape.getRotation()` metodunu çağırın. |

## Profesyonel ipuçları

* **Reuse the builder** – her şekil için yeni bir `DocumentBuilder` oluşturmak ek yük getirir. Belge başına tek bir builder tutun.  
* **Unit conversion** – milimetre ile çalışıyorsanız, puanlara dönüştürün (`points = mm * 2.83465`).  
* **Performance** – büyük belgeler için, tüm şekiller eklendikten sonra `doc.updatePageLayout()` metodunu yalnızca bir kez çağırın.

## Sonuç

Artık Aspose.Words for Java kullanarak **create blank document**, **add shapes to Word** ve özellikle **how to insert triangle** şeklinin nasıl ekleneceğini biliyorsunuz. Tam örnek, boş bir dosyadan gruplanmış bir üçgen içeren kaydedilmiş **create word document**'a kadar tam iş akışını gösterir.

Buradan, ek `ShapeType` değerlerini keşfedebilir, özel stil uygulayabilir veya birden fazla grubu birleştirerek karmaşık diyagramlar oluşturabilirsiniz. Farklı boyutlar, renkler ve konumlarla deney yaparak Java'da Word otomasyonunda uzmanlaşın.

--- 

*Bir sonraki raporunuzu otomatikleştirmeye hazır mısınız? Örneği klonlayın, boyutları ayarlayın ve kodu bugün kendi uygulamanıza entegre edin.*

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen teknikler üzerine inşa edilen yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for .NET Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)
- [Gölgelendirilmiş Dikdörtgen Şekilli Boş Word Belgesi Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words ile Word'de Dikdörtgen Şekil Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}