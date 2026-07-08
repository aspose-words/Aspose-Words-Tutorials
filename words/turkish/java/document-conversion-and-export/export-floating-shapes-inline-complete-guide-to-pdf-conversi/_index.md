---
category: general
date: 2026-07-03
description: Word'ü PDF'ye dönüştürürken yüzen şekilleri satır içi olarak dışa aktarın.
  Java'da PDF seçeneklerini nasıl ayarlayacağınızı ve Word'ü PDF olarak kaydetme seçeneklerini
  öğrenin.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: tr
og_description: Word belgesini PDF’ye dönüştürürken yüzen şekilleri satır içi olarak
  dışa aktar. Bu öğretici, PDF seçeneklerini nasıl ayarlayacağınızı ve Word’ü PDF
  olarak kaydetme seçeneklerini gösterir.
og_title: Yüzen Şekilleri Satır İçi Dışa Aktar – Java PDF Dönüştürme Rehberi
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Yüzen Şekilleri Satır İçi Olarak Dışa Aktarma – PDF Dönüştürme Tam Rehberi
url: /tr/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yüzen Şekilleri Satır İçi Dışa Aktarma – PDF Dönüştürme Tam Kılavuzu

Bir Word belgesini PDF’ye dönüştürürken **yüzen şekilleri satır içi dışa aktarmanız** gerektiğinde hiç zorlandınız mı? Yalnız değilsiniz—birçok geliştirici, diyagramları veya ikonların gizemli bir şekilde ayrı katmanlara kayması sorunuyla karşılaşıyor. İyi haber şu ki, tek bir PDF seçeneği bu şekilleri `<span>` etiketleri içinde tutarak, düzeni Word’de gördüğünüz gibi koruyabiliyor.

Bu öğreticide **PDF seçeneklerini Java’da nasıl ayarlayacağınızı** adım adım gösterecek, **Word’ü PDF seçenekleriyle kaydetmek** için gereken kodu sunacak ve **Word’ü satır içi PDF’ye dönüştürmenin** varsayılan blok‑seviyeli dışa aktarmaya göre neden tercih edilebileceğini açıklayacağız. Sonunda, herhangi bir Maven veya Gradle projesine ekleyebileceğiniz çalıştırmaya hazır bir kod parçacığı elde edeceksiniz.

## Öğrenecekleriniz

- Yüzen şekiller için satır içi `<span>` ve blok `<div>` dışa aktarımı arasındaki fark.  
- `PdfSaveOptions`ı satır içi renderlamayı zorlamak için nasıl yapılandıracağınız.  
- `.docx` dosyasını yükleyen, seçeneği uygulayan ve PDF olarak yazan adım‑adım kod.  
- Yaygın tuzaklar (eksik fontlar, desteklenmeyen şekiller) ve bunlardan nasıl kaçınılacağı.  
- Çıktıyı test etme ipuçları ve yaklaşımı diğer belge öğelerine genişletme yolları.

**Önkoşullar** – Java 8 veya daha yeni bir sürüm, Aspose.Words for Java kütüphanesi (veya `PdfSaveOptions` sınıfını taklit eden herhangi bir API) ve yüzen şekiller içeren bir örnek Word dosyası (öğreticide `FloatingShapes.docx` kullanılıyor). Başka bir dış araç gerekmez.

---

## Adım 1: Kaynak Word Belgesini Yükleyin

İlk olarak dönüştürmek istediğiniz `.docx` dosyasını açmanız gerekir. Bu oldukça basittir, ancak yolun mutlak olduğundan veya sınıf yolunuzdan doğru çözüldüğünden emin olun.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Neden önemli:*  
Belge doğru şekilde yüklenmezse, sonraki PDF dönüşümü bir `FileNotFoundException` fırlatır. `Document` kullanmak, sayfadaki yüzen şekiller de dahil olmak üzere iç nesne modelinin tamamen doldurulmasını sağlar.

---

## Adım 2: PDF Kaydetme Seçeneklerini Oluşturun ve Yüzen Şekilleri Satır İçi Olarak Ayarlayın

İşte sihrin gerçekleştiği yer. Varsayılan olarak Aspose.Words, yüzen şekilleri blok‑seviyeli `<div>` öğeleri olarak dışa aktarır; bu da HTML‑tabanlı PDF’lerde akışı bozabilir. `setExportFloatingShapesAsInlineTag(true)` çağrısı, motorun her şekli satır içi bir `<span>` içinde sarmasını sağlar.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Neden önemli:*  
- **Düzen sadakati** – Satır içi etiketler şekli çevredeki metinle hizalı tutar, istenmeyen boşlukları önler.  
- **Arama yapılabilirlik** – Satır içi öğeler PDF okuyucular tarafından daha doğru indekslenme eğilimindedir.  
- **Stil kontrolü** – PDF’yi daha sonra HTML’ye dönüştürürseniz, `<span>`’ı CSS ile hedefleyebilirsiniz.

> **Pro ipucu:** Belirli bir belge için eski blok davranışına ihtiyacınız olursa, sadece `false` geçin veya çağrıyı tamamen kaldırın.

---

## Adım 3: Belgeyi Yapılandırılmış Seçeneklerle PDF Olarak Kaydedin

Şimdi yüklü `Document` nesnesi ile `PdfSaveOptions`ı birleştirip dosyayı dışa aktarın. Bu tek satır tüm işi yapar.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Neden önemli:*  
`save` metodu, `pdfOptions` üzerinde ayarladığınız her bayrağa saygı gösterir. Seçenekleri geçmeyi unutmak, varsayılan blok dışa aktarmaya geri dönerek **yüzen şekilleri satır içi dışa aktarma** amacını bozar.

---

## Tam Çalışan Örnek

Hepsini bir araya getirdiğimizde, hemen derleyip çalıştırabileceğiniz kompakt bir program elde edersiniz. `YOUR_DIRECTORY` kısmını makinenizdeki gerçek bir yol ile değiştirin.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Beklenen çıktı** – Programı çalıştırdıktan sonra `FloatingShapes.pdf` dosyasını açın. Şekillerin metinle hizalı, ekstra boşluk olmadan göründüğünü ve PDF’nin iç yapısını (XML’i) incelediğinizde her şeklin etrafında `<span>` etiketleri olduğunu göreceksiniz.

![Export floating shapes inline example](https://example.com/export-inline.png "Screenshot showing floating shapes rendered inline in the PDF")

*Resim alt metni:* **export floating shapes inline** PDF’de satır içi şekillerin ekran görüntüsü.

---

## Yaygın Sorular & Kenar Durumları

### 1. “Belgem karmaşık bir SmartArt içeriyorsa ne olur?”

SmartArt bir çizim nesnesi olarak ele alınır. Satır içi bayrağı çoğu vektör şekli için çalışır, ancak çok karmaşık SmartArt hâlâ bir resim olarak renderlanabilir. Bu durumda, dönüşümden önce Word’de SmartArt’ı düzleştirmeyi düşünün veya `pdfOptions.setExportSmartArtAsImage(true)` kullanarak resmi dışa aktarmayı zorlayın.

### 2. “Aynı belgede satır içi ve blok dışa aktarmayı birleştirebilir miyim?”

Maalesef API ayarı global olarak uygulanır. Karışık davranışa ihtiyacınız varsa, belgeyi bölümlere ayırın, her bölümü farklı seçeneklerle dışa aktarın ve ardından `PdfMerger` ile PDF’leri birleştirin.

### 3. “Bu, font gömmeyi etkiler mi?”

Hayır. Font gömme `pdfOptions.setEmbedFullFonts(true)` (varsayılan) ile kontrol edilir. Satır içi şekil bayrağını etkilemeden güvenle açıp kapatabilirsiniz.

### 4. “Şekillerin gerçekten `<span>` olduğunu nasıl doğrularım?”

PDF’yi **PDF.js** veya **Adobe Acrobat** → **Edit PDF** → **Object Inspector** gibi bir araçla açın. Alt XML’de şeklin bir `<span>` öğesi içinde olduğunu göreceksiniz. `<div>` görürseniz, seçenek uygulanmamıştır.

---

## Yaklaşımı Genişletme – İlgili Seçenekler

Burada olduğunuz sürece, diğer PDF dönüşüm ayarlarını da keşfetmek isteyebilirsiniz:

| Seçenek | Ne işe yarar | Tipik kullanım senaryosu |
|--------|--------------|--------------------------|
| `setCompressImages(true)` | Görüntü boyutunu azaltır | Daha hızlı indirme |
| `setUseHighQualityRendering(true)` | Vektör renderlamasını iyileştirir | Baskıya hazır PDF’ler |
| `setExportDocumentStructure(true)` | Erişilebilirlik için yapısal etiketler ekler | WCAG uyumluluğu |
| `setSaveFormat(SaveFormat.PDF)` | Formatı açıkça ayarlar (nadiren gerekir) | Çok‑formatlı işlem hatları |

Bu ayarlar, **convert word to pdf inline** senaryolarında hem düzen sadakati hem de performans ihtiyacını karşılamak için **convert word to pdf inline** ile güzel bir uyum sağlar.

---

## Dönüşümünüzü Test Etme

1. **Görsel kontrol** – PDF’yi iki farklı görüntüleyicide (Chrome ve Adobe Reader) açarak şekillerin hizalı olduğundan emin olun.  
2. **Otomatik fark** – `pdfbox` gibi bir kütüphane kullanarak XML’i çıkarın ve `<span>` etiketlerinin varlığını doğrulayan bir test yazın.  
3. **Performans ölçümü** – `setCompressImages` ile ve olmadan geçen süreyi ölçerek dengeyi görün.

Basit bir JUnit örneği:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## Sonuç

Artık **export floating shapes inline** yaparken **convert word to pdf inline** işlemi için uçtan uca bir çözümünüz var. `PdfSaveOptions`ı yapılandırarak her şekil için kullanılan HTML etiketini kontrol edebilir, PDF’lerinizi düzenli ve aranabilir tutabilirsiniz. Çıktıyı test etmeyi, görüntü sıkıştırma gibi ilgili seçenekleri ayarlamayı ve karmaşık SmartArt gibi kenar durumlarını ele almayı unutmayın.

Bir sonraki adıma hazır mısınız? Aynı tekniği **export floating tables inline** için deneyin veya Aspose’un `HtmlSaveOptions`ı ile CSS‑styled PDF’ler oluşturun. Yükle → yapılandır → kaydet deseni, neredeyse her belge‑to‑PDF senaryosu için geçerlidir.

**pdf seçeneklerini nasıl ayarlayacağınız** veya farklı bir kütüphane için **save word as pdf options** konusunda daha fazla sorunuz varsa yorum bırakın, mutlu kodlamalar!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere yakın konuları kapsar ve adım‑adım açıklamalarla tam çalışan kod örnekleri sunar; böylece ek API özelliklerini hâkim olabilirsiniz ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}