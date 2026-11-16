---
category: general
date: 2026-11-15
description: LoadOptions kullanarak Java'da alt çizgi biçimlendirmesini korumak ve
  içe aktarma davranışını kontrol etmek için markdown belgesini nasıl yükleyeceğinizi
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown document
- LoadOptions
- import underline formatting
- Document class
- custom import behavior
language: tr
lastmod: 2026-11-15
og_description: LoadOptions ile Java’da markdown belgesini yükleyin. Alt çizgi biçimlendirmesini
  koruyun ve içe aktarma davranışını sadece birkaç satır kodla ince ayarlayın.
og_image_alt: Screenshot of Java code loading a markdown document with custom LoadOptions
og_title: Java'da markdown belgesini yükle – özel içe aktarma seçenekleri rehberi
schemas:
- author: GroupDocs
  dateModified: '2026-11-15'
  description: Learn how to load markdown document in Java using LoadOptions to preserve
    underline formatting and control import behavior.
  headline: How to load markdown document in Java with custom import options
  type: TechArticle
- description: Learn how to load markdown document in Java using LoadOptions to preserve
    underline formatting and control import behavior.
  name: How to load markdown document in Java with custom import options
  steps:
  - name: Why you need a `LoadOptions` instance
    text: '* **Predictable results** – Without explicit options the parser may drop
      or change formatting. * **Future‑proofing** – Adding new flags later (e.g.,
      handling tables or code blocks) is as simple as setting another property.'
  - name: When to enable this flag
    text: '* Your markdown contains emphasis that relies on underlining (common in
      technical documentation). * You are generating PDFs or HTML where visual fidelity
      matters.'
  - name: Verifying the load
    text: 'You can quickly confirm that the document loaded correctly:'
  - name: Pro tip
    text: 'Always log the effective `LoadOptions` before loading the file. This makes
      debugging easier when the document doesn’t look as expected:'
  type: HowTo
tags:
- Java
- Markdown
- File I/O
title: Java'da özelleştirilmiş içe aktarma seçenekleriyle markdown belgesi nasıl yüklenir
url: /tr/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java'da özel içe aktarma seçenekleriyle markdown belgesi nasıl yüklenir

Belirli biçimlendirmeyi koruyarak **markdown belgesi yüklemeniz** gerektiğinde, bu kılavuz size özlü, üretim‑hazır bir çözüm gösterir. Bir `LoadOptions` örneği yapılandırarak alt çizgi stilinin ve diğer özelliklerin kaynak dosyadan nasıl içe aktarılacağını kontrol edebilirsiniz.

Bu öğretici, bilmeniz gereken her şeyi kapsar: gerekli içe aktarmalar, adım‑adım kod, her ayarın neden önemli olduğu ve kaçınılması gereken yaygın tuzaklar. Harici bir dokümantasyona ihtiyaç yoktur—sadece kopyalayıp yapıştırın ve çalıştırın.

## Önkoşullar

* Java 17 veya daha yeni bir sürüm yüklü.
* `Document` ve `LoadOptions` sağlayan kütüphane (ör. **GroupDocs.Viewer** veya **Aspose.Words** gibi bir markdown işleme SDK'sı). Farklı bir paket kullanıyorsanız içe aktarma ifadelerini ayarlayın.
* `input.md` adlı bir markdown dosyasını, kodunuzdan referans alabileceğiniz bir dizine yerleştirin.

## Adım 1: İçe aktarma davranışını özelleştirmek için bir `LoadOptions` nesnesi oluşturun

```java
// Import the necessary classes from the SDK
import com.example.sdk.LoadOptions;
import com.example.sdk.Document;

// Step 1: Instantiate LoadOptions for fine‑grained control
LoadOptions loadOptions = new LoadOptions();
```

`LoadOptions`, **Document sınıfının** kaynak dosyayı nasıl yorumlayacağını belirten merkezi sınıftır. Bir örnek oluşturarak onlarca bayrağa erişim elde edersiniz—bunlardan biri alt çizgi biçimlendirmesini içe aktarma yeteneğidir.

### Neden bir `LoadOptions` örneğine ihtiyacınız var

* **Tahmin edilebilir sonuçlar** – Açık seçenekler olmadan ayrıştırıcı biçimlendirmeyi atabilir veya değiştirebilir.
* **Geleceğe hazırlık** – Daha sonra yeni bayraklar eklemek (ör. tabloları veya kod bloklarını işlemek) başka bir özelliği ayarlamak kadar basittir.

## Adım 2: Alt çizgi biçimlendirmesinin içe aktarılmasını etkinleştirin

```java
// Step 2: Turn on underline import
loadOptions.setImportUnderlineFormatting(true);
```

`setImportUnderlineFormatting(true)` çağrısı **import underline formatting** bayrağını etkinleştirir. Bu bayrak `true` olduğunda, orijinal markdown'da altı çizili olan tüm metin, ortaya çıkan `Document` nesnesinde aynı stili korur.

### Bu bayrağı ne zaman etkinleştirmelisiniz

* Markdown'ınız alt çizgiye dayalı vurgu içeriyorsa (teknik dokümantasyonda yaygındır).
* Görsel doğruluğun önemli olduğu PDF veya HTML oluşturuyorsanız.

Bu adımı atladığınızda, altı çizili metin düz metin olarak görünecek ve görsel ipuçlarına dayanan okuyucuları şaşırtabilir.

## Adım 3: Yapılandırılmış `LoadOptions` kullanarak markdown dosyasını yükleyin

```java
// Step 3: Load the markdown document with the custom options
Document markdownDoc = new Document("YOUR_DIRECTORY/input.md", loadOptions);
```

`loadOptions` örneğini `Document` yapıcısına geçirerek **Document sınıfına**, `input.md` dosyasını okurken özel içe aktarma kurallarını uygulaması talimatını verirsiniz.

### Yüklemeyi doğrulama

Belgenin doğru yüklendiğini hızlıca doğrulayabilirsiniz:

```java
System.out.println("Document loaded. Page count: " + markdownDoc.getPageCount());
```

Dosya eksikse veya yol yanlışsa, yapıcı bilgilendirici bir istisna fırlatır ve hatayı nazikçe ele almanızı sağlar.

## Tam, çalıştırılabilir örnek

Aşağıda, olduğu gibi derleyip çalıştırabileceğiniz tam bir program bulunmaktadır (paket adını SDK'nıza uygun olanla değiştirin).

```java
import com.example.sdk.LoadOptions;
import com.example.sdk.Document;

public class LoadMarkdownExample {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions to customize import behavior
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable importing of underline formatting from the source
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the markdown document using the configured options
        try {
            Document markdownDoc = new Document("YOUR_DIRECTORY/input.md", loadOptions);
            System.out.println("Markdown document loaded successfully.");
            System.out.println("Page count: " + markdownDoc.getPageCount());
        } catch (Exception e) {
            System.err.println("Failed to load markdown document: " + e.getMessage());
        }
    }
}
```

**Beklenen çıktı (dosya mevcut ve en az bir sayfa içerik içeriyorsa):**

```
Markdown document loaded successfully.
Page count: 1
```

Dosya bulunamazsa, aşağıdaki gibi bir hata mesajı görürsünüz:

```
Failed to load markdown document: File not found: YOUR_DIRECTORY/input.md
```

## Kenar durumları ve en iyi uygulama ipuçları

| Durum | Dikkat edilmesi gereken | Önerilen yaklaşım |
|-----------|-------------------|----------------------|
| **Dosya yolu boşluk içeriyor** | `new Document("C:/My Docs/input.md", ...)` bazı işletim sistemlerinde kırılabilir. | `java.nio.file.Paths` kullanarak yolu güvenli bir şekilde oluşturun: `Paths.get("C:", "My Docs", "input.md").toString()` |
| **Büyük markdown dosyaları** | Çok büyük dosyaların yüklenmesi bellek tüketebilir. | SDK bunu sağlıyorsa akış seçeneklerini etkinleştirin veya JVM yığınını (`-Xmx`) artırın. |
| **Alt çizgi desteği eksik** | Bazı SDK sürümleri alt çizgi bayrağını görmezden gelir. | `setImportUnderlineFormatting` uygulayan bir sürüm kullandığınızı doğrulayın. Sürüm notlarını kontrol edin. |
| **Birden fazla içe aktarma bayrağı gerekli** | Tabloları, kod bloklarını vb. korumanız da gerekebilir. | `loadOptions` üzerinde ek ayarlayıcıları zincirleyin, ör. `loadOptions.setImportTables(true);` |

### Pro ipucu

Dosyayı yüklemeden önce etkili `LoadOptions` değerlerini her zaman günlüğe kaydedin. Belge beklendiği gibi görünmediğinde hata ayıklamayı kolaylaştırır:

```java
System.out.println("Import underline formatting: " + loadOptions.isImportUnderlineFormatting());
```

## Görsel genel bakış

![Özel LoadOptions ile bir markdown belgesi yükleyen Java kodunun ekran görüntüsü](load-markdown.png)

*Alt metin: Özel LoadOptions ile bir markdown belgesi yükleyen Java kodunun ekran görüntüsü.*

## Sonuç

Artık Java'da **markdown belgesi yükleme** işlemini alt çizgi stilini koruyarak ve `LoadOptions` aracılığıyla **özel içe aktarma davranışı** uygulayarak nasıl yapacağınızı biliyorsunuz. Üç adımlı desen—`LoadOptions` oluşturma, istenen bayrakları etkinleştirme ve seçenekleri `Document` yapıcısına geçirme—diğer birçok içe aktarma ayarına da uygulanabilir.

Buradan `setImportTables` gibi ek bayrakları keşfedebilir, yüklenen `Document`'i bir PDF dönüştürücü ile birleştirebilir veya belgeyi bir web görüntüleyiciye gömebilirsiniz. Aynı yaklaşım SDK'nın desteklediği diğer dosya türleri için de çalışır ve bu deseni Java araç setinizde çok yönlü bir araç haline getirir.

--- 

*Sonraki adımlar:*  

* Yüklenen `Document`'i **PDF** veya HTML olarak **dışa aktarmayı** öğrenin.  
* Markdown ayrıştırmasını ince ayarlamak için `LoadOptions` özelliklerinin tam listesini keşfedin.  
* Üretim seviyesindeki uygulamalar için hata yönetimi ve günlük kaydı entegrasyonu yapın.

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanıza ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Java'da markdown alt çizgi yükleme – tam programlama rehberi](/words/english/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/)
- [Java'da Markdown Yükleme – Tam Rehber](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)
- [Aspose.Words ile Java'da bir Markdown dosyasını okuma ve yükleme](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}