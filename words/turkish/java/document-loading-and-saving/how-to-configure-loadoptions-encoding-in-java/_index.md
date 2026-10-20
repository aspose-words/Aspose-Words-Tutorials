---
category: general
date: 2026-10-20
description: Java'da LoadOptions kodlamasını yapılandırarak belgeleri doğru şekilde
  okuyun ve Aspose.Words ile belge kodlamasını UTF‑8'e değiştirin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- configure LoadOptions encoding
- change document encoding to utf-8
- Aspose.Words Java encoding
- Java document conversion
- character set handling Java
language: tr
lastmod: 2026-10-20
og_description: Java'da LoadOptions kodlamasını yapılandırarak doğru karakter işleme
  sağlayın ve Aspose.Words kullanarak belge kodlamasını UTF-8'e nasıl değiştireceğinizi
  öğrenin.
og_image_alt: Screenshot showing Java code that configures LoadOptions encoding and
  saves a document
og_title: Java'da LoadOptions kodlamasını yapılandırma – tam rehber
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Configure LoadOptions encoding in Java to correctly read documents
    and change document encoding to UTF-8 with Aspose.Words.
  headline: How to configure LoadOptions encoding in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Encoding
title: Java'da LoadOptions kodlamasını nasıl yapılandırılır
url: /tr/java/document-loading-and-saving/how-to-configure-loadoptions-encoding-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java'da LoadOptions kodlamasını yapılandırma

Java'da **LoadOptions kodlamasını yapılandırmanız** gerektiğinde, bu kılavuz doğru karakter kümesini nasıl ayarlayacağınızı ve ardından **belgenin kodlamasını UTF-8'e** nasıl değiştireceğinizi Aspose.Words kullanarak gösterir. Doğru kodlama, Big5, Shift_JIS veya Windows‑1252 gibi eski kod sayfalarını kullanan dosyaları yüklerken bozuk metin oluşmasını önler.

Şunları öğreneceksiniz:

* belirli bir kodlama ile bir `LoadOptions` örneği oluşturma,
* bu kodlamayı kullanan bir kaynak belgeyi yükleme,
* belgeyi farklı bir kodlamada (UTF‑8) veri kaybı olmadan kaydetme,
* dönüşümün başarılı olduğunu doğrulama.

Bu öğretici, temel bir Java geliştirme ortamına ve geçerli bir Aspose.Words for Java lisansına sahip olduğunuzu varsayar. Harici araçlara ihtiyaç yoktur.

## Önkoşullar

| Gereksinim | Neden Önemlidir |
|-------------|----------------|
| Java 17 veya daha yeni bir sürüm | Modern dil özellikleri ve uzun vadeli destek sağlar. |
| Aspose.Words for Java (v23.9 veya daha yeni) | `LoadOptions` sınıfı bu kütüphanede bulunur. |
| Eski bir kod sayfası ile kodlanmış bir kaynak belge (ör. Big5) | Özel kodlamanın gerekliliğini gösterir. |
| Bir IDE veya derleme aracı (Maven/Gradle) | Örneğin derlenip çalıştırılmasını kolaylaştırır. |

Maven kullanıyorsanız `pom.xml` dosyanıza Aspose.Words bağımlılığını ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## LoadOptions kodlamasını yapılandırma

İlk adım, Aspose.Words'ün dosyayı okurken hangi karakter kümesini beklemesi gerektiğini söylemektir. Bu, `LoadOptions` nesnesini yapılandırarak yapılır.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import java.nio.charset.Charset;

// Step 1: Create LoadOptions and set the desired encoding (Big5 in this example)
LoadOptions loadOptions = new LoadOptions();
loadOptions.setEncoding(Charset.forName("Big5"));
```

**Neden Önemlidir:** Bir belge eski bir kodlamayla kaydedildiğinde, varsayılan yükleyici UTF‑8 varsayar. Kodlamayı açıkça ayarlayarak bozuk karakterlerin (mojibake) oluşmasını önler ve orijinal metni korursunuz.

### Pro ipucu
Bir dosyanın hangi kodlamayı kullandığından emin değilseniz, bayt sırası işaretçisini (BOM) inceleyebilir veya belge sağlayıcıdan bilgi alabilirsiniz. Yaygın eski kodlamalar arasında `Big5`, `Shift_JIS` ve `Windows-1252` bulunur.

## Belgeyi yapılandırılmış seçeneklerle yükleme

`LoadOptions` hazır olduğuna göre, kaynak dosyayı yükleyin. Dosya yolunu ve bir `LoadOptions` örneğini kabul eden yapıcı, özel kodlamanın uygulanmasını sağlar.

```java
// Step 2: Load the document using the configured LoadOptions
String sourcePath = "C:/Docs/big5_doc.docx";
Document doc = new Document(sourcePath, loadOptions);
```

**Neden Önemlidir:** `Document` nesnesi artık orijinal dosyada göründüğü gibi metni içerir, çünkü yükleyici sağladığınız Big5 kod sayfasına saygı gösterdi.

## Belge kodlamasını UTF-8'e değiştirme

Aspose.Words metni dahili olarak Unicode tutar, bu yüzden belgeyi kaydetme işlemi dış kodlamayı belirler. UTF‑8 bir dosya üretmek için ek bir kodlama belirtmeden kaydedin—UTF‑8, modern Office Open XML formatları için varsayılandır. Ancak açıklık sağlamak amacıyla bunu açıkça belirtebilirsiniz.

```java
// Step 3: Save the document using UTF-8 encoding (default for .docx)
String outputPath = "C:/Docs/Converted.docx";
doc.save(outputPath);
```

Düz metin (ör. `.txt`) temsili oluşturmanız ve UTF‑8 kullanmanız gerekiyorsa, bir `SaveOptions` nesnesi geçirin:

```java
import com.aspose.words.TxtSaveOptions;

// Save as UTF-8 encoded plain text
TxtSaveOptions txtOptions = new TxtSaveOptions();
txtOptions.setEncoding(Charset.forName("UTF-8"));
doc.save("C:/Docs/Converted.txt", txtOptions);
```

**Neden Önemlidir:** UTF‑8 olarak kaydetmek, herhangi bir downstream sistemin—web servisleri, veritabanları veya modern editörlerin—dosyayı ek bir dönüşüm adımı olmadan okuyabilmesini garanti eder.

## Dönüşümü doğrulama

Kodlama değişikliğinin başarılı olduğunu hızlıca doğrulamanın bir yolu, kaydedilen dosyayı bir UTF‑8 okuyucu ile tekrar okuyup birkaç karakteri yazdırmaktır.

```java
import java.nio.file.Files;
import java.nio.file.Paths;

byte[] utf8Bytes = Files.readAllBytes(Paths.get(outputPath));
String content = new String(utf8Bytes, Charset.forName("UTF-8"));
System.out.println("First 200 characters of the converted file:");
System.out.println(content.substring(0, Math.min(200, content.length())));
```

Eğer çıktı okunabilir karakterler (� simgesi olmadan) gösteriyorsa, dönüşüm beklendiği gibi çalışmıştır.

## Tam çalıştırılabilir örnek

Aşağıda tüm adımları bir araya getiren bağımsız bir program yer alıyor. Dosya yollarını kendi konumlarınızla değiştirin.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.TxtSaveOptions;
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Paths;

public class EncodingDemo {
    public static void main(String[] args) throws Exception {
        // 1. Configure LoadOptions with the source encoding (Big5)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setEncoding(Charset.forName("Big5"));

        // 2. Load the legacy‑encoded document
        String sourcePath = "C:/Docs/big5_doc.docx";
        Document doc = new Document(sourcePath, loadOptions);

        // 3. Save as UTF‑8 encoded .docx (default) and .txt for verification
        String docxOutput = "C:/Docs/Converted.docx";
        doc.save(docxOutput); // UTF‑8 by default

        String txtOutput = "C:/Docs/Converted.txt";
        TxtSaveOptions txtOptions = new TxtSaveOptions();
        txtOptions.setEncoding(Charset.forName("UTF-8"));
        doc.save(txtOutput, txtOptions);

        // 4. Verify the .txt file content
        byte[] utf8Bytes = Files.readAllBytes(Paths.get(txtOutput));
        String content = new String(utf8Bytes, Charset.forName("UTF-8"));
        System.out.println("First 200 characters of the UTF‑8 text file:");
        System.out.println(content.substring(0, Math.min(200, content.length())));
    }
}
```

**Beklenen çıktı**

```
First 200 characters of the UTF-8 text file:
[Readable Chinese characters from the original Big5 document...]
```

Karakterler doğru görünüyorsa, **LoadOptions kodlamasını yapılandırdı** ve **belge kodlamasını UTF-8'e değiştirdiniz**.

## Yaygın tuzaklar ve nasıl önlenir

| Belirti | Neden | Çözüm |
|---------|-------|-----|
| Yükleme sonrası bozuk karakterler | `LoadOptions` ayarlanmamış veya yanlış charset adı | `loadOptions.setEncoding(Charset.forName("Big5"))` ifadesinin kaynak dosyanın kod sayfasıyla eşleştiğinden emin olun. |
| `UnsupportedEncodingException` | Charset adının yanlış yazılması | `Charset.availableCharsets()` içinde listelenen tam adı kullanın. |
| Çıktı dosyası hâlâ mojibake gösteriyor | UTF‑8 seçenekleri olmadan eski bir format (ör. `.rtf`) ile kaydedildi | `TxtSaveOptions` ile `setEncoding("UTF-8")` kullanın veya `.docx` olarak kaydedin. |
| Büyük dosyalarda performans yavaşlaması | Her belge için yeni `LoadOptions` oluşturulması | Aynı kaynak kodlamasını kullanan birçok dosya işlenirken tek bir `LoadOptions` örneği yeniden kullanın. |

## Sonuç

Artık Java'da **LoadOptions kodlamasını yapılandırarak** eski kodlamalı belgeleri okuyabilir ve **belge kodlamasını UTF-8'e değiştirerek** güvenli downstream tüketimi sağlayabilirsiniz. Bu yaklaşım, Java’nın `Charset` sınıfı tarafından desteklenen herhangi bir kod sayfası için çalışır ve çok dilli uygulamalar için esnek bir çözümdür.

İleride şunları keşfedebilirsiniz:

* **Toplu dönüşüm** – bir klasördeki belgeler üzerinde aynı kodlama mantığını döngüyle uygulama.
* **Kodlama tespiti** – `juniversalchardet` gibi kütüphanelerle kaynak charset’i otomatik algılayıp `LoadOptions` yapılandırma.
* **Biçim koruma** – UTF‑8 uyumluluğunu korurken PDF veya HTML olarak kaydetmeyi deneme.

Kodu projenizin mimarisine göre uyarlamaktan çekinmeyin ve güçlü Aspose.Words API’sinin belge manipülasyonu işini sizin yerinize yapmasına izin verin.

![Code snippet showing configuration of LoadOptions encoding and document save](/images/encoding-demo.png){: .align-center alt="Java kod örneğinde LoadOptions kodlamasını yapılandırma ve belge kaydetme"}

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımları keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words for Java'da LoadOptions Nasıl Ayarlanır](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words Kullanarak Java'da UTF-8 Kodlamalı RTF Metni Nasıl Dönüştürülür](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Aspose.Words LoadOptions – Java Rehberi ile Bozuk DOCX Word Belgesi Nasıl Kurtarılır](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}