---
category: general
date: 2026-10-20
description: Programlı olarak boş bir DOCX oluşturun ve Java kullanarak bir komut
  düğmesi ekleyin. Düğmeli Word belgesini kaydetmek ve komut düğmesi başlığını ayarlamak
  için tam Word belgesi oluşturma kodunu öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: tr
lastmod: 2026-10-20
og_description: Programlı olarak boş bir DOCX oluşturun ve bir komut düğmesi ekleyin.
  Düğmeli Word dosyasını kaydetmek ve komut düğmesi başlığını ayarlamak için bu adım
  adım Java rehberini izleyin.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Programlı olarak boş bir DOCX oluştur – bir komut düğmesi ekle
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: Programlı olarak boş bir DOCX oluştur ve bir komut düğmesi ekle
url: /tr/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş bir DOCX dosyasını programlı olarak oluşturun ve bir komut düğmesi ekleyin

Programlı olarak **boş bir DOCX oluşturmanız** gerekiyorsa, bu öğretici dosyaya doğrudan bir komut düğmesi yerleştirmenizi gösterir. Bir düğmeli Word belgesini kaydeden, **komut düğmesi başlığını ayarlamanıza** izin veren ve en son Aspose.Words for Java kütüphanesiyle çalışan tam *create word document code* alacaksınız.

Bir DOCX dosyasına etkileşimli denetimler eklemek, makroları tetikleyen, harici programları başlatan veya sadece kullanıcıları tıklanabilir bir “Click Me” düğmesiyle yönlendiren şablonlar dağıtmak istediğinizde faydalıdır. Aşağıdaki adımlar, boş bir belgeyi başlatmaktan dosyanın diske kaydedilmesine kadar her şeyi kapsar.

## Önkoşullar

* Java 17 veya daha yeni bir sürüm yüklü.
* Bağımlılıkları yönetmek için Maven (veya tercih ettiğiniz derleme aracı).
* Aspose.Words for Java 23.9 veya daha yenisi. Bağımlılığı `pom.xml` dosyanıza ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* IntelliJ IDEA veya VS Code gibi bir IDE (Java destekleyen herhangi bir editör çalışır).

## Boş bir DOCX dosyasını programlı olarak oluşturma – adım adım

Aşağıdaki bölümler süreci net, numaralı adımlara ayırır. Her adım, sadece **ne** yazılacağını değil, **neden** gerektiğini açıklar.

### Adım 1: Yeni bir boş belge başlatma

Boş bir belge, komut düğmesini yerleştireceğiniz tuvaldir. Aspose.Words bu amaçla `Document` sınıfını sağlar.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Neden önemli*: Boş bir `Document` ile başlamak, gizli biçimlendirme veya mevcut denetimlerin daha sonra ekleyeceğiniz düğmeye müdahale etmesini önler.

### Adım 2: `DocumentBuilder`'ı kurma

`DocumentBuilder`, düşük seviyeli düğüm manipülasyonu ile uğraşmadan OLE denetimleri dahil içerik eklemenizi sağlayan bir yardımcıdır.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Neden önemli*: Builder mevcut imleç konumunu korur, böylece düğme tam olarak belirttiğiniz yere yerleştirilir.

### Adım 3: OLE komut düğmesi ekleme

Word, etkileşimli denetimleri OLE (Object Linking and Embedding) nesneleri olarak kabul eder. Aspose.Words bunun için `Forms2OleControl` sınıfını sunar.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Neden önemli*: Denetimi eklemek, daha sonra (tür, başlık, konum) yapılandırabileceğiniz bir yer tutucu oluşturur.

### Adım 4: Düğmeyi yapılandırma – tür, başlık ve konum

Denetimin türünü (`COMMANDBUTTON`) tanımlamalı, kullanıcıya görünen bir başlık ayarlamalı ve sayfaya yerleştirmelisiniz.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Neden önemli*:  
* **Type** Word'e denetimin tıklanabilir bir düğme gibi davranacağını söyler.  
* **Caption** kullanıcının gördüğü metindir; bunu değiştirmek **set command button caption** (komut düğmesi başlığını ayarlama) yöntemidir.  
* **Left** ve **Top** tam konumu kontrol eder, bu da **add command button word** belgelerinde hassas yerleşim gerektiğinde kritiktir.

### Adım 5: Gömülü düğmeli belgeyi kaydetme

Son olarak, dosyayı diske yazın. Oluşan dosya Microsoft Word'de açılabilir ve düğme tam işlevsel olacaktır.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Neden önemli*: Bu adım **saves Word with button** (Word'ü düğmeli kaydeder) böylece denetim makineler arasında kalıcı olur. Dosya şablon olarak dağıtılabilir veya otomatik rapor üretim hatlarında kullanılabilir.

## Tam çalışan örnek

Aşağıdaki sınıfı tamamen `CommandButtonDemo.java` adlı bir dosyaya kopyalayın, `YOUR_DIRECTORY`'yi gerçek bir yol ile ayarlayın ve `mvn compile exec:java` ile çalıştırın.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Beklenen sonuç

`CommandButton.docx` dosyasını Microsoft Word'de açtığınızda:

* Belge, **Click Me** etiketiyle bir düğme dışında tamamen boştur.
* Düğmeye tıklamak, varsayılan Word davranışını gösterir (bir makro ekli değilse hiçbir şey yapmaz), bu da OLE denetiminin doğru şekilde gömüldüğünü doğrular.

## Yaygın sorular ve uç durumlar

| Soru | Cevap |
|----------|--------|
| **Düğme boyutunu değiştirebilir miyim?** | Evet. Boyutları puan cinsinden ayarlamak için `commandButton.setWidth(double)` ve `commandButton.setHeight(double)` kullanın. |
| **Düğmeye bir makro eklemem gerekirse ne olur?** | Düğme kendisi sadece bir OLE denetimidir. Belgeye bir VBA makrosunu manuel olarak ya da Aspose.Words `Document` API'sinin `addMacro` yardımcılarıyla eklemeniz gerekir. |
| **Düğme LibreOffice'de çalışır mı?** | LibreOffice sınırlı OLE denetimlerini destekler. Düğme görünür, ancak tıklama davranışı farklı olabilir. |
| **Birden fazla düğme nasıl eklenir?** | Adım 3‑4'ü yeni bir `Forms2OleControl` örneğiyle tekrarlayın. Çakışmayı önlemek için her düğme için `setLeft`/`setTop` değerlerini ayarlayın. |
| **Kod .NET ile uyumlu mu?** | Aynı mantık geçerlidir, ancak .NET sınıfları (`Document`, `DocumentBuilder`, `Forms2OleControl`) için `Aspose.Words` for .NET kullanırsınız. |

## Sahadan İpuçları

* **Pro tip:** Düğmeyi eklemeden önce `builder.moveToDocumentEnd()` kullanın; böylece belge içeriğine bakılmaksızın düğme belgenin tam sonuna yerleştirilir.
* **Watch out for:** Çok küçük `Left`/`Top` değerleri düğmeyi yazdırılabilir alanın dışına koyabilir, bu da Word'in düzen görünümünde görünmez olmasına neden olur.
* **Performance note:** Çok sayıda OLE denetimi eklemek dosya boyutunu artırabilir. Sadece görsel bir işaret gerekiyorsa, bunun yerine düz bir `Shape` ve bir hiperlink kullanmayı düşünün.

## Sonuç

Artık **boş bir DOCX dosyasını programlı olarak oluşturma** ve Java kullanarak tam işlevli bir komut düğmesi gömme konusunda bilgi sahibisiniz. Öğretici, tüm *create word document code* iş akışını kapsadı, **save Word with button** (Word'ü düğmeli kaydetme) nasıl yapılacağını gösterdi, **add command button word** öğelerinin doğru eklenişini gösterdi ve **set command button caption** (komut düğmesi başlığını ayarlama) nasıl yapılacağını açıkladı.

Buradan itibaren şunları yapabilirsiniz:

* Daha zengin formlar için daha fazla OLE denetimi (onay kutuları, açılır kutular) ekleyin.
* Düğmenin özel eylemler yapmasını sağlamak için VBA makroları ekleyin.
* Dinamik, etkileşimli şablonlar için bu tekniği belge posta birleştirme (mail‑merge) ile birleştirin.

İş gereksinimlerinize uygun düğme stilleri, konumları ve ek denetimler üzerinde denemeler yapmaktan çekinmeyin. Kodlamanın keyfini çıkarın

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Komut düğmesi ile boş Word belgesi oluşturma – adım adım rehber](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [Word'de ActiveX Düğmesi Ekleme – Düğme Başlığını Ayarlama](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Java ile Boş Word Belgesi Oluşturma – Tam Aspose.Words Rehberi](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}