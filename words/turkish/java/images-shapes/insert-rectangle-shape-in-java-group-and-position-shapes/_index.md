---
category: general
date: 2026-07-26
description: Aspose.Words kullanarak Java'da dikdörtgen şekli ekleyin. Şekil boyutunu
  ayarlamayı, şeklin konumunu belirlemeyi ve bir DOCX dosyasında şekilleri nasıl gruplayacağınızı
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: tr
lastmod: 2026-07-26
og_description: Java'da dikdörtgen şekli ekleyerek zengin DOCX grafikleri oluşturun.
  Şekil boyutunu ayarlamak, şekli konumlandırmak ve şekilleri sorunsuzca gruplamak
  için bu adım adım rehberi izleyin.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Java'da Dikdörtgen Şekli Ekle – Gruplama ve Konumlandırmada Ustalık
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Java'da Dikdörtgen Şekil Ekle – Şekilleri Gruplandır ve Konumlandır
url: /tr/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da Dikdörtgen Şekil Ekle – Şekilleri Gruplama ve Konumlandırma

Java kodu yazarken bir Word belgesine **dikdörtgen şekil ekleme** ihtiyacı hiç duydunuz mu? Tek başınıza değilsiniz—rapor, fatura veya özel şablonlar oluşturan geliştiriciler bu engelle sık sık karşılaşıyor. İyi haber şu ki, Aspose.Words for Java ile sadece birkaç satır kod yazarak **dikdörtgen şekil ekleyebilir**, **şekil boyutunu ayarlayabilir**, **şekli konumlandırabilir** ve hatta **şekilleri nasıl gruplayacağınızı** öğrenerek tek bir birim gibi hareket etmelerini sağlayabilirsiniz.

Bu rehberde, boş bir belge oluşturup iki dikdörtgeni düzenli bir şekilde gruplayan bir `.docx` dosyasına kadar tüm süreci adım adım inceleyeceğiz. Sonunda **dikdörtgen ekleme** nesnelerini nasıl ekleyeceğinizi, boyutlarını nasıl kontrol edeceğinizi, tam istediğiniz yere nasıl yerleştireceğinizi ve yeniden kullanılabilir bir grup içinde nasıl birleştireceğinizi öğreneceksiniz. Aspose.Words dışındaki ek bir kütüphane gerekmez ve kod Java 8‑ ve üzeri sürümlerle çalışır.

## Ön Koşullar

- Java 8 veya daha yeni bir sürüm (Ben JDK 17 kullanıyorum, Maven destekleyen herhangi bir sürüm yeterli)
- Aspose.Words for Java 23.9 veya üzeri – bağımlılığı `pom.xml` dosyanıza ekleyin ya da JAR dosyasını indirin
- Java sözdizimi hakkında temel bilgi (eğer bir `main` metodu yazabiliyorsanız yeterli)
- Tercih ettiğiniz bir IDE veya metin editörü (IntelliJ IDEA, Eclipse, VS Code…)

> **Pro tip:** Maven kullanıyorsanız bağımlılık şu şekilde görünür:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Temel altyapıyı kurduğumuza göre, koda dalalım.

## Dikdörtgen Şekil Ekle ve Boyutunu Ayarla

İlk adım, yeni bir `Document` ve bir `DocumentBuilder` oluşturmaktır. Builder, sayfaya şekil çizen “kalem”inizdir. Aşağıda **dikdörtgen şekil ekliyoruz** ve hemen **şekil boyutunu** 100 × 80 puan olarak **ayar** ediyoruz.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

`setWidth`/`setHeight` çağrılarının **şekil boyutunu** puan cinsinden (1 pt ≈ 1/72 inç) ayarladığını fark edin. Tek bir metod tercih ederseniz `setSize` de kullanabilirsiniz, ancak açıkça belirtilen çağrılar niyeti kristal netliğinde gösterir.

## Şekli Sayfada Konumlandır

İlk dikdörtgeni ekledikten sonra, ikinci şeklin **konumlandırılması** gerekir; aksi takdirde birincisiyle çakışır. Konumlandırma aynı şekilde çalışır: `Left` ve `Top` özelliklerini grubun orijinine göre ayarlarsınız.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Neden `setX` yerine `setLeft` kullandığımızı merak ediyorsanız, Aspose.Words klasik Windows GDI koordinat sistemini benimser—`Left` yatay offset, `Top` ise dikey offsettir. Bu değerleri değiştirerek tablo veya paragrafla uğraşmadan düzeni ince ayar yapabilirsiniz.

## Şekilleri Nasıl Gruplarsınız

“Gruplama neden gerekli?” diye sorabilirsiniz. Şekillerin birlikte hareket etmesi, bir bütün olarak döndürülmesi veya ortak bir stile sahip olması gerektiğinde gruplama mantıklı olur. Yukarıdaki kod parçacığında zaten `builder.insertGroupShape` ile bir `GroupShape` oluşturduk. Bu nesne temelde bir kapsayıcıdır—diğer şekil dosyalarını tutan bir klasör gibi düşünebilirsiniz.

> **Neden Önemli:** Daha sonra bir başlık eklemek veya tüm diyagramı döndürmek isterseniz, sadece grubu değiştirmeniz yeterli olur; her bir dikdörtgeni ayrı ayrı düzenlemeniz gerekmez.

## Dikdörtgeni Gruba Nasıl Eklenir

**Gruba dikdörtgen ekleme** işlemi sadece `group.appendChild(rectangle)` çağrısıdır. Aspose.Words arka planda grubun iç koleksiyonunu günceller ve sınırlayıcı kutuyu otomatik olarak yeniden hesaplayarak grup hâlâ belirtilen genişlik ve yüksekliğe sığar.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Diğer `ShapeType` değerleriyle de deney yapabilirsiniz—`ShapeType.ELLIPSE`, `ShapeType.TRIANGLE` vb.—ve aynı `appendChild` deseni çalışır.

## Belgeyi Kaydet

Son olarak belgeyi diske kalıcı hâle getiriyoruz. Yol mutlak ya da göreceli olabilir; sadece klasörün var olduğundan emin olun.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

`GroupShape.docx` dosyasını Microsoft Word’de açtığınızda, yan yana iki dikdörtgeni, içinde açık gri bir kutu bulunan bir grup olarak göreceksiniz. Gri kutuyu seçtiğinizde iki dikdörtgen de aynı anda vurgulanır—**şekilleri gruplama** gerçekten çalışıyor demektir.

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="Java‑oluşturulmuş DOCX dosyasında iki dikdörtgenin gruplandığını gösteren dikdörtgen şekil ekleme örneği"}

*Görsel alt metni (SEO):* **Java‑oluşturulmuş DOCX dosyasında iki dikdörtgenin gruplandığını gösteren dikdörtgen şekil ekleme örneği**.

## Beklenen Çıktı

- `output` klasöründe bulunan bir `GroupShape.docx` dosyası.
- Belge içinde: 400 × 200 pt bir grup, içinde iki dikdörtgen (100 × 80 pt ve 120 × 60 pt) sırasıyla (20, 30) ve (150, 50) konumlarında.
- Grup ince bir siyah kenarlık ve açık gri dolgu içerir, bu da gruplamayı görsel olarak belirgin kılar.

Dosyayı açın ve gri kutuyu sürüklemeyi deneyin—her iki dikdörtgen de birlikte hareket etmelidir. Eğer hareket etmiyorsa, her şekil için `group.appendChild` çağrısını yaptığınızdan emin olun.

## Yaygın Hatalar & Kenar Durumları

| Sorun | Neden Oluşur | Çözüm |
|-------|--------------|------|
| **Dikdörtgenler sayfanın dışına çıkıyor** | `Left`/`Top` değerleri grubun boyutlarını aşıyor | Grup boyutunu (`insertGroupShape(width, height)`) artırın veya offsetleri azaltın |
| **Grup kaydedildikten sonra kayboluyor** | Grubun `Width`/`Height` değerleri 0 olarak ayarlanmış | `insertGroupShape` çağrısında sıfır olmayan boyutlar sağlayın |
| **Şekil renkleri yanlış görünüyor** | Varsayılan dolgu transparan; Word bunu beyaz olarak gösterebilir | `setFillColor` ile açıkça renk belirleyin veya `ShapeStyle` kullanın |
| **`ArgumentOutOfRangeException` hatası** | Negatif koordinatlar kullanılıyor | `Left` ve `Top` değerlerini negatif olmaktan kaçının |

Bu sorunları erken aşamada çözmek, yeni başlayanların sıkça yaşadığı “şeklim neden kayboldu?” başlıklı baş ağrılarından sizi kurtarır.

## Özet ve Sonraki Adımlar

Java’da **dikdörtgen şekil ekleme** sürecinin tam döngüsünü ele aldık: belge oluşturma, **şekil boyutunu ayarlama**, **şekli konumlandırma**, **şekilleri gruplama** ve **dikdörtgeni gruba ekleme**. Tam, çalıştırılabilir örnek yukarıdaki kod bloğunda yer alıyor; Maven projenize yapıştırıp sonucu hemen görebilirsiniz.

Sırada ne var? Şunları deneyebilirsiniz:

- Her dikdörtgenin içine metin eklemek için


## Bir Sonraki Öğrenmeniz Gerekenler


Aşağıdaki eğitimler, bu rehberde gösterilen tekniklere dayanan ve ilgili konuları derinlemesine ele alan içeriklerdir. Her kaynak, adım adım açıklamalar ve tam çalışan kod örnekleri sunar; böylece API özelliklerini daha iyi kavrayabilir ve projelerinizde alternatif uygulama yaklaşımları keşfedebilirsiniz.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}