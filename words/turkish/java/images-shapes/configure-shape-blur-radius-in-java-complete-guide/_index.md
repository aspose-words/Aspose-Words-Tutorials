---
category: general
date: 2026-06-27
description: Aspose.Words for Java kullanarak şekil bulanıklık yarıçapını nasıl yapılandıracağınızı
  öğrenin. Bu adım adım öğretici ayrıca gölge ayarlarını, şeffaflığı ve belgeyi kaydetmeyi
  kapsar.
draft: false
keywords:
- configure shape blur radius
- Aspose.Words shape shadow
- Java shadow format
- Word document shape manipulation
- set blur radius
language: tr
og_description: Java kullanarak bir Word belgesinde şekil bulanıklık yarıçapını yapılandırın.
  Aspose.Words şekil gölge ayarlarını ustalaşmak için bu ayrıntılı öğreticiyi izleyin.
og_title: Java'da Şekil Bulanıklık Yarıçapını Yapılandırma – Tam Kılavuz
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  headline: Configure Shape Blur Radius in Java – Complete Guide
  type: TechArticle
- description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  name: Configure Shape Blur Radius in Java – Complete Guide
  steps:
  - name: Understanding the Numbers
    text: '- **Blur radius** (`setBlurRadius`) controls how fuzzy the shadow looks.
      A value of `0` gives a crisp edge, while `10` or higher yields a dreamy glow.
      - **DistanceX / DistanceY** shift the shadow relative to the shape. Positive
      X moves it right; positive Y moves it down. - **Transparency** makes the'
  - name: Targeting a Specific Shape by Name
    text: 'If your document contains many shapes, rely on the shape’s **name** (set
      in Word’s layout options) instead of index:'
  - name: Applying Different Blur Radii
    text: 'You might want a stronger blur for background graphics and a subtle one
      for icons. Loop through all shapes:'
  - name: Compatibility Notes
    text: '- **Units:** Aspose.Words uses points (1 pt = 1/72 inch). If you work with
      millimeters, convert accordingly. - **Version:** The API shown works with Aspose.Words
      for Java 24.9 and later. Older versions may use `setBlurRadius(double)` but
      lack some newer shadow properties.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Java'da Şekil Bulanıklık Yarıçapını Yapılandırma – Tam Rehber
url: /tr/java/images-shapes/configure-shape-blur-radius-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da Şekil Bulanıklık Yarıçapını Yapılandırma – Tam Kılavuz

Java ile çalışırken bir Word belgesinde **şekil bulanıklık yarıçapını** yapılandırmanız gerektiğinde hiç zorlandınız mı? Bu konuda yalnız değilsiniz. İster kurumsal bir raporu cilalıyor olun, ister bir broşüre ince bir görsel dokunuş ekliyor olun, bu ayarı ustalaşmak belgelerinizi çok daha profesyonel gösterir.

Bu öğreticide, **.docx** dosyasını yüklemekten gölgenin bulanıklığını ayarlamaya ve sonucu kaydetmeye kadar tüm süreci adım adım inceleyeceğiz. Ayrıca **Aspose.Words şekil gölgesi**, **Java gölge formatı** ve genel **Word belgesi şekil manipülasyonu** gibi ilgili konulara da değineceğiz. Sonunda çalıştırmaya hazır bir kod parçacığı ve her satırın neden önemli olduğuna dair net bir anlayışa sahip olacaksınız.

## Öğrenecekleriniz

- Aspose.Words for Java ile bir Word belgesini nasıl yüklersiniz.  
- Belge gövdesindeki ilk `Shape` nesnesini nasıl bulursunuz.  
- **Şekil bulanıklık yarıçapını** ve mesafe, şeffaflık gibi diğer gölge özelliklerini yapılandırmak için tam adımlar.  
- Değişiklikleri yeni bir `.docx` dosyasına nasıl kaydedersiniz.  

Aspose.Words dışındaki ek bir kütüphane gerekmez ve kod Java 8‑plus ve Aspose.Words for Java’ın (ör. 24.9) herhangi bir güncel sürümüyle çalışır. Temel Java sözdizimini biliyorsanız sorunsuz ilerleyebilirsiniz.

---

## Adım 1: Word Belgesini Yükleyin

Herhangi bir şekle dokunmadan önce belgeyi belleğe almanız gerekir. Aspose.Words bunu tek satırda yapar.

```java
// Load the source .docx file
com.aspose.words.Document document = new com.aspose.words.Document("YOUR_DIRECTORY/input.docx");
```

**Neden önemli:**  
`Document` nesnesi oluşturmak dosyanın tamamını ayrıştırır, bölümlere, paragraflara, tablolara **ve şekillere** erişim sağlar. Bu adımı atlamak, bulanıklık yarıçapını uygulayacak bir bağlam bırakmaz.

> **İpucu:** Büyük dosyalarla çalışıyorsanız, sadece ihtiyacınız olan bölümleri akış olarak almak için `LoadOptions` kullanmayı düşünün. Bellek kullanımını büyük ölçüde azaltabilir.

---

## Adım 2: Hedef Şekli Alın

Şekiller başlıklarda, altbilgilerde, tablolarda vb. her yerde bulunabilir. Basitlik açısından, ilk bölümün ana gövdesinde bulunan ilk şekli alacağız.

```java
// Navigate to the first shape in the document body
com.aspose.words.Shape shape = (com.aspose.words.Shape) document
        .getFirstSection()
        .getBody()
        .getChild(com.aspose.words.NodeType.SHAPE, 0, true);
```

**Neden önemli:**  
`getChild` çağrısı düğüm ağacını derinlemesine dolaşır ve `NodeType.SHAPE` ile eşleşen *ilk* şekli döndürür. Belgenizde birden fazla şekil varsa, indeksi (`0`) ayarlayabilir veya `document.getChildNodes(NodeType.SHAPE, true)` üzerinden döngü yapabilirsiniz.

> **Köşe durumu:** Belge hiç şekil içermiyorsa, `shape` `null` olur ve bir sonraki satır `NullPointerException` fırlatır. Üretim kodunda her zaman buna karşı kontrol ekleyin.

---

## Adım 3: Şeklin Gölgesini Yapılandırın – Bulanıklık Yarıçapını Ayarlayın

Şimdi asıl gösteriyi ayarlama zamanı: bulanıklık yarıçapını değiştirmek. Bu, şekle bağlı `ShadowFormat` nesnesi içinde bulunur.

```java
// Access the shadow format of the shape
com.aspose.words.ShadowFormat shadow = shape.getShadowFormat();

// Set the blur radius (in points). Larger values produce a softer edge.
shadow.setBlurRadius(5.0);

// Optional: fine‑tune other shadow attributes
shadow.setDistanceX(3.0);          // Horizontal offset
shadow.setDistanceY(3.0);          // Vertical offset
shadow.setTransparency(0.3);      // 0 = fully opaque, 1 = fully transparent
```

### Sayıların Anlamı

- **Bulanıklık yarıçapı** (`setBlurRadius`) gölgenin ne kadar flu görüneceğini kontrol eder. `0` keskin bir kenar verir, `10` ve üzeri ise rüya gibi bir parıltı oluşturur.
- **DistanceX / DistanceY** gölgeyi şekle göre kaydırır. Pozitif X sağa, pozitif Y aşağıya hareket ettirir.
- **Transparency** gölgeyi saydam yapar. Katı bir siyah blok yerine ince bir etki istediğinizde kullanışlıdır.

> **Neden bulanıklık yarıçapı yapılandırılır?**  
> Birçok kurumsal şablonda hafif bir bulanıklık, okuyucuyu rahatsız etmeden derinlik katar. Görsel bir dokunuş, algılanan kaliteyi büyük ölçüde artırabilir.

---

## Adım 4: Değiştirilmiş Belgeyi Kaydedin

Tüm ağır işleri tamamladınız; şimdi değişiklikleri diske yazın.

```java
// Persist the modified document
document.save("YOUR_DIRECTORY/output.docx");
```

**Neden önemli:**  
`save` çağrısı, güncellenmiş `ShadowFormat` dahil olmak üzere tüm belgeyi yazar. Sadece şekli bir resim olarak dışa aktarmak isterseniz, `shape.getImageData().save(...)` kullanabilirsiniz.

---

## Tam Çalışan Örnek

Aşağıda, herhangi bir Java IDE’sine kopyalayıp yapıştırabileceğiniz, eksiksiz, bağımsız bir program bulunuyor. Aspose.Words for Java JAR dosyasının sınıf yolunuzda olduğundan emin olun.

```java
import com.aspose.words.*;

public class ConfigureShapeBlurRadius {
    public static void main(String[] args) throws Exception {
        // 1. Load the document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Get the first shape (add null‑check for safety)
        Shape shape = (Shape) document.getFirstSection()
                .getBody()
                .getChild(NodeType.SHAPE, 0, true);
        if (shape == null) {
            System.out.println("No shape found in the document.");
            return;
        }

        // 3. Configure shadow – focus on blur radius
        ShadowFormat shadow = shape.getShadowFormat();
        shadow.setBlurRadius(5.0);          // Soft blur
        shadow.setDistanceX(3.0);           // Horizontal offset
        shadow.setDistanceY(3.0);           // Vertical offset
        shadow.setTransparency(0.3);        // Slightly transparent

        // 4. Save the result
        document.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved with configured shape blur radius.");
    }
}
```

**Beklenen çıktı:**  
Programı çalıştırdığınızda, ilk şeklin `5` puanlık bir bulanıklık yarıçapına sahip, hafif yarı‑saydam bir gölgeyle yeni bir `output.docx` dosyası oluşturulur. Word’de dosyayı açın, şekli seçin ve **Şekil Biçimi → Gölge Efektleri → Gölge Seçenekleri** altında ayarladığınız değerlerin UI’da yansıtıldığını göreceksiniz.

---

## Birden Çok Şekil ve İleri Senaryoları Ele Alma

### İsme Göre Belirli Bir Şekli Hedefleme

Belgenizde birçok şekil varsa, indeks yerine şeklin **adı**na (Word düzen seçeneklerinde ayarlanan) dayanabilirsiniz:

```java
Shape target = (Shape) document.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getName().equals("MyLogo"))
        .findFirst()
        .orElse(null);
```

### Farklı Bulanıklık Yarıçapları Uygulama

Arka plan grafikleri için daha güçlü, simgeler için daha hafif bir bulanıklık isteyebilirsiniz. Tüm şekiller üzerinde döngü yapın:

```java
for (Node node : document.getChildNodes(NodeType.SHAPE, true)) {
    Shape s = (Shape) node;
    ShadowFormat sf = s.getShadowFormat();
    sf.setBlurRadius(s.getName().contains("Background") ? 10.0 : 3.0);
}
```

### Uyumluluk Notları

- **Birimler:** Aspose.Words puan (point) kullanır (1 pt = 1/72 inç). Milimetre ile çalışıyorsanız, uygun dönüşümü yapın.
- **Sürüm:** Gösterilen API, Aspose.Words for Java 24.9 ve sonrası ile çalışır. Daha eski sürümler `setBlurRadius(double)` kullanabilir ancak bazı yeni gölge özelliklerini içermez.

---

## Yaygın Tuzaklar ve Önleme Yöntemleri

| Tuzak | Neden Oluşur | Çözüm |
|---------|----------------|-----|
| `NullPointerException` on `shape` | Belge şekil içermiyor veya indeks aralık dışı | `ShadowFormat` erişmeden önce null kontrolü ekleyin. |
| Word’de gölge görünmüyor | Gölge rengi varsayılan olarak şeffaf veya mesafe değerleri gölgeyi sayfadan dışarı itiyor | Görünür bir `ShadowColor` ayarlayın (`shadow.setColor(Color.BLACK)`) ve `DistanceX/Y` değerlerini makul tutun. |
| Bulanıklık yarıçapı değişmiyor | Özelliği yok sayan eski bir Aspose.Words sürümü kullanılıyor | En son kütüphaneye yükseltin; özellik sürüm 20.5’te tanıtıldı. |
| Büyük belgelerde performans düşüşü | Her şekil değişikliğinden sonra belgeyi tekrar kaydediyor | Tüm değişiklikleri biriktirin, ardından tek bir `save` çağrısı yapın. |

---

## Sonuç

Java ve Aspose.Words kullanarak bir Word belgesinde **şekil bulanıklık yarıçapını** nasıl yapılandıracağınızı artık biliyorsunuz. Dosyayı yüklemek, doğru `Shape` nesnesini almak, `ShadowFormat`’u ayarlamak ve değişiklikleri kalıcı hâle getirmek—her adım açıklamalar ve gerçek dünya ipuçlarıyla ele alındı.

Bu teknik tek bir şekille sınırlı değil; tüm belgelere ölçekleyebilir, farklı bulanıklık seviyeleri uygulayabilir veya **gölge şeffaflığı Java** gibi diğer gölge özellikleriyle birleştirebilirsiniz. Bir sonraki mantıklı adım, **görüntüler için bulanıklık yarıçapı** ayarlamayı keşfetmek, grafiklerde **Java gölge formatı** denemek ya da **Word belgesi şekil manipülasyonu** ile dinamik rapor üretimine dalmak olabilir.

Burada ele alınmayan bir senaryonuz mu var? Yorum bırakın ya da daha gelişmiş gölge efektleri için Aspose.Words for Java belgelerine göz atın. Kodlamanın tadını çıkarın!

---

<img src="configure-shape-blur-radius.png" alt="Configure shape blur radius using Aspose.Words Java example" style="max-width:100%;">

---


## Sonra Ne Öğrenmelisiniz?


Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakın konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımları keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}