---
category: general
date: 2026-10-26
description: Aspose.Words for Java kullanarak Word belgesini programlı olarak nasıl
  oluşturacağınızı, bir şekil ekleyeceğinizi ve Word’de nesneyi nasıl gizleyeceğinizi
  öğrenin – adım adım rehber.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: tr
lastmod: 2026-10-26
og_description: Word belgesini programlı olarak oluşturun, Aspose.Words for Java ile
  Word’de şekil eklemeyi ve nesneyi gizlemeyi öğrenin. Tam, çalıştırılabilir örnek.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: Word belgesini programlı olarak oluştur – Java'da şekilleri ekleyin ve gizleyin
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Word belgesini programlı olarak oluştur ve Java'da bir şekil ekle
url: /tr/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java'da programlı olarak Word belgesi oluşturma ve şekil ekleme

Programlı olarak **Word belgesi oluşturmanız** gerekiyorsa, bu öğretici tam olarak nasıl yapılacağını, bir şekil eklemeyi ve ardından Word'de nesneyi gizlemeyi gösterir. Bir rapor oluşturucu ya da otomatik sözleşme sistemi geliştiriyor olsanız da, sadece birkaç dakika içinde eksiksiz, çalıştırmaya hazır bir çözüm elde edeceksiniz.

Şu konuları öğreneceksiniz:

* Aspose.Words for Java ile bir Word belgesi başlatma.  
* **how to add shape** tekniğini kullanarak bir elips (veya başka bir şekil) ekleme.  
* Bu şekli dosya açıldığında hiç görünmeyecek şekilde gizleme, **how to hide shape** sorusuna yanıt.

Aspose.Words kütüphanesi dışında harici bir araç gerekmez ve kod Java 17 ve üzeri sürümlerle çalışır.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* Java Development Kit (JDK) 17 veya daha yeni bir sürüm yüklü.  
* Bağımlılıkları yönetmek için Maven ya da Gradle (örnek Maven kullanıyor).  
* Geçerli bir Aspose.Words for Java lisansı (ücretsiz deneme sürümü test için çalışır).  

Aspose.Words'e yeniyseniz, resmi Getting Started kılavuzuna bakabilirsiniz, ancak bu öğreticiyi takip etmek için onu okumanıza gerek yok.

## Maven Bağımlılığı

Aşağıdaki bağımlılığı `pom.xml` dosyanıza ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Pro tip:** Sürüm numarasını güncel tutun; daha yeni sürümler şekil işleme için hata düzeltmeleri içerir.

## Adım 1: Programlı olarak Word belgesi oluşturma – belgeyi başlatma

Programlı olarak **Word belgesi oluşturduğunuzda** ilk yaptığınız şey bir `Document` nesnesi örneklemektir. Bu nesne, bellek içinde tüm .docx dosyasını temsil eder.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Neden bu adım önemlidir*: `Document` sınıfı, tüm Word‑işleme işlemleri için giriş noktasıdır. Onsuz sayfa, paragraf veya şekil ekleyemezsiniz.

## Adım 2: Şekil ekleme – elips ekleme

Şimdi öğreticinin **how to add shape** bölümüne değiniyoruz. Aspose.Words birçok şekil türünü destekler (Ellipse, Rectangle, TextBox, vb.). Aşağıda 50 puan genişlik ve yüksekliğe sahip bir elips ekliyoruz.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

`insertShape` yöntemi, renk, çizgi stili, dönüş ve daha fazlasını özelleştirebileceğiniz bir `Shape` nesnesi döndürür. Koordinatlar puan cinsinden ölçülür (1/72 inç).

*Neden şekil eklemek isteyebilirsiniz*: Şekiller, filigranlar, dekoratif öğeler veya daha sonra gizleyip değiştireceğiniz yer tutucular için faydalıdır.

## Adım 3: Şekli gizleme – nesneyi Word'de görünmez yapma

**how to hide shape** sorusuna yanıt olarak, şeklin `Hidden` özelliğini `true` olarak ayarlamanız yeterlidir. Bu, Word'e şekli gizli bir nesne olarak ele almasını söyler, böylece belge görünümünde veya çıktısında hiç görüntülenmez.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

Belirli bir kullanıcı veya koşul için **hide object in Word** yapmanız gerekiyorsa, bu özelliği çalışma zamanında iş mantığınıza göre değiştirebilirsiniz.

> **Not:** Gizli şekiller hâlâ belgenin XML yapısının bir parçasıdır. `setHidden(false)` ayarlanarak daha sonra ortaya çıkarılabilir.

## Adım 4: Belgeyi kaydetme

Şekli ekleyip gizledikten sonra belgeyi diske yazın.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

`HiddenShapeDemo.docx` dosyasını Microsoft Word'de açtığınızda, elips gizli olduğu için boş bir sayfa göreceksiniz. Belge, aksi takdirde normal bir Word dosyası gibi davranır.

## Tam çalışan örnek

Tüm parçaları bir araya getirerek, işte eksiksiz, çalıştırılabilir program:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Beklenen çıktı**

```
Document created successfully.
```

`HiddenShapeDemo.docx` dosyasını açmak boş bir sayfa gösterir; gizli elips render edilmez, bu da **hide object in Word** işleminin başarılı olduğunu doğrular.

## Kenar durumları ve varyasyonlar

| Durum | Ne değiştirilmeli | Neden |
|-----------|----------------|-----|
| Elips yerine bir dikdörtgen gizle | `insertShape` içinde `ShapeType.RECTANGLE` kullanın | Farklı görsel yer tutucu |
| Birden fazla şekli aynı anda gizle | `doc.getChildNodes(NodeType.SHAPE, true)` üzerinde döngü kurup `setHidden(true)` ayarlayın | Toplu işleme için faydalı |
| Şekli yalnızca yazdırma görünümünde göster | `shape.setVisible(false)` ve `shape.setPrint(true)` ayarlayın | Word, ekran ve yazdırma görünürlüğünü ayırır |
| Farklı bir ölçü birimi kullan | `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` çağırın | Düzen gereksinimlerinizle uyumlu |

## Yaygın tuzaklar

* **`setHidden(true)` çağırmayı unutmak** – şekil normal gibi görünecek.  
* **Şekli gizlemeden belgeyi kaydetmek** – sıralama önemlidir; önce gizleyin, ardından kaydedin.  
* **Eski bir Aspose.Words sürümü kullanmak** – eski sürümler `setHidden` API'sine sahip olmayabilir.  

Gizli durumun beklendiği gibi çalıştığından emin olmak için oluşturulan dosyayı hedef Microsoft Word sürümünde her zaman test edin.

## Sonuç

Bu rehberde Aspose.Words for Java kullanarak **programlı olarak Word belgesi oluşturmayı**, **şekil eklemeyi** ve **Word'de nesneyi gizlemeyi** öğrendiniz. Tam örnek, belgeyi başlatmadan şeklin hiç görünmediği bir dosyayı kaydetmeye kadar tam adımları gösterir.

Buradan şunları yapabilirsiniz:

* Diğer şekil türleriyle (`ShapeType.LINE`, `ShapeType.TEXT_BOX`) deney yapın.  
* Gizli şekilleri yer imleriyle birleştirerek dinamik şablonlar oluşturun.  
* `setVisible` ve `setPrint` özelliklerini inceleyerek nesne görünürlüğü üzerinde daha ayrıntılı kontrol sağlayın.

Kodlamaktan keyif alın ve Word belgelerinizi otomatikleştirmenin tadını çıkarın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [How to create blank word document with Aspose.Words for Java](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}