---
category: general
date: 2026-07-03
description: Java'da dikdörtgen şekli oluşturun ve şekle gölge eklemeyi, gölge etkisini
  uygulamayı, şekil şeffaflığını ayarlamayı ve hızlıca boş belge oluşturmayı öğrenin.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: tr
og_description: Java'da gölge, şeffaflık ve boş bir belge ile dikdörtgen şekli oluşturun.
  Şekil işleme konusunda uzmanlaşmak için bu rehberi izleyin.
og_title: Java'da Dikdörtgen Şekli Oluşturma – Tam Programlama Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Java'da dikdörtgen şekli oluşturma – Tam Adım Adım Rehber
url: /tr/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da dikdörtgen şekli oluşturma – Tam Adım‑Adım Kılavuz

Bir Word belgesinde **dikdörtgen şekli oluşturmayı** Java ile merak ettiniz mi? Tek değilsiniz—geliştiriciler genellikle geometrik grafikler eklemek ve ardından düzenin daha rafine görünmesi için hafif bir gölge vermek ister. Bu öğreticide, **boş belge oluşturma**, **şekle gölge ekleme**, **gölge etkisi uygulama** ve hatta **şekil şeffaflığını ayarlama** adımlarını baştan sona inceleyeceğiz.

Aşağıdaki kod parçacığı, projenize kopyalayıp yapıştırabileceğiniz tam işlevsel bir örnektir. Harici bir dokümantasyona ihtiyaç yok—adımları izleyin, “neden”ini anlayın ve birkaç saniye içinde gölgeli dikdörtgenler üretin.

## Öğrenecekleriniz

- Aspose.Words for Java ile programatik olarak **dikdörtgen şekli oluşturma**.
- **Şekle gölge ekleme** ve görsel özelliklerini yapılandırmak için gereken tam çağrılar.
- **Gölge etkisi uygulama** ve ofset, bulanıklık yarıçapı, renk gibi parametreleri ayarlama yolları.
- Daha ince bir görünüm için **şekil şeffaflığını ayarlama** teknikleri.
- **Boş belge oluşturma**, şekli ekleme ve sonucu kaydetme.

> **Pro ipucu:** Tüm bu işlemler tek bir `Document` örneği üzerinde gerçekleştirilir, yani ara dosya I/O’su hakkında endişelenmeden zincirleme yapabilirsiniz.

## Ön Koşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

- Java 17 (veya daha yeni bir JDK) kurulu.
- Projeye eklenmiş Aspose.Words for Java kütüphanesi (Maven koordinatları: `com.aspose:aspose-words:23.12`).
- Bir Java IDE’si ya da basit bir metin düzenleyici—fancy bir şey gerekmez, sadece derleyip çalıştırabileceğiniz bir ortam.

Bu öğelerden birini kaçırdıysanız, Oracle’dan JDK’yı indirin ve Aspose bağımlılığını Maven ya da Gradle üzerinden ekleyin. Hazır olduğunuzda, işe koyulabilirsiniz.

## Adım 1: **Boş belge oluşturma** – her şeyin tuvali

İlk olarak bir `Document` nesnesi oluşturmanız gerekir. Bunu, yeni bir kağıt sayfası gibi düşünün; olmadan dikdörtgeninizi koyacak bir yer yoktur.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Neden boş bir belgeyle başlıyoruz? Çünkü her şekil bir `Section` içinde yer alır ve yeni oluşturulan bir `Document` zaten bir varsayılan bölüm ve gövde içerir. Bu adımı atlamak, daha sonra bölümler oluşturmanızı gerektirir ve gereksiz karmaşıklık ekler.

## Adım 2: **Dikdörtgen şekli oluşturma** ve boyutlarını tanımlama

Şimdi tuvalimiz var, **dikdörtgen şekli oluşturma** zamanıdır. `Shape` sınıfı belge referansını ve bir `ShapeType` alır. Burada `RECTANGLE` seçip genişlik/yüksekliği puan cinsinden ayarlıyoruz (1 pt ≈ 1/72 inç).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Neden `WrapType.INLINE` kullanıyoruz? Inline sarma, şeklin paragraftaki bir karakter gibi davranmasını sağlar ve çevredeki metinle birlikte hareket eder. Yüzen bir davranış isterseniz `WrapType.SQUARE` ya da `WrapType.TOP_BOTTOM`’a geçebilirsiniz.

## Adım 3: **Gölge etkisi uygulama** – dikdörtgene derinlik katma

Düz bir dikdörtgen… tam olarak düz. Bir gölge eklemek onu öne çıkarır. **Gölge etkisi uygulama** için bir `ShadowEffect` örneği oluşturup görsel özelliklerini ayarlayacağız.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Şimdi bunu biraz açalım:

- **Color** – `Color.getGray(0.5)` %50 gri verir; nötrdür ve çoğu arka planla uyumludur.
- **OffsetX/Y** – Pozitif değerler gölgeyi sağa ve aşağı iter; negatif değerler sola/yukarı hareket ettirir.
- **BlurRadius** – Daha büyük değerler daha yumuşak, dağılmış bir gölge oluşturur.
- **Transparency** – `0` (opak) ile `1` (tamamen şeffaf) arasında değişir. Burada %30 şeffaflık için `0.3` seçtik.

## Adım 4: **Şekle gölge ekleme** – efekti bağlama

Efekti oluşturmak yeterli değil; **şekle gölge ekleme** için `ShadowEffect` nesnesini dikdörtgene atamalıyız.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

Arka planda bu çağrı, Word’ün gölgeleri renderlamak için kullandığı OpenXML işaretlemesini (`<w:shdw>`) günceller. Kaydedilen `.docx` dosyasını incelerseniz, ayarladığınız parametrelerle doldurulmuş bir `<w:effect>` öğesi göreceksiniz.

## Adım 5: **Şekil şeffaflığını ayarlama** – isteğe bağlı ama sıkça yararlı

Bazen dikdörtgenin kendisini yarı‑şeffaf yapmak istersiniz, böylece arka plan metni görünebilir. `Shape` sınıfı `setFillColor` ve `setFillTransparency` metodlarını sunar. İşte dikdörtgeni %40 şeffaf yapan kısa bir örnek:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Bunu neden yaparsınız? Bir filigran ya da vurgulanan bir not düşünün; altındaki içerik okunabilir kalmalı. Şeffaflık değerini tasarım dilinize göre ayarlayın.

## Adım 6: Şekli belgeye ekleme

Dikdörtgeni, gölgeyi ekledik ve (isteğe bağlı) şeffaflığını ayarladık. Son adım, **şekli belgenin ilk bölümüne ekleme**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Şekli gövdeye eklemek, onu ilk paragrafın sonuna yerleştirir. Belirli bir konuma ihtiyacınız varsa hedef `Paragraph`’ı alın ve `insertBefore` ya da `insertAfter` kullanın.

## Adım 7: Belgeyi kaydetme – sonucu görme

Tüm bu çalışmalar tek bir `save` çağrısıyla sonuçlanır. Ortamınıza uygun bir yol seçin.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Oluşan `ShadowShape.docx` dosyasını Microsoft Word ya da LibreOffice’da açın; hafif gri bir gölgeye sahip net bir dikdörtgen, isteğe bağlı adımda şeffaflaştırılmış olarak göreceksiniz. Görsel, programatik olarak tanımladığımız parametrelerle eşleşir.

---

![Word belgesinde gölgeli dikdörtgen şekli oluşturma](https://example.com/images/rectangle-shadow.png "Word belgesinde gölgeli dikdörtgen şekli oluşturma")

*Görsel alt metni:* **gölgeli dikdörtgen şekli oluşturma** – son çıktının görsel temsili.

## Yaygın Sorular & Kenar Durumları

### Farklı bir gölge rengi istersem ne yapmalıyım?

`setColor` çağrısını şu şekilde değiştirin:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Aşırı canlı gölgeler profesyonel görünmez; genellikle ince tonlar daha iyidir.

### Aynı gölgeyi birden fazla şekle uygulayabilir miyim?

Evet. Tek bir `ShadowEffect` örneği oluşturup yapılandırın, ardından yeniden kullanın:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

`ShadowEffect` nesnesini diğer şekillere bağladıktan sonra değiştirmemeye dikkat edin; aksi takdirde hepsi güncellenir.

### Gölge bulanıklığını dinamik olarak nasıl değiştiririm?

`setBlurRadius`’a bağlanan bir UI kaydırıcısı ekleyin. `2` ile `12` arasındaki değerler tipiktir; daha büyük sayılar “parıltı” etkisi verir.

### Şeklin inline yerine yüzen olmasını istersem?

Sarma tipini şu şekilde değiştirin:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Yüzen şekiller daha fazla yerleşim özgürlüğü sağlar ancak ek konumlandırma mantığı gerektirir.

## Tam Çalışan Örnek

Aşağıda, tartıştığımız tüm adımları içeren, kopyala‑yapıştır‑hazır bir program yer alıyor. Normal bir Java uygulaması olarak çalıştırın.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Beklenen çıktı:** `ShadowShape.docx` dosyasını açtığınızda, ilk paragrafta ortalanmış, 200 × 100 pt boyutunda beyaz bir dikdörtgen, 5 pt ofsetli, 8 yarıçaplı orta‑gri gölge ve %30 şeffaflık göreceksiniz. Dikdörtgenin kendisi %40 şeffaf, altındaki metnin bir kısmı görülebilir.

## Sonuç

Sıfırdan **dikdörtgen şekli oluşturduk**, **şekle gölge ekledik**, **gölge etkisi uyguladık** ve hatta **şekil şeffaflığını ayarladık**—hepsi **boş belge oluşturma** temeli üzerine kurulu. Yaklaşım basit, Aspose.Words’ün akıcı API’sine dayanıyor ve daireler, yıldızlar ya da özel çokgenler gibi şekillere genişletilebilir.

Sıradaki adımınız ne? `ShapeType.RECTANGLE` yerine `ShapeType.OVAL` kullanarak gölgeli daireler üretin ya da degrade doldurmalarla deneyler yapın.

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayalı olarak ilgili konuları kapsar. Her kaynak, adım‑adım açıklamalar ve tam çalışan kod örnekleri içerir; böylece API özelliklerini daha iyi kavrayabilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Word Belgesi Java – Gölge Efektiyle Dikdörtgen Şekil Ekleme](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Boş Word Belgesi ve Gölgelendirilmiş Dikdörtgen Şekil – Adım‑Adım Kılavuz](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Şekil Gölgesi Öğreticisi – C#’ta Word Şekline Gölge Ekleme](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}