---
category: general
date: 2026-10-07
description: Java’da dipnotları nasıl biçimlendirilir – dipnot ayırıcıyı değiştirmeyi
  öğrenin, dipnot ayırıcı biçimlendirmesini düzenleyin ve biçimlendirilmiş dipnotlarla
  belgeyi kaydedin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to style footnotes
- change footnote separator
- edit footnote separator
- format footnote separator
- access footnote separator
language: tr
lastmod: 2026-10-07
og_description: Java'da Aspose.Words ile dipnotları nasıl biçimlendireceğiniz. Bu
  öğreticide dipnot ayırıcıyı nasıl değiştireceğinizi, dipnot ayırıcı biçimlendirmesini
  nasıl düzenleyeceğinizi ve şık bir belge oluşturacağınızı gösteriyor.
og_image_alt: Screenshot illustrating how to style footnotes in a Java Word processing
  example
og_title: Java'da dipnotları nasıl biçimlendiririz – tam programlama rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: how to style footnotes in Java – learn to change footnote separator,
    edit footnote separator formatting, and save the document with styled footnotes.
  headline: how to style footnotes in Java using Aspose.Words
  type: TechArticle
- description: how to style footnotes in Java – learn to change footnote separator,
    edit footnote separator formatting, and save the document with styled footnotes.
  name: how to style footnotes in Java using Aspose.Words
  steps:
  - name: Load the source document.
    text: Load the source document.
  - name: Iterate through each footnote and **access footnote separator** runs.
    text: Iterate through each footnote and **access footnote separator** runs.
  - name: Apply the desired styling (bold, color, underline, etc.).
    text: Apply the desired styling (bold, color, underline, etc.).
  - name: Save the document with the updated footnote separator.
    text: Save the document with the updated footnote separator.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Java'da Aspose.Words kullanarak dipnotları nasıl biçimlendirilir
url: /tr/java/document-styling/how-to-style-footnotes-in-java-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java kullanarak Aspose.Words ile dipnotları nasıl biçimlendirilir

Eğer Java kullanarak bir Word belgesindeki dipnotları biçimlendirmeniz gerekiyorsa, bu kılavuz **dipnotları nasıl biçimlendireceğinizi** Aspose.Words ile gösterir. Dipnot ayırıcıyı nasıl değiştireceğinizi, dipnot ayırıcı biçimlendirmesini nasıl düzenleyeceğinizi ve değiştirilmiş belgeyi birkaç net adımda nasıl kaydedeceğinizi öğreneceksiniz.

Dipnotlarla çalışmak genellikle ana metin ile dipnot listesi arasındaki ayırıcı çizgiyi ayarlamayı gerektirir. Bu öğreticinin sonunda **dipnot ayırıcı** koşullarına erişebilecek, kalın ya da renk stilini uygulayabilecek ve IDE’nizden çıkmadan dipnotların genel görünümünü kontrol edebileceksiniz.

## Prerequisites

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

* Java 17 veya daha yenisi yüklü.
* Bağımlılıkları yönetmek için Maven 3.6+ (veya Gradle).
* Geçerli bir Aspose.Words for Java lisansı (bu örnek için ücretsiz deneme sürümü yeterlidir).
* En az bir dipnot içeren bir Word kaynağı (ör. `Footnotes.docx`).

Bu gereksinimler, kodun modern Java çalışma zamanlarında sorunsuz çalışmasını sağlar ve **dipnotları nasıl biçimlendireceğiniz** tekniğine odaklanmanızı kolaylaştırır.

## How to style footnotes – overall approach

İşlem dört mantıksal aşamadan oluşur:

1. Kaynak belgeyi yükleyin.
2. Her dipnotu dolaşın ve **dipnot ayırıcı** koşullarına erişin.
3. İstenen stili (kalın, renk, alt çizgi vb.) uygulayın.
4. Güncellenmiş dipnot ayırıcıyla belgeyi kaydedin.

Her aşama doğrudan bir kod satırına karşılık gelir, bu da uygulamayı takip etmeyi ve değiştirmeyi kolaylaştırır.

## Step 1: Set up the Maven project

Yeni bir Maven projesi oluşturun (veya mevcut bir projeye ekleyin) ve Aspose.Words bağımlılığını ekleyin:

```xml
<!-- pom.xml -->
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.10</version> <!-- Use the latest version -->
    </dependency>
</dependencies>
```

> **Pro tip:** Kütüphane sürümünü güncel tutun; yeni sürümler dipnot işleme için hata düzeltmeleri içerir.

## Step 2: Load the source document containing footnotes

```java
import com.aspose.words.*;

public class FootnoteStyler {
    public static void main(String[] args) throws Exception {
        // Load the Word file that has footnotes.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
```

`Document` nesnesi tüm Word dosyasını temsil eder. **dipnotları nasıl biçimlendireceğiniz** sürecindeki ilk somut adımdır bu.

## Step 3: Iterate over each footnote and **access footnote separator**

```java
        // Iterate through all footnotes in the document.
        for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
            // The separator is a Run that appears between the main text and the footnote list.
            Run separator = footnote.getSeparator();

            // Guard against unexpected null values (rare but possible with corrupted files).
            if (separator != null) {
                // Apply desired styling to the separator run.
                separator.getFont().setBold(true);          // change footnote separator to bold
                separator.getFont().setColor(Color.BLUE);   // optional: set a custom color
                separator.getFont().setUnderline(Underline.SINGLE);
            }
        }
```

Bu blokta `footnote.getSeparator()` aracılığıyla **dipnot ayırıcı** koşullarına **erişiyoruz**. `Run` nesnesi, metin stilini tam kontrol etmenizi sağlar ve tek bir kod satırıyla **dipnot ayırıcı** görünümünü değiştirmenize imkan verir.

### Why we use `Footnote.getSeparator()`

* `Footnote.getSeparator()` ayırıcı çizgiyi içeren koşulu döndürür.  
* **dipnot ayırıcı**nı doğrudan **düzenlemenizi** sağlayan tek API giriş noktasıdır.  
* Koşulun `Font` özelliklerini değiştirmek, aynı stili paylaşan tüm dipnotların görsel ayırıcısını günceller.

## Step 4: (Optional) Style the continuation separator and notice

Word üç ayrı ayırıcı türünü ayırt eder:

| Tür                       | API yöntemi                                 | Tipik kullanım durumu |
|---------------------------|---------------------------------------------|-----------------------|
| Ana ayırıcı               | `Footnote.getSeparator()`                   | Ana metni ilk dipnottan ayırır |
| Devam ayırıcı             | `Footnote.getContinuationSeparator()`      | Sonraki dipnot sayfalarını ayırır |
| Devam bildirimi           | `Footnote.getContinuationNotice()`          | Sonraki sayfalarda “Continued…” metnini gösterir |

Eğer devam sayfaları için de **dipnot ayırıcı** biçimlendirmek istiyorsanız, döngü içinde aşağıdaki kodu ekleyin:

```java
            // Continuation separator (optional)
            Run contSeparator = footnote.getContinuationSeparator();
            if (contSeparator != null) {
                contSeparator.getFont().setItalic(true);
                contSeparator.getFont().setSize(9);
            }

            // Continuation notice (optional)
            Run contNotice = footnote.getContinuationNotice();
            if (contNotice != null) {
                contNotice.getFont().setColor(Color.GRAY);
            }
```

Bu snippet’ler, birincil satırın ötesinde **dipnot ayırıcı** nesnelerini **düzenlemenizi** sağlayarak dipnot düzeni üzerinde tam kontrol sunar.

## Step 5: Save the modified document

```java
        // Save the document with the styled footnote separators.
        doc.save("YOUR_DIRECTORY/FootnotesStyled.docx");
    }
}
```

Dosyayı kaydetmek, tüm stil değişikliklerini diske yazar ve **dipnotları nasıl biçimlendireceğiniz** iş akışını tamamlar.

## Full, runnable example

Tüm parçaları bir araya getirdiğinizde, kopyalayıp derleyip çalıştırabileceğiniz bağımsız bir program elde edersiniz:

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to style footnotes in a Word document using Aspose.Words for Java.
 * The example loads a document, makes the footnote separator bold and blue,
 * optionally styles continuation elements, and saves the result.
 */
public class FootnoteStyler {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");

        // 2. Iterate through each footnote.
        for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
            // 3a. Access and style the primary separator.
            Run separator = footnote.getSeparator();
            if (separator != null) {
                separator.getFont().setBold(true);          // change footnote separator
                separator.getFont().setColor(Color.BLUE);   // set a custom color
                separator.getFont().setUnderline(Underline.SINGLE);
            }

            // 3b. (Optional) Style continuation separator.
            Run contSeparator = footnote.getContinuationSeparator();
            if (contSeparator != null) {
                contSeparator.getFont().setItalic(true);
                contSeparator.getFont().setSize(9);
            }

            // 3c. (Optional) Style continuation notice.
            Run contNotice = footnote.getContinuationNotice();
            if (contNotice != null) {
                contNotice.getFont().setColor(Color.GRAY);
            }
        }

        // 4. Save the modified document.
        doc.save("YOUR_DIRECTORY/FootnotesStyled.docx");
    }
}
```

**Beklenen çıktı:** `FootnotesStyled.docx` dosyasını Microsoft Word’de açın. Ana metin ile dipnot listesi arasındaki ayırıcı çizgi kalın, mavi ve altı çizili olarak görünür. Belge birden fazla sayfaya yayılan dipnotlar içeriyorsa, devam ayırıcı italik ve daha küçük, devam bildirimi ise gri renkte gösterilir.

## Common questions and edge‑case handling

| Soru | Cevap |
|------|-------|
| *Bir dipnotun ayırıcısı yoksa ne olur?* | `Footnote.getSeparator()` `null` döndürür. Kod, stil uygulamadan önce `null` kontrolü yapar ve `NullPointerException` oluşmasını önler. |
| *Sadece ilk dipnota farklı bir stil uygulayabilir miyim?* | Evet. Döngü içinde bir sayaç ekleyin ve `index == 0` olduğunda koşullu biçimlendirme yapın. |
| *.doc dosyalarıyla çalışır mı?* | Aspose.Words hem `.doc` hem de `.docx` formatlarını destekler. Uygun yolu yükleyin, aynı API çağrıları geçerlidir. |
| *Orijinal stile nasıl geri dönerim?* | Orijinal `Font` ... |

## What Should You Learn Next?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalarla tam çalışan kod örnekleri içerir; böylece ek API özelliklerini öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to Change Cell Borders in Tables – Aspose.Words for Java](/words/english/java/document-conversion-and-export/formatting-tables-and-table-styles/)
- [How to Add Watermark – Document Conversion and Export with Aspose.Words for Java](/words/english/java/document-conversion-and-export/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}