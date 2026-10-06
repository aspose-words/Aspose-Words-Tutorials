---
category: general
date: 2026-02-28
description: Belgeyi markdown'a dönüştürürken nasıl resim gömeceğinizi öğrenin. Resimli
  markdown dışa aktarın ve Java kullanarak markdown içinde satır içi resimler elde
  edin.
draft: false
keywords:
- how to embed images
- convert doc to markdown
- convert word to markdown
- export markdown with images
- inline images in markdown
language: tr
og_description: Word belgesini Markdown'a dönüştürürken resimleri nasıl gömeceğinizi
  keşfedin. Bu rehber, resimlerle birlikte markdown dışa aktarmayı ve resimleri satır
  içinde tutmayı gösterir.
og_title: Word'ü Markdown'a Dönüştürürken Görselleri Nasıl Gömersiniz
tags:
- markdown
- java
- Aspose.Words
- image handling
title: Word'ü Markdown'a Dönüştürürken Görselleri Nasıl Gömeli – Tam Rehber
url: /tr/java/document-conversion-and-export/how-to-embed-images-when-converting-word-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'den Markdown'e Görüntü Gömme – Tam Kılavuz

Bir Word belgesinden oluşturduğunuz bir Markdown dosyasına **görselleri nasıl gömeceğinizi** hiç merak ettiniz mi? Belki hızlı bir dışa aktarma denediniz, ancak bir sürü asılı görüntü dosyası ve kırık bağlantı ile karşılaştınız. Bu, özellikle tek bir taşınabilir `.md` dosyasına ihtiyacınız olduğunda – bir static‑site jeneratörüne ya da GitHub README'ye bırakmak istediğinizde – yaygın bir sıkıntıdır.

İyi haber? Dışa aktarıcıya her resmi Base64‑kodlu bir dize olarak satır içine eklemesini söyleyebilirsiniz, böylece ortaya çıkan Markdown kendi içinde bütünleşik olur. Bu öğreticide tam adımları gösterecek, tam Java kodunu sunacak ve her parçanın neden önemli olduğunu açıklayacağız. Sonunda **doc to markdown** dönüşümünü görüntüler gömülü şekilde yapabilecek ve “markdown with images” ya da “inline images in markdown” gibi diğer senaryolar için süreci nasıl ayarlayacağınızı da göreceksiniz.

## Öğrenecekleriniz

- Gerekli kütüphaneler ve minimal proje kurulumu.  
- Görsellerin Base64 veri URI'ları haline gelmesi için `MarkdownSaveOptions` nasıl yapılandırılır.  
- `ResourceSavingCallback` kullanmanın görüntü işleme kontrolü açısından en temiz yol olması.  
- Markdown dosyasının gerçekten gömülü görüntüler içerdiğini nasıl doğrularsınız.  
- Kenar durumları için ipuçları (büyük görüntüler, farklı MIME tipleri ve performans düşünceleri).  

Aspose.Words ile ilgili önceden bir deneyime ihtiyacınız yok; temel bir Java geçmişi yeterli.

---

## Ön Koşullar

Kodlamaya başlamadan önce şunlara sahip olduğunuzdan emin olun:

| Gereksinim | Neden Önemli |
|-------------|----------------|
| **Java 17+** (veya herhangi bir güncel JDK) | Aspose.Words for Java API'si Java 8+ hedefler, ancak en yeni JDK yerleşik `Base64` yardımcılarını sağlar. |
| **Aspose.Words for Java** (en son sürüm) | Bu kütüphane, kullanacağımız `MarkdownSaveOptions` ve geri çağırma altyapısını sağlar. |
| **Bir Word belgesi** (`.docx`) içinde en az bir görüntü | Dönüştürmek için bir şeyimiz olmalı; örnek `sample.docx` adlı dosyayı varsayar. |
| **Bir IDE veya metin editörü** (IntelliJ, VS Code vb.) | Örneği hızlıca derleyip çalıştırmak için. |

Aspose bağımlılığını `pom.xml` (Maven) ya da `build.gradle` (Gradle) dosyanıza ekleyin. İşte Maven snippet'i:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check the latest version on Maven Central -->
</dependency>
```

Gradle tercih ediyorsanız:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro ipucu:** Aspose ücretsiz 30‑günlük bir deneme sunar. Geçici bir lisans anahtarı alın ve su işareti mesajlarından kaçınmak için erken kaydedin.

---

## Adım 1: Markdown Kaydetme Seçeneklerini Oluşturun

İlk yaptığımız şey `MarkdownSaveOptions` nesnesini örneklemek. Bu nesne, Aspose'a dönüşümün nasıl davranmasını istediğimizi söyler – yazı tipi işleme, liste biçimlendirme ve bizim için en önemlisi görüntü işleme.

```csharp
// Step 1: Create Markdown save options
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();
```

Java'da sözdizimi aynıdır; sadece kod bloğundaki `csharp` anahtar kelimesini daha sonra `java` ile değiştirin.  
Neden önemli: seçenekleri özelleştirmeden Aspose, her görüntüyü `.md` dosyasının yanına ayrı bir dosya olarak yazar. Seçenek nesnesini şimdi hazırlayarak, bu varsayılan davranışı yakalamak için bir kanca elde ederiz.

---

## Adım 2: Görüntü Kaynaklarını Yakala ve Base64 Olarak Kodla

Aspose, bir kaynak (görüntü, CSS vb.) yazmak istediğinde bir geri çağırma tetikler. `IResourceSavingCallback` uygulayarak her kaynakla ne yapacağımıza karar verebiliriz. Aşağıdaki snippet, kaynağın bir görüntü olup olmadığını kontrol eder, dosya adını temizler (böylece dış dosya oluşturulmaz), ikili veriyi Base64'e kodlar ve uygun MIME tipini ayarlar.

```java
// Step 2: Embed all images directly as Base64 data
markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Check if the resource being saved is an image
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Suppress writing an external image file
            args.setResourceFileName(null);
            // Encode the image bytes to a Base64 string
            args.setResourceData(Base64.getEncoder()
                    .encodeToString(args.getResourceData()));
            // Set the appropriate MIME type for the embedded image
            args.setResourceContentType("image/png");
        }
    }
});
```

**Arka planda ne oluyor?**

1. **`args.getResourceType()`** – Aspose her dışa aktarılan bloğu sınıflandırır. Biz sadece `ResourceType.IMAGE` ile ilgileniriz.  
2. **`args.setResourceFileName(null)`** – Dosya adını null yaparak kütüphaneye fiziksel bir dosya yazmamasını söyleriz.  
3. **`Base64.getEncoder().encodeToString(...)`** – Ham bayt dizisi, güvenle bir Markdown veri URI'sine yerleştirilebilecek bir metin dizesine dönüşür.  
4. **`args.setResourceContentType("image/png")`** – Bu, oluşturulan Markdown etiketinin `![alt](data:image/png;base64,…)` şeklinde görünmesini sağlar. Kaynak belgenizde JPEG'ler varsa, orijinal baytları inceleyip `"image/jpeg"` seçebilirsiniz.

> **Neden Base64?**  
> Veri URI'larını anlayan Markdown işlemcileri resmi doğrudan render eder ve ortaya çıkan dosya taşınabilir kalır—kopyalanacak ekstra varlık yoktur. Bu, dış kaynaklara izin vermeyen GitHub README'ları veya dokümantasyon siteleri için özellikle kullanışlıdır.

---

## Adım 3: Dönüşümü Gerçekleştir

Seçenekler hazır olduğuna göre, Word belgenizi yükleyin ve `save` metodunu çağırın. Sağladığınız yol, oluşturulan Markdown dosyasının konumu olacaktır.

```java
// Step 3: Load the source Word document
Document doc = new Document("sample.docx");

// Step 4: Save the document as a Markdown file using the configured options
doc.save("output/doc.md", markdownSaveOptions);
```

Hepsi bu—gerçek dönüşüm kodu iki satır. Ağır iş (DOCX okuma, görüntü çıkarma, paragraf dönüştürme) tamamen Aspose tarafından halledilir.

---

## Adım 4: Sonucu Doğrula – Satır İçi Görüntüler Görünür

`output/doc.md` dosyasını herhangi bir metin editöründe açın. Şuna benzer bir şey görmelisiniz:

```markdown
# Sample Document

Here is an inline image:

![Image 1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

Markdown'ı veri URI'larını destekleyen bir görüntüleyiciye (GitHub, VS Code önizlemesi veya bir static‑site jeneratörü) yapıştırırsanız, ek dosya olmadan resim renderlanır.

**Hızlı kontrol**:  

- **`data:image/` için arama yapın** – Birkaç uzun dize bulursanız gömme işlemi başarılı demektir.  
- **`![](` kalıplarını sayın** – Orijinal Word dosyasındaki görüntü sayısıyla eşleşmelidir.

---

## Kenar Durumlarını Ele Alma

### Büyük Görüntüler

Base64, orijinal boyutu yaklaşık **%33** oranında şişirir. Çok büyük resimler (ör. yüksek çözünürlüklü fotoğraflar) için Markdown dosyası hantal hâle gelebilir. Şu stratejileri değerlendirin:

| Strateji | Ne Zaman Kullanılır |
|----------|---------------------|
| **Dönüştürmeden önce yeniden boyutlandır** – `java.awt.Image` ile küçültün. | Kaynak belgede tam boyutta gerek olmayan yüksek çözünürlüklü varlıklar varsa. |
| **JPEG'e geç** – `args.setResourceContentType("image/jpeg")` yapın. | PNG'in kayıpsız formatının gereksiz olduğu fotoğraflar için. |
| **Belgeyi böl** – Word dosyasını bölümlere ayırıp her birini ayrı ayrı dışa aktarın. | Markdown dosyasını belirli bir boyut sınırı altında tutmanız gerektiğinde (ör. GitHub’ın 10 MB dosya sınırı). |

### PNG Olmayan Görüntüler

Word belgeniz karışık formatlar içeriyorsa, MIME tipini dinamik olarak tespit edebilirsiniz:

```java
String mime = args.getResourceContentType(); // returns something like "image/jpeg"
args.setResourceContentType(mime); // keep original type
```

Aspose zaten `ResourceContentType` değerini doldurur, bu yüzden genellikle `"image/png"` sabitini kodlamanıza gerek kalmaz.

### Performans İpuçları

- **Bir `Base64.Encoder` örneğini tekrar kullanın** eğer bir döngüde çok sayıda görüntü kodluyorsanız.  
- **`markdownSaveOptions.setExportImagesAsBase64(true)`** (API sürümü destekliyorsa) etkinleştirerek geri çağırmayı tamamen atlayabilirsiniz.  
- **Dönüşümü arka plan iş parçacığında çalıştırın** toplu belge işleme yapan bir sunucu ortamındaysanız.

---

## Tam Çalışan Örnek (Hepsi Bir Arada)

Aşağıda, içe aktarmalar, hata yönetimi ve tartıştığımız tam akışı içeren, kopyala‑yapıştır hazır bir Java programı bulabilirsiniz.

```java
import com.aspose.words.*;
import java.util.Base64;
import java.nio.file.Paths;

public class WordToMarkdownWithEmbeddedImages {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("sample.docx");

            // Configure Markdown save options
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

            // Embed images as Base64 data URIs
            mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
                @Override
                public void resourceSaving(ResourceSavingArgs rsArgs) {
                    if (rsArgs.getResourceType() == ResourceType.IMAGE) {
                        // Prevent external file creation
                        rsArgs.setResourceFileName(null);
                        // Encode image bytes to Base64
                        String base64 = Base64.getEncoder()
                                .encodeToString(rsArgs.getResourceData());
                        rsArgs.setResourceData(base64);
                        // Preserve original MIME type (PNG, JPEG, etc.)
                        String mime = rsArgs.getResourceContentType();
                        rsArgs.setResourceContentType(mime);
                    }
                }
            });

            // Define output path (ensure directory exists)
            String outputPath = Paths.get("output", "doc.md").toString();
            doc.save(outputPath, mdOptions);

            System.out.println("Conversion complete! Markdown saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Beklenen çıktı**: satır içi Base64 görüntüler içeren tek bir `doc.md` dosyası, herhangi bir Markdown‑uyumlu araçta kullanılmaya hazır.

---

## Sık Sorulan Sorular

**S1: Bu, Aspose.Words'un eski sürümleriyle çalışır mı?**  
*Genellikle evet.* Geri çağırma API'si sürüm 19'dan beri kararlıdır. Ancak `setExportImagesAsBase64` kısayolu daha yeni sürümlerde ortaya çıktı; eski bir sürüm kullanıyorsanız yukarıda gösterilen açık geri çağırmayı kullanmanız gerekir.

**S2: GitHub Flavored Markdown (GFM) olarak dışa aktarmam gerekirse ne yapmalıyım?**  
Aspose'un `MarkdownSaveOptions` zaten GFM uyumlu sözdizimi üretir. Tek ek adım, deponuzun veri URI'larını desteklediğinden emin olmaktır—GitHub bunu destekler.

**S3: Bu yaklaşımı HTML gibi diğer formatlar için de kullanabilir miyim?**  
Kesinlikle. Aynı `ResourceSavingCallback` `HtmlSaveOptions` için de çalışır. Sadece seçenek sınıfını değiştirin ve Base64 mantığını aynı tutun.

---

##

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}