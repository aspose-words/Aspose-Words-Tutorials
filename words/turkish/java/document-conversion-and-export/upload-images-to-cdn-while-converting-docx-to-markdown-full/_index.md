---
category: general
date: 2026-04-24
description: Aspose.Words kullanarak DOCX'i markdown'a dönüştürürken görselleri CDN'ye
  yükleyin. Görsel işleme ve CDN entegrasyonu ile Word'ü markdown'a dışa aktarmayı
  öğrenin.
draft: false
keywords:
- upload images to cdn
- convert docx to markdown
- export word to markdown
- how to convert docx
- markdown conversion with images
language: tr
og_description: DOCX'i markdown'a dönüştürürken görüntüleri CDN'ye yükleyin. Word'ü
  markdown'a dışa aktarma, görüntü işleme ve CDN yüklemesini kapsayan adım adım Java
  rehberi.
og_title: DOCX'i Markdown'a Dönüştürürken Görüntüleri CDN'ye Yükle – Java Öğreticisi
tags:
- Java
- Aspose.Words
- Markdown
- CDN
- Document Conversion
title: DOCX'i Markdown'a Dönüştürürken Görüntüleri CDN'ye Yükleme – Tam Java Rehberi
url: /tr/java/document-conversion-and-export/upload-images-to-cdn-while-converting-docx-to-markdown-full/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX'i Markdown'a Dönüştürürken Görüntüleri CDN'e Yükleme

DOCX‑to‑Markdown dönüşümünün bir parçası olarak **görüntüleri CDN'e yüklemeniz** gerektiğinde hiç zorlandınız mı? Tek başınıza değilsiniz. Birçok geliştirici, oluşturulan markdown'un üretim ortamına hiç ulaşmayan yerel görüntü dosyalarına işaret etmesiyle karşılaşıyor. İyi haber? Aspose.Words for Java ile her bir görüntünün tam olarak nereye konulacağını kontrol edebilirsiniz—yerel bir “imgs” klasöründe kalabilir ya da seçtiğiniz bir CDN'e itilebilir.

Bu öğreticide, **bir Word belgesini markdown'a dönüştüren**, görüntüleri bir alt‑klasöre kaydeden ve yerel yolları CDN URL'leriyle değiştiren tam, çalıştırılabilir bir örnek üzerinden ilerleyeceğiz. Sonunda, tercih ettiğiniz herhangi bir CDN'de barındırılan görüntülere referans veren, dağıtıma hazır bir markdown dosyanız olacak.

> **Neler öğreneceksiniz**
> - Aspose.Words ile bir DOCX dosyasını nasıl yüklersiniz.
> - `MarkdownSaveOptions` nasıl yapılandırılır ve `IResourceSavingCallback` nasıl uygulanır.
> - Kendi CDN yükleme mantığınızı nereye ekleyeceğiniz.
> - Son markdown çıktısını nasıl doğrulayacağınız.

Temel adımlar için harici bir hizmete ihtiyaç yok, ancak görüntüleri Amazon S3, Cloudflare veya Azure Blob Storage'a itmek isterseniz bir HTTP istemcisi veya SDK ekleyebileceğiniz yerleri de tartışacağız.

---

## Önkoşullar

- **Java 17** veya daha yeni (kod eski sürümlerle de derlenebilir, ancak 17 şu anki LTS).
- **Aspose.Words for Java** 23.9 veya üzeri. Maven Central'dan alabilirsiniz:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

- Dönüştürmek istediğiniz bir **DOCX** dosyası (biz `input.docx` diye adlandıracağız).
- İsteğe bağlı: Görüntüleri gerçekten yükleyecekseniz CDN kimlik bilgileriniz.

---

## Adım 1 – Kaynak Word Belgesini Yükleme

İlk olarak DOCX'i bir Aspose `Document` nesnesine okuruz. Bu, belgenin yapısına tam erişim sağlar; paragraflar, tablolar ve gömülü kaynaklar dahil.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Load the source Word document from the file system
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Neden önemli:**  
> Belgeyi önceden yüklemek, markdown yazarına dokunmadan önce içeriğini incelemenize veya değiştirmenize olanak tanır. Yorumları kaldırmak veya bir stil uygulamak isterseniz, bu satırdan hemen sonra yapabilirsiniz.

---

## Adım 2 – Markdown Kaydetme Seçeneklerini Ayarlama

Aspose.Words, dönüşümü ince ayar yapmanızı sağlayan bir `MarkdownSaveOptions` sınıfı sunar. Bu adımda bir örnek oluşturur ve bir sonraki adımda dolduracağımız kaynak‑kaydetme geri çağırmasını etkinleştiririz.

```java
        // Create save options for Markdown output
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

        // Optional: tweak options (e.g., use GitHub‑flavored markdown)
        saveOptions.setExportImagesAsBase64(false); // keep images as external files
```

> **İpucu:** `ExportImagesAsBase64` değerini `false` bırakmak, görüntüleri bir CDN'e yüklemek istiyorsanız şarttır. Base64‑kodlu görüntüler markdown içine gömülür, dış hostlamanın amacını bozar.

---

## Adım 3 – Kaynak‑Kaydetme Geri Çağırmasını Uygulama

İşte öğreticinin kalbi. `IResourceSavingCallback`, Aspose'un dış kaynak (görüntüler, CSS vb.) yazması gerektiğinde her seferinde tetiklenir. Bu çağrıyı yakalayabilir, görüntüyü bir CDN'e yükleyebilir ve ardından markdown referansını yeniden yazabiliriz.

```java
        // Define a callback to control how external resources (e.g., images) are saved
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // Only act on image resources
                if (args.getResourceFileType() == ResourceFileType.IMAGE) {
                    // Build a local relative path first (e.g., imgs/picture1.png)
                    String localPath = "imgs/" + args.getResourceFileName();
                    args.setResourceFileName(localPath);

                    // --------------------------------------------------------------
                    // OPTIONAL: Upload to CDN here.
                    // --------------------------------------------------------------
                    // For illustration we’ll pretend to upload and get a CDN URL.
                    // Replace the stub with real SDK calls (AWS S3, Azure Blob, etc.).
                    String cdnUrl = uploadToCdn(args.getResourceBytes(), args.getResourceFileName());

                    // If the upload succeeded, tell Aspose to use the CDN URL instead.
                    if (cdnUrl != null && !cdnUrl.isEmpty()) {
                        args.setResourceUri(cdnUrl);
                    }
                    // --------------------------------------------------------------
                }
            }

            // ----- Helper method that you would replace with real upload logic -----
            private String uploadToCdn(byte[] imageBytes, String fileName) {
                // Placeholder: simulate a CDN URL.
                // In production you might use an HTTP client or cloud SDK.
                // Example: return "https://cdn.example.com/images/" + fileName;
                return "https://cdn.example.com/images/" + fileName;
            }
        });
```

### Neden bir geri çağırma kullanmalı?

- **Dosya adı kontrolü:** Her şeyi `imgs/` klasörü altında saklarız, markdown temiz kalır.
- **CDN entegrasyonu:** `args.setResourceUri(...)` ile markdown yazarına yerel yol yerine CDN URL'si ekletiriz.
- **Geleceğe dönük:** CDN sağlayıcısını daha sonra değiştirirseniz, sadece `uploadToCdn` metodunu güncellemeniz yeterli olur.

> **Yaygın tuzak:** `args.setResourceFileName(...)` çağrısını atlamak, Aspose'un görüntüyü markdown dosyasının yanına rastgele bir adla dökmesine ve göreli linklerin kırılmasına neden olur.

---

## Adım 4 – Belgeyi Markdown Olarak Kaydetme

Geri çağırma bağlandıktan sonra, tek satırlık bir komutla markdown dosyasını yazdırırız. Geri çağırma her görüntü için otomatik olarak çalışır.

```java
        // Save the document as Markdown, applying the custom resource handling
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Program bittiğinde şunları bulacaksınız:

1. `output.md` içinde, CDN'inize işaret eden görüntü referansları bulunan markdown metni (ör. `![](https://cdn.example.com/images/picture1.png)`).
2. Orijinal görüntülerle doldurulmuş bir `imgs/` klasörü—hata ayıklama veya yedek senaryoları için faydalı.

---

## Beklenen Çıktı

`input.docx` içinde `chart.png` adlı tek bir resim olduğunu varsayalım; ortaya çıkan `output.md` şöyle görünecek:

```markdown
# My Document Title

Here is an introductory paragraph.

![](https://cdn.example.com/images/chart.png)

More text follows...
```

Görüntü artık CDN üzerinden sunuluyor, yani downstream tüketiciler (GitHub, statik site jeneratörü vb.) onu küresel dağıtılmış bir uç noktadan çekecek.

---

## Profesyonel İpuçları & Kenar Durumları

| Durum | Ne Yapmalı |
|-----------|------------|
| **Yüzlerce görüntülü büyük DOCX** | Görüntüleri asenkron olarak toplu yükleyerek ana iş parçacığını engellemekten kaçının. |
| **CDN'iniz desteklemeyen görüntü formatı** | `args.getResourceBytes()`'ı desteklenen bir formata (ör. PNG) dönüştürüp ardından yükleyin. |
| **Belge başına özel klasör yapısı ihtiyacınız var** | `args.setResourceFileName("docs/" + docId + "/" + args.getResourceFileName());` kullanın. |
| **CDN'iniz kimlik doğrulama başlıkları istiyor** | `uploadToCdn` içinde imzalı URL veya kimlik doğrulamayı yöneten bir SDK kullanarak yüklemeyi gerçekleştirin. |
| **Çevrimdışı dokümanlar için base64 yedekleme istiyorsunuz** | `saveOptions.setExportImagesAsBase64(true)` ayarlayın *ve* isterseniz CDN yüklemesi için geri çağırmayı da tutun. |

---

## Sıkça Sorulan Sorular

**S: Bu, eski Aspose.Words sürümleriyle çalışır mı?**  
C: `IResourceSavingCallback` API'si 20.5 sürümünde tanıtıldı. Daha eski bir sürüm kullanıyorsanız yükseltin—kodunuz ileriye dönük uyumlu olur ve performans iyileştirmelerinden de faydalanırsınız.

**S: Henüz bir CDN'im yoksa ne yapmalıyım?**  
C: Örnekteki `uploadToCdn` metodu sadece sahte bir URL döndürür. CDN yüklemesi olmadan dönüşümü çalıştırabilirsiniz; markdown yerel `imgs/` yoluna referans verir.

**S: Birden fazla DOCX dosyasını toplu işleyebilir miyim?**  
C: Kesinlikle. Mantığı bir döngüye sarın, her yinelemede farklı bir `input.docx` ve çıktı yolu verin. Çok sayıda dosya işliyorsanız hız için tek bir `MarkdownSaveOptions` örneğini yeniden kullanın.

---

## Sonuç

Aspose.Words for Java kullanarak **DOCX'i markdown'a dönüştürürken görüntüleri CDN'e yükleme** işlemini nasıl yapacağınızı gösterdik. Süreç üç temel adıma indirgenir:

1. Word belgesini yükleyin.
2. Her görüntüyü yükleyen ve markdown linkini yeniden yazan bir `IResourceSavingCallback` bağlayın.
3. `MarkdownSaveOptions` ile belgeyi kaydedin.

Hepsi bu—ekstra post‑işleme betikleri, manuel URL kopyalama yok. Artık statik site jeneratörleri, dokümantasyon portalları veya başka bir markdown‑uyumlu platform için temiz bir markdown dosyanız var.

Bir sonraki meydan okumaya hazır mısınız? CDN yüklemesini bir **Azure Blob Storage** SDK çağrısı ile değiştirin ya da **GitHub‑flavored markdown** seçenekleriyle deney yapın (`saveOptions.setExportImagesAsBase64(true)`). Bunu, her commit'te güncellenen dokümanları otomatik olarak yayınlayan bir CI/CD boru hattına da entegre edebilirsiniz.

Bir sorunla karşılaştıysanız veya akıllı bir tweak keşfettiyseniz, aşağıya yorum bırakın. Mutlu kodlamalar ve kenardan hizmet veren görüntülerin hızının tadını çıkarın!

---

![Diagram illustrating the upload images to cdn workflow during DOCX to Markdown conversion](upload-images-to-cdn-diagram.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}