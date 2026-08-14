---
category: general
date: 2026-08-14
description: Java kullanarak Aspose.Words ile Word’de şekilleri gruplayın. Dikdörtgen
  şekil oluşturmayı, şekil boyutlarını ayarlamayı ve boş bir Word belgesinde birden
  fazla şekli gruplamayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: tr
lastmod: 2026-08-14
og_description: Aspose.Words for Java kullanarak Word'de şekilleri gruplayın. Boş
  bir Word belgesi oluşturun, dikdörtgen şekil ekleyin, şekil boyutlarını ayarlayın
  ve birkaç dakikada birden fazla şekli gruplayın.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Word'de şekilleri gruplama – Geliştiriciler için Java örneği
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Word'de şekilleri gruplama – tam programlama rehberi
url: /tr/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de şekilleri gruplama – tam programlama rehberi

Eğer **Word'de şekilleri gruplamanız** gerekiyorsa, bu öğretici Java ve Aspose.Words ile tüm süreci adım adım gösterir. **Boş bir Word belgesi oluşturmayı**, **dikdörtgen şekil eklemeyi**, **şekil boyutlarını ayarlamayı** ve sonunda **birden fazla şekli tek bir nesne gibi davranacak şekilde gruplamayı** öğreneceksiniz.

Word dosyasında şekillerle çalışmak, bir fırça olmadan tuval üzerine çizim yapmaya benzer. Bu rehberin sonunda, rapor, fatura veya özel şablonlar oluştururken herhangi bir Java projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız.

## Gereksinimler

- Java 8 veya daha yeni bir sürüm
- Aspose.Words for Java (en son sürüm, ör. 24.9)
- IntelliJ IDEA veya Eclipse gibi bir IDE
- Nesne‑yönelimli programlamaya temel aşinalık

Bu ön koşulların tamamı ücretsiz olarak kurulabilir ve aşağıdaki kod tek bir Maven bağımlılığıyla derlenir:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Adım 1: Boş Word belgesi oluşturma ve builder'ı başlatma

İlk olarak **boş bir Word belgesi oluşturmanız** gerekir. Bu, daha sonra şekiller ekleyebileceğiniz temiz bir tuval sağlar.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` tüm *.docx* dosyasını temsil ederken, `DocumentBuilder` paragraf, tablo ve şekil ekleyen yardımcıdır. Her iki nesnenin de başlatılması, herhangi bir Word otomasyon görevinin temelini oluşturur.

## Adım 2: Grup şekli kapsayıcısı ekleme

Bir **grup şekli**, diğer şekilleri tutabilen bir klasör gibi davranır. İlk olarak, sabit 400 pt × 200 pt boyutunda bir kapsayıcı oluştururuz.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

`insertGroupShape` yöntemi bir `GroupShape` nesnesi döndürür. Tek bir birim olarak ele almak istediğiniz tüm sonraki şekiller bu nesneye eklenmelidir.

## Adım 3: Dikdörtgen şekilleri oluşturma ve şekil boyutlarını ayarlama

Şimdi **dikdörtgen şekil** nesneleri oluşturur, boyutlarını yapılandırır ve grup içinde konumlandırırız. Bu adım aynı zamanda **şekil boyutlarını** kesin olarak nasıl ayarlayacağınızı gösterir.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Her iki dikdörtgen aynı boyutları paylaşır, ancak `left` özellikleri farklıdır, bu yüzden yan yana görünürler. İhtiyacınız olan herhangi bir düzeni oluşturmak için `setTop` ve `setLeft` değerlerini değiştirebilirsiniz.

## Adım 4: Gruplanmış dikdörtgenleri içeren belgeyi kaydetme

Şekiller grup içinde yer aldığında, sadece `Document`'i kaydedersiniz. Oluşan dosya, seçildiğinde birlikte hareket eden iki dikdörtgeni gösterir.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Programı çalıştırdığınızda çalışma dizininde `GroupShape.docx` oluşturulur. Microsoft Word'de açın, bir dikdörtgeni seçin ve tüm grubun bir birim olarak hareket ettiğini fark edin — **Word'de şekilleri gruplama** amacının tam olarak karşılandığını göreceksiniz.

![Group shapes in Word example](group-shapes.png){alt="Word'de grup şekilleri örneği"}

*Şekil: Word belgesinde birlikte gruplanmış iki dikdörtgen şekil.*

## Pro ipucu: Aynı grup şeklini yeniden kullanma

Daha sonra (ör. daireler, metin kutuları) daha fazla şekil eklemeniz gerekirse, `groupShape` referansını tutun ve `appendChild` çağrısına devam edin. Bu, kapsayıcının yeniden oluşturulmasını önler ve tüm üyelerin senkron kalmasını sağlar.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Kenar durumları ve sık sorulan sorular

- **Şekiller üst üste bindiğinde ne olur?** Üst üste binme izinlidir; Word, şekilleri eklenme sırasına göre render eder. Açık bir yığın düzeni istiyorsanız `setZOrder` kullanın.
- **Farklı sayfalardaki şekilleri gruplayabilir miyim?** Hayır. Bir `GroupShape` tek bir sayfaya sınırlıdır çünkü koordinat sistemi sayfa‑bağlantılıdır.
- **Gruplanmış şekiller biçimlendirmeyi miras alır mı?** Her alt öğe kendi biçimlendirmesini (dolgu rengi, çizgi stili) korur. Tek tip bir stil uygulamak için `groupShape.getChildNodes()` üzerinde döngü kurup özellikleri programatik olarak ayarlayın.

## Referans için tam kaynak kodu

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Programı çalıştırdığınızda iki dikdörtgenin **gruplandığı** bir DOCX dosyası üretilir. Herhangi bir dikdörtgeni seçmek, ikisinin de hareket ettiğini gösterir; böylece **birden fazla şekli gruplama** işlemini başarıyla tamamladığınız kanıtlanmış olur.

## Sonuç

Artık **Java kullanarak Word'de şekilleri gruplama** konusunda, **boş bir Word belgesi oluşturma**, **dikdörtgen şekil ekleme**, **şekil boyutlarını ayarlama** ve sonunda **birden fazla şekli tek, taşınabilir bir nesne olarak gruplama** adımlarını biliyorsunuz. Bu desen, herhangi bir sayıda şekle ölçeklenebilir ve metin, resim veya grafiklerle birleştirilerek zengin, programatik belgeler oluşturmanıza olanak tanır.

### Sıradaki adım ne?

- Farklı türlerde (elips, ok, metin kutusu) **birden fazla şekli gruplamayı** keşfedin.
- `shape.getFillColor()` ve `shape.getLine().setColor()` çağrılarıyla dolgu renkleri veya kenarlıklar ekleyin.
- Gruplanmış şekli yapılandırılmış raporlar için bir tablo hücresine yerleştirin.
- Bu yaklaşımı posta birleştirme (mail‑merge) ile birleştirerek markalı grafikler içeren kişiselleştirilmiş sözleşmeler üretin.

Deney yapmaktan, boyutları uyarlamaktan veya ek içerik eklemekten çekinmeyin. Gruplamayı ustalaştığınızda Word otomasyon betikleriniz çok daha esnek ve sürdürülebilir olur. Kodlamanın tadını çıkarın!


## Bir Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}