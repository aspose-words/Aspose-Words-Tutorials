---
date: '2026-08-10'
description: Aspose Words Maven dependency eklemeyi ve Aspose.Words for Java kullanarak
  master document manipulation'ı öğrenin, page backgrounds ve node import dahil.
keywords:
- aspose words maven dependency
- set page background color
- customize import format
- add shape as background
- apply background color
lastmod: '2026-08-10'
og_description: Aspose Words Maven dependency ekleyin ve Java'da master document manipulation
  yapın, page background color ayarlama ve nodes import etme dahil.
og_image_alt: Guide showing Aspose Words Maven setup and document background customization
  in Java
og_title: Aspose Words Maven Dependency – Java belge manipülasyonu rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Learn how to add the Aspose Words Maven dependency and master document
    manipulation using Aspose.Words for Java, including page backgrounds and node
    import.
  headline: Aspose Words Maven Dependency – Java document manipulation
  type: TechArticle
- description: Learn how to add the Aspose Words Maven dependency and master document
    manipulation using Aspose.Words for Java, including page backgrounds and node
    import.
  name: Aspose Words Maven Dependency – Java document manipulation
  steps:
  - name: '**Free trial** – Register on the Aspose website for a 30‑day trial key.'
    text: '**Free trial** – Register on the Aspose website for a 30‑day trial key.'
  - name: '**Temporary license** – Use the trial key to generate a temporary license
      file for full‑feature evaluation.'
    text: '**Temporary license** – Use the trial key to generate a temporary license
      file for full‑feature evaluation.'
  - name: '**Purchase** – Buy a perpetual license to remove evaluation limits and
      receive priority support.'
    text: '**Purchase** – Buy a perpetual license to remove evaluation limits and
      receive priority support.'
  type: HowTo
- questions:
  - answer: No. The `aspose-words` artifact includes built‑in support for PDF, DOCX,
      HTML, and over 30 other formats.
    question: Do I need a separate Maven artifact for PDF support?
  - answer: Yes, load the saved file, call `setPageColor()` again, and re‑save; the
      operation is fast because Aspose.Words works directly on the file stream.
    question: Can I change the background color after the document is saved?
  - answer: The library can process multi‑hundred‑page files (up to 10,000 pages)
      using streaming APIs that keep memory consumption under 200 MB.
    question: How large a document can Aspose.Words handle?
  - answer: Footnotes are stored in the main document’s `Footnotes` collection; `GlossaryDocument`
      is optional and only needed for separate glossary sections.
    question: Is the `GlossaryDocument` required for footnotes?
  - answer: Yes, Aspose.Words 25.3+ is fully compatible with Java 8, 11, 17, and newer
      LTS releases.
    question: Does the library support Java 17?
  type: FAQPage
tags:
- aspose words
- maven dependency
- java document manipulation
- page background
- import nodes
title: Aspose Words Maven Dependency – Java belge manipülasyonu
url: /tr/java/content-management/aspose-words-java-document-manipulation-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Words Maven bağımlılığı – Java belge işleme

Bu öğreticide, **aspose words maven dependency**'yi bir Java projesine nasıl ekleyeceğinizi ve ardından Aspose.Words for Java'ı belgeleri işlemek için—belgeleri başlatma, sayfa arka plan renklerini ayarlama, düğümleri içe aktarma ve şekilleri arka plan olarak ekleme—nasıl kullanacağınızı öğreneceksiniz. Sonunda, Microsoft Word yüklü olmadan zengin biçimlendirilmiş belgeler oluşturabilen üretim‑hazır bir kod tabanına sahip olacaksınız.

## Hızlı cevaplar
- **Aspose.Words'u ekleyen Maven artefaktı hangisidir?** `com.aspose:aspose-words` en son sürüm numarası ile.  
- **Sayfa arka plan rengini ayarlayabilir miyim?** Evet, herhangi bir `java.awt.Color` ile `Document.setPageColor()` metodunu çağırın.  
- **Belgeler arasında bir bölümü içe aktarmak güvenli mi?** `importNode()`, uygun `ImportFormatMode` ile kullanıldığında yapı ve stilleri korur.  
- **Şekiller sayfa arka planı olarak çalışır mı?** `ShapeType.IMAGE` tipinde bir `Shape` ekleyebilir ve bunu arka plan olarak işlev görmesi için üstbilgi/altbilgiye gönderebilirsiniz.  
- **Hangi Java sürümü gereklidir?** JDK 8 veya üzeri; kütüphane Java 11, 17 ve daha yeni LTS sürümleriyle uyumludur.

## Aspose Words Maven bağımlılığı nedir?
**aspose words maven dependency**, Aspose.Words for Java kütüphanesini ve tüm geçişli bağımlılıklarını projenizin sınıf yoluna çeken Maven koordinatıdır. `pom.xml` dosyasına bu tek satırı eklemek, 35'ten fazla giriş ve çıkış formatına erişim sağlar ve herhangi bir JVM üzerinde yüksek performanslı belge üretimini etkinleştirir.

## Aspose.Words for Java neden kullanılmalı?
Aspose.Words, **35+** belge formatını—DOCX, PDF, HTML ve EPUB dahil—işler ve tüm belgeyi belleğe yüklemeden **500 sayfaya** kadar dosyaları yönetir. Bu performans‑öncelikli tasarım, yerel Office otomasyonu ile karşılaştırıldığında sunucu RAM kullanımını **%70** kadar azaltır ve bulut‑yerel mikro hizmetler için ideal hâle getirir.

## Önkoşullar

- **Aspose.Words for Java** sürüm 25.3 veya üzeri (en son stabil sürüm önerilir).  
- Java Development Kit (JDK) 8+ makinenizde kurulu olmalı.  
- Projeyi düzenlemek ve derlemek için IntelliJ IDEA veya Eclipse gibi bir IDE.  
- Bağımlılık yönetimi için Maven veya Gradle.  

### Gerekli kütüphaneler ve sürümler
- `com.aspose:aspose-words:25.3` (veya daha yeni).  

### Bilgi önkoşulları
- Temel Java sözdizimi ve nesne‑yönelimli kavramlara aşina olmak.  
- Maven/Gradle yapı dosyalarının anlaşılması.

Önkoşullar karşılandığında, Maven bağımlılığını eklemeye ve kodlamaya hazırsınız.

## Aspose.Words kurulumu

Aspose.Words'u Java projenize entegre etmek için, kütüphaneyi bir Maven veya Gradle bağımlılığı olarak ekleyin.

### Maven
Bu snippet'i `pom.xml` dosyanıza ekleyin:
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle
Aşağıdakini `build.gradle` dosyanıza ekleyin:
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Lisans edinme adımları
1. **Ücretsiz deneme** – Aspose web sitesinde 30‑günlük deneme anahtarı için kaydolun.  
2. **Geçici lisans** – Deneme anahtarını tam özellikli değerlendirme için geçici bir lisans dosyası oluşturmak üzere kullanın.  
3. **Satın alma** – Değerlendirme sınırlamalarını kaldırmak ve öncelikli destek almak için kalıcı bir lisans satın alın.

### Temel başlatma ve kurulum

`Document` sınıfı, bir PDF, Word veya desteklenen herhangi bir dosyayı bellekte temsil eden temel nesnedir. Maven bağımlılığını ekledikten sonra, aşağıdaki gibi örnekleyebilirsiniz:
```java
import com.aspose.words.Document;

public class DocumentSetup {
    public static void main(String[] args) throws Exception {
        // Initialize a new document
        Document doc = new Document();
        
        System.out.println("Document initialized successfully!");
    }
}
```

Aspose.Words kurulduğunda, belge işleme için ihtiyaç duyacağınız belirli özellikleri keşfedelim.

## Uygulama rehberi

### Özellik 1: belge başlatma

#### Genel bakış
Belgeleri ve alt sınıflarını başlatmak, sözlükler, dipnotlar veya özel bölümler gibi karmaşık şablonlar oluşturmanıza olanak tanır.

#### Bir sözlük belgesi nasıl başlatılır?
Ana bir `Document` örneği oluşturun, ardından sözlük girişlerini tek, bütünleşik bir dosyada yönetmek için bir `GlossaryDocument` ekleyin. `GlossaryDocument`, bir Word belgesinin sözlük kısmını temsil eder ve sözlük öğeleri, dipnotlar ve özel bölümler gibi girişleri depolar.

```java
import com.aspose.words.Document;
import com.aspose.words.GlossaryDocument;

public class DocumentInitialization {
    public static void constructor() throws Exception {
        // Create a new document instance
        Document doc = new Document();

        // Initialize and set a GlossaryDocument to the main document
        GlossaryDocument glossaryDoc = new GlossaryDocument();
        doc.setGlossaryDocument(glossaryDoc);
    }
}
```

**Açıklama**  
- `Document`, tüm Aspose.Words belgeleri için temel sınıftır.  
- `GlossaryDocument`, ana belgeye atanabilir ve sözlük girişlerini, dipnotları ve diğer yardımcı içeriği dosyanın ayrılmış bir kısmında saklamanızı sağlar.

### Özellik 2: sayfa arka plan rengini ayarla

#### Genel bakış
Sayfa arka planlarını özelleştirmek, okunabilirliği artırır ve belgeleri kurumsal marka ile uyumlu hâle getirir.

#### Sayfa arka plan rengini nasıl ayarlarsınız?
`Document` nesnesi üzerinde `setPageColor()` metodunu kullanın ve istediğiniz tonu temsil eden bir `java.awt.Color` değeri geçirin.

```java
import com.aspose.words.Document;
import java.awt.Color;

public class SetPageBackgroundColor {
    public void setPageColor() throws Exception {
        // Create a new document and add text to it (omitted for brevity)
        Document doc = new Document();

        // Set the background color of all pages to light gray
        doc.setPageColor(Color.lightGray);

        // Save the document with a specified path
        String outputPath = "YOUR_OUTPUT_DIRECTORY/DocumentBase.SetPageColor.docx";
        doc.save(outputPath);
    }
}
```

**Açıklama**  
- `setPageColor()`, belgede her sayfaya tek tip bir arka plan rengi uygular.  
- `Color` sınıfı RGB değerlerini kabul eder, böylece herhangi bir marka paletini tam olarak eşleştirebilirsiniz.

### Özellik 3: belgeler arasında düğüm içe aktarma

#### Genel bakış
Birden çok kaynaktan içeriği birleştirmek, raporlama ve otomatik yayınlama hatları için yaygın bir gereksinimdir.

#### Kaynak belgeden bir bölümü nasıl içe aktarırsınız?
Hedef `Document` üzerinde `importNode()` metodunu çağırın, içe aktarılacak düğümü ve stil işleme biçimini belirten bir `ImportFormatMode` sağlayın.

```java
import com.aspose.words.Document;
import com.aspose.words.Section;

public class ImportNode {
    public void importNode() throws Exception {
        // Create source and destination documents
        Document srcDoc = new Document();
        Document dstDoc = new Document();

        // Add text to paragraphs in both documents
        srcDoc.getFirstSection().getBody()
            .getFirstParagraph()
            .appendChild(new com.aspose.words.Run(srcDoc, "Source document first paragraph text."));
        dstDoc.getFirstSection().getBody()
            .getFirstParagraph()
            .appendChild(new com.aspose.words.Run(dstDoc, "Destination document first paragraph text."));

        // Import section from source to destination document
        Section importedSection = (Section) dstDoc.importNode(srcDoc.getFirstSection(), true);
        
        // Append the imported section to the destination document
        dstDoc.appendChild(importedSection);
    }
}
```

**Açıklama**  
- `importNode()`, bir düğümü (örneğin bir `Section`) bir belgeden diğerine aktarırken iç yapısını korur.  
- Orijinal stilleri korumak için `ImportFormatMode.KEEP_SOURCE_FORMATTING`, hedef belgenin temasını benimsemek için `USE_DESTINATION_STYLES` seçin.

### Özellik 4: özel format modu ile düğüm içe aktarma

#### Genel bakış
Belgeleri birleştirirken stil tutarlılığını sağlamak görsel uyumsuzlukları önler.

#### Özel içe aktarma format modu nasıl uygulanır?
`importNode()` çağırırken istenen `ImportFormatMode`'u belirtin. Bu, kaynak formatlamanın korunup korunmayacağını kontrol etmenizi sağlar. `ImportFormatMode`, düğüm içe aktarımı sırasında formatlamanın nasıl ele alındığını tanımlayan bir enum'dur; örneğin kaynak stilleri tutma veya hedef stilleri kullanma gibi.

```java
import com.aspose.words.Document;
import com.aspose.words.Style;
import com.aspose.words.StyleType;
import com.aspose.words.ImportFormatMode;

public class ImportNodeCustom {
    public void importNodeCustom() throws Exception {
        // Create source and destination documents with different style configurations
        Document srcDoc = new Document();
        Style srcStyle = srcDoc.getStyles().add(StyleType.CHARACTER, "My style");
        srcStyle.getFont().setName("Courier New");

        Document dstDoc = new Document();
        Style dstStyle = dstDoc.getStyles().add(StyleType.CHARACTER, "My style");
        dstStyle.getFont().setName("Calibri");

        // Use importNode with specific format mode
        Section importedSection = (Section) dstDoc.importNode(srcDoc.getFirstSection(), true, ImportFormatMode.USE_DESTINATION_STYLES);
    }
}
```

**Açıklama**  
- `ImportFormatMode` üç seçenek sunar: `KEEP_SOURCE_FORMATTING`, `USE_DESTINATION_STYLES` ve `MERGE_FORMATTING`.  
- Uygun modu seçmek, içe aktarma sonrası stil temizleme ihtiyacını ortadan kaldırır.

### Özellik 5: belge sayfaları için arka plan şekli ayarlama

#### Genel bakış
Şekilleri sayfa arka planı olarak kullanmak, ana içeriğin arkasına filigran, logo veya tam sayfa görüntü eklemenizi sağlar.

#### Arka plan şekli nasıl eklenir?
`ShapeType.IMAGE` tipinde bir `Shape` oluşturun, düzenini `WRAP_NONE` olarak ayarlayın ve belgeye tüm metnin arkasında görünmesi için üstbilgi veya altbilgiye ekleyin. `Shape`, bir görüntü, metin kutusu veya geometrik şekil gibi bir çizim nesnesini temsil eder ve belge içinde herhangi bir yere yerleştirilebilir.

```java
import com.aspose.words.Document;
import com.aspose.words.Shape;

public class SetBackgroundShape {
    public void setBackgroundShape() throws Exception {
        // Create a new document
        Document doc = new Document();

        // Add a shape to the background of each page
        Shape shape = new Shape(doc, com.aspose.words.ShapeType.STAR);
        shape.setWidth(200);
        shape.setHeight(100);
        shape.getFill().setColor(Color.RED);
        
        // Set the shape as the background for all pages (code omitted for brevity)

        doc.save("YOUR_OUTPUT_DIRECTORY/DocumentWithBackgroundShape.docx");
    }
}
```

**Açıklama**  
- `Shape` nesneleri görüntüler, vektör grafikler veya geometrik şekiller içerebilir.  
- Şekli bir üstbilgi/altbilgiye yerleştirmek, her sayfada tekrarlanmasını sağlar ve gövde akışını etkilemez.

## Yaygın sorunlar ve hata ayıklama

- **Lisans bulunamadı** – `License` nesnesinin geçerli bir `.lic` dosyasına işaret ettiğini ve dosyanın sınıf yolunda bulunduğunu doğrulayın.  
- **Renk uygulanmadı** – `setPageColor()` metodunu belgeyi kaydetmeden **önce** çağırdığınızdan emin olun; kaydettikten sonraki değişiklikler kalıcı olmaz.  
- **ImportNode bir istisna fırlatıyor** – Hem kaynak hem de hedef belgelerin aynı `LoadOptions` (ör. aynı `LoadFormat`) ile yüklendiğini doğrulayın.  
- **Arka plan şekli metnin arkasında görünüyor ancak görünmez** – Görüntü dosya yolunun doğru olduğundan ve şeklin `RelativeHorizontalPosition` ve `RelativeVerticalPosition` değerlerinin `PAGE` olarak ayarlandığından emin olun.

## Sıkça sorulan sorular

**S: PDF desteği için ayrı bir Maven artefaktına ihtiyacım var mı?**  
C: Hayır. `aspose-words` artefaktı, PDF, DOCX, HTML ve 30'dan fazla diğer format için yerleşik desteği içerir.

**S: Belge kaydedildikten sonra arka plan rengini değiştirebilir miyim?**  
C: Evet, kaydedilen dosyayı yükleyin, `setPageColor()` metodunu tekrar çağırın ve yeniden kaydedin; işlem hızlıdır çünkü Aspose.Words doğrudan dosya akışı üzerinde çalışır.

**S: Aspose.Words ne kadar büyük bir belgeyi işleyebilir?**  
C: Kütüphane, akış API'lerini kullanarak bellek tüketimini 200 MB altında tutarak çok sayfalı dosyaları (10.000 sayfaya kadar) işleyebilir.

**S: Dipnotlar için `GlossaryDocument` gerekli mi?**  
C: Dipnotlar, ana belgenin `Footnotes` koleksiyonunda saklanır; `GlossaryDocument` isteğe bağlıdır ve yalnızca ayrı sözlük bölümleri için gereklidir.

**S: Kütüphane Java 17'yi destekliyor mu?**  
C: Evet, Aspose.Words 25.3+ Java 8, 11, 17 ve daha yeni LTS sürümleriyle tam uyumludur.

---

**Son Güncelleme:** 2026-08-10  
**Test Edilen Versiyon:** Aspose.Words for Java 25.3  
**Yazar:** Aspose

## İlgili Öğreticiler

- [Aspose.Words Java İçerik Yönetimi Öğreticileri - Belge İşlemede Ustalık](/words/java/content-management/)
- [Aspose.Words Java'yı Verimli Belge Değişken Manipülasyonu için Ustalaştırın](/words/java/content-management/aspose-words-java-document-variable-manipulation/)
- [Aspose.Words Java: Belge İşlemleri Öğreticileri](/words/java/document-operations/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< blocks/products/products-backtop-button >}}

{{< /blocks/products/pf/main-wrap-class >}}