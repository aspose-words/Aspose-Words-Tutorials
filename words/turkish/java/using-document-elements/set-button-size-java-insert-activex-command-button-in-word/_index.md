---
category: general
date: 2026-07-29
description: 'düğme boyutunu ayarla java öğreticisi: Java ve Aspose.Words kullanarak
  bir Word belgesine ActiveX komut düğmesi eklemeyi, ayrıca boyutlandırmayı ve boş
  belge oluşturmayı öğrenin.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: tr
lastmod: 2026-07-29
og_description: Set Button Size Java Kılavuzu, Java kullanarak bir Word dosyasına
  ActiveX komut düğmesi eklemeyi, boyutunu ayarlamayı ve belgeyi programlı olarak
  kaydetmeyi gösterir.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: Java'da düğme boyutunu ayarla – Java ile Word'e ActiveX Komut Düğmesi ekle
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: buton boyutunu ayarla java – Word’de ActiveX Komut Düğmesi Ekle
url: /tr/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – Word'de ActiveX Komut Düğmesi Ekleme

Ever wondered **how to set button size java** when you’re automating Word documents? Maybe you’re building a reporting tool that needs a clickable “Submit” button right inside the .docx file. In this tutorial we’ll walk through the entire process—creating a blank Word document, inserting an ActiveX command button, and explicitly setting its width and height—all with Java and Aspose.Words.

We’ll also answer the lingering “how to insert activex” question that pops up for many developers. By the end you’ll have a runnable program that produces a Word file containing a perfectly‑sized command button, ready for further customization.

---

## Gereksinimler

İlerlemeye başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

- **Java Development Kit (JDK) 8 veya daha yeni** – kod, herhangi bir yeni JDK ile derlenir.
- **Aspose.Words for Java** (July 2026 itibarıyla en son sürüm). JAR dosyasını [Aspose web sitesinden](https://products.aspose.com/words/java) ya da Maven üzerinden edinin:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- Bir IDE ya da basit bir metin düzenleyici—IntelliJ IDEA, Eclipse veya VS Code işinizi görecektir.
- Oluşturulan **CommandButton.docx** dosyasının bulunmasını istediğiniz bir klasör.

Hepsi bu kadar. Ek Office interop kütüphaneleri, COM hileleri yok, sadece saf Java.

## Adım‑Adım Uygulama

We’ll break the solution into five logical steps. Each step has a dedicated H2 header; one of them contains our **primary keyword** to satisfy SEO.

### 1. Projeyi Kurma ve Aspose.Words'i İçe Aktarma

First, create a new Maven (or Gradle) project and add the Aspose.Words dependency shown above. Then, import the required classes in your Java source file:

```java
import com.aspose.words.*;
```

> **Pro tip:** Bir IDE kullanıyorsanız, sınıfların otomatik içe aktarılmasına izin verin. Bu, çok fazla yazmayı tasarruf ettirir ve yazım hatalarını önler.

### 2. java create blank word Document

Şimdi gerçekten **java create blank word** belgesini oluşturuyoruz. Bu, daha sonra **insert command button word** ekleyeceğimiz temeldir.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

`Document` nesnesi, bellek içindeki tüm Word dosyasını temsil eder. Bu noktada dosyada sayfa, metin yok—sadece temiz bir sayfa.

### 3. DocumentBuilder'ı Başlatma ve ActiveX Kontrolünü Ekleme

`DocumentBuilder`, içerik, paragraf, tablo ve evet, ActiveX kontrolleri eklememizi sağlayan bir yardımcıdır. İşte **how to insert activex** sorusuna yanıt verdiğimiz yer:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl`, Aspose'in bir OLE nesnesi üzerindeki sarmalayıcısıdır. `COMMANDBUTTON` belirterek Word'e klasik bir ActiveX komut düğmesi gömmesini söylüyoruz.

### 4. How to Set Button Size Java – Genişlik ve Yüksekliği Ayarlama

Şimdi öğreticinin kalbi geliyor: **how to set button size java**. Kontrol, `Left`, `Top`, `Width` ve `Height` gibi birkaç yerleşim özelliği sunar. Bunları doğrudan ayarlamak, düğmenin sayfadaki görünümünü kontrol eder.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Bu sayılar neden? Word'de bir point, inçin 1/72'sine eşittir. Bu yüzden `120` point genişlik yaklaşık 1.67 inç eder—okunabilir bir etiket için yeterli, ama çok büyük değil. Değerleri düzenlemenize göre ayarlayın; aynı özellikler, sahip olabileceğiniz **how to set button** sorusuna da yanıt verir.

> **Not:** Farklı bir düğme türüne ihtiyacınız varsa (ör. bir onay kutusu), `Forms2OleControlType.COMMANDBUTTON` ifadesini uygun enum değeriyle değiştirin.

### 5. Belgeyi Kaydet

Son olarak, belgeyi diske kaydedin:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

`YOUR_DIRECTORY` ifadesini makinenizdeki mutlak ya da göreli bir yol ile değiştirin. Programı çalıştırdıktan sonra oluşturulan dosyayı Microsoft Word'de açın. Sol kenardan 100 pt, üstten 200 pt konumlandırılmış ve tam olarak ayarladığımız boyutta “Click Me” etiketiyle bir düğme göreceksiniz.

## Tam Çalışan Örnek

Aşağıda eksiksiz, çalıştırmaya hazır Java sınıfı yer alıyor. `CommandButtonActiveX.java` dosyasına kopyalayıp yapıştırın, çıktı yolunu ayarlayın ve **Run** tuşuna basın.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Beklenen çıktı:** Word'de `CommandButton.docx` dosyasını açtığınızda, yaklaşık sayfanın ortasında yer alan tıklanabilir bir “Click Me” düğmesi içeren tek bir sayfa görüntülenir. Düğmenin boyutları, ayarladığınız değerlerle eşleşir ve **set button size java**'nin amaçlandığı gibi çalıştığını doğrular.

## Yaygın Sorular ve Kenar Durumları

### Düğme Word'de görünmezse ne olur?

- **Word sürümünü kontrol edin.** ActiveX kontrolleri, Word'ün masaüstü sürümünü gerektirir; Word Online bunları kaldırır.
- **Aspose.Words lisansının uygulandığından emin olun** (ücretli bir sürüm kullanıyorsanız). Lisanssız deneme sürümü bir filigran ekleyebilir ancak kontrolü yine de gösterir.
- **Düğmenin yazı tipini veya rengini değiştirebilir miyim?** Evet. Kontrolü ekledikten sonra, altındaki OLE nesnesine erişebilir ve VBA özelliklerini manipüle edebilirsiniz. Bu daha ileri bir konudur—örneğin kırmızı bir başlık için `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` koduna bakın.
- **Düğmenin tıklama olayını nasıl yönetirim?** ActiveX komut düğmeleri bir VBA `Click` olayı tetikler. Düğmeyi işlevsel hale getirmek için aynı belgeye bir makro eklemeniz gerekir. Aspose.Words, `Document.getMacros()` API'si aracılığıyla bir makro modülü ekleyebilir, ancak makro kodu VBA ile yazılmalıdır.
- **Farklı düğme türleri hakkında ne söyleyebiliriz?** Aspose.Words, `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX` gibi birçok `Forms2OleControlType` değerini destekler. Deney yapmak için `insertForms2OleControl` çağrısındaki enum sabitini değiştirin.

## Üretim‑Hazır Kod İçin Pro İpuçları

- **Yerleşim değerleri için sabitler kullanın** – gelecekteki ayarlamaları kolaylaştırır.
- **Kaydetme yolunu bir `Path` nesnesi içinde sarın** – platforma özgü ayırıcıları önlemek için.
- **Document nesnesini serbest bırakın** (veya try‑with‑resources kullanın) eğer bir döngüde çok sayıda dosya işliyorsanız.
- **`save` çağrısı yapmadan önce çıktı klasörünü doğrulayın** – `FileNotFoundException` hatasını önlemek için.

## Sonuç

Şimdiye kadar **set button size java**'yi, boş bir Word dosyası oluşturup, bir ActiveX komut düğmesi ekleyerek ve boyutlarını tam olarak yapılandırarak öğrendiniz—hepsi birkaç satır Java kodu ile. Bu, **how to insert activex**, **how to set button**, **java create blank word** ve **insert command button word** konularının temelini tek bir, bağımsız örnek içinde kapsar.

Sonraki adımlar? Düğmenin başlığını özelleştirmeyi, tıklamalara yanıt veren bir makro eklemeyi veya aynı sayfada birden fazla kontrol gömmeyi deneyin. Ayrıca, oluşturulan .docx dosyasını Aspose.Words ile PDF'ye dönüştürüp düğmeyi statik bir görüntü olarak korumayı da keşfedebilirsiniz.

Denemekten çekinmeyin, bir sorunla karşılaşırsanız aşağıya yorum bırakın. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren eksiksiz çalışan kod örnekleri sunar.

- [Aspose.Words for Java'da DocumentBuilder Kullanarak Form Alanları Oluşturma ve İçerik Ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words Java ile Word Belgelerini Yükleme: Kapsamlı Rehber](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Aspose.Words for Java ile Belgeyi PDF Olarak Kaydetme](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}