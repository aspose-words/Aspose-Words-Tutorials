---
category: general
date: 2026-10-13
description: Aspose.Words for Java kullanarak Word’de form alanı düğmesi oluşturun.
  Komut düğmesi form alanlarını nasıl ekleyeceğinizi ve komut düğmesi başlığını birkaç
  kolay adımda nasıl ayarlayacağınızı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: tr
lastmod: 2026-10-13
og_description: Aspose.Words for Java ile Word’de form alanı düğmesi oluşturun. Bu
  öğreticide, komut düğmesi kelime alanlarını nasıl ekleyeceğinizi ve komut düğmesi
  başlığını hızlıca nasıl ayarlayacağınızı gösterir.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Word'de form alanı düğmesi oluşturma – Aspose.Words Java rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Aspose.Words Java ile Word'de form alanı düğmesi oluşturma
url: /tr/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Aspose.Words Java ile form alanı düğmesi oluşturma

Eğer bir Word belgesinde **form alanı düğmesi oluşturmanız** gerekiyorsa, bu rehber Aspose.Words for Java kullanarak sürecin tamamını adım adım gösterir. İster doldurulabilir bir form şablonu oluşturuyor olun, ister bir rapora etkileşimli denetimler ekliyor olun, **insert command button word** form alanlarını nasıl **set command button caption** işlemini minimal kodla yapacağınızı öğreneceksiniz.

Bu öğretici, Maven kurulumundan tamamen çalıştırılabilir bir örneğe kadar her şeyi kapsar; böylece kodu kopyalayıp yapıştırabilir, çalıştırabilir ve içinde tıklanabilir bir düğme bulunan bir `.docx` dosyasını görebilirsiniz.

## Önkoşullar

Başlamadan önce aşağıdakilerin kurulu olduğundan emin olun:

- Java 17 (veya daha yeni bir sürüm) makinenizde yüklü ve yapılandırılmış.
- Bağımlılık yönetimi için Maven 3.6+.
- Tercih ettiğiniz bir IDE veya metin düzenleyici (ör. IntelliJ IDEA, VS Code).
- Geçerli bir Aspose.Words for Java lisansı (ücretsiz deneme sürümü değerlendirme için çalışır).

## Adım 1: Aspose.Words'u Maven projenize ekleyin

`pom.xml` dosyanızı oluşturun (veya mevcut dosyayı düzenleyin) ve Aspose.Words bağımlılığını ekleyin:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Pro ipucu:** Sürüm numarasını güncel tutun. Yeni sürümler en son Word özelliklerini destekler ve performansı artırır.

## Adım 2: Boş bir belge ve bir `DocumentBuilder` başlatın

`DocumentBuilder` sınıfı, bir Word belgesini düzenlemek için akıcı bir API sağlar. Bu adımda boş bir `Document` oluşturur ve ona bir builder ekleriz.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Belge oluşturmak, öğreticide daha sonra **form alanı düğmesi oluşturma** nesnelerini eklemenin temelini oluşturur.

## Adım 3: Bir komut düğmesi form alanı ekleyin

Aspose.Words, OLE form denetimleri için `Forms2OleControl` sınıfını sunar. **insert command button word** form alanlarını eklemek için `COMMANDBUTTON` enum değerini kullanarak `insertForms2OleControl` metodunu çağırın.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Metod, kaydetmeden önce yapılandırabileceğimiz bir `Forms2OleControl` örneği döndürür.

## Adım 4: Düğmenin boyut ve konumunu tanımlayın

Bir komut düğmesinin sayfa üzerindeki kesin boyut ve konuma ihtiyacı vardır. Genişlik, yükseklik ve koordinatları düzenleyerek tasarımınıza uygun hale getirin.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Bu değerlerin ince ayarı, düğmenin nihai belgede tam istediğiniz yerde görünmesini sağlar.

## Adım 5: **Komut düğmesi başlığını ayarlayın**

Düğmenin üzerindeki görünen metin `setCaption` metodu ile kontrol edilir. İşte **set command button caption** işlemini gerçekleştirdiğimiz yer.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

`"Click Me"` ifadesini, formunuzun amacına uygun herhangi bir etiketle değiştirebilirsiniz; örneğin `"Submit"` veya `"Approve"`.

## Adım 6: Belgeyi kaydedin

Son olarak belgeyi diske yazın. Oluşan dosya etkileşimli düğmeyi içerir ve Microsoft Word ya da LibreOffice ile açılabilir.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Programı çalıştırdığınızda `CommandButtonDemo.docx` oluşturulur. Word'de açtığınızda düğmenin **Click Me** başlığıyla, sayfanın solundan 50 pt, üstünden 100 pt uzaklıkta konumlandığını görürsünüz.

### Beklenen çıktı

- `CommandButtonDemo.docx` adlı bir `.docx` dosyası.
- Belge, tek bir sayfada bir komut düğmesi form alanı içerir.
- Düğme, ayarladığınız başlığı (ör. **Click Me**) gösterir.

## Yaygın varyasyonlar ve kenar durumları

| Durum | Nasıl uyarlamalısınız |
|-----------|--------------|
| **Birden fazla düğme** | `insertForms2OleControl` metodunu tekrar tekrar çağırın, her yeni düğme için `setLeft`/`setTop` değerlerini ayarlayın. |
| **Düğme başlığı farklı olsun** | Her eklemeden sonra `setCaption` metodunu benzersiz bir dizeyle kullanın. |
| **Düğme bir tablo hücresinin içinde** | Kontrolü eklemeden önce `builder.moveTo(cell.getFirstParagraph())` ile imleci istenen hücreye taşıyın. |
| **Eski Word formatları (.doc)** | `doc.save("Demo.doc", SaveFormat.DOC);` ile kaydedin – komut düğmesi korunur. |
| **Salt okunur formlar** | Ekledikten sonra `commandButton.setEnabled(false);` ile kullanıcı etkileşimini engelleyin. |

## Sağlam bir uygulama için ipuçları

- **Boyutları doğrulayın**: Aşırı büyük genişlikler düğmenin sayfa kenarını aşmasına neden olabilir.
- **Lisans uygulaması**: Geçerli bir lisans olmadan Aspose.Words, oluşturulan belgeye bir filigran ekler. Lisansınızı erken uygulayın: `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Test etme**: Oluşturulan dosyayı Word'de açın ve **Design Mode** (Geliştirici → Design Mode) seçeneğini etkinleştirerek düğmenin özelliklerini inceleyin.

## Tam kaynak kodu özeti

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Kodu `InsertCommandButtonDemo.java` adlı bir dosyaya yapıştırın, Maven ile derleyin (`mvn compile`) ve çalıştırın (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). Oluşturulan belge projenizin kök klasöründe görünecektir.

## Sonuç

Artık Aspose.Words for Java kullanarak Word'de **form alanı düğmesi oluşturma**, **insert command button word** form alanlarını ekleme ve **set command button caption** işlemlerini programlı olarak yapabildiğinizi biliyorsunuz. Bu uçtan uca örnek, tek bir gönder düğmesi ya da tam bir form denetimi paketi ihtiyacınız olsun, daha zengin ve etkileşimli Word belgeleri oluşturmanız için sağlam bir temel sağlar.

### Sıradaki adımınız ne?

- `Forms2OleControlType.CHECKBOX` gibi onay kutuları ve `Forms2OleControlType.TEXTBOX` gibi metin kutuları gibi diğer form denetimlerini keşfedin.
- Kişiselleştirilmiş anketler üretmek için form alanlarını posta birleştirme (mail‑merge) ile birleştirin.
- Belge doldurulduktan sonra kullanıcı tarafından girilen verileri okumak için Aspose.Words `FormField` API'sini kullanın.

Farklı boyutlar, başlıklar ve konumlarla denemeler yapmaktan çekinmeyin. Komut düğmelerini ustalıkla kullandığınızda, Word otomasyon hatlarınızda tam özellikli formlar eklemek basit bir görev haline gelir. Kodlamanın tadını çıkarın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsamaktadır. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Aspose.Words for Java'da DocumentBuilder kullanarak form alanları oluşturma ve içerik ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for .NET ile bir Word belgesine Combo Box Form Field ekleme](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Aspose.Words for .NET ile bir Word belgesine Check Box Form Field ekleme](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}