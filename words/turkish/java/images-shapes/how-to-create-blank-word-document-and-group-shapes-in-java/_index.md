---
category: general
date: 2026-09-27
description: Java'da boş bir Word belgesi oluşturun ve Aspose.Words kullanarak şekilleri
  gruplayın. Şekil boyutunu ayarlamayı, şekil dolgu rengini belirlemeyi ve çocuğu
  gruba eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: tr
lastmod: 2026-09-27
og_description: Aspose.Words ile Java’da boş bir Word belgesi oluşturun. Bu öğreticide
  Word’de şekilleri gruplama, şekil boyutunu ayarlama, şekil dolgu rengini belirleme
  ve gruba çocuk ekleme gösterilmektedir.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Java’da boş bir Word belgesi oluşturun ve şekilleri gruplayın – adım adım
  rehber
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Java'da boş bir Word belgesi oluşturma ve şekilleri gruplama
url: /tr/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş Word belgesi oluşturma ve Java'da şekilleri gruplama

Programlamatik olarak **boş bir Word belgesi oluşturmanız** gerektiğinde, bu rehber Aspose.Words for Java ile bunu nasıl yapacağınızı adım adım gösterir. Ayrıca **Word'de şekilleri gruplama**, her şeklin boyutunu ayarlama, dolgu rengi uygulama ve **çocuğu gruba ekleme** sayesinde nesnelerin tek bir birim gibi davranmasını öğrenirsiniz.

Kod üzerinden Word dosyalarıyla çalışmak, manuel biçimlendirmeden kurtulmanızı sağlar ve raporlar, sözleşmeler ya da pazarlama broşürleri gibi belgeleri otomatik olarak oluşturmanıza imkan tanır. Bu öğreticinin sonunda, içinde bir mavi dikdörtgen ve bir resim bulunan, ikisi de birlikte gruplanmış bir `.docx` dosyası üreten çalıştırılabilir bir Java programına sahip olacaksınız.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

- Java 17 (veya daha yeni bir JDK)
- Bağımlılıkları yönetmek için Maven ya da Gradle
- Aspose.Words for Java lisansı (ücretsiz deneme sürümü test için yeterlidir)
- Koddaki referansla erişebileceğiniz bir klasörde bulunan örnek bir resim dosyası (ör. `sample.jpg`)

> **Pro ipucu:** Resim dosyalarınızı bir `resources` dizininde tutun ve `ClassLoader.getResourceAsStream` ile yükleyin; böylece sabit mutlak yollar kullanmaktan kaçınmış olursunuz.

## Adım 1: Boş bir Word belgesi oluşturun ve bir GroupShape ekleyin

İlk adım, boş bir Word dosyasını temsil eden yeni bir `Document` nesnesi oluşturmak ve ardından bir `GroupShape` eklemektir. Grup, daha sonra ekleyeceğiniz tüm şekiller için bir kapsayıcı görevi görür.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Neden önemli:* `GroupShape`, birden fazla şekli birlikte taşımanıza, döndürmenize veya biçimlendirmenize olanak tanır; bu, diyagramlar ya da filigranlar gibi karmaşık düzenler için vazgeçilmezdir.

## Adım 2: Bir dikdörtgen ekleyin ve **şekil boyutunu ayarlayın**

Şimdi bir dikdörtgen oluşturun, boyutlarını tanımlayın ve gruba ekleyin. Bu, **şekil boyutunu ayarlama** işlemini gösterir.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Açıklama:* `setWidth` ve `setHeight` metodları, şeklin tam boyutunu puan cinsinden kontrol eder (1 puan = 1/72 inç). Bu değerleri, düzen gereksinimlerinize göre ayarlayın.

## Adım 3: Dikdörtgen için **şekil dolgu rengini ayarlayın**

Dikdörtgenin arka planı `setFillColor` ile maviye ayarlanır. İstediğiniz herhangi bir `java.awt.Color` sabitini ya da özel bir RGB rengi oluşturabilirsiniz.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Neden faydalı:* Dolgu renkleri, nesneleri görsel olarak ayırt etmeye yardımcı olur; özellikle belgeyi PDF’ye dönüştürdüğünüzde ya da yazdırdığınızda fark edilir.

## Adım 4: Bir resim ekleyin ve **çocuğu gruba ekleyin**

Şimdi aynı `GroupShape` içine bir resim ekleyin. Resim, `DocumentBuilder.insertImage` ile eklenir ve ardından grup içine eklenir; böylece dikdörtgenle birlikte hareket eder.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Köşe durumu:* Resim yolu yanlışsa, Aspose.Words `FileNotFoundException` hatası verir. Bu sorunu önlemek için göreli bir yol kullanın ya da resmi kaynaklardan yükleyin.

## Adım 5: **Gruplanmış şekillerle belgeyi kaydedin**

Son olarak belgeyi diske yazın. Oluşan dosya, birlikte gruplanmış bir dikdörtgen ve resim içerecek.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Beklenen çıktı

- Belirtilen dizinde `GroupShape.docx` adlı bir dosya oluşur.
- Microsoft Word ile dosyayı açtığınızda, tek bir nesne olarak seçilebilen (birlikte taşınabilir veya yeniden boyutlandırılabilir) mavi bir dikdörtgen ve seçtiğiniz resimle boş bir sayfa görürsünüz.

![gruplu şekillerle boş word belgesi oluşturma](/images/grouped-shapes.png "gruplu şekillerle boş word belgesi oluşturma")

*Yukarıdaki ekran görüntüsü, yeni oluşturulan Word belgesi içinde son grup şekillerini göstermektedir.*

## Yaygın varyasyonlar ve ek ipuçları

| Durum | Nasıl ele alınır |
|-----------|-----------------|
| **Birden fazla resim** | Her resmi `builder.insertImage` ile ekleyin ve her biri için `group.appendChild(picture)` çağırın. |
| **Farklı şekil türleri** | `Shape` nesnesi oluştururken `ShapeType.OVAL`, `ShapeType.LINE` vb. kullanın. |
| **Grup konumunu değiştirme** | Tüm çocukları ekledikten sonra, bütün grubu taşımak için `group.setLeft(x)` ve `group.setTop(y)` ayarlayın. |
| **PDF’ye dışa aktarma** | Gruplamadan sonra `doc.save("output.pdf")` çağırın; PDF grup yapısını korur. |
| **Lisans uygulaması** | Değerlendirme sürümünü çalıştırırsanız bir filigran görünür. Filigranı kaldırmak için geçerli bir lisans kurun. |

## Sonuç

Artık **boş bir Word belgesi oluşturma**, bir **GroupShape** ekleme, **şekil boyutunu ayarlama**, **şekil dolgu rengini ayarlama** ve **çocuğu gruba ekleme** işlemlerini Aspose.Words for Java ile nasıl yapacağınızı biliyorsunuz. Bu desen, daha sonra Word içinde düzenlenebilecek ya da diğer formatlara aktarılabilecek karmaşık, programatik düzenler oluşturmanıza olanak tanır.

Sonraki adım olarak, **Word'de şekilleri gruplama** ile metin kutuları eklemeyi, şekillere köprüler (hyperlink) eklemeyi ya da çok sayfalı raporların otomatik oluşturulmasını keşfedebilirsiniz. Aynı prensipler geçerlidir—daha fazla şekil oluşturun, özelliklerini yapılandırın ve aynı gruba ekleyin.

İyi kodlamalar!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve ilgili konuları derinlemesine ele alan örnek kodlar ve adım adım açıklamalar içerir.

- [Java ile Word'de Dikdörtgen Şekil Oluşturma – Tam Kılavuz](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Java ile Word Belgesi Oluşturma – Gölgelendirme Efektiyle Dikdörtgen Şekil Ekleme](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [.NET için Aspose.Words ile Word Belgesinde Grup Şekil Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}