---
category: general
date: 2025-12-25
description: DOCX'i markdown'a dönüştürürken LaTeX'i nasıl dışa aktarır ve belgeyi
  PDF olarak kaydedersiniz—Java kodlu adım adım rehber.
draft: false
keywords:
- how to export latex
- convert docx to markdown
- save document as pdf
- how to save pdf
- save word as markdown
language: tr
og_description: LaTeX'i dışa aktarmayı, DOCX'i markdown'a dönüştürmeyi ve belgeyi
  Java ile PDF olarak kaydetmeyi öğrenin. Tam kod ve ipuçları.
og_title: Word'den LaTeX Nasıl Dışa Aktarılır – DOCX'i Markdown'a Dönüştür ve PDF
  Olarak Kaydet
tags:
- Aspose.Words
- Java
- Document Conversion
title: 'Word''ten LaTeX Nasıl Dışa Aktarılır: DOCX''i Markdown''a Dönüştür ve PDF
  Olarak Kaydet'
url: /tr/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'ten LaTeX Nasıl Dışa Aktarılır: DOCX'i Markdown'a Dönüştür ve PDF Olarak Kaydet

Hiç **Word dosyasından LaTeX dışa aktarmanın** nasıl yapılacağını, o şık denklemleri kaybetmeden merak ettiniz mi? Yalnız değilsiniz. Birçok projede—akademik makaleler, teknik bloglar veya iç dökümanlar—insanlar bir `.docx` dosyasından LaTeX çıkarmak, tüm içeriği markdown'a dönüştürmek ve dağıtım için düzenli bir PDF sürümü tutmak zorunda kalıyor.  

Bu öğreticide tüm süreci adım adım inceleyeceğiz: **docx'i markdown'a dönüştür**, **LaTeX dışa aktar**, ve **Aspose.Words for Java** kütüphanesini kullanarak **dökümanı PDF olarak kaydet**. Sonunda, tüm bunları yapan hazır bir Java programına ve kendi kod tabanınıza kopyalayıp yapıştırabileceğiniz birkaç pratik ipucuya sahip olacaksınız.

## Neler Öğreneceksiniz

- Geri kurtarma modunda olası bozuk bir Word dökümanı yükleme.  
- Markdown olarak kaydederken Office Math denklemlerini LaTeX olarak dışa aktarma.  
- Yüzen şekilleri satır içi etiketler olarak işleyerek aynı dökümanı PDF olarak kaydetme.  
- Markdown dışa aktarımı sırasında görüntü işleme özelleştirme (görüntüleri ayrı bir klasöre kaydetme).  
- **Word'ü markdown olarak kaydet** ve hâlâ yüksek kaliteli bir PDF kopyasını tutma.  

**Önkoşullar**: Java 17 veya daha yeni bir sürüm, Maven ya da Gradle, ve bir Aspose.Words for Java lisansı (deneme sürümü deneyler için yeterli). Başka üçüncü‑taraf kütüphane gerekmez.

---

## Adım 1: Projenizi Kurun

İlk iş—Aspose.Words jar dosyasını sınıf yoluna ekleyelim. Maven kullanıyorsanız, `pom.xml` dosyanıza şu bağımlılığı ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Check for the latest version -->
</dependency>
```

Gradle için ise tek satır yeterli:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **İpucu:** Her zaman en son kararlı sürümü kullanın; geri kurtarma modu ve LaTeX dışa aktarımı için hata düzeltmeleri içerir.

`DocxProcessor.java` adında yeni bir Java sınıfı oluşturun. İhtiyacımız olan tüm importları ekleyeceğiz:

```java
import com.aspose.words.*;

import java.io.File;
import java.io.IOException;
```

---

## Adım 2: Dökümanı Geri Kurtarma Modunda Yükleyin

Bozuk dosyalar olur—özellikle e‑posta ya da bulut senkronizasyonu sırasında. Aspose.Words, *recovery mode* ile dosyaları açmanıza izin verir, böylece tüm içeriği kaybetmezsiniz.

```java
public class DocxProcessor {

    public static void main(String[] args) throws Exception {
        // Adjust these paths to match your environment
        String inputPath = "YOUR_DIRECTORY/corrupted.docx";
        String outputMarkdown = "YOUR_DIRECTORY/output.md";
        String outputPdf = "YOUR_DIRECTORY/output.pdf";
        String customMarkdown = "YOUR_DIRECTORY/output_with_custom_images.md";

        // Step 2: Load with recovery mode
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // STRICT, IGNORE are alternatives
        Document doc = new Document(inputPath, loadOptions);

        // Continue with export steps...
```

Neden `RecoveryMode.RECOVER` kullanıyoruz? İçeriğin mümkün olduğunca kurtarılmasını deniyor, fakat dosya tamamen okunamazsa bir istisna fırlatıyor. Bu, güvenlik ile pratikliği dengeler.

---

## Adım 3: DOCX'i Markdown'a Dönüştürürken LaTeX Dışa Aktarın

Şimdi gösterinin yıldızı: **Word dökümanından LaTeX dışa aktarma**. `MarkdownSaveOptions` sınıfının `OfficeMathExportMode` özelliği sayesinde LaTeX, MathML veya görüntü çıktısı seçebilirsiniz. Biz LaTeX'i seçeceğiz.

```java
        // Step 3: Export Office Math as LaTeX during markdown conversion
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        doc.save(outputMarkdown, mdOptions);
```

Oluşan `output.md` dosyası, satır içi denklemler için `$…$` ve gösterim denklemleri için `$$…$$` içinde LaTeX parçacıkları barındıracak. Dosyayı MathJax ya da KaTeX destekli bir markdown editöründe açarsanız denklemler güzelce renderlanır.

> **Neden LaTeX?** Çünkü bilimsel yayıncılığın ortak dili o. LaTeX'e doğrudan dışa aktarmak, görüntülere dönüştürürseniz oluşacak kayıplı dönüşümü önler.

---

## Adım 4: PDF Olarak Kaydedin (Yüzen Şekilleri Koruyun)

Çoğu zaman markdown'a alışık olmayan inceleyiciler için bir PDF sürümüne hâlâ ihtiyaç duyarsınız. Aspose.Words bunu çok basit hâle getirir ve yüzen şekillerin (ör. diyagramlar) nasıl işleneceğini kontrol edebilirsiniz.

```java
        // Step 4: Save as PDF, exporting floating shapes as inline tags
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save(outputPdf, pdfOptions);
```

`ExportFloatingShapesAsInlineTag` özelliğini `true` yaparak her yüzen şekli PDF'in iç yapısında satır içi bir `<span>` etiketi haline getirirsiniz; bu, sonraki işlemler (ör. PDF erişilebilirlik araçları) için faydalı olabilir.

---

## Adım 5: Markdown Kaydederken Görüntü İşlemeyi Özelleştirin

Varsayılan olarak Aspose.Words, tüm görüntüleri markdown dosyasının bulunduğu klasöre, sıralı isimlerle yazar. Daha düzenli bir `images/` alt klasörü istiyorsanız `ResourceSavingCallback`'e bağlanabilirsiniz.

```java
        // Step 5: Custom image folder for markdown export
        MarkdownSaveOptions customMdOptions = new MarkdownSaveOptions();
        customMdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // Place each image under YOUR_DIRECTORY/images/
                String imageFolder = "YOUR_DIRECTORY/images/";
                new File(imageFolder).mkdirs(); // Ensure the folder exists
                args.setFileName(imageFolder + args.getFileName());
                // You could also modify the stream here or skip saving if needed
            }
        });

        doc.save(customMarkdown, customMdOptions);
```

Artık `output_with_custom_images.md` içinde referans verilen tüm görüntüler `images/` klasörünün altında düzgünce saklanır. Bu, sürüm kontrolünü temiz tutar ve GitHub’da gördüğünüz tipik düzeni yansıtır.

---

## Tam Çalışan Örnek

Hepsini bir araya getirdiğimizde, derleyip çalıştırabileceğiniz tam `DocxProcessor.java` dosyası şu şekilde:

```java
import com.aspose.words.*;

import java.io.File;

public class DocxProcessor {

    public static void main(String[] args) throws Exception {
        // ==== USER CONFIGURATION ====
        String inputPath        = "YOUR_DIRECTORY/corrupted.docx";
        String outputMarkdown   = "YOUR_DIRECTORY/output.md";
        String outputPdf        = "YOUR_DIRECTORY/output.pdf";
        String customMarkdown   = "YOUR_DIRECTORY/output_with_custom_images.md";

        // ==== 1️⃣ Load document with recovery mode ====
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER);
        Document doc = new Document(inputPath, loadOptions);

        // ==== 2️⃣ Export LaTeX while converting to markdown ====
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        doc.save(outputMarkdown, mdOptions);

        // ==== 3️⃣ Save as PDF, handling floating shapes ====
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save(outputPdf, pdfOptions);

        // ==== 4️⃣ Custom image folder for markdown export ====
        MarkdownSaveOptions customMdOptions = new MarkdownSaveOptions();
        customMdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                String imageFolder = "YOUR_DIRECTORY/images/";
                new File(imageFolder).mkdirs();
                args.setFileName(imageFolder + args.getFileName());
            }
        });
        doc.save(customMarkdown, customMdOptions);

        System.out.println("All exports completed successfully!");
    }
}
```

### Beklenen Çıktı

- `output.md` – LaTeX denklemleri (`$…$` ve `$$…$$`) içeren markdown dosyası.  
- `output.pdf` – yüksek çözünürlüklü PDF, yüzen şekiller satır içi etiketlere dönüştürülmüş.  
- `output_with_custom_images.md` – aynı markdown fakat tüm görüntüler `images/` altında depolanmış.  

Markdown dosyasını VS Code’da *Markdown Preview Enhanced* eklentisiyle açın; denklemler orijinal Word dosyasındaki gibi renderlanacaktır.

---

## Sık Sorulan Sorular (SSS)

**S: Bu .doc dosyalarıyla da çalışır mı, sadece .docx mi?**  
C: Evet. Aspose.Words formatı otomatik algılar. `inputPath`'deki dosya uzantısını değiştirmeniz yeterli.

**S: LaTeX yerine MathML istesem ne yapmalıyım?**  
C: `OfficeMathExportMode.LATEX` yerine `OfficeMathExportMode.MATHML` kullanın. Pipeline'in geri kalanı aynı kalır.

**S: PDF adımını atlayabilir miyim?**  
C: Kesinlikle. PDF bloğunu yorum satırı yapın. Kod modüler olduğu için **save document as PDF** sadece ihtiyacınız olduğunda çalıştırabilirsiniz.

**S: Şifre korumalı belgeler nasıl işlenir?**  
C: `Document` örneğini oluşturmadan önce `LoadOptions.setPassword("yourPassword")` çağırın.

**S: LaTeX'i doğrudan PDF'e gömebilir miyim?**  
C: Yerel olarak mümkün değil; PDF'ler LaTeX'i anlayamaz. Önce denklemleri görüntüye dönüştürmeniz gerekir, bu da temiz LaTeX dışa aktarma amacını bozar.

---

## Kenar Durumları ve İpuçları

- **Bozuk Görüntüler**: Bir görüntü okunamazsa Aspose.Words bir yer tutucu ekler. `ResourceSavingCallback` içinde `args.getStream().available()` kontrol ederek bunu tespit edebilirsiniz.
- **Büyük Belgeler**: 100 MB üzerindeki dosyalar için PDF çıktısını akış olarak kaydetmeyi (`doc.save(outputPdf, pdfOptions)` ve `outputPdf` bir `FileOutputStream`) düşünün; bellek baskısını azaltır.
- **Performans**: `RecoveryMode.IGNORE` yükleme hızını artırır ama içerik kaybına yol açabilir. Dengeli bir yaklaşım için `RECOVER` kullanın.
- **Lisans Uygulaması**: Deneme modunda kaydedilen her belge bir filigran alır. Lisans kaydedin ve filigranı kaldırın—`License license = new License(); license.setLicense("Aspose.Words.lic");` kodunu herhangi bir işlemden önce çağırın.

---

## Sonuç

İşte **Word dosyasından LaTeX dışa aktarma**, **docx'i markdown'a dönüştürme** ve **dökümanı PDF olarak kaydetme** işlemlerini tek bir düzenli Java programında nasıl yapacağınız. Geri kurtarma modunda yükleme, LaTeX dışa aktarma, yüzen‑şekil işleme ile PDF üretimi ve markdown için özel görüntü klasörleri konularını kapsadık.  

Şimdi diğer dışa aktarma formatları (HTML, EPUB) ile deneyler yapabilir, bu mantığı bir web servisine entegre edebilir ya da yüzlerce dosyayı toplu işleyebilirsiniz. Tüm yapı taşları hazır, Aspose.Words API'si ise workflow'u genişletmeyi sorunsuz hâle getiriyor.

Bu rehberi faydalı bulduysanız GitHub’da yıldız verin, ekip arkadaşlarınızla paylaşın ya da kendi ayarlamalarınızı aşağıya yorum olarak bırakın. İyi kodlamalar, LaTeX'iniz her zaman kusursuz renderlansın!

![Diagram showing the conversion pipeline from DOCX → Markdown (with LaTeX) → PDF, alt metin: "DOCX'ten markdown'a dönüştürürken LaTeX dışa aktarımı ve PDF olarak kaydetme sürecini gösteren diyagram"]{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}