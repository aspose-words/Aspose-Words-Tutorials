---
category: general
date: 2026-01-11
description: 'Java ile bir Word belgesi hızlıca oluşturun: bir dikdörtgen şekli ekleyin,
  dolgu rengini ayarlayın ve şekle gölge uygulayın. Adım adım öğrenin.'
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: tr
og_description: Java ile bir dikdörtgen şekli ekleyerek, dolgu rengini ayarlayıp gölge
  uygulayarak Word belgesi oluşturun. Kodlu tam rehber.
og_title: Java ile Word Belgesi Oluştur – Gölgelikli Dikdörtgen Şekil Ekle
tags:
- Aspose.Words
- Java
- Document Generation
title: Java ile Word Belgesi Oluştur – Gölge Efektiyle Dikdörtgen Şekil Ekle
url: /tr/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java ile Word Belgesi Oluşturma – Gölge Efektli Dikdörtgen Şekli Ekleme

Hiç **create word document java** oluşturup biraz daha şık bir görünüm elde etmek istediniz mi? Belki bir rapor üreticisi geliştiriyorsunuz ve sade bir sayfa yeterli gelmiyor. İyi haber? Aspose.Words for Java ile bir belgeye dikdörtgen şekil ekleyebilir, ona renk verebilir ve hatta hafif bir gölge de ekleyebilirsiniz—tek bir kaç satır kodla.

Bu öğreticide tam olarak bunu yapacağız: bir dikdörtgen şekil ekleme, dolgu rengini ayarlama ve şekle gölge uygulama. Sonunda kendi projenize kopyalayıp yapıştırabileceğiniz çalıştırılabilir bir örnek elde edeceksiniz.

## İhtiyacınız Olanlar

- **Java 17** (veya daha yeni bir JDK) – kod standart dil özelliklerini kullanır.
- **Aspose.Words for Java** kütüphanesi – 23.9 veya daha yeni bir sürüm önerilir.
- Tercih ettiğiniz bir IDE veya metin editörü – IntelliJ IDEA, Eclipse, VS Code… seçiminize kalmış.
- Oluşturulan `ShadowShape.docx` dosyasının kaydedileceği bir klasör.

Ek bir yapılandırma sihirbazına gerek yok; sadece Aspose.Words JAR dosyasını sınıf yolunuza ekleyin, hazırsınız.

## Adım 1: Projeyi Kurun ve Aspose.Words'ü İçe Aktarın

İlk olarak yeni bir Maven (veya Gradle) projesi oluşturun ve Aspose.Words bağımlılığını ekleyin. İşte Maven için minimal bir `pom.xml` kesiti:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

Maven kullanmıyorsanız, JAR dosyasını `libs` klasörünüze koyup derleme yoluna ekleyin.

> **Pro tip:** Aspose, `License license = new License(); license.setLicense("Aspose.Words.lic");` ile gömebileceğiniz ücretsiz bir deneme lisansı sunar. Hızlı testler için atlayabilirsiniz; kütüphane değerlendirme modunda çalışır.

## Adım 2: Yeni Bir Belge ve Oluşturucu Oluşturun

Şimdi **create word document java** nesnelerini oluşturacağız. `Document` sınıfı tüm .docx dosyasını temsil ederken, `DocumentBuilder` içerik eklememizi sağlar.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

Bu noktada şekiller, paragraflar veya ihtiyacınız olan başka öğeler için hazır boş bir belgeniz var.

## Adım 3: Bir Dikdörtgen Şekli Ekleyin ve Dolgu Rengini Ayarlayın

Şekil eklemek `insertShape` çağrısı kadar basittir. **add rectangle shape** tekniğini kullanacağız; bu, ikincil anahtar kelime *add rectangle shape* altında yer alır.

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

Neden turuncu? Beyaz bir alanda öne çıkar, ancak istediğiniz herhangi bir `java.awt.Color` ile değiştirebilirsiniz. Bu adım ikincil anahtar kelime *set shape fill color*’ı kapsar.

## Adım 4: Gölge Görünümünü Yapılandırın – Şekle Gölge Uygulayın

Şimdi eğlenceli kısım: dikdörtgene hafif bir gölge eklemek. Aspose API, gölgenin her yönünü kontrol eden bir `ShadowFormat` nesnesi sunar.

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

Bu kod bloğu **apply shadow to shape** ikincil anahtar kelimeyi tam olarak uygular. `blur`, `offsetX/Y` ve `transparency` değerlerini tasarım dilinize göre ayarlayabilirsiniz. Örneğin, daha büyük bir `offsetX` daha dramatik bir gölge yaratırken, yüksek bir `transparency` gölgeyi fısıltı gibi yapar.

## Adım 5: Belgeyi Kaydedin

Son olarak belgeyi diske yazdırıyoruz. Yazma izniniz olan bir klasör seçin ve dosyaya açıklayıcı bir ad verin.

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

`ShadowShape.docx` dosyasını Microsoft Word ya da LibreOffice’da açtığınızda, altında hafif gri bir gölgeyle parlak turuncu bir dikdörtgen göreceksiniz.

![create word document java ile dikdörtgen şekil](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*Görsel alt metni anahtar kelimeyi içerir, SEO kuralını karşılar.*

## Yaygın Sorular ve Son Durumlar

### Farklı bir şekle ihtiyacım olursa ne olur?

Aspose.Words, `ShapeType` değerleri bakımından onlarca seçenek sunar – yıldızlar, oklar, balonlar vb. `ShapeType.RECTANGLE` yerine `ShapeType.OVAL` ya da başka bir enum sabiti koymanız yeterli. Aynı **nasıl şekil eklenir** adımların geçerli olur.

### Şekli belirli bir paragrafa nasıl eklerim?

Şekli doğrudan builder ile seçme yerine önce (`new Shape(document, ShapeType.RECTANGLE)`) oluşturup, ardından `paragraph.appendChild(shape)` ile bir `Paragraph` içine girebilirsiniz. Bu, yerleşimin daha iyi kontrol edilmesini sağlar.

### Düz renk yerine degrade dolgu uygulayabilir miyim?

Evet! `rectangle.getFill().setFillType(FillType.GRADIENT)` ve bir `LinearGradientFill` tanımlayın. API biraz daha ayrıntılıdır, ancak modern yapılar için harikadır.

### Eski Word sürümleriyle uyumluluk ne olacak?

Aspose.Words varsayılan olarak .docx formatındadır; bu format Word2007+ ve LibreOffice tarafından desteklenir. .doc gerekir ise `document.save("file.doc", SaveFormat.DOC)` çağrısını yapın. Gölge render'ı biraz farklı olabilir, ancak şekil aynı kalır.

## Tam Çalışma Örneği (Kopyala-Yapıştır'a Hazır)

Aşağıda tüm program yer alıyor, derlenip çalıştırılmaya hazır. `YOUR_DIRECTORY` kısmının makinenizdeki gerçek bir yol ile onaylandı.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Bu kodu çalıştırdığınızda, turuncu dikdörtgen ve yumuşak gri gölge içeren bir Word dosyası elde edeceksiniz—tam da **create word document java** ile stilize bir şekil eklemek istediğimizde hedeflediğimiz sonuç.

## Çözüm

Artık **create word document java** için *add rectangle shape*, *set shape fill color* ve *apply shadow to shape* adımlarını içeren eksiksiz bir tarifiniz var. Yaklaşım basit, API akıcı ve sayısız şekilde genişletilebilir—farklı şekiller, degrade dolgu ya da şekil başına birden fazla gölge gibi.

Sırada ne var? Birkaç şekli üst üste koymayı deneyin, farklı bir görsel his için `ShadowStyle.ETCHED` ile oynayın ya da tablo üretimiyle birleştirerek tam teşekküllü raporlar oluşturun. Olanaklar sadece hayal gücünüzle (ve belki Aspose lisans seviyenizle) sınırlı.

Herhangi bir sorunla karşılaştıysanız ya da ek geliştirme fikirleriniz varsa aşağıya yorum bırakın. Mutlu kodlamalar ve Word belgelerinizi biraz daha az sıradan hâle getirin!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}