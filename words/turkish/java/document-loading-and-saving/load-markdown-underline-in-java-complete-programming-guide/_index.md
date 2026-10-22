---
category: general
date: 2026-08-04
description: Java'da markdown alt çizgiyi yükleyin ve markdown'ı belgeye yüklerken
  markdown biçimlendirmesini koruyun. Bu adım adım öğreticiyi izleyin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: tr
lastmod: 2026-08-04
og_description: Java'da markdown alt çizgiyi yükleyin ve markdown biçimlendirmesini
  koruyun. Tam alt çizgi desteğiyle markdown'ı belgeye nasıl yükleyeceğinizi öğrenin.
og_image_alt: Diagram showing load markdown underline process
og_title: Java'da markdown alt çizgiyi yükleme – adım adım rehber
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: Java'da markdown alt çizgisi yükleme – tam programlama rehberi
url: /tr/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da markdown alt çizgisi yükleme – tam programlama rehberi

Eğer bir Markdown dosyasını `Document` nesnesine dönüştürürken **markdown alt çizgisini yüklemeniz** gerekiyorsa, bu rehber tam olarak nasıl yapılacağını gösterir. Ayrıca **markdown'ı belgeye yüklemeyi** alt çizgi stilini kaybetmeden nasıl yapacağınızı öğrenecek ve orijinal Markdown biçimlendirmesinin tamamen korunmasını sağlayacaksınız.

Bu öğretici, bilmeniz gereken her şeyi kapsar: gerekli kütüphaneler, her yapılandırma adımı ve alt çizgi biçimlendirmesinin içe aktarım sırasında hayatta kalıp kalmadığını nasıl doğrulayacağınız. Sonunda, herhangi bir Java projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

- Java 17 veya daha yeni bir sürüm yüklü (örnek modern modül sistemini kullanır)
- En son **GroupDocs.Viewer** sürümü (veya `LoadOptions` ve `Document` sağlayan uyumlu bir kütüphane)
- Alt çizgili metin içeren bir Markdown dosyası (`sample.md`), örneğin `<u>underlined</u>` veya GitHub‑tarzı sözdizimi `__underlined__`
- IntelliJ IDEA veya VS Code gibi bir IDE, ancak herhangi bir metin düzenleyici de çalışır

Bu gereksinimler, kodun ek yapılandırma olmadan çalışmasını garanti eder.

## Markdown alt çizgisi yükleme – adım adım rehber

İşlem üç temel adımdan oluşur: bir `LoadOptions` örneği oluşturma, alt çizgi algılamayı etkinleştirme ve son olarak bu seçeneklerle Markdown dosyasını yükleme. Her adım aşağıda açıklanmıştır.

### Adım 1: Belge için `LoadOptions` Oluşturma

`LoadOptions`, kütüphanenin kaynak dosyayı nasıl ayrıştıracağını özelleştirmenizi sağlar. Yeni bir örnek oluşturmak, sonraki ayarlar için temiz bir başlangıç sunar.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

`LoadOptions` nesnesi, tüm içe aktarma‑ile ilgili ince ayarların giriş noktasıdır. Alt çizgi algılamasını bir sonraki adımda açmak için bunu kullanacaksınız.

### Adım 2: Yükleme sırasında alt çizgi biçimlendirmesinin algılanmasını etkinleştirme

Varsayılan olarak görüntüleyici, Markdown’da daha az yaygın oldukları için alt çizgi etiketlerini göz ardı edebilir. Bu bayrağı etkinleştirmek, ayrıştırıcıya alt çizgi aralıklarını korumasını söyler.

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

`setImportUnderlineFormatting(true)` ayarı, herhangi bir `<u>` HTML etiketi veya GitHub‑tarzı alt çizgi sözdiziminin `Document` modeline bir alt çizgi stili olarak çevrilmesini sağlar. Bu, **markdown alt çizgisini yükleme** işleminin beklendiği gibi çalışmasını sağlayan temel adımdır.

### Adım 3: Yapılandırılmış seçeneklerle Markdown dosyasını yükleme

Şimdi dosyayı yükleyebilirsiniz. `loadOptions` nesnesini `Document` yapıcısına aktarın, böylece ayrıştırıcı alt çizgi bayrağını dikkate alır.

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

Yapıcı tamamlandığında, `markdownDoc` Markdown kaynağının tam bir bellek içi temsilini, alt çizgi çalıştırmalarıyla birlikte içerir.

### Adım 4: Alt çizgi biçimlendirmesinin korunduğunu doğrulama

Hızlı bir tutarlılık kontrolü, **markdown biçimlendirmesini koruma** işleminin başarılı olduğunu doğrulamanıza yardımcı olur. Aşağıdaki kod parçacığı, her paragrafın metnini yazdırır ve alt çizili bölümleri görünürlük için tilde (`~`) ile işaretler.

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**Beklenen çıktı** (`sample.md` dosyasının `This is __underlined__ text` içerdiğini varsayarsak):

```
This is ~underlined~ text
```

Tildeler, alt çizgi stilinin içe aktarım sırasında hayatta kaldığını gösterir ve **markdown'ı belgeye yükleme** işleminin orijinal biçimlendirmeyi koruduğunu kanıtlar.

## Yaygın tuzaklar ve nasıl kaçınılır

| Belirti | Neden | Çözüm |
|---|---|---|
| Yükleme sonrası alt çizgi kaybolur | `setImportUnderlineFormatting` varsayılan `false` olarak bırakıldı | `Document` oluşturulmadan önce `loadOptions.setImportUnderlineFormatting(true)` çağırdığınızdan emin olun. |
| Metnin yalnızca bir kısmı alt çizgili | Karışık Markdown sözdizimi (örneğin HTML `<u>` ile `__underline__` karışımı) | Kütüphane her ikisini de destekler; kaynak dosyanın tutarlı bir alt çizgi işareti kullandığını doğrulayın. |
| Belge yüklenemedi | Yanlış dosya yolu veya eksik kütüphane bağımlılıkları | Mutlak bir yol kullanın veya `sample.md` dosyasını çalışma dizinine göre yerleştirin; viewer JAR'larını sınıf yoluna ekleyin. |

**Pro tip:** Kalın veya italik stilleri de korumanız gerekiyorsa, sırasıyla `setImportBoldFormatting(true)` ve `setImportItalicFormatting(true)` ile etkinleştirin. Bu bayrakları birleştirerek, en yaygın Markdown stillerinin tam bir içe aktarımını elde edersiniz.

## Tam çalıştırılabilir örnek

Aşağıda her şeyi bir araya getiren bağımsız bir Java programı bulunmaktadır. Kodu `LoadMarkdownUnderlineDemo.java` adlı bir dosyaya kopyalayın, dosya yolunu ayarlayın ve `java LoadMarkdownUnderlineDemo` ile çalıştırın.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

Programı çalıştırdığınızda belge içeriği alt çizgi işaretleriyle yazdırılır, bu da **markdown alt çizgisini yükleme** özelliğinin çalıştığını ve içe aktarma hattı boyunca **markdown biçimlendirmesini koruma** yapabildiğinizi kanıtlar.

## Sonuç

Artık Java’da **markdown alt çizgisini yükleme**, **markdown'ı belgeye yükleme** sırasında orijinal stilin korunması ve alt çizgi biçimlendirmesinin bütünlüğünün doğrulanması konularını biliyorsunuz. Bu yaklaşım, en yeni GroupDocs.Viewer sürümleriyle çalışır ve kalın, italik ve tablolar gibi ek Markdown özelliklerini destekleyecek şekilde genişletilebilir.

Sonra, **tablolar için markdown biçimlendirmesini koruma**, **Markdown'ı PDF'e dönüştürme** veya **içe aktarılan Markdown öğelerinin özel stilini ayarlama** gibi ilgili konuları keşfedin. `LoadOptions` bayraklarını uygulamanızın tam biçimlendirme gereksinimlerine göre ayarlayın; böylece her içe aktarma adımı üzerinde ince ayar kontrolüne sahip olursunuz. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaştırmanıza ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalarla tam çalışan kod örnekleri içerir.

- [Aspose.Words for Java ile Markdown Yükleme Seçeneklerini Ustalaştırın](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [Aspose Words Java ile Markdown Yükleme Seçeneklerini Ustalaştırın](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}