---
category: general
date: 2026-05-04
description: Java'da boş bir Word belgesi oluşturun ve şekiller için gölge rengi,
  bulanıklık ve offset ayarlamayı öğrenin – hızlı öğretici.
draft: false
keywords:
- create blank word
- set shadow color
- how to add shadow
- how to set blur
- how to set offset
language: tr
og_description: Java'da boş bir Word belgesi oluşturun ve şekiller için gölge rengi,
  bulanıklık ve offset ayarlamayı öğrenin. Bu adım adım öğreticiyi izleyin.
og_title: Java'da gölgeli boş kelime oluşturma – Tam rehber
tags:
- Aspose.Words
- Java
- Document Automation
title: Java’da gölgeli boş kelime oluşturma – Tam rehber
url: /tr/java/images-shapes/create-blank-word-with-shadow-in-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da gölgeyle boş Word belgesi oluşturma – Tam kılavuz

Koddan **create blank word** dosyaları oluşturup onları biraz daha şık hale getirmeye hiç ihtiyaç duydunuz mu? Tek başınıza değilsiniz. Birçok raporlama veya şablon‑oluşturma projesinde, ilk yaptığınız şey boş bir Word belgesi oluşturmak, ardından ona bir gölgeyle şekil ekleyerek cilalı bir his vermektir.

Bu öğreticide tam olarak bunu adım adım göstereceğiz—Aspose.Words for Java kullanarak boş bir Word belgesi nasıl oluşturulur, **how to add shadow** bir şekle nasıl eklenir ve **set shadow color**, **how to set blur**, **how to set offset** ayrıntıları. Sonunda, güzel bir şekilde bulanıklaştırılmış, yarı saydam kırmızı bir gölgeye sahip bir dikdörtgeni gösteren hazır bir `.docx` dosyanız olacak.

## Gerekenler

- **Aspose.Words for Java** (herhangi bir yeni sürüm; kod 23.9+ ile çalışır)
- JDK 8 veya daha yenisi
- Bir IDE veya basit bir metin düzenleyici ve bir terminal
- Temel Java bilgisi—fantezi bir şey değil, sadece bir `main` metodunu çalıştırabilme yeteneği

Demo için ekstra Maven veya Gradle yapılandırması gerekmez; sadece Aspose JAR dosyasını sınıf yolunuza (classpath) ekleyin ve hazırsınız.

---

![gölgeyle boş Word belgesi oluşturma örneği](image-placeholder.png){: .center alt="gölgeyle boş Word belgesi oluşturma örneği"}

## Boş Word oluşturma – Belgeyi Başlatma

İlk adım, yepyeni, boş bir Word dosyası oluşturmak. Bunu, daha sonra şekiller, tablolar veya metin çizebileceğiniz temiz bir tuval olarak düşünün.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();

        // Step 2: Initialise a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Neden önemli:** `Document` bütün `.docx` paketini temsil eder. Varsayılan yapıcıyla oluşturduğunuzda etkili bir şekilde **create blank word** yapmış olursunuz – içerik, bölüm yok, sadece doldurmanız için hazır dosya yapısı.

## Bir şekle gölge ekleme

Artık temiz bir belgemiz olduğuna göre, gölgeyi barındıracak bir dikdörtgen ekleyelim. Görsel sihrin başladığı yer burası.

```java
        // Step 3: Insert a rectangle shape that will receive a custom shadow
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

> **Pro ipucu:** `insertShape` çağrısı şekli otomatik olarak mevcut paragrafa ekler, bu yüzden mutlak konumlandırma istemediğiniz sürece konumu manuel olarak yönetmenize gerek yok.

## Gölge rengini ayarlama – gölgeyi öne çıkarmak

Renk olmadan bir gölge sadece gri bir bulanıklık olur ve düz görünebilir. Gölgenin rengini ayarlayarak marka renklerine uyum sağlayabilir veya sadece dikkat çekmesini sağlayabilirsiniz.

```java
        // Step 4a: Make the shadow visible and set its color
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.RED); // set shadow color
```

> **Ne oluyor:** `ShadowFormat` gölgenin her görsel yönünü kontrol eder. `setVisible(true)` etkinleştirmek efekti açar ve `setColor` herhangi bir `java.awt.Color` seçmenizi sağlar. Örneğimizde **set shadow color**'ı net göstermek için kırmızı seçtik.

## Hafif bir etki için bulanıklık ayarlama

Keskin, sert kenarlı bir gölge sert görünebilir. Bulanıklık eklemek kenarları yumuşatır ve daha doğal bir görünüm verir.

```java
        // Step 4b: Define how fuzzy the shadow should be
        rectangleShape.getShadowFormat().setBlur(5.0); // how to set blur
```

> **Neden bulanıklık önemli:** `setBlur` değeri puan (point) cinsinden ölçülür. `5.0` değeri hafif bir yayılım oluşturur; daha bulutlu bir gölge için artırın, daha keskin bir hat için azaltın.

## Ofset ayarlama – gölgeyi konumlandırma

Ofsetler, gölgenin şekle göre nerede konumlandığını belirler. Bunu X ve Y kaymaları olarak düşünün.

```java
        // Step 4c: Position the shadow horizontally and vertically
        rectangleShape.getShadowFormat().setOffsetX(8.0); // how to set offset (horizontal)
        rectangleShape.getShadowFormat().setOffsetY(8.0); // how to set offset (vertical)
```

> **Ofset açıklaması:** Pozitif X gölgeyi sağa, pozitif Y aşağıya hareket ettirir. Gölgenin ters tarafta görünmesini istiyorsanız negatif sayılarla oynayın.

## Şeffaflığı ince ayarlama

Gölgenin daha az baskın olmasını istiyorsanız şeffaflığını ayarlayın. Bu adım bir anahtar kelime gereksinimi değildir ancak görsel kontrolü tamamlar.

```java
        // Optional: Make the shadow semi‑transparent (30 % transparent)
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

## Belgeyi kaydetme – sonucu görün

Son olarak, belgeyi diske yazın. Word, LibreOffice veya formatı destekleyen herhangi bir görüntüleyicide açabileceğiniz bir `.docx` dosyanız olacak.

```java
        // Step 5: Save the document with the shaped shadow
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

> **Görmeniz gereken:** `ShadowShape.docx` dosyasını açın. Tek bir sayfa, 150 × 80 pt boyutunda bir dikdörtgeni kırmızı, hafif bulanıklaştırılmış bir gölgeyle, 8 pt aşağı ve sağa kaydırılmış olarak gösterecek. Gölge %30 şeffaftır, bu yüzden dikdörtgen net bir şekilde görünür.

---

## Yaygın sorular ve uç durumlar

### Farklı bir şekle ihtiyacım olursa?

`ShapeType.RECTANGLE` ifadesini başka bir enum değeriyle (`ELLIPSE`, `CLOUD`, `CALLOUT` vb.) değiştirin. Gölge ayarları şekiller arasında aynı şekilde çalışır.

### Aynı gölgeyi birden fazla şekle kod tekrarlamadan uygulayabilir miyim?

Kesinlikle. Bir yardımcı metot oluşturun:

```java
private static void applyShadow(Shape shape, java.awt.Color color,
                                double blur, double offsetX, double offsetY,
                                double transparency) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(color);
    shape.getShadowFormat().setBlur(blur);
    shape.getShadowFormat().setOffsetX(offsetX);
    shape.getShadowFormat().setOffsetY(offsetY);
    shape.getShadowFormat().setTransparency(transparency);
}
```

Ardından herhangi bir şekil için `applyShadow(rectangleShape, Color.RED, 5.0, 8.0, 8.0, 0.3);` çağrısını yapın.

### Bu, eski Aspose sürümleriyle çalışır mı?

`ShadowFormat` API'si sürüm 19.8'den beri stabil, bu yüzden çoğu yeni sürümde sorunsuz çalışır. Çok eski bir sürüm kullanıyorsanız, `ShadowFormat` için Javadoc'ı kontrol edip metod isimlerini doğrulayın.

### Gölgeyi koruyarak PDF'ye nasıl dışa aktarılır?

Şekil oluşturulduktan sonra sadece `document.save("output.pdf");` çağırın. Aspose.Words gölgeleri PDF'de doğru şekilde işler, bulanıklık ve şeffaflığı korur.

---

## Özet – özel bir gölgeyle boş Word oluşturma

Başlangıçta `new Document()` kullanarak **create blank word** yaptık, ardından bir dikdörtgen ekledik, **set shadow color** ayarladık, **how to add shadow** öğrenerek, **how to set blur** ayarladık ve sonunda **how to set offset** ile gölgeyi tam istediğimiz gibi konumlandırdık. Tam ve çalıştırılabilir kod yukarıdaki snippet'te yer alıyor ve ortaya çıkan dosya efekti net bir şekilde gösteriyor.

---

## Sıradaki adımlar

- **Diğer gölge özellikleriyle deneme yapın** gibi `ShadowFormat.setStyle(ShadowStyle.OUTER)` farklı görsel stiller için.
- **Birden fazla şekli birleştirin**; her biri kendi gölgesiyle karmaşık diyagramlar oluşturun.
- **Şeklin içine metin ekleyin** `builder.insertHtml("<b>Hello</b>")` kullanarak şekli eklemeden önce, ardından aynı gölge mantığını uygulayın.
- **Diğer biçimlendirme seçeneklerini keşfedin**; örneğin çizgi stili, dolgu rengi veya degrade doldurmalar—Aspose.Words bu konularda zengin bir API sunar.

Bulanıklık yarıçapını, ofsetleri veya renkleri, gölgenin belge tasarım diliniz için tam doğru hissettiği noktaya kadar özgürce ayarlayın. Kodlamaktan keyif alın ve oluşturduğunuz Word dosyaları her zaman biraz daha cilalı görünsün!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}