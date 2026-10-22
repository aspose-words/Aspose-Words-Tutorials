---
category: general
date: 2026-08-07
description: Aspose.Words ile Java’da dipnotu nasıl düzenlersiniz – özel tire ekleyin,
  dipnot çizgisini değiştirin ve cilalı belgeler için paragraf hizalamasını ayarlayın.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: tr
lastmod: 2026-08-07
og_description: Java'da Aspose.Words ile dipnotu nasıl düzenlersiniz. Özel bir tire
  eklemeyi, dipnot çizgisini değiştirmeyi ve paragraf hizalamasını sadece birkaç adımda
  öğrenin.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Java'da dipnotu nasıl düzenlenir – tire ekle, satırı değiştir, hizalamayı
  ayarla
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Java'da Aspose.Words ile dipnot nasıl düzenlenir
url: /tr/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java ile Aspose.Words'da dipnotu nasıl düzenlenir

Eğer Java kullanarak bir Word belgesinde **dipnotu nasıl düzenleyeceğinizi** öğrenmek istiyorsanız, bu rehber tam süreci gösterir. Özel bir tire eklemeyi, dipnot satırını değiştirmeyi ve paragraf hizalamasını ayarlamayı öğrenecek ve dipnot ayırıcıyı profesyonel bir görünüme kavuşturacaksınız.

Dipnotları düzenlemek, yasal sözleşmeler, akademik makaleler veya pazarlama broşürleri hazırlarken sıkça karşılaşılan bir gereksinimdir. Aşağıdaki adımlar belgeyi yüklemekten son dosyayı kaydetmeye kadar ihtiyacınız olan her şeyi kapsar; ek bir araç gerektirmez.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* Java 17 veya daha yeni bir sürüm yüklü.
* Aspose.Words for Java (en son sürüm) projenizin sınıf yoluna eklenmiş.
* En az bir dipnot içeren bir DOCX dosyası (`input.docx`).

Bu öğeler, kodun çalışma zamanı hatası almadan çalışmasını garanti eder.

## Dipnot ayırıcı ve satırını nasıl düzenlenir

Dipnot ayırıcı, ana metin ile dipnot listesinin arasında görünen paragraftır. Görünümünü değiştirmek okunabilirliği artırır ve kurumsal kimliğe uygun hale getirir.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Her satırın önemi

1. **Belgeyi yükleme** – `new Document(...)` DOCX dosyasını belleğe okur ve tüm düğümlere erişmenizi sağlar.
2. **Ayırıcıyı alma** – `getFootnoteSeparator()` Aspose.Words'in dipnot satırı olarak gördüğü özel paragrafı döndürür. Bu nesne, ayırıcıyı güvenle değiştirebileceğiniz tek yerdir.
3. **Paragraf hizalamasını ayarlama** – `setAlignment(ParagraphAlignment.CENTER)` satırın hizalamasını değiştirir. *set paragraph alignment* anahtar kelimesi doğrudan ayırıcıya uygulanır ve ortalanmış bir tire sağlar.
4. **Özel bir tire ekleme** – Mevcut run'ları temizleyip `Run` nesnesiyle em‑dash karakterini (`—`) ekleyerek *add custom dash* etkisini elde eder ve aynı zamanda *change footnote line* işlemini istediğiniz stile dönüştürürsünüz.
5. **Belgeyi kaydetme** – `doc.save(...)` değişiklikleri diske yazar ve tüm modifikasyonları yansıtan bir çıktı dosyası üretir.

## Dipnot ayırıcıya özel bir tire ekleme

**Adım 4**'teki kod, *add custom dash* tekniğini gösterir. Em‑dash yerine `"***"` veya `"---"` gibi herhangi bir dizeyi kullanarak belgenizin görsel diline uygun hale getirebilirsiniz.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Varsayılan ince çizgi marka yönergelerine uymadığında özel bir tire kullanmak özellikle faydalıdır.

## Dipnot satırının stilini değiştirme

Katı bir çizgi tercih ediyorsanız, bir Unicode kutu‑çizim karakteri ya da tekrarlanan alt çizgi ekleyebilirsiniz.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

*change footnote line* adımı, seçtiğiniz karakter ne olursa olsun aynı şekilde çalışır; çünkü ayırıcı paragraf yalnızca içinde bulunan metni render eder.

## Dipnot ayırıcı için paragraf hizalamasını ayarlama

*set paragraph alignment* işlemi sadece ortalanma ile sınırlı değildir. İhtiyacınıza göre sola, sağa ya da iki yana yaslayabilirsiniz.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

Ayırıcıyı sağa hizalamak, çift dilli yayınlar gibi sağa hizalanmış dipnotlar kullanan belgeler için yararlı olabilir.

## Tam, çalıştırılabilir örnek

Aşağıda tüm kavramları birleştiren tam program yer alıyor – belgeyi yükleme, dipnot ayırıcıyı düzenleme, özel bir tire ekleme, satır stilini değiştirme ve hizalamayı ayarlama.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Beklenen çıktı:** `output.docx` dosyası, orijinal ince çizginin bulunduğu yerde ortalanmış bir em‑dash içerir. Tüm dipnotlar bozulmadan kalır ve belgenin düzeni yeni ayırıcı stilini yansıtır.

## Yaygın tuzaklar ve nasıl önlenir

| Sorun | Sebep | Çözüm |
|-------|--------|-----|
| Ayırıcı bulunamadı | Belge dipnot içermiyor veya özel bir dipnot stili kullanıyor | `getFootnoteSeparator()` çağrılmadan önce kaynak DOCX'in en az bir dipnot içerdiğinden emin olun |
| Özel tire görünmüyor | Yazı tipi seçilen karakteri desteklemiyor | Belgenin varsayılan yazı tipi tarafından desteklenen bir Unicode karakteri kullanın veya uyumlu bir yazı tipi gömün |
| Hizalama değişmemiş görünüyor | Paragraf formatı kodda daha sonra üzerine yazılıyor | Hizalamayı, sıfırlayabilecek diğer biçimlendirme çağrılarından **sonra** uygulayın |

Bu noktaları ele almak çalışma zamanı hatalarını önler ve *dipnotu nasıl düzenleyeceğiniz* sürecinin güvenilir bir şekilde çalışmasını sağlar.

## Sonraki adımlar

Artık **dipnotu nasıl düzenleyeceğinizi** bildiğinize göre ilgili görevleri keşfedebilirsiniz:

* **Özel dipnot referans stili ekleme** – `FootnoteReference` düğümlerini değiştirerek numaralandırmayı veya sembolleri özelleştirin.
* **Programatik olarak yeni dipnotlar ekleme** – dinamik içerik için `DocumentBuilder.insertFootnote()` kullanın.
* **Koşullu biçimlendirme uygulama** – dipnot görünümünü paragraf stili veya içerik uzunluğuna göre değiştirin.

Bu uzantıların her biri, *add custom dash*, *change footnote line* ve *set paragraph alignment* işlemlerinde kullandığınız aynı API yüzeyine dayanır.

---

*Keyifli kodlamalar! Eğitim, dipnot düzenleme konusunda size yardımcı olduysa, ekibiyle paylaşmayı veya örneği daha da iyileştirmek için bir pull request göndermeyi düşünün.*

## Sonra Ne Öğrenmelisiniz?


Aşağıdaki eğitimler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Set Footnote And End Note Position](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}