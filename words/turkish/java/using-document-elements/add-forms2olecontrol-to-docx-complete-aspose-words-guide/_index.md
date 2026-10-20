---
category: general
date: 2026-07-23
description: Aspose.Words kullanarak DOCX'e Forms2OleControl eklemeyi öğrenin. Bu
  adım adım kılavuz, Java'da bir ActiveX CommandButton kontrolünün eklenmesini gösterir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add forms2olecontrol to docx
- insert ActiveX control in DOCX
- Aspose.Words Forms2OleControl example
- embed CommandButton in Word document
- Java DocumentBuilder ActiveX
language: tr
lastmod: 2026-07-23
og_description: Forms2OleControl'i DOCX'e anında ekleyin. Aspose.Words for Java kullanarak
  bir ActiveX CommandButton gömmek için bu pratik rehberi izleyin.
og_image_alt: Screenshot of Java code that adds Forms2OleControl to DOCX using Aspose.Words
og_title: Forms2OleControl'u DOCX'e Ekle – Tam Aspose.Words Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  headline: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  name: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  steps:
  - name: Using a Different ActiveX Control
    text: 'If you want a checkbox instead of a button, just change the control type:'
  - name: Embedding Multiple Controls
    text: Call `builder.insertForms2OleControl()` multiple times, moving the cursor
      with `builder.moveTo()` or inserting text between calls. Each call adds a new
      OLE container, so you can build complex forms inside a single DOCX.
  - name: Working with .NET
    text: The same logic applies to C#—the method names are identical (`DocumentBuilder.InsertForms2OleControl()`).
      If you’re on .NET, replace the Java syntax with its C# counterpart, but the
      **embed CommandButton in Word document** concept stays unchanged.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Java
- DOCX
title: DOCX'e Forms2OleControl Ekle – Tam Aspose.Words Rehberi
url: /tr/java/using-document-elements/add-forms2olecontrol-to-docx-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX'e Forms2OleControl Ekleme – Tam Aspose.Words Rehberi

Saçlarınızı çekmeden **add Forms2OleControl to DOCX** nasıl yapılır diye hiç merak ettiniz mi? Tek başınıza değilsiniz. Şablon‑tabanlı bir rapor oluşturuyor olun ya da bir Word dosyası içinde tıklanabilir bir düğmeye ihtiyacınız olsun, ActiveX kontrolü gömmek gizli sosdur.

Bu öğreticide, Aspose.Words for Java ile **adds Forms2OleControl to DOCX** yapan somut bir örnek üzerinden ilerleyeceğiz. Tam kodu görecek, her satırın neden önemli olduğunu anlayacak ve geliştiricileri sık sık zorlayan tuhaflıklarla başa çıkmak için ipuçları alacaksınız.

## Öğrenecekleriniz

- Java projesinde Aspose.Words nasıl kurulur  
- DOCX içinde **insert an ActiveX control in DOCX** için tam adımlar (evet, ana anahtar kelime yine)  
- CommandButton özelliklerini gerçek bir UI öğesi gibi davranacak şekilde yapılandırma  
- Belgeyi kaydetme ve kontrolün gerçekten gömülü olduğunu doğrulama  

ActiveX ile ilgili önceden bir deneyim gerekli değil, ancak Java ve Maven/Gradle temel bilgisi yolculuğu daha sorunsuz hale getirecektir. Hazır mısınız? Hadi başlayalım.

---

## Adım 1: Projenizde Aspose.Words'ı Kurun

**add Forms2OleControl to DOCX** yapmadan önce, classpath'te Aspose.Words kütüphanesine ihtiyacınız var. En kolay yol Maven üzerinden:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

> **Pro tip:** Gradle kullanıyorsanız, eşdeğeri `implementation 'com.aspose:aspose-words:24.9'`.

Neden önemli: Aspose.Words, **insert an ActiveX control in DOCX** için güveneceğimiz `DocumentBuilder.insertForms2OleControl()` metodunu sağlar. Kütüphane olmadan, derleyici `Forms2OleControl`'ün ne olduğunu bilemez.

## Adım 2: DOCX'e Forms2OleControl Ekleme

Şimdi öğretinin çekirdeği geliyor—tam olarak **add Forms2OleControl to DOCX** yaptığımız yer. Yeni bir belge oluşturacağız, bir `DocumentBuilder` başlatacağız ve ekleme metodunu çağıracağız.

```java
import com.aspose.words.*;

public class ActiveXExample {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2.2: Insert an ActiveX Forms2OleControl (CommandButton)
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Step 2.3: Configure the CommandButton properties
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setName("MyButton");
        commandButton.setCaption("Click Me");

        // Step 2.4: Save the document with the embedded control
        String outPath = "output/ActiveXButton.docx";
        document.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Burada ne oluyor?**  

- `new Document()` bize temiz bir tuval verir. Bunu, **insert ActiveX control in DOCX** için hazır bir temiz kağıt gibi düşünün.  
- `builder.insertForms2OleControl()` Aspose.Words'un *Forms2OleControl* dediği düşük seviyeli OLE konteynerini oluşturur. Bu, gerçekten **adds Forms2OleControl to DOCX** yapan tek API çağrısıdır.  
- `OleControlType.COMMANDBUTTON` ayarlamak, OLE nesnesinin klasik bir CommandButton gibi davranmasını Word'e söyler—tam olarak UI tasarımcısında bir forma sürüklediğiniz düğme gibi.  
- Son olarak, `document.save(...)` .docx dosyasını yazar, gömülü ActiveX'i kalıcı hale getirir.

## Adım 3: CommandButton Özelliklerini Yapılandırma (Neden Önemli)

Kontrolü sadece eklemek boş bir yer tutucu verir. Faydalı olması için birkaç özelliği ayarlamanız gerekir:

| Özellik | Amaç | Tipik Değer |
|----------|---------|---------------|
| `setOleControlType` | ActiveX kontrolünün tipini tanımlar (Button, CheckBox, vb.) | `OleControlType.COMMANDBUTTON` |
| `setName` | Word makroları veya VBA betikleri tarafından kullanılan iç kimlik | `"MyButton"` |
| `setCaption` | Düğme yüzeyinde gösterilen metin | `"Click Me"` |

Bunları atlayarsanız, düğme genel bir isim ve etiket olmadan görünür—kullanıcının tıklayacağı bir şey olmaz. Ayrıca, ActiveX kontrollerinin **platform‑specific** olduğunu unutmayın; sadece uygun COM kütüphanelerine sahip Windows makinelerinde çalışırlar.  

> **Dikkat:** Oluşturulan DOCX'i Windows dışı bir platformda (ör. macOS) açtığınızda, Word gerçek bir düğme yerine bir yer tutucu resim gösterir. Bu, ActiveX'in normal bir sınırlamasıdır, kodunuzdaki bir hata değildir.

## Adım 4: Belgeyi Kaydetme ve Doğrulama

`document.save(...)` çağrısı, modern bir Microsoft Word sürümünün açabileceği standart bir DOCX dosyası yazar. Programı çalıştırdıktan sonra `ActiveXButton.docx` dosyasını açın:

1. Eklediğiniz yerde “Click Me” düğmesini bulun.  
2. Düğmeye sağ‑tıklayın → **Properties** (Özellikler) ile isim ve başlığı doğrulayın.  
3. Düğmeye tıklayın; bir makro eklediyseniz Word basit bir ileti kutusu gösterir (bu kılavuzun kapsamı dışında).  

Düğme eksikse, **Aspose.Words Forms2OleControl example**'ı doğru kullandığınızdan ve çıktı klasörünün var olduğundan emin olun.  

> **Köşe durumu:** Düğmenin bir makroyu tetiklemesi gerekiyorsa, belge kaydedildikten sonra VBA kodu eklemeniz gerekir. Aspose.Words, `Document.getBuiltInDocumentProperties()` API'siyle VBA enjekte edebilir, ancak bu ayrı bir öğreticidir.

## Yaygın Varyasyonlar ve Tuzaklar

### Farklı Bir ActiveX Kontrolü Kullanma
Bir düğme yerine onay kutusu istiyorsanız, sadece kontrol tipini değiştirin:

```java
commandButton.setOleControlType(OleControlType.CHECKBOX);
commandButton.setCaption("Accept Terms");
```

### Birden Çok Kontrol Gömme
`builder.insertForms2OleControl()` metodunu birden çok kez çağırın, imleci `builder.moveTo()` ile hareket ettirin veya çağrılar arasında metin ekleyin. Her çağrı yeni bir OLE konteyneri ekler, böylece tek bir DOCX içinde karmaşık formlar oluşturabilirsiniz.

### .NET ile Çalışma
Aynı mantık C#'a da uygulanır—metod isimleri aynı (`DocumentBuilder.InsertForms2OleControl()`). .NET üzerindeyseniz, Java sözdizimini C# karşılığıyla değiştirin, ancak **embed CommandButton in Word document** kavramı değişmez kalır.

## Sonuç

Artık Aspose.Words for Java kullanarak **adds Forms2OleControl to DOCX** yapan çalışan, uçtan uca bir örneğiniz var. Boş bir belge oluşturup, ActiveX kontrolünü ekleyip, özelliklerini yapılandırıp dosyayı kaydederek **insert ActiveX control in DOCX**'i başarıyla yaptınız ve bu deseni diğer kontrol tiplerine de genişletebilirsiniz.

Sırada ne var? Bu tekniği Aspose.Words mail‑merge ile birleştirip kişiselleştirilmiş formlar oluşturmayı deneyin ya da düğmenin gerçekten bir şeyler yapması için VBA makroları eklemeyi keşfedin. **Aspose.Words Forms2OleControl example** kodunu kendi iş mantığınızla birleştirdiğinizde sınır yoktur.

Kodlamaktan keyif alın, ve herhangi bir sorunla karşılaşırsanız yorum bırakmaktan çekinmeyin!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere yakın konuları kapsar ve kendi projelerinizde alternatif uygulama yaklaşımları keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Aspose.Words for Java'da DocumentBuilder kullanarak form alanları oluşturma ve içerik ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java ile Word'e Yer İmleri Ekleme – Ekle, Güncelle, Sil](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)
- [Aspose.Words for Java Kullanarak Belgelere Filigran Ekleme](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}