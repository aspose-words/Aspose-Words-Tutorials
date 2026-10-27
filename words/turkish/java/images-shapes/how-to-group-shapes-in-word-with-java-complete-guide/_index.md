---
category: general
date: 2026-10-16
description: Java kullanarak Word’de şekilleri nasıl gruplayacağınızı öğrenin. Bu
  öğreticide dikdörtgen şekli ekleme, şekil boyutunu ve ölçülerini ayarlama ve belgeyi
  kaydetme gösterilmektedir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: tr
lastmod: 2026-10-16
og_description: Java kullanarak Word'de şekilleri gruplayın. Dikdörtgen şekli ekleyin,
  şekil boyutunu ve ölçülerini ayarlayın ve programlı olarak profesyonel belgeler
  oluşturun.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Java ile Word’de Şekilleri Gruplama – Adım Adım Rehber
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Java ile Word’te Şekilleri Nasıl Gruplandırılır – Tam Kılavuz
url: /tr/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Şekilleri Java ile Nasıl Gruplandırılır – tam kılavuz

Programlı olarak **Word'de şekilleri gruplandırmanız** gerekiyorsa, bu öğretici hazır‑çalıştır çözümünü sunar. **Dikdörtgen şekli ekleme**, boyutunu ayarlama, şekil boyutlarını belirleme ve sonunda gruplandırılmış bir dikdörtgen ve bir elips içeren bir DOCX dosyası kaydetme adımlarını göreceksiniz.

Word'de şekilleri gruplandırmak, karmaşık diyagramlar oluşturmak, yeniden kullanılabilir grafik bileşenleri yaratmak veya belge daha sonra düzenlendiğinde ilgili nesneleri bir arada tutmak için faydalıdır. Kod, herhangi bir yeni JDK ile çalışan ve Microsoft Word'ün kurulu olmasını gerektirmeyen Aspose.Words for Java kütüphanesini kullanır.

## Önkoşullar

Başlamadan önce şunların olduğundan emin olun:

| Gereklilik | Sebep |
|------------|-------|
| Java 17 (veya daha yeni) | Kütüphane modern Java çalışma zamanlarını hedefler. |
| Aspose.Words for Java (en son sürüm) | Örnekte kullanılan `Document`, `DocumentBuilder`, `GroupShape` ve `Shape` sınıflarını sağlar. |
| Bir IDE veya derleme aracı (Maven/Gradle) | Örneği derlemek ve çalıştırmak için. |
| Java sözdizimi hakkında temel bilgi | Kod akışını anlamak için gereklidir. |

Aspose.Words bağımlılığını projenize ekleyin. Maven için:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Veya Gradle için:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Çözümün genel görünümü

Öğretici, net bir **problem → çözüm → açıklama** modeli izler:

1. **Yeni bir Word belgesi oluştur** ve bir `DocumentBuilder` al.  
2. **Bir `GroupShape` konteyneri ekle**; bu konteyner birden fazla şekli tutacak.  
3. **Bir dikdörtgen ekle**, genişlik/yüksekliğini ayarla (**şekil boyutunu ayarla** adımı) ve gruba bağla.  
4. **Bir elips ekle**, aynı grup içinde konumlandır ve boyutlarını da ayarla.  
5. **Belgeyi kaydet**.

Her adım, kodun **neden** yapıldığını açıklar; böylece API'nin ne yaptığını ve diğer senaryolara nasıl uyarlayabileceğinizi anlarsınız.

## Adım 1: Belgeyi ve bir DocumentBuilder'ı oluştur

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Neden önemli:** `Document`, tüm DOCX dosyasını temsil ederken, `DocumentBuilder` düşük seviyeli düğüm yönetimiyle uğraşmadan içerik eklemenizi sağlayan bir yardımcıdır. İlk önce bunları oluşturmak, sonraki tüm şekil işlemleri için temiz bir tuval sağlar.

## Adım 2: Bir GroupShape konteyneri ekle

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`GroupShape`, çizim nesneleri için bir **klasör** gibi çalışır. Grubu taşıdığınızda, döndürdüğünüzde veya sildiğinizde tüm alt şekiller otomatik olarak izler. Bu, **Word'de şekilleri gruplandırma** özelliğinin temelidir.

## Adım 3: Bir dikdörtgen şekli ekle – dikdörtgen şekil kodu

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – `Shape` yapıcıya `ShapeType.RECTANGLE` geçirilir; bu, Aspose.Words'e dikdörtgen bir kontur çizmeyi söyler.  
- **set shape size** – `setWidth` ve `setHeight`, **şekil boyutlarını** puan cinsinden tanımlar (1 pt = 1/72 in). Görsel boyutu kontrol etmenin en yaygın yoludur.  
- **Why we use `appendChild`** – Dikdörtgeni `GroupShape`'e ekler, böylece grup ile birlikte hareket eder.

## Adım 4: Bir elips ekle ve grup içinde konumlandır

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

Elips, basit bir dikdörtgenden farklı **şekil boyutlarını ayarlama** örneği sunar. `setLeft` çağrısı, grup içinde yatay kaydırmayı kontrol eder; bu, birden çok nesneyi düzenlerken faydalıdır.

## Adım 5: Belgeyi kaydet

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

*GroupShapeDemo.docx* dosyasını Microsoft Word'de açtığınızda, tek bir grup içinde kilitlenmiş bir dikdörtgen ve bir elips göreceksiniz. Her iki şekilden birini seçmek, tüm grubu seçer – **Word'de şekilleri gruplandırma** beklentiniz tam olarak budur.

## Tam, çalıştırılabilir örnek

Tüm parçaları bir araya getirerek, IDE'nize kopyalayabileceğiniz tam kaynak dosyası aşağıdadır:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Beklenen çıktı

- Proje klasöründe **GroupShapeDemo.docx** adlı bir dosya oluşur.  
- Word'de dosyayı açtığınızda iki şekil (dikdörtgen ve elips) birlikte gruplandırılmış olarak görünür.  
- Her iki şekilden birini sürüklemek bütün grubu hareket ettirir; bu da **Word'de şekilleri gruplandırma** işlevinin doğru çalıştığını gösterir.

## Yaygın varyasyonlar ve kenar durumları

| Senaryo | Ne değiştirilmeli | Neden |
|---------|-------------------|-------|
| **Farklı şekil tipleri** (ör. üçgen) | `Shape` oluştururken `ShapeType.TRIANGLE` veya başka bir enum değeri kullanın. | Daha karmaşık diyagramlar oluşturmanıza olanak tanır. |
| **Dolgu rengi ayarlama** | Şekli oluşturduktan sonra `shape.getFillColor().setColor(Color.BLUE);` çağırın. | Görsel görünümü iyileştirir, gruplamayı etkilemez. |
| **Grubu döndürme** | `groupShape.setRotationAngle(45);` | Tüm alt şekilleri birlikte döndürür; simgeler için kullanışlıdır. |
| **Şekil içine metin ekleme** | `shape.appendChild(new Paragraph(document));` ardından bir `Run` ile metin ekleyin. | Şekli etiket veya açıklama gibi kullanılabilir. |
| **Akıma kaydetme** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Belgeyi doğrudan döndüren web servisleri için faydalıdır. |

### Pro ipucu

Dinamik veriye (ör. barkod uzunluğu) dayalı **şekil boyutlarını ayarlamanız** gerektiğinde, önce genişlik/yüksekliği puan cinsinden hesaplayın:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

Bu, sabit değerler kullanmaktan kaçınır ve kodunuzun uyarlanabilirliğini artırır.

## Sonuç

Artık Java kullanarak **Word'de şekilleri gruplandırma**, **dikdörtgen şekli ekleme**, **şekil boyutunu ayarlama** ve **şekil boyutlarını ayarlama** konularını üretim‑hazır kodla biliyorsunuz. Yukarıdaki adımları izleyerek yeniden kullanılabilir grafik grupları oluşturabilir, bunları otomatik raporlara ekleyebilir veya Word'ü manuel olarak açmadan özel diyagram araçları geliştirebilirsiniz.

### Sıradaki adım ne?

- **add rectangle shape** varyasyonlarını keşfedin; örneğin köşeleri yuvarlatılmış dikdörtgen (`ShapeType.RECTANGLE` ile `setCornerRadius`).  
- **group shapes in word** özelliğini tablolar veya grafiklerle birleştirerek daha zengin belgeler oluşturun.  
- **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) gibi Aspose.Words API'lerini inceleyerek çevre metnin şekillerinizle nasıl etkileşeceğini kontrol edin.

Deneyler yapmaktan, **rectangle shape code**'u uyarlamaktan ve sonuçlarınızı paylaşmaktan çekinmeyin.


## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımları keşfetmeniz için adım‑adım açıklamalı tam çalışan kod örnekleri içerir.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}