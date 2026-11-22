---
category: general
date: 2026-11-22
description: Java kullanarak bir Word belgesine makro düğmesi oluşturun. Komut düğmesi
  eklemeyi, düğme metnini ayarlamayı ve etkileşimli belgeler için makroyu düğmeye
  bağlamayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: tr
lastmod: 2026-11-22
og_description: Java kullanarak bir Word belgesine makro düğmesi oluşturun. Bu öğreticide
  komut düğmesi ekleme, düğme metnini ayarlama ve tam etkileşim için makroyu düğmeye
  bağlama gösterilmektedir.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Java ile bir Word belgesine makro düğmesi oluşturma – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Aspose.Words for Java ile bir Word belgesinde makro düğmesi nasıl oluşturulur
url: /tr/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile bir Word belgesinde macro button oluşturma

Bir Word dosyasında **macro button** oluşturmanız gerekiyorsa, bu rehber size gereken adımları adım adım gösterir. **Insert command button**, **set button text** ve **link macro to button** nasıl yapılacağını öğrenecek ve belge tam anlamıyla etkileşimli hale gelecektir.

Geliştiriciler genellikle bir belge içinde VBA makrolarını tetiklemek için OLE kontrolleri ekler. Bu öğretici, proje kurulumundan .docx dosyasına **interactive button** ekleyen çalıştırılabilir bir Java örneğine kadar tam süreci kapsar. Harici betiklere gerek yok—her şey Java süreci içinde çalışır.

## Önkoşullar

* JDK 17 veya daha yeni bir sürüm yüklü.  
* Bağımlılık yönetimi için Maven 3.8+ (veya Gradle).  
* Aspose.Words for Java 23.9 veya daha yeni – kütüphane `DocumentBuilder` ve OLE kontrol API'lerini sağlar.  
* Java ve VBA makroları hakkında temel bilgi.

Eğer bu öğelerden herhangi biri eksikse, önce onları kurun; öğreticinin geri kalanı bunların mevcut olduğunu varsayar.

## Aspose.Words for Java ile macro button oluşturma

Çözümün temeli dört eylemden oluşur:

1. **Insert command button** OLE kontrolünü belgeye ekleyin.  
2. Kullanıcının gördüğü **Set button text** (başlık) ayarlayın.  
3. Tıklanınca istenen VBA rutinini çalıştırmak için **Link macro to button** bağlayın.  
4. Gömülü makro ile **Save the document** yapın.

Her eylem aşağıda kendi bölümünde açıklanmıştır.

### Adım 1: Belgeye command button ekleme

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Why this matters:** OLE kontrolü makro için bir kapsayıcı görevi görür. Bunu eklemezseniz, kullanıcının tıklayabileceği görsel bir öğe olmaz.

### Adım 2: Buton metnini (başlık) ayarlama

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Why this matters:** Açık buton metni kullanılabilirliği artırır. `setCaption` yöntemi OLE kontrolünün `Caption` özelliğini günceller; Word bu özelliği buton etiketi olarak gösterir.

### Adım 3: Makroyu butona bağlama

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Why this matters:** Bir makroyu bağlamak etkileşimli davranışı oluşturur. Kullanıcı Word'de butona tıkladığında ilişkili VBA rutini çalışır.

### Adım 4: Word belgesine etkileşimli bir buton ekleme

OLE kontrolünü yapılandırdıktan sonra, konumlandırmak, yeniden boyutlandırmak veya çevresine metin eklemek isteyebilirsiniz. `DocumentBuilder` belge üzerinde işlem yapmaya devam eder; bu sayede butondan önce veya sonra paragraflar ekleyebilirsiniz.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Why this matters:** `.docm` olarak kaydetmek makro kodunu korur. `.docx` olarak kaydederseniz, makro referansı kaybolur.

## Tam çalıştırılabilir örnek

Aşağıda, import'ları, istisna yönetimini ve her adımı açıklayan yorumları içeren tam Java programı yer almaktadır. Kodu Aspose.Words bağımlılığı olan bir Maven projesine kopyalayın ve çalıştırın.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Beklenen çıktı

Programı çalıştırmak `MacroButtonDemo.docm` dosyasını oluşturur. Dosyayı Microsoft Word'de açtığınızda şunlar görülür:

* *“Press the button to execute the macro:”* metnini içeren bir paragraf.  
* Paragrafın hemen altında **Run Report** etiketiyle bir buton.  
* Butona tıkladığınızda Word, `MyMacro` makrosunu çalıştırmaya çalışır. (Gerçek VBA kodunu belgeye manuel olarak ya da başka bir otomasyon adımıyla eklemeniz gerekir.)

Makro mevcut değilse, Word bir güvenlik uyarısı gösterir; bu, makro‑etkin belgeler için standart bir davranıştır.

## Yaygın varyasyonlar ve kenar durumları

| Senaryo | Kodu nasıl uyarlarsınız |
|----------|-----------------------|
| **Farklı buton başlığı** | `setCaption`'a geçirilen dizeyi değiştirin. |
| **Birden fazla buton** | `insertForms2OleControl`'ı tekrarlayarak çağırın, her biri kendi `setCaption` ve `setOnClick` değerlerine sahip olsun. |
| **Özel makro adları** | `"MyMacro"` ifadesini geçerli bir VBA prosedür adıyla, örneğin `"ExportToExcel"` ile değiştirin. |
| **Buton boyut kısıtlamaları** | `setWidth` ve `setHeight` değerlerini ayarlayın; Word sağladığınız puanları dikkate alır. |
| **Makroyu programlı olarak gömme** | `Document.getBuiltInDocumentProperties().add("Macros", …)` kullanın veya ayrı bir VBA enjeksiyon adımı uygulayın; Aspose.Words kendisi VBA kodu yazmaz. |

**Pro tip:** Geliştirme aşamasında, oluşturulan `.docm` dosyasını makro güvenliği *Enable all macros* (tüm makroları etkinleştir) olarak ayarlanmış bir makinede her zaman test edin. Üretimde, güvenlik uyarılarını önlemek için makroyu güvenilir bir sertifika ile imzalayın.

## Sorun giderme kontrol listesi

* **Button does not appear** – Belgenin `.docm` olarak kaydedildiğini ve OLE kontrollerini destekleyen bir Word sürümünde açıldığını doğrulayın.  
* **Macro does not run** – Makro adının büyük/küçük harf duyarlılığı dahil tam olarak eşleştiğinden ve makronun belgenin VBA projesinde mevcut olduğundan emin olun.  
* **Button caption is truncated** – Daha uzun metin için `setWidth` kullanarak buton genişliğini artırın.  
* **Unexpected layout shift** – Kontrolü eklemeden önce imleci tam olarak konumlandırmak için `builder.moveTo` kullanın.

## Sonuç

Artık Java kullanarak bir Word belgesinde **macro button** oluşturmayı, **insert command button**, **set button text** ve **link macro to button** işlemlerini tam etkileşim için nasıl yapacağınızı biliyorsunuz. Tam örnek, gerekli tüm API çağrılarını gösterir, her adımın neden önemli olduğunu açıklar ve yaygın varyasyonlar için rehberlik sağlar.

Sonrasında şunları keşfedebilirsiniz:

* **Add interactive button** yeni bir belge yerine mevcut şablonlara ekleyin.  
* **Programmatically inject VBA code** Open XML SDK veya ikinci bir otomasyon aracı kullanarak ekleyin.  
* **Combine multiple OLE controls** (checkboxes, list boxes) kullanarak zengin formlar oluşturun.

Farklı başlıklar, makro adları ve buton boyutlarıyla deneyler yaparak kendi kullanım senaryonuza uyarlayın. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Java kullanarak bir Word belgesine command button ekleme](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [Java ile bir Word belgesinde buton konumunu ayarlama](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [Word'de ActiveX Button ekleme – Buton Başlığını Ayarlama](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}