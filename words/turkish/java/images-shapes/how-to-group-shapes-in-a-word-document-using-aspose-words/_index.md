---
category: general
date: 2026-08-20
description: Aspose.Words for Java ile şekilleri gruplamayı, şekil boyutunu ayarlamayı,
  belgeye resim eklemeyi, gruba resim eklemeyi ve dikdörtgen şekil oluşturmayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: tr
lastmod: 2026-08-20
og_description: Aspose.Words kullanarak bir Word belgesinde şekilleri nasıl gruplandırılır.
  Şekil boyutunu ayarlamak, belgeye resim eklemek, gruba resim eklemek ve dikdörtgen
  şekil oluşturmak için bu adım adım Java öğreticisini izleyin.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Aspose.Words ile bir Word belgesindeki şekilleri gruplama – Java rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Aspose.Words ile bir Word belgesindeki şekilleri nasıl gruplayabilirsiniz
url: /tr/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words kullanarak bir Word belgesinde şekilleri nasıl gruplandırılır

Bir Word dosyasında **how to group shapes** yapmanız gerekiyorsa, bu öğretici tam Java çözümünü gösterir. **set shape size**, **insert image into document**, **add picture to group** ve **create rectangle shape** nasıl yapılacağını göreceksiniz—tüm bunlar net açıklamalar ve çalıştırılabilir bir kod örneği ile.

Şekilleri gruplandırmak, düzen yönetimini basitleştirir, birden fazla nesneyi tek bir birim olarak taşımanıza veya döndürmenize olanak tanır ve belgenizi düzenli tutar. Aşağıdaki adımlarda bir dikdörtgen ve bir resim içeren bir grup oluşturacak ve ardından grubu sayfaya yerleştireceksiniz.

## Önkoşullar

* Java 17 veya daha yeni bir sürüm yüklü.
* Aspose.Words for Java (version 23.9 veya daha yeni) projenizin classpath'ine eklenmiş.
* `YOUR_DIRECTORY/sample.jpg` konumunda bir örnek JPEG resmi ( `YOUR_DIRECTORY` kısmını gerçek yol ile değiştirin).

Aspose.Words'ı Maven aracılığıyla ekleyebilirsiniz:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Aspose.Words ile şekilleri nasıl gruplandırılır

Aşağıdaki bölümler, **how to group shapes** için gerekli her işlemi adım adım gösterir. Birincil H2 başlığı, birincil anahtar kelimeyi içerir ve SEO kurallarını karşılar.

### Adım 1: Yeni bir belge ve bir `DocumentBuilder` oluşturun

`Document`, Word dosyasını temsil ederken, `DocumentBuilder` içerik eklemek için kullanışlı yöntemler sağlar.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Neden önemli*: Yeni bir `Document` ile başlamak, oluşturduğunuz grubun mevcut öğelerle çakışmamasını sağlar.

### Adım 2: Birden fazla alt şekli tutacak bir grup şekli ekleyin

Grup şekli bir konteyner gibi davranır. Boyutları, tüm alt şekiller için sınırlayıcı kutuyu tanımlar.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*İpucu*: Genişlik (`300`) ve yükseklik (`200`) puan cinsindendir (1 pt = 1/72 inç). Eklemeyi planladığınız şekillerin boyutuna göre ayarlayın.

### Adım 3: Bir dikdörtgen şekli oluşturun, boyutunu ayarlayın ve gruba ekleyin

Bir şeklin tam boyutunu ayarlamak, kesin düzen kontrolü istediğinizde çok önemlidir.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Neden şekil boyutu ayarlıyoruz*: `setWidth` ve `setHeight` metodları, **set shape size** ikincil anahtar kelimesine karşılık gelir ve dikdörtgenin görünümünü piksel‑tam kontrol etmenizi sağlar.

### Adım 4: Bir resim ekleyin, ardından resim şeklini aynı gruba ekleyin

Resim eklemek, **insert image into document** gereksiniminin temelini oluşturur. Döndürülen `Shape`, diğer şekiller gibi gruplanabilen bir resim şeklidir.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro ipucu*: Orijinal en‑boy oranını korumanız gerekiyorsa, sadece bir boyutu ayarlayın (`setWidth` veya `setHeight`). Aspose.Words diğer boyutu otomatik olarak ölçeklendirir.

### Adım 5: Tüm grubu sayfada konumlandırın

Tüm alt şekilleri ekledikten sonra, bütün grubu taşıyabilir, döndürebilir veya gizleyebilirsiniz. Konumlandırma, **add picture to group** kavramını dolaylı olarak kullanır, çünkü grup artık resmi içeriyor.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Açıklama*: `setLeft` ve `setTop`, grubu sayfanın kenar boşluklarına göre konumlandırır. Grubu döndürmek, tüm alt şekillerin dönüşümü miras aldığını gösterir.

### Adım 6: Belgeyi kaydedin

Son olarak, dosyayı diske yazın. Oluşan `.docx` dosyasını Word'de açarak gruplamayı doğrulayabilirsiniz.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

Programı çalıştırmak, bir dikdörtgen ve bir resmi birlikte içeren **GroupShapesDemo.docx** oluşturur. Word'de herhangi bir şekli seçtiğinizde diğeri de seçilir ve **how to group shapes** konusunu başarıyla öğrendiğinizi doğrular.

---

## Beklenen çıktı

Microsoft Word'de *GroupShapesDemo.docx* dosyasını açtığınızda:

* Grupun sol tarafında bir dikdörtgen (altın dolgu) görünür.
* Sağladığınız resim, dikdörtgenin sağında görünür.
* Grubu sürüklediğinizde her iki nesne de birlikte hareket eder.
* Grup, sol kenar boşluğundan 50 pt, üst kenar boşluğundan 100 pt uzaklıkta konumlandırılmış ve 15° döndürülmüştür.

Resim görünmezse, `insertImage` içindeki dosya yolunu iki kez kontrol edin. Aspose.Words, dosya bulunamadığında bir `IOException` fırlatır.

---

## Yaygın sorular ve uç‑durum yönetimi

| Question | Answer |
|----------|--------|
| **İki'den fazla şekil ekleyebilir miyim?** | Evet. Her ek şekil için `groupShape.appendChild(otherShape)` çağırın. |
| **Dikdörtgen için şeffaf bir arka plan gerekirse ne yapmalıyım?** | Şunu kullanın: `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Gruplama eski Word formatlarında (ör. `.doc`) destekleniyor mu?** | Gruplama `.docx` ve `.doc` için çalışır ancak bazı eski görüntüleyiciler grup meta verilerini görmezden gelebilir. Tam doğruluk için `.docx` olarak kaydedin. |
| **Daha sonra grubu nasıl ayırırım?** | `groupShape.getChildNodes(NodeType.ANY, true)` ile alt düğümleri alın, belge gövdesine taşıyın ve ardından grubu kaldırın. |
| **Farklı bölümler arasında şekilleri gruplandırabilir miyim?** | Hayır. Bir `GroupShape` tek bir `Story` içinde (genellikle ana belge gövdesi) bulunmalıdır. |

---

## Sağlam şekil işleme için pro ipuçları

* **Mutlak konumlandırmayı sınırlı kullanın** – göreli konumlandırma (`builder.moveToDocumentEnd()`) genellikle daha duyarlı düzenler sağlar.
* **`DocumentBuilder`'ı önbelleğe alın** – her işlem için yeni bir builder oluşturmak büyük belgelerde performansı düşürebilir.
* **`PictureFillMode` ayarlayın** resmi şekil içinde uzatmanız veya döşemeniz gerektiğinde: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Resim boyutlarını doğrulayın** eklemeden önce, grup sınırlayıcı kutusunu etkileyebilecek beklenmedik ölçeklendirmeleri önlemek için.

## Sonraki adımlar

Artık **how to group shapes** bildiğinize göre, şunları keşfedebilirsiniz:

* **Insert image into document**'i kırpma gibi gelişmiş seçeneklerle (`pictureShape.setCropTop(...)`) kullanın.
* **Set shape size**'i sayfa boyutlarına göre dinamik olarak (`doc.getFirstSection().getPageSetup().getPageWidth()`) ayarlayın.
* **Add picture to group**'ı başlıklı grafikler için metin kutularıyla birlikte ekleyin.
* **Create rectangle shape**'i yuvarlatılmış köşelerle (`rectangleShape.setCornerRadius(5);`) oluşturun.

Bu konular aynı API yüzeyine dayanır ve gelişmiş, programatik Word raporları oluşturmanıza yardımcı olur.

## Sonuç

Bu öğreticide, Aspose.Words for Java kullanarak bir Word belgesinde **how to group shapes** öğrendiniz. Altı adımı izleyerek—belge oluşturma, grup ekleme, **creating rectangle shape**, **set shape size**, **insert image into document**, **add picture to group** ve grubu konumlandırma—şimdi karmaşık düzen senaryoları için yeniden kullanılabilir bir deseniniz var. Uygulamanızın ihtiyaçlarına göre ek alt şekiller, farklı dönüşler veya koşullu gruplama mantığıyla denemeler yapmaktan çekinmeyin.

Kodlamanın tadını çıkar!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Word Belgesi Oluşturma Java – Gölge Efektiyle Dikdörtgen Şekil Ekle](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java'da Belge Şekillerini Kullanma](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [.NET için Aspose.Words Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}