---
category: general
date: 2026-09-18
description: Java'da boş bir belge oluşturun ve bir ActiveX düğmesi ekleyin. Komut
  düğmesi eklemeyi, etkileşimli bir form oluşturmayı ve bir Word belgesini kaydetmeyi
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: tr
lastmod: 2026-09-18
og_description: Java'da boş bir belge oluşturun ve bir ActiveX komut düğmesi yerleştirin.
  Etkileşimli bir form oluşturmak ve Word dosyasını kaydetmek için bu adım adım rehberi
  izleyin.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Word'de etkileşimli bir komut düğmesiyle boş belge oluştur
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Java kullanarak Word'de etkileşimli bir komut düğmesiyle boş belge oluştur
url: /tr/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java kullanarak Word'de etkileşimli bir komut düğmesiyle boş belge oluşturma

Eğer tıklanabilir bir düğme içeren **boş belge oluşturma** ihtiyacınız varsa, bu kılavuz size Aspose.Words for Java ile bunu tam olarak nasıl yapacağınızı gösterir. Etkileşimli bir form oluşturmayı, bir ActiveX düğmesi eklemeyi ve sonunda Word dosyasını kaydetmeyi öğreneceksiniz — birkaç özlü adımda.

Bir komut düğmesi eklemek, statik bir .docx dosyasını, son kullanıcıların doğrudan Microsoft Word içinde etkileşimde bulunabileceği işlevsel bir forma dönüştürür. Bu öğreticide ayrıca **komut düğmesinin nasıl ekleneceği**, yaygın hataların ele alınması ve çözümün daha karmaşık formlar için genişletilmesi ele alınmaktadır.

## Önkoşullar

* Java 17 veya daha yeni (kod JDK 17+ ile derlenir)
* Aspose.Words for Java 23.9 veya daha yeni – kütüphane `Document`, `DocumentBuilder` ve `Forms2OleControl` sağlar.
* Aspose.Words bağımlılığını ekleyebilen bir IDE veya derleme aracı (Maven/Gradle).
* Java sözdizimi ve Word belge kavramları hakkında temel bilgi.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Adım 1: Boş bir belge oluşturma

İlk işlem, yeni bir `Document` nesnesi örneklemektir. Bu nesne, içerik eklemeye hazır boş bir Word dosyasını temsil eder.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Boş bir belge oluşturmak size temiz bir tuval sağlar; bu, önceden var olan bir şablon olmadan programlı olarak **Word belgesi oluşturmak** istediğinizde çok önemlidir.

## Adım 2: DocumentBuilder'ı Başlatma

`DocumentBuilder`, metin, tablo ve form denetimleri eklemek için birincil sınıftır. Az önce oluşturduğunuz `Document` üzerinde çalışır.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder, mevcut ekleme noktasını korur, böylece sonraki komutlar dosyadaki doğru konumu etkiler.

## Adım 3: Forms2Ole komut düğmesi denetimi ekleme

Aspose.Words, ActiveX denetimleri için `Forms2OleControl` sınıfını sunar. **ActiveX düğmesi eklemek** için, builder'dan bir `COMMANDBUTTON` türü talep edersiniz.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

`insertForms2OleControl` yöntemi, denetimi builder'ın mevcut imleç konumuna ekler. Denetim bir ActiveX nesnesi olduğu için yalnızca Microsoft Word masaüstü sürümünde çalışır, Word Online'da çalışmaz.

## Adım 4: Düğmenin görünümünü ve konumunu yapılandırma

Denetimin ayarlayıcılarını kullanarak düğmenin başlığını, boyutunu ve konumunu ayarlayabilirsiniz. Konum değerleri point biriminde ölçülür (1 point = 1/72 inç).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Bu özellikleri neden yapılandırmalısınız?* `Top` ve `Left` ayarları, düğmenin sayfada beklediğiniz yerde görünmesini sağlar, `Caption` ise kullanıcıya görünen etiketi tanımlar. Genişlik/yüksekliği atlayarsanız, Word varsayılan boyutları atar ve bu tasarımınıza uymayabilir.

### Pro ipucu
Birden fazla denetim eklemeyi planlıyorsanız, nesnelerin çakışmasını önlemek için her eklemeden önce `builder.moveToDocumentEnd()` çağırın.

## Adım 5: Gömülü komut düğmesiyle belgeyi kaydetme

Son olarak, belgeyi diske yazın. ActiveX denetimini korumak için dosya uzantısı `.docx` (veya eski Word sürümleri için `.doc`) olmalıdır.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

`CommandButton.docx` dosyasını Microsoft Word'de açtığınızda, **Click Me** etiketli bir düğme göreceksiniz. Ona tıklamak, varsayılan ActiveX eylemini tetikler (varsayılan olarak hiçbir şey yapmaz). Daha sonra özel davranış tanımlamak için bir makro veya VBA betiği ekleyebilirsiniz.

## Mevcut bir forma komut düğmesi ekleme (isteğe bağlı)

Zaten metin alanları içeren bir formunuz varsa ve bir düğme içeren **etkileşimli form oluşturmak** istiyorsanız, şu ek adımları izleyin:

1. Mevcut belgeyi yükleyin: `Document doc = new Document("ExistingForm.docx");`
2. Builder'ı istediğiniz konuma taşıyın: `builder.moveToParagraph(5, 0); // 6. paragraf, ilk düğüm`
3. Düğmeyi Adım 3'te gösterildiği gibi ekleyin.
4. Düğmenin `Top`/`Left` değerlerini paragrafın düzenine göre ayarlayın.

Bu yaklaşım, tüm dosyayı yeniden oluşturmak zorunda kalmadan herhangi bir önceden hazırlanmış Word şablonunu ActiveX düğmesiyle zenginleştirmenizi sağlar.

## Kenar durumları ve sorun giderme

| Durum | Kontrol Edilecek | Önerilen Çözüm |
|-----------|---------------|-----------------|
| Düğme Word'de görünmüyor | Dosyayı Word'ün masaüstü sürümünde açtığınızdan emin olun (Word Online ActiveX'i kaldırır). | Dosyayı Word 2016+ masaüstü sürümünde açın. |
| Başlık kesiliyor | Düğme genişliğinin metni içerecek kadar büyük olduğunu doğrulayın. | `setWidth` değerini başlık sığana kadar artırın. |
| `IOException` hatası alınıyor | Çıktı dizininin var olduğunu ve yazma izninizin olduğunu doğrulayın. | Dizini oluşturun veya programı yükseltilmiş haklarla çalıştırın. |
| Birden fazla düğme üst üste geliyor | Builder'ın imleci önceki eklemeden sonra hareket etmemiş olabilir. | Her yeni denetim eklemeden önce `builder.moveToDocumentEnd()` çağırın. |

## Tam çalıştırılabilir örnek

Aşağıda, kopyalayıp derleyip çalıştırabileceğiniz eksiksiz, bağımsız bir Java programı bulunmaktadır. Bu program **boş belge oluşturma**, **ActiveX düğmesi ekleme** ve **Word belgesi kaydetme** işlemlerini tek bir akışta gösterir.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Beklenen çıktı**

```
Document created: CommandButton.docx
```

`CommandButton.docx` dosyasını açtığınızda, üstten ve soldan 100 pt uzaklıkta konumlandırılmış **Click Me** etiketli bir düğme içeren tek bir sayfa görürsünüz.

## Sonuç

Artık **boş belge oluşturma**, bir **ActiveX düğmesi** gömme ve sade bir Word dosyasını **etkileşimli forma** dönüştürme konusunda bilgi sahibisiniz. **Komut düğmesinin nasıl ekleneceğini** öğrenerek bu deseni onay kutuları, combo kutuları eklemek ya da hatta özel VBA‑tabanlı mantık eklemek için genişletebilirsiniz.

Sonraki adımda, aşağıdaki ilgili konuları keşfetmeyi düşünün:

* `builder.insertField` ile metin alanları içeren **etkileşimli form oluşturma**
* `builder.insertOleObject` ile bir VBA makrosu çalıştıran **ActiveX düğmesi ekleme**
* `Document(docTemplatePath)` kullanarak bir şablondan **Word belgesi oluşturma**
* Oluşturulan .docx dosyasını düğmeyi koruyarak PDF'ye dönüştürme (not: PDF düğmeyi statik bir görüntü olarak render eder).

Düğmenin boyutu, konumu ve başlığıyla UI tasarımınıza uygun şekilde denemeler yapmaktan çekinmeyin. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for Java'da DocumentBuilder kullanarak form alanları oluşturma ve içerik ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Word Belgesinde VBA Projesi Oluşturma](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Yeni Word Belgesi Oluşturma](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}