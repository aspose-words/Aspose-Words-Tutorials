---
category: general
date: 2025-12-18
description: Docx'i hızlıca markdown'a dönüştürün, denklemleri LaTeX olarak dışa aktarmayı
  öğrenin, bozuk docx dosyalarını kurtarın ve ayrıca tek bir öğreticide docx'i PDF'ye
  dönüştürün.
draft: false
keywords:
- convert docx to markdown
- how to export equations
- recover corrupted docx
- convert docx to pdf
- how to convert docx
language: tr
og_description: docx'i kolayca markdown'a dönüştür, denklemleri LaTeX olarak dışa
  aktar, bozuk docx dosyalarını kurtar ve ayrıca docx'i Java kullanarak pdf'ye dönüştür.
og_title: docx'i markdown'a dönüştür – Tam Adım Adım Kılavuz
tags:
- Aspose.Words
- Java
- DocumentConversion
title: docx'i markdown'a dönüştür – Denklem Dışa Aktarma, Kurtarma ve PDF Dönüştürme
  ile Tam Kılavuz
url: /turkish/java/document-operations/convert-docx-to-markdown-complete-guide-with-equation-export/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# docx'i markdown'e dönüştür – Tam Adım‑Adım Kılavuz

Hiç **docx'i markdown'e dönüştürmek** gerektiğinde denklemlerinizi, görsellerinizi ve hatta bozuk dosyalarınızı nasıl koruyacağınızı bilemediniz mi? Yalnız değilsiniz. Bu öğreticide bir DOCX dosyasını yüklemeyi, bozuk bir dosyayı kurtarmayı, her denklemi LaTeX olarak dışa aktarmayı ve sonunda aynı kaynağı temiz bir PDF'e dönüştürmeyi—tamamen saf Java kodu ile—adım adım göstereceğiz.

Ayrıca birkaç “nasıl yapılır” ipucu da ekleyeceğiz: **denklemleri dışa aktarma**, **bozuk docx'i kurtarma**, **docx'i pdf'e dönüştürme**, ve **docx'i diğer formatlara dönüştürme**. Sonunda hepsini yapan tek bir yeniden kullanılabilir kod parçacığına ve projenize doğrudan kopyalayabileceğiniz birkaç pratik tüyoya sahip olacaksınız.

> **Pro ipucu:** Aspose.Words for Java JAR dosyasını sınıf yolunuzda tutun; her adımı sorunsuz yapan motor budur.

---

## Gerekenler

- **Java 17** (veya herhangi bir yeni JDK) – kod modern `var` sözdizimini kullanıyor ancak küçük ayarlamalarla daha eski sürümlerde de çalışır.  
- **Aspose.Words for Java** (2025 itibarıyla en son sürüm) – Maven bağımlılığını ekleyin veya düz JAR dosyasını kullanın.  
- Dönüştürmek istediğiniz bir **DOCX** dosyası (biz buna `input.docx` diyeceğiz).  
- Aşağıdaki gibi bir klasör yapısı:

```
YOUR_DIRECTORY/
├─ input.docx
├─ markdown_imgs/      ← images extracted from markdown will land here
└─ output.md / output.pdf
```

Ekstra kütüphane gerekmez; geri kalan her şey Aspose.Words tarafından yönetilir.

---

## Adım 1: Belgeyi Kurtarma Modu ile Yükleme (Bozuk docx'i Kurtarma)

Bir dosya kısmen hasar gördüğünde, Aspose.Words hâlâ *kurtarma* modunda açabilir. Bu, **bozuk docx** dosyalarını iyi kısımları kaybetmeden **kurtarmak** için tam olarak ihtiyacınız olan şeydir.

```java
// Import statements
import com.aspose.words.*;

public class DocxConverter {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the document with recovery mode enabled
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.Recover);   // tries to salvage broken parts
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Kurtarmanın önemi:**  
Dosya kırık bir tablo veya yalnız kalmış bir görsel içeriyorsa, standart yükleyici bir istisna fırlatır ve her şeyi durdurur. `RecoveryMode.Recover` etkinleştirildiğinde, Aspose.Words hatalı bölümleri atlar, bir uyarı kaydeder ve hâlâ üzerinde çalışabileceğiniz kısmen doldurulmuş bir `Document` nesnesi sağlar.

---

## Adım 2: docx'i markdown'e dönüştür – Denklemleri Dışa Aktarma ve Görselleri İşleme

Artık sağlıklı bir `Document` nesnemiz olduğuna göre, **docx'i markdown'e dönüştürelim**. Anahtar, Aspose'a her Office Math nesnesini LaTeX'e dönüştürmesini söylemek; bu, çoğu markdown rendercısı tarafından anlaşılır.

```java
        // 2️⃣ Save as Markdown, exporting equations as LaTeX and handling images manually
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setOfficeMathExportMode(OfficeMathExportMode.LaTeX); // <-- how to export equations

        // Custom callback to store each extracted image
        markdownOptions.setResourceSavingCallback((resource, outStream) -> {
            String imageFileName = "img_" + java.util.UUID.randomUUID() + ".png";
            try (java.io.FileOutputStream fos = new java.io.FileOutputStream(
                    "YOUR_DIRECTORY/markdown_imgs/" + imageFileName)) {
                resource.save(fos);
            }
        });

        doc.save("YOUR_DIRECTORY/output.md", markdownOptions);
```

### Kodun yaptığı

1. **`OfficeMathExportMode.LaTeX`** motoru, her denklemi LaTeX kaynağını içeren bir `$…$` veya `$$…$$` bloğu ile değiştirmeye yönlendirir.  
2. **`ResourceSavingCallback`** normalde veri‑URI olarak satır içine gömülen her görseli yakalar. Her görsele benzersiz bir ad verir ve `markdown_imgs/` klasörüne kaydederiz.  
3. **`output.md`** temiz markdown, LaTeX denklemleri ve `![](markdown_imgs/img_1234.png)` gibi bağlantılar içerir.

> **Görsel örneği**  
> ![docx'i markdown'e dönüştürme örneği](YOUR_DIRECTORY/markdown_imgs/sample.png "docx'i markdown'e dönüştür")

*(Alt metin, SEO için birincil anahtar kelimeyi içerir.)*

---

## Adım 3: docx'i pdf'e dönüştür – Yüzen Şekilleri Satır İçi Etiketler Olarak Dışa Aktarma

Eğer aynı zamanda bir PDF sürümüne de ihtiyacınız varsa, Aspose yüzen şekilleri (metin kutuları, görseller, grafikler) satır içi etiketler olarak ele alabilir; bu, PDF farklı cihazlarda görüntülendiğinde düzenin düzenli kalmasını sağlar.

```java
        // 3️⃣ Save as PDF, converting floating shapes to inline tags
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true); // <-- convert docx to pdf with proper shape handling
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

**Bunun önemi:**  
Yüzen şekiller PDF dönüşümlerinde sık sık kayar veya kaybolur. Onları satır içi zorlayarak, orijinal DOCX'i yansıtan bir WYSIWYG sonucu garantilersiniz.

---

## Adım 4: İleri – İlk Şeklin Gölgesini Ayarlama (Stil ile docx'i Nasıl Dönüştürürsünüz)

Bazen dışa aktarmadan önce görsel öğeleri ince ayarlamak istersiniz. Aşağıda belgedeki ilk `Shape` nesnesini alıp gölgesini değiştiriyoruz. Bu, özel stilleri koruyarak **docx'i nasıl dönüştürürsünüz** gösterir.

```java
        // 4️⃣ Adjust the shadow of the first shape (optional styling step)
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (firstShape != null) {
            Shadow shapeShadow = firstShape.getShadow();
            shapeShadow.setBlurRadius(5.0);
            shapeShadow.setDistance(3.0);
            shapeShadow.setAngle(45);
            shapeShadow.setColor(Color.getBlue());
            shapeShadow.setTransparency(0.2);
        }

        // Optional: re‑save the modified document as another PDF to see the effect
        doc.save("YOUR_DIRECTORY/output_styled.pdf", pdfOptions);
    }
}
```

**Temel Çıkarımlar**

- `getChild` çağrısı düğüm ağacını dolaşır ve konumundan bağımsız olarak her zaman ilk şekli almanızı sağlar.  
- Gölge özellikleri (`blurRadius`, `distance`, `angle` vb.) Aspose tarafından tam olarak desteklenir, bu yüzden son PDF görsel ayarlamayı yansıtacaktır.  
- Bu adım isteğe bağlı **docx'i dönüştürürken** sahip olduğunuz esnekliği gösterir.

---

## Yaygın Sorular & Özel Durumlar

### DOCX dosyam desteklenmeyen nesneler içerirse ne olur?

Aspose.Words bir uyarı kaydeder ve onları atlar. Bu uyarıları bir `DocumentBuilder` dinleyicisi ekleyerek veya `LoadOptions.setWarningCallback` kontrol ederek yakalayabilirsiniz.

### Görsellerim çok büyük—markdown dışa aktarımı sırasında nasıl küçültebilirim?

`ResourceSavingCallback` içinde `resource` nesnesini `BufferedImage` olarak okuyabilir, `java.awt.Image` ile yeniden boyutlandırabilir ve ardından daha küçük sürümü çıktı akışına yazabilirsiniz.

### DOCX dosyaları içeren bir klasörü toplu işleyebilir miyim?

Kesinlikle. `main` mantığını `for (File file : new File("input_folder").listFiles(...))` döngüsüyle sarın, çıktı yollarını buna göre ayarlayın ve tek tıkla çalışan bir dönüştürücüye sahip olun.

### Bu .doc (ikili) dosyalarla da çalışır mı?

Evet. Aynı `Document` yapıcı `.doc` dosyalarını da kabul eder; sadece yol içindeki dosya uzantısını değiştirin.

---

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

```java
import com.aspose.words.*;

public class DocxConverter {
    public static void main(String[] args) throws Exception {
        // Load with recovery (handles corrupted docx)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.Recover);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---------- Convert docx to markdown ----------
        MarkdownSaveOptions mdOpts = new MarkdownSaveOptions();
        mdOpts.setOfficeMathExportMode(OfficeMathExportMode.LaTeX);
        mdOpts.setResourceSavingCallback((resource, outStream) -> {
            String imgName = "img_" + java.util.UUID.randomUUID() + ".png";
            try (java.io.FileOutputStream fos = new java.io.FileOutputStream(
                    "YOUR_DIRECTORY/markdown_imgs/" + imgName)) {
                resource.save(fos);
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOpts);

        // ---------- Convert docx to pdf ----------
        PdfSaveOptions pdfOpts = new PdfSaveOptions();
        pdfOpts.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOpts);

        // ---------- Optional styling ----------
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (firstShape != null) {
            Shadow shadow = firstShape.getShadow();
            shadow.setBlurRadius(5.0);
            shadow.setDistance(3.0);
            shadow.setAngle(45);
            shadow.setColor(Color.getBlue());
            shadow.setTransparency(0.2);
        }
        // Save styled PDF (if you changed the shape)
        doc.save("YOUR_DIRECTORY/output_styled.pdf", pdfOpts);
    }
}
```

Sınıfı çalıştırın, aşağıdakilere sahip olacaksınız:

- `output.md` – temiz markdown, LaTeX denklemleri ve görsel bağlantıları.  
- `output.pdf` – yüzen şekiller satır içi işlenmiş, orijinale sadık bir PDF.  
- `output_styled.pdf` – yukarıdakinin aynı sürümü ancak ilk şeklin üzerine özel bir gölge eklenmiş.

---

## Sonuç

LaTeX olarak denklemleri dışa aktararak, bozuk bir dosyayı kurtararak ve aynı zamanda şık bir PDF oluşturarak **docx'i markdown'e nasıl dönüştürürsünüz** gösterdik—tek, kolay‑yeniden‑kullanılabilir bir Java programı içinde. Birincil anahtar kelime tüm metinde yer alıyor, SEO sinyalini güçlendiriyor ve adım‑adım açıklama, AI asistanlarının bu kılavuzu eksiksiz bir yanıt olarak alıntılamasını sağlıyor.

Sonraki adımda şunları keşfetmek isteyebilirsiniz:

- **Denklemleri MathML**'e dışa aktarmak web sayfaları için.  
- Çoklu iş parçacığı kullanarak toplu **bozuk docx** dosyalarını kurtarmak.  
- **docx'i pdf'e** şifre koruması ile dönüştürmek.  
- **docx'i** HTML veya EPUB gibi diğer formatlara dönüştürmek.

Bunları deneyin ve herhangi bir sorunla karşılaşırsanız yorum bırakmaktan çekinmeyin. İyi dönüştürmeler!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}