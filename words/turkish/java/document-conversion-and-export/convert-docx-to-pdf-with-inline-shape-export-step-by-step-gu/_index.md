---
category: general
date: 2026-02-18
description: DOCX'i PDF'ye dönüştürmeyi ve Word'ü PDF olarak kaydederken yüzen şekilleri
  korumayı öğrenin. Bu kılavuz, şekilleri doğru bir şekilde dışa aktarmayı gösterir.
draft: false
keywords:
- convert docx to pdf
- save word as pdf
- how to export shapes
language: tr
og_description: DOCX'i PDF'ye dönüştürün ve şekilleri nasıl dışa aktaracağınızı öğrenin.
  Word'ü doğru etiketleme ile PDF olarak kaydetmek için bu kapsamlı öğreticiyi izleyin.
og_title: DOCX'yi PDF'ye Dönüştür – Satır İçi Şekil Dışa Aktarma Kılavuzu
tags:
- Aspose.Words
- Java
- PDF conversion
title: DOCX'i PDF'ye Dâhil Şekil Dışa Aktarma ile Dönüştür – Adım Adım Kılavuz
url: /tr/java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX'yi PDF'ye Dönüştür – Satır İçi Şekil Dışa Aktarma Kılavuzu

Hiç **DOCX'yi PDF'ye dönüştürmek** gerekti ve kayan resimlerinizin ya da metin kutularınızın kaybolacağından ya da yer değiştireceğinden endişe ettiniz mi? Yalnız değilsiniz. Birçok projede—otomatik rapor oluşturucularını veya toplu‑işlem hatlarını düşünün—bir Word belgesinin tam düzenini korumak tartışılmaz bir gerekliliktir.  

İyi haber? Birkaç satır kodla **Word'ü PDF olarak kaydedebilir** ve bu kayan şekillerin satır içi etiketler haline gelip gelmeyeceğini ya da blok‑seviyesinde kalıp kalmayacağını kontrol edebilirsiniz. Aşağıda tam olarak **şekilleri nasıl dışa aktaracağınızı** istediğiniz şekilde göreceksiniz, ayrıca yaygın tuzaklardan kaçınmanıza yardımcı olacak birkaç ipucu da bulacaksınız.

---

## Öğrenecekleriniz

* Diskten bir `.docx` dosyası yükleyin.  
* `PdfSaveOptions`'ı yapılandırarak kayan şekillerin satır içi etiketler olarak dışa aktarılmasını sağlayın.  
* Ortaya çıkan PDF'yi seçtiğiniz bir klasöre yazın.  
* `setExportFloatingShapesAsInlineTag` bayrağının neden önemli olduğunu ve ne zaman değiştirebileceğinizi anlayın.  

Harici hizmetler yok, sihirli “tıkla‑ve‑indir” UI'si yok—sadece herhangi bir Maven ya da Gradle projesine ekleyebileceğiniz saf Java kodu.

---

## Önkoşullar

| Requirement | Why it matters |
|-------------|----------------|
| **Aspose.Words for Java** (v23.12 or later) | Örnekte kullanılan `Document` ve `PdfSaveOptions` sınıflarını sağlar. |
| **JDK 8+** | Kütüphane Java 8 ve üzeri için derlenmiştir; daha eski çalışma zamanları `UnsupportedClassVersionError` hatası verir. |
| **A DOCX file** with at least one floating shape (image, text box, WordArt) | Şekil‑dışa aktarma seçeneğinin etkisini görmek için içinde gerçekten kayan nesneler bulunan bir belgeye ihtiyacınız var. |

Bu parçalar zaten elinizdeyse, harika—hadi başlayalım.

---

## 1. Adım – Kaynak Belgeyi Yükleyin  

İlk olarak, dönüştürmek istediğiniz `.docx` dosyasına işaret eden bir `Document` örneği oluştururuz. Yapıcı dosyayı belleğe okur, OpenXML paketini ayrıştırır ve iç nesne modelini hazırlar.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **Pro ipucu:** Bir döngüde birçok dosya işliyorsanız, `doc.close()` (veya çöp toplayıcının halletmesine izin vererek) çağırdıktan sonra tek bir `Document` nesnesini yeniden kullanın. Bu, Windows'ta dosya‑tanıtıcı sızıntılarını önler.

---

## 2. Adım – Şekilleri Dışa Aktarmak İçin PDF Kaydetme Seçeneklerini Yapılandırın  

Eğitimin kalbi burada. `PdfSaveOptions` dönüşümün nasıl davranacağını belirlemenizi sağlar. `setExportFloatingShapesAsInlineTag(true)` ayarını yapmak, her kayan şeklin PDF'in etiket yapısında *satır içi* bir öğe olarak ele alınmasını zorunlu kılar. Bu, ekran okuyucuların şekli çevredeki metinle aynı sırada okuması anlamına gelir ve genellikle erişilebilirlik uyumluluğu için gereklidir.

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**`false` olarak ne zaman ayarlarsınız?**  
PDF'iniz yalnızca baskı dağıtımı için tasarlandıysa ve şekillerin mantıksal okuma sırasını etkilemeden orijinal konumlarını korumasını istiyorsanız, blok‑seviyeli etiketlemeyi tercih edebilirsiniz. Varsayılan değer `false` olduğundan, bu eğitim için satır içi davranışı açıkça etkinleştiriyoruz.

---

## 3. Adım – Belgeyi PDF Olarak Kaydedin  

Seçenekler hazır olduğuna göre, hedef dosya adı ve seçenek nesnesiyle `save` metodunu çağırın. Kütüphane ağır işi halleder: yerleşim motoru, font gömme ve etiket oluşturma.

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

Çağrı tamamlandıktan sonra, belirtilen klasörde `shapes.pdf` dosyasını bulacaksınız. Adobe Acrobat'ta ya da etiketleri gösteren herhangi bir PDF görüntüleyicide (genellikle **File → Properties → Tags** altında) açın ve kayan şeklin satır içi bir etiket olarak göründüğünü göreceksiniz.

---

## Tam, Çalıştırılabilir Örnek  

Hepsini bir araya getirerek, derleyip çalıştırabileceğiniz bağımsız bir Java sınıfı burada. Aspose.Words JAR'ının sınıf yolunuzda (classpath) olduğundan emin olun.

```java
import com.aspose.words.*;

public class DocxToPdfWithShapes {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF options – export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → inline tagging

            // 3️⃣ Save as PDF
            String outputPath = "YOUR_DIRECTORY/shapes.pdf";
            doc.save(outputPath, pdfOptions);

            System.out.println("✅ Conversion complete! PDF saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("❌ Something went wrong: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Beklenen sonuç:**  
- PDF dosyası, orijinal DOCX ile aynı metin içeriğini içerir.  
- Tüm kayan resimler veya metin kutuları artık *satır içi* olarak etiketlenmiştir, yani ayrı bloklar yerine okuma sırasına göre görünürler.  
- PDF'in **Tags** panelini açarsanız, `<Paragraph>` içinde gömülü bir `<Figure>` öğesi göreceksiniz—tam olarak `setExportFloatingShapesAsInlineTag(true)`'ın garantisi.

---

## Sıkça Sorulan Sorular & Kenar Durumları  

### 1️⃣ Bu, şifre‑korumalı DOCX dosyalarıyla çalışır mı?  
Evet—yüklemeden önce şifreyi sağlayın:

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

### 2️⃣ Word dosyasındaki SVG veya EMF görüntüler ne olur?  
Aspose.Words PDF'ye kaydederken vektör grafikleri otomatik olarak rasterleştirir. Vektör olarak kalmalarını istiyorsanız, şu ayarı yapın:

```java
pdfOptions.setRasterizeTransformedElements(false);
```

### 3️⃣ Dönüştürürken hiperlinkleri nasıl korurum?  
Bağlantılar varsayılan olarak korunur. Ancak, etiketleri devre dışı bırakırsanız (`pdfOptions.setSaveFormat(SaveFormat.PDF)` seçenek olmadan), mantıksal yapıyı kaybedebilirsiniz. Hem etiketleri hem de bağlantıları tutmak için `PdfSaveOptions` nesnesini koruyun.

### 4️⃣ DOCX dosyalarının bir klasörünü toplu‑işlem yapabilir miyim?  
Kesinlikle. `DocxToPdfWithShapes` mantığını `Files.list(Paths.get("YOUR_DIRECTORY"))` üzerinde dönen bir döngüye sarın. Her dosya için istisnaları yakalamayı unutmayın; böylece tek bir hatalı belge tüm çalışmayı durdurmaz.

---

## Saha İpuçları  

* **Eksik fontlara dikkat edin.** Kaynak DOCX, sunucuda yüklü olmayan özel bir font kullanıyorsa, PDF bir yedek fontla değiştirir ve düzen bozulabilir. Gömmeyi zorlamak için `pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)` kullanın.  
* **Erişilebilirlik testi.** Dönüştürmeden sonra Acrobat'ın **Accessibility Checker** aracını çalıştırın. Satır içi etiketleme genellikle puanı artırır, ancak yine de görüntülere alternatif metin eklemeniz gerekebilir.  
* **Performans ipucu:** Büyük belgeler (100+ sayfa) için `pdfOptions.setMemoryOptimization(true)`'ı etkinleştirerek yığın (heap) kullanımını azaltın.

---

## Görsel Doğrulama  

Aşağıda, Adobe Acrobat'ta açılmış PDF'in hızlı bir ekran görüntüsü yer alıyor; **Tags** bölmesinde satır içi etiketlenmiş şekil vurgulanmış olarak gösteriliyor.

![DOCX'yi PDF'ye dönüştürme örnek çıktısı](image.png)

*Alt metin: inline şekil etiketlerini gösteren DOCX'yi PDF'ye dönüştürme örnek çıktısı.*

---

## Özet  

Artık **DOCX'yi PDF'ye nasıl dönüştüreceğinizi** ve kayan nesnelerin dışa aktarım şeklini kontrol ettiğinizi biliyorsunuz. `setExportFloatingShapesAsInlineTag`'ı değiştirerek, şekillerin okuma sırasının bir parçası olup olmayacağına ya da bağımsız bloklar olarak kalacağına karar verirsiniz—bu, erişilebilirlik ve görsel doğruluk açısından kritik öneme sahiptir.

Buradan şunları yapabilirsiniz:

* Arşivleme için Word'ü toplu olarak **PDF olarak kaydedin**.  
* Uzun vadeli koruma için `setCompliance(PdfCompliance.PDF_A_1B)` gibi diğer `PdfSaveOptions` seçeneklerini deneyin.  
* Tam Aspose.Words belgelerini inceleyerek veya daha zengin etiket ağaçları için `setExportDocumentStructure(true)` bayrağını deneyerek **şekilleri nasıl dışa aktaracağınızı** daha derinlemesine keşfedin.

Bir deneyin, seçenekleri ayarlayın ve PDF'lerinizin tam istediğiniz gibi görünmesini sağlayın. Kodlamanın tadını çıkarın!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}