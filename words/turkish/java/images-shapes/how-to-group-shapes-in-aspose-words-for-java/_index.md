---
category: general
date: 2026-10-20
description: Aspose.Words for Java'da şekilleri nasıl gruplayacağınızı öğrenin – dikdörtgen
  şekil eklemeyi, bunları gruplamayı ve belgeyi kaydetmeyi tek bir rehberde.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: tr
lastmod: 2026-10-20
og_description: Aspose.Words for Java'da şekilleri nasıl gruplayabilirsiniz. Bu öğreticide
  dikdörtgen şekli nasıl ekleyeceğiniz, onları nasıl gruplayacağınız ve sonucu nasıl
  dışa aktaracağınız gösterilmektedir.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Aspose.Words for Java'da şekilleri gruplama – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Aspose.Words for Java'da şekilleri nasıl gruplandırılır
url: /tr/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java'da şekilleri gruplama

Aspose.Words for Java kullanarak bir Word belgesinde **how to group shapes** yapmanız gerekiyorsa, bu kılavuz size tam iş akışını gösterir. **insert rectangle shape** nasıl yapılacağını, ikinci bir dikdörtgen eklemeyi, iki şekli gruplamayı ve sonunda dosyayı kaydetmeyi öğreneceksiniz—hepsi net, çalıştırılabilir kodlarla.

Şekilleri gruplamak, birden fazla çizimi tek bir birim olarak taşımak, döndürmek veya stil vermek istediğinizde faydalıdır. Rapor şablonu, diyagram veya özel bir broşür oluşturuyor olun, şekil gruplamayı ustalaşmak zaman kazandırır ve düzeninizin tutarlı kalmasını sağlar.

In this tutorial you will:

* Yeni bir `Document` ve bir `DocumentBuilder` oluşturun.
* **How to insert rectangle** şekillerini kesin boyutlarla ekleyin.
* Dikdörtgenleri bir `GroupShape` içine gruplayın.
* Belgeyi kaydedin ve sonucu doğrulayın.

> **Prerequisite** – Projenize Aspose.Words for Java (v23.12 veya daha yeni) eklemiş olmalısınız. Maven kullanıcıları aşağıda gösterilen bağımlılığı ekleyebilir.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## İhtiyacınız olanlar

| Öğe | Sebep |
|------|--------|
| Java 17+ | Modern dil özellikleri ve daha iyi performans |
| Aspose.Words for Java | `DocumentBuilder`, `Shape` ve `GroupShape` API'lerini sağlar |
| An IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | Örneği derlemek ve çalıştırmak için |
| Write permission to a folder | Belge diske kaydedilecektir |

## Dikdörtgen şekli ekleme

İlk adım bir `Document` ve bir `DocumentBuilder` oluşturmaktır. Builder, çizim nesnelerini yerleştirmek için `insertShape` gibi yöntemler sunar.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Why this matters** – `insertShape` kullanmak, Aspose.Words'te **how to insert rectangle** nesnelerini eklemenin standart yoludur. Şekli otomatik olarak belgenin geçerli paragrafına ekler, böylece düşük seviyeli OpenXML ile uğraşmanız gerekmez.

## Dikdörtgen konumlarını ayarlama (isteğe bağlı)

İkinci dikdörtgenin birincisine göre özel bir konuma ihtiyacı varsa, `left` ve `top` özelliklerini değiştirebilirsiniz. Bu adım isteğe bağlıdır ancak genellikle kesin diyagram düzeni için gereklidir.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Pro tip:** Tüm ölçümler puan cinsindendir (1 pt ≈ 1/72 in). UI tabanlı hesaplamalar için piksel değerlerine ihtiyacınız varsa `convertPointsToPixels` kullanın.

## Şekilleri gruplama

Dikdörtgenler artık mevcut olduğuna göre, onları bir `GroupShape` içine yerleştirebilirsiniz. Gruplama, iki dikdörtgenin tek bir nesne gibi davranmasını sağlar—grubu taşımak, döndürmek veya biçimlendirmek her iki şekli de etkiler.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Why grouping works** – `GroupShape`, `Shape` sınıfından miras alır, bu yüzden grubu diğer çizim nesneleri gibi aynı şekilde kullanabilirsiniz. `appendChild` çağırdığınızda, şekiller orijinal konumlarından kaldırılır ve grubun çocuğu haline gelir.

## Gruplanmış şekilleri içeren belgeyi kaydetme

Son olarak, belgeyi diske yazın. Dosya içinde iki dikdörtgen bulunan tek bir `GroupShape` içerecek.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Beklenen sonuç

Microsoft Word'de `GroupShape.docx` dosyasını açın:

* Yan yana konumlandırılmış iki dikdörtgen (mavi ve yeşil) göreceksiniz.
* Herhangi bir dikdörtgeni seçmek tüm grubu seçer—sürüklemek ikisini birlikte hareket ettirir.
* Grup ince kırmızı bir kenarlığa sahiptir, bu da `GroupShape` özelliklerinin uygulandığını doğrular.

Gruba sağ tıklayıp **Group → Ungroup** seçerseniz, dikdörtgenler bağımsız şekillere geri döner ve gruplama işleminin geri alınabilir olduğunu gösterir.

## Yaygın varyasyonlar ve uç durumlar

| Durum | Nasıl ele alınır |
|-----------|------------------|
| **More than two shapes** | Her şekli ekleyin, ardından hepsini aynı `GroupShape` içine ekleyin. |
| **Different shape types** (e.g., ellipse, picture) | `builder.insertShape(ShapeType.ELLIPSE, …)` veya `builder.insertImage(...)` kullanarak ekleyin, ardından ekleyin. |
| **Scaling the group** | `group.setWidth(newWidth)` veya `group.setHeight(newHeight)` çağırın; çocuklar orantılı olarak ölçeklenir. |
| **Rotating the group** | `group.setRotationAngle(45);` grubu merkez etrafında döndürür. |
| **Preserving original positions** | Gruplamadan önce her şeklin `left`/`top` değerlerini saklayın ve gerekirse gruptan çıkardıktan sonra geri yükleyin. |

## Tam, çalıştırılabilir örnek

Aşağıda IDE'nize kopyalayıp yapıştırabileceğiniz tam Java sınıfı bulunmaktadır. Tüm importları, hata yönetimini ve açıklamaları içerir.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Programı çalıştırın, oluşan `GroupShape.docx` dosyasını açın ve açıklanan şekilde gruplandırılmış dikdörtgenleri göreceksiniz.

## Sonuç

Artık Aspose.Words for Java'da **how to group shapes** nasıl yapılacağını biliyorsunuz; belge oluşturma, dikdörtgen şekilleri ekleme, konumlarını ayarlama ve sonunda `GroupShape` ile gruplama adımlarını gördünüz. Bu teknik, birden fazla çizimi tek bir varlık gibi ele almanızı sağlar, düzen ayarlamalarını ve görsel tutarlılığı basitleştirir.

**Next steps**

* **how to insert rectangle** şekillerini farklı dolgu desenleri veya kenarlıklarla keşfedin.
* **insert rectangle shape**'i metin kutularıyla birleştirerek etiketli diyagramlar oluşturun.
* Grubu döndürerek veya ölçeklendirerek daha karmaşık grafikler üretmeyi deneyin.

Kodları diğer şekil tipleri, daha büyük gruplar veya dinamik belge oluşturma senaryoları için uyarlamaktan çekinmeyin. İyi kodlamalar!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalarla tam çalışan kod örnekleri içerir.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [how to insert group shape in Java – Complete Guide](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [How to Set Shadow on a Shape in Aspose.Words – Complete Guide](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}