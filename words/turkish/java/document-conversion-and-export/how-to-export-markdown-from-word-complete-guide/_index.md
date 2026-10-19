---
category: general
date: 2026-04-28
description: DOCX dosyasından markdown dışa aktarma ve resimleri çıkarma. Docx'i markdown'a
  dönüştürmeyi, resimleri bir klasöre yerleştirmeyi ve Word'ü markdown olarak kaydetmeyi
  öğrenin.
draft: false
keywords:
- how to export markdown
- convert docx to markdown
- extract images from docx
- how to place images
- save word as markdown
language: tr
og_description: Java'da bir DOCX dosyasından markdown nasıl dışa aktarılır. Bu öğretici,
  docx'i markdown'a dönüştürmeyi, görüntüleri çıkarmayı ve düzenlemeyi gösterir.
og_title: Word'den Markdown Nasıl Dışa Aktarılır – Tam Rehber
tags:
- Aspose.Words
- Java
- Markdown
- Document Conversion
title: Word'den Markdown Nasıl Dışa Aktarılır – Tam Kılavuz
url: /tr/java/document-conversion-and-export/how-to-export-markdown-from-word-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'ten Markdown Nasıl Dışa Aktarılır – Tam Kılavuz

Word belgesinden gömülü resimlerin hiçbirini kaybetmeden **markdown nasıl dışa aktarılır** diye hiç merak ettiniz mi? Tek başınıza değilsiniz. Birçok geliştirici, statik site jeneratörleri, dokümantasyon siteleri veya GitHub README dosyaları için temiz bir Markdown dosyası ve düzenli bir resim klasörü gerektiğinde bir çıkmaza takılıyor.

Bu öğreticide **docx'i markdown'a dönüştürmek**, kaynaktan her resmi çıkarmak ve **görselleri** bir `img` alt‑klasörüne **yerleştirmek** için tam adımları göstereceğiz, böylece ortaya çıkan Markdown referansları bozulmaz. Sonunda `output.md` dosyasını bir `img` diziniyle birlikte yayınlamaya hazır olarak elde edeceksiniz—manuel kopyala‑yapıştırma gerekmez.

> **Neler elde edeceksiniz:** Aspose.Words kullanan çalıştırılabilir bir Java kod parçacığı, her satırın neden önemli olduğuna dair net bir açıklama ve SVG görüntüler veya büyük ikili dosyalar gibi uç durumları ele almak için ipuçları.

*Önkoşullar:* Java 8+ yüklü, bir IDE (IntelliJ IDEA, Eclipse veya VS Code) ve geçerli bir Aspose.Words for Java lisansı (ücretsiz deneme, deneyler için yeterlidir).

---

## Word Belgesinden Markdown Nasıl Dışa Aktarılır

### Adım 1: Kaynak Belgeyi Yükleyin  

Herhangi bir dönüşüm gerçekleşmeden önce, DOCX dosyasını belleğe almamız gerekir. Aspose.Words bir Word dosyasını `Document` sınıfı ile temsil eder.

```java
import com.aspose.words.Document;
import com.aspose.words.License;

// Load your license (optional for trial)
License license = new License();
license.setLicense("Aspose.Words.Java.lic");

// Step 1 – read the .docx file
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Neden önemli:* Dosyanın yüklenmesi formatı doğrular ve belge ağacına (paragraflar, koşular, görseller) erişim sağlar. Dosya bozuksa, Aspose net bir istisna fırlatır ve sonradan çokça hata ayıklamaktan sizi kurtarır.

### DOCX'i Markdown'a Dönüştür – Seçenekleri Ayarlama  

`MarkdownSaveOptions` nesnesi Aspose'a belgeyi nasıl serileştireceğini söyler. Varsayılan davranış, Markdown dosyasıyla aynı klasöre işaret eden resim bağlantıları yazar. Bunu bir sonraki adımda değiştireceğiz.

```java
import com.aspose.words.MarkdownSaveOptions;
import com.aspose.words.ResourceSavingArgs;
import com.aspose.words.IResourceSavingCallback;
import com.aspose.words.ResourceType;

// Step 2 – configure Markdown export
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

*Pro ipucu:* GitHub‑tarzı Markdown'a ihtiyacınız varsa, `mdOptions.setExportImagesAsBase64(false);` ayarlayarak görselleri veri URI'ları olarak gömmek yerine ayrı dosyalar olarak tutun.

### DOCX'den Görselleri Dışa Aktarırken Çıkarın  

Şimdi en lezzetli kısım geliyor: DOCX'ten her resmi çıkarmak ve bir `img` klasörüne koymak. `IResourceSavingCallback`, kaydetme işlemi sırasında Aspose'un yazdığı her dış kaynağa (görseller, yazı tipleri vb.) tetiklenir.

```java
// Step 3 – tell Aspose where to put image resources
mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Only act on image resources
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Build a path like "img/picture1.png"
            String newName = "img/" + args.getResourceFileName();
            args.setResourceFileName(newName);

            // Optional: you could compress the image here
            // InputStream original = args.getResourceStream();
            // args.setResourceStream(compress(original));
        }
    }
});
```

*Neden bir geri çağırma (callback) kullanıyoruz:* Olmasaydı, Aspose görselleri `output.md` ile aynı dizine dağıtırdı ve deponuz karışık olurdu. Geri çağırma, adlandırma, klasör yapısı ve hatta son‑işleme (ör. PNG yeniden boyutlandırma) üzerinde tam kontrol sağlar.

### Word'ü Markdown Olarak Kaydet – Son Yazma  

Belge yüklendi ve kaydetme seçenekleri ayarlandıktan sonra, sonunda Markdown dosyasını yazarız. Görseller otomatik olarak tanımladığımız `img` alt‑klasörüne kaydedilir.

```java
// Step 4 – write the Markdown file
doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

Her şey sorunsuz giderse, şu sonuca sahip olacaksınız:

```
YOUR_DIRECTORY/
├─ input.docx
├─ output.md
└─ img/
   ├─ image1.png
   ├─ image2.jpg
   └─ ...
```

`output.md` dosyasını herhangi bir editörde açın ve `![Image 1](img/image1.png)` gibi Markdown resim sözdizimini göreceksiniz. Bağlantılar zaten göreceli, bu yüzden GitHub, MkDocs veya herhangi bir statik site jeneratöründe çalışır.

---

## Görselleri Alt‑Klasöre Nasıl Yerleştirirsiniz (Gelişmiş Seçenekler)

Bazen `assets/images/` gibi daha derin bir hiyerarşiye ihtiyaç duyarsınız. Sadece geri çağırmayı (callback) ayarlayın:

```java
String newName = "assets/images/" + args.getResourceFileName();
args.setResourceFileName(newName);
```

Veya dosyaları daha açıklayıcı bir şeyle yeniden adlandırmak isterseniz (ör. çevreleyen paragraf temelinde), geri çağırma içinde `args.getResourceFileName()` ve `args.getDocumentNode()` inceleyebilirsiniz. Bu esneklik, **görselleri nasıl yerleştirirsiniz** sorusunun sıkça insanları zorlamasının nedeni—Aspose size kancayı verir, siz mantığı sağlarsınız.

### SVG veya Desteklenmeyen Formatlarla Baş Etme  

Aspose.Words çoğu raster formatını kutudan çıkar çıkmaz dönüştürür. SVG için, önce rasterleştirmeniz gerekebilir:

```java
if (args.getResourceFileName().endsWith(".svg")) {
    // Convert SVG to PNG on the fly (requires a third‑party lib)
    InputStream svgStream = args.getResourceStream();
    InputStream pngStream = convertSvgToPng(svgStream);
    args.setResourceStream(pngStream);
    args.setResourceFileName(args.getResourceFileName().replace(".svg", ".png"));
}
```

*Uç durum notu:* Tüm Markdown renderlayıcıları SVG'yi satır içi desteklemez. PNG'ye dönüştürmek uyumluluğu garanti eder.

---

## Word'ü Markdown Olarak Kaydet – Tam Çalışan Örnek  

Aşağıda tam, çalıştırmaya hazır program yer alıyor. `Main.java` dosyasına kopyalayıp yapıştırın, yolları ayarlayın ve **Run** tuşuna basın.

```java
// Main.java
import com.aspose.words.*;

public class Main {
    public static void main(String[] args) throws Exception {
        // --------------------------------------------------------------------
        // 1️⃣ Load the DOCX file
        // --------------------------------------------------------------------
        License license = new License();
        // Uncomment the next line if you have a license file
        // license.setLicense("Aspose.Words.Java.lic");

        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // --------------------------------------------------------------------
        // 2️⃣ Prepare Markdown options
        // --------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        // Keep images as separate files (GitHub‑flavored)
        mdOptions.setExportImagesAsBase64(false);

        // --------------------------------------------------------------------
        // 3️⃣ Callback – extract and relocate images
        // --------------------------------------------------------------------
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                if (args.getResourceType() == ResourceType.IMAGE) {
                    // Place every image in the "img" folder
                    String newName = "img/" + args.getResourceFileName();
                    args.setResourceFileName(newName);

                    // Example: compress PNGs (pseudo‑code)
                    // if (newName.endsWith(".png")) {
                    //     args.setResourceStream(compressPng(args.getResourceStream()));
                    // }
                }
            }
        });

        // --------------------------------------------------------------------
        // 4️⃣ Save as Markdown
        // --------------------------------------------------------------------
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        System.out.println("✅ Markdown export complete! Check the img folder for pictures.");
    }
}
```

**Beklenen sonuç:** `output.md` temiz Markdown metni içerir ve her resim referansı `img/<filename>`'e işaret eder. Dosyayı VS Code'un Markdown önizlemesinde açarak resimlerin doğru şekilde render edildiğini doğrulayın.

---

## Yaygın Sorular & Tuzaklar

| Soru | Cevap |
|----------|--------|
| *DOCX'im gömülü yazı tipleri içeriyorsa ne olur?* | Gerekliyse `mdOptions.setExportFontsAsBase64(true)` ayarlayın, ancak çoğu Markdown işlemcisi yazı tiplerini görmez. |
| *Farklı bir klasör yapısına dışa aktarabilir miyim?* | Kesinlikle—geri çağırmadaki `newName` dizesini istediğiniz herhangi bir yola değiştirin. |
| *Bu .doc dosyalarıyla çalışır mı?* | Evet. Aspose.Words `.doc` dosyasını aynı şekilde okur; sadece `Document` yapıcısındaki dosya uzantısını değiştirin. |
| *Büyük görsellerle ne yapılmalı?* | Geri çağırma içinde bir sıkıştırma adımı eklemeyi düşünün (ör. kaliteyi düşürmek için `javax.imageio` kullanarak). |
| *Üretim için lisans gerekli mi?* | Ücretsiz deneme, çıktının ilk sayfasına bir filigran ekler. Ticari kullanım için, filigranı kaldırmak üzere bir lisans alın. |

## Sonuç

Artık bir Word dosyasından **markdown nasıl dışa aktarılır**, **docx'i markdown'a dönüştürülür**, **docx'ten görseller nasıl çıkarılır** ve **görsellerin nasıl bir klasöre yerleştirileceği** konusunda bilgi sahibisiniz—tüm bunlar Aspose.Words kullanan birkaç Java satırıyla. Yukarıdaki tam örnek herhangi bir projeye eklemeye hazır ve geri çağırmayı (callback) özel adlandırma şemalarına veya ek son‑işlem adımlarına uyacak şekilde ayarlayabilirsiniz.

Sonraki adımlar? Oluşturulan Markdown'ı Jekyll veya Hugo gibi bir statik site jeneratörüne beslemeyi deneyin, farklı görüntü formatlarıyla deney yapın veya bu dönüşümü otomatik bir CI boru hattına bağlayın. Aynı desen PDF, HTML veya hatta düz metin için de çalışır—sadece `SaveOptions` sınıfını değiştirin.

Kodlamaktan keyif alın ve belgelerinizin her zaman temiz ve görsel açısından zengin olmasını dileriz!

---  

![Word'ten markdown dışa aktarımını gösteren diyagram – DOCX'ten Markdown'a akış ve alt‑klasördeki görseller](https://example.com/placeholder.png "markdown dışa aktarma diyagramı")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}