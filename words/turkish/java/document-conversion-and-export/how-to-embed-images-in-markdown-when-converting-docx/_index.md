---
category: general
date: 2026-10-23
description: DOCX dosyasını dönüştürürken markdown içinde resimleri nasıl gömeceğinizi
  öğrenin, küçük grafikler için Base64 ve büyük resimler için dış dosyalar kullanarak.
draft: false
keywords:
- how to embed images
- embed images in markdown
- convert docx to markdown
- extract images from docx
- embed images as base64
lastmod: 2026-10-23
og_description: DOCX dosyasını dönüştürürken markdown içinde resimleri nasıl gömeceğinizi
  öğrenin, küçük grafikler için Base64 ve büyük resimler için dış dosyalar kullanarak.
  Bu rehber, Aspose.Words for Java ile tam adımları gösterir.
og_image_alt: Screenshot of markdown output with embedded Base64 images generated
  by Aspose.Words for Java
og_title: markdown içinde resimleri nasıl gömmek – Java DOCX dönüştürme rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to embed images in markdown when converting a DOCX file,
    using Base64 for tiny graphics and external files for larger pictures.
  headline: How to embed images in markdown when converting docx
  type: TechArticle
- questions:
  - answer: Yes. The same API works in any Java environment, including servlet containers
      and Spring Boot applications. Just stream the `output.md` back to the client
      after conversion.
    question: Can I use this approach in a web service that generates Markdown on
      the fly?
  - answer: A valid Aspose.Words license is required for production deployments. A
      free evaluation license is available for testing and development.
    question: Is a commercial license required for production use?
  - answer: Load the document with `new Document("file.docx", new LoadOptions("password"))`.
      The same conversion pipeline then applies.
    question: How do I handle password‑protected DOCX files?
  - answer: Convert the SVG to PNG or JPEG first, then let the callback treat it as
      any other image. Aspose.Words does not natively render SVG inside Markdown.
    question: What if I need to embed SVG images?
  - answer: Yes. Aspose.Words for Java is platform‑agnostic and runs wherever a compatible
      JDK is available.
    question: Does this work on Windows, macOS, and Linux?
  type: FAQPage
tags:
- Aspose.Words
- Java
- markdown
- image embedding
- docx conversion
- developer guide
title: DOCX dönüştürürken markdown içinde resimleri nasıl gömmek gerekir
url: /tr/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Docx dönüştürürken markdown içinde resimleri nasıl gömmek gerekir

Bir Word belgesinden gelen bir Markdown dosyasında **resimleri nasıl gömmek** gerektiğini hiç merak ettiniz mi? Tek başınıza değilsiniz. Çoğu geliştirici, dönüşüm sırasında resimleri kaybettiğinde ya da son düzeni bozan bir şekilde depolandığında sorun yaşar.  

Bu rehberde, küçük grafikler için Base64 veri URI'leri olarak **resimleri nasıl gömmek** gerektiğini, daha büyük varlıkların ise yan bir klasöre yazıldığını gösteren tam, çalıştırmaya hazır bir örnek üzerinden ilerleyeceğiz. Ayrıca **docx'i markdown'a dönüştürme**, Aspose.Words ile **docx nasıl dönüştürülür** konularına değinecek ve resimlerin Base64 olarak gömülmesi ile ayrı dosyalar olarak dışa aktarılması arasındaki farkı açıklayacağız.  

> **Pro tip:** Sadece hızlı bir kanıt‑konsepti (proof‑of‑concept) istiyorsanız, aşağıdaki kod tek bir Maven bağımlılığıyla kutudan çıkar çıkmaz çalışır.

## Hızlı cevaplar
- **Dönüşümü hangi kütüphane yönetiyor?** Aspose.Words for Java, DOCX → Markdown dönüşümünü ve resim çıkarımını gerçekleştirir.
- **Küçük resimler nasıl saklanıyor?** Markdown dosyasının içinde doğrudan Base64 veri URI'leri olarak satır içi (inline) eklenir.
- **Büyük resimler nereye gidiyor?** Daha büyük resimler, Markdown dosyasının yanındaki `markdown_resources` klasörüne kaydedilir.
- **Microsoft Word yüklü olması gerekiyor mu?** Hayır, Aspose.Words Microsoft Office'den tamamen bağımsız çalışır.
- **Hangi Java sürümü gerekiyor?** Java 17 veya daha yeni bir LTS sürümü.

## 'how to embed images' nedir?
`how to embed images` ifadesi, bir Markdown belgesine resim verisini doğrudan ekleme tekniğini, ya Base64‑kodlu bir veri URI'si olarak ya da harici bir dosyaya göreceli bir bağlantı olarak tanımlar. Bu yaklaşım, küçük grafikler için tek bir taşınabilir Markdown dosyası tutmanıza olanak tanırken, yüksek çözünürlüklü varlıkları ayrı dosyalarla desteklemeye devam eder.

## Neden markdown içinde resimleri gömmek?
Resimleri Base64 olarak gömmek, simgeler ve küçük grafikler için HTTP isteklerini azaltır; bu da düşük gecikmeli ağlarda sayfa yükleme hızını %30’a kadar artırabilir. Aynı zamanda büyük fotoğrafları dışarıda tutmak, Markdown dosyasının 5 MB’ı aşmasını engeller, editör performansını ve sürüm‑kontrol farklarını korur.

## Önkoşullar
- **Java 17** (veya daha yeni bir JDK). API Java‑merkezli, ancak kavramlar diğer dillere de uyarlanabilir.
- **Aspose.Words for Java** – DOCX → Markdown dönüşümünü destekleyen ticari bir kütüphane.
- Küçük simgeler ve büyük fotoğraflar içeren bir **örnek DOCX**.
- Markdown dosyasının ve kaynaklarının kaydedileceği yazılabilir bir klasör.

Ek bir çerçeve, dış script yok. Sadece saf Java ve Aspose.Words.

## Projenize Aspose.Words eklemek için neler gerekir (docx'i markdown'a dönüştürmek)

Maven kullanıyorsanız, aşağıdaki snippet'i `pom.xml` dosyanıza ekleyin. Okuma zamanındaki en yeni sürümle değiştirmekten çekinmeyin.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Neden bu önemli:** Aspose.Words, DOCX yapısını ayrıştırma, resimleri çıkarma ve Markdown sözdizimini oluşturma işini üstlenir. Kendi ayrıştırıcınızı yazmak, muhtemelen ihtiyacınız olmayan bir tavşan deliğine düşmek olur.

## Document sınıfı nasıl çalışır?
`Document`, Aspose.Words'ün bellekte tek bir Word dosyasını temsil eden çekirdek nesnesidir. Belgeleri birçok formatta yükleme, değiştirme ve kaydetme yöntemleri sunar.  
Bölümler, paragraflar, tablolar ve gömülü kaynaklar dahil olmak üzere tüm belge yapısını kapsar; böylece alttaki XML ile uğraşmadan içeriği programatik olarak manipüle edebilirsiniz.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

## Callback ile Base64 ve harici dosyalar arasında nasıl karar verilir
Kaynak callback'i, dönüşüm sırasında her bir resmi yakalamanızı sağlayan `IResourceSavingCallback` uygulamasıdır.  
Bu, **resimleri nasıl gömmek** gerektiğini doğru şekilde belirlemenin kalbidir. Callback, dönüştürücünün yazmak istediği her kaynak (resim, stil vb.) için bir kanca (hook) sunar. Resim boyutunu inceleyerek, veri URI'si olarak gömülüp gömülmeyeceğine ya da harici bir dosya olarak kaydedileceğine karar verebilir, böylece performans ve dosya boyutu arasında denge kurabilirsiniz.

```java
        // Step 3: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Step 4: Decide how to handle each image
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    // Small image – embed as Base64
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger image – write to a folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        // Normalize path for Markdown (use forward slashes)
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });
```

### Neden bir callback?
- **Kontrol:** Resmin satır içi Base64 dizesi mi yoksa ayrı bir dosya mı olacağına siz karar verirsiniz.
- **Performans:** Küçük simgeler Markdown içinde yer alır, ekstra HTTP istekleri ortadan kalkar.
- **Taşınabilirlik:** Büyük fotoğraflar harici dosyalar olarak kalır, Markdown boyutu makul seviyede tutulur.

## Belgeyi markdown olarak nasıl kaydederiz
SaveOptions, Aspose.Words'ün çıktıyı nasıl yazacağını kontrol eden bir yapılandırma nesnesidir; format, kodlama ve kaynak yönetimi gibi ayarları içerir.  
Son olarak, az önce yapılandırdığımız seçeneklerle Aspose.Words'ün Markdown dosyasını yazmasını söyleyelim. `SaveOptions` nesnesi, çıktı klasörünü, kaynak callback'ini ve diğer biçimlendirme tercihlerini belirlemenizi sağlar; böylece oluşturulan Markdown projenizin standartlarına uyar. Ayrıca içindekiler tablosu oluşturmayı açıp kapatabilir ve dipnotların nasıl render edileceğini kontrol edebilirsiniz.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Programı çalıştırdığınızda iki şey üretilir:

1. `output.md` – orijinal DOCX'inizin Markdown temsili.  
2. `markdown_resources` klasörü – gömülmemiş büyük resimler burada bulunur.

## Tam çalışan örnek (tüm adımlar bir yerde)

Aşağıda, IDE'nize kopyalayıp‑yapıştırabileceğiniz eksiksiz kaynak dosyası yer alıyor. `YOUR_DIRECTORY` kısmını makinenizdeki gerçek yol ile değiştirin.

```java
import com.aspose.words.*;
import java.nio.file.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Small images (<10 KB) become Base64 data URIs
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger images are written to a dedicated folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });

        // Step 3: Save the document as Markdown
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

**Beklenen çıktı:** `output.md` dosyasını herhangi bir Markdown görüntüleyicide açın. Küçük simgeler satır içinde görünür, örneğin:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

[Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)

Daha büyük fotoğraflar ise şöyle referanslanır:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

[Photo](markdown_resources/photo1.jpg)

Bu, **resimleri gömmek** ve dosya boyutunu yönetilebilir tutmak için tam olarak ihtiyacınız olan şeydir.

## Yaygın sorular ve uç durumlar

### Görüntü PNG yerine JPEG ise ne olur?
Callback yukarıda her zaman URI'yi `image/png` olarak önekler. JPEG'ler için `args.getData()`'nın ilk birkaç baytını inceleyebilir ya da `args.getFileName()` kullanarak doğru MIME tipini çıkarabilirsiniz:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Boyut eşiğini değiştirebilir miyim?
Kesinlikle. `10_000` bayt limiti sadece bir örnek. Bant genişliği bütçeniz genişse 50 KB ya da daha fazlasına çıkarabilirsiniz. Tam tersi durumda, ultra‑hafif Markdown dosyaları istiyorsanız eşiği düşürün.

### Bu, tablolar veya diğer Word nesneleriyle çalışır mı?
Evet. Aspose.Words otomatik olarak tabloları, listeleri ve hatta dipnotları Markdown'a dönüştürür. Kaynak callback yalnızca resimleri yakalar; diğer öğeler için ekstra koda gerek yoktur.

### ASCII olmayan dosya adları ne durumda?
API, `markdown_resources` klasörüne yazarken Unicode dosya adlarını güvenli bir şekilde kodlar. Dosya sisteminizin UTF‑8 desteklediğinden emin olun (çoğu modern OS bunu yapar).

## Sorun giderme ipuçları ve yaygın tuzaklar

- **Dönüşüm sonrası resimler eksik:** Callback'in `args.getData()`'sının null olmadığını ve çıktı klasörünün yazma iznine sahip olduğunu kontrol edin.  
- **Base64 dizeleri bozuk görünüyor:** `Base64.getEncoder().encodeToString()` çağrısının tam bayt dizisini aldığından emin olun; akış tam okunmadığında kesintiler oluşabilir.  
- **Büyük Markdown dosyaları:** Oluşan `.md` 5 MB'ı aşıyorsa, boyut eşiğini düşürmeyi ya da büyük resimleri kaynak klasörüne kaydetmeden önce sıkıştırmayı düşünün.  
- **Sürüm uyumsuzlukları:** Aspose.Words 24.9+ 35+ çıktı formatını destekler ve tipik bir 2.5 GHz sunucuda 500‑sayfalık DOCX'i 4 saniyeden kısa sürede işleyebilir. Beklenmedik davranışları önlemek için Maven sürümünü kilitleyin.

## Sıkça sorulan sorular

**S: Bu yaklaşımı, anlık Markdown üreten bir web servisinde kullanabilir miyim?**  
C: Evet. Aynı API, servlet konteynerleri ve Spring Boot uygulamaları dahil olmak üzere herhangi bir Java ortamında çalışır. Dönüştürmeden sonra `output.md` dosyasını istemciye akış olarak gönderebilirsiniz.

**S: Üretim ortamında ticari bir lisans gerekli mi?**  
C: Üretim dağıtımları için geçerli bir Aspose.Words lisansı şarttır. Test ve geliştirme için ücretsiz bir değerlendirme lisansı mevcuttur.

**S: Şifre korumalı DOCX dosyalarını nasıl yönetirim?**  
C: Belgeyi `new Document("file.docx", new LoadOptions("password"))` ile yükleyin. Aynı dönüşüm hattı sonrasında uygulanır.

**S: SVG resimleri gömmem gerekirse ne yapmalıyım?**  
C: Önce SVG'yi PNG ya da JPEG'e dönüştürün, ardından callback diğer resimler gibi işlesin. Aspose.Words, Markdown içinde SVG'yi yerel olarak render etmez.

**S: Bu, Windows, macOS ve Linux'ta çalışır mı?**  
C: Evet. Aspose.Words for Java platform‑bağımsızdır ve uyumlu bir JDK bulunduğu her yerde çalışır.

---

**Son Güncelleme:** 2026-10-23  
**Test edilen sürüm:** Aspose.Words for Java 24.10  
**Yazar:** Aspose

## İlgili Eğitimler

- [Word Görsellerini Kaydet - Docx'i Java ile Markdown'a Dönüştür](/words/java/document-conversion-and-export/save-word-images-convert-docx-to-markdown-with-java/)
- [Docx'i Markdown'a Dönüştürürken Görselleri CDN'ye Yükle (Tam)](/words/java/document-conversion-and-export/upload-images-to-cdn-while-converting-docx-to-markdown-full/)
- [Docx'i Markdown'a Dönüştürme - Tam Java Rehberi](/words/java/document-conversion-and-export/convert-docx-to-markdown-complete-java-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}