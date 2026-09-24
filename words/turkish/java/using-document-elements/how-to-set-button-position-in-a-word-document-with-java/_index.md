---
category: general
date: 2026-09-24
description: Java ve Aspose.Words kullanarak bir Word belgesinde düğme konumunu ayarlayın.
  Düğmeyi nasıl ekleyeceğinizi, ActiveX kontrolü eklemeyi ve Java tarzında Word belgesi
  oluşturmayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: tr
lastmod: 2026-09-24
og_description: Java kullanarak bir Word belgesinde düğme konumunu ayarlayın. Bu kılavuz,
  düğme eklemeyi, ActiveX kontrolü eklemeyi ve Aspose.Words ile Java Word belgesi
  oluşturmayı gösterir.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Java ile bir Word belgesinde düğme konumunu ayarlama – tam rehber
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Java ile bir Word belgesinde düğme konumunu nasıl ayarlarsınız
url: /tr/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java ile bir Word belgesinde düğme konumunu ayarlama

Bir Word dosyası içinde **düğme konumunu ayarlamanız** gerektiğinde, bu rehber size tam, çalıştırılabilir bir çözüm sunar. Kullanıcı etkileşimi gerektiren bir şablon oluşturuyor ya da bir formu otomatikleştiriyor olun, **Aspose.Words for Java** kullanarak **düğme ekleme** ve konumunu kontrol etme konusunda tam olarak ne yapmanız gerektiğini öğreneceksiniz.

Bu öğretici, bir Word belgesine **ActiveX kontrolü ekleme**, **Word'e düğme ekleme** ve **Word belgesi Java** tarzında oluşturma sürecinin tamamını kapsar. Harici referanslara gerek yok—sadece kopyalayın, çalıştırın ve sonucu doğrulayın.

## Önkoşullar

Başlamadan önce şunların kurulu olduğundan emin olun:

* Java 17 (veya herhangi bir Java 8+ çalışma zamanı)
* Bağımlılıkları yönetmek için Maven ya da Gradle
* Aspose.Words for Java lisansı (değerlendirme için ücretsiz deneme sürümü yeterli)
* Java sözdizimi hakkında temel bir anlayış

> **İpucu:** Aspose.Words JAR dosyalarınızı bir `libs/` klasöründe tutun ve sürüm çakışmalarını önlemek için proje sınıf yoluna ekleyin.

## Adım 1: Maven projesini kurun

Basit bir Maven projesi oluşturun (ya da Gradle kullanın) ve Aspose.Words bağımlılığını ekleyin:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

`mvn clean compile` komutunu çalıştırmak, kütüphaneyi indirir ve derleme yolunu hazırlar.

## Adım 2: Yeni bir Word belgesi oluşturun

İlk işlem, **Word belge java** tarzında **belge oluşturma**dır. Bir `Document` nesnesi ve dosyayı düzenlemenizi sağlayan bir `DocumentBuilder` örneği oluşturursunuz.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` sınıfı tüm .docx dosyasını temsil ederken, `DocumentBuilder` içerik eklemek için akıcı bir API sağlar.

## Adım 3: Düğme ekleme – ActiveX kontrolü ekleme

Aspose.Words, bir CommandButton gibi eski tip ActiveX kontrollerini eklemek için `Forms2OleControl` sınıfını sunar. Bu adım, **düğme ekleme** işlemini tam olarak gösterir.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

`insertForms2OleControl` yöntemi, yapılandırabileceğiniz bir `Forms2OleControl` örneği döndürür. Bu, **ActiveX kontrolü ekleme** sürecinin çekirdeğidir.

## Adım 4: Düğme konumunu ayarlama

Şimdi gerçekten **düğme konumunu ayarlıyoruz**. Kontrolün `setLeft` ve `setTop` metodları, puan (point) cinsinden değer alır (1 pt = 1/72 in). Düğmeyi tipik ekran koordinatlarıyla hizalamak için pikselleri puana dönüştürebilirsiniz (1 px ≈ 0.75 pt). Örnekte, düğmeyi sol kenardan 100 px, üst kenardan 150 px uzaklıkta konumlandırıyoruz.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

**Düğme konumunu ayarlama** mantığı burada kapsüllendiği için, bir kontrolü taşımanız gerektiğinde bu satırları yeniden kullanabilirsiniz. Sayıları, düzen gereksinimlerinize göre ayarlayın.

## Adım 5: Boyut ve başlık tanımlama

Etiketi olmayan bir düğme kafa karıştırıcıdır. Görünür bir görünüm kazandırmak için `setWidth`, `setHeight` ve `setCaption` kullanın.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

Boyut da puan cinsindendir, bu yüzden tutarlılık için piksellerden dönüştürme yapılır.

## Adım 6: Belgeyi kaydet – **Word belge java** akışını tamamlama

Son olarak dosyayı diske kalıcı olarak yazın. Yol mutlak ya da proje köküne göre göreli olabilir.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Programı çalıştırdığınızda `output` klasörü içinde `CommandButtonDemo.docx` oluşturulur. Dosyayı Microsoft Word’de açtığınızda, tam olarak belirlediğiniz konumda tıklanabilir bir düğme görürsünüz.

### Beklenen çıktı

* **CommandButtonDemo.docx** adlı bir `.docx` dosyası.
* Belge içinde, “Click Me” etiketiyle **CommandButton** sol kenardan 100 px, üst kenardan 150 px uzaklıkta görünür.
* Düğme, Word’de belge açıldığında tıklamalara yanıt verir (özel VBA kodu eklemediğiniz sürece varsayılan bir ActiveX mesajı gösterir).

## Adım 7: Yaygın varyasyonlar ve kenar durumları

### Birden fazla düğme ekleme

**Word'e düğme ekleme** işlemini birden fazla kez yapmanız gerekiyorsa, her seferinde yeni bir `Forms2OleControl` örneğiyle adım 3‑5’i tekrarlayın. Düğmelerin üst üste binmemesi için `setTop` değerini ayarlamayı unutmayın.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Lisans olmadan çalışma

Aspose.Words lisans olmadan kullanıldığında bir filigran ekler. Üretim kodu için bir lisans satın alın ve `main` metodunun başında uygulayın:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Daha eski Office sürümleriyle uyumluluk

ActiveX kontrolleri `.doc` (Word 97‑2003) formatında da desteklenir. Eski bir dosya oluşturmak için kaydetme formatını değiştirin:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Tam kaynak kodu (çalıştırılabilir)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Dosyayı `src/main/java/CommandButtonDemo.java` olarak kaydedin, `mvn exec:java -Dexec.mainClass=CommandButtonDemo` komutunu çalıştırın ve oluşturulan belgeyi açarak sonucu görün.

## Sıkça Sorulan Sorular

**S: Bu OpenJDK ile çalışır mı?**  
C: Evet. Aspose.Words saf Java’dır ve OpenJDK dahil tüm JDK 8+ implementasyonlarında çalışır.

**S: Düğmenin yazı tipini ya da rengini değiştirebilir miyim?**  
C: ActiveX düğme görünümü, ana uygulama (Word) tarafından kontrol edilir. Çalışma zamanında özellikleri değiştirmek için VBA kodu ekleyebilirsiniz, ancak statik görünüm varsayılan stile sınırlıdır.

**S: Düğmeyi bir tablo hücresi içinde konumlandırmam gerekirse ne yapmalıyım?**  
C: `DocumentBuilder` imlecini hücreye taşıdıktan sonra `insertForms2OleControl` çağırın. Kontrol, hücrenin düzenini miras alır ve hâlâ ince ayar için `setLeft`/`setTop` kullanılabilir.

## Sonuç

Artık Java kullanarak bir Word belgesinde **düğme konumunu ayarlama**, **düğme ekleme**, **ActiveX kontrolü ekleme** ve **Word'e düğme ekleme** konularını, **Word belge java** projeleri için en iyi uygulamaları izleyerek biliyorsunuz. Tam örnek, proje kurulumundan işlevsel bir CommandButton içeren `.docx` dosyasının kaydedilmesine kadar tüm iş akışını gösterir.

### Sonraki adımlar

* `Forms2OleControl.ControlType` değerlerinden diğerlerini (ör. `CHECKBOX`, `TEXTBOX`) keşfederek daha zengin formlar oluşturun.
* Özel tıklama işleme için düğmeyi VBA makrolarıyla birleştirin.
* Aspose.Words’ün mail‑merge özelliğini kullanarak, etkileşimli kontrolleri önceden içeren kişiselleştirilmiş belgeler üretin.

İyi kodlamalar ve Java ile Word belgelerini otomatikleştirmenin keyfini çıkarın!


## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words for Java’da DocumentBuilder ile form alanları oluşturma ve içerik ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for .NET ile Word Belgesine Combo Box Form Alanı Ekleme](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Aspose.Words Java ile Word Belgelerini Yükleme: Kapsamlı Rehber](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}