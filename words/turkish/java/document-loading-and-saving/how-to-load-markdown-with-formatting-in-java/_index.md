---
category: general
date: 2026-11-22
description: Java’da biçimlendirmeli markdown nasıl yüklenir öğrenin. Bu kılavuz,
  LoadOptions ve Document kullanarak biçimlendirmeli markdown nasıl okunacağını gösterir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to load markdown
- read markdown with formatting
- Java markdown parsing
- LoadOptions import underline
- Document processing Java
language: tr
lastmod: 2026-11-22
og_description: Java'da biçimlendirmeli markdown nasıl yüklenir. Biçimlendirmeli markdown
  okumak, alt çizgi stillerini korumak ve Document nesneleriyle çalışmak için bu kapsamlı
  öğreticiyi izleyin.
og_image_alt: Java code snippet showing markdown loading with formatting enabled
og_title: Java’da biçimlendirmeli markdown nasıl yüklenir – adım adım rehber
schemas:
- author: GroupDocs
  dateModified: '2026-11-22'
  description: Learn how to load markdown with formatting in Java. This guide shows
    you how to read markdown with formatting using LoadOptions and Document.
  headline: How to load markdown with formatting in Java
  type: TechArticle
tags:
- markdown
- java
- document-processing
title: Java'da biçimlendirmeli markdown nasıl yüklenir
url: /tr/java/document-loading-and-saving/how-to-load-markdown-with-formatting-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java'da biçimlendirmeli markdown nasıl yüklenir

Görsel stillerini koruyarak **markdown nasıl yüklenir** ihtiyacınız varsa, bu öğretici size hazır‑çalıştır bir çözüm sunar. Altı çizili metin gibi **biçimlendirmeli markdown nasıl okunur** olduğunu tam olarak göreceksiniz, böylece oluşturulan belge orijinal kaynağa eşleşir.

Kılavuz, yükleyiciyi yapılandırmadan biçimlendirmenin içe aktarımda hayatta kalıp kalmadığını doğrulamaya kadar her adımı kapsar. Standart GroupDocs.Viewer kütüphanesi (veya `LoadOptions` ve `Document` sağlayan herhangi bir uyumlu API) dışındaki harici araçlara ihtiyaç yoktur. Sonunda markdown yüklemeyi herhangi bir Java backend, web servisi veya masaüstü uygulamasına entegre edebilirsiniz.

## Önkoşullar

Başlamadan önce şunların kurulu olduğundan emin olun:

* Java 17 veya daha yeni bir sürüm yüklü.
* Bağımlılık yönetimi için Maven veya Gradle.
* `LoadOptions` ve `Document` sınıflarını içeren GroupDocs.Viewer (veya eşdeğeri) JAR dosyasına erişim.
* Altı çizili işaretleme içeren bir örnek markdown dosyası (`sample.md`) (ör. `<u>underlined text</u>` veya `_underlined_`, ayrıştırıcıya bağlı olarak).

## Adım 1: Gerekli bağımlılığı ekleyin

Maven kullanıyorsanız, `pom.xml` dosyanıza aşağıdakileri ekleyin. Sürümü en son kararlı sürüme göre ayarlayın.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>23.12</version>
</dependency>
```

Gradle kullanıcıları şunu ekleyebilir:

```groovy
implementation 'com.groupdocs:groupdocs-viewer:23.12'
```

Kütüphaneyi eklemek, `LoadOptions` ve `Document` sınıflarını derleme zamanında kullanılabilir hâle getirir.

## Adım 2: Altı çizili biçimlendirmeyi içe aktarmak için LoadOptions yapılandırın

`LoadOptions` nesnesi, ayrıştırıcının hangi markdown özelliklerini koruyacağını belirtir. Altı çizili biçimlendirmeyi etkinleştirmek, görsel stilin oluşan `Document` içinde görünmesini sağlar.

```java
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Creates a LoadOptions instance with underline import enabled.
 *
 * @return configured LoadOptions
 */
private static LoadOptions createLoadOptions() {
    LoadOptions loadOptions = new LoadOptions();
    // Preserve underline markup when the markdown is parsed.
    loadOptions.setImportUnderlineFormatting(true);
    return loadOptions;
}
```

**Bu neden önemlidir:**  
`setImportUnderlineFormatting(true)` çağrısı olmadan, ayrıştırıcı altı çizili etiketleri kaldırır ve sadece düz metin bırakır. Bu bayrağın etkinleştirilmesi stilin bütünlüğünü korur; bu, alt süreç tüketicisinin (ör. bir PDF oluşturucu) görsel ipuçlarına dayanması gerektiğinde kritiktir.

## Adım 3: Yapılandırılmış seçeneklerle markdown belgesini yükleyin

Şimdi markdown dosyasını okuyabilirsiniz. `Document` yapıcı metodu, dosya yolunu ve az önce hazırladığınız `LoadOptions` nesnesini kabul eder.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Loads a markdown file while preserving formatting.
 *
 * @param markdownPath absolute or relative path to the .md file
 * @param options      LoadOptions with formatting flags
 * @return Document representing the parsed markdown
 */
private static Document loadMarkdown(String markdownPath, LoadOptions options) {
    return new Document(markdownPath, options);
}
```

**Bu neden önemlidir:**  
`LoadOptions` nesnesini `Document` yapıcısına geçirmek, ayrıştırıcının tüm içe aktarma sürecinde altı çizili bayrağı dikkate almasını garanti eder. Ortaya çıkan `Document` nesnesi tam biçimlendirme ile render, dönüştürme veya inceleme yapılabilir.

## Adım 4: Altı çizili biçimlendirmenin hayatta kalıp kalmadığını doğrulayın

Altı çizili stilin mevcut olduğunu hızlıca kontrol etmenin bir yolu, belgeyi HTML’e render edip çıktıyı yazdırmaktır. İçe aktarma başarılıysa HTML `<u>` etiketlerini içerecektir.

```java
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.Viewer;

/**
 * Renders the loaded Document to HTML and prints the first page.
 *
 * @param doc Document loaded from markdown
 */
private static void renderAndPrint(Document doc) {
    // Create a Viewer instance for rendering.
    Viewer viewer = new Viewer(doc);
    // Render the first page as HTML.
    HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
    viewer.view(viewOptions, 1);
    String html = viewOptions.getHtmlContent();

    System.out.println("Rendered HTML snippet:");
    System.out.println(html.substring(0, Math.min(html.length(), 500)));
}
```

Tam programı çalıştırdığınızda `<u>underlined text</u>` içeren bir HTML snippet’i görüntülenir. Etiket eksikse, `setImportUnderlineFormatting(true)` çağrısının dosya yüklemeden önce yapıldığını tekrar kontrol edin.

## Tam çalıştırılabilir örnek

Her şeyi bir araya getirdiğimizde, derleyip çalıştırabileceğiniz bağımsız bir Java sınıfı aşağıdadır:

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.Viewer;
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Demonstrates how to load markdown with formatting in Java.
 * The program reads a markdown file, preserves underline markup,
 * renders the first page to HTML, and prints a snippet.
 */
public class MarkdownLoader {

    public static void main(String[] args) {
        // Path to the markdown file – adjust as needed.
        String markdownPath = "sample.md";

        // Step 1: create LoadOptions with underline support.
        LoadOptions options = createLoadOptions();

        // Step 2: load the markdown document.
        Document doc = loadMarkdown(markdownPath, options);

        // Step 3: render the document to HTML and verify formatting.
        renderAndPrint(doc);
    }

    private static LoadOptions createLoadOptions() {
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setImportUnderlineFormatting(true);
        return loadOptions;
    }

    private static Document loadMarkdown(String path, LoadOptions options) {
        return new Document(path, options);
    }

    private static void renderAndPrint(Document doc) {
        Viewer viewer = new Viewer(doc);
        HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
        viewer.view(viewOptions, 1); // render first page
        String html = viewOptions.getHtmlContent();

        System.out.println("Rendered HTML snippet:");
        System.out.println(html.substring(0, Math.min(html.length(), 500)));
    }
}
```

**Beklenen çıktı (kısaltılmış):**

```
Rendered HTML snippet:
<div class="page">
  <p>This is a <u>underlined text</u> example from the markdown file.</p>
  …
```

`<u>` etiketi görünüyorsa, markdown biçimlendirmesi korunarak yüklenmiştir.

## Yaygın varyasyonlar ve kenar durumları

| Durum                                   | Ne değiştirilmeli                                               |
|----------------------------------------|-----------------------------------------------------------------|
| **Farklı markdown uzantıları**          | Kalın metin için **bold** `loadOptions.setImportBoldFormatting(true)` kullanın. |
| **Büyük dosyalar (> 10 MB)**            | Dosyayı `FileInputStream` ile akışa alıp akışı `Document`'e geçirin. |
| **PDF çıktısı gerekiyor**               | Yüklemeden sonra, altı çizili stilleri koruyan bir PDF oluşturmak için `Viewer` ile `PdfViewOptions` kullanın. |
| **Servlet konteynerinde çalıştırma**    | `Document`'i istek kapsamına (request scope) kaydedin ve anında HTML olarak render edin. |

**Pro ipucu:** Her yükleme işlemi için yeni bir `LoadOptions` örneği oluşturun. Aynı nesneyi birden çok iş parçacığında yeniden kullanmak beklenmeyen durum sızıntılarına yol açabilir.

## Sonuç

Artık **Java'da biçimlendirmeli markdown nasıl yüklenir** ve `LoadOptions` kullanarak **biçimlendirmeli markdown nasıl okunur** biliyorsunuz. Tam örnek, yapılandırma, yükleme ve doğrulamayı gösteriyor; böylece bu deseni markdown dosyaları işleyen herhangi bir Java projesine yerleştirebilirsiniz.  

Sonra, **markdown'ı resimlerle okuma**, **markdown'ı PDF'ye dönüştürme** veya **diğer stil içe aktarmalarını (kalın, italik, üstü çizili) özelleştirme** gibi ilgili konuları keşfedin. Bu uzantıların her biri aynı modeli izler: `LoadOptions` bayraklarını ayarlayın, `Document`'i yükleyin ve istediğiniz formatta render edin.

Kodlamanın tadını çıkarın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Java'da özel içe aktarma seçenekleriyle markdown belgesi nasıl yüklenir](/words/english/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/)
- [Aspose.Words ile Java'da bir Markdown dosyasını nasıl okur ve yüklersiniz](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)
- [Java'da Markdown Yükleme – Tam Kılavuz](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}