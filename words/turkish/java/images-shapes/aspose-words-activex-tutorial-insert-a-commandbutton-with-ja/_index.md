---
category: general
date: 2026-08-07
description: Aspose.Words ActiveX öğreticisi, Java kullanarak bir Word belgesine CommandButton
  kontrolü eklemeyi gösterir. Tam kodu, yapılandırmayı ve kaydetme adımlarını öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: tr
lastmod: 2026-08-07
og_description: Aspose.Words ActiveX öğreticisi, Java kullanarak bir Word belgesine
  CommandButton ActiveX denetimi nasıl yerleştirileceğini açıklar. Belgeyi oluşturmak,
  yapılandırmak ve kaydetmek için tam örneği izleyin.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Aspose.Words ActiveX öğreticisi – Java adım adım rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Aspose.Words ActiveX öğreticisi – Java ile bir CommandButton ekleme
url: /tr/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX öğreticisi – Java ile bir CommandButton ekleme

Eğer bir Word dosyasına ActiveX kontrolü yerleştirmeniz gerekiyorsa, bu **Aspose.Words ActiveX tutorial** size tüm süreci adım adım gösterir. Boş bir belge oluşturmayı, bir CommandButton eklemeyi, özelliklerini ayarlamayı ve sonucu kaydetmeyi—hepsi sade Java kodu ile—göreceksiniz.

Örnek, Aspose.Words for Java API'sini kullanır; bu sayede derleme sunucusunda Microsoft Office kurulu olmasına gerek kalmaz. Bu rehberin sonunda, Windows ortamlarında kullanılmaya hazır tam işlevsel CommandButton kontrolleri içeren .docx dosyaları oluşturabilirsiniz.

## Önkoşullar

- Java Development Kit (JDK) 8 veya daha yeni bir sürümünün kurulu olması.
- Bağımlılıkları yönetmek için Maven veya başka bir yapı aracı.
- Değerlendirme filigranlarından kaçınmak için bir Aspose.Words for Java lisansı (veya geçici değerlendirme anahtarı).
- Java sözdizimi ve nesne‑yönelimli programlama konusunda temel bilgi.

> **Pro ipucu:** IDE'nin sınıfları otomatik olarak çözebilmesi için `pom.xml` dosyanıza Aspose.Words Maven bağımlılığını ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Adım 1: Yeni bir boş belge ve bir `DocumentBuilder` oluşturma

`Document` sınıfı, Word dosyasını bellek içinde temsil ederken, `DocumentBuilder` belgeyi düzenlemek için akıcı bir API sunar. Her iki nesnenin de başlatılması, belgenin sonraki değişikliklere hazır olmasını sağlar.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Neden önemli:**  
`DocumentBuilder` mevcut imleç konumunu izler, böylece sonraki ekleme işlemleri—örneğin bir kontrol eklemek—tam istediğiniz yerde görünür.

## Adım 2: Bir CommandButton ActiveX kontrolü ekleme

Aspose.Words, ActiveX nesneleri için `Forms2OleControl` sınıfını sunar. `insertForms2OleControl` yöntemi, kontrol tipini `Forms2OleControlType` enum'ı aracılığıyla belirtmenizi gerektirir.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Açıklama:**  
Eklenen kontrol, belge Windows ortamında açıldığında Word tarafından tıklanabilir bir düğme olarak işlenen bir COM‑tabanlı nesnedir.

## Adım 3: Düğmenin özelliklerini yapılandırma

Ekleme işleminden sonra, düğmenin adını, başlığını, boyutunu ve konumunu ayarlayabilirsiniz. Bu özellikler, kontrolün Word içinde nasıl göründüğünü ve davrandığını etkiler.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Bu ayarların önemi:**  

- **Name** – VBA makrolarının kontrolü referans almasını sağlar (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Kullanıcıların tıkladığı görünen etiketi belirler.
- **Left / Top** – Sayfa kenar boşluklarına göre yerleşimi kontrol eder.
- **Width / Height** – Farklı ekran çözünürlüklerinde tutarlı bir görsel boyut sağlar.

## Adım 4: Belgeyi kaydetme

`save` metodunu çağırmak, bellek içindeki temsili fiziksel bir dosyaya yazar. Desteklenen herhangi bir formatı (`.docx`, `.doc`, `.pdf` vb.) seçebilirsiniz. Bu öğreticide yerel Word formatını koruyoruz.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Sonuç:**  
`ActiveXDemo.docx` dosyasını Microsoft Word'de açtığınızda, belirtilen koordinatlarda **Submit** etiketiyle bir CommandButton görüntülenir. Düğmeye tıklamak varsayılan davranışı tetikler (varsayılan olarak herhangi bir VBA kodu ekli değildir).

## Tam kaynak kodu

Parçaları bir araya getirdiğinizde, tam ve çalıştırılabilir program aşağıdaki gibi görünür:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Beklenen çıktı

- `output` klasöründe **ActiveXDemo.docx** adlı bir dosya.
- Microsoft Word (Windows) içinde açıldığında, belge tanımlı konumda tıklanabilir bir **Submit** düğmesi gösterir.
- Düğme, Word UI üzerinden (Geliştirici → Özellikler) seçilebilir, taşınabilir veya VBA koduna bağlanabilir.

## Yaygın varyasyonların ele alınması

| Senaryo | Ayarlama |
|----------|------------|
| **.doc olarak kaydet** (eski format) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Add an event handler** | Word, Aspose.Words aracılığıyla ActiveX olaylarını ortaya çıkarmaz. Belge oluşturulduktan sonra VBA kodunu manuel olarak eklemeniz gerekir. |
| **Multiple controls** | Farklı `setName` ve `setCaption` değerleriyle ekleme/konfigürasyon bloğunu tekrarlayın. |
| **Different control type (e.g., CheckBox)** | `insertForms2OleControl` çağrısında `Forms2OleControlType.CHECKBOX` kullanın. |
| **Non‑Windows platforms** | ActiveX kontrolleri yalnızca Windows Word'de görüntülenir. Çapraz platform çözümleri için içerik kontrollerini (`StructuredDocumentTag`) düşünün. |

## En iyi uygulamalar ve tuzaklar

- **Erken lisanslama** – Değerlendirme uyarılarını önlemek için `Document` oluşturulmadan önce Aspose.Words lisansınızı kaydedin.
- **Koordinat sistemi** – Pozisyonlar nokta biriminde ölçülür (1 pt = 1/72 in). UI tasarımınız bu birimleri kullanıyorsa piksel veya santimetreden dönüştürün.
- **Dosya yolları** – Çıktı dizini mevcut olmadığında `FileNotFoundException` hatasını önlemek için mutlak yollar veya Java’nın `Paths` API'sini kullanın.
- **İş parçacığı güvenliği** – `Document` ve `DocumentBuilder` iş parçacığı güvenli değildir. Paralel belge üretimi yapıyorsanız, her iş parçacığı için ayrı örnekler oluşturun.
- **Test** – Oluşturulan belgeyi hedef Word sürümünde (ör. Word 2016, Word 365) doğrulayın; çünkü eski sürümler ActiveX kontrollerini farklı gösterebilir.

## Sonuç

Bu **Aspose.Words ActiveX tutorial** Java kullanarak bir Word belgesine programlı olarak CommandButton kontrolü eklemenin nasıl yapılacağını gösterir. Şunları öğrendiniz:

1. `Document` ve `DocumentBuilder`'ı başlatma.
2. `COMMAND_BUTTON` tipinde bir `Forms2OleControl` ekleme.
3. Düğmenin adını, başlığını, boyutunu ve konumunu ayarlama.
4. ActiveX kontrolünü içeren .docx dosyası olarak belgeyi kaydetme.

Buradan, ek kontrol tiplerini keşfedebilir, VBA makro enjeksiyonunu otomatikleştirebilir veya ActiveX kontrollerini mail‑merge ve içerik kontrolleri gibi diğer Aspose.Words özellikleriyle birleştirebilirsiniz. Farklı düzenlerle denemeler yapın ve oluşturulan belgeleri daha büyük Java‑tabanlı raporlama hattınıza entegre edin.

---

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words for Java'da OLE Nesneleri ve ActiveX Kontrolleri Kullanma](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Aspose.Words for Java'da DocumentBuilder ile form alanları oluşturma ve içerik ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java Öğreticisi ile Word'ü RTF'ye Dönüştürme](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}