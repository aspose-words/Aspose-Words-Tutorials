---
category: general
date: 2026-09-21
description: Java kullanarak programlı bir şekilde Word belgesi oluşturun. Word'de
  şekilleri nasıl gruplayacağınızı, bir dikdörtgen şekli eklemeyi, şekil boyutunu
  ayarlamayı ve şekilleri bir Word belgesine eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: tr
lastmod: 2026-09-21
og_description: 'Java ile programlı olarak Word belgesi oluşturma: bu rehber, Word''de
  şekilleri gruplama, dikdörtgen şekilleri ekleme, şekil boyutunu ayarlama ve şekilleri
  bir Word belgesine ekleme yöntemlerini gösterir.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Program aracılığıyla Word belgesi oluştur, Java’da şekilleri grupla
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Programlı olarak Word belgesi oluştur, Java’da şekilleri grupla
url: /tr/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java'da programlı olarak Word belgesi oluşturma, şekilleri gruplama

Programlı olarak **Word belgesi oluşturmanız** gerekiyorsa, bu kılavuz size eksiksiz bir çözüm sunar. **Word'de şekilleri gruplamayı**, bir dikdörtgen eklemeyi, boyutunu ayarlamayı ve diğer şekilleri eklemeyi—hepsini Java ve Aspose.Words for Java kütüphanesini kullanarak göreceksiniz.

Bu öğretici, proje kurulumundan son .docx dosyasının kaydedilmesine kadar her adımı kapsar. Sonunda, bir dikdörtgen ve bir görüntünün tek bir grup içinde sarıldığı bir Word belgesi üretebileceksiniz; bu da onları birlikte hareket ettirmeyi veya yeniden boyutlandırmayı kolaylaştırır. Aspose.Words API'siyle ilgili önceden bir deneyime ihtiyacınız yoktur, ancak temel bir Java geliştirme ortamına sahip olmalısınız.

## Gereksinimler

* Java Development Kit (JDK) 8 veya daha yeni  
* Bağımlılık yönetimi için Maven veya Gradle  
* Aspose.Words for Java 23.9 (veya en son sürüm) – kütüphane değerlendirme için ücretsizdir  
* Bilinen bir dizine yerleştirilmiş bir görüntü dosyası (ör. `sample.jpg`)  

Bu öğeleri hazır bulundurmak, kodun ek bir yapılandırma gerektirmeden çalışmasını sağlar.

## Adım 1: Projeyi kurun ve Aspose.Words'ü içe aktarın

Bir Maven projesi oluşturun (veya mevcut `pom.xml` dosyanıza bağımlılığı ekleyin):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Gradle tercih ediyorsanız, `build.gradle` dosyanıza aşağıdakileri ekleyin:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

Bağımlılık çözüldükten sonra, Java kaynak dosyanıza gerekli sınıfları içe aktarın:

```java
import com.aspose.words.*;
import java.io.File;
```

## Adım 2: Word belgesini programlı olarak oluşturun

Herhangi bir otomasyon senaryosundaki ilk işlem, bir `Document` nesnesi ve bir `DocumentBuilder` örneği oluşturmaktır. Builder, metin, görüntü ve şekil eklemeyi basitleştirir.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Bu noktada belge yalnızca bellek içinde vardır. Şekil eklemeye şimdi başlayabilirsiniz.

## Adım 3: Dikdörtgen şekli ekleyin – nasıl dikdörtgen şekli eklenir

Dikdörtgen, `ShapeType.RECTANGLE` ile tanımlanan temel bir `Shape`'dir. Boyutlarını `setWidth`, `setHeight` ile kontrol eder, konumunu ise `setTop` ve `setLeft` ile ayarlarsınız.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Neden önemli:** Boyut ve konumu açıkça ayarlamak (`set shape size word`) dikdörtgenin, belgenin varsayılan düzeninden bağımsız olarak tam istediğiniz yerde görünmesini garanti eder.

## Adım 4: Görüntü ekleyin – şekilleri Word belgesine ekleyin

`DocumentBuilder`, bir dosya yolundan doğrudan bir görüntü ekleyebilir. Ekleme sonrası resmi, diğer şekiller gibi yeniden konumlandırabilirsiniz.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Dikdörtgen ve resim artık belgede bağımsız şekillerdir.

## Adım 5: Şekilleri gruplayın – Word'de şekilleri nasıl gruplayabilirsiniz

Şekilleri grup halinde hareket ettirmek veya yeniden boyutlandırmak istediğinizde gruplama faydalıdır. Aspose.Words bu amaçla bir `GroupShape` konteyneri sağlar.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

Grup kaydedildiğinde, Word iki çocuğu tek bir mantıksal nesne olarak işler. Daha sonra grubu seçip sürükleyebilir, hem dikdörtgen hem de görüntü birlikte hareket eder.

## Adım 6: Belgeyi kaydedin

Son olarak, belgeyi diske yazın. Yol, Java süreci tarafından yazılabilir olmalıdır.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

`main` metodunu çalıştırdığınızda **GroupShapeExample.docx** adlı bir dosya üretilir. Microsoft Word'de açtığınızda, bir grup içinde kilitlenmiş bir dikdörtgen ve bir görüntü görürsünüz. Grubu seçmek, iki nesneyi aynı anda hareket ettirmenizi sağlar ve gruplamanın başarılı olduğunu doğrular.

## Beklenen çıktı

* Belirttiğiniz dizinde bulunan bir Word dosyası (`GroupShapeExample.docx`).  
* Dosyanın içinde, üst‑sol köşede ışık‑gri dolguya sahip bir dikdörtgen görünür ve görüntü doğrudan onun altında yer alır.  
* Her iki nesne de tek bir grubun parçasıdır, bu yüzden birini sürüklediğinizde diğeri de hareket eder.

## Yaygın varyasyonlar ve kenar durumları

| Durum | Öneri |
|-----------|----------------|
| **Farklı görüntü formatları** | Aspose.Words PNG, BMP, GIF ve TIFF formatlarını destekler. `insertImage` içinde uygun dosya uzantısını kullanın. |
| **Negatif boyutlar** | API `ArgumentException` hatası verir. `setWidth` / `setHeight` çağırmadan önce her zaman genişlik ve yüksekliği doğrulayın. |
| **Büyük belgeler** | Birçok şekli gruplamak dosya boyutunu artırabilir. Performans önemliyse şekilleri tek bir resimde birleştirmeyi düşünün. |
| **Word sürüm uyumluluğu** | GroupShape Word 2007 (`.docx`) ve sonrasıyla çalışır. Daha eski `.doc` dosyalarında grup düzleştirilir. |
| **Dinamik konumlandırma** | Adaptif yerleştirme gerekiyorsa sayfa boyutuna (`doc.getFirstSection().getPageSetup().getPageWidth()`) dayalı hesaplamalar kullanın. |

**Pro ipucu:** Grubu oluşturduktan sonra, değiştirebilirsiniz

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Java ile Word Belgesi Oluşturma – Gölge Efektiyle Dikdörtgen Şekil Ekle](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Java ile Word'de Dikdörtgen Şekil Oluşturma – Tam Kılavuz](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [.NET için Aspose.Words Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}