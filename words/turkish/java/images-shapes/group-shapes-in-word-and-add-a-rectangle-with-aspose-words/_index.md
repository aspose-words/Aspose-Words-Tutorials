---
category: general
date: 2026-09-11
description: Word'de şekilleri gruplayın ve Aspose.Words for Java kullanarak bir dikdörtgen
  şekli ekleyin. Şekil boyutunu nasıl ayarlayacağınızı, nesneleri nasıl gruplayacağınızı
  ve belgeyi nasıl kaydedeceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: tr
lastmod: 2026-09-11
og_description: Word'de şekilleri gruplayın ve Aspose.Words for Java kullanarak bir
  dikdörtgen şekli ekleyin. Bu öğreticide şekil boyutunu ayarlama, şekilleri gruplama
  ve belgeyi dışa aktarma gösterilmektedir.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Word'de şekilleri gruplayın – Aspose.Words ile dikdörtgen ekleyin
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Word'de şekilleri gruplayın ve Aspose.Words ile bir dikdörtgen ekleyin
url: /tr/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de şekilleri gruplayın ve Aspose.Words ile bir dikdörtgen ekleyin

Word'de **şekilleri gruplayarak** programlı bir şekilde bir dikdörtgen eklemeniz gerekiyorsa, bu kılavuz size eksiksiz, çalıştırmaya hazır bir çözüm sunar. Bir grup şekil eklemenin, bir dikdörtgen şekli eklemenin, şekil boyutunu ayarlamanın ve sonunda belgeyi kaydedip sonucu anında görüntülemenin tam olarak nasıl yapılacağını göreceksiniz.

Word belgeleriyle çalışmak genellikle birden fazla nesneyi—resimler, grafikler veya basit geometrik şekiller—tek bir mantıksal birimde düzenlemeyi gerektirir. Bu nesneleri gruplayarak, birlikte hareket ettirmeleri, döndürmeleri veya stillendirmeleri daha kolay olur. Bu öğreticide ayrıca **dikdörtgen ekleme** şekillerini ve **şekil boyutunu ayarlama** konularını da kapsayacağız.

## Öğrenecekleriniz

* Aspose.Words for Java ile yeni bir Word belgesi oluşturma.  
* **Şekilleri gruplama** böylece tek bir nesne gibi davranırlar.  
* **Gruba dikdörtgen şekli ekleme** ve aynı gruba bir resim ekleme.  
* **Şekil boyutunu ayarlama** hem dikdörtgen hem de resim için.  
* Belgeyi kaydedip Microsoft Word'de açarak sonucu doğrulama.

### Önkoşullar

* Java 17 veya daha yeni bir sürüm kurulu.  
* Bağımlılıkları yönetmek için Maven veya Gradle.  
* Geçerli bir Aspose.Words for Java lisansı (veya ücretsiz deneme anahtarı).  
* Bilinen bir dizine yerleştirilmiş bir resim dosyası (`sample.png`) (`YOUR_DIRECTORY` ifadesini gerçek yolunuzla değiştirin).

---

## Aspose.Words kullanarak Word'de şekilleri nasıl gruplayabilirsiniz

İlk adım bir `Document` ve bir `DocumentBuilder` oluşturmaktır. Builder, şekiller, metin ve diğer öğeleri eklemek için kullanışlı bir API sağlar.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Neden önemli:** `DocumentBuilder` doğrudan temel `Document` nesnesiyle çalışır, düşük seviyeli düğüm koleksiyonlarını manuel olarak yönetmeden şekil eklemenizi sağlar.

### Grup şekli ekleme

Grup şekli, diğer şekilleri tutabilen bir kapsayıcıdır. Bunu çizim nesneleri için bir klasör gibi düşünün.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

`insertGroupShape()` yöntemi bir `GroupShape` düğümü oluşturur ve döndürür, böylece daha sonra alt şekilleri ekleyebilirsiniz.  

---

## Gruba bir dikdörtgen şekli ekleme

Şimdi, önceden oluşturulan gruba **dikdörtgen şekli ekleyeceğiz**. Dikdörtgen, resim için bir arka plan veya kenarlık görevi görecek.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **İpucu:** `FillColor` ve `StrokeColor` ayarlamak, dikdörtgeni son belgede görünür kılar. Bu özellikleri atlamanız durumunda şekil şeffaf görünebilir.

### Dikdörtgen ekleme

Yukarıdaki kod, `ShapeType.RECTANGLE` ile bir `Shape` örneği oluşturarak ve ardından bunu `GroupShape`'e ekleyerek **dikdörtgen eklemenin** nasıl yapılacağını gösterir. Bu desen, diğer şekil türleri için de çalışır (ör. `ELLIPSE`, `POLYLINE`).

---

## Dikdörtgen ve resim için şekil boyutunu ayarlama

Doğru boyutlandırma, dikdörtgen ve resmin doğru hizalanmasını sağlar. Burada ayrıca ekleyeceğimiz resim için **şekil boyutunu ayarlıyoruz**.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Dikdörtgen ve resim artık aynı boyutları (100 × 50 point) paylaşıyor. Aynı gruba ait oldukları için, grubu hareket ettirmek veya döndürmek her iki şekli de birlikte etkiler.

> **Neden boyutları eşleştirmeli?** Boyutları hizalamak, resmin dikdörtgenin içinde düzgün bir şekilde oturmasını sağlar ve temiz bir “çerçeveli resim” etkisi yaratır.

---

## Belgeyi kaydedin ve sonucu görüntüleyin

Son olarak belgeyi diske yazıyoruz. Dosyayı Microsoft Word'de açtığınızda, gruplanmış şekiller tek bir seçilebilir nesne olarak gösterilir.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

`output.docx` dosyasını açtığınızda, içinde resim bulunan bir dikdörtgen göreceksiniz. Şekle tıkladığınızda hem dikdörtgen hem de resim seçilir çünkü **gruplandırılmıştır**.

![Word'de grup şekilleri örneği](https://example.com/images/group-shapes-word.png "Word'de grup şekilleri örneği")

*Resim alt metni:* *Word'de grup şekilleri örneği* – bir grup dikdörtgen ve resim gösteren bir Word belgesi.

---

## Yaygın sorular ve uç‑durum yönetimi

| Soru | Cevap |
|----------|--------|
| **Resim için farklı bir boyuta ihtiyacım olursa ne yapmalıyım?** | `picture.setWidth()` ve `picture.setHeight()` metodlarını eklemeden sonra ayarlayın. Dikdörtgen orijinal boyutunu koruyabilir veya ona da uyacak şekilde yeniden boyutlandırabilirsiniz. |
| **Aynı gruba daha fazla şekil ekleyebilir miyim?** | Evet. Ekstra `Shape` nesneleri için `group.appendChild(newShape)` metodunu çağırın. |
| **Tüm grubu nasıl döndürürüm?** | `group.setRotationAngle(double angleInRadians)` metodunu kullanın. Döndürme, her alt şekle uygulanır. |
| **Resim dosyası eksik olursa ne olur?** | `insertImage` `FileNotFoundException` hatası fırlatır. Çağrıyı bir try‑catch bloğuna alın ve bir yedek yer tutucu şekil sağlayın. |
| **Daha sonra grubu ayırmak mümkün mü?** | Çocukları ayırmak için `group.removeAllChildren()` metodunu çağırın, ardından onları belgeye tek tek yeniden ekleyin. |

---

## Sonuç

Artık Aspose.Words for Java kullanarak **Word'de şekilleri nasıl gruplayacağınızı**, **dikdörtgen şekli eklemeyi**, **şekil boyutunu ayarlamayı** ve **belgeyi kaydetmeyi** gösteren eksiksiz, çalıştırılabilir bir örneğe sahipsiniz. Dikdörtgeni ve resmi gruplayarak, onları tek bir birim olarak hareket ettirebilir, yeniden boyutlandırabilir veya döndürebilirsiniz—bu, birçok belge‑otomasyon senaryosunun tam olarak ihtiyaç duyduğu şeydir.

Buradan aşağıdakileri keşfedebilirsiniz:

* Aynı gruba metin kutuları ekleme (`how to add rectangle`‑stilinde metin).  
* Farklı dolgu desenleri veya degrade uygulama (`set shape size` ile stil birleştirme).  
* Aynı tekniği kullanarak grafikler, tablolar veya SmartArt'ı gruplayın (`how to group shapes` diğer nesne türlerinde).  

Diğer şekil türleri, renkler ve düzen seçenekleriyle denemeler yapmaktan çekinmeyin. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren eksiksiz çalışan kod örnekleri sunar.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}