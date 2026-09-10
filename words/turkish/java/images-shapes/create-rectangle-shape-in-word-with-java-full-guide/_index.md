---
category: general
date: 2026-02-10
description: Aspose.Words for Java kullanarak bir Word belgesine dikdörtgen şekli
  oluşturun. Gölge rengini nasıl ayarlayacağınızı, gölgeyi nasıl ekleyeceğinizi öğrenin
  ve programlı olarak Word belgesi oluşturun.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: tr
og_description: Aspose.Words for Java kullanarak bir Word belgesinde dikdörtgen şekil
  oluşturun. Gölge rengini ayarlamak, gölge eklemek ve Word belgesi oluşturmak için
  bu adım adım öğreticiyi izleyin.
og_title: Java ile Word’de Dikdörtgen Şekil Oluşturma – Tam Rehber
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

# Word'de Dikdörtgen Şekli Oluşturma – Java – Tam Kılavuz

Bir Word belgesinde **dikdörtgen şekli oluşturma** ihtiyacı duydunuz ama nereden başlayacağınızı bilmiyor musunuz? Tek başınıza değilsiniz—birçok geliştirici, Word'de grafik çizmeye programatik olarak ilk kez başladığında bu engelle karşılaşır. İyi haber? Aspose.Words for Java ile bir sayfaya dikdörtgen ekleyebilir, güzel bir gölge verebilir ve dosyayı saniyeler içinde kaydedebilirsiniz. Bu öğreticide **gölge ekleme**, **gölge rengini ayarlama** ve **kelime belgesi oluşturma** adımlarını adım adım göstereceğiz.  

İhtiyacınız olan her şeyi ele alacağız: gerekli kütüphaneler, her kod satırı, belirli ayarların neden önemli olduğu ve resmi belgelerde bulunmayabilecek birkaç ipucu. Sonunda, *Shadow.docx* olarak kaydedilen, yumuşak gri bir gölgeye sahip dikdörtgen şekli oluşturan çalıştırılabilir bir örnek elde edeceksiniz.

## Ön Koşullar – Başlamadan Önce Neye İhtiyacınız Var

Kodlara geçmeden önce aşağıdakilere sahip olduğunuzdan emin olun:

| Gereksinim | Sebep |
|-------------|--------|
| Java Development Kit (JDK) 8 veya daha yeni bir sürüm | Aspose.Words modern bir JDK üzerinde çalışır. |
| Maven veya Gradle (isteğe bağlı) | Aspose.Words bağımlılığını eklemeyi basitleştirir. |
| Aspose.Words for Java lisansı (veya ücretsiz deneme) | Kütüphane ticari; test için bir deneme sürümü yeterli. |
| Bir IDE (IntelliJ IDEA, Eclipse, VS Code vb.) | Örneği hızlıca çalıştırıp hata ayıklamanıza yardımcı olur. |

Zaten bir Java projeniz varsa, sadece Maven koordinatını ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Bundan öteye bir kurulum gerekmez—sadece basit bir `public static void main` metodu yeterli.

![create rectangle shape example](https://example.com/rectangle-shadow.png "create rectangle shape with shadow in Word")

*Görsel alt metni: gölgeyle birlikte bir cyan dikdörtgen gösteren örnek.*

## Adım 1 – Yeni Bir Word Belgesi Oluşturma

İlk yapmamız gereken, boş bir belge başlatmak. Bunu, üzerine daha sonra çizeceğiniz taze bir Word dosyası açmak gibi düşünün.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Neden boş bir `Document` ile başlıyoruz? Çünkü Aspose.Words, `Document` sınıfını sonraki tüm işlemler için bir tuval olarak kabul eder—paragraf, tablo veya şekil eklemek gibi. Bu adımı atladığınızda, bir şey eklemeye çalıştığınız anda `NullPointerException` alırsınız.

## Adım 2 – DocumentBuilder'ı Ayarlama

`DocumentBuilder`, `Document` içine yazan dost kaleminizdir. İçerik eklemenin önerilen yoludur çünkü imleç konumunu otomatik olarak yönetir.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

“Neden belgeyi doğrudan manipüle etmiyoruz?” diye sorabilirsiniz. Cevap: builder, bölüm yönetimi gibi düşük seviyeli detayları soyutlayarak kodu daha temiz ve hata yapma olasılığını azaltır.

## Adım 3 – Dikdörtgen Şekli Ekleme

Şimdi eğlenceli kısma geliyoruz—**şekil oluşturma**. 100 × 50 puan ölçülerinde bir dikdörtgen ekleyecek ve görebilmeniz için cyan dolgu vereceğiz.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

Birkaç not:

* `ShapeType.RECTANGLE` Aspose'a bir dikdörtgen istediğimizi söyler; `OVAL`, `LINE` vb. ile değiştirebilirsiniz.
* Boyutlar puan cinsindendir (1 pt ≈ 1/72 in). Düzeninize göre ayarlayın.
* Dolgu rengi olmadan şekil beyaz sayfada görünmez—bu yüzden cyan kullandık.

## Adım 4 – Gölge Ekleme ve **Gölge Rengini Ayarlama**

İşte bulmacanın **gölge ekleme** kısmını yanıtladığımız yer. `ShadowFormat` nesnesi, gölgenin renkten bulanıklık yarıçapına kadar her görsel özelliğini kontrol eder.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Bu değerleri neden seçtik?

* **Görünürlük** – `setVisible(true)` olmadan diğer ayarlar yok sayılır.
* **Renk** – Gri, hem açık hem de koyu arka planlarda çalışan nötr bir tercihtir. `java.awt.Color.GRAY` yerine istediğiniz herhangi bir `java.awt.Color` kullanabilirsiniz.
* **Bulanıklık yarıçapı** – `5.0` değeri hafif bir yumuşaklık verir; daha büyük sayılar gölgeyi daha da dağınık gösterir.
* **OffsetX/Y** – Ofsetler gölgeyi sağa ve aşağı kaydırır, üst‑sol köşeden gelen bir ışık kaynağını taklit eder.
* **Şeffaflık** – Yarı şeffaf bir gölge, özellikle baskıda sayfayla daha iyi bütünleşir.

Daha keskin bir görünüm isterseniz, bulanıklık yarıçapını `0` yapıp ofseti artırın. Deney yapmaktan çekinmeyin—gölgeler görsel bir konudur ve doğru ayarlar belge tasarımınıza bağlıdır.

## Adım 5 – Belgeyi Kaydetme

Son olarak her şeyi bir `.docx` dosyasına kalıcı hâle getiriyoruz. İstediğiniz yolu seçebilirsiniz; sadece klasörün var olduğundan emin olun.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

*Shadow.docx* dosyasını Microsoft Word'de açtığınızda, sağa ve aşağıya 4 pt kaymış hafif gri bir gölgeye sahip cyan bir dikdörtgen göreceksiniz. Bu, **kelime belgesi oluşturma** sürecinin tam tamamıdır.

### Beklenen Sonuç

| Öğe | Görünüm |
|---------|------------|
| Dikdörtgen | Cyan dolgu, 100 × 50 pt boyut |
| Gölge | Gri, %30 şeffaf, 5 pt bulanıklık, ofset (4, 4) |
| Dosya | `Shadow.docx` belirtilen yolda depolanmış |

Şekil görünmüyorsa, dolgu renginin sayfa arka planıyla aynı olmadığını ve gölgenin görünür olarak ayarlandığını kontrol edin.

## Pro İpuçları & Yaygın Tuzaklar

* **Pro ipucu:** `rectangle.setStrokeColor(java.awt.Color.BLACK);` kullanarak şekle bir kenarlık ekleyin. Bu, dikdörtgenin basılı sayfalarda daha çok öne çıkmasını sağlar.
* **Dikkat:** Okunabilir‑yazılabilir olmayan bir klasöre kaydetmeye çalışmak `IOException` fırlatır. Yazılabilir bir konum seçin ya da dosya izinlerini ayarlayın.
* **Köşe durumu:** Şeffaf bir dolgu (renk yok) isterseniz `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);` çağırın. Şekil hâlâ gölge verir; bu, filigran‑tarz grafikler için faydalı olabilir.
* **Performans notu:** Bir döngü içinde yüzlerce şekil eklemek bellek kullanımını artırabilir. Tüm şekiller eklendikten sonra `document.save` metodunu yalnızca bir kez çağırın.

## Tam Çalışan Örnek

Aşağıda, `ShadowDemo` adlı bir Java sınıfına kopyalayıp yapıştırabileceğiniz tüm program yer alıyor. Aspose.Words JAR'ı sınıf yolunda olduğu sürece derlenir ve çalıştırılır.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Programı çalıştırın, ortaya çıkan *Shadow.docx* dosyasını açın ve dikdörtgenin gölgesi tam olarak tarif edildiği gibi görünsün.

## Daha Fazla Şekil İhtiyacınız Olursa?

“**dikdörtgen şekli oluşturma**” işlemini birden çok kez yapabilir ya da başka şekiller kullanabilir miyim?” diye merak edebilirsiniz. Kesinlikle. Ekleme kodunu bir döngü içinde çalıştırın ve konumları `builder.moveTo` ya da `builder.insertParagraph` ile ayarlayın. Aynı gölge ayarlarını bir yardımcı metoda çıkararak tekrar kullanabilirsiniz:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Her şekil eklemesinden sonra `applyStandardShadow(rectangle);` çağırarak kodunuzu DRY (Don’t Repeat Yourself) tutun.

## Sonraki Adımlar – Temelin Ötesine Geçmek

Artık **gölge ekleme** konusunu bildiğinize göre, aşağıdaki ilgili konuları keşfetmeyi düşünün:

* **Metin çalıştırmaları için gölge rengi ayarlama** – başlıklara hafif bir yükseliş verir.
* **Tablolar ve görsellerle kelime belgesi oluşturma** – şekilleri diğer içeriklerle birleştirin.
* **Word'ün yerleşik**… (devamı resmi dokümantasyonda)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}