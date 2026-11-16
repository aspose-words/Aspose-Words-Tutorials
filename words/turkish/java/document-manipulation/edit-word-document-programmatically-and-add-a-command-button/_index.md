---
category: general
date: 2026-11-15
description: Word belgesini programlı olarak düzenleyerek bir komut düğmesi ekleyin.
  Düğmeyi nasıl ekleyeceğinizi, komut düğmesi adını nasıl ayarlayacağınızı ve Word’de
  form düğmesi oluşturmayı dakikalar içinde öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: tr
lastmod: 2026-11-15
og_description: Word belgesini programlı olarak düzenleyin ve bir komut düğmesi ekleyin.
  Bu kılavuz, düğme eklemeyi, komut düğmesi adını ayarlamayı ve Word’de form düğmesi
  oluşturmayı hızlı bir şekilde gösterir.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Word belgesini programlı olarak düzenle – bir komut düğmesi ekle
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Word belgesini programlı olarak düzenleyin ve bir komut düğmesi ekleyin
url: /tr/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word belgesini programlı olarak düzenleyin ve bir komut düğmesi ekleyin

Programlı olarak **Word belgesini düzenlemeniz** gerekiyorsa, en hızlı yol Aspose.Words API'sini kullanmaktır. Bu öğretici, **buton eklemenin** nasıl yapılacağını, denetimlerin başlığını yapılandırmayı ve **komut düğmesi adını ayarlamayı** tam olarak gösterir, böylece belge basit bir form olarak işlev görebilir. Sonunda, aşağı akış işlemleri için hazır işlevsel bir komut düğmesi içeren tamamen düzenlenebilir bir *.docx* dosyanız olacak.

**Komut düğmesi kelimesi eklemeyi**, **form düğmesi kelimesi oluşturmayı** ve Word'ü manuel olarak açmadan düğme özelliklerini yönetmeyi öğreneceksiniz. Tek ön koşul, temel bir Java geliştirme ortamı ve Aspose.Words for Java kütüphanesidir.

## Önkoşullar

- Java 17 veya daha yeni (kod Java 8+ ile de çalışır)
- Aspose.Words for Java (şuradan indirin [Aspose.Words for Java](https://products.aspose.com/words/java/))
- Değiştirmek istediğiniz mevcut bir Word belgesi (`input.docx`)
- Aspose.Words bağımlılığını eklemek için Maven veya Gradle konusunda aşinalık

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Adım 1: Word belgesini yükleyin

Programlı olarak **Word belgesini düzenlediğinizde** ilk işlem, kaynak dosyayı bir `Document` nesnesine yüklemektir. Bu nesne, tüm Word dosyasını bellekte temsil eder ve içeriğini manipüle etmenizi sağlar.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Neden önemli:** Belgeyi yüklemek, Aspose.Words'un dolaşabileceği ve değiştirebileceği bir DOM benzeri yapı oluşturur. Bu adımı atlamak, düğme ekleme için bir hedefiniz olmamasına yol açar.

## Adım 2: Belgeyi düzenlemek için bir `DocumentBuilder` oluşturun

`DocumentBuilder`, Word dosyası içinde bir imleç gibi davranır. Mevcut konumda metin, resim ve form denetimleri eklemenizi sağlar.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Tip:** Belirli bir paragrafta düğmeye ihtiyacınız varsa, önce `builder.moveToParagraph(index, true);` ile builder'ı taşıyın.

## Adım 3: Forms2OleControl (komut düğmesi) ekleyin

Şimdi, Word dosyasında **buton eklemenin** temel sorusuna yanıt veriyoruz. `insertForms2OleControl()` yöntemi, Word sürümleri arasında en uyumlu kontrol olan eski bir *Forms2.0* komut düğmesi oluşturur.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Köşe durumu:** Forms2.0 kontrolü yalnızca Word'ün *Design Mode* (Tasarım Modu) içinde görünür. Daha yeni bir ActiveX düğmesine ihtiyacınız varsa, bunun yerine `insertOleControl()`'ı düşünün, ancak eski kontrol çoğu otomasyon senaryosunda çalışır.

## Adım 4: Düğmenin özelliklerini yapılandırın

Kontrolü ekledikten sonra, **komut düğmesi adını ayarlayabilir** ve **komut düğmesi kelimesi ekleyebilirsiniz** (başlık) böylece kullanıcı dostu olur.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Neden bu özellikler?**  
> - `setName`, VBA veya dış araçların başvurabileceği bir tanımlayıcı verir.  
> - `setCaption` ise görünen etikettir, etkili bir şekilde **form düğmesi kelimesi oluşturur** ve son kullanıcılar tıklar.

Ayrıca, temel OLE nesnesine erişerek boyut, konum ayarlayabilir veya bir makro ekleyebilirsiniz, ancak bu konular bu hızlı kılavuzun kapsamı dışındadır.

## Adım 5: Değiştirilen belgeyi kaydedin

Son olarak, değişiklikleri yeni bir dosyaya kaydedin. Bu adım, çıktı belgesinde **form düğmesi kelimesi oluşturur**.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Sonuç:** `output.docx` dosyasını Microsoft Word'de açtığınızda, “Submit” etiketiyle bir düğme göreceksiniz. Word'ü *Design Mode* (Geliştirici → Tasarım Modu) içine geçirdiğinizde, düğmeye çift tıklayarak bir makro ekleyebilir veya sadece bir formda yer tutucu olarak kullanabilirsiniz.

### Beklenen çıktı

`output.docx` dosyasını açtığınızda:

- İmleç‑ekleme noktası bir düğme ile değiştirilir.
- Düğme **Submit** başlığını gösterir.
- Düğmenin iç adı **cmdSubmit**'dir ve VBA veya dış otomasyon betiklerinde başvurabilirsiniz.

## Sık sorulan sorular ve varyasyonlar

### Belirli bir paragrafta düğme nasıl eklenir?

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### Bir tablo hücresi içine düğme nasıl eklenir?

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### Daha büyük bir düğmeye ihtiyacım olsaydı ne olur?

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### **Komut düğmesi kelimesi** farklı bir dil (ör. C#) kullanarak nasıl eklenir?

Aynı mantık geçerlidir; Java sözdizimini C# eşdeğerleriyle değiştirin:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## Profesyonel ipuçları ve tuzaklar

- **Pro tip:** Düğmeyi belgenin en sonuna eklemek istiyorsanız, her zaman `builder.moveToDocumentEnd()` çağırın.  
- **Watch out for:** Açtığınız aynı dosyaya kaydetmek, bir istisna oluşursa belgeyi bozabilir. Gösterildiği gibi ayrı bir çıktı yolu kullanın.  
- **Compatibility:** Eski Forms2.0 düğmesi Word 2007‑2021'de çalışır. Web üzerindeki Word için içerik denetimlerini kullanmayı düşünün.  
- **Performance:** Çok büyük belgeleri (>100 MB) yüklemek önemli bellek tüketebilir. Kaynak kullanımını sınırlamak için `Document.load(InputStream, LoadOptions)` ile `LoadOptions.setLoadFormat(LoadFormat.DOCX)` kullanın.

## Tam çalışan örnek

Aşağıda, eksiksiz, çalıştırmaya hazır Java programı yer almaktadır. `WordButtonDemo.java` adlı bir sınıfa kopyalayın, dosya yollarını ayarlayın ve `mvn compile exec:java` komutunu çalıştırın.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Programı çalıştırın ve `output.docx` dosyasını açarak düğmenin beklendiği gibi göründüğünü doğrulayın.

## Sonuç

Artık Aspose.Words for Java kullanarak **Word belgesini programlı olarak düzenlemeyi**, **komut düğmesi kelimesi eklemeyi**, **form düğmesi kelimesi oluşturmayı** ve **komut düğmesi adını ayarlamayı** biliyorsunuz. Bu yaklaşım manuel düzenlemeyi ortadan kaldırır, formların toplu işlenmesini sağlar ve otomatik iş akışlarıyla sorunsuz bir şekilde bütünleşir.

Sonra, aşağıdakileri keşfedebilirsiniz:

- Düğmeye VBA makroları eklemek (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- **İçerik denetimlerini** daha zengin form deneyimleri için kullanmak (`builder.insertCheckBox()` vb.)  
- Bir döngü ile birden çok belgeye toplu ekleme otomasyonu  

Düğmenin boyutunu, konumunu ve olay işleyişini kendi senaryonuza göre denemekten çekinmeyin. İyi kodlamalar!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Word belgesine programlı olarak komut düğmesi ekleme](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Programlı olarak Word belgesi oluşturma ve ActiveX düğmesi ekleme](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Aspose.Words ile Word Belgesine Komut Düğmesi Ekleme – Tam Kılavuz](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}