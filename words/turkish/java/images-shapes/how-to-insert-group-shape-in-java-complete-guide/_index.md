---
category: general
date: 2026-07-16
description: Aspose.Words kullanarak Java’da grup şekli ekleme – dikdörtgen şekli
  ekle, şekil boyutlarını ayarla ve renkli dikdörtgen ve daire oluştur.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: tr
lastmod: 2026-07-16
og_description: 'Java''da grup şekli nasıl eklenir: dikdörtgen şekli ekleme, şekil
  boyutlarını ayarlama ve Aspose.Words ile renkli dikdörtgen ve daire oluşturma konusunda
  uygulamalı bir rehber.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Java'da Grup Şekli Ekle – Tam Aspose.Words Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Java'da grup şekli nasıl eklenir – Tam Kılavuz
url: /tr/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da grup şekli ekleme – Tam Kılavuz

Hiç **Java kullanarak bir Word belgesine grup şekli nasıl eklenir** diye merak ettiniz mi? Tek başınıza değilsiniz. İster bir rapor oluşturucu, ister dinamik bir broşür üreticisi olun, şekilleri gruplamak düzeninizi temiz tutar ve kodunuzu yönetilebilir kılar.

Bu öğreticide **dikdörtgen şekli ekleme**, **şekil boyutlarını ayarlama**, **renkli dikdörtgen oluşturma** ve **renkli daire oluşturma** adımlarını Aspose.Words kütüphanesiyle adım adım göstereceğiz. Sonunda, içinde mavi bir dikdörtgen ve kırmızı bir daire barındıran bir .docx dosyası üreten çalıştırılabilir bir programınız olacak.

## Prerequisites

İlerlemeye başlamadan önce şunların yüklü olduğundan emin olun:

- Java 17 (veya daha yeni bir JDK) kurulu ve yapılandırılmış.
- Bağımlılıkları yönetmek için Maven veya Gradle.
- Aspose.Words for Java 23.9 veya daha yeni bir sürüm – Maven Central’dan alabilirsiniz.
- Java sözdizimi hakkında temel bir anlayış – ekstra bir şey gerekmez.

Eğer bunlardan birini kaçırdıysanız, Oracle’ın sitesinden JDK’yı indirin ve `pom.xml` dosyanıza Aspose.Words bağımlılığını ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Temel hazırlıklar tamam, şimdi işe koyulalım.

## how to insert group shape – Overview

Temel fikir basit: bir `Document` oluştur, bir `DocumentBuilder` aç, bir **grup şekli** ekle, ardından bu gruba ayrı ayrı şekiller (bir dikdörtgen ve bir daire) yerleştir. Grup, bir konteyner gibi davranır; daha sonra taşındığında içindeki her şey aynı anda hareket eder – karmaşık düzenler için ideal.

Aşağıda tamamen çalıştırılabilir kodu bulabilirsiniz. İsterseniz `InsertGroupShapeDemo` adlı yeni bir Java sınıfına kopyalayıp yapıştırın.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Pro tip:** `setLeft` ve `setTop` değerleri sayfanın değil, grubun orijinine göre verilir. Bu sayede bütün grubu yeniden konumlandırmak çok kolay olur.

### What just happened?

1. **Document & Builder** – Boş bir Word dosyası ve içerik eklememizi sağlayan bir `DocumentBuilder` oluşturuyoruz.
2. **Group Shape** – `builder.insertGroupShape()` bir konteyner yaratır. Bunu çizim nesneleri için bir klasör gibi düşünün.
3. **Blue Rectangle** – `RECTANGLE` tipinde bir `Shape` örneği oluşturup boyutlandırıyor, konumlandırıyor ve maviyle dolduruyoruz – bu **create colored rectangle** adımı.
4. **Red Circle** – Aynı desen, ancak mükemmel bir daire için `ELLIPSE` kullanılıyor ve kırmızıyla dolduruluyor – bu **create colored circle** kısmı.
5. **Saving** – Son olarak her şeyi `GroupShapeDemo.docx` dosyasına kaydediyoruz.

Programı çalıştırın (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) ve ortaya çıkan dosyayı açın. Sol tarafta mavi bir dikdörtgen, sağ tarafta kırmızı bir daire göreceksiniz; ikisi de tek bir grup kutusunun içinde kilitli.

## Adding a Rectangle Shape

Sadece bir dikdörtgene ihtiyacınız varsa ve gruplamayı atlamak istiyorsanız, `insertGroupShape()` çağrısını atlayıp dikdörtgeni doğrudan belgenin gövdesine ekleyebilirsiniz. Ancak, grup kullanmak birden fazla şekli tek seferde taşıma, döndürme veya silme esnekliği sağlar.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Burada **add rectangle shape** mantığını kullandığımıza dikkat edin. Dikdörtgen sayfada bağımsız bir nesne olarak görünür. Çoğu gerçek dünya senaryosunda grup tercih edilir, çünkü göreceli konumlamayı korur.

## Setting Shape Dimensions

`setWidth` ve `setHeight` gibi metodları gördüğünüzde, bunların **point** (1/72 inç) biriminde değer aldığını unutmayın. Milimetre tercih ediyorsanız önce dönüştürün:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Bu snippet, birim dönüşümüyle **set shape dimensions** işlemini gösterir – tasarım spesifikasyonlarınız metrik birimlerdeyse çok işe yarar.

## Creating a Colored Rectangle

Bir şekli renklendirmek, `getFill().setForeColor()` çağrısı kadar basittir. Herhangi bir `java.awt.Color` geçirebilirsiniz. Bir degrade istiyorsanız, başlangıç rengi için `setForeColor`, bitiş rengi için `setBackColor` kullanın.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

Bu, **create colored rectangle** işlemini katı bir renk yerine degrade dolgu ile hızlıca yapmanın yoludur.

## Creating a Colored Circle

Daireler, eşit genişlik ve yüksekliğe sahip elipslerdir. Aynı renk mantığı burada da geçerlidir:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Şeffaf bir dolgu istiyorsanız alfa kanalını ayarlayın:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Böylece **create colored circle** tekniğini de tam anlamış oldunuz.

## Saving the Document

Aspose.Words, DOCX, PDF, HTML, PNG gibi birçok formata çıktı verebilir. Bu demo için DOCX’i tercih ediyoruz; çünkü vektörel şekilleri mükemmel korur.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

`SaveFormat`’ı değiştirerek aynı gruplandırılmış çalışmanın PDF versiyonunu da kolayca üretebilirsiniz.

## Common Pitfalls & How to Avoid Them

- **Şekli gruba eklemeyi unuttunuz mu?** Şekil sayfada görünecek ama grup ile birlikte hareket etmeyecek. Her zaman `group.appendChild(yourShape)` çağrısını yapın.

## What Should You Learn Next?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakın konuları ele alıyor. Her kaynak, adım adım açıklamalar ve tam çalışan kod örnekleri içeriyor; böylece ek API özelliklerini öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}