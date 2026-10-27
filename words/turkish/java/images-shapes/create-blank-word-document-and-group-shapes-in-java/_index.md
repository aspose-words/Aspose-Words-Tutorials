---
category: general
date: 2026-08-23
description: Aspose.Words for Java ile boş bir Word belgesi oluşturun, şekilleri nasıl
  gruplayacağınızı, dikdörtgen şeklinin rengini nasıl değiştireceğinizi öğrenin ve
  belgeyi dakikalar içinde docx olarak kaydedin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: tr
lastmod: 2026-08-23
og_description: Aspose.Words for Java ile boş bir Word belgesi oluşturun, ardından
  şekilleri gruplamayı, dikdörtgen şekline renk vermeyi ve belgeyi docx olarak verimli
  bir şekilde kaydetmeyi görün.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Java’da boş Word belgesi oluşturun ve şekilleri gruplayın – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Java'da boş Word belgesi oluştur ve şekilleri grupla
url: /tr/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş Word belgesi oluşturma ve Java'da şekilleri gruplama

Programlı olarak **boş Word belgesi oluşturmak** istiyorsanız, Aspose.Words for Java bunu oldukça basit hale getirir. Bu öğreticide tam olarak nasıl **boş Word belgesi oluşturacağınızı**, **Word'de grup şekilleri ekleyeceğinizi**, **renkli dikdörtgen şekli** uygulayacağınızı ve sonunda **belgeyi docx olarak kaydetmeyi** göstereceğiz. Sonunda, herhangi bir Java projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız.

Öğrenecekleriniz:

* Aspose.Words için gerekli Maven/Gradle bağımlılığı.
* Boş bir belge ve bir `DocumentBuilder` nasıl başlatılır.
* `GroupShape` içinde **şekilleri nasıl gruplayacağınız** adımları.
* Dikdörtgen şekillerine dolgu renklerinin nasıl ayarlanacağı.
* **Belgeyi docx olarak kaydetme** için en iyi uygulama ve çıktı dosyasının nerede bulunacağı.

Aspose.Words ile daha önce bir deneyiminiz olması gerekmez, ancak temel Java geliştirme konusunda rahat olmalı ve JDK 8 veya daha yeni bir sürüm yüklü olmalıdır.

---

## Gereksinimler

| Gereksinim | Sürüm / Detay |
|-------------|-------------------|
| Java Development Kit | 8 veya üzeri |
| Derleme aracı | Maven 3+ veya Gradle 6+ |
| Aspose.Words for Java | 23.12 veya daha yeni (yazım anındaki en son sürüm) |
| IDE (isteğe bağlı) | IntelliJ IDEA, Eclipse, VS Code veya herhangi bir Java‑uyumlu editör |

---

## Adım 1: Aspose.Words'ü projenize ekleyin

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro ipucu:** Kurumsal bir proxy kullanıyorsanız, resmi dokümanlarda açıklandığı gibi Maven/Gradle'ı Aspose deposundan paketi çekecek şekilde yapılandırın.

---

## Adım 2: **Boş Word belgesi** oluşturma ve bir builder kullanma

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` yapıcı (constructor) bellekte boş bir `.docx` konteyneri oluşturur. `DocumentBuilder` ise içerik eklemek için akıcı bir API sağlar; şekiller de buna dahildir.

---

## Adım 3: **Word'de grup şekilleri** konteyneri ekleme

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

`GroupShape`, mini bir tuval gibi çalışır. İçine eklenen tüm şekiller birlikte hareket eder; bu da **şekilleri gruplamanın** düzen tutarlılığı açısından tam olarak ne anlama geldiğini gösterir.

---

## Adım 4: İlk **renkli dikdörtgen şekli** (kırmızı) ekleme

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

`ShapeType.RECTANGLE` sabiti basit bir dikdörtgen oluşturur. `getFill().setForeColor(...)` çağrısı **renkli dikdörtgen şekli**nizi kontrol etmenizi sağlar. `java.awt.Color.RED` yerine herhangi bir `java.awt.Color` sabiti ya da özel RGB değeri kullanabilirsiniz.

---

## Adım 5: İkinci **renkli dikdörtgen şekli** (yeşil) ekleme ve konumlandırma

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

`setLeft` (veya `setTop`) çağrısı, şekli **Word'de grup şekilleri** konteynerinin sol‑üst köşesine göre hareket ettirir. Bu, **şekilleri gruplama** sırasında kesin konumlandırmanın nasıl yapılacağını gösterir.

---

## Adım 6: **Belgeyi docx olarak kaydetme** ve sonucu doğrulama

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save` yöntemi dosya uzantısı `.docx` olduğu için otomatik olarak bir `.docx` dosyası yazar. Farklı bir format (ör. PDF) isterseniz uygun `SaveFormat` enum değerini geçirin.

> **İpucu:** Hedef dizinin (`output/` bu örnekte) var olduğundan emin olun veya `new File("output").mkdirs();` ile programatik olarak oluşturun.

---

## Hızlı kopyala‑yapıştır için tam kaynak kodu

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Beklenen çıktı:** `GroupShapeDemo.docx` dosyasını Microsoft Word'de açtığınızda, iki renkli dikdörtgenin (sol tarafta kırmızı, sağ tarafta yeşil) bulunduğu tek bir sayfa görürsünüz; grup seçildiğinde ikisi birlikte hareket eder.

---

## Yaygın sorular ve kenar‑durum yönetimi

| Soru | Cevap |
|----------|--------|
| *Aynı gruba iki'den fazla şekil ekleyebilir miyim?* | Evet. Her ek şekil için `groupShape.appendChild(yourShape)` çağırın. Grup, en uzak kenarlara göre otomatik olarak yeniden boyutlanır; isterseniz genişlik/yüksekliği manuel ayarlayabilirsiniz. |
| *Farklı bir şekil türüne (ör. elips) ihtiyacım olursa?* | `ShapeType.RECTANGLE` yerine `ShapeType.ELLIPSE` kullanın. Aynı dolgu‑renk mantığı geçerlidir. |
| *`Document` nesnesini serbest bırakmam (dispose) gerekiyor mu?* | Aspose.Words yerel kaynakları dahili olarak yönetir. JVM sonlandığında kaynaklar serbest bırakılır. Uzun‑çalışan uygulamalarda, **Aspose.Words for Java (Native)** sürümünü kullanıyorsanız `doc.dispose();` çağırabilirsiniz. |
| *Z‑order'ı değiştirerek bir dikdörtgenin diğerinin üzerinde görünmesini nasıl sağlarım?* | Çocukları yeniden sıralamak için `groupShape.insertAfter(shape, referenceShape);` veya `groupShape.insertBefore(shape, referenceShape);` kullanın. |
| *Farklı bölümlerdeki şekilleri gruplayabilir miyim?* | Hayır. `GroupShape` tek bir paragraf veya şekil konteyneri içinde bulunmalıdır. Bölümler arasında grup oluşturmak istiyorsanız, her bölümde ayrı gruplar oluşturun. |

---

## Sonuç

Artık Aspose.Words for Java ile **boş Word belgesi oluşturma**, **Word'de şekilleri gruplama**, **renkli dikdörtgen şekli** stilini uygulama ve **belgeyi docx olarak kaydetme** konularını biliyorsunuz. Bu desen, daha karmaşık düzenlere ölçeklenebilir—ek şekiller ekleyin, ofsetleri ayarlayın ve isteğe bağlı olarak grup içinde metin, resim veya bağlantılar ekleyin.

**İleriki adımlar** olarak şunları keşfedebilirsiniz:

* **Word'de grup şekilleri** kullanarak akış şemaları veya UI mock‑up'ları oluşturma.
* **Belgeyi docx olarak kaydetme** ile PDF dönüşümünü (`doc.save("out.pdf")`) birleştirme.
* **Renkli dikdörtgen şekli**ne degrade veya desen uygulayarak daha zengin görsel tasarımlar elde etme.
* Gelişmiş raporlama belgeleri için gruplandırılmış şekilleri tablolar veya grafiklerle birleştirme.

Boyutları, renkleri veya şekil türlerini projenizin marka kimliğine göre değiştirmekten çekinmeyin. Mutlu kodlamalar!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak ilgili konuları ayrıntılı bir şekilde ele alır. Her kaynak, tam çalışan kod örnekleri ve adım adım açıklamalar içerir; böylece ek API özelliklerini ustalaşabilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Word Belgesi Oluşturma Java – Gölgelendirme Efektiyle Dikdörtgen Şekil Ekleme](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java ile belgeyi PDF olarak kaydetme](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Aspose.Words for Java'da Belge Şekillerini Kullanma](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}