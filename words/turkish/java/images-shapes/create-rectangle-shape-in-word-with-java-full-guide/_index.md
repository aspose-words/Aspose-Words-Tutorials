---
category: general
date: 2026-02-15
description: Java kullanarak bir Word belgesine dikdörtgen şekli oluşturun. Şekil
  gölgesi eklemeyi, Word belgesini kaydetmeyi ve Aspose.Words ile dikdörtgen şekli
  eklemeyi öğrenin.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: tr
og_description: Java ile bir Word dosyasında dikdörtgen şekli oluşturun. Bu kılavuz,
  şekil gölgesi eklemeyi, Word belgesini kaydetmeyi ve adım adım dikdörtgen şekli
  eklemeyi gösterir.
og_title: Dikdörtgen şekli oluştur – Java Aspose.Words Öğreticisi
tags:
- Aspose.Words
- Java
- Document Automation
title: Java ile Word'de Dikdörtgen Şekli Oluşturma – Tam Rehber
url: /tr/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da Word Belgesine Dikdörtgen Şekli Oluşturma – Tam Kılavuz

Bir Word dosyasında **dikdörtgen şekil** oluşturmanız gerektiğinde nereden başlayacağınızı bilemediniz mi? Tek başınıza değilsiniz—birçok geliştirici raporlar veya faturalar otomatikleştirirken bu engelle karşılaşıyor. İyi haber? Aspose.Words for Java ile birkaç satır kodla bir dikdörtgen oluşturabilir, güzel bir gölge ekleyebilir ve Word belgesini kaydedebilirsiniz.

Bu öğreticide, boş bir belgeyi başlatmaktan gölge yapılandırmaya, dosyayı kaydetmeye kadar ihtiyacınız olan her şeyi adım adım inceleyeceğiz. Sonunda **şekil gölgesi ekleme**, **şekil gölgesi nasıl eklenir**, ve **dikdörtgen şekil ekleme** konularını kavrayacaksınız. Harici dokümantasyona gerek yok—sadece çalıştırılabilir kod.

## Önkoşullar

- Java 8 veya daha yeni bir sürüm (API Java 11+ ile de çalışır).  
- Aspose.Words for Java kütüphanesi (sürüm 23.9 veya üzeri).  
- IntelliJ IDEA veya Eclipse gibi bir IDE—herhangi biri yeterli.  
- Java sözdizimine temel aşinalık.

> **Pro ipucu:** Maven kullanıyorsanız, `pom.xml` dosyanıza Aspose.Words bağımlılığını ekleyin ve IDE’nin geri kalanını halletmesine izin verin.

---

## Adım 1: Yeni Bir Belge Başlatma – **dikdörtgen şekil oluşturma**  

İlk iş olarak temiz bir tuvale ihtiyacınız var. Aspose.Words’te bu tuval bir `Document` nesnesidir.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

`Document` sınıfı, tüm .docx dosyasını temsil eder. Daha sonra **dikdörtgen şekil** ve gölgesini **ekleyeceğiniz** bir not defteri gibi düşünebilirsiniz.

## Adım 2: Dikdörtgeni Oluşturma – **dikdörtgen şekil ekleme**  

Şimdi gerçekten dikdörtgeni inşa ediyoruz. Boyutunu, yerleşimini ve dolgu rengini ayarlayacağız.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

`INLINE` sarma neden? Şeklin bir paragraf gibi davranmasını istiyoruz—basit raporlar için mükemmel. Daha sonra şeklin etrafına metin akışı gerekiyorsa `TOPBOTTOM` olarak değiştirebilirsiniz.

## Adım 3: Gölge Uygulama – **şekil gölgesi nasıl eklenir**  

Düz bir dikdörtgen biraz sıkıcı görünebilir. Gölge eklemek derinlik kazandırır ve belgenin daha profesyonel hissettirmesini sağlar. İşte **şekil gölgesi nasıl eklenir** sorusunun pratiğe döküldüğü kısım.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

Her özellik belirli bir iş yapar:

- `setVisible(true)` gölgeyi etkinleştirir.  
- `setColor` hafif bir etki için koyu gri seçer.  
- `setBlurRadius` kenarların ne kadar yumuşak olacağını kontrol eder.  
- `setOffsetX/Y` gölgeyi sağa ve aşağı kaydırarak bir ışık kaynağını taklit eder.  
- `setTransparency` gölgeyi hafif saydam yapar, böylece şekil ön planda kalır.

> **Not:** Renkli bir gölgeye ihtiyacınız olursa, `setColor` metoduna farklı bir `java.awt.Color` değeri geçirin.

## Adım 4: Şekli Belgeye Eklemek  

Dikdörtgen ve gölgesi hazır olduğunda, belge'nin ilk bölümüne yerleştiriyoruz.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

Gövdeye eklemek, şekli yeni bir paragrafın gideceği yere koyar. Dikdörtgeni belirli bir konuma yerleştirmek isterseniz `insertBefore` kullanabilir veya `Paragraph` koleksiyonunu manipüle edebilirsiniz.

## Adım 5: **Word belgesini kaydetme** – Çalışmanızı Kalıcı Hale Getirin  

Son adım, dosyayı diske yazmaktır. İşte **Word belgesini kaydetme** anı.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

`YOUR_DIRECTORY` ifadesini makinenizdeki mutlak ya da göreli bir yol ile değiştirin. Programı çalıştırdıktan sonra `ShadowShape.docx` dosyasını Microsoft Word’de açın—hafif gri bir dikdörtgen ve yumuşak koyu bir gölge görmelisiniz.

![Aspose.Words kullanılarak gölgeli bir dikdörtgen şekli gösteren diyagram](https://example.com/rectangle-shadow.png "gölgeli dikdörtgen şekli oluşturma")

---

## Yaygın Sorular & Kenar Durumları  

### Birden fazla dikdörtgene ihtiyacım olursa ne yapmalıyım?  

**Adım 2** ve **Adım 3**’ü bir döngü içinde tekrarlayın, her yinelemede `setWidth`, `setHeight` veya `setFillColor` değerlerini ayarlayın. Her şekle benzersiz bir değişken adı verin ya da bir listede saklayın.

### DOCX yerine PDF olarak dışa aktarmak mümkün mü?  

Kesinlikle. Şekil eklendikten sonra `document.save("output.pdf")` çağrısını yapın. Aspose.Words dönüşümü halleder ve gölge korunur.

### Eski Word sürümleriyle uyumluluk nasıl?  

`document.save("file.doc", SaveFormat.DOC)` aşırı yüklemesini kullanın. API özellikleri otomatik olarak düşürülür, ancak bazı gölge stilleri eski formatlarda biraz farklı görünebilir.

### Gölge yönünü nasıl değiştiririm?  

`setOffsetX` ve `setOffsetY` değerlerini değiştirin. Pozitif X gölgeyi sağa, negatif X sola kaydırır. Pozitif Y aşağı, negatif Y yukarı hareket ettirir. Işık kaynağını istediğiniz açıdan simüle etmek için bu sayıları oynatın.

---

## Şekillerle Çalışma İpuçları  

- **Şekilleri gruplayın**: Dikdörtgenin yanına bir etiket eklemeniz gerekiyorsa, bir `GroupShape` oluşturup hem dikdörtgeni hem de bir `TextBox` ekleyin.  
- **Z‑sırası önemlidir**: `shape.moveToFront()` veya `shape.moveToBack()` metodlarıyla hangi şeklin üstte görüneceğini kontrol edin.  
- **Performans**: Yüzlerce şekil eklemek yavaşlayabilir. Tüm şekilleri tek bir bölümde toplayın, ardından en sonda bir kez `document.updatePageLayout()` çağırın.

---

## Özet  

Java kullanarak bir Word belgesine **dikdörtgen şekil** nasıl oluşturulur, **şekil gölgesi ekleme** nasıl yapılır ve **Word belgesini kaydetme** adımları ele alındı. Yukarıdaki kod parçacıkları tam ve çalıştırılabilir; ayrıca her özelliğin “neden”ini de anladığınız için renkleri, bulanıklığı ve ofsetleri istediğiniz gibi ayarlayabilirsiniz.

Bir sonraki meydan okumaya hazır mısınız? Dikdörtgeni bir grafikle birleştirin ya da dosyayı PDF olarak dışa aktarın ve gölgenin nasıl renderlandığını görün. Ayrıca **dikdörtgen şekil ekleme**’yi tablolar içinde kullanarak şık rapor düzenleri oluşturabilirsiniz.

Kodlamanız keyifli olsun, belgeleriniz kodunuz kadar keskin görünsün!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}