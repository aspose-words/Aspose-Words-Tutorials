---
category: general
date: 2026-08-23
description: Java ve Aspose.Words kullanarak bir Word belgesine komut düğmesi eklemeyi
  öğrenin. Bu kılavuz, form denetimi eklemeyi, düğme adını ayarlamayı ve bir ActiveX
  düğmesi gömmeyi gösterir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: tr
lastmod: 2026-08-23
og_description: Java kullanarak bir Word belgesine komut düğmesi ekleyin. Form denetimi
  eklemek, düğme adını ayarlamak ve Aspose.Words ile bir ActiveX düğmesi gömmek için
  bu kılavuzu izleyin.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Java ile Word'e komut düğmesi ekleme – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Java kullanarak bir Word belgesine komut düğmesi nasıl eklenir
url: /tr/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java kullanarak bir Word belgesine komut düğmesi ekleme

Bir Word dosyasına **komut düğmesi eklemeniz** gerektiğinde, bu öğretici Aspose.Words for Java ile eksiksiz bir çözüm sunar. Form denetimi eklemeyi, başlığını yapılandırmayı ve düğme adını IDE'nizden çıkmadan ayarlamayı göreceksiniz.

Kılavuz, Microsoft Word'de kullanılmaya hazır bir ActiveX düğmesi içeren bir `.docx` oluşturmak için ihtiyacınız olan her şeyi kapsar. Ek bir araç gerektirmez ve örnek Java 8+ üzerinde çalışır.

## Öğrenecekleriniz

* Word belgesine **CommandButton** türünde form denetimi eklemeyi.  
* **set button name** ve **add activex button** özelliklerini ayarlamak için kesin adımları.  
* Belgeyi kaydetmeyi, böylece Word'de açıldığında düğmenin doğru şekilde görünmesini.  

Temel bir Java geliştirme ortamına ve Aspose.Words kütüphanesini içe aktarabilecek bir Maven veya Gradle projesine sahip olmalısınız.

## Önkoşullar

| Gereksinim | Sebep |
|-------------|--------|
| Java 8 veya daha yeni | Aspose.Words for Java, Java 8+ üzerinde çalışır. |
| Maven veya Gradle yapı aracı | Aspose.Words bağımlılığını eklemeyi basitleştirir. |
| Aspose.Words for Java lisansı (veya ücretsiz deneme) | Tam özellik seti için gereklidir; API değerlendirme modunda çalışır. |
| IntelliJ IDEA veya Eclipse gibi bir IDE | Örneği düzenlemeyi ve çalıştırmayı kolaylaştırır. |

## Adım 1: Aspose.Words'u projenize ekleyin

Maven kullanıyorsanız, aşağıdaki bağımlılığı `pom.xml` dosyasına ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Gradle için, bu satırı `build.gradle` dosyasına ekleyin:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Bağımlılık çözüldükten sonra, Java kaynak dosyanıza kütüphane sınıflarını içe aktarabilirsiniz.

## Adım 2: Komut düğmesini ekleyin – temel kod

`InsertCommandButtonDemo` adlı yeni bir Java sınıfı oluşturun. Aşağıdaki kod, **komut düğmesi eklemek** için gereken dört işlemi gerçekleştirir:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Her satırın önemi

* **Document & DocumentBuilder** – Word dosyasının bellek içi temsilini ve içeriğini değiştirmek için API'yi sağlar.  
* **insertForms2OleControl** – Bu yöntem `COMMAND_BUTTON` türünde **form control** ekler. Dönen `Forms2OleControl` nesnesi ActiveX denetimini temsil eder.  
* **setName** – Programatik bir tanımlayıcı (`btnSubmit`) atar. Word makroları veya VBA daha sonra bu adı referans alabilir.  
* **setCaption** – Kullanıcının düğmede gördüğü metni tanımlar, “düğme nasıl eklenir” sorusuna yanıt verir.  
* **save** – `.docx` dosyasını diske yazar, gömülü ActiveX düğmesini korur.  

Programı çalıştırmak, çalışma dizininde `CommandButtonDemo.docx` dosyasını oluşturur. Dosyayı Microsoft Word'de açtığınızda, **Submit** etiketiyle bir düğme gösterilir; üzerine tıkladığınızda değerlendirme modunda varsayılan bir ActiveX iletişim kutusu görüntülenir.

## Adım 3: Eklenen düğmeyi Word'de doğrulayın

1. `CommandButtonDemo.docx` dosyasını Microsoft Word (2016 veya daha yeni) ile açın.  
2. **Submit** düğmesi, ekleme sırasında imlecin konumlandığı yerde görünür.  
3. Düğmeye sağ tıklayın ve **Properties** (Özellikler) seçeneğini seçin; **Name** alanının `btnSubmit` içerdiğini göreceksiniz.  

Düğme görünmezse, Word'ün Trust Center ayarlarında **ActiveX controls** (ActiveX denetimleri) etkinleştirildiğinden emin olun.

## Adım 4: Düğmeyi özelleştirme (isteğe bağlı)

Düğmenin boyutunu, konumunu ayarlayarak veya bir VBA makrosu ekleyerek daha da özelleştirebilirsiniz. `Forms2OleControl` sınıfı `setWidth`, `setHeight` ve `setLeft` gibi ek özellikler sunar. Aşağıda düğmeyi daha büyük yapan bir örnek bulunmaktadır:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Bu satırlar `setCaption` çağrısından sonra yerleştirilebilir. Temel eklemenin ötesinde **add activex button** özelleştirmesini gösterir.

## Yaygın tuzaklar ve nasıl önlenir

| Belirti | Neden | Çözüm |
|---------|-------|------|
| Düğme Word'de görünmüyor | Kontrol eklenmeden belge kaydedildi | `insertForms2OleControl`'ün `doc.save`'den önce çağrıldığından emin olun. |
| Düğme başlığı boş | `setCaption` çağrılmadı veya boş bir dizeyle çağrıldı | Boş olmayan bir dize sağlayın, ör. `"Submit"`. |
| VBA düğmeyi bulamıyor | VBA kodu ile `setName` değeri arasında isim uyuşmazlığı | İsmi tutarlı tutun; `setName("btnSubmit")` kullanın ve VBA'da `btnSubmit`'i referans alın. |
| Dosya açılırken güvenlik uyarısı | Word'ün makro güvenliği ActiveX denetimlerini engelliyor | Trust Center > Macro Settings ayarlarını değiştirin veya belgeyi güvenilir bir sertifikayla imzalayın. |

## Tam, çalıştırılabilir örnek

Aşağıda, IDE'nize kopyala‑yapıştır yapmaya hazır tam kaynak dosyası yer almaktadır. İçe aktarma ifadeleri, istisna yönetimi ve her ana adımı açıklayan bir yorum bloğu içerir.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Beklenen sonuç:** Programı çalıştırdıktan sonra `CommandButtonDemo.docx` içinde tek bir **Submit** düğmesi bulunur. Dosyayı Word'de açtığınızda, düğme `DocumentBuilder` imlecinin bulunduğu konumda tam olarak gösterilir.

## Sonraki adımlar

* **Daha fazla form denetimi ekleyin** – Tam Word formları oluşturmak için `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` veya `TEXT_BOX` kullanın.  
* **Mail merge ile birleştirin** – Kişiselleştirilmiş etkileşimli formlar oluşturmak için birleştirilmiş belgeye düğmeler ekleyin.  
* **VBA makroları ekleyin** – Düğmenin `Click` olayına yanıt veren VBA'yı programlı olarak gömerek gelişmiş otomasyon sağlayın.  

Bu konular, yeni öğrendiğiniz **add form control** tekniğini doğal olarak genişletir.

---

### Özet

Artık Java kullanarak bir Word belgesine **komut düğmesi eklemeyi**, **form denetimi eklemeyi**, **düğme adını ayarlamayı** ve **activex düğmesi** özelleştirmelerini nasıl yapacağınızı biliyorsunuz. Tam örnek kutudan çıkar çıkmaz çalışır ve herhangi bir belge‑oluşturma iş akışına uyacak şekilde uyarlayabilirsiniz. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for Java'da DocumentBuilder kullanarak form alanları oluşturma ve içerik ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Word Belgesine Combo Box Form Alanı Ekleme](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Word Belgesine Check Box Form Alanı Ekleme](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}