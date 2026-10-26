---
category: general
date: 2026-10-26
description: LoadOptions kullanarak Java'da kodlamayı nasıl belirleyeceğinizi öğrenin.
  Bu kılavuz karakter kodlamasını, setEncoding metodunu ve belge yükleme seçeneklerini
  kapsar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to specify encoding
- character encoding in Java
- LoadOptions encoding
- setEncoding method
- document loading options
- Aspose.Words for Java
language: tr
lastmod: 2026-10-26
og_description: Aspose.Words kullanarak Java'da kodlamayı nasıl belirteceğinizi öğrenin.
  Doğru karakter kümesiyle belgeleri yüklemek için bu kapsamlı öğreticiyi izleyin.
og_image_alt: Screenshot showing how to specify encoding in Java LoadOptions
og_title: Aspose.Words ile Java’da kodlamayı nasıl belirtirsiniz – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  headline: How to specify encoding when loading a document with Aspose.Words for
    Java
  type: TechArticle
- description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  name: How to specify encoding when loading a document with Aspose.Words for Java
  steps:
  - name: 5.1 Loading from an `InputStream`
    text: 'Sometimes you receive a document as a stream (e.g., from a web service).
      You can still control the encoding by passing the stream together with `LoadOptions`:'
  - name: 5.2 Fallback when the encoding is unknown
    text: If you cannot determine the source file’s charset, you can attempt a detection
      library (such as ICU4J) before setting the encoding. Once you have a guess,
      invoke `setEncoding` with that value. This approach reduces the risk of mis‑decoded
      text.
  - name: 5.3 Dealing with unsupported encodings
    text: Java supports a wide range of code pages, but a few legacy encodings may
      be missing. In that case, consider converting the file to UTF‑8 externally (e.g.,
      using `iconv`) before loading it with Aspose.Words. After conversion, you can
      omit the `setEncoding` call because UTF‑8 is the default for most m
  type: HowTo
tags:
- Java
- Encoding
- Aspose.Words
title: Aspose.Words for Java ile bir belgeyi yüklerken kodlamayı nasıl belirtirsiniz?
url: /tr/java/document-loading-and-saving/how-to-specify-encoding-when-loading-a-document-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile bir belgeyi yüklerken kodlamayı nasıl belirtirsiniz

Java’da bir kaynak dosya için **kodlamayı nasıl belirtiriz** gerektiğinde, bu öğretici size tam adımları gösterir. Belge Big5, UTF‑8 veya başka bir karakter kümesi kullansın, `LoadOptions` ile okuma sürecini kontrol edebilirsiniz. Kılavuzun sonunda karakter kodlamasının neden önemli olduğunu, `setEncoding` metodunu nasıl uygulayacağınızı ve belgenin doğru yüklendiğini nasıl doğrulayacağınızı anlayacaksınız.

Doğru karakter kodlamasıyla bir belgeyi yüklemek bozuk metin oluşumunu önler ve çok dilli içeriğin amaçlandığı gibi görüntülenmesini sağlar. Bu öğreticide şunlar ele alınmaktadır:

* **Java’da karakter kodlamasının** dosya okurken rolü.
* Aspose.Words için **LoadOptions kodlamasının** nasıl yapılandırılacağı.
* Projenize kopyalayabileceğiniz pratik kod örnekleri.
* Uyumsuz kodlamalar gibi yaygın tuzaklar ve bunların nasıl giderileceği.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* Java Development Kit (JDK) 8 veya üzeri.
* Bağımlılıkları yönetmek için Maven veya Gradle.
* Aspose.Words for Java 23.10 veya daha yeni bir sürüm (bu kılavuzda kullanılan sürüm).
* İstenilen kodlamayla kaydedilmiş bir örnek metin belgesi (`input.doc`) (ör. Big5).

Ek bir kütüphane gerekmez; örnek yalnızca temel Aspose.Words API’sini kullanır.

## Adım 1: Aspose.Words’u projenize ekleyin

Maven kullanıyorsanız, `pom.xml` dosyanıza aşağıdaki bağımlılığı ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Gradle için ise `build.gradle` dosyanıza şu satırı ekleyin:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Kütüphaneyi eklemek, `LoadOptions`, `Document` ve `Encoding` sınıflarını kullanılabilir hâle getirir.

## Adım 2: Bir `LoadOptions` örneği oluşturun

`LoadOptions`, Aspose.Words’un bir dosyayı nasıl açacağını özelleştirmenizi sağlar. **Kodlamayı nasıl belirtiriz** sorusunun ilk adımı nesneyi oluşturmaktır.

```java
// Step 2: Create load options to customize how the document is opened
LoadOptions loadOptions = new LoadOptions();
```

`LoadOptions` nesnesi varsayılan ayarlarla başlar. Özelliklerini bir sonraki adımda ayarlayacağız.

## Adım 3: İstenen karakter kodlamasını ayarlayın

`setEncoding` metodu, yükleyicinin kullanması gereken **Java’da karakter kodlamasını** tanımlar. Bu örnekte geleneksel Çince metin dosyaları için yaygın olan Big5 kod sayfasını seçiyoruz.

```java
// Step 3: Specify the character encoding (Big5) for the source file
loadOptions.setEncoding(Encoding.getEncoding("Big5"));
```

*Neden önemli*: Dosyanın baytları yanlış bir kod sayfası ile yorumlanırsa, karakterler soru işareti ya da anlamsız karakterler olarak görünür. `setEncoding` metodunu açıkça çağırarak Aspose.Words’a bayt akışını Big5 eşleme tablosu ile çözmesini söylersiniz.

`"Big5"` ifadesini, Java’nın tanıdığı herhangi bir karakter kümesi adıyla değiştirebilirsiniz; örneğin `"UTF-8"`, `"ISO-8859-1"` veya `"Windows-1252"`. İsim geçersizse metod `UnsupportedEncodingException` fırlatır; bu yüzden üretim kodunda bu istisna yakalanabilir.

## Adım 4: Yapılandırılmış seçeneklerle belgeyi yükleyin

Artık **LoadOptions kodlaması** ayarlandığına göre, bu seçenekleri `Document` yapıcısına geçirin. Bu adım, **kodlamayı nasıl belirtiriz** iş akışının çekirdek kısmını tamamlar.

```java
// Step 4: Load the document using the configured options
Document doc = new Document("YOUR_DIRECTORY/input.doc", loadOptions);
```

`YOUR_DIRECTORY` ifadesini dosyanızın mutlak ya da göreli yolu ile değiştirin. `Document` örneği artık sağladığınız kodlamayı dikkate alarak tamamen ayrıştırılmış içeriği taşır.

## Adım 5: Metnin doğru yüklendiğini doğrulayın

Kısa bir doğrulama, kodlamanın beklendiği gibi uygulanıp uygulanmadığını kontrol etmenizi sağlar. Belgenin metnini çıkarıp konsola yazdırabilirsiniz:

```java
// Step 5: Output the document text to verify correct decoding
System.out.println(doc.getText());
```

Konsolda okunabilir Çince karakterler (veya beklediğiniz dil) görüyorsanız, kodlama başarılıdır. Hâlâ bozuk çıktı alıyorsanız, orijinal dosyanın kodlamasını yeniden kontrol edin ve karakter kümesi adının tam olarak eşleştiğinden emin olun.

## Yaygın kenar durumlarını ele alma

### 5.1 Bir `InputStream`’den yükleme

Bazen belge bir akış (ör. bir web servisi) olarak gelir. Akışı ve `LoadOptions`’ı birlikte geçirerek yine kodlamayı kontrol edebilirsiniz:

```java
try (InputStream stream = new FileInputStream("YOUR_DIRECTORY/input.doc")) {
    Document docFromStream = new Document(stream, loadOptions);
    System.out.println(docFromStream.getText());
}
```

Aynı **belge yükleme seçenekleri** geçerlidir ve `setEncoding` çağrısı değişmez.

### 5.2 Kodlama bilinmiyorsa geri dönüş yöntemi

Kaynak dosyanın karakter kümesini belirleyemiyorsanız, kodlamayı ayarlamadan önce bir tespit kütüphanesi (ör. ICU4J) kullanabilirsiniz. Bir tahmin elde ettiğinizde, bu değeri `setEncoding` ile geçin. Bu yaklaşım hatalı çözümlenen metin riskini azaltır.

### 5.3 Desteklenmeyen kodlamalarla başa çıkma

Java geniş bir kod sayfası yelpazesi destekler, ancak bazı eski kodlamalar eksik olabilir. Bu durumda dosyayı dışarıda (ör. `iconv` kullanarak) UTF‑8’e dönüştürmeyi düşünün, ardından Aspose.Words ile yükleyin. Dönüştürmeden sonra `setEncoding` çağrısına gerek kalmaz; çünkü UTF‑8 çoğu modern API için varsayılandır.

## İpucu: Toplu işleme için `LoadOptions` nesnesini yeniden kullanın

Aynı karakter kümesini paylaşan birçok belgeyi yüklemeniz gerekiyorsa, tek bir `LoadOptions` örneği oluşturup yeniden kullanın:

```java
LoadOptions sharedOptions = new LoadOptions();
sharedOptions.setEncoding(Encoding.getEncoding("Big5"));

String[] files = {"doc1.doc", "doc2.doc", "doc3.doc"};
for (String file : files) {
    Document d = new Document("YOUR_DIRECTORY/" + file, sharedOptions);
    // Process each document...
}
```

Nesneyi yeniden kullanmak, nesne oluşturma maliyetini azaltır ve toplu işlem boyunca tutarlı kodlamayı garanti eder.

## Tam çalıştırılabilir örnek

Aşağıda tüm adımları birleştiren, gerekli importları içeren ve olası istisnaları ele alan tam program yer almaktadır.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.Encoding;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.UnsupportedEncodingException;

public class LoadDocumentWithEncoding {
    public static void main(String[] args) {
        // Path to the input document
        String inputPath = "YOUR_DIRECTORY/input.doc";

        try {
            // Create LoadOptions and set the desired charset (Big5 in this case)
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setEncoding(Encoding.getEncoding("Big5"));

            // Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Output the document text to verify correct decoding
            System.out.println("Document text:");
            System.out.println(doc.getText());

            // Optional: load from InputStream using the same options
            try (InputStream stream = new FileInputStream(inputPath)) {
                Document docFromStream = new Document(stream, loadOptions);
                System.out.println("Text from stream:");
                System.out.println(docFromStream.getText());
            }

        } catch (UnsupportedEncodingException e) {
            System.err.println("The specified encoding is not supported: " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Error loading document: " + e.getMessage());
        }
    }
}
```

**Beklenen çıktı** (kaynak dosya Big5 ile kodlanmış Çince metin içeriyorsa):

```
Document text:
【此處顯示正確的中文內容】...
Text from stream:
【此處顯示正確的中文內容】...
```

Çıktı okunamaz semboller gösteriyorsa, karakter kümesi adını yeniden gözden geçirin veya dosyanın orijinal kodlamasını doğrulayın.

## Sıkça Sorulan Sorular

**Bu diğer belge formatları (DOCX, RTF, HTML) ile çalışır mı?**  
Evet. Aynı `LoadOptions` nesnesi, Aspose.Words tarafından desteklenen herhangi bir formatta kullanılabilir. Tek şart, dosyanın gerçekten belirtilen karakter kümesini kullanmasıdır.

**Belge yüklendikten sonra kodlamayı değiştirmem gerekirse ne yapmalıyım?**  
Kodlama yalnızca okuma aşamasını etkiler. `Document` nesnesi oluşturulduktan sonra, içsel Unicode temsili orijinal karakter kümesinden bağımsızdır. Çıktı kodlamasını değiştirmek istiyorsanız, dosyayı kaydederken `SaveOptions` ayarlarını düzenleyin.

**Bu yaklaşımı başka kütüphaneler (ör. Apache POI) ile kullanabilir miyim?**  
Apache POI, eski ikili formatlar için kendi karakter kümesi algılamasını yapar, ancak bir yükleyiciye karakter kümesi sağlamanın konsepti benzerdir. Aspose.Words için `LoadOptions`, **kodlamayı nasıl belirtiriz** sorusunun resmi yoludur.

## Sonuç

Artık Aspose.Words for Java ile bir belgeyi yüklerken **kodlamayı nasıl belirtiriz** konusunda bilgi sahibisiniz. Bir `LoadOptions` nesnesi oluşturup `setEncoding` metodunu çağırarak ve bu seçenekleri `Document` yapıcısına geçirerek dosyanın baytlarının doğru şekilde yorumlanmasını sağlarsınız. Bu uygulama bozuk metinleri ortadan kaldırır, çok dilli içeriği destekler ve toplu işleme ya da akış‑tabanlı çalışma akışlarıyla sorunsuz entegrasyon sunar.

**Belge yükleme seçenekleri**, **belirli kodlamalarla kaydetme** ve **Java’da Unicode işleme** gibi ilgili konuları keşfederek metin işleme konusundaki uzmanlığınızı derinleştirin. Farklı karakter kümesi adlarıyla deney yapın, PDF dönüşümüyle birleştirin ya da çeşitli kodlamalarda dosya kabul eden bir web servisine entegre edin.

İyi kodlamalar!


## Sonra Ne Öğrenmelisiniz?


Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini hâkim olmanıza ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [How to Convert RTF Text with UTF-8 Encoding in Java Using Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Recover Corrupted DOCX Word Document Using Aspose.Words LoadOptions – Java Guide](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}