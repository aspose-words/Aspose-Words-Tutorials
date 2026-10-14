---
category: general
date: 2026-10-13
description: Java ile Word'de gruplanmış şekiller oluşturmayı öğrenin. Bu kılavuz,
  grup şekli eklemeyi, gruba çizgi eklemeyi ve birden fazla şekli Word genelinde gruplamayı
  gösterir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: tr
lastmod: 2026-10-13
og_description: Java ile Word’de gruplanmış şekiller oluşturun. Grup şekli eklemek,
  gruba çizgi eklemek ve birden fazla şekli Word belgelerinde gruplayarak bu kapsamlı
  öğreticiyi izleyin.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Java ile Word'de Gruplandırılmış Şekiller Oluşturma – Adım Adım Rehber
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Java kullanarak bir Word belgesinde gruplanmış şekiller nasıl oluşturulur
url: /tr/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java kullanarak bir Word belgesinde gruplandırılmış şekiller nasıl oluşturulur

Java'dan bir Microsoft Word dosyasında **gruplandırılmış şekiller oluşturmanız** gerekiyorsa, bu öğretici size tüm süreci adım adım gösterir. **insert group shape** nasıl yapılır, aynı kapsayıcı içinde bir dikdörtgen ve bir çizgi nasıl yerleştirilir ve sonunda belgeyi gruplandırılmış grafiklerle nasıl kaydedersiniz göreceksiniz.

Şekilleri gruplandırmak, birden fazla çizim nesnesini tek bir birim olarak taşıma, yeniden boyutlandırma veya stil verme işlemlerini kolaylaştırır—diyagramlar, akış şemaları veya özel sayfa süslemeleri için mükemmeldir. Bu rehberin sonunda **add line to group**, **group multiple shapes word** belgelerini ekleyebilecek ve aynı tekniği istediğiniz sayıda şekil için yeniden kullanabileceksiniz.

## Önkoşullar

- Geliştirme makinenizde yüklü Java 17 veya daha yeni bir sürüm.  
- Aspose.Words for Java lisansı (veya ücretsiz deneme sürümü).  
- Aspose.Words bağımlılığını ekleyebileceğiniz bir Maven veya Gradle projesi:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Ek bir kütüphane gerekmemektedir.

## Adım 1: Grup şekil kapsayıcısını ekleyin

İlk adım, belgeye **insert group shape** eklemektir. Bu kapsayıcı, sonraki tüm şekilleri tutacaktır.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` tipinde `GROUPSHAPE` olan boş bir `Shape` nesnesi oluşturur. Bunu, diğer çizim nesnelerini içerebilen şeffaf bir kanvas olarak düşünün.

## Adım 2: Gruba bir dikdörtgen ekleyin

Bir dikdörtgen, genellikle bir şekil grubunun görsel arka planı olarak hizmet eder.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

`Left` ve `Top` değerlerini `0` olarak ayarlamak, dikdörtgeni grubun sol‑üst köşesine konumlandırır. Bu değerleri değiştirerek şekli grup içinde ofsetleyebilirsiniz.

## Adım 3: **Add line to group** – bir çizgi şekli oluşturun

Şimdi **add line to group** yapıyoruz. Çizgi, dikdörtgenin altında görünecek.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

`Top` özelliği, çizgiyi dikdörtgenden 60 point aşağı kaydırarak basit bir yığılmış düzen oluşturur. Yatay ofset gerekiyorsa `Left` değerini de ayarlayabilirsiniz.

## Adım 4: Belgeyi gruplandırılmış şekillerle kaydedin

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

`GroupShapeDemo.docx` dosyasını Microsoft Word'de açtığınızda, hem dikdörtgeni hem de çizgiyi içeren tek bir grup göreceksiniz. Grubu seçmek, iki şekli birlikte taşımanıza izin verir; bu da **group multiple shapes word** işlemini başarıyla gerçekleştirdiğinizi gösterir.

## Tam, çalıştırılabilir örnek

Aşağıda tüm importlar ve hata yönetimi dahil tam program yer almaktadır. IDE'nize kopyalayın, `YOUR_DIRECTORY` ifadesini mevcut bir klasör yolu ile değiştirin ve çalıştırın.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Beklenen çıktı

- Hedef klasörde `GroupShapeDemo.docx` adlı bir dosya oluşur.  
- Dosyayı Word'de açtığınızda, üstte bir dikdörtgen ve altında bir çizgi içeren tek bir gruplandırılmış nesne gösterilir.  
- Grubu sürüklemek, iki şekli birlikte hareket ettirir ve **created grouped shapes** işlemini başarıyla tamamladığınızı doğrular.

## İpuçları ve yaygın hatalar

- **Pro tip:** Grup içindeki bireysel şekilleri döndürmeniz veya stil vermeniz gerekiyorsa, onları gruba eklemeden önce ilgili ayarlayıcıları (`setRotation`, `getFill().setForeColor` vb.) çağırın. Grup bu görsel özellikleri koruyacaktır.  
- **Dikkat:** Çizgi için `Top` özelliğini ayarlamayı unutmak, dikdörtgenle çakışmasına ve grubun dağınık görünmesine neden olabilir.  
- **Köşe durumu:** İki'den fazla şekil eklediğinizde, her çocuğun koordinatlarının grup orijini (0,0) göreceli olduğunu unutmayın. Düzeni buna göre planlayın.  
- **Performans notu:** Yüzlerce şekli gruplandırmak dosya boyutunu biraz artırabilir, ancak Word'de sonraki düzenlemeleri basitleştirir.

## **group multiple shapes word** belgelerini programlı olarak nasıl gruplandırılır

Yukarıda gösterilen desen—bir grup kapsayıcı oluşturma, her çocuk şekli yapılandırma ve ekleme—her türlü şekil için çalışır: daireler, resimler, metin kutuları vb. `doc.save()` çağırmadan önce “şekil oluştur → özellikleri ayarla → ekle” adımlarını tekrarlamanız yeterlidir.

Grup zaten diğer şekilleri içeriyorken **add line to group** eklemeniz gerekiyorsa, mevcut grubu şu şekilde alabilirsiniz:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Bu, belge yaşam döngüsünün herhangi bir noktasında bir grubu değiştirebileceğinizi gösterir.

## Sonuç

Artık Java ve Aspose.Words kullanarak bir Word belgesinde **create grouped shapes** nasıl yapılacağını biliyorsunuz. **inserting group shape**, **adding line to group** ve **group multiple shapes word** sayesinde tek bir nesne gibi davranan karmaşık çizimler oluşturabilirsiniz—diyagramlar, şablonlar ve otomatik rapor üretimi için idealdir.

Sonra, bu ilgili konuları keşfedin:

- **Applying styles to grouped shapes** – tüm çocukların dolgu renklerini, kenarlıklarını ve efektlerini bir kerede ayarlamayı öğrenin.  
- **Exporting grouped shapes to PDF** – belgeyi dönüştürdüğünüzde aynı grubun nasıl korunduğunu görün.  
- **Animating shapes with VBA** – Java tarafından oluşturulan grupları Word makrolarıyla birleştirerek etkileşimli belgeler oluşturun.

Farklı şekil tipleri, boyutları ve konumlarıyla denemeler yapmaktan çekinmeyin. Gruplandırma, birçok nesneyi tek bir nesne gibi ele almanızı sağlayarak hem kodu hem de kullanıcı etkileşimini basitleştirir. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Word Belgesi Oluştur Java – Gölge Efektiyle Dikdörtgen Şekli Ekle](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Java ile Word'de Dikdörtgen Şekli Oluştur – Tam Kılavuz](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [.NET için Aspose.Words Kullanarak Word Belgesinde Grup Şekli Oluştur](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}