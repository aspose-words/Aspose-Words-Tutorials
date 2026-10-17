---
category: general
date: 2026-01-11
description: DOCX dosyasını dönüştürürken Markdown'a resimleri nasıl gömeceğinizi
  öğrenin; küçük resimler için Base64 kullanın ve büyük kaynakları ayrı kaydedin.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- export word document markdown
language: tr
og_description: Bir DOCX dosyasını dönüştürürken Markdown'da resimleri nasıl gömeceğinizi
  öğrenin; küçük resimler için Base64 kullanın ve büyük kaynakları ayrı olarak kaydedin.
og_title: DOCX Dönüştürürken Markdown'a Görselleri Nasıl Gömülür
tags:
- Aspose.Words
- Java
- Markdown
- Image Embedding
title: DOCX Dönüştürürken Markdown'a Görselleri Nasıl Gömülür
url: /tr/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX Dönüştürürken Markdown'e Görüntü Nasıl Gömülür

Bir Word belgesinden gelen bir Markdown dosyasına **görsellerin nasıl gömüleceğini** hiç merak ettiniz mi? Tek başınıza değilsiniz. Çoğu geliştirici, dönüşüm sırasında resimlerin kaybolması ya da son düzeni bozan bir şekilde depolanması sorunuyla karşılaşıyor.  

Bu rehberde, küçük grafikler için Base64 veri URI'leri olarak **görsellerin nasıl gömüleceğini** gösteren, tamamen çalıştırılabilir bir örnek üzerinden adım adım ilerleyeceğiz; daha büyük varlıklar ise yan bir klasöre kaydedilecek. Ayrıca **convert docx to markdown** konusunu ele alacak, Aspose.Words ile **how to convert docx** üzerine değinecek ve görselleri Base64 olarak gömmek ile ayrı dosyalar olarak dışa aktarmak arasındaki farkı açıklayacağız.  

> **Pro tip:** Sadece hızlı bir kanıt‑konsepti (proof‑of‑concept) ihtiyacınız varsa, aşağıdaki kod tek bir Maven bağımlılığıyla doğrudan çalışır.

---

## İhtiyacınız Olanlar

- **Java 17** (veya herhangi bir yeni JDK) – API Java odaklıdır, ancak kavramlar diğer dillere de uygulanabilir.
- **Aspose.Words for Java** – DOCX → Markdown dönüşümünü destekleyen ticari bir kütüphane.
- Küçük simgeler ve büyük fotoğrafların karışımını içeren bir **örnek DOCX**.
- Markdown ve ilgili kaynakların bulunmasını istediğiniz bir klasör.

Ek bir çerçeve, harici betik yok. Sadece saf Java ve Aspose.Words.

## Adım 1 – Projeye Aspose.Words Ekleyin (convert docx to markdown)

Maven kullanıyorsanız, aşağıdaki kod parçacığını `pom.xml` dosyanıza ekleyin. Okuma zamanındaki en son sürümle değiştirmekten çekinmeyin.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Neden önemli:** Aspose.Words, DOCX yapısını ayrıştırma, görselleri çıkarma ve Markdown sözdizimini oluşturma işini üstlenir. Kendi ayrıştırıcınızı yazmaya çalışmak, muhtemelen ihtiyacınız olmayan bir tavşan deliğine girmek anlamına gelir.

## Adım 2 – Kaynak DOCX Belgesini Yükleyin

İlk olarak, API'yi dönüştürmek istediğiniz Word dosyasına yönlendirin. `Document` yapıcı (constructor) tüm işi yapar—manuel XML ayrıştırması gerekmez.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Yorumun bu satırın *neden* kritik olduğunu açıkladığını fark edin: bir `Document` örneği olmadan dönüştürülecek bir şey yoktur.

## Adım 3 – Kaynak‑Kaydetme Geri Çağrımıyla MarkdownSaveOptions Hazırlayın

Bu, **görsellerin nasıl doğru şekilde gömüleceğinin** kalbidir. Geri çağrı, dönüştürücünün yazmak istediği her kaynak (görsel, stil vb.) için bir kanca sağlar.

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

### Neden bir geri çağrı?

- **Kontrol:** Görselin satır içi Base64 dizesi mi yoksa ayrı bir dosya mı olacağına siz karar verirsiniz.
- **Performans:** Küçük simgeler Markdown'in bir parçası olur, ekstra HTTP istekleri ortadan kalkar.
- **Taşınabilirlik:** Daha büyük resimler dış dosyalar olarak kalır, Markdown boyutu makul seviyede tutulur.

## Adım 4 – Belgeyi Markdown Olarak Kaydedin

Son olarak, Aspose.Words'a daha önce yapılandırdığımız seçenekleri kullanarak Markdown dosyasını yazmasını söyleyin.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Programı çalıştırdığınızda iki şey üretilir:

1. `output.md` – orijinal DOCX'inizin Markdown temsili.
2. Gömülmemiş büyük görselleri içeren bir `markdown_resources` klasörü.

## Tam Çalışan Örnek (Tüm Adımlar Tek Bir Yerde)

Aşağıda, IDE'nize kopyalayıp yapıştırmaya hazır tam kaynak dosyası bulunmaktadır. `YOUR_DIRECTORY` ifadesini makinenizdeki gerçek yol ile değiştirin.

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

Daha büyük resimler şu şekilde referans alınır:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

Bu, dosya boyutunu yönetilebilir tutarken **görselleri gömmek** için tam olarak ihtiyacınız olan şeydir.

## Yaygın Sorular ve Kenar Durumları

### Görsel PNG yerine JPEG olsaydı ne olur?

Yukarıdaki geri çağrı her zaman URI'yi `image/png` ile önekler. JPEG'ler için `args.getData()`'nın ilk birkaç baytını inceleyebilir veya doğru MIME tipini tahmin etmek için `args.getFileName()`'i kullanabilirsiniz:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Boyut eşiğini değiştirebilir miyim?

Kesinlikle. `10_000` bayt sınırı sadece bir örnek. Geniş bir bant genişliği bütçeniz varsa, bunu 50 KB ya da daha fazlasına çıkarabilirsiniz. Aksine, ultra‑hafif Markdown dosyalarına ihtiyacınız varsa düşürebilirsiniz.

### Tablolar veya diğer Word nesneleriyle çalışır mı?

Evet. Aspose.Words tabloları, listeleri ve hatta dipnotları otomatik olarak Markdown'a dönüştürür. Kaynak geri çağrısı yalnızca görselleri yakalar, bu yüzden diğer öğeler için ekstra koda ihtiyacınız yok.

### ASCII olmayan dosya adları ne olur?

API, `markdown_resources` klasörüne yazarken Unicode dosya adlarını güvenli bir şekilde kodlar. Dosya sisteminizin UTF‑8'i desteklediğinden emin olun (çoğu modern işletim sistemi bunu destekler).

## Sorunsuz Dönüşüm İçin Pro İpuçları

- **Çıktı klasörünü temiz tutun.** Her dönüşümde sadece bir kez `Files.createDirectories` çalıştırın veya her çalıştırmadan önce klasörü silerek temiz bir başlangıç yapın.
- **Markdown'i doğrulayın.** `markdownlint` gibi araçlar, hatalı Base64 dizgileriyle eklenen hatalı karakterleri yakalayabilir.
- **Aspose.Words sürüm kilidi koyun.** Belirli bir sürüm, büyük bir sürüm değişikliği varsayılan davranışı değiştirse bile kodunuzun çalışmaya devam etmesini sağlar.
- `markdown_resources/` klasörü için bir .gitignore girdisi kullanın

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}