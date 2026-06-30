---
category: general
date: 2026-06-30
description: Aspose.Words Java'da uyarılar için LoadOptions yapılandırın. Yazı tipi
  ikamesi ve diğer yükleme seçenekleri uyarıları için bir uyarı geri çağrısı ayarlamayı
  öğrenin.
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: tr
og_description: Aspose.Words Java'da uyarılar için LoadOptions'ı yapılandırın. Bu
  kılavuz, bir uyarı geri çağrımıyla font değiştirme uyarılarını nasıl yakalayacağınızı
  gösterir.
og_title: Uyarılar için LoadOptions'ı Yapılandır – Java Öğretisi
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: Uyarılar için LoadOptions'ı yapılandırın – Tam Java Rehberi
url: /tr/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# LoadOptions'ı Uyarılar İçin Yapılandırma – Tam Java Rehberi

Aspose.Words for Java ile bir Word belgesi açarken **uyarılar için LoadOptions'ı yapılandırmanız** gerektiğinde hiç mi oldu? Tek başınıza değilsiniz. Birçok geliştirici, eksik bir fontun sessizce değişmesi ve son PDF'nin marka dışı görünmesi sorunuyla karşılaşıyor. İyi haber? **Java uyarı geri çağrısını** `LoadOptions`'ınıza ekleyerek, gerçekleşen her font‑değiştirme uyarısını yakalayabilirsiniz.

Bu öğreticide, sadece geri çağırmanın nasıl kurulacağını göstermekle kalmayan, aynı zamanda *neden* her parçanın önemli olduğunu açıklayan uygulamalı bir örnek üzerinden ilerleyeceğiz. Sonunda **font uyarılarını** ele alabilecek, bunları kaydedebilecek veya hatta anında fontları değiştirebileceksiniz—tahmine gerek kalmayacak.

## Öğrenecekleriniz

- Her font‑değiştirme uyarısını yazdıran tam çalışabilir bir Java programı.
- **Aspose.Words font substitution** mekaniklerine dair bir anlayış.
- Büyük projeler için uyarı işleme özelleştirme ipuçları.
- **Document loading options** hakkında içgörü ve ne zaman ayarlama yapılacağı.

> **Önkoşul:** Java 8+ ve Aspose.Words for Java kütüphanesi (sürüm 23.9 veya üzeri). Başka bir dış bağımlılık gerekmez.

---

## Adım 1: Uyarılar İçin LoadOptions'ı Yapılandırma

İlk olarak ihtiyacınız olan, uyarı raporlayacağını bilen bir `LoadOptions` örneğidir. `LoadOptions`'ı, Aspose.Words dosyayı açmadan önce ona verdiğiniz bir araç kutusu gibi düşünün.

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**Neden önemli:**  
`LoadOptions`, kütüphanenin belgeyi nasıl okuduğunu kontrol eder. Bir `IWarningCallback` atayarak, Aspose.Words'un dikkat çekici bir şeyle (örneğin eksik bir font) karşılaştığında kodunuzu çalıştırmasını sağlarsınız. Bu olmadan, kütüphane sessizce fontu değiştirir ve bunu asla bilmezsiniz.

> **Pro ipucu:** *Tüm* uyarıları yakalamak istiyorsanız `if` kontrolünü kaldırın. Şimdilik, düzen sürprizlerinin en yaygın kaynağı oldukları için font sorunlarına odaklanıyoruz.

---

## Adım 2: Yapılandırılmış Seçenekleri Kullanarak Belgeyi Yükleme

Geri çağırma hazır olduğuna göre, aynı `LoadOptions` ile `.docx` (veya desteklenen herhangi bir format) dosyanızı yükleyin. İşte **document loading options**'ın gerçekten etkili olduğu yer.

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Arka planda:**  
Aspose.Words `input.docx` dosyasını ayrıştırdığında, font tablolarını tarar. Belgede referans verilen bir font, ana makinede yüklü değilse, motor bir `FONT_SUBSTITUTION` uyarısı oluşturur ve bu da hemen daha önce tanımladığımız geri çağırmayı tetikler.

---

## Adım 3: Belgeyi Kaydet – Uyarılar Zaten Yazdırıldı

Belgeyi kaydetmek basittir, ancak geri çağırmanın doğru şekilde tetiklendiğini doğrulayabileceğiniz an budur. Tüm uyarılar yükleme adımında yazdırılır, bu yüzden kaydetme işlemi sadece temizliktir.

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**Beklenen konsol çıktısı:**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

Eğer hiçbir şey görmüyorsanız, belge yalnızca yüklü fontlar kullandı demektir ya da geri çağırma doğru şekilde bağlanmadı—Adım 1'i tekrar kontrol edin.

---

## Adım 4: Geri Çağırmayı **Font Uyarılarını** Zarifçe Ele Alacak Şekilde Genişletme

Konsola yazdırmak demo için uygundur, ancak üretim kodu genellikle daha zengin bir işleme ihtiyaç duyar: bir dosyaya loglama, uyarı gönderme veya hatta programatik olarak font değiştirme.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**Neden bunu yaparsınız:**  
Bir log dosyası, özellikle belge topluları işlenirken, sonradan analiz için içgörü sağlar. Opsiyonel substitution bloğu, **uyarılar için LoadOptions'ı yapılandırma**'yı ve kurumsal bir font politikasını uygulamak için müdahale etmeyi gösterir.

---

## İleri Düzey: Diğer **Aspose.Words Font Substitution** Senaryolarını Kontrol Etme

Uyarı geri çağrısı, eksik fontlarla sınırlı değildir. Şunları da yakalayabilirsiniz:

- **Desteklenmeyen Unicode karakterleri** (`WarningType.UNSUPPORTED_CHAR`).
- **Karmaşık betik sorunları** (`WarningType.COMPLEX_SCRIPT`).

`if` ifadesini genişletmeniz yeterlidir:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

Bu, çözümünüzü çok dilli belgeler için sağlam kılar; bu, küresel uygulamalarda yaygın bir kenar durumudur.

---

## Tam Çalışan Örnek

Aşağıda tam ve çalıştırılabilir program bulunmaktadır. Herhangi bir Java IDE'sine yapıştırın, `YOUR_DIRECTORY` yer tutucularını değiştirin ve *Run* tuşuna basın.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Beklenen Sonuç

- Konsol, herhangi bir font‑değiştirme uyarısını yazdırır.
- `font-warnings.log`, zaman damgalı bir liste içerir (opsiyonel loglamayı tuttuysanız).
- `output.docx`, tanımladığınız yedekleme ile eşleşen değiştirilmiş fontlarla kaydedilir.

---

## Yaygın Tuzaklar ve Nasıl Kaçınılır

| Pitfall | Why It Happens | Fix |
|---------|----------------|-----|
| **Uyarı görünmemesi** | Geri çağırma eklenmemişti veya belge yalnızca yüklü fontları kullanıyor. | `loadOptions.setWarningCallback(...)` çağrısının belgeyi yüklemeden *önce* yapıldığını doğrulayın. |
| **`input.docx` üzerinde FileNotFoundException** | Yol yanlış veya dosya proje ile paketlenmemiş. | Mutlak bir yol kullanın veya dosyayı projenin resources klasörüne yerleştirin. |
| **Binlerce belge işlenirken performans yavaşlaması** | Her uyarı için diske aşırı loglama. | Logları tamponlayıp toplu olarak yazın veya sadece kritik uyarıları loglayarak sınırlayın. |
| **Yedekleme ayarına rağmen beklenmeyen font değişimi** | Substitution tablosu yeterince erken uygulanmadı. | Substitution ayarlarını belgeyi yüklemeden **önce** ayarlayın veya `FontSettings.setSubstitutionSettings`'i global olarak kullanın. |

---

## Sonraki Adımlar

Artık **uyarılar için LoadOptions'ı yapılandırma** konusunda uzmanlaştığınıza göre, aşağıdaki takip konularını göz önünde bulundurun:

- **Batch processing**: Belgeler dizini üzerinde döngü kurarak tüm font uyarılarını tek bir raporda toplayın.
- **Custom font providers**: Fontları yerel işletim sisteminden ziyade bir ağ paylaşımından veya gömülü kaynaklardan yükleyin.
- Log4j gibi **logging framework'leri** ile bütünleştirerek kurumsal düzeyde izlenebilirlik sağlayın.
- `LoadFormat` algılama veya korumalı dosyalar için `Password` işleme gibi diğer **document loading options**'ı keşfedin.

Bunların her biri aynı desen üzerine kuruludur—bir `LoadOptions` nesnesi oluşturun, uygun geri çağırmaları ekleyin ve Aspose.Words'un ağır işi halletmesine izin verin.

---

## Sonuç

Aspose.Words for Java'da **uyarılar için LoadOptions'ı yapılandırma**, bir **Java uyarı geri çağrısı** kurma ve bu bilgiyi **font uyarılarını** akıllıca ele almak için nasıl kullanacağınızı derinlemesine inceledik. Kod kompakt, kavramlar net ve artık uyarı işleme yeteneğini desteklenmeyen karakterler veya karmaşık betikler gibi diğer senaryolara genişletmek için sağlam bir temele sahipsiniz.

Bir deneyin, substitution tablosunu marka fontlarınıza göre ayarlayın ve sessiz font değişimlerinin kaybolduğunu izleyin. İyi kodlamalar!

![Uyarılar için LoadOptions'ı yapılandırma akışını gösteren diyagram](configure-loadoptions-for-warnings-diagram.png "Configure LoadOptions for warnings flow")

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Java'da Aspose.Words ile Font Değiştirme Uyarılarını Yakalama – Tam Kılavuz](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Aspose.Words for Java'da LoadOptions Nasıl Ayarlanır](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words for Java'da RTF Load Options'ı Yapılandırarak RTF Belgeleri Nasıl Yüklenir](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}