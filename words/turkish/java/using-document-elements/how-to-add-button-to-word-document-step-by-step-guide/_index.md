---
category: general
date: 2026-07-20
description: Aspose.Words kullanarak Word belgesine nasıl düğme eklenir. DocumentBuilder
  ile Forms2OleControl düğmesini dakikalar içinde eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: tr
lastmod: 2026-07-20
og_description: Aspose.Words ile Word belgesine nasıl düğme eklenir. Java kullanarak
  Forms2OleControl CommandButton eklemek için bu pratik kılavuzu izleyin.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Word Belgesine Düğme Ekleme – Tam Aspose.Words Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Word Belgesine Düğme Ekleme – Adım Adım Kılavuz
url: /tr/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesine Düğme Ekleme – Tam Aspose.Words Öğreticisi

Hiç **Word belgesine nasıl düğme eklenir** sorusunu, UI’yı açmadan ve tıklamadan merak ettiniz mi? Tek başınıza değilsiniz. Birçok geliştirici, bir şablonda son kullanıcı tarafından doldurulacak bir “Gönder” düğmesi gibi etkileşimli kontrolleri programlı olarak eklemek zorunda. İyi haber? Aspose.Words for Java ile bunu sadece birkaç satır kodla yapabilirsiniz.

Bu öğreticide, `DocumentBuilder` kullanarak **CommandButton** tipinde bir `Forms2OleControl` eklemek için gereken adımları adım adım inceleyeceğiz. Sonunda, “Click Me” etiketiyle tıklanabilir bir düğme gösteren hazır bir `.docx` dosyanız olacak. Gizem yok, sadece net kod ve her satırın mantığı.

## Öğrenecekleriniz

- Sıfırdan yeni bir Word belgesi nasıl oluşturulur.
- **DocumentBuilder** kullanarak bir **Forms2OleControl** nasıl yerleştirilir.
- Düğme başlığını (caption) ve boyutunu neden bu şekilde ayarlamamız gerektiği.
- Sonucu nasıl kaydedip doğrularız.
- Yaygın tuzaklar (ör. eksik kütüphaneler, desteklenmeyen kontrol tipleri) ve bunlardan nasıl kaçınılır.

**Önkoşullar** – Java 8+ (veya daha yenisi) ve Aspose.Words for Java kütüphanesi (versiyon 23.12 veya sonrası) gerekir. IntelliJ IDEA veya Eclipse gibi bir IDE işleri kolaylaştırır, ancak herhangi bir metin düzenleyici de çalışır.

---

## 1. Adım: Projenizi Kurun ve Bağımlılıkları İçe Aktarın

Herhangi bir kod çalıştırılmadan önce, Maven (veya Gradle) Aspose.Words’u nereden çekeceğini bilmelidir. `pom.xml` dosyanıza aşağıdaki snippet’i ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Gradle tercih ediyorsanız eşdeğeri şudur:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro ipucu:** En son sürümü kullanın; eski sürümlerde `Forms2OleControl` API’si bulunmayabilir.

Bağımlılık çözüldükten sonra Java kodunu yazmaya hazırsınız.

---

## 2. Adım: Yeni Bir Belge Oluşturun ve DocumentBuilder’ı Edinin

`Document` sınıfı tüm `.docx` paketini temsil ederken, `DocumentBuilder` içeriği üzerine “boyamak” için kullandığınız fırçadır. `DocumentBuilder`ı, bir sonraki öğenin nereye yerleştirileceğini bilen bir “imleç” olarak düşünebilirsiniz.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Neden önemli?** Yeni bir `Document` başlatmak temiz bir tuval sağlar. Builder otomatik olarak ilk paragrafı işaret eder, böylece bölümleri veya sayfaları manuel olarak yönetmek zorunda kalmazsınız.

---

## 3. Adım: CommandButton Tipinde Bir Forms2OleControl Ekleyin

Şimdi gösterinin yıldızı: `insertForms2OleControl`. Bu metod, Word’un bir form öğesi olarak gördüğü bir OLE (Object Linking and Embedding) kontrolü oluşturur. Üç argüman geçeceğiz:

1. `Forms2OleControlType.COMMANDBUTTON` – Word’a bir düğme istediğimizi söyler.
2. `100` – genişlik (puan cinsinden, ≈1.39 inç).
3. `30` – yükseklik (puan cinsinden, ≈0.42 inç).

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**Nasıl çalışır?** Aspose.Words, `word/document.xml` kısmına uygun XML’i ekler ve OLE nesnesine referans verir. Sağladığınız boyutlar Word’ün yerleşim motoru tarafından saygı görür, böylece düğme builder’ın imlecinin bulunduğu konumda tam olarak görünür.

---

## 4. Adım: Düğmenin Başlığını (Metnini) Ayarlayın

Etiketsiz bir düğme kafa karıştırıcıdır—sessiz bir asansör düğmesi gibi. `setCaption` metodu görünür metni ayarlar:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

Başlığı istediğiniz gibi değiştirebilirsiniz: “Submit”, “Approve” ya da yerelleştirilmiş bir dize. Başlık OLE nesnesinin özelliklerinde saklanır, böylece Word bunu yerel olarak render eder.

---

## 5. Adım: Belgeyi Kaydedin ve Sonucu Doğrulayın

Son olarak dosyayı diske yazın. Yazma izniniz olan bir klasör seçin; aksi takdirde `IOException` alırsınız.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`button-demo.docx` dosyasını Microsoft Word’de açın. Belgenin üst kısmında **Click Me** etiketiyle bir düğme görmelisiniz. Word içinde ona tıkladığınızda varsayılan OLE davranışı (genellikle bir yer tutucu mesaj) tetiklenir; bir makro bağlamadıysanız.

---

## Yaygın Kenar Durumları ve Çözüm Yolları

| Durum | Neden Oluşur | Çözüm |
|-----------|----------------|-----|
| **Missing `Forms2OleControl` type** | Eski Aspose.Words sürümleri bu enum’u sağlamaz. | 23.12+ veya daha yeni bir sürüme yükseltin. |
| **Button appears as a picture** | Word’un güvenlik ayarları OLE kontrollerini engeller. | Trust Center’da “Trust access to the VBA project object model” seçeneğini etkinleştirin veya makro‑destekli bir `.docm` kullanın. |
| **Incorrect size** | Puan ile piksel karışıklığı. | 1 point = 1/72 inch olduğunu unutmayın. Sayıları buna göre ayarlayın. |
| **Saving throws `FileNotFoundException`** | Yol mevcut değil. | `doc.save`’den önce dizinin (`output/`) oluşturulduğundan emin olun. `new File("output").mkdirs();` kullanın. |

---

## Örneği Genişletmek: Birden Fazla Düğme veya Diğer Kontroller Eklemek

Birden fazla düğmeye ihtiyacınız varsa, `builder.moveTo` ya da `builder.writeln()` ile imleci hareket ettirip `insertForms2OleControl` metodunu tekrar çağırın.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

Ayrıca `Forms2OleControlType.COMMANDBUTTON` yerine uygun enum değerini (`CHECKBOX`, `COMBOBOX` vb.) değiştirerek **CheckBox**, **ComboBox** veya **ListBox** ekleyebilirsiniz. Aynı genişlik/yükseklik parametreleri geçerlidir.

---

## Bu Yaklaşımın Daha Büyük Word Otomasyon İş Akışlarına Uyumu

- **Şablon Oluşturma:** Alt aşamalı onay için “Approve” düğmesi içeren bir sözleşme şablonu oluşturun.
- **Raporlama:** Makro tetikleyen bir “Refresh Data” düğmesiyle günlük rapor üretin.
- **Form Dağıtımı:** Önceden doldurulmuş etkileşimli kontrollerle bir anket gönderin.

Bu senaryoların tümü, gösterdiğimiz **Word otomasyonu** yaklaşımından fayda sağlar. Kontrolleri programlı olarak gömerek manuel düzenlemeyi ortadan kaldırır ve insan hatasını azaltırsınız.

---

## Tam Kaynak Kodu (Kopyala‑Yapıştır Hazır)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Beklenen çıktı:** `output/button-demo.docx` dosyasını Microsoft Word’de açtığınızda, üstte dikey olarak istiflenmiş iki düğme—“Click Me” ve “Submit”—görürsünüz.

---

## Sonuç

**Word belgesine nasıl düğme eklenir** sorusunu Aspose.Words for Java ile adım adım yanıtladık. Boş bir `Document`’tan başlayıp **DocumentBuilder** ile **CommandButton** tipinde bir `Forms2OleControl` ekledik, dostça bir başlık ayarladık ve sonucu kaydettik. Bu yaklaşım birden fazla kontrol eklemek ve daha geniş **Word otomasyonu** hatlarına sorunsuzca entegre olmak için ölçeklenebilir.

Bir sonraki meydan okumaya hazır mısınız? Düğmeyi bir **CheckBox** ile değiştirin ya da `.docm` dosyasında kullanıcı tıkladığında bir makro çalıştırın. Aynı desen geçerli—sadece enum’u değiştirin ve başlığı ayarlayın.

Herhangi bir sorunla karşılaşırsanız, kütüphane sürümünüzü ve çıktı klasörü izinlerini yeniden kontrol edin. Sorularınızı aşağıya yorum olarak bırakmaktan veya kendi kullanım senaryolarınızı paylaşmaktan çekinmeyin. İyi kodlamalar!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak ilgili konuları kapsar. Her kaynak, tam çalışan kod örnekleri ve adım adım açıklamalar içerir; böylece ek API özelliklerini öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}