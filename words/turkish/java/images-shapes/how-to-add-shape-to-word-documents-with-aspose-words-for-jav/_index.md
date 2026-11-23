---
category: general
date: 2026-11-22
description: Aspose.Words for Java kullanarak Word'e şekil eklemeyi öğrenin – bir
  dikdörtgen ekleyin ve programlı olarak gizleyin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: tr
lastmod: 2026-11-22
og_description: Aspose.Words for Java kullanarak Word'e şekil ekleyin. Bu öğreticide
  bir dikdörtgen nasıl eklenir, şekil nasıl gizlenir ve belge nasıl kaydedilir gösterilmektedir.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Aspose.Words ile Word'e Şekil Ekle – Java Rehberi
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Aspose.Words for Java ile Word belgelerine şekil ekleme
url: /tr/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile Word belgelerine şekil ekleme

Programlı olarak **Word belgelerine şekil eklemeniz** gerekiyorsa, Aspose.Words for Java bunu oldukça basit hale getirir. Bu rehberde **şekil ekleme**, görünürlüğünü kontrol etme ve **şekli gizleme** konularını öğrenecek ve son dosyanın tam istediğiniz gibi görünmesini sağlayacaksınız.

Mevcut bir `.docx` dosyasını yükleyen, bir dikdörtgen ekleyen, gizleyen ve sonucu kaydeden tam, çalıştırılabilir bir örnek üzerinden ilerleyeceksiniz. Harici betikler veya manuel adımlar gerekmez ve öğretici, sıfırdan yeni bir belge oluşturma veya yalnızca yazdırma sırasında şekli gizleme gibi yaygın varyasyonları da kapsar.

## Önkoşullar

* Java 17 (veya daha yeni) yüklü – daha eski sürümler çalışır ancak en yeni LTS daha iyi performans sağlar.  
* Maven 3.8+ bağımlılık yönetimi için.  
* Geçerli bir Aspose.Words for Java lisansı (ücretsiz deneme sürümü öğrenme amaçlı kullanılabilir).  
* Tercih ettiğiniz bir IDE veya metin düzenleyici (ör. IntelliJ IDEA, VS Code).

## Adım 1: Aspose.Words'u Maven projenize ekleyin

`pom.xml` dosyanıza aşağıdaki bağımlılığı ekleyin. Bu, en son kararlı sürümü (Kasım 2026 itibarıyla) çeker.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Pro tip:** Kendi lisanslama mantığınızla JAR'ı dağıtmayı planlıyorsanız `<scope>provided</scope>` ifadesini kullanın.

## Word'e şekil ekleme – belgeyi başlatma

İlk işlevsel adım bir `Document` nesnesi elde etmektir. Mevcut bir dosyayı yükleyebilir veya yeni bir tane oluşturabilirsiniz.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*​*Neden önemli*: `Document` sınıfı tüm Word işlemleri için giriş noktasıdır. Mevcut bir dosyayı yüklemek stilleri, üstbilgileri ve altbilgileri korur, yeni bir belge ise temiz bir sayfa sunar.

## Word belgesine şekil ekleme

Sonra, belgenin içeriğini değiştirmek için bir `DocumentBuilder` oluşturun. Builder, metin, tablo ve **şekil** eklemek için yöntemler sunar.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

`insertShape` çağrısı, daha fazla yapılandırabileceğiniz bir `Shape` nesnesi döndürür (renk, kenarlık, metin vb.). Boyutlar puan cinsinden ifade edilir (1 pt = 1/72 in).

*​*Neden bir dikdörtgen kullanabilirsiniz*: Dikdörtgenler, açıklamalar, filigranlar veya yer tutucular için en yaygın kapsayıcıdır. Farklı görsel ihtiyaçları karşılamak için `ShapeType.RECTANGLE` yerine `ShapeType.ELLIPSE`, `ShapeType.LINE` vb. kullanabilirsiniz.

## Word'de şekli gizleme

Bazen bir şeklin yerleşim hesaplamaları için var olması gerekir ancak son renderda görünmemelidir. Aspose.Words, bunu başarmak için `setHidden(true)` metodunu sağlar.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

Gizli bayrağı, Microsoft Word'deki **Hidden** biçimlendirme seçeneği gibi çalışır: şekil görsel yerleşimden çıkarılır ancak belge nesne modelinde hâlâ bulunur. Bu şu durumlar için faydalıdır:

* Uygulamanızın daha sonra okuyacağı meta veri veya işaretçileri depolama.  
* Yayınlamadan hemen önce kaldırılan yer tutucular oluşturma.  
* Farklı çıktı formatları için görünürlüğü kontrol etme (ör. HTML'de gizle, PDF'de tut).

> **Not:** Gizli şekiller varsayılan olarak PDF'ye hâlâ aktarılır. PDF'den de çıkarılmaları gerekiyorsa, `rectangle.getWrapType( ) = WrapType.NONE` ayarlayın ve `Hidden` özelliğini buna göre düzenleyin.

## Adım 4: Değiştirilen belgeyi kaydetme

Son olarak, değişiklikleri yeni bir dosyaya kaydedin.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

`output.docx` dosyasını Microsoft Word'de açtığınızda, dikdörtgen görünmez olacak ancak belge ağacının bir parçası olarak kalır. Dosyayı yeniden yükleyip `Shape.isHidden()` kontrol ederek varlığını programlı olarak doğrulayabilirsiniz.

### Beklenen çıktı

* `output.docx` dosyası herhangi bir görünür şekil olmadan açılır.  
* Belgeyi Aspose.Words ile incelerseniz (ör. `doc.getChildNodes(NodeType.SHAPE, true).size()`), şekil sayısı **1** olacaktır, bu da şeklin var olduğunu ancak gizli olduğunu doğrular.

## İleri düzey varyasyonlar ve uç durumlar

### 1. Yeni bir belgede şekil oluşturma

Sıfırdan başlıyorsanız, yükleme satırını şununla değiştirin:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Şekli tam olarak konumlandırma

Varsayılan olarak, `insertShape` şekli mevcut imleç konumuna yerleştirir. Mutlak konumlandırmak için:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Çıktı formatına göre görünürlüğü kontrol etme

Şeklin Word arayüzünde görünür, ancak PDF'ye aktarılırken gizli olmasını istiyorsanız, `Hidden` ile birlikte `Shape.setWrapType(WrapType.NONE)` kullanın:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Şeklin içine metin ekleme

Bir dikdörtgen bir metin çerçevesi içerebilir:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Ardından aynı `setHidden(true)` çağrısıyla metin kutusunu gizleyebilirsiniz.

## Yaygın tuzaklar ve nasıl önlenir

| Semptom | Neden | Çözüm |
|---------|-------|-----|
| Şekil, `setHidden(true)` çağrıldıktan sonra bile görünüyor | Gizli bayrak ayarlanmadan belge kaydedildi. | `setHidden(true)` metodunu **`doc.save()`**'den **önce** çağırdığınızdan emin olun. |
| Şekil boyutu bozulmuş görünüyor | Yüksek DPI ekranlarda puan ve piksel karışıklığı. | Platformlar arasında tutarlı boyutlandırma için puanları (72 pt = 1 in) kullanın. |
| Gizli şekil hâlâ yazdırılıyor | Bazı yazıcılar gizli bayrağı görmezden gelir. | `Shape.setWrapType(WrapType.NONE)` ayarlayın ve ayrıca `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)` değerini temizleyin. |

## Sonuç

Artık Aspose.Words for Java kullanarak Word belgelerine **şekil ekleme**, **şekil ekleme** ve **şekli gizleme** konularını biliyorsunuz; böylece şekil son kullanıcılar için görünmez olurken belge yapısının bir parçası olmaya devam eder. Yukarıdaki tam örnek bir dosya yükler, bir dikdörtgen ekler, gizler ve sonucu kaydeder; hem tipik kullanım senaryolarını hem de çeşitli uç durumları kapsar.

Buradan, özel dolgu renkleriyle **şekil ekleme**, koşullu yazdırma için **Word'de şekli gizleme** veya Aspose.Words ile toplu belge işleme otomasyonu gibi ilgili konuları keşfedebilirsiniz. Belirli iş akışınıza uyacak şekilde farklı `ShapeType` değerleri, konumlandırma seçenekleri ve görünürlük bayraklarıyla deneyler yapın.

Kodlamaktan keyif alın ve programlı Word manipülasyonunun Java uygulamalarınıza getirdiği esnekliğin tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalarla birlikte tam çalışan kod örnekleri içerir ve ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olur.

- [Aspose.Words kullanarak Java'da programlı olarak Word belgesi oluşturma, şekil ekleme ve gizleme](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Java kullanarak Word belgesinde şekli gizleme](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Aspose.Words ile boş bir .docx Word belgesi oluşturma ve gizli bir dikdörtgen şekil ekleme](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}