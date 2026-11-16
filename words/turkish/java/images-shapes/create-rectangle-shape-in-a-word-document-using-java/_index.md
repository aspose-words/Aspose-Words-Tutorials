---
category: general
date: 2026-11-15
description: Java ile Word'te dikdörtgen şekli oluşturun ve Word'e şekil eklemeyi,
  şekil boyutlarını ayarlamayı ve Word belgesini verimli bir şekilde kaydetmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: tr
lastmod: 2026-11-15
og_description: Java kullanarak bir Word belgesinde dikdörtgen şekli oluşturun. Şekilleri
  Word’e eklemeyi, şekil boyutlarını ayarlamayı ve Word belgesini dakikalar içinde
  kaydetmeyi öğrenin.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Java ile Word'de Dikdörtgen Şekli Oluşturma – Adım Adım Rehber
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Java kullanarak bir Word belgesinde dikdörtgen şekli oluştur
url: /tr/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java kullanarak bir Word belgesinde dikdörtgen şekli oluşturma

Bir Word dosyası içinde **dikdörtgen şekli oluşturmanız** gerekiyorsa, bu rehber Java ile bunu tam olarak nasıl yapacağınızı gösterir. **Word'e şekil ekleme**, **şekil boyutlarını ayarlama** ve sonunda **Word belgesini kaydetme** işlemlerini IDE'nizden çıkmadan göreceksiniz.

Takip eden bölümlerde eksiksiz, çalıştırılabilir bir örnek, her satırın açıklaması ve boyutlandırma sorunları ve belge uyumluluğu gibi yaygın tuzaklar için ipuçları bulacaksınız. Harici referanslara gerek yok—sadece Aspose.Words for Java kütüphanesi yeterli.

## Öğrenecekleriniz

* Bir `Document` ve bir `DocumentBuilder` başlatmayı.
* **GroupShape** eklemeyi ve içine bir dikdörtgen yerleştirmeyi.
* `setWidth` ve `setHeight` kullanarak **şekil boyutunu tanımlamayı**.
* `.docx` formatında **Word belgesini kaydetmeyi**.
* Farklı sayfa boyutları ve DPI ayarları için kenar durumlarını ele almayı.

### Önkoşullar

* Java 17 veya daha yeni (kod Java 8 ile de derlenir).
* Aspose.Words for Java 23.10 veya daha yeni – Maven Central'dan edinebilirsiniz.
* Java sözdizimi ve nesne‑yönelimli kavramlara temel bir anlayış.

> **Pro ipucu:** Daha sonra daha fazla şekil eklemeyi (ör. daireler veya metin kutuları) planlıyorsanız, bunları aynı `GroupShape` içinde tutun. Bu, tüm koleksiyonu taşıma, döndürme veya biçimlendirmeyi çok daha kolay hâle getirir.

## Adım 1: Belgeyi ve builder'ı başlatma

İlk adım, boş bir Word dosyası ve içerik yazmanıza olanak tanıyan bir `DocumentBuilder` oluşturmaktır.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Neden önemli:* Bir `Document` tüm dosyayı temsil ederken, `DocumentBuilder` metin, tablo ve **şekiller** eklemek için yüksek‑seviye yöntemler sunar. Builder olmadan düşük‑seviye düğümleri manuel olarak manipüle etmeniz gerekir.

## Adım 2: Birden fazla şekli tutmak için grup şekli ekleme

Bir **group shape** bir konteyner gibi davranır; birkaç şekil ekleyebilir ve daha sonra tek bir nesne gibi (ör. birlikte taşıma veya döndürme) işlem yapabilirsiniz.

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Neden grup şekli kullanmalı?* Daha sonra dikdörtgenin etrafına oklar, daireler veya etiketler eklemeye karar verirseniz, grup her şeyi hizalı tutar. Ayrıca **Word'e şekil ekleme** iş akışını basitleştirir çünkü her yeni şekil için sadece bir `appendChild` çağrısına ihtiyacınız olur.

## Adım 3: Dikdörtgen şekli oluşturma

Şimdi grup içinde yer alacak gerçek dikdörtgeni oluşturuyoruz. `Shape` yapıcı metodunun sahibi `Document` ve istediğiniz şekil tipine ihtiyacı vardır.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Neden dikdörtgen?* `ShapeType.RECTANGLE`, bölümleri vurgulamak, yer tutucular oluşturmak veya Word içinde doğrudan basit UI mock‑up'ları çizmek için en yaygın temel şekildir.

## Adım 4: Dikdörtgenin boyutunu tanımlama

Boyutları ayarlamak, **şekil boyutlarını ayarlama**'nın önemli olduğu yerdir. Aspose.Words tarafından desteklenen herhangi bir ölçü birimini kullanabilirsiniz; varsayılan birim puandır (1 pt = 1/72 inç).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Not:** Milimetre tercih ediyorsanız, `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` çağrısını yapın; burada `1.39 in ≈ 35 mm`. Bu, **şekil boyutunu tanımlama** esnekliğini gösterir.

## Adım 5: Dikdörtgeni grup şekline ekleme

Dikdörtgeni önceden oluşturulan gruba eklemek, belgenin içinde görünmesini sağlar.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

Bu noktada dikdörtgen, grubun sol‑üst köşesine konumlanmıştır. Daha hassas yerleştirme gerekiyorsa, `rectangle.setLeft(...)` ve `rectangle.setTop(...)` ile daha sonra taşıyabilirsiniz.

## Adım 6: (İsteğe Bağlı) Sonucu görmek için belgeyi kaydetme

Son olarak, belgeyi diske yazın. Bu, **Word belgesini kaydetme** adımıdır ve Microsoft Word, LibreOffice veya Google Docs'ta açabileceğiniz bir `.docx` dosyası üretir.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

Programı çalıştırmak, grup şekli içinde tek bir dikdörtgen içeren `RectangleShapeDemo.docx` dosyasını oluşturur. Dosyayı açtığınızda, tanımladığınız tam boyutta sade beyaz bir dikdörtgen görürsünüz.

### Beklenen çıktı

* `RectangleShapeDemo.docx` adlı bir Word dosyası.
* İlk paragrafta, 100 pt × 50 pt bir dikdörtgen içeren bir grup şekli.
* Metin eklenmediği için dikdörtgen boş bir sayfada görünür.

## Yaygın varyasyonlar ve kenar durumları

| Durum | Kodu nasıl uyarlamalısınız |
|-----------|-----------------------|
| **Farklı sayfa boyutu** (ör. A4) | Şekli eklemeden önce `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` çağırın. |
| **Yazdırma için daha yüksek DPI** | Genişlik/yüksekliği istenen DPI faktörüyle çarpın, ör. çift çözünürlük için `rectangle.setWidth(200 * 2);`. |
| **Dikdörtgenin içine bir metin etiketi ekleme** | `TEXT_BOX` tipinde bir `Shape` oluşturun, `setWidth`/`setHeight` değerlerini dikdörtgene eşitleyin ve ardından aynı `GroupShape` içine ekleyin. |
| **Dikdörtgeni döndürme** | `rectangle.setRotationAngle(45);` kullanarak 45 derece saat yönünde döndürün. |
| **DOCX yerine PDF olarak kaydetme** | `document.save("output.docx");` ifadesini `document.save("output.pdf");` ile değiştirin – aynı API PDF için de çalışır ve dikdörtgeni korur. |

## Sağlam bir uygulama için pro ipuçları

1. **Builder'ı yeniden kullanın** – grup şekli ekledikten sonra yeni bir builder örneği oluşturmadan paragraf veya tablo eklemeye devam edebilirsiniz.
2. **Kaynakları serbest bırakın** – Java’nın çöp toplayıcısı çoğu nesneyi yönetse de, (akış kullanıyorsanız) `document.close();` çağrısı dosya tutamağı sızıntılarını önler.
3. **Boyutları doğrulayın** – `setWidth`/`setHeight` çağırmadan önce değerlerin pozitif olduğundan emin olun; negatif değerler `IllegalArgumentException` fırlatır.
4. **Sürüm uyumluluğu** – kod Aspose.Words 23.x ve sonrası ile çalışır. Daha eski sürümler ayrı ayarlayıcılar yerine `Shape.setSize(width, height)` gerektirebilir.

## Tam, çalıştırılabilir örnek

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Sonuç doğrulama:** `output/RectangleShapeDemo.docx` dosyasını Microsoft Word'de açın. İlk sayfanın üst kısmında ortalanmış, belirtilen boyutta bir dikdörtgen görmelisiniz. Dikdörtgen çok küçük görünüyorsa, `setWidth` ve `setHeight`'e verilen değerleri ayarlayın.

## Sonuç

Artık Java kullanarak bir Word dosyasında **dikdörtgen şekli oluşturmayı**, bir `GroupShape` aracılığıyla **Word'e şekil eklemeyi**, **şekil boyutlarını ayarlamayı** ve **şekil boyutunu tanımlamayı**, ve son olarak **Word belgesini kaydetmeyi** biliyorsunuz. Aynı desen diğer şekil tipleri için de çalışır ve programlı olarak karmaşık diyagramlar oluşturmanıza olanak tanır.

### Sıradaki adımlar

* **Word'e şekil ekleme**'yi keşfedin; daireler, oklar veya metin kutuları ekleyin.
* Birden fazla şekli tek bir `GroupShape` içinde birleştirin ve dönüşümler (döndürme, çevirme) uygulayın.
* Grafiklerin şekil olarak gömülü olduğu raporlar oluşturun, ardından **Word belgesini** PDF olarak kaydedip paylaşın.

Boyutlar, renkler ve konumlandırma ile özgürce denemeler yapın, böylece kendi senaryonuza uyarlayabilirsiniz. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren eksiksiz çalışan kod örnekleri sunar.

- [Word Belgesi Oluşturma Java – Gölge Efektiyle Dikdörtgen Şekli Ekle](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Java Word Belgesinde Dikdörtgen Şekli Oluşturma – Tam Adım‑Adım Kılavuz](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Word Belgesi Oluşturma Java – Şekli Gizle ve Dolgu Rengini Ayarla](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}