---
category: general
date: 2026-10-04
description: Aspose.Words ile Java’da yeni bir belge için DocumentBuilder’ı nasıl
  başlatacağınızı ve bir ActiveX düğmesi ekleyeceğinizi öğrenin. Tam kodlu adım adım
  rehber.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: tr
lastmod: 2026-10-04
og_description: Yeni belge için DocumentBuilder'ı başlatın ve Aspose.Words Java API'siyle
  bir ActiveX komut düğmesi ekleyin. Bu özlü öğreticiyi izleyin.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: Yeni belge için DocumentBuilder'ı başlat – kapsamlı Aspose.Words rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Aspose.Words kullanarak yeni belge için DocumentBuilder nasıl başlatılır
url: /tr/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile yeni belge için DocumentBuilder nasıl başlatılır

Bir Java projesinde **yeni belge için DocumentBuilder başlatmanız** gerektiğinde, bu öğretici tam adımları gösterir. Boş bir Word dosyası oluşturmayı, bir ActiveX komut düğmesi eklemeyi ve sonucu kaydetmeyi tek bir, bağımsız kod örneğiyle göreceksiniz.

Word belgeleriyle programlı olarak çalışmak, genellikle form denetimleri gibi düşük seviyeli ayrıntıları yönetmeyi gerektirir. Bu kılavuzun sonunda IDE’nizden çıkmadan bir ActiveX düğmesi gömebileceksiniz; bu, şablonlar, otomatik raporlar veya etkileşimli formlar oluşturmak için faydalıdır.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* Java 17 veya daha yeni bir sürüm  
* Maven 3.8+ (ya da tercih ederseniz Gradle)  
* Aspose.Words for Java lisansı (test için ücretsiz deneme sürümü yeterli)  
* Java sözdizimi hakkında temel bilgi  

Aspose.Words, Word belgeleri oluşturmak, düzenlemek ve kaydetmek için yüksek seviyeli bir API sağlar. `DocumentBuilder` sınıfı, belge içeriği oluşturmanın temel giriş noktasıdır.

## Adım 1: Maven projesini ayarlayın

Yeni bir Maven projesi oluşturun (ya da mevcut bir projeye ekleyin) ve Aspose.Words bağımlılığını ekleyin:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Pro ipucu:** Kütüphane sürümünü güncel tutun; yeni sürümler ek form denetimleri desteği ekler ve performansı artırır.

## Adım 2: Yeni belge için `DocumentBuilder`'ı başlatın

Öğreticinin çekirdeği **yeni belge için DocumentBuilder başlatma** işlemidir. Önce boş bir `Document` örneği oluşturur, ardından bunu `DocumentBuilder` yapıcısına geçirirsiniz.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Neden önemli:* `DocumentBuilder`'ı başlatmak, oluşturucuyu belirli bir `Document` nesnesine bağlar; böylece paragraflar, tablolar veya form denetimlerini doğrudan o belgeye ekleyebilirsiniz. Bu adım olmadan oluşturucu çalışacak bir hedefe sahip olmaz.

## Adım 3: ActiveX komut düğmesi denetimi ekleyin

Aspose.Words, eski ActiveX denetimlerini gömmek için `Forms2OleControl` sınıfını sunar. Aşağıdaki kod, geçerli imleç konumuna bir **Forms2OleControl komut düğmesi** ekler.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### ActiveX komut düğmesi nedir?

ActiveX komut düğmesi, bir Word belgesi içinde kullanıcı tıkladığında makroları çalıştırabilen veya olayları tetikleyebilen eski bir UI öğesidir. Modern Office sürümleri İçerik Denetimlerini tercih etse de, birçok kurumsal şablon hâlâ geriye dönük uyumluluk için ActiveX kullanır.

## Adım 4: Belgeyi kaydedin

Denetimi ekledikten sonra sadece `save` metodunu çağırmanız yeterlidir. Dosya, ActiveX düğmesini içerir ve Microsoft Word’de açılabilir.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

`ActiveXButton.docx` dosyasını Word’de açtığınızda **Click Me** etiketiyle bir düğme göreceksiniz. Düğmeye tıklamak bir şey yapmaz; bir makro eklemediğiniz sürece sadece denetim işlevsel olur.

## Tam, çalıştırılabilir örnek

Aşağıda `src/main/java/com/example/ActiveXButtonDemo.java` içine kopyalayıp yapıştırabileceğiniz tam program yer alıyor. Gerekli tüm importları ve hızlı bir test için hata yönetimini içerir.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Beklenen çıktı**

```
Document saved to output/ActiveXButton.docx
```

Oluşturulan dosyayı Microsoft Word 2016 veya daha yeni bir sürümde açın; ilk sayfanın üst kısmında *Click Me* etiketiyle bir düğme görmelisiniz.

## Yaygın varyasyonlar ve kenar durumları

| Senaryo | Ayarlama |
|----------|------------|
| **Düğmeyi belirli bir paragrafa ekle** | `builder.moveToParagraph(index, NodeType.PARAGRAPH);` ile oluşturucunun imlecini hareket ettirip `insertForms2OleControl` metodunu çağırmadan önce. |
| **Düğme boyutunu ayarla** | `commandButton.setWidth(100);` ve `commandButton.setHeight(30);` ile boyutları puan cinsinden tanımlayın. |
| **Düğmeye bir makro ekle** | Belgeyi kaydettikten sonra Word’de açın, Geliştirici sekmesini etkinleştirin ve düğmeye manuel olarak bir VBA makrosu ekleyin (ActiveX denetimleri doğrudan Aspose.Words’tan scriptlenemez). |
| **.doc (ikili) formatını hedefle** | `doc.save(outputPath, SaveFormat.DOC);` kullanarak eski Word 97‑2003 dosyası üretin. |
| **Android’da çalıştır** | Java API’si üzerinden Aspose.Words for Android kullanın; aynı kod, kütüphane APK’ye dahil edildiği sürece çalışır. |

## Sorun giderme ipuçları

* **`java.lang.NoClassDefFoundError`** – Aspose.Words JAR dosyasının sınıf yolunda olduğundan emin olun. Maven otomatik ekler; manuel derlemelerde JAR’ı `libs/` içine koyup IDE’nizin kütüphanelerine ekleyin.  
* **Düğme Word’de görünmüyor** – Word’ün Güven Merkezi’ndeki *Eski formları göster* seçeneğinin etkin olduğundan emin olun (`Dosya → Seçenekler → Güven Merkezi → Güven Merkezi Ayarları → Makro Ayarları`).  
* **Lisans istisnası** – Geçerli bir lisans olmadan kodu çalıştırırsanız Aspose.Words bir filigran ekler. Ücretsiz deneme kaydedin ya da lisans satın alarak filigranı kaldırın.

## Sonuç

Artık **yeni belge için DocumentBuilder başlatma**, bir ActiveX komut düğmesi ekleme ve sonucu Aspose.Words for Java ile kaydetme konusunda bilgi sahibisiniz. Bu desen, programlı olarak etkileşimli Word şablonları üretmenizi sağlar; otomatik raporlama veya form‑tabanlı iş akışları için özellikle kullanışlıdır.

Bundan sonra ek form denetimlerini (`Forms2OleControlType.CHECKBOX`, `COMBOBOX` vb.) keşfedebilir, düğmeyi özel VBA makrolarıyla birleştirebilir veya aynı `DocumentBuilder` akışıyla tablolar, görseller ve stil içeren tam özellikli belgeler oluşturabilirsiniz.

---

*Daha karmaşık Word otomasyonu oluşturmak mı istiyorsunuz? **DocumentBuilder ile tablo ekleme**, **programatik olarak stiller uygulama** ve **Aspose.Words ile PDF’ye dışa aktarma** rehberlerimize göz atın.*


## Sonra Ne Öğrenmelisiniz?


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım‑adım açıklamalar içerir.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Add a watermark to a document using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}