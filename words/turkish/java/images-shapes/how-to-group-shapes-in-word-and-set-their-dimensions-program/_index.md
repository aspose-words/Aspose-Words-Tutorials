---
category: general
date: 2026-11-25
description: Java kullanarak Word’de şekilleri nasıl gruplandırılır ve Aspose.Words
  ile bir DOCX dosyasında şekil boyutları nasıl ayarlanır.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: tr
lastmod: 2026-11-25
og_description: Aspose.Words Java API ile Word’de şekilleri nasıl gruplayıp şekil
  boyutunu hızlıca ayarlarsınız. Tam adım adım çözümü izleyin.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Word'de şekilleri gruplama ve boyutlarını ayarlama – Java rehberi
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Word'de şekilleri gruplama ve boyutlarını programlı olarak ayarlama
url: /tr/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de şekilleri nasıl gruplayıp boyutlarını programlı olarak ayarlarsınız

Eğer **Word'de şekilleri nasıl gruplayacağınızı** ve tam boyutlarını kontrol etmeniz gerekiyorsa, bu kılavuz size eksiksiz, çalıştırılabilir bir çözüm gösterir. Aspose.Words for Java kullanarak bir dikdörtgen, bir elips oluşturabilir, bunları bir `GroupShape` içine ekleyebilir ve ardından **şekil boyutlarını nasıl ayarlayacağınızı** genişlik ve yükseklik gibi tek bir DOCX dosyasında gösterebilirsiniz.

Şunları öğreneceksiniz:

* Sıfırdan yeni bir Word belgesi oluşturun.  
* `GroupShape` ekleyin (24.9 sürümündeki yeni API).  
* Gruba bir dikdörtgen ve bir elips ekleyin.  
* **Word'de şekil boyutunu ayarlayın** kesin olarak `setWidth` ve `setHeight` ile.  
* Belgeyi diske kaydedin.

Harici bir araç gerekmiyor—sadece Java 17+, Maven ve Aspose.Words for Java kütüphanesi.

## Prerequisites

* Java Development Kit 17 veya daha yeni bir sürüm.  
* Bağımlılık yönetimi için Maven (veya Gradle).  
* Aspose.Words for Java 24.9 veya daha yeni ( `GroupShape` API'si 24.9'da tanıtıldı).  
* Java sözdizimi ve nesne‑yönelimli kavramlara temel aşinalık.

Henüz projenize Aspose.Words eklemediyseniz, aşağıdaki Maven bağımlılığını ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Step 1: Create a new document and a DocumentBuilder

Adım 1: Yeni bir belge ve DocumentBuilder oluşturun

`Document` sınıfı tüm Word dosyasını temsil ederken, `DocumentBuilder` içeriği eklemenin pratik bir yolunu sağlar.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this step?*  
*Neden bu adım?*  
Yeni bir `Document` oluşturmak size temiz bir tuval sağlar. `DocumentBuilder`, paragraf, tablo ve bu durumda şekiller eklemenizi sağlayan yüksek seviyeli bir yardımcıdır.

## Step 2: Insert a GroupShape (new API in version 24.9)

Adım 2: GroupShape ekleyin (24.9 sürümündeki yeni API)

`GroupShape`, bir kapsayıcı gibi davranır; eklediğiniz her şekil aynı görsel grubun bir parçası olur.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Why use `GroupShape`?*  
*Neden `GroupShape` kullanılır?*  
Şekilleri gruplamak, birden fazla nesneyi aynı anda taşımayı, döndürmeyi veya biçimlendirmeyi basitleştirir. API 24.9'da eklendi, bu yüzden eski sürümler bu satırı derlemez.

## Step 3: Create a rectangle, set its size, and add it to the group

Adım 3: Bir dikdörtgen oluşturun, boyutunu ayarlayın ve gruba ekleyin

Burada bir dikdörtgen için **şekil boyutlarını nasıl ayarlayacağınızı** gösteriyoruz.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Why set width and height explicitly?*  
*Neden genişlik ve yükseklik açıkça ayarlanır?*  
Word, şekil boyutunu puan (point) cinsinden saklar. `setWidth` ve `setHeight` çağırarak tam görsel alanı kontrol edersiniz; bu, kesin bir yerleşim gerektiğinde veya PDF'ye dışa aktarırken çok önemlidir.

## Step 4: Create an ellipse, set its size, and add it to the same group

Adım 4: Bir elips oluşturun, boyutunu ayarlayın ve aynı gruba ekleyin

Aynı **şekil boyutunu ayarlama** tekniği, herhangi bir şekil türü için çalışır.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Why add the ellipse to the same `GroupShape`?*  
*Neden elips aynı `GroupShape` içine eklenir?*  
Her iki şekil de bir birim olarak birlikte hareket eder. Bu, hizalanmış kalması gereken simgeler, logolar veya karmaşık diyagramlar oluştururken faydalıdır.

## Step 5: Save the document with the grouped shapes

Adım 5: Gruplanmış şekillerle belgeyi kaydedin

Son olarak, DOCX dosyasını diske kaydedin.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

Bu programı çalıştırdığınızda **GroupShape.docx** adlı bir dosya oluşturulur; içinde bir dikdörtgen ve bir elips birlikte gruplanmış olarak bulunur. Dosyayı Microsoft Word'de açtığınızda iki şeklin tek bir nesne gibi davrandığını göreceksiniz—birlikte sürükleyebilir, yeniden boyutlandırabilir veya döndürebilirsiniz.

### Expected output

### Beklenen çıktı

* Bir sayfalı Word belgesi (`GroupShape.docx`).  
* `GroupShape`, 100 × 50 pt bir dikdörtgen ve 80 × 80 pt bir elips içerir.  
* Herhangi bir şekli seçmek tüm grubu seçer.

## Common questions and edge cases

## Yaygın sorular ve kenar durumları

### How to change the position of the grouped shapes?

### Gruplanmış şekillerin konumunu nasıl değiştirirsiniz?

`GroupShape` oluşturduktan sonra, `left` ve `top` özelliklerini ayarlayabilirsiniz:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Bu koordinatlar da puan (point) cinsindendir.

### What if I need to add more than two shapes?

### İki'den fazla şekil eklemem gerekirse?

`GroupShape`, diğer kapsayıcı düğümler gibi çalışır. Her ek şekil için `groupShape.appendChild(yourShape)` çağırın. API, çocuk sayısını sınırlamaz.

### Can I apply style (fill color, line weight) to individual shapes?

### Bireysel şekillere stil (dolgu rengi, çizgi kalınlığı) uygulayabilir miyim?

Evet. Her `Shape` nesnesi biçimlendirme özelliklerini sunar:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Does the code work with older Aspose.Words versions?

### Kod eski Aspose.Words sürümleriyle çalışır mı?

`insertGroupShape` yöntemi 24.9 sürümünde tanıtıldı. Daha eski bir sürüm kullanıyorsanız, düğüm ağacı üzerinden `GroupShape`'i manuel olarak oluşturmanız gerekir; bu daha karmaşıktır. Yükseltme önerilen yoldur.

## Pro tips

## Profesyonel ipuçları

* **Tutarlılık için puan (point) kullanın** – Word'ün iç birimi puandır (1/72 inç). Piksellerden veya santimetrelerden dönüştürmek beklenmedik boyutlara yol açabilir.  
* **Konumlandırmadan önce gruplayın** – Tüm çocukları ekledikten sonra `GroupShape`'i konumlandırın; aksi takdirde ofsetleri yeniden hesaplamanız gerekebilir.  
* **DocumentBuilder'ı yeniden kullanın** – Her `insertGroupShape` çağrısından önce oluşturucunun imlecini (`builder.moveTo`) hareket ettirerek aynı belgede birden fazla grup ekleyebilirsiniz.

## Conclusion

## Sonuç

Artık Aspose.Words for Java kullanarak **Word'de şekilleri nasıl gruplayacağınızı** ve **şekil boyutlarını nasıl ayarlayacağınızı** gösteren eksiksiz, uçtan uca bir örneğe sahipsiniz. Eğitim, bir belge oluşturmayı, `GroupShape` eklemeyi, bir dikdörtgen ve bir elips eklemeyi, tam boyutlarını ayarlamayı ve sonucu kaydetmeyi kapsadı.

Bundan sonra şunları keşfedebilirsiniz:

* Aynı gruba metin kutuları veya resimler eklemek.  
* Word'ün akıllı sanat özellikleriyle (API aracılığıyla) gruplandırılmış şekilleri animasyonlu hale getirmek.  
* Gruplanmış şekilleri web kullanımı için PDF veya SVG olarak dışa aktarmak.

Farklı şekil türleri, boyutları ve konumlarla denemeler yapmaktan çekinmeyin—gruplama, Word belgelerindeki karmaşık düzenler üzerinde güçlü bir kontrol sağlar.

## What Should You Learn Next?

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki eğitimler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren eksiksiz çalışan kod örnekleri sunar.

- [Java'da boş bir Word belgesi oluşturma ve şekilleri gruplama](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [Java ile Word'de şekilleri gruplama – tam kılavuz](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}