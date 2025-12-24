---
category: general
date: 2025-12-23
description: Java'da markdown görüntüleri gömün ve belge markdown'ını kaydetmeyi,
  doc markdown'ını dönüştürmeyi, denklemleri LaTeX olarak dışa aktarmayı ve Java markdown
  dışa aktarımını gerçekleştirmeyi öğrenin—hepsi tek bir öğreticide.
draft: false
keywords:
- embed images markdown
- save document markdown
- convert doc markdown
- export equations latex
- java markdown export
language: tr
og_description: Java ile markdown içinde resimleri göm, belge markdown'ını kaydet,
  doc markdown'ını dönüştür, denklemleri LaTeX olarak dışa aktar ve tek bir pratik
  öğreticide Java markdown dışa aktarmayı ustala.
og_title: Görselleri Gömme Markdown – Java Adım Adım Kılavuzu
tags:
- Java
- Markdown
- DocumentConversion
title: Görselleri Gömme Markdown – Denklemleri Kaydetme, Dönüştürme ve Dışa Aktarma
  İçin Tam Java Rehberi
url: /tr/java/document-conversion-and-export/embed-images-markdown-complete-java-guide-to-save-convert-an/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Embed Images Markdown – Kaydetme, Dönüştürme ve Denklem Dışa Aktarma İçin Tam Java Rehberi

Java'dan belge oluştururken **embed images markdown**'e ihtiyaç duydunuz mu? Tek başınıza değilsiniz. Birçok geliştirici, doc‑to‑markdown dönüşümü sırasında görselleri ve OfficeMath denklemlerini korumaya çalışırken bir duvara çarpar.

Bu öğreticide, **save document markdown**, **convert doc markdown**, **export equations latex** ve tek bir görseli bile kaçırmadan tam bir **java markdown export** nasıl yapılır göreceksiniz. Sonunda, bir `.md` dosyası yazan, her görseli bir `images/` klasörüne döken ve OfficeMath'i La‑TeX'e dönüştüren çalıştırmaya hazır bir kod parçacığına sahip olacaksınız.

## Öğrenecekleriniz

- `MarkdownSaveOptions`'ı OfficeMath için LaTeX dışa aktarımıyla ayarlama.
- Her görsel dosyasını depolayan bir kaynak‑kaydetme geri çağrısı (callback) yazma.
- Belgeyi Markdown olarak kaydederken göreceli görsel yollarını koruma.
- Yaygın tuzaklar (yinelenen dosya adları, eksik klasörler) ve bunlardan kaçınma yolları.
- Çıktıyı nasıl doğrulayacağınızı ve çözümü daha büyük işlem hatlarına nasıl entegre edeceğinizi öğrenme.

> **Önkoşullar**: Java 17+, Aspose.Words for Java (veya benzer API'ler sunan herhangi bir kütüphane), Markdown sözdizimi hakkında temel bilgi.

## 1. Adım – Markdown Kaydetme Seçeneklerini Hazırlama (Save Document Markdown)

Başlamak için bir `MarkdownSaveOptions` örneği oluşturur ve kütüphaneye OfficeMath'i LaTeX olarak dışa aktarmasını söyleriz. Bu, sürecin **export equations latex** bölümüdür.

```java
// Import required classes
import com.aspose.words.*;

public class MarkdownExporter {
    public static void main(String[] args) throws Exception {
        // Load your source .docx (or .doc) file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 1️⃣ Create Markdown save options and enable LaTeX export for OfficeMath
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setOfficeMathExportMode(OfficeMathExportMode.LaTeX);
```

**Neden önemli** – Varsayılan olarak Aspose.Words denklemleri görsel olarak render eder, bu da markdown'ı şişirir. LaTeX, onları hafif ve düzenlenebilir tutar.

## 2. Adım – Görsel Geri Çağrısını Tanımlama (Embed Images Markdown)

Kütüphane, karşılaştığı her görsel için bir **resource‑saving callback** çağırır. Geri çağrı içinde benzersiz bir dosya adı oluşturur, görseli diske yazar ve Markdown'un referans alacağı göreceli yolu döndürür.

```java
        // 2️⃣ Define a callback that saves each image resource to a folder and returns its relative path
        markdownOptions.setResourceSavingCallback((resource, stream) -> {
            // Generate a unique file name for the image
            String imageFileName = "img_" + java.util.UUID.randomUUID() + ".png";

            // Ensure the target directory exists
            java.nio.file.Path imageDir = java.nio.file.Paths.get("YOUR_DIRECTORY/images");
            java.nio.file.Files.createDirectories(imageDir);

            // Save the image to the desired directory
            try (java.io.FileOutputStream fos = new java.io.FileOutputStream(
                    imageDir.resolve(imageFileName).toFile())) {
                stream.transferTo(fos);
            }

            // Return the relative path that will be written into the Markdown file
            return "images/" + imageFileName; // <-- this is the embed images markdown part
        });
```

**İpucu**: `UUID.randomUUID()` kullanmak, aynı orijinal ada sahip iki görselin çakışmasını engeller. Ayrıca, `Files.createDirectories` klasör eksikse sessizce oluşturur—artık “directory not found” istisnası yok.

## 3. Adım – Belgeyi Markdown Olarak Kaydetme (Java Markdown Export)

Şimdi, yapılandırılmış seçeneklerimizle `doc.save`'i çağırıyoruz. Metot `.md` dosyasını yazar ve geri çağrı sayesinde her görseli `images/` alt klasörüne koyar.

```java
        // 3️⃣ Save the document as a Markdown file using the configured options
        doc.save("YOUR_DIRECTORY/output.md", markdownOptions);
    }
}
```

Program tamamlandığında şunları göreceksiniz:

- `output.md`, `![](images/img_3f8c9a2e-...png)` gibi görsel bağlantıları içeren Markdown metni içerir.
- PNG dosyalarıyla dolu bir `images/` klasörü.
- Tüm OfficeMath denklemleri LaTeX olarak render edilir, örn. `$$\int_{a}^{b} f(x)\,dx$$`.

**Markdown'un Görünümü** (alıntı):

```markdown
Here is a picture of the architecture:

![](images/img_7e2b1c4d-...png)

And here is an equation:

$$\frac{a}{b} = c$$
```

## 4. Adım – Çıktıyı Doğrulama (Convert Doc Markdown)

Hızlı bir doğrulama, dönüşümün başarılı olduğunu garantiler:

1. `output.md` dosyasını bir Markdown önizleyicide (VS Code, Typora veya GitHub önizleme) açın.
2. Her görselin doğru şekilde görüntülendiğini doğrulayın.
3. Denklemlerin LaTeX blokları (`$$ … $$`) olarak göründüğünü kontrol edin. Eğer ham LaTeX gösteriyorsa, önizleyiciniz bunu destekliyor demektir; aksi takdirde bir MathJax eklentisine ihtiyacınız olabilir.

Eğer bir görsel eksikse, geri çağrının döndürdüğü yolu iki kez kontrol edin. Göreceli yol, `.md` dosyasına göre klasör yapısıyla eşleşmelidir.

## 5. Adım – Kenar Durumları ve Yaygın Tuzaklar (Save Document Markdown)

| Situation | Why it Happens | Fix |
|-----------|----------------||
| **Büyük görseller** yavaş rendera neden olur | Görseller orijinal çözünürlükte kaydedilir | Kaydetmeden önce yeniden boyutlandırın veya sıkıştırın (`ImageIO` yardımcı olabilir) |
| **UUID'ye rağmen yinelenen dosya adları** | Nadir ama UUID çakışırsa mümkün | Ek güvenlik için zaman damgası veya kısa bir hash ekleyin |
| **Eksik `images/` klasörü** | Geri çağrı klasör oluşturulmadan önce çalışır | `Files.createDirectories`'i geri çağrının *dışında* çağırın, gösterildiği gibi |
| **Denklem LaTeX olarak dışa aktarılmıyor** | `OfficeMathExportMode` varsayılan olarak bırakılmış | Kaydetmeden önce `setOfficeMathExportMode(OfficeMathExportMode.LaTeX)` çağrıldığından emin olun |

## Tam Çalışan Örnek (Tüm Adımlar Birleştirildi)

```java
import com.aspose.words.*;
import java.io.*;
import java.nio.file.*;
import java.util.UUID;

public class MarkdownExporter {
    public static void main(String[] args) throws Exception {
        // Load source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 1️⃣ Configure Markdown options with LaTeX export
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setOfficeMathExportMode(OfficeMathExportMode.LaTeX);

        // 2️⃣ Callback for image handling
        markdownOptions.setResourceSavingCallback((resource, stream) -> {
            String imageFileName = "img_" + UUID.randomUUID() + ".png";
            Path imageDir = Paths.get("YOUR_DIRECTORY/images");
            Files.createDirectories(imageDir);
            try (FileOutputStream fos = new FileOutputStream(imageDir.resolve(imageFileName).toFile())) {
                stream.transferTo(fos);
            }
            return "images/" + imageFileName;
        });

        // 3️⃣ Save as Markdown
        doc.save("YOUR_DIRECTORY/output.md", markdownOptions);

        System.out.println("Markdown export complete! Check YOUR_DIRECTORY for output.md and images/");
    }
}
```

**Beklenen konsol çıktısı**

```
Markdown export complete! Check YOUR_DIRECTORY for output.md and images/
```

`output.md` dosyasını açın – tüm görsellerin ve LaTeX denklemlerinin doğru şekilde gömülmüş olduğunu görmelisiniz.

## Sonuç

Artık **embed images markdown** yaparken **java markdown export** gerçekleştiren, aynı zamanda **save document markdown**, **convert doc markdown** ve **export equations latex** yapan sağlam bir uçtan‑uca tarifiniz var. Ana bileşenler `MarkdownSaveOptions` yapılandırması ve her görseli öngörülebilir bir konuma yazan kaynak‑kaydetme geri çağrısıdır.

Buradan itibaren şunları yapabilirsiniz:

- Bu kodu daha büyük bir derleme işlem hattına (ör. Maven veya Gradle görevi) entegre edin.
- Geri çağrıyı SVG veya GIF gibi diğer kaynak türlerini işlemek için genişletin.
- Üretim belgeleri için görsel bağlantılarını bir CDN'ye yönlendirecek bir son‑işlem adımı ekleyin.

Sorularınız veya paylaşmak istediğiniz bir varyasyon var mı? Yorum bırakın, iyi kodlamalar!

--- 

<img src="https://example.com/placeholder-diagram.png" alt="embed images markdown sürecinin akışını gösteren diyagram" style="max-width:100%;">

*Diyagram: Bir Word belgesinden → MarkdownSaveOptions → Görsel geri çağrısı → images klasörü + Markdown dosyası akışı.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}