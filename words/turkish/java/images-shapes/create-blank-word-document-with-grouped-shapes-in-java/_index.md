---
category: general
date: 2026-08-07
description: Aspose.Words kullanarak Java'da gruplanmış şekillerle boş bir Word belgesi
  oluşturun. Şekli nasıl gruplayacağınızı, şekil boyutunu nasıl ayarlayacağınızı ve
  şekilleri Word'e nasıl ekleyeceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: tr
lastmod: 2026-08-07
og_description: Java'da gruplanmış şekillerle boş bir Word belgesi oluşturun. Şekil
  boyutunu ayarlamak, şekilleri Word'e eklemek ve şekilleri nasıl gruplayacağınızı
  öğrenmek için bu rehberi izleyin.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Gruplandırılmış şekillerle boş Word belgesi oluşturma – Java öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Java'da gruplanmış şekillerle boş Word belgesi oluştur
url: /tr/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java'da Gruplanmış Şekiller İçeren Boş Word Belgesi Oluşturma

Eğer **create blank Word document** içeren ve birkaç şeklin tek bir birim olarak düzenlendiği bir dosya oluşturmanız gerekiyorsa, bu öğretici tam olarak nasıl yapılacağını gösterir. **how to group shape** nesnelerini, boyutlarını ayarlamayı ve Aspose.Words for Java kullanarak **add shapes to Word** işlemini gösteren eksiksiz, çalıştırılabilir bir örnek göreceksiniz.

Kılavuz, proje kurulumundan son .docx dosyasının kaydedilmesine kadar her adımı adım adım anlatır; böylece kodu doğrudan kendi uygulamanıza kopyalayabilirsiniz. Harici referanslara gerek yoktur ve çözüm Aspose.Words 23.9 veya sonraki sürümlerle çalışır.

## Önkoşullar

* Java 17 (veya desteklenen herhangi bir JDK)
* Maven veya Gradle bağımlılık yönetimi için
* Aspose.Words for Java lisansı (veya geçici bir değerlendirme anahtarı)
* Bilinen bir dizine yerleştirilmiş örnek bir resim dosyası (ör. `sample.jpg`)

Bu öğelerden herhangi biri eksikse, önce onları kurun; öğreticinin geri kalanı ortamın hazır olduğunu varsayar.

## Adım 1: Aspose.Words'u projenize ekleyin

Aspose.Words bağımlılığını `pom.xml` (Maven) veya `build.gradle` (Gradle) dosyanıza ekleyin. Bu kütüphane, daha sonra kullanılacak `Document`, `DocumentBuilder`, `GroupShape` ve `Shape` sınıflarını sağlar.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Neden önemli:** Kütüphane olmadan, Word‑processing API'leri mevcut değildir ve programlı olarak **create blank Word document** oluşturamazsınız.

## Adım 2: Boş bir Word belgesi oluşturun

İlk somut adım, bellekte bir **blank Word document** temsil eden bir `Document` nesnesi örneklemektir.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* varsayılan ayarlarla (A4 sayfa, varsayılan kenar boşlukları) bir **blank Word document** oluşturur. Eşlik eden `DocumentBuilder`, mevcut imleç konumuna içerik eklemenizi sağlar.

## Adım 3: Bir grup şekil ekleyin (how to group shape)

Bir *group shape*, diğer şekiller için bir kapsayıcı görevi görür. Bu adımda **how to group shape** nesnelerini birlikte hareket edecek şekilde nasıl gruplayacağınızı öğrenirsiniz.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

`insertGroupShape` yöntemi, kapsayıcıyı builder'ın imleç konumuna yerleştirir. Birden fazla çizimi tek bir varlık olarak ele almak istediğinizde gruplama zorunludur—bu, **group shapes word** işlevselliğinin temelidir.

## Adım 4: Bir dikdörtgen oluşturun ve boyutunu ayarlayın

Şimdi gruba bir dikdörtgen ekleyin. Bu, **set shape size** gösterimi olup, kesin yerleşim için gereklidir.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Boyutlar neden ayarlanmalı?* `setWidth` ve `setHeight` metodlarını açıkça çağırmak, dikdörtgenin belge varsayılan şekil stillerinden bağımsız olarak tam istediğiniz gibi görünmesini garantiler.

## Adım 5: Bir resim ekleyin ve gruba dahil edin

Bir resim eklemek, **add shapes to word** için başka bir yaygın kullanım senaryosunu gösterir. Resim aynı grup içinde yer alır ve dikdörtgenle birlikte hareket eder.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Resim dosyası eksikse, Aspose.Words bir istisna fırlatır. Pratik bir ipucu, yolu önceden doğrulamaktır:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Adım 6: Gruplanmış şekilleri içeren belgeyi kaydedin

Son olarak, **blank Word document** (şimdi bir grup şekil içeren) diske kalıcı olarak kaydedilir.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

`GroupShapeDemo.docx` dosyasını Microsoft Word'de açtığınızda, içinde bir dikdörtgen ve bir resim bulunan tek bir grup nesne göreceksiniz. Grubun herhangi bir parçasını seçmek, tüm kapsayıcıyı hareket ettirir ve şekillerin doğru şekilde **grouped** olduğunu doğrular.

### Beklenen çıktı

* Belirtilen dizinde `GroupShapeDemo.docx` adlı bir dosya.
* Dosyayı açtığınızda 300 × 200 puanlık bir kapsayıcı içinde:
  * (20, 20) konumunda konumlandırılmış 100 × 50 puanlık bir dikdörtgen.
  * Aynı kapsayıcı içinde (150, 30) konumunda bir resim.

## Kenar durumları ve varyasyonlar

| Durum | Nasıl ele alınır |
|-----------|-----------------|
| **Different page size** | Grup eklemeden önce `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` çağırın. |
| **Multiple groups** | Yeni bir `GroupShape` örneğiyle adım 3‑5'i tekrarlayın; her grup bağımsız olarak konumlandırılabilir. |
| **Rotating shapes** | Bir dikdörtgeni veya resmi gruba eklemeden önce döndürmek için `shape.setRotationAngle(45.0);` kullanın. |
| **Non‑image shapes** | `ShapeType.ELLIPSE`, `ShapeType.LINE` vb. tipinde `Shape` nesneleri oluşturup dikdörtgen gibi ekleyin. |
| **Large images** | Grubun orijinal sınırları içinde kalması için resmi `picture.setWidth(80.0); picture.setHeight(60.0);` ile ölçeklendirin. |

Bu varyasyonlar, temel deseni geniş bir belge‑oluşturma senaryosuna uyarlamanızı sağlar.

## Deneyimden Pratik İpuçları

* **Pro tip:** Grubun `RelativeHorizontalPosition` ve `RelativeVerticalPosition` değerlerini `RelativeHorizontalPosition.PAGE` ve `RelativeVerticalPosition.PAGE` olarak ayarlayın; böylece grup imleç yerine sayfaya sabitlenir.
* **Dikkat edilmesi gereken:** Grubun boyutlarını aşan bir şekil eklemek; şekil Word'de kırpılır. Grubun boyutunu `group.setWidth()` ve `group.setHeight()` ile buna göre ayarlayın.
* **Performans notu:** Döngü içinde çok sayıda belge üretiyorsanız, tek bir `DocumentBuilder` örneğini yeniden kullanın ve nesne oluşturma maliyetini azaltmak için `doc.clone()` çağırın.

## Sonuç

Artık Aspose.Words for Java kullanarak **create blank Word document** içinde gruplanmış bir şekil koleksiyonu oluşturmayı biliyorsunuz. Öğretici, kütüphanenin kurulumu, belgenin oluşturulması, bir grup eklenmesi, **set shape size**, **add shapes to word** ve sonucun kaydedilmesi adımlarını kapsayan tam bir iş akışı sundu.

Bundan sonra, grafik gruplama, tek tek şekillere stil uygulama veya belgeyi PDF olarak dışa aktarma gibi daha gelişmiş özellikleri keşfedebilirsiniz. Bu konuların her biri, bu rehberde gösterilen aynı prensiplere dayanır.

---


## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve birbirleriyle yakından ilişkili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for .NET Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)
- [Java ile Word Belgesi Oluşturma – Gölgelendirme Efektiyle Dikdörtgen Şekil Ekleme](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for .NET Kullanarak Word Belgelerine Şekil Ekleme](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}