---
category: general
date: 2026-11-22
description: Java ile bir Word belgesine dikdörtgen şekli ekleyin, şekil boyutunu
  ayarlayın, birden fazla şekli gruplayın ve şekli gruba verimli bir şekilde ekleyin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: tr
lastmod: 2026-11-22
og_description: Java kullanarak bir Word belgesine dikdörtgen şekli ekleyin, ardından
  şekil boyutunu ayarlayın, birden fazla şekli gruplayın ve tek bir iş akışında şekli
  gruba ekleyin.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Java’da dikdörtgen şekli ekleyin ve şekilleri gruplayın – tam rehber
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Java'da dikdörtgen şekli ekle ve şekilleri grupla
url: /tr/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da dikdörtgen şekli ekleme ve şekilleri gruplama

Bir Word belgesine **dikdörtgen şekli eklemek** istiyorsanız, bu kılavuz tam adımları size gösterir. Ayrıca **şekil boyutunu ayarlamayı**, **birden fazla şekli gruplamayı** ve **şekli gruba eklemeyi** IDE’den çıkmadan öğrenebileceksiniz.

DOCX dosyası içinde vektör grafikleriyle çalışmak genellikle ayrı API’lerle uğraşmak gibi hissettirebilir. Bu öğreticinin sonunda, bir dikdörtgen, bir elips ve ihtiyacınız olabilecek diğer şekilleri oluşturan, ardından bunları tek bir nesne gibi hareket ettirecek şekilde gruplayan tek bir, bağımsız programınız olacak. Aspose.Words for Java dışındaki hiçbir araç gerekmeyecek.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* Java 17 veya daha yeni bir sürüm.
* Bağımlılıkları yönetmek için Maven 3.8+ (veya Gradle).
* Geçerli bir Aspose.Words for Java lisansı (deneme sürümü test için çalışır).
* IntelliJ IDEA veya VS Code gibi bir IDE, ancak herhangi bir metin düzenleyici de kullanılabilir.

Bu gereksinimler, kodun modern bir geliştirme ortamında derlenip çalıştırılmasını sağlar.

## Adım 1: Maven projesini ayarlama

Yeni bir Maven projesi oluşturun veya mevcut bir `pom.xml` dosyasına Aspose.Words bağımlılığını ekleyin:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

Bağımlılık, `Document`, `DocumentBuilder`, `Shape` ve `GroupShape` gibi belge manipülasyonu için gereken tüm sınıfları getirir. Maven, `mvn compile` komutunu çalıştırdığınızda JAR dosyalarını otomatik olarak indirir.

## Adım 2: Belgeyi yükleyin ve bir DocumentBuilder oluşturun

`DocumentBuilder`, içerik eklemek için akıcı bir API sağlar. Mevcut bir DOCX dosyasını yükleyin veya boş bir belgeden başlayın:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder’ı erken oluşturmak, belge başında bir imleç konumlandırır ve şekil eklemeye hazır hâle getirir.

## Word belgesine dikdörtgen şekli ekleme

### Adım 3: Dikdörtgen şekli ekleme

Dikdörtgen, belge içine yerleştirmek istediğimiz ilk görsel öğedir. `Shape` yapıcısını `ShapeType.RECTANGLE` ile kullanarak tamamen düzenlenebilir bir nesne elde edersiniz.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Bu noktada dikdörtgen eklenmesi, boyutu tanımlanıp bir kapsayıcıya eklenene kadar yerleşimi etkilemez.

### Şekil boyutunu ve ölçülerini ayarlama

#### Adım 4: Genişlik ve yükseklik tanımlama

Şeklin ölçülerini ayarlamak, sayfada nasıl görüneceğini belirler. Genişlik ve yükseklik değerleri puan cinsindendir (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Bu sayıları tasarım gereksinimlerinize göre ayarlayabilirsiniz. Aynı yöntemler herhangi bir `Shape` örneği için geçerlidir; böylece daireler, oklar veya özel çizimler için de yeniden kullanılabilir.

#### Adım 5: Dikdörtgeni belgeye ekleme

Şeklin boyutu belirlendikten sonra, sayfaya yerleştirin. `DocumentBuilder`’ın `insertShape` metodu, şekli mevcut imleç konumuna ekler.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

Bu aşamada dikdörtgen sayfada tek başına görünür. Sonraki adımlar, onu diğer şekillerle birleştirmeyi gösterir.

## Birden fazla şekli birlikte gruplama

Şekilleri gruplamak, onları tek bir birim olarak taşımanıza, döndürmenize veya yeniden boyutlandırmanıza olanak tanır. Bu, karmaşık diyagramlar oluştururken özellikle faydalıdır.

### Adım 6: Grup şekli kapsayıcısı oluşturma

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`insertGroupShape` çağrısı, belgeye boş bir kapsayıcı ekler. Bu kapsayıcıya eklenen tüm şekiller grup içinde yer alır.

### Şekli gruba ekleme

#### Adım 7: Dikdörtgeni gruba ekleme

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

Ekleme, dikdörtgeni belge gövdesinden grubun iç koleksiyonuna taşır. Dikdörtgen artık grup dönüşümlerine uyar.

#### Adım 8: Demonstrasyon için bir elips ekleme

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

Elips, dikdörtgenle aynı koordinat uzayını paylaşır; gerekirse `setLeft` ve `setTop` özelliklerini ayarlayarak görsel olarak hizalayabilirsiniz.

### Adım 9: Belgeyi kaydetme

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

Programı çalıştırdığınızda `output.docx` oluşturulur. Dosyayı Microsoft Word veya LibreOffice’da açın; bir dikdörtgen ve bir elipsin birlikte gruplandığını göreceksiniz. Her iki şekli de seçtiğinizde tüm grup vurgulanır ve **şekli gruba ekleme** işleminin başarılı olduğu kanıtlanır.

![Add rectangle shape example in Java](image.png){alt="Java’da dikdörtgen şekli ekleme örneği"}

*Ekran görüntüsü, tek bir grup içinde bulunan dikdörtgen ve elipsi, ortak bir şekilde manipüle edilebilir halde gösterir.*

## Bu yaklaşımın önemi

* **Tek kaynak gerçeği** – Tüm şekil özellikleri grup oluşturulmadan önce ayarlandığından, yerleşim hataları önlenir.
* **Yeniden kullanılabilirlik** – Aynı `setWidth`/`setHeight` metodları herhangi bir şekil için çalışır; örneği oklar, yıldızlar veya özel SVG’ler için genişletebilirsiniz.
* **Performans** – Gruplama, Word render’ının işlemesi gereken çizim nesnesi sayısını azaltır, bu da büyük belgelerin açılma hızını artırır.
* **Bakım kolaylığı** – Şekil oluşturma ve gruplama mantığını bir arada tutarak, gelecekteki geliştiricilerin boyutları değiştirmesini veya yeni şekiller eklemesini, alakasız kodlar arasında arama yapmadan yapmasını sağlar.

## Yaygın varyasyonlar ve kenar durumları

| Senaryo | Ayarlama |
|----------|------------|
| **Farklı birimler** | `PointsToPixels` dönüşümünü kullanın veya satır içi yerleştirme için `Shape.setWrapType(WrapType.INLINE)` ayarlayın. |
| **Grubu döndürme** | `groupShape.setRotation(45);` ile tüm alt şekilleri 45° döndürün. |
| **Şekle metin ekleme** | Boyut ayarlandıktan sonra `Shape.setText("Label");` kullanın. |
| **Dinamik boyutlandırma** | `doc.getFirstSection().getPageSetup().getPageWidth()` ile sayfa ölçülerini alın ve şekil boyutlarını orantılı olarak hesaplayın. |

Bu varyasyonlar, temel deseni—**dikdörtgen şekli ekleme**, **şekil boyutunu ayarlama**, **birden fazla şekli gruplama**, **şekli gruba ekleme**—gerçek dünya gereksinimlerine nasıl uyarlayabileceğinizi gösterir.

## Sonuç

Artık Java kullanarak bir Word belgesine **dikdörtgen şekli ekleme**, **şekil boyutunu ayarlama**, **birden fazla şekli gruplama** ve **şekli gruba ekleme** konularını temiz ve sürdürülebilir bir şekilde yapabildiğinizi biliyorsunuz. Tam örnek tek bir çalıştırılabilir sınıfa derlenir ve ortaya çıkan DOCX dosyası beklenen çıktıyı gösterir.

Bundan sonra şunları keşfedebilirsiniz:

* Her şekle metin etiketleri veya hiperlinkler ekleme.
* Hiyerarşik diyagramlar oluşturmak için grupları iç içe kullanma.
* Şekil gruplarını koruyarak belgeyi PDF’ye dışa aktarma.

Farklı boyutlar, renkler ve ek şekil tipleriyle denemeler yapmaktan çekinmeyin. Şekil manipülasyonunu ustalaşmak, otomatik rapor oluşturma, dinamik diyagramlar ve zengin belge deneyimlerinin kapılarını doğrudan Java kodundan açar.

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım‑adım açıklamalar içerir.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}