---
category: general
date: 2026-09-27
description: Aspose.Words kullanarak Java’da ActiveX içeren docx oluşturun. ActiveX
  komut düğmesini adım adım eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: tr
lastmod: 2026-09-27
og_description: Aspose.Words ile Java’da ActiveX içeren bir docx oluşturun. Bu kılavuzu
  izleyerek bir ActiveX komut düğmesi ekleyin ve belgeyi kaydedin.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Java’da ActiveX içeren docx oluşturma – tam rehber
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Java ve Aspose.Words ile ActiveX içeren docx nasıl oluşturulur
url: /tr/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java ve Aspose.Words ile ActiveX içeren docx nasıl oluşturulur

Eğer **ActiveX içeren docx oluşturmanız** gerekiyorsa, bu kılavuz size tam bir çözüm gösterir. Aspose.Words for Java kullanarak bir Word dosyasına **ActiveX komut düğmesi eklemeyi** öğrenecek ve ardından sonucu Microsoft Word'de açılabilecek bir .docx olarak kaydedeceksiniz.

Programatik olarak bir Word belgesi oluşturmak, manuel düzenlemeden sizi kurtarır ve raporlar, sözleşmeler veya form şablonları arasında tutarlılığı garanti eder. Aşağıdaki adımlar, proje kurulumundan yaygın sorunların ele alınmasına kadar her şeyi kapsar, böylece tekniği herhangi bir Java uygulamasına entegre edebilirsiniz.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* Java Development Kit (JDK) 8 veya daha yeni bir sürüm.
* Maven 3.6+ (veya tercih ettiğiniz başka bir yapı aracı).
* Aspose.Words for Java lisans dosyası (ücretsiz değerlendirme sürümü test için çalışır).
* ActiveX kontrolünü görsel olarak doğrulamak istiyorsanız hedef makinede Microsoft Word yüklü olmalı.

Bu öğeler gereklidir çünkü Aspose.Words belgeyi oluşturan API'yi sağlar, Word ise ActiveX kontrolünü render etmek için gereklidir.

## Adım 1: Maven projesini ayarlayın

Yeni bir Maven projesi oluşturun veya mevcut bir `pom.xml` dosyasına Aspose.Words bağımlılığını ekleyin:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **İpucu:** Aspose.Words sürümünü resmi sürüm notlarıyla senkronize tutun; böylece hata düzeltmelerinden ve yeni ActiveX özelliklerinden yararlanabilirsiniz.

## Adım 2: Belgeyi oluşturan Java kodunu yazın

`ActiveXDocxCreator` adlı bir sınıf oluşturun. Aşağıdaki kod, gerekli tüm importları, bir `main` metodunu ve her işlemi açıklayan ayrıntılı yorumları içerir.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Her satırın önemi

* `Document` tüm Word içeriği için kapsayıcıdır. Yeni bir örnek oluşturmak size temiz bir tuval sağlar.
* `DocumentBuilder` öğeleri eklemek için akıcı bir API sunar; ekleme noktasını otomatik olarak izler.
* `insertForms2OleControl()` genel bir OLE kontrol yer tutucusu oluşturur. Aspose.Words bunu bir ActiveX konteyneri olarak değerlendirir.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` Word'e yer tutucunun bir CommandButton olarak render edilmesi gerektiğini söyler.
* `setCaption("Click Me")` düğmede gösterilecek metni tanımlar.
* `setLeft` ve `setTop` düğmeyi sayfa kenar boşluklarına göre konumlandırır. Bu değerleri düzeninize göre ayarlayın.
* `setWidth` ve `setHeight` isteğe bağlıdır ancak varsayılan boyut çok küçük olduğunda düğmenin görünümünü iyileştirir.
* `doc.save` bellek içindeki yapıyı Word'ün açabileceği fiziksel bir .docx dosyasına yazar.

## Adım 3: Oluşturulan belgeyi doğrulayın

`output/ActiveXCommandButton.docx` dosyasını Microsoft Word'de açın:

1. Belge, **Click Me** etiketiyle bir düğme içeren tek bir sayfa göstermeli ve düğme sayfanın sol‑üst köşesine yakın bir konumda olmalıdır.
2. Düğme görünmüyorsa, Word'ün Güven Merkezi'nde **ActiveX kontrollerinin etkin olduğundan** emin olun (Dosya → Seçenekler → Güven Merkezi → Güven Merkezi Ayarları → ActiveX Ayarları).
3. Düğme yalnızca ActiveX'i destekleyen Windows sürümlerindeki Word'de çalışır. macOS veya web‑tabanlı Word'de kontrol statik bir görüntü olarak gösterilir.

## Adım 4: Yaygın kenar durumlarını ele alma

| Durum | Sebep | Önerilen eylem |
|-----------|--------|--------------------|
| Dosya açıldıktan sonra düğme eksik | Word'ün güvenlik ayarları ActiveX'i engelliyor | Güvenilen konumlar için “Tüm kontrolleri kısıtlama olmadan çalıştır” seçeneğini etkinleştirin. |
| Oluşturulan .docx açılamıyor | Uyumsuz Aspose.Words sürümü | En son Aspose.Words sürümüne yükseltin; eski sürümler gerekli OLE parçalarını doğru şekilde eklemeyebilir. |
| Düğmenin bir makro çalıştırması gerekiyor | ActiveX tek başına makro kodu içermez | ActiveX kontrolünü `Click` olayını işleyen bir VBA makrosu ile birleştirin. Makro‑etkin bir şablon eklemek için `DocumentBuilder.insertOleObject` metodunu kullanın. |
| Farklı sayfa boyutlarında düzen bozuk | Koordinatlar mutlak puanlarla verilmiş | Kontrolün konumlandırılmasından önce sayfa boyutunu standartlaştırmak için `builder.getPageSetup().setPageWidth` ve `setPageHeight` kullanın. |

## Adım 5: Çözümü genişletme

`ControlType` enum'ını değiştirerek diğer ActiveX kontrollerini ekleyebilirsiniz:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words ayrıca **ActiveX metin kutuları**, **liste kutuları** ve **combo kutuları** eklemeyi destekler. Aynı konumlandırma yöntemleri (`setLeft`, `setTop`, `setWidth`, `setHeight`) geçerlidir.

Birden fazla kontrol yerleştirmeniz gerekiyorsa, `builder.insertForms2OleControl()` metodunu tekrarlayın ve her kontrolün koordinatlarını buna göre ayarlayın.

## Tam kaynak dosyası

Aşağıda, kopyala‑yapıştır için hazır olan `ActiveXDocxCreator.java` dosyasının tamamı yer almaktadır:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

Bu programı çalıştırmak, **ActiveX içeren docx** üretir; böylece etkileşimli formlara ihtiyaç duyan son kullanıcılara dağıtabilirsiniz.

## Sonuç

Artık Java ve Aspose.Words kullanarak **ActiveX içeren docx oluşturmayı** ve **ActiveX komut düğmesini** programatik olarak eklemeyi biliyorsunuz. Kılavuz, proje kurulumu, tam kaynak kodu, doğrulama adımları ve tipik sorunlarla başa çıkma stratejilerini kapsadı. 

Bundan sonra şunları keşfedebilirsiniz:

* Düğme tıklamasına yanıt veren VBA makroları eklemek.
* Onay kutuları veya combo kutuları gibi diğer ActiveX kontrollerini gömmek.
* Dinamik veri ile çok sayfalı formların otomatik oluşturulması.

Farklı koordinatlar, boyutlar ve kontrol tipleriyle deneyler yaparak belge düzeninize en uygun çözümü bulun. İyi kodlamalar!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Aspose.Words for Java'da OLE Nesneleri ve ActiveX Kontrollerinin Kullanımı](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Aspose.Words for Java'da DocumentBuilder ile form alanları oluşturma ve içerik ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words ile Word'de dikdörtgen şekil oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}