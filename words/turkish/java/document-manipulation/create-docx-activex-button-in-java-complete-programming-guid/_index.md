---
category: general
date: 2026-08-14
description: Aspose.Words ile Java’da docx ActiveX düğmesi oluşturun. Word’de programlı
  olarak bir form düğmesi eklemeyi ve belgeyi kaydetmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: tr
lastmod: 2026-08-14
og_description: Aspose.Words kullanarak Java'da docx ActiveX düğmesi oluşturun. Bu
  kılavuz, Word'de bir form düğmesi eklemeyi, yapılandırmayı ve dosyayı kaydetmeyi
  gösterir.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Java'da docx ActiveX düğmesi oluşturma – adım adım öğretici
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Java’da docx ActiveX düğmesi oluşturma – tam programlama rehberi
url: /tr/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da docx ActiveX düğmesi oluşturma – tam programlama rehberi

Java’da **docx ActiveX düğmesi oluşturmanız** gerekiyorsa, bu rehber size tüm süreci adım adım gösterir. Word’de bir form düğmesi eklemeyi, özelliklerini yapılandırmayı ve kullanıma hazır bir .docx dosyası üretmeyi öğreneceksiniz.

ActiveX denetimlerini kullanmak, eski Word formlarını otomatikleştirirken yaygın bir gereksinimdir. Bu öğreticide, Aspose.Words for Java kütüphanesini kullanarak **add form button word** belgeleri eklemeyi öğrenecek ve manuel düzenleme yapmadan etkileşimli denetimler gömebileceksiniz.

## Gereksinimler

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

* Java 17 veya daha yeni bir sürüm (kod daha eski sürümlerle derlenebilir, ancak Java 17 önerilir).
* Aspose.Words for Java 23.10 veya daha yenisi – JAR dosyasını Aspose web sitesinden indirin veya Maven bağımlılığını ekleyin.
* Bir IDE (IntelliJ IDEA, Eclipse veya VS Code) ya da basit bir metin düzenleyici ve komut satırı derleme araçları.
* Java sözdizimi ve nesne‑yönelimli programlama hakkında temel bilgi.

## Aspose.Words ile docx ActiveX düğmesi oluşturma

Aşağıdaki adımlar, **docx ActiveX düğmesi oluşturma** nesnelerini oluşturup bir Word belgesine gömmek için gereken tam sıralamayı gösterir.

### Adım 1: Projeyi kurun ve Aspose.Words’u içe aktarın

Maven kullanıyorsanız `pom.xml` dosyanıza Aspose.Words bağımlılığını ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Veya Gradle tercih ediyorsanız:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Bağımlılık çözüldükten sonra Java kaynak dosyanıza gerekli sınıfları içe aktarın:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Bu içe aktarmalar, ActiveX denetimlerini eklemek için kullanılan `Document`, `DocumentBuilder` ve `Forms2OleControl` API’sine erişim sağlar.

### Adım 2: Yeni boş bir belge oluşturun

Boş bir Word dosyasını temsil eden bir `Document` nesnesi oluşturun.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Belgeyi önce oluşturmak, sonraki builder’ın temiz bir tuval üzerinde çalışmasını sağlar.

### Adım 3: DocumentBuilder’ı başlatın

`DocumentBuilder`, metin, resim ve denetim eklemek için akıcı bir arayüz sunar. Oluşturduğunuz belgeye bağlayın.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

Builder, belgedeki mevcut imleç konumunu izler; böylece sonraki ekleme tam olarak istediğiniz yere yapılır.

### Adım 4: ActiveX CommandButton denetimini ekleyin

ActiveX `CommandButton` eklemek için `insertForms2OleControl` metodunu kullanın. Bu metod, daha sonra yapılandırabileceğiniz bir `Forms2OleControl` örneği döndürür.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

Bu aşamada .docx dosyası bir düğme yer tutucusu içerir, ancak henüz görsel bir başlık veya boyut ayarı yoktur.

### Adım 5: Düğmenin özelliklerini yapılandırın

Denetimin adını, başlığını ve yerleşim özelliklerini ayarlayın. Bu değerler, düğmenin Word içinde nasıl görüneceğini ve VBA ya da otomasyon betikleri aracılığıyla nasıl referans alınacağını belirler.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **İpucu:** Word konumları puan (point) cinsinden ölçülür (1 pt ≈ 1/72 in). `setTop` ve `setLeft` değerlerini, düğmeyi çevredeki içerikle hizalayacak şekilde ayarlayın.

### Adım 6: Belgeyi kaydedin

Son olarak belgeyi diske yazın. Dosyanın modern Office Open XML formatında kalması için `.docx` uzantısını kullanın.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Microsoft Word’de oluşturulan dosyayı açtığınızda, belirttiğiniz koordinatlarda **Submit** adlı bir düğme göreceksiniz. Word içinde düğmeye tıklamak herhangi bir eylemi tetiklemez; VBA kodu eklemediğiniz sürece sadece form‑tabanlı iş akışları için tam işlevsel bir denetim olur.

## Yaygın sorular ve uç durumlar

| Soru | Cevap |
|----------|--------|
| **Özel bir Word sürümüne ihtiyacım var mı?** | ActiveX denetimleri, Windows üzerindeki masaüstü Microsoft Word sürümünde desteklenir. Mac için Word ya da Word Online’da mevcut değildir. |
| **`.doc` dosyalarıyla da kullanabilir miyim?** | Evet. Belgeyi `.doc` uzantısıyla kaydedin (`document.save("ActiveXButton.doc")`). Aynı API eski ikili format için de çalışır. |
| **Düğme görünmüyorsa ne yapmalıyım?** | **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** menüsünden ActiveX denetimlerine izin verildiğinden emin olun. Ayrıca belgenin “Protected View” (Korunan Görünüm) içinde açılmadığını kontrol edin. |
| **Başka ActiveX denetimleri ekleyebilir miyim?** | Kesinlikle. `Forms2OleControlType.COMMAND_BUTTON` yerine `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` vb. kullanabilirsiniz. |
| **Boyut sınırlaması var mı?** | Denetim boyutu yalnızca sayfa düzeniyle sınırlıdır. Çok büyük boyutlar sayfa taşmasına neden olabilir. |

## Tam, çalıştırılabilir örnek

Aşağıda, kopyalayıp derleyebileceğiniz ve çalıştırabileceğiniz eksiksiz bir Java sınıfı bulunmaktadır. Tüm içe aktarmalar, `main` metodu ve açıklayıcı yorumlar içerir.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Beklenen sonuç:** Programı çalıştırdıktan sonra çalışma dizininde `ActiveXButton.docx` dosyası oluşur. Microsoft Word’de açtığınızda, ilk sayfanın sol‑üst kısmına yerleştirilmiş tıklanabilir bir **Submit** düğmesi görürsünüz.

## Sonuç

Artık Aspose.Words kullanarak Java’da **docx ActiveX düğmesi oluşturma** nesnelerini nasıl oluşturacağınızı ve **add form button word** belgelerini programatik olarak nasıl ekleyeceğinizi biliyorsunuz. Projeyi kurma, belge oluşturma, denetimi ekleme, özelliklerini yapılandırma ve kaydetme adımları, baştan sona tüm iş akışını kapsar.

İleride şunları keşfedebilirsiniz:

* Düğme tıklamasına yanıt veren VBA makroları eklemek.
* Onay kutuları veya liste kutuları gibi diğer ActiveX denetimlerini gömmek.
* Birden fazla etkileşimli öğe içeren çok sayfalı formların otomatik oluşturulması.

Boyutları, konumları ve başlıkları kendi form tasarım gereksinimlerinize göre deneyimlemekten çekinmeyin. İyi kodlamalar!

## Bir Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}