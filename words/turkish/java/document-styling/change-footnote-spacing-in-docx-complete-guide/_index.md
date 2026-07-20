---
category: general
date: 2026-07-20
description: DOCX dosyalarında dipnot aralığını kolayca değiştirin. Aralığı nasıl
  ayarlayacağınızı, dipnot ayırıcıyı nasıl düzenleyeceğinizi ve paragraf satır aralığını
  Java ile nasıl ayarlayacağınızı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote spacing
- how to set spacing
- adjust footnote separator
- set paragraph line spacing
- change line spacing docx
language: tr
lastmod: 2026-07-20
og_description: DOCX dosyalarında dipnot aralığını hızlıca değiştirin. Bu kılavuz,
  aralığı nasıl ayarlayacağınızı, dipnot ayırıcıyı nasıl düzenleyeceğinizi ve Java’da
  paragraf satır aralığını nasıl özelleştireceğinizi gösterir.
og_image_alt: Screenshot showing Java code that changes footnote spacing in a DOCX
  document
og_title: DOCX’te dipnot aralığını değiştir – Adım Adım Kılavuz
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Change footnote spacing in DOCX files easily. Learn how to set spacing,
    adjust footnote separator, and set paragraph line spacing with Java.
  headline: Change footnote spacing in DOCX – Complete Guide
  type: TechArticle
tags:
- footnote
- docx
- java
- spacing
title: DOCX'te dipnot aralığını değiştir – Tam Kılavuz
url: /tr/java/document-styling/change-footnote-spacing-in-docx-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX'te Dipnot Boşluğunu Değiştirme – Tam Kılavuz

Bir Word belgesinde **dipnot boşluğunu değiştirme** ihtiyacı hiç duydunuz mu ama nereden başlayacağınızı bilemediniz mi? Yalnız değilsiniz. Tezi mükemmelleştiriyor ya da bir sözleşmeyi düzenliyorsanız, dipnot ayırıcıyı doğru ayarlamak büyük bir fark yaratabilir.  

Bu öğreticide **boşluk ayarlama**, dipnot ayırıcıyı düzenleme ve **paragraf satır aralığını ayarlama** konularını Java tabanlı kütüphanelerle adım adım göstereceğiz. Sonunda, herhangi bir projeye ekleyebileceğiniz çalıştırmaya hazır bir örnek elde edeceksiniz.

## Gerekenler

- Java 17 veya daha yeni (kod modern dil özelliklerini kullanıyor)
- Bağımlılık yönetimi için Maven veya Gradle
- En az bir dipnot içeren bir DOCX dosyası (veya manuel olarak bir tane oluşturabilirsiniz)
- **Aspose.Words for Java** kütüphanesi (veya uyumlu herhangi bir API; örnekte Aspose'u kullanacağız)

Hepsi bu—ağır çerçeveler yok, sadece saf Java ve tek bir kütüphane.

![Change footnote spacing in DOCX example](/images/footnote-spacing.png){alt="DOCX'te dipnot boşluğunu değiştirme örneği"}

## Adım 1: DOCX Belgesini Yükleme (Dipnot Boşluğunu Değiştirme)

İlk yapmanız gereken Word dosyasını açmaktır. Bu, üzerinde işlem yapabileceğiniz bir `Document` nesnesi sağlar.

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // Load the DOCX file – change the path to your own file
        Document doc = new Document("input.docx");
        
        // Continue with spacing adjustments...
        adjustFootnoteSeparator(doc);
        
        // Save the updated document
        doc.save("output.docx");
    }
}
```

*Neden önemli*: Belgeyi yüklemek, **dipnot boşluğunu değiştirme** için giriş noktasıdır. Bir `Document` örneği olmadan dipnot ayırıcıya veya herhangi bir paragraf biçimine ulaşamazsınız.

## Adım 2: Dipnot Ayırıcıyı Alıp Düzenleme (Dipnot Ayırıcıyı Ayarlama)

Dipnot ayırıcı, ana metin ile dipnot listesi arasında yer alan gizli bir paragraftır. Satır aralığını değiştirmek için o paragrafı alıp biçimini ayarlamanız gerekir.

```java
private static void adjustFootnoteSeparator(Document doc) throws Exception {
    // Get the footnote separator (the first one is usually the default separator)
    FootnoteSeparator separator = doc.getFootnoteSeparator();
    
    // If the document has no separator (rare), create one
    if (separator == null) {
        separator = new FootnoteSeparator(doc);
        doc.getFootnotes().add(separator);
    }
    
    // Access the underlying paragraph and set line spacing
    Paragraph sepParagraph = separator.getSeparatorParagraph();
    ParagraphFormat fmt = sepParagraph.getParagraphFormat();
    
    // Set line spacing to 12 points – this is the core of "change footnote spacing"
    fmt.setLineSpacing(12.0);
    
    // Optional: also adjust spacing before/after if needed
    fmt.setSpaceBefore(0);
    fmt.setSpaceAfter(0);
}
```

### Bu sorunu nasıl çözüyor

- **Dipnot ayırıcıyı al** – bu, aslında değiştirmek istediğiniz parçadır ve *dipnot ayırıcıyı ayarlama* gereksinimini karşılar.
- **Satır aralığını ayarla** – `setLineSpacing(12.0)` gizli paragraf için *boşluk nasıl ayarlanır* sorusuna doğrudan yanıt verir.
- **Köşe durumlarını ele al** – belge bir şekilde ayırıcı içermiyorsa, anında bir tane oluştururuz ve `NullPointerException` oluşmasını önleriz.

## Adım 3: Değişikliği Doğrulama ve Kaydetme (Paragraf Satır Aralığını Ayarlama)

Ayırıcıyı değiştirdikten sonra, değişikliğin kalıcı olduğundan emin olmak istersiniz. Kaydedilen dosyayı Word'de açmak yeni boşluğu gösterecektir, ancak bunu programlı olarak da kontrol edebilirsiniz.

```java
private static void verifySpacing(Document doc) throws Exception {
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
    System.out.println("Current footnote separator line spacing: " + spacing);
}
```

`main` içinde `doc.save(...)` çağrısından hemen önce `verifySpacing(doc);` satırını ekleyin. Programı çalıştırdığınızda şunu görmelisiniz:

```
Current footnote separator line spacing: 12.0
```

Bu, **docx'te satır aralığını değiştirme** işleminin başarılı olduğunu doğrular.

## Yaygın Tuzaklar ve Uzman İpuçları

- **Tuzak**: `setLineSpacing`'i “12” gibi görünen bir değerle kullanmak, ancak bunun “12 pts” (puan) yerine “12 satır” olarak yorumlanması. Aspose puan bekler, bu yüzden 12 = 12 pt demektir. Çift satır aralığı için `24.0` kullanın.
- **Uzman ipucu**: Tüm dipnot türlerinde (ayırıcı, devam ayırıcı vb.) tutarlı bir görünüm istiyorsanız, aynı adımları `doc.getFootnoteContinuationSeparator()` ve `doc.getFootnoteContinuationNotice()` için de tekrarlayın.
- **Tuzak**: Değişikliklerden sonra `save()` çağırmayı unutmak. Bellekteki belge değişir, ancak disk üzerindeki dosya aynı kalır.
- **Uzman ipucu**: Boşluk değişikliklerini stil güncellemeleri (`ParagraphStyle`) ile birleştirerek tamamen işlenmiş bir dipnot bölümü elde edin.

## Tam Çalışan Örnek (Tüm Adımlar Tek Dosyada)

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the DOCX document
        Document doc = new Document("input.docx");

        // 2️⃣ Adjust the footnote separator – this is where we "change footnote spacing"
        adjustFootnoteSeparator(doc);

        // 3️⃣ Verify the new line spacing (optional but handy for debugging)
        verifySpacing(doc);

        // 4️⃣ Save the result – now your footnotes have the desired spacing
        doc.save("output.docx");
        System.out.println("Footnote spacing updated and saved to output.docx");
    }

    private static void adjustFootnoteSeparator(Document doc) throws Exception {
        FootnoteSeparator separator = doc.getFootnoteSeparator();
        if (separator == null) {
            separator = new FootnoteSeparator(doc);
            doc.getFootnotes().add(separator);
        }
        Paragraph sepParagraph = separator.getSeparatorParagraph();
        ParagraphFormat fmt = sepParagraph.getParagraphFormat();

        // Core operation: "set paragraph line spacing" for the separator
        fmt.setLineSpacing(12.0);   // 12 pt line spacing
        fmt.setSpaceBefore(0);
        fmt.setSpaceAfter(0);
    }

    private static void verifySpacing(Document doc) throws Exception {
        FootnoteSeparator sep = doc.getFootnoteSeparator();
        double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
        System.out.println("Current footnote separator line spacing: " + spacing);
    }
}
```

Yukarıdaki kodu yeni bir Java sınıfına kopyalayın, Aspose.Words Maven bağımlılığını ekleyin ve çalıştırın. `output.docx` dosyanız artık dipnot ayırıcı satır aralığını **12 pt** olarak ayarlayacak ve böylece **dipnot boşluğunu değiştirmiş** olacak.

### Maven Bağımlılığı

`pom.xml` dosyanıza bu snippet'i ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Gradle tercih ediyorsanız eşdeğeri şudur:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## Sonuç

Java kullanarak bir DOCX dosyasında **dipnot boşluğunu değiştirme** yöntemini yeni öğrendiniz. Belgeyi yükleyerek, **dipnot ayırıcıyı** alıp **paragraf satır aralığını ayarlayarak**, dipnotların görünümünü hassas bir şekilde kontrol edebilirsiniz.  

Buradan, dipnot metin stilini değiştirme, özel ayırıcılar ekleme veya birden fazla belge üzerinde toplu güncellemeler otomatikleştirme gibi ilgili ayarlamaları keşfedebilirsiniz.  

**dipnot ayırıcıyı ayarlama** veya diğer Word otomasyon görevleri hakkında daha fazla sorunuz mu var? Yorum bırakın ve kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisin?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Word Belgesinde Asya Paragraf Boşluğu ve Girintilerini Değiştir](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Word Belgesinde Asya Paragraf Boşluğu ve Girintilerini Değiştir](/words/german/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Word Belgesinde Asya Paragraf Boşluğu ve Girintilerini Değiştir](/words/french/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}