---
category: general
date: 2026-04-28
description: Aspose.Words for Java kullanarak PDF UA belgesi oluşturun. Docx dosyasını
  kurtarma ile yüklemeyi, denklemleri LaTeX'e dışa aktarmayı, Word'den markdown kaydetmeyi
  ve eksik yazı tiplerini geri almayı öğrenin.
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: tr
og_description: Java için Aspose.Words ile PDF/UA belgesi oluşturun. Kurtarma yüklemesi,
  LaTeX dışa aktarımı, Markdown kaydetme ve eksik font alma konularını kapsayan adım
  adım rehber.
og_title: PDF UA Belgesi Oluştur – Tam Java Öğreticisi
tags:
- Aspose.Words
- Java
- PDF/UA
title: Aspose.Words ile PDF UA Belgesi Oluşturma – Tam Java Rehberi
url: /tr/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PDF UA Belgesi Oluşturma – Tam Java Öğreticisi

Bir Word dosyasından **PDF UA belgesi** oluştururken bozuk içerikle nasıl başa çıkılır? Bu öğreticide, kurtarma modu ile DOCX yüklemeyi, denklemleri LaTeX’e aktarmayı, Word’den Markdown kaydetmeyi ve eksik yazı tiplerini geri getirmeyi Aspose.Words for Java ile adım adım göstereceğiz.  

Eğer bir .docx dosyasına bakıp PDF’nizin neden erişilebilir olmadığını merak ettiyseniz, doğru yerdesiniz. Sonunda tam uyumlu bir PDF/UA 1 dosyanız, LaTeX denklemleri içeren bir Markdown sürümünüz ve yükleme sırasında gerçekleşen yazı tipi değişimlerinin net bir listesi olacak.

## Gerekenler

- **Aspose.Words for Java** (2026 itibarıyla en son sürüm) – Maven/Gradle bağımlılığını ekleyin veya JAR dosyasını sınıf yolunuza ekleyin.  
- Java 17 veya daha yeni bir sürüm (API akışları kullandığı için güncel bir JDK önerilir).  
- Bozuk bölümler, Office Math denklemleri ve yüzen şekiller içerebilecek bir `input.docx` örneği.  

Ek bir kütüphane gerekmez; her şey Aspose.Words içinde bulunur.

---

## Adım 1 – Kurtarma Modu ile DOCX Yükleme  

Bir belge kısmen hasar gördüğünde, varsayılan yükleyici bir istisna fırlatır. Kurtarma modunu etkinleştirerek Aspose.Words’e devam etmesini ve yalnızca uyarılar üretmesini söylersiniz.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Neden önemli:* Kurtarma modu, tek bir hatalı paragraftan dolayı tüm iş akışınızın kırılmasını önler. Ayrıca `doc.getWarnings()` doldurulur, böylece daha sonra **eksik yazı tiplerini** ve diğer sorunları **alabilirsiniz**.

---

## Adım 2 – Denklemleri LaTeX Olarak Markdown Dosyasına Aktarma  

Çoğu geliştirici belgelemeler için Markdown’ı sever, ancak Word’ün yerleşik denklemleri kopyalanması zor bir iştir. Aspose.Words, bunları doğrudan LaTeX’e çevirebilir.

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*İpucu:* Geri çağırma, çıkarılan her görselin `imgs/` klasörüne yerleştirilmesini sağlar. Bu, GitHub’ın Markdown’ı nasıl işlediğine benzer – temiz ve taşınabilir.

---

## Adım 3 – Doğru Etiketleme ile PDF / UA Belgesi Oluşturma  

PDF/UA (Evrensel Erişilebilirlik) uyumu, birçok kamu sektörü projesi için zorunludur. Aşağıdaki seçenekler, Aspose.Words’ün yüzen şekilleri doğru şekilde etiketlemesini ve PDF/UA uyum bayrağını ayarlamasını sağlar.

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*Ne göreceksiniz:* `output.pdf` dosyasını Adobe Acrobat Pro’da açtığınızda belge özelliklerinde “PDF/UA‑1 compliant” ibaresini göreceksiniz. Tüm yüzen şekiller (metin kutuları, resimler) ekran okuyucular için uygun etiketlere sahip olacaktır.

---

## Adım 4 – Bir Şeklin Gölgesini Ayarlama (İsteğe Bağlı Stil)  

Erişilebilirlik için zorunlu olmasa da, görsel ayarlamalar iç raporlar için kullanışlı olabilir.

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*Niçin?* PDF aynı zamanda bir pazarlama materyali ise, hafif bir gölge düzeni daha şık gösterir ve uyumu bozmadan görünümü iyileştirir.

---

## Adım 5 – Eksik Yazı Tiplerini ve Diğer Uyarıları Getirme  

Kurtarma yüklemesi sırasında Aspose.Words, gerçekleşen tüm yazı tipi ikamelerini kaydeder. Bunları listelemek, doğru yazı tipini gömmek ya da yedekle kabul etmek konusunda karar vermenize yardımcı olur.

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*Tipik çıktı* (konsolunuzda şu şekilde bir şey göreceksiniz):

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

Eğer kritik yazı tiplerinin eksik olduğunu görürseniz, sunucunuza bu yazı tiplerini kurmayı ya da `PdfSaveOptions.setEmbedFullFonts(true)` ile gömmeyi düşünün.

---

## Tam Çalışan Örnek  

Aşağıda, tamamen çalıştırılabilir Java sınıfı yer alıyor. IDE’nize yapıştırın, yolları ayarlayın ve **Run** tuşuna basın.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**Beklenen sonuçlar**

| Çıktı | Açıklama |
|--------|-------------|
| `output.md` | Her Office Math denkleminin LaTeX (`$…$`) olarak göründüğü Markdown dosyası. Görseller `imgs/` altında depolanır. |
| `output.pdf` | PDF/UA‑1 uyumlu belge; Acrobat’ta Dosya → Özellikler → Standartlar altında “PDF/UA‑1” gösterilir. |
| Konsol | Eksik yazı tiplerinin listesi, örn. “Missing: Calibri → substituted: Arial”. |

---

## Sık Sorulan Sorular (SSS)

**S: Bu, eski Aspose.Words sürümleriyle çalışır mı?**  
C: `RecoveryMode`, `OfficeMathExportMode.LATEX` ve `PdfCompliance.PDF_UA_1` enum’ları 22.8’de tanıtıldı. Daha eski bir sürüm kullanıyorsanız yükseltin – erişilebilirlik özellikleri geriye dönük olarak eklenmedi.

**S: Orijinal yazı tiplerini ikame yerine gömmek istiyorum, ne yapmalıyım?**  
C: `pdfOptions.setEmbedFullFonts(true)` ayarlayın ve yazı tipi dosyalarının JVM’in font yolunda erişilebilir olduğundan emin olun.

**S: LaTeX denklemlerini koruyarak başka işaretleme formatlarına (ör. HTML) dışa aktarabilir miyim?**  
C: Evet. `HtmlSaveOptions` kullanın ve `setOfficeMathExportMode(OfficeMathExportMode.LATEX)` ayarlayın – aynı enum formatlar arasında çalışır.

**S: DOCX dosyamda çok sayıda yüzen şekil var; hepsi etiketlenecek mi?**  
C: `setExportFloatingShapesAsInlineTag(true)` ile Aspose.Words, her yüzen şekli PDF/UA için bir `<Figure>` etiketiyle sarar ve çoğu ekran okuyucu kontrolünü karşılar.

---

## Özet  

Word kaynağından **PDF UA belgesi** oluşturmayı, **docx’i kurtarma modu ile yüklemeyi**, **denklemleri LaTeX’e aktarmayı**, **Word’den markdown kaydetmeyi** ve **eksik yazı tiplerini getirmeyi** gösterdik. Kod tamamen bağımsız, Java 17+ ortamında çalışır ve hem erişilebilirlik denetimleri hem de geliştirici ihtiyaçları için hazır varlıklar üretir.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}