---
category: general
date: 2026-10-10
description: Aspose.Words for Java kullanarak bir Word belgesinde başlık stili dipnotları
  uygulayın – eksiksiz adım adım rehber.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- apply heading style footnotes
- footnote separator
- endnote separator
- Aspose.Words for Java
- style identifier
language: tr
lastmod: 2026-10-10
og_description: Aspose.Words for Java kullanarak bir Word belgesinde başlık stili
  dipnotları uygulayın. Dipnot ve sonnot ayırıcılarını dakikalar içinde nasıl biçimlendireceğinizi
  öğrenin.
og_image_alt: Document after applying heading style footnotes to footnote and endnote
  separators
og_title: Aspose.Words for Java ile başlık stili dipnotlarını uygulama – tam rehber
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Apply heading style footnotes in a Word document using Aspose.Words
    for Java – a complete step‑by‑step guide.
  headline: Apply heading style footnotes with Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word processing
- Document styling
title: Aspose.Words for Java ile başlık stili dipnotlarını uygulayın
url: /tr/java/annotations-comments/apply-heading-style-footnotes-with-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile başlık stili dipnotları uygulama

Eğer bir Word belgesinde **başlık stili dipnotları uygulamanız** gerekiyorsa, bu öğretici Aspose.Words for Java ile bunu tam olarak nasıl yapacağınızı gösterir. Hem dipnot ayırıcı hem de sonnot ayırıcıyı yerleşik başlık stilleriyle biçimlendiren eksiksiz, çalıştırılabilir bir örnek göreceksiniz.

Dipnot ve sonnot ayırıcılarını biçimlendirmek, belgelerin daha kolay okunmasını sağlar ve büyük el yazmalarında tutarlı bir biçimlendirme sunar. Kılavuz ayrıca yaygın tuzakları da kapsar; örneğin doğru `StyleIdentifier` kullanıldığından emin olmak ve zaten özel ayırıcılar içeren belgelerle başa çıkmak.

## Öğrenecekleriniz

* Dipnot ve sonnot içeren bir `.docx` dosyasını nasıl yükleyeceğinizi.  
* **footnote separator** paragrafını nasıl alıp stilini `HEADING_2` olarak ayarlayacağınızı.  
* **endnote separator** paragrafını nasıl alıp stilini `HEADING_3` olarak ayarlayacağınızı.  
* Değiştirilmiş belgeyi nasıl kaydedip değişiklikleri doğrulayacağınızı.  

**Önkoşullar**

* Java 17 veya daha yeni bir sürüm.  
* Aspose.Words for Java 23.12 (veya en son sürüm).  
* Word işleme kavramlarına (dipnotlar, sonnotlar, stiller) temel aşinalık.

---

## Başlık stili dipnotları uygulama – genel bakış

Temel fikir, Aspose.Words’ `Document.getFootnoteSeparator()` ve `Document.getEndnoteSeparator()` yöntemlerini kullanmaktır. Her iki yöntem de ana metin ile dipnot/sonnot alanı arasındaki gizli ayırıcı satırı temsil eden bir `Paragraph` nesnesi döndürür. Paragrafın `ParagraphFormat`'ını değiştirip bir `StyleIdentifier` atayarak, Word arayüzünü manuel olarak düzenlemeden **başlık stili dipnotları** etkili bir şekilde uygularsınız.

## Adım 1: Projeyi kurma

Bir Maven (veya Gradle) projesi oluşturun ve Aspose.Words for Java bağımlılığını ekleyin:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Pro ipucu:** `StyleIdentifier` enum'ı ile ilgili hata düzeltmelerinden yararlanmak için en son sürümü kullanın.

---

## Adım 2: Kaynak belgeyi yükleme

```java
import com.aspose.words.*;

public class ApplyHeadingStyleFootnotes {
    public static void main(String[] args) throws Exception {
        // Load a Word document that already contains footnotes and endnotes.
        Document document = new Document("YOUR_DIRECTORY/Footnotes.docx");
        // From here we will manipulate the footnote and endnote separators.
```

*`Document` yapıcı (constructor) dosyayı belleğe okur ve size tam programatik erişim sağlar.*

---

## Adım 3: Dipnot ayırıcıyı biçimlendirme

```java
        // Retrieve the hidden paragraph that separates footnotes from the main text.
        Paragraph footnoteSeparator = document.getFootnoteSeparator();

        // Apply the built‑in Heading 2 style to this separator.
        footnoteSeparator.getParagraphFormat()
                         .setStyleIdentifier(StyleIdentifier.HEADING_2);
```

`HEADING_2` neden? Başlık stilleri yazı tipi boyutu, renk ve boşlukları devralır; bu da ayırıcıyı görsel olarak belirgin kılar ve yine de belgenin stil hiyerarşisini takip eder.

---

## Adım 4: Sonnot ayırıcıyı biçimlendirme

```java
        // Retrieve the hidden paragraph that separates endnotes.
        Paragraph endnoteSeparator = document.getEndnoteSeparator();

        // Apply the built‑in Heading 3 style to this separator.
        endnoteSeparator.getParagraphFormat()
                        .setStyleIdentifier(StyleIdentifier.HEADING_3);
```

`HEADING_3` kullanmak, dipnot ayırıcıdan daha düşük görsel ağırlık sağlar ve tipik akademik biçimlendirme kurallarıyla uyumludur.

---

## Adım 5: Değiştirilmiş belgeyi kaydetme

```java
        // Persist the changes to a new file.
        document.save("YOUR_DIRECTORY/FootnoteStyled.docx");
        System.out.println("Document saved with styled footnote and endnote separators.");
    }
}
```

Programı çalıştırdıktan sonra, `FootnoteStyled.docx` dosyasını Microsoft Word'de açın. Şunları fark edeceksiniz:

* Dipnot ayırıcı artık **Heading 2** biçimlendirmesiyle (daha büyük yazı tipi, varsayılan olarak kalın) görünür.  
* Sonnot ayırıcı ise **Heading 3** (hafif daha küçük, yine de kalın) biçimini yansıtır.

Bu değişiklikler, belgeye eklenen yeni dipnot ve sonnotlar da dahil olmak üzere, tüm dipnot ve sonnotlara otomatik olarak uygulanır.

---

## Yaygın sorular ve uç durumlar

| Soru | Cevap |
|----------|--------|
| **Belge zaten ayırıcılar için özel stiller kullanıyorsa ne olur?** | `StyleIdentifier`'ı üzerine yazarak mevcut stil değiştirilecektir. Özel biçimlendirmeyi korumanız gerekiyorsa, orijinal stili klonlayın, değiştirin ve klonun tanımlayıcısını atayın. |
| **Yerleşik bir başlık yerine özel bir stil kullanabilir miyim?** | Evet. `document.getStyles().add(StyleIdentifier.CUSTOM)` ile özel stili oluşturun, özelliklerini yapılandırın ve ardından ayırıcı paragrafına tanımlayıcısını atayın. |
| **`.doc` (ikili) dosyalarla da çalışır mı?** | Kesinlikle. Aspose.Words dosya formatını soyutlar, bu yüzden aynı kod `.doc` ve `.docx` için çalışır. |
| **Büyük belgelerde performans etkisi var mı?** | İşlemler O(1) seviyesindedir çünkü tek bir gizli paragrafı hedefler; 500 sayfalık bir belge bile milisaniyeler içinde işlenir. |

---

## Tam kaynak kodu (çalıştırılabilir)

```java
import com.aspose.words.*;

public class ApplyHeadingStyleFootnotes {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document containing footnotes and endnotes.
        Document document = new Document("YOUR_DIRECTORY/Footnotes.docx");

        // 2️⃣ Retrieve the footnote separator and apply Heading 2.
        Paragraph footnoteSeparator = document.getFootnoteSeparator();
        footnoteSeparator.getParagraphFormat()
                         .setStyleIdentifier(StyleIdentifier.HEADING_2);

        // 3️⃣ Retrieve the endnote separator and apply Heading 3.
        Paragraph endnoteSeparator = document.getEndnoteSeparator();
        endnoteSeparator.getParagraphFormat()
                        .setStyleIdentifier(StyleIdentifier.HEADING_3);

        // 4️⃣ Save the modified document.
        document.save("YOUR_DIRECTORY/FootnoteStyled.docx");
        System.out.println("Document saved with styled footnote and endnote separators.");
    }
}
```

**Beklenen çıktı** (konsol):

```
Document saved with styled footnote and endnote separators.
```

Kaydedilen dosyayı açarak biçimlendirilmiş ayırıcıları görün.

---

## Sonuç

Artık Aspose.Words for Java kullanarak bir Word belgesinde **başlık stili dipnotları** nasıl uygulayacağınızı biliyorsunuz. **footnote separator** ve **endnote separator** paragraflarını alıp uygun `StyleIdentifier` değerlerini atayarak sadece birkaç kod satırıyla tutarlı, profesyonel bir biçimlendirme elde edersiniz.

İleride düşünebileceğiniz adımlar:

* Yerleşik başlıklar yerine özel stillerle denemeler yapın.  
* Aynı yaklaşımı kullanarak bir belge topluluğunda stil değişikliklerini otomatikleştirin.  
* Bu tekniği, `getFootnoteOptions()` gibi ince ayarlı dipnot numaralandırması için diğer `Document` API'larıyla birleştirin.

Kodu kendi yayın akışlarınıza uyarlamaktan çekinmeyin, iyi kodlamalar!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words for Java'da Dipnot ve Sonnot Kullanımı](/words/english/java/using-document-elements/using-footnotes-and-endnotes/)
- [Word'ü PDF olarak kaydetme – Aspose.Words ile Adım Adım Java Rehberi](/words/english/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Word'ü Markdown'a Aktarma – Aspose.Words Kullanarak Java Rehberi](/words/english/java/document-conversion-and-export/export-word-to-markdown-java-guide-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}