---
category: general
date: 2026-03-19
description: Aspose.Words for Java'da uyarıların nasıl yakalanacağını ve eksik yazı
  tiplerinin nasıl tespit edileceğini öğrenin. Bu adım adım kılavuz, eksik yazı tiplerini
  nazikçe nasıl ele alacağınızı da gösterir.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: tr
og_description: Aspose.Words for Java'da uyarıları yakalama, eksik fontları tespit
  etme ve eksik fontları işleme hakkında tam bir kod örneği.
og_title: Uyarıları Yakalama – Aspose.Words'ta Eksik Yazı Tiplerini Tespit Etme
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Uyarıları Yakalama – Aspose.Words'ta Eksik Yazı Tiplerini Tespit Etme
url: /tr/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uyarıları Yakalama – Aspose.Words'ta Eksik Yazı Tiplerini Tespit Etme

Bir Word belgesi yüklendiğinde ve bazı yazı tipleri makinede bulunmadığında **uyarıların nasıl yakalanacağını** hiç merak ettiniz mi? Tek başınıza değilsiniz. Gerçek dünyadaki birçok projede, eksik yazı tipleri sessiz yerleşim kaymalarına neden olur ve ne olduğunu öğrenmenin tek yolu, Aspose.Words'ün yaydığı uyarı akışını dinlemektir.  

Bu öğreticide, **eksik yazı tiplerini tespit eden**, size programlı olarak **eksik yazı tiplerini nasıl tespit edeceğinizi** gösteren ve hatta çıktınızın öngörülebilir kalması için **eksik yazı tiplerini nasıl ele alacağınız** konusunda hızlı bir ipucu veren, eksiksiz ve çalıştırmaya hazır bir örnek üzerinden ilerleyeceğiz.

> **Hızlı not:** Kod, Aspose.Words 23.9 (veya daha yeni) sürümleriyle çalışır ve Java 8+ gerektirir.

---

## Gerekenler

- **Aspose.Words for Java** (Maven/Gradle bağımlılığı veya sınıf yolunda JAR)  
- Sisteminizde yüklü olmayan bir yazı tipine (ör. “Comic Sans MS”) başvuran bir Word dosyası (`input.docx`)  
- Bir Java IDE'si veya basit `javac`/`java` komut satırı kurulumu  

Başka bir kütüphane gerekmez—diğer her şey Aspose.Words paketinin içinde bulunur.

---

## Adım 1 – Uyarıları Yakalamak İçin LoadOptions'ı Ayarlama  

Uyarıları dinlemeye başlamak için bir `LoadOptions` örneği oluşturmanız gerekir. Bu nesne, yükleyiciye eksik yazı tipleri gibi karşılaştığı sorunları izlemeyi söyler.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Neden önemli:** `LoadOptions` olmadan, yükleyici eksik yazı tiplerini sessizce varsayılan sistem yazı tipine değiştirir ve bir ikame gerçekleştiğini asla öğrenemezsiniz. Uyarıları etkinleştirmek size tam görünürlük sağlar.

## Adım 2 – LoadOptions Kullanarak Belgeyi Yükleme  

Şimdi belgeyi gerçekten yüklüyoruz. Az önce oluşturduğumuz `LoadOptions` yapıcıya geçirilir, böylece ayrıştırma sırasında üretilen tüm uyarılar yakalanır.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Pro ipucu:** Bir toplu işlemde çok sayıda dosya işliyorsanız, gereksiz nesne oluşturmayı önlemek için aynı `LoadOptions` örneğini yeniden kullanın.

## Adım 3 – Yakalanan Uyarılar Üzerinde Döngü  

Aspose.Words her uyarıyı bir `WarningInfo` nesnesi olarak saklar. Sadece yazı tipiyle ilgili uyarılarla ilgileniyoruz, bu yüzden `FontSubstitutionWarningInfo` üzerinden filtreleme yapıyoruz.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Açıklama:**  
- `document.getWarnings()` yükleme sırasında oluşan tüm uyarıların bir listesini döndürür.  
- `FontSubstitutionWarningInfo` iki kritik veri içerir: **istek yapılan yazı tipi** (DOCX'in istediği) ve Aspose.Words'ün geri döndüğü **gerçek yazı tipi**.  
- İkisini de yazdırarak, hangi yazı tiplerinin eksik olduğunu ve hangi ikamenin gerçekleştiğini anında görürsünüz.

## Adım 4 – (İsteğe Bağlı) Eksik Yazı Tiplerini Programlı Olarak Ele Alma  

Uyarıları yakalamak sadece hikayenin yarısıdır. Bir yazı tipinin eksik olduğunu öğrendikten sonra, özel bir ikame sağlayarak veya sorunu daha sonra incelemek üzere kaydederek **eksik yazı tiplerini ele almak** isteyebilirsiniz.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Bunu neden yapmalı?**  
- Makinalar arasında tutarlı render almayı garantiler.  
- Daha sonra oluşturulan PDF'lerde veya görüntülerde beklenmeyen yerleşim değişikliklerini önler.  

Uyarı detaylarını bir veritabanında saklayabilir, içerik ekibine e-posta gönderebilir veya kritik bir yazı tipi eksikse süreci iptal edebilirsiniz.

## Tam Çalışan Örnek  

Aşağıda eksiksiz, çalıştırılabilir program yer alıyor. `YOUR_DIRECTORY/input.docx` ifadesini test dosyanızın yolu ile değiştirin, Aspose.Words JAR'ını sınıf yolunuza ekleyin ve çalıştırın.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Beklenen çıktı** (“Comic Sans MS” eksik olduğunda):

```
Requested: Comic Sans MS → Substituted: Arial
```

İsteğe bağlı geri dönüş kodu çalıştıktan sonra, kaydedilen `output.docx`, “Comic Sans MS” orijinal olarak referans verilen her yerde **Arial** kullanarak renderlanacaktır.

## Yaygın Sorular & Kenar Durumları  

| Soru | Cevap |
|----------|--------|
| *Belge birden fazla eksik yazı tipine sahipse ne olur?* | Döngü her biri için bir uyarı yayar. Bunları toplu işleme için bir `Map<String, String>` içinde toplayabilirsiniz. |
| *Bu, belgeden oluşturulan PDF'ler için çalışır mı?* | Kesinlikle. Yazı tipi ikamesi yükleme aşamasında gerçekleşir, bu yüzden sonraki tüm dışa aktarmalar (PDF, HTML, görüntü) çözülen yazı tiplerini kullanır. |
| *Uyarıları yakalamak yerine bastırabilir miyim?* | Evet—`loadOptions.setWarningCallback(null);` olarak ayarlayın; ancak eksik yazı tiplerini görme imkanını kaybedersiniz. |
| *Kaydetme sonrası uyarı listesi temizlenir mi?* | Uyarı koleksiyonu `Document` örneğine aittir. `document.save()` çağırdıktan sonra, yeni bir `Document` oluşturmadığınız sürece liste değişmeden kalır. |
| *DOCX içinde gömülü özel yazı tipleri ne olur?* | Gömülü yazı tipleri mevcut olarak kabul edilir; Aspose.Words, bunları ana sistemde yüklü olmasalar bile kullanır. |

## Üretim Kullanımı İçin Pro İpuçları  

- **FontSettings Önbellekle:** Yüzlerce dosya işliyorsanız, tercih ettiğiniz geri dönüşlerle tek bir `FontSettings` oluşturun ve aşırı yüklemeyi önlemek için yeniden kullanın.  
- **Yapılandırılmış Veri Günlüğü:** Düz `System.out` yerine uyarıları bir JSON günlüğüne yazın—bu, sonraki analizleri (ör. “en çok eksik yazı tipleri”) çok basitleştirir.  
- **Erken Doğrulama:** Ağır işleme başlamadan önce `LoadOptions` ile hızlı bir “dry‑load” çalıştırın; kritik yazı tipleri eksikse erken iptal edin.  
- **İş Parçacığı Güvenliği:** `Document` nesneleri iş parçacığı güvenli değildir. Her dosyanın işlenmesini kendi iş parçacığında tutun veya bir iş parçacığı‑yerel `LoadOptions` kullanın.  

## Sonuç  

Artık Aspose.Words for Java'da **uyarıların nasıl yakalanacağını**, **eksik yazı tiplerini nasıl tespit edeceğinizi** ve **eksik yazı tiplerini temiz bir geri dönüş stratejisiyle nasıl ele alacağınızı** biliyorsunuz. `LoadOptions` kullanarak ve `document.getWarnings()` üzerinde döngü yaparak, yazı tipi ikame olayları hakkında tam bir içgörü elde eder, oluşturduğunuz belgelerin tüm ortamlar içinde tam olarak istediğiniz gibi görünmesini sağlarsınız.

Bir sonraki adıma hazır mısınız? Bu deseni **eksik görselleri tespit etmek**, **desteklenmeyen özellikleri izlemek** veya hatta **eksik yazı tiplerini çıktıya otomatik olarak gömmek** için genişletmeyi deneyin. Aynı uyarı yakalama yaklaşımı, kodunuzu sağlam ve geleceğe dayanıklı kılan birçok başka belge‑işleme senaryosunda da çalışır.

Kodlamaktan keyif alın, ve belgeleriniz her zaman güzel bir şekilde renderlansın!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}