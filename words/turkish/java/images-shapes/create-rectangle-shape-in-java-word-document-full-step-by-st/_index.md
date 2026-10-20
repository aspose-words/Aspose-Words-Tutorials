---
category: general
date: 2026-05-26
description: Java Word belgesinde dikdörtgen şekli oluşturun ve gölge efekti uygulayın.
  Şekil gölgesi eklemeyi, gölge mesafesini ayarlamayı ve dosyayı kaydetmeyi öğrenin.
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: tr
og_description: Java Word belgesinde dikdörtgen şekil oluşturun, gölge etkisi uygulayın,
  şekil gölgesi ekleyin ve gölge mesafesini Aspose.Words ile ayarlayın.
og_title: Java Word Belgesinde Dikdörtgen Şekil Oluşturma – Tam Kılavuz
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: Java Word Belgesinde Dikdörtgen Şekli Oluşturma – Tam Adım Adım Rehber
url: /tr/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java Word Belgesinde Dikdörtgen Şekil Oluşturma – Tam Adım‑Adım Kılavuz

Java Word belgesinde **create rectangle shape** oluşturmanız gerektiğinde ama nereden başlayacağınızı bilemediğiniz oldu mu? Yalnız değilsiniz—birçok geliştirici raporlar veya faturalar oluştururken bu sorunu yaşıyor. Bu öğreticide tam olarak nasıl **create rectangle shape** oluşturacağınızı, şık bir gölge uygulayacağınızı ve gölge mesafesini ince ayar yaparak sonucun profesyonel görünmesini sağlayacağımızı adım adım göstereceğiz.

Aspose.Words for Java'ı kullanacağız; Microsoft Office yüklü olmadan Word dosyalarını manipüle etmenizi sağlayan güçlü bir kütüphane. Bu rehberin sonunda sadece birkaç satır kodla **create word document java** projeleri oluşturabilecek, **add shape shadow**, **apply shadow effect** ve **set shadow distance** yapabileceksiniz.

---

## Oluşturacağınız Şeyler

- Cyan bir dikdörtgen içeren yeni bir `.docx` dosyası.
- Bulanik, açıyla ve kısmen şeffaf bir gerçekçi gölge.
- Gölgenin şekilden uzaklığı üzerinde tam kontrol.
- Herhangi bir Maven veya Gradle projesine ekleyebileceğiniz, çalıştırmaya hazır bir Java sınıfı.

Harici araçlar yok, manuel UI adımları yok—sadece saf kod.

## Önkoşullar

- Java 8 veya daha yeni (kod Java 11, Java 17 vb. sürümlerde çalışır).
- Aspose.Words for Java kütüphanesi (Maven Central üzerinden temin edilebilir).
- Sevdiğiniz bir IDE veya metin düzenleyici (IntelliJ IDEA, Eclipse, VS Code…).
- Java sözdizimi hakkında temel bilgi.

Daha önce Maven bağımlılığı eklemediyseniz, işte hızlı bir snippet:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

Şimdi, derinlemesine inceleyelim.

## Adım 1: Word Belgesinde Dikdörtgen Şekil Oluşturma

İlk olarak boş bir belge ve bir `DocumentBuilder`'a ihtiyacımız var. Builder'ı belgeye yazan bir kalem gibi düşünün. Bunu elde ettiğimizde, tek bir metod çağrısıyla **create rectangle shape** yapabiliriz.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **Neden önemli:** `insertShape` metodu yalnızca geometriyi oluşturmakla kalmaz, aynı zamanda şekli belgenin iç koleksiyonuna ekler, böylece hemen stil vermeye başlayabilirsiniz.

## Adım 2: Şekle Gölge Efekti Uygulama

Dikdörtgen sayfada yer aldığından, **apply shadow effect** yapacağız. Gölge derinlik katar, şeklin sayfadan yükselmiş gibi hissetmesini sağlar—raporlarda okunabilirliği artırabilecek ince bir UI iyileştirmesi.

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **Pro ipucu:** `5.0` bulanıklık çoğu ekranda görüntülenen belge için doğaldır. Yazdırıyorsanız, bulanık bir görünümden kaçınmak için biraz daha düşük bir değer tercih edebilirsiniz.

## Adım 3: Gölge Mesafesini Ayarlama – Yerleşimi İnce Ayarlama

Gölge sadece bulanıklıkla ilgili değildir; doğru ofset de gerekir. İşte **set shadow distance** burada devreye girer. `7.0` puanlık bir mesafe, fark edilir ama abartılı olmayan bir ofset oluşturur.

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **Daha büyük bir ofsete mi ihtiyacınız var?** Değeri artırın; daha sıkı bir görünüm için azaltın. Unutmayın, mesafe gölgenin doğru konumlandırılması için açıyla birlikte çalışır.

## Adım 4: Belgeyi Kaydet – Çalışmanızı Saklayın

Son olarak belgeyi diske yazıyoruz. Dosyanın konumunu istediğiniz yere göre değiştirin.

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

Sınıfı çalıştırmak, `shadow.docx` dosyasını oluşturur; bu dosya Microsoft Word veya LibreOffice'te açıldığında, 45° açıyla ve 7 puan ofsetle yumuşak gri bir gölgeye sahip cyan bir dikdörtgen gösterir.

## Tam Çalışan Örnek

Aşağıda tam, kopyala‑yapıştır‑hazır kod bulunmaktadır. Tüm importları, yorumları ve son `save` çağrısını içerir.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**Beklenen çıktı:** `shadow.docx` dosyasını açın → ilk sayfanın ortasında cyan bir dikdörtgen göreceksiniz, hafifçe sağ‑alt köşeye kaymış ince bir gri gölge oluşturur. Gölgenin bulanıklığı ve şeffaflığı, doğal bir aydınlatma gibi görünmesini sağlar.

## Yaygın Sorular & Özel Durumlar

### “Farklı bir şekil kullanabilir miyim?”

Kesinlikle. `ShapeType.RECTANGLE` yerine `ShapeType.OVAL`, `ShapeType.LINE` veya desteklenen başka bir enum kullanın. Gölge kodunun geri kalanı aynı kalır.

### “Birden fazla gölgeye ihtiyacım olsaydı?”

Aspose.Words bir şekil başına yalnızca tek bir gölgeyi destekler. Birden fazla gölgeyi taklit etmek için şekli çoğaltın, her kopyayı ofsetleyin ve şeffaflığı ayarlayın.

### “Gölge LibreOffice'te görünüyor mu?”

Evet—Aspose.Words standart OOXML yazar, LibreOffice bunu doğru yorumlar. Render motorları nedeniyle gölge biraz farklı görünebilir, ancak efekt korunur.

### “Gölge rengini markama uygun nasıl değiştiririm?”

`java.awt.Color.GRAY` yerine istediğiniz herhangi bir `java.awt.Color` değerini koyun; örneğin kurumsal mavi için `new java.awt.Color(0, 120, 215)`.

## Görsel Açıklama

![Java Word belgesinde dikdörtgen şekil oluşturma](https://example.com/images/rectangle-shadow.png)

*Alt metin:* **create rectangle shape** illüstrasyonu, Word belgesinde gri bir gölgeye sahip cyan bir dikdörtgeni gösterir.

## Özet & Sonraki Adımlar

Aspose.Words for Java kullanarak **create rectangle shape**, **apply shadow effect**, **add shape shadow** ve **set shadow distance** nasıl yapılacağını ele aldık. Kod bağımsızdır, herhangi bir modern JDK'da çalışır ve dağıtıma hazır şık bir `.docx` dosyası üretir.

Daha ileri gitmek ister misiniz? Şunları deneyin:

- `builder.moveTo(rectangleShape.getAbsolutePosition())` ile dikdörtgenin içine metin ekleme.
- Bir diyagram oluşturmak için şekillerden bir tablo yaratma.
- Belgeyi PDF olarak dışa aktarma (`doc.save("output.pdf", SaveFormat.PDF);`).

Bunların her biri, az önce incelediğimiz aynı temeller üzerine kurulu olduğundan, örneği genişletirken rahat hissedeceksiniz.

## Son Düşünceler

**create word document java** gibi şekil oluşturma ve gölgelendirme görevlerinde uzmanlaşmak, raporları, sözleşmeleri veya pazarlama materyallerini otomatikleştirirken size büyük bir avantaj sağlar. Burada gösterilen yaklaşım temiz, sürdürülebilir ve—en önemlisi—herhangi bir görsel stil için kolayca ayarlanabilir.

Kodu çalıştırın, bulanıklığı, açıyı ve mesafeyi ayarlayın ve belgelerinizin sade bir halden şık bir hale dönüşümünü izleyin. Bir sorunla karşılaşırsanız, aşağıya yorum bırakın; yardımcı olmaktan memnuniyet duyarım.

Kodlamanın keyfini çıkar!

## İlgili Öğreticiler

- [Word Belgesi Java Oluştur – Dikdörtgen Şekil ve Gölge Efekti Ekle](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java'da DocumentBuilder kullanarak form alanları oluşturma ve içerik ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Word'den PDF Oluşturma ve Barkod Üretimi – Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}