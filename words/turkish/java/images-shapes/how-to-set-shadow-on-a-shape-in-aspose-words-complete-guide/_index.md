---
category: general
date: 2026-03-19
description: Aspose.Words for Java kullanarak bir şekle hızlıca gölge ayarlamayı,
  şekle gölge eklemeyi, şeffaflığı değiştirmeyi, gölgeyi bulanıklaştırmayı ve mesafeyi
  ayarlamayı öğrenin.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- how to change transparency
- how to blur shadow
- how to set distance
language: tr
og_description: Aspose.Words'ta bir şekle gölge ayarlamayı öğrenin. Bu kılavuz, şekle
  gölge eklemeyi, şeffaflığı değiştirmeyi, gölgeyi bulanıklaştırmayı ve mesafeyi ayarlamayı
  gösterir.
og_title: Şekle Gölge Nasıl Eklenir – Adım Adım Java Rehberi
tags:
- Aspose.Words
- Java
- ShapeShadow
title: Aspose.Words'ta Bir Şekle Gölge Nasıl Ayarlanır – Tam Rehber
url: /tr/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words'ta Bir Şekle Gölge Ayarlama – Tam Kılavuz

Sonsuz API belgeleri arasında kaybolmadan bir şekle **gölge nasıl eklenir** diye hiç merak ettiniz mi? Yalnız değilsiniz. Bir diyagram, logo veya Word belgesindeki bir açıklama için ince bir düşen gölgeye ihtiyaç duyduklarında birçok geliştirici bir engelle karşılaşıyor. İyi haber? Aspose.Words for Java ile bu iş çok kolay ve sadece birkaç satırla yapabilirsiniz.

Bu öğreticide tüm süreci adım adım inceleyeceğiz: **şekle gölge ekleme**, **saydamlığı** ayarlama, **bulanıklık** uygulama ve **mesafe** ile açıyı ince ayarlama. Sonunda, cilalı görünen tamamen biçimlendirilmiş bir şekle sahip olacaksınız ve her özelliğin neden önemli olduğunu anlayacaksınız.

---

## Önkoşullar

- Java 8 veya daha yeni bir sürüm yüklü.
- Aspose.Words for Java (en son sürüm; yazı zamanı v24.10).
- `input.docx` dosyasında en az bir şekil (ör. bir dikdörtgen veya resim) içeren basit bir `.docx` dosyası.
- Favori IDE'niz (IntelliJ IDEA, Eclipse, VS Code… herhangi biri yeterli).

Ekstra kütüphane gerekmez—Aspose.Words ihtiyacınız olan her şeyi içinde barındırır.

---

## Şekle Gölge Ayarlama – Adım Adım

Aşağıda çözümü küçük adımlara bölüyoruz. Her adım kısa bir kod parçacığı, **neden** yaptığımızın açıklaması ve işinize yarayabilecek bir ipucu içerir.

### 1. Kaynak belgeyi yükleyin

İlk olarak, diskteki dosyaya işaret eden bir `Document` nesnesine ihtiyacımız var. Bunu, bir Word dosyasını bellekte açmak gibi düşünün.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Neden önemli:* Yüklenmiş bir belge olmadan değiştirilecek bir şeyiniz olmaz. `Document` sınıfı, herhangi bir Aspose.Words işleminin giriş noktasıdır.

> **Pro tip:** Geliştirme sırasında “dosya bulunamadı” sürprizlerinden kaçınmak için mutlak bir yol kullanın.

### 2. Şekle gölge ekle – ilk şekli al

Şimdi biçimlendirmek istediğimiz şekli buluyoruz. `NodeType.SHAPE` seçicisi düğüm ağacında dolaşır ve karşılaştığı ilk `Shape` nesnesini döndürür.

```java
        // Step 2: Retrieve the first shape in the document
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
```

*Neden önemli:* Şekiller resim, çizim veya SmartArt olabilir. Doğru düğümü yakalamak, yanlışlıkla bir paragrafı veya tabloyu değiştirmediğimizden emin olmamızı sağlar.

> **Dikkat:** Belgenizde şekil yoksa, `firstShape` `null` olur ve sonraki satırlar bir `NullPointerException` fırlatır. Üretim kodunda her zaman `null` kontrolü yapın.

### 3. Gölgenin Saydamlığını Nasıl Değiştirirsiniz

Tamamen opak bir gölge ağır görünür. `transparency` özelliğini ayarlamak, gölgeyi ince bir örtüye indirgemenizi sağlar.

```java
        // Step 3: Obtain the shadow formatting object for the shape
        ShadowFormat shadowFormat = firstShape.getShadowFormat();

        // Step 4: Make the shadow 30 % transparent
        shadowFormat.setTransparency(0.3);
```

*Neden önemli:* Saydamlık, gölgenin altında kalan içeriğin ne kadarının görüneceğini kontrol eder. `0.0` değeri tamamen siyah; `0.3` ise hafif, geçirgen bir etki verir.

> **Yaygın hata:** `setTransparency` çağrısını unutmak, varsayılan (tamamen opak) değeri bırakır ve bu gölgenin çok sert görünmesine neden olabilir.

### 4. Gölgeyi Nasıl Bulanıklaştırırsınız

Bulanıklaştırma kenarları yumuşatır, gölgenin daha doğal görünmesini sağlar, özellikle yüksek çözünürlüklü ekranlarda.

```java
        // Step 5: Apply a soft blur with a radius of 5 points
        shadowFormat.setBlurRadius(5.0);
```

*Neden önemli:* `0` bulanıklık yarıçapı keskin, gerçek dışı bir kenar verir. Yarıçapı artırmak gölgeyi yayar ve ışığın gerçek dünyada nasıl dağıldığını taklit eder.

> **Hızlı test:** `5.0` değerini `10.0` yapıp yeniden çalıştırın—gölgenin nasıl daha tüylü hale geldiğine dikkat edin.

### 5. Gölgenin Mesafe ve Açısını Nasıl Ayarlarsınız

Mesafe, gölgeyi şekilden uzaklaştırır, açı ise ışık kaynağının yönünü belirler.

```java
        // Step 6: Set the shadow offset distance to 4 points
        shadowFormat.setDistance(4.0);

        // Step 7: Define the shadow direction angle (45 degrees)
        shadowFormat.setAngle(45.0);
```

*Neden önemli:* `0` mesafe, gölgeyi doğrudan şeklin arkasına sabitler ve bu genellikle düz görünür. `45°` açı, üst‑sol taraftan gelen bir ışık kaynağını taklit eder, yaygın bir tasarım tercihidir.

> **Köşe durumu:** Açılar, yatay eksenden saat yönünde ölçülür. `180` açı gölgeyi karşı tarafa çevirir.

### 6. Belgeyi Kaydedin

Son olarak, değiştirilmiş belgeyi diske geri yazın. Orijinali üzerine yazabilir veya yeni bir dosya oluşturabilirsiniz.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output_with_shadow.docx");
    }
}
```

*Neden önemli:* Kaydetmek, yeni yapılandırdığınız tüm gölge ayarlarını kalıcı hale getirir. Sonuç dosyasını Word'de açarak efekti görebilirsiniz.

---

## Tam Çalışan Örnek

Hepsini bir araya getirerek, işte tam, çalıştırmaya hazır program:

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the first shape (add null‑check for safety)
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (firstShape == null) {
            System.out.println("No shapes found in the document.");
            return;
        }

        // Access the shadow format
        ShadowFormat shadowFormat = firstShape.getShadowFormat();

        // Make the shadow 30 % transparent
        shadowFormat.setTransparency(0.3);

        // Apply a soft blur with a radius of 5 points
        shadowFormat.setBlurRadius(5.0);

        // Set the shadow offset distance to 4 points
        shadowFormat.setDistance(4.0);

        // Define the shadow direction angle (45 degrees)
        shadowFormat.setAngle(45.0);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/output_with_shadow.docx");

        System.out.println("Shadow applied successfully!");
    }
}
```

**Beklenen sonuç:** `output_with_shadow.docx` dosyasını açın. İlk şekil, hafif bulanık, %30 saydam bir gölgeyi, 4 pt uzaklıkta ve 45° açıyla göstermelidir. Şeklin sayfanın hemen üzerinde süzülüyor gibi görünür.

---

## Sık Sorulan Sorular (SSS)

### Birden fazla şekle aynı anda gölge ekleyebilir miyim?

Kesinlikle. Tek şekil alımını bir döngüyle değiştirin:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node node : shapes) {
    Shape shape = (Shape) node;
    ShadowFormat sf = shape.getShadowFormat();
    // Apply the same settings or vary per shape
}
```

### Siyah yerine renkli bir gölgeye ihtiyacım olursa ne olur?

`ShadowFormat` ayrıca bir `setColor(Color)` metoduna sahiptir. Koyu mavi bir gölge için:

```java
shadowFormat.setColor(Color.fromArgb(0, 0, 255));
```

### Şeklin içindeki resimlerle de çalışır mı?

Evet. Aspose.Words, resimleri “Picture” (satır içi değil) olarak eklediğiniz sürece `Shape` nesneleri olarak kabul eder. Aynı gölge özellikleri geçerlidir.

### Bulanıklık yarıçapı nokta mı yoksa piksel mi ölçülür?

Nokta cinsinden ölçülür (1 pt = 1/72 in). Bu, farklı DPI ayarlarında görünümün tutarlı kalmasını sağlar.

---

## Sonuç

Başlangıçtan sona kadar bir şekle **gölge nasıl eklenir** konusunu ele aldık, **şekle gölge ekleme** gösterdik, **saydamlığın nasıl değiştirileceğini** gösterdik, **gölgeyi nasıl bulanıklaştıracağınızı** açıkladık ve sonunda **mesafe ve açının nasıl ayarlanacağını** detaylandırdık. Kod kompakt, kavramlar net ve artık Aspose.Words for Java'da herhangi bir şekli biçimlendirmek için yeniden kullanılabilir bir deseniniz var.

Bir sonraki meydan okumaya hazır mısınız? Bu gölge ayarlarını **gradient doldurmalar** ile birleştirmeyi deneyin ya da şekli klonlayıp her kopyayı kaydırarak **çoklu gölgeler** ile deney yapın. Gökyüzü sınırdır ve yeni öğrendiğiniz araçlarla belgelerinize kısa sürede profesyonel bir parlaklık kazandırabilirsiniz.

Bu kılavuzu faydalı bulduysanız, bir yorum bırakın, kendi varyasyonlarınızı paylaşın veya **şekil biçimlendirme**, **metin efektleri** ve **belge dönüştürme** konularındaki diğer öğreticilerimize göz atın. Kodlamanın tadını çıkarın! 

![şekle gölge ayarlama örneği](image.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}