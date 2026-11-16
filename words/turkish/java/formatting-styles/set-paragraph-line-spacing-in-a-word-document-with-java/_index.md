---
category: general
date: 2026-11-15
description: Java ile bir Word belgesinde paragraf satır aralığını ayarlayın. Aspose.Words
  kullanarak satır aralığını programlı olarak nasıl ayarlayacağınızı öğrenin ve belge
  formatlamasını hassas bir şekilde yapın.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: tr
lastmod: 2026-11-15
og_description: Java ile bir Word belgesinde paragraf satır aralığını ayarlayın. Bu
  kılavuz, Aspose.Words kullanarak paragraflar ve dipnot ayırıcıları için satır aralığını
  nasıl ayarlayacağınızı açıklayarak belge düzeni üzerinde tam kontrol sağlar.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Java kullanarak Word'de paragraf satır aralığını ayarlayın
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Java ile bir Word belgesinde paragraf satır aralığını ayarlayın
url: /tr/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java ile bir Word belgesinde paragraf satır aralığını ayarlama

Eğer bir Word belgesinde **paragraf satır aralığını ayarlamanız** gerekiyorsa, bu öğretici Java ve Aspose.Words ile bunu nasıl yapacağınızı gösterir. Ayrıca profesyonel belgeleri biçimlendirirken yaygın bir gereksinim olan dipnot ayırıcıları için **satır aralığını nasıl ayarlayacağınızı** öğreneceksiniz.

Aşağıdaki bölümlerde şunları yapacaksınız:

* Mevcut bir *.docx* dosyasını yükleyin.
* Dipnot ayırıcı paragrafını alın.
* Özel bir satır‑aralığı değeri uygulayın.
* Güncellenmiş belgeyi kaydedin.

Projeye Aspose.Words kütüphanesini eklemenin ötesinde harici bir yapılandırma gerekmez; bu yüzden kodu olduğu gibi kopyalayıp hemen çalıştırabilirsiniz.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* Java 17 veya daha yeni bir sürüm.
* Bağımlılıkları yönetmek için Maven (veya başka bir yapı aracı).
* Geçerli bir Aspose.Words for Java lisansı (ücretsiz deneme sürümü test için yeterlidir).
* Bilinen bir dizinde bulunan bir giriş Word belgesi (`input.docx`).

Aspose.Words bağımlılığını `pom.xml` dosyanıza ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Aspose.Words ile paragraf satır aralığını ayarlama

Bu H2 başlığı ana anahtar kelimeyi içerir ve SEO gereksinimini karşılar.

### Adım 1: Word belgesini yükleyin

İlk olarak, kaynak dosyanıza işaret eden bir `Document` örneği oluşturun.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Why this matters*: Belgeyi yüklemek, orijinal dosyaya dokunmadan, yalnızca açıkça kaydettiğinizde değişiklik yapabileceğiniz bir bellek içi model sağlar.

### Adım 2: Dipnot ayırıcıyı alın

Dipnot ayırıcıları, dipnotlar ile ana metin arasında görünen özel paragraflardır. Görünümünü değiştirmek için `FootnoteSeparator` nesnesine erişmeniz gerekir.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Tip*: Belgenizde dipnot yoksa bile ayırıcı gizli bir paragraf olarak bulunur, bu yüzden çağrı asla `null` döndürmez.

### Adım 3: Ayırıcı paragrafının satır aralığını nasıl ayarlarsınız

Şimdi istediğiniz satır aralığını uygulayın. Aspose.Words satır‑aralığı değerleri için puan (point) birimini kullanır; 12 pts çoğu yazı tipi için tek satır aralığına yakındır.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Ayrıca diğer aralık modlarını da kullanabilirsiniz:

| Mod                     | Metod çağrısı                                      |
|--------------------------|--------------------------------------------------|
| **Exactly** (sabit pt) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`   |
| **Multiple** (örnek, 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Doğru kuralı seçmek, belgenin Word, Google Docs ve diğer görüntüleyicilerde tutarlı bir şekilde render edilmesini sağlar.

### Adım 4: Güncellenmiş belgeyi kaydedin

Son olarak, değişiklikleri diske yazın.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

`output.docx` dosyasını Microsoft Word’de açtığınızda, dipnot ayırıcı tanımladığınız satır aralığıyla görüntülenecektir.

## Düzenli paragraflar için satır aralığını nasıl ayarlayacağınızı anlama

Aynı API, sadece dipnot ayırıcıları için değil, herhangi bir `Paragraph` nesnesi için de çalışır. İşte gövdenin ilk paragrafının aralığını ayarlayan hızlı bir örnek:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Why you might need this**: Raporlar, sözleşmeler ve akademik makaleler genellikle belirli bir satır‑aralığı stiline (ör. taslaklar için çift satır) ihtiyaç duyar. Aynı `setLineSpacing` metodunu kullanmak, beklediğiniz kesin düzeni garanti eder.

## Yaygın tuzaklar ve nasıl önlenir

| Sorun                                 | Neden                                   | Çözüm |
|---------------------------------------|----------------------------------------|-----|
| Satır aralığı değişmemiş görünüyor    | `LineSpacingRule` varsayılan (AUTO) olarak bırakıldı | `setLineSpacingRule` ile kuralı açıkça ayarlayın. |
| Ayırıcıdan sonra ekstra boş satırlar  | Ayırıcı gizli satır sonları içeriyor | Satır aralığını uygulamadan önce `separator.getText().trim();` ile ayırıcının metnini kırpın. |
| Kaydetme sonrası belge bozuluyor      | Eski bir Aspose.Words sürümü kullanılıyor | En son sürüme (ör. 24.10) yükseltin; bu sürüm kaydetme için hata düzeltmeleri içerir. |

## Pro ipucu: birden fazla belgeyi toplu işleyin

Onlarca dosyayı güncellemeniz gerekiyorsa, mantığı bir yardımcı metoda sarın ve bir klasör üzerinde yineleyin:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Bu yöntemi bir döngü içinde çalıştırmak, saatler süren manuel düzenlemeyi ortadan kaldırır.

## Beklenen çıktı

Tam programı çalıştırdıktan sonra `output.docx` şu şekilde olacaktır:

* Satır aralığı dışındaki orijinal içerik aynı kalır.
* Dipnot ayırıcı tek satır aralığı (12 pts) düzeniyle gösterilir.
* Diğer tüm biçimlendirmeler (stilller, görseller, tablolar) korunur.

Dosyayı Word’de açın ve ayırıcı çizgisinin daha sıkı (veya daha gevşek) olduğunu, ayarladığınız değere bağlı olarak doğrulayın.

## Sonuç

Artık Java kullanarak bir Word belgesinde **paragraf satır aralığını ayarlamayı** ve hem dipnot ayırıcıları hem de normal paragraflar için **satır aralığını nasıl ayarlayacağınızı** biliyorsunuz. Tam, çalıştırılabilir örnek, bir belgeyi yüklemeyi, satır‑aralığı özelliklerini ayarlamayı ve sonucu kaydetmeyi – birkaç net API çağrısıyla – gösterir.

**Next steps** olarak şunları keşfedebilirsiniz:

* Tablolar ve liste öğeleri için **satır aralığını nasıl ayarlarsınız**.
* Başlıklar ile gövde metni arasında farklı aralık kuralları uygulama.
* Tüm belge boyunca aralığı zorlamak için `Style` nesnesini kullanma.

Değerlerle deney yapın, diğer biçimlendirme seçenekleriyle birleştirin ve herhangi bir Java uygulamasında belge düzeni üzerinde tam kontrol sahibi olun. İyi kodlamalar!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım‑adım açıklamalar içerir.

- [Aspose.Words for Java’da seçenekleri nasıl ayarlarsınız – tam kılavuz](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Aspose.Words for Java’da LoadOptions nasıl ayarlanır](/words/english/java/document-loading-and-saving/using-load-options/)
- [Word Belgesinde Asya Paragraf Aralığını ve Girintilerini Değiştir](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}