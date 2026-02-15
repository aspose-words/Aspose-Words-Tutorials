---
category: general
date: 2026-02-15
description: Aspose.Words kullanarak Java’da Word’i Markdown’e dışa aktarın. DOCX’i
  Markdown’e dönüştürmeyi ve görüntüleri özel bir geri arama ile ayrı bir klasöre
  kaydetmeyi öğrenin.
draft: false
keywords:
- export word to markdown
- convert docx to markdown
- store images in separate folder
- aspose words markdown
- java document conversion
language: tr
og_description: Aspose.Words ile Word'ü Markdown'a Dışa Aktarın. Bu kılavuz, DOCX'i
  Markdown'a nasıl dönüştüreceğinizi ve görselleri ayrı bir klasöre nasıl kaydedeceğinizi
  gösterir.
og_title: Word'ü Markdown'a Aktar – Tam Java Öğreticisi
tags:
- Java
- Aspose.Words
- Markdown
- Image handling
title: Word'ü Markdown'a Dışa Aktar – Tam Java Rehberi
url: /tr/java/document-conversion-and-export/export-word-to-markdown-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'ı Markdown'a Dışa Aktarma – Tam Java Eğitimi

Hiç **Word'ı Markdown'a dışa aktarmanın** gömülü resimleri kaybetmeden nasıl yapılacağını merak ettiniz mi? Tek başınıza değilsiniz—geliştiriciler sürekli olarak “DOCX'i Markdown'a dönüştürürken resimleri düzenli tutmanın yolu nedir?” sorusunu sorar. İyi haber şu ki Aspose.Words for Java bu işi çocuk oyuncağı haline getiriyor. Bu öğreticide, bir `.docx` dosyasını Markdown'a dönüştüren ve ayrıca **görselleri ayrı bir klasöre kaydeden** hazır‑çalıştır örneği adım adım inceleyeceğiz.

İhtiyacınız olan her şeyi ele alacağız: gerekli kütüphaneler, adım‑adım kod, her satırın neden önemli olduğu ve hızlı bir doğrulama kontrol listesi. Sonunda, herhangi bir Java projesine ekleyebileceğiniz yeniden kullanılabilir bir desen elde edeceksiniz.

---

## İhtiyacınız Olanlar

| Önkoşul | Neden Önemli |
|--------------|----------------|
| **Java 8+** | Aspose.Words en az JDK 8 gerektirir. |
| **Aspose.Words for Java** (latest version) | `Document`, `MarkdownSaveOptions` ve `IResourceSavingCallback` arayüzünü sağlar. |
| **A DOCX file** you want to convert | Dönüştürmek istediğiniz kaynak belge (`input.docx`). |
| **Write permission** on the output directories | Kütüphane Markdown dosyasını ve görsel klasörünü yazacaktır. |

Add the Maven dependency (or download the JAR) before you start:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version> <!-- check for the newest release -->
</dependency>
```

## Adım 1 – Kaynak Word Belgesini Yükle

İlk yaptığımız şey, `.docx` dosyamıza işaret eden bir `Document` örneği oluşturmaktır. Bu nesne, tüm Word dosyasını bellekte temsil eder ve içeriğine, stillerine ve gömülü kaynaklarına erişim sağlar.

```java
import com.aspose.words.*;

public class MarkdownExportDemo {
    public static void main(String[] args) throws Exception {
        // Load the source .docx
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Neden önemli:* Dosya yolu yanlış ise Aspose `FileNotFoundException` hatası fırlatır. Mutlak ya da doğru çözümlenmiş bir göreli yol kullanmak bu sorunu önler.

## Adım 2 – Markdown Kaydetme Seçeneklerini Hazırla

`MarkdownSaveOptions`, dönüşümün nasıl davranacağını ayarlamamıza olanak tanır. Varsayılan olarak görseller, Markdown dosyasının yanında genel isimlerle kaydedilir. Bunu daha sonra geçersiz kılacağız, ancak önce bir seçenek nesnesine ihtiyacımız var.

```java
        // Create options for Markdown export
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

*Not:* Görsel dışa aktarmayı kontrol etmek isterseniz `mdOptions.setExportImages(true)` ayarını da yapabilirsiniz, ancak varsayılan zaten `true`.

## Adım 3 – Kaynak‑Kaydetme Geri Çağrısını Tanımla (Görselleri Ayrı Klasörde Sakla)

İşte öğreticinin kalbi. `IResourceSavingCallback`'i uygulayarak her bir görselin nereye kaydedileceği üzerinde tam kontrol elde ederiz. Geri çağrı, Aspose'un yazmak istediği her kaynak (görseller, yazı tipleri vb.) için bir `ResourceSavingArgs` nesnesi alır.

```java
        // Customize image saving location
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                // Only intervene for image resources
                if (args.getResourceFileType() == ResourceFileType.IMAGE) {
                    // Build a unique filename based on document hash and original extension
                    String uniqueName = "img_" + doc.hashCode() + "." + args.getResourceFileExtension();
                    args.setResourceFileName(uniqueName);
                    // Store images in a dedicated folder
                    args.setResourceFilePath("YOUR_DIRECTORY/customImages/" + uniqueName);
                }
                // Let Aspose handle other resource types (e.g., fonts) automatically
            }
        });
```

**Bunu yapmamızın nedeni:**  
- **İsim çakışmalarını önlemek:** Aynı orijinal isme sahip iki görsel farklı dosya adları alır.  
- **Daha temiz proje düzeni:** Tüm resimler `customImages/` altında bulunur, Markdown klasörünü düzenli tutar.  
- **Tahmin edilebilir URL'ler:** Markdown `customImages/img_12345.png` adresine referans verir; bu adresi daha sonra bir CDN'ye gönderebilir veya statik bir siteye gömebilirsiniz.

## Adım 4 – Belgeyi Markdown Olarak Kaydet

Şimdi Aspose'a, az önce yapılandırdığımız seçenekleri kullanarak Markdown dosyasını yazmasını söylüyoruz. Çağrı eşzamanlıdır; döndüğünde dosya ve görseller zaten diskte bulunur.

```java
        // Export to Markdown
        doc.save("YOUR_DIRECTORY/CustomMarkdown.md", mdOptions);
    }
}
```

Eğer her şey sorunsuz ilerlerse şunları bulacaksınız:

- `CustomMarkdown.md`, `![](customImages/img_12345.png)` gibi görsel bağlantıları içeren dönüştürülmüş metni barındırır.
- Tüm görsel dosyaları `YOUR_DIRECTORY/customImages/` içinde yer alır.

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

Aşağıda, derlemeye hazır tam sınıf yer alıyor. `YOUR_DIRECTORY` ifadesini makinenizdeki gerçek yol ile değiştirin.

```java
import com.aspose.words.*;

public class MarkdownExportDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source DOCX
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create Markdown save options
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

        // 3️⃣ Hook into the resource‑saving pipeline
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                if (args.getResourceFileType() == ResourceFileType.IMAGE) {
                    String uniqueName = "img_" + doc.hashCode() + "." + args.getResourceFileExtension();
                    args.setResourceFileName(uniqueName);
                    args.setResourceFilePath("YOUR_DIRECTORY/customImages/" + uniqueName);
                }
                // Other resources (fonts, etc.) use default handling
            }
        });

        // 4️⃣ Save as Markdown
        doc.save("YOUR_DIRECTORY/CustomMarkdown.md", mdOptions);
    }
}
```

### Beklenen Sonuç

`CustomMarkdown.md` dosyasını herhangi bir metin düzenleyicide veya Markdown görüntüleyicide açın. Şuna benzer bir şey görmelisiniz:

```markdown
# Sample Document

This is a paragraph from the original Word file.

![](customImages/img_123456789.png)

Another paragraph follows.
```

`img_123456789.png` görsel dosyası, Markdown dosyasının yanındaki `customImages` klasöründe bulunacaktır.

## Profesyonel İpuçları ve Yaygın Tuzaklar

- **Klasör varlığı:** Aspose hedef görsel klasörünü otomatik olarak **oluşturmaz**. Dışa aktarmadan önce `customImages/` klasörünün var olduğundan emin olun veya programatik olarak oluşturun.  
  ```java
  new java.io.File("YOUR_DIRECTORY/customImages").mkdirs();
  ```
- **Hash çakışmaları:** `doc.hashCode()` kullanmak genellikle güvenlidir, ancak aynı belgeyi çok kez dönüştürürseniz aynı isimler oluşabilir. Ek benzersizlik için zaman damgası ekleyin:  
  ```java
  String uniqueName = "img_" + doc.hashCode() + "_" + System.currentTimeMillis() + "." + args.getResourceFileExtension();
  ```
- **Büyük belgeler:** Binlerce görsel içeren DOCX dosyaları için çıktıyı akış olarak işlemek veya JVM yığınını (`-Xmx2g`) artırmak düşünün.  
- **Görsel formatları:** Aspose orijinal görsel formatını (PNG, JPEG, vb.) korur. Tüm görselleri PNG olarak istiyorsanız, klasörü sonradan işlemek ya da Aspose'un görsel dönüştürme API'lerini kullanmanız gerekir.

## Sıkça Sorulan Sorular

**S: Bu .doc dosyalarıyla da çalışır mı, sadece .docx mi?**  
C: Evet. Aspose.Words formatı otomatik olarak algılar, dolayısıyla `new Document("file.doc")` ile gösterebilir ve aynı işlem hattı çalışır.

**S: Görsellerin dış dosyalar yerine base64 olarak gömülmesini istersem ne yapmalıyım?**  
C: `mdOptions.setExportImagesAsBase64(true)` ayarlayın. Bu, görsel verisini doğrudan Markdown dosyasına satır içi ekler, ancak ayrı bir görsel klasörünün avantajını kaybedersiniz.

**S: Statik site jeneratörü için Markdown dosya uzantısını `.mdx` olarak değiştirebilir miyim?**  
C: Kesinlikle. `save` metodunun ilk argümanı sadece bir dosya adı olduğundan, `doc.save("output.mdx", mdOptions);` aynı şekilde çalışır.

## Özet

Aspose.Words kullanarak **Word'ı Markdown'a dışa aktardık**, **DOCX'i Markdown'a nasıl dönüştüreceğinizi** gösterdik ve **görselleri ayrı bir klasörde saklamanın** temiz bir yolunu sergiledik. Bu desen—yükle → seçenekleri yapılandır → geri çağrı ekle → kaydet—otomatik belge dönüşümüne ihtiyaç duyan herhangi bir projeye ölçeklenebilir.

İleride keşfedebileceğiniz adımlar:

- Bu kodu bir Spring Boot REST uç noktasına entegre ederek kullanıcıların bir DOCX yükleyip hazır‑yayınlanabilir bir Markdown paketi almasını sağlayın.  
- Bir statik site jeneratörü (ör. Hugo) ile birleştirerek blog yayınlama süreçlerini otomatikleştirin.  
- Görsel‑kaydetme mantığını bulut depolamaya (AWS S3, Azure Blob) değiştirmek için geri çağrı içinde yükleme yapın ve Markdown bağlantısını herkese açık URL olarak ayarlayın.

Daha fazla sorunuz mu var? Yorum bırakın, iyi kodlamalar! 

![Word'ı Markdown'a dışa aktarma örneği](export_word_to_markdown.png "Word'ı Markdown'a dışa aktarma illüstrasyonu")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}