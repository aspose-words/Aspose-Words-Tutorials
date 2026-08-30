---
category: general
date: 2026-06-27
description: Aspose.Words for Java kullanarak docx'i markdown'a dönüştürün. Görüntüleri
  base64 olarak nasıl gömeceğinizi öğrenin ve Word belgesini zahmetsizce markdown'a
  aktarın.
draft: false
keywords:
- convert docx to markdown
- embed images as base64
- how to embed images markdown
- export word document to markdown
- convert docx to markdown with images
language: tr
og_description: convert docx to markdown with Aspose.Words for Java. This tutorial
  shows how to embed images as base64 and export Word document to markdown in a single
  flow.
og_title: gömülü resimlerle docx'i markdown'a dönüştür – Java rehberi
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: convert docx to markdown using Aspose.Words for Java. Learn how to
    embed images as base64 and export Word document to markdown effortlessly.
  headline: convert docx to markdown with embedded images – Java guide
  type: TechArticle
- description: convert docx to markdown using Aspose.Words for Java. Learn how to
    embed images as base64 and export Word document to markdown effortlessly.
  name: convert docx to markdown with embedded images – Java guide
  steps:
  - name: Read the image file into a byte array (`Files.readAllBytes`).
    text: Read the image file into a byte array (`Files.readAllBytes`).
  - name: Encode with `Base64.getEncoder().encodeToString`.
    text: Encode with `Base64.getEncoder().encodeToString`.
  - name: 'Insert the data URI into your Markdown string: `![alt](data:image/png;base64,${base64})`.'
    text: 'Insert the data URI into your Markdown string: `![alt](data:image/png;base64,${base64})`.'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Conversion
title: Gömülü Görsellerle DOCX'i Markdown'a Dönüştür – Java Rehberi
url: /tr/java/document-conversion-and-export/convert-docx-to-markdown-with-embedded-images-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# docx'i markdown'a gömülü görüntülerle dönüştür – Java rehberi

Hiç **docx'i markdown'a dönüştürmeniz** gerektiğinde, görüntülerin kaybolması ya da kırık bağlantılara dönüşmesiyle karşılaştınız mı? Tek başınıza değilsiniz. Birçok projede—statik site jeneratörleri, dokümantasyon boru hatları veya hızlı ön izlemeler—bu resimleri korumak şart, ancak yaygın dönüştürücüler genellikle onları atar.  

Şanslıyız, Aspose.Words for Java bize **görüntüleri base64 olarak gömmek** için temiz bir yöntem sunuyor, böylece çıktı dosyası gerçekten taşınabilir oluyor. Bu rehberde tüm süreci adım adım inceleyeceğiz: bir Word dosyasını yükleme, Markdown kaydetme seçeneklerini yapılandırma, görüntü kaynaklarını işleme ve sonunda kaydetme. Sonunda **görüntüleri markdown içinde nasıl gömeceğinizi** tam olarak öğrenecek ve Maven ya da Gradle projenize ekleyebileceğiniz çalıştırmaya hazır bir kod parçacığı elde edeceksiniz.

## İhtiyacınız olanlar

- Java 17 veya daha yeni (API eski sürümlerle de çalışır, ancak 17 en uygun sürüm).
- Aspose.Words for Java kütüphanesi (en yeni JAR'ı Maven Central'dan alabilirsiniz: `com.aspose:aspose-words:23.12`).
- Dönüştürmek istediğiniz bir `.docx` dosyası (biz ona `Report.docx` diyeceğiz).
- İyi bir IDE (IntelliJ IDEA, Eclipse veya Java uzantılı VS Code).

Ek bir görüntü‑işleme aracına ihtiyaç yok—kütüphane her şeyi arka planda hallediyor.

## Adım 1: Word belgesini yükleyin – **docx'i markdown'a dönüştür** temeli

İlk olarak, kaynak dosyaya işaret eden bir `Document` örneği oluştururuz. Bu nesneyi, paragraf, tablo ve tabii ki görüntülerle dolu Word dosyanızın bellek içi temsili olarak düşünebilirsiniz.

```java
import com.aspose.words.*;

public class DocxToMarkdown {
    public static void main(String[] args) throws Exception {
        // Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/Report.docx");
        // … we’ll configure options next
    }
}
```

> **Pro ipucu:** Docx'i bir akıştan (ör. yüklenen bir dosya) okuyorsanız, `Document` yapıcısına bir `InputStream` geçirebilirsiniz—web uygulamaları için mükemmel.

## Adım 2: MarkdownSaveOptions yapılandırması – **görüntüleri base64 olarak gömme** sihri

Aspose.Words, dönüşüm davranışını ayarlamamıza izin veren bir `MarkdownSaveOptions` sınıfı ile birlikte gelir. Görüntüleri canlı tutmanın anahtarı `IResourceSavingCallback`'tir. Callback içinde her görüntü akışını yakalar, Base64 stringine çevirir ve kaynak adını bir data URI'ye yeniden yazarız.

```java
import java.io.ByteArrayOutputStream;
import java.util.Base64;
import com.aspose.words.*;

MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();

// Embed images directly as Base64 data URIs
markdownOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) throws Exception {
        // Only act on image resources
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Copy the image stream to a byte array
            ByteArrayOutputStream baos = new ByteArrayOutputStream();
            args.getStream().copyTo(baos);
            // Encode the bytes as Base64
            String base64 = Base64.getEncoder().encodeToString(baos.toByteArray());
            // Build a data URI (png assumed, adjust if needed)
            args.setResourceFileName("data:image/png;base64," + base64);
            // Close the original stream – we no longer need it
            args.setKeepResourceStreamOpen(false);
        }
    }
});
```

Neden bu ekstra adımı atıyoruz? Çünkü **export word document to markdown** callback olmadan çalıştırıldığında, görüntüler ayrı bir klasöre dökülür ve göreli yollarla referans verilir. Bu yollar, Markdown dosyasını taşıdığınızda, özellikle CI boru hatlarında kırılır. Görüntüyü Base64 stringi olarak gömerek, Markdown tek bir, kendine yeterli eser haline gelir—GitHub README'leri veya harici varlıkları desteklemeyen statik site jeneratörleri için mükemmeldir.

### Farklı görüntü formatlarını işleme

Yukarıdaki kod parçası PNG (`image/png`) varsayar. Kaynak Word belgenizde JPEG'ler varsa, orijinal içerik tipini inceleyebilirsiniz:

```java
String mime = args.getContentType(); // e.g., "image/jpeg"
args.setResourceFileName("data:" + mime + ";base64," + base64);
```

Bu küçük dokunuş, sonuç Markdown'un orijinal formata bakılmaksızın doğru şekilde render edilmesini sağlar.

## Adım 3: Dosyayı kaydedin – **export word document to markdown** son adım

Seçenekler hazır olduğunda, sadece `document.save` metodunu çağırıp hedef yolu ve yapılandırılmış `MarkdownSaveOptions` nesnesini geçiririz. Kütüphane ağır işi yapar: belge ağacını dolaşır, paragrafları Markdown sözdizimine dönüştürür ve Base64 görüntülerimizi gerektiği yere enjekte eder.

```java
// Save the document as Markdown with embedded Base64 images
document.save("YOUR_DIRECTORY/Report.md", markdownOptions);
System.out.println("Conversion complete! Check Report.md");
```

`Report.md` dosyasını herhangi bir Markdown görüntüleyicide (VS Code, GitHub, typora vb.) açtığınızda, görüntülerin satır içi render edildiğini, ekstra dosyalara ihtiyaç duyulmadığını göreceksiniz.

## Adım 4: Tam, çalıştırılabilir örnek – **docx'i markdown'a görüntülerle dönüştür** tek bir yerde

Hepsini bir araya getirerek, kopyalayıp yapıştırabileceğiniz, derleyip çalıştırabileceğiniz tam program aşağıdadır:

```java
import com.aspose.words.*;
import java.io.*;
import java.util.Base64;

public class DocxToMarkdown {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/Report.docx");

        // 2️⃣ Set up Markdown save options with Base64 image embedding
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                if (args.getResourceType() == ResourceType.IMAGE) {
                    ByteArrayOutputStream baos = new ByteArrayOutputStream();
                    args.getStream().copyTo(baos);
                    String base64 = Base64.getEncoder().encodeToString(baos.toByteArray());
                    String mime = args.getContentType(); // Preserve original MIME type
                    args.setResourceFileName("data:" + mime + ";base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                }
            }
        });

        // 3️⃣ Save as Markdown – this is where we **export word document to markdown**
        document.save("YOUR_DIRECTORY/Report.md", markdownOptions);
        System.out.println("✅ convert docx to markdown with embedded images finished.");
    }
}
```

### Beklenen çıktı

`Report.md` dosyasını açtığınızda aşağıdakine benzer bir şey görmelisiniz:

```markdown
# Sample Report

Here is an introductory paragraph.

![Image](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...==)

Another paragraph follows.
```

Uzun Base64 stringi görüntü verisini temsil eder. Çoğu editör UI'da bunu kısaltır, ancak ön izleme sırasında görüntü mükemmel şekilde render olur.

## Yaygın tuzaklar ve nasıl önlenir

| Sorun | Neden oluşur | Çözüm |
|------|----------------|-----|
| Görüntüler kırık bağlantı olarak görünür | Callback, `ResourceType` kontrolü eksik olduğu için tetiklenmedi. | `if (args.getResourceType() == ResourceType.IMAGE)` ifadesinin mantığınızın etrafını sarmaladığından emin olun. |
| Çıktı dosyası çok büyük | Base64, veriyi yaklaşık %33 oranında şişirir. | Taşınabilirlik için bu takası kabul edin, ya da boyut bir sorun ise harici görüntülere geçin. |
| Yanlış görüntü formatı | JPEG'ler için sabit kodlu `image/png`. | Orijinal MIME tipini korumak için `args.getContentType()` kullanın. |
| Büyük belgelerde bellek yetersizliği | Devasa bir DOCX'i belleğe yüklemek. | Belgeyi parçalara bölerek işleyin veya JVM yığınını artırın (`-Xmx2g`). |

## Başka bağlamlarda **görüntüleri markdown içinde nasıl gömeceğinizi** gerektiğinde

Aspose.Words kullanmıyorsanız ama yine de Base64 görüntüler gömmek istiyorsanız, prensip aynı kalır:

1. Görüntü dosyasını bir byte dizisine okuyun (`Files.readAllBytes`).
2. `Base64.getEncoder().encodeToString` ile kodlayın.
3. Data URI'yi Markdown stringinize ekleyin: `![alt](data:image/png;base64,${base64})`.

Kütüphane, karşılaştığı her görüntü için bu işlemi otomatikleştirir, böylece bir döngü yazmaktan kurtulursunuz.

## Sonraki adımlar – dönüşümü genişletme

Artık **docx'i markdown'a görüntülerle dönüştür** konusunu ustaca kullandığınıza göre, şu iyileştirmeleri düşünün:

- **Stil koruma**: Önce `HtmlSaveOptions` kullanın, ardından flexmark‑java gibi bir araçla HTML'i Markdown'a dönüştürerek daha zengin biçimlendirme elde edin.
- **Tablo işleme**: Aspose zaten tabloları dönüştürüyor, ancak `markdownOptions.setTableAlignment` ile sütun hizalamasını ince ayar yapabilirsiniz.
- **Toplu işleme**: Yukarıdaki kodu bir dizin tarayıcısına sararak onlarca raporu otomatik olarak dönüştürün.
- **CI entegrasyonu**: JAR'ı derleme boru hattınıza ekleyin ve her commit'te dokümantasyon üretin.

Bu fikirlerin her biri, burada ele aldığımız temel kavramlar üzerine kurulu, bu yüzden kodu uyarlamaktan çekinmeyeceksiniz.

## Sonuç

**docx'i markdown'a dönüştür** ve tüm resimlerin Base64 stringi olarak gömülü kalmasını sağlayan tam, uçtan uca bir çözümü adım adım inceledik. Ana adımlar—belgeyi yükleme, özel bir `IResourceSavingCallback` ile `MarkdownSaveOptions` yapılandırma ve dosyayı kaydetme—basit ve Aspose.Words for Java ile kutudan çıkar çıkmaz çalışır.  

Bu bilgiyle artık dokümantasyon boru hatlarını otomatikleştirebilir, taşınabilir Markdown raporları üretebilir veya Word içeriğinizin tek dosyalı, temiz bir versiyonunu tutabilirsiniz. SVG'leri işleme veya başlık seviyelerini özelleştirme gibi daha ileri ayarlara meraklıysanız, Aspose.Words API dokümanlarını keşfedin; burada inşa ettiğimiz şeyle uyumlu pek çok örnek bulacaksınız.

İyi kodlamalar, ve Markdown'unuz her zaman görüntü‑zengin olsun!  

![convert docx to markdown diagram](convert-docx-to-markdown.png "convert docx to markdown")

---


## Sonra Ne Öğrenmelisiniz?


Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanıza ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [DOCX Dönüştürürken Markdown'a Görüntüleri Gömme](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [Aspose.Words for Java ile Markdown'ı Dışa Aktarma](/words/english/java/document-loading-and-saving/saving-documents-as-markdown/)
- [docx'i markdown'a Dönüştür – Aspose.Words ile Matematik Denklemlerini LaTeX'e Aktarma](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}