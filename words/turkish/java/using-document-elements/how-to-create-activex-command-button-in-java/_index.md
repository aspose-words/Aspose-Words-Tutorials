---
category: general
date: 2026-10-07
description: Java'da ActiveX komut düğmesi oluşturun ve programlı olarak Word belgelerine
  komut düğmesi ekleyin. Düğmenin sol üst konumlarını nasıl ayarlayacağınızı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: tr
lastmod: 2026-10-07
og_description: Java'da ActiveX komut düğmesi oluşturarak Word belgelerinize etkileşimli
  denetimler ekleyin. Komut düğmesini programlı olarak nasıl ekleyeceğinizi, konumunu
  nasıl ayarlayacağınızı ve görünümünü nasıl özelleştireceğinizi öğrenin.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Java'da ActiveX komut düğmesi oluşturma – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Java'da ActiveX komut düğmesi nasıl oluşturulur
url: /tr/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java'da ActiveX komut düğmesi oluşturma

Java kullanarak bir Word belgesinde **ActiveX komut düğmesi oluşturma** ihtiyacınız varsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. `setLeft` ve `setTop` ile konumlandırılan, **komut düğmesini programlı olarak ekleyen** tam ve çalıştırılabilir bir örnek görecek ve sonucu bir `.docx` dosyası olarak kaydedeceksiniz.

Etkileşimli bir düğme eklemek, formlar oluşturmanıza, iş akışlarını otomatikleştirmenize veya kullanıcı girdisini doğrudan bir Word dosyası içinde toplamanıza olanak tanır. Aşağıdaki adımlar, proje kurulumundan son doğrulamaya kadar her şeyi kapsar, böylece kodu kendi projenize eksiksiz bir şekilde kopyalayabilirsiniz.

## Gereksinimler

Başlamadan önce şunların yüklü olduğundan emin olun:

- JDK 17 veya daha yeni bir sürüm yüklü  
- Maven 3.8+ (veya tercih ettiğiniz yapı aracı)  
- Aspose.Words for Java 23.9 veya daha yeni – `DocumentBuilder` ve OLE kontrol desteği sağlayan kütüphane  
- Java sözdizimi ve nesne‑yönelimli kavramlara temel aşinalık  

Maven kullanıyorsanız, bağımlılığı `pom.xml` dosyanıza ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **İpucu:** En son Aspose.Words sürümünü kullanarak hata düzeltmelerinden ve yeni OLE özelliklerinden yararlanabilirsiniz.

## Adım 1: Yeni boş bir belge ve DocumentBuilder oluşturma

**ActiveX komut düğmesi oluşturma** için ilk adım, boş bir `Document` ve bir `DocumentBuilder` örneği oluşturmaktır. Builder, OLE kontrolleri dahil içerik eklemek için akıcı bir API sunar.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document`, Word dosyasını bellekte temsil ederken, `DocumentBuilder` elemanları tam olarak istediğiniz yere yerleştirmenizi sağlayan bir imleç görevi görür.

## Adım 2: OLE komut düğmesi kontrolü ekleme

ActiveX kontrolleri OLE nesneleri olarak eklenir. Aspose.Words bu amaçla `Forms2OleControl` sınıfını sağlar.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

`insertForms2OleControl()` metodunu çağırdığınızda, Aspose otomatik olarak ActiveX düğmesini barındıracak bir yer tutucu şekil oluşturur.

## Adım 3: Düğmenin özelliklerini yapılandırma

Şimdi **komut düğmesini programlı olarak ekleme** ayrıntılarını, örneğin ProgID, başlık ve boyut gibi özellikleri ayarlayın. Bir komut düğmesi için en yaygın ProgID `"Forms.CommandButton.1"` dir.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Düğmenin sol üst konumunu ayarlama

Düğmenin konumlandırılması, ikincil anahtar kelime **how to set button left top** ile ilgili hale gelir. `setLeft` ve `setTop` metodları, puan cinsinden değerler alır (1 puan = 1/72 in).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Bu sayıları düzenleyerek tasarımınıza uydurun. Örneğin, düğmeyi bir tablo hücresiyle hizalamak için hücrenin koordinatlarını hesaplayıp `setLeft`/`setTop` metodlarına geçirebilirsiniz.

## Adım 4: Belgeyi kaydetme

Son olarak belgeyi diske yazın. Dosya, Microsoft Word'de açıldığında etkileşim için hazır bir ActiveX düğmesi içerecektir.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

`main` metodunu çalıştırdığınızda `CommandButton.docx` oluşur. Dosyayı Word'de açın, istenirse içeriği etkinleştirin ve **Click Me** etiketiyle belirtilen koordinatlarda bir tıklanabilir düğme gördüğünüzden emin olun.

![Java'da ActiveX komut düğmesi oluşturma](/images/activex-button-screenshot.png){.center width=600 alt="Java'da ActiveX komut düğmesi oluşturma ekran görüntüsü, Word belgesi içindeki düğmeyi gösteriyor"}

## Yaygın varyasyonlar ve uç durumlar

### Birden fazla düğme ekleme

Birden fazla düğmeye ihtiyacınız varsa, her kontrol için **Adım 2** ve **Adım 3**'ü tekrarlayın. Düğmelerin çakışmaması için `setLeft` ve `setTop` değerlerini ayarlamayı unutmayın.

### Düğme davranışını değiştirme

ActiveX düğmeleri tıklandığında VBA makroları çalıştırabilir. Bir makro eklemek için `setOnAction` özelliğini makro adıyla ayarlayın:

```java
commandButton.setOnAction("MyMacro");
```

Hedef belgenin ilgili VBA modülünü içerdiğinden emin olun; aksi takdirde Word bir hata gösterir.

### Uyumluluk notları

- Düğme, yalnızca ActiveX'i destekleyen masaüstü Word sürümlerinde (ör. Windows için Word) çalışır. Mac için Word veya çevrimiçi editörlerde statik bir resim olarak görünür.  
- Karma bir ortam hedefliyorsanız, ActiveX kontrolü yerine **content control** (`RichTextContentControl`) kullanmayı düşünün.

## Referans için tam kaynak kodu

Aşağıda, yeni bir Maven projesine kopyalayıp hemen çalıştırabileceğiniz, eksiksiz ve bağımsız bir örnek yer almaktadır.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Beklenen çıktı:** Çalıştırdıktan sonra proje çalışma dizininizde `CommandButton.docx` dosyasını bulacaksınız. Microsoft Word'de dosyayı açtığınızda, “Click Me” başlıklı bir düğmenin belirtilen konumda göründüğünü göreceksiniz.

## Sonuç

Artık Java'da **ActiveX komut düğmesi oluşturma**, bir Word belgesine **komut düğmesini programlı olarak ekleme** ve **how to set button left top** yöntemleriyle konumunu hassas bir şekilde kontrol etme konusunda bilgi sahibisiniz. Bu teknik, makroları tetikleyebilen, harici uygulamaları başlatabilen veya doğrudan belge içinde kullanıcı girdisi toplayabilen zengin, etkileşimli Word formları oluşturmanıza olanak tanır.

### Sonraki adımlar

- `Forms.TextBox.1` veya `Forms.CheckBox.1` gibi diğer ActiveX kontrollerini keşfedin.  
- Tam özellikli formlar oluşturmak için bir VBA modülüyle birden fazla kontrolü birleştirin.  
- Çapraz platform uyumluluğu gerekiyorsa ActiveX yerine içerik kontrollerini kullanın.  

Boyut, başlık ve konumlandırma ile deneyler yaparak UI tasarımınıza uygun hale getirin. Sorunlarla karşılaşırsanız, kullandığınız Aspose.Words sürümünün OLE kontrollerini desteklediğini ve Word güvenlik ayarlarının ActiveX çalıştırmaya izin verdiğini iki kez kontrol edin. İyi kodlamalar!

## Bir sonraki öğrenmeniz gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Word Belgelerinde OLE Nesneleri ve ActiveX Kontrolleri Gömme](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Aspose.Words for Java'da DocumentBuilder ile form alanları oluşturma ve içerik ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Java ile Word'de dikdörtgen şekil oluşturma – Tam Kılavuz](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}