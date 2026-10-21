---
category: general
date: 2026-04-28
description: Bir Word dosyasındaki belge uyarılarını yineleyerek eksik yazı tiplerini
  tespit edin, eksik yazı tipi adlarını alın ve Aspose.Words for Java kullanarak eksik
  yazı tipi ayrıntılarını yazdırın.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: tr
og_description: Belge uyarılarını döngüyle işleyerek eksik yazı tiplerini bulun, eksik
  yazı tipi adlarını alın ve eksik yazı tipi ayrıntılarını tam bir Java örneğiyle
  yazdırın.
og_title: 'Belge uyarılarını yineleyin: Java''da eksik yazı tiplerini tespit edin'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Belge uyarılarını yinele: Java’da eksik yazı tiplerini tespit edin'
url: /tr/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Belge uyarılarını yineleyin – Java’da Eksik Yazı Tiplerini Algılayın

Bir Word dosyası açarken **belge uyarılarını yinelemeye** ihtiyaç duydunuz mu ve hangi yazı tiplerinin eksik olduğunu merak ettiniz mi? Tek başınıza değilsiniz. Eksik yazı tipleri bir raporun görünümünü bozabilir ve bunları tespit etmenin bir yolu olmadan, orijinaliyle hiç benzemeyen bir belge gönderebilirsiniz.  

Bu öğreticide, bir Word belgesi yükleyerek, uyarılarını yineleyerek, eksik yazı tipi adlarını alarak ve sonunda eksik yazı tipi bilgilerini yazdırarak **eksik yazı tiplerini algılamanın** nasıl yapılacağını göstereceğiz—tüm bunlar Aspose.Words for Java ile.  

İlk kod satırından beklenen konsol çıktısına kadar her şeyi ele alacağız, böylece çalışan bir çözümü hemen projenize kopyalayıp yapıştırabilirsiniz. Ek belge gerekmez.

## Önkoşullar

- Java 8 veya daha yeni bir sürüm yüklü.
- Aspose.Words for Java kütüphanesi (2026‑04‑28 itibarıyla en son sürüm).
- Makinenizde yüklü olmayan yazı tipleri içerebilecek bir Word dosyası (ör. `doc-with-missing-font.docx`).

Eğer bunlara sahipseniz, harika—**Word belgesini yüklemeye** ve yinelemeye hazırsınız.

## Adım 1 – Varsayılan Seçeneklerle Word Belgesini Yükleyin

**Belge uyarılarını yineleyebilmek** için dosyanın belleğe yüklenmesi gerekir. Aspose.Words bunu tek bir yapıcı çağrısıyla yapmanıza olanak tanır. Varsayılan `LoadOptions` genellikle yeterlidir, ancak açıklık için açık oluşturmayı göstereceğiz.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Neden önemli:**  
> Belgeyi yüklemek, Aspose.Words'ün dosyayı yerel olarak yüklü olmayan yazı tipleri gibi çözülemeyen kaynaklar için taramasını tetikler. Bu sorunlar **uyarılar** olarak saklanır ve bir sonraki adımda **belge uyarılarını yineleyeceğiz**.

## Adım 2 – Yazı Tipi Sorunlarını Bulmak için Belge Uyarılarını Yineleyin

Şimdi çözümün kalbi geliyor: kütüphanenin yükleme sırasında topladığı her uyarıyı döngüyle geçiyoruz. `WarningInfo` nesneleri neyin yanlış gittiğini bize bildirir ve `FontSubstitutionWarning` için filtreleyerek **eksik yazı tiplerini algılayabiliriz**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Pro ipucu:** `instanceof` kontrolü, sadece yazı tipiyle ilgili uyarıları işlediğimizden emin olur, görüntü‑yükleme sorunları gibi diğerlerini görmezden gelir. Bu, döngüyü verimli kılar ve çıktıyı gerçekten **eksik yazı tipi** bilgilerini **almanız** gereken yazı tiplerine odaklar.

### Beklenen Konsol Çıktısı

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Belge eksik yazı tipi içermiyorsa, döngü sessizce sona erer—**eksik yazı tipini yazdırmak** için bir şey yok.

## Adım 3 – Neden Sadece Bir İstisna Yakalanmıyor?

Şöyle düşünebilirsiniz: “`new Document(...)` çağrısını bir try‑catch bloğuna alıp bir istisna aramak neden yapılmaz?” Cevap iki yönlüdür:

1. **Ayrıntılı Bilgi:** İstisnalar sadece bir şeyin başarısız olduğunu söyler. Uyarılar ise tam yazı tipi adını ve Aspose.Words'ün seçtiği yedekleme (fallback) yazı tipini verir.
2. **Ölümcül Olmayan Sorunlar:** Eksik yazı tipleri genellikle ölümcül değildir; belge yine de yüklenir, ancak görsel doğruluk bozulur. **Belge uyarılarını yineleyerek**, dosyanın geri kalanını işleme yeteneğinizi korursunuz.

## Adım 4 – Örneği Genişletmek: Eksik Yazı Tiplerini Bir Listeye Toplamak

Bazen eksik yazı tiplerini daha ileri işleme için ihtiyaç duyarsınız—belki gömmek ya da bir UI aracılığıyla kullanıcıyı uyarmak için. İşte adları bir `Set<String>` içine toplayan hızlı bir değişiklik.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Artık **eksik yazı tipi** verilerini programlı olarak **almak** için temiz bir yolunuz var; bu verileri bir raporlama modülüne ya da bir yazı tipi kurulum sihirbazına besleyebilirsiniz.

## Adım 5 – Gerçek Dünya Düşünceleri

- **Birden Çok Yedekleme:** Tek bir eksik yazı tipi, belgenin farklı bölümlerinde farklı yazı tipleriyle yedeklenebilir. Uyarı listesi her oluşumu içerir, bu yüzden yinelenen eksik‑yazı tipi girdileri görebilirsiniz.
- **Performans:** Çok büyük belgeleri yüklemek binlerce uyarı üretebilir. Sadece yazı tipleriyle ilgileniyorsanız, döngüyü hızlı tutmak için gösterildiği gibi erken filtreleme yapın.
- **Çapraz Platform Yazı Tipleri:** Linux'ta varsayılan yedekleme yazı tipi genellikle *Liberation Sans*'tır. Windows'ta ise *Arial* olabilir. Yedeklemeyi bilmek, uygulamanızla birlikte özel yazı tipleri dağıtmanız gerekip gerekmediğine karar vermenize yardımcı olur.

## Adım 6 – Görsel Yardım

Aşağıda konsol çıktısının bir ekran görüntüsü (alt metin SEO için anahtar kelimeyi içerir).

![Iterate document warnings console output showing missing fonts and their substitutes](/images/iterate-document-warnings.png)

*Alt metin:* *eksik yazı tipi adlarını ve yedekleme detaylarını gösteren belge uyarılarını yineleme örneği.*

## Sonuç

Aspose.Words for Java'da **belge uyarılarını yinelemeyi**, **eksik yazı tiplerini algılamayı**, **Word belgesini** güvenli bir şekilde **yüklemeyi**, **eksik yazı tipi** bilgilerini **almayı** ve konsola **eksik yazı tipini** ayrıntılarını **yazdırmayı** yeni öğrendiniz. Tam kod parçacığı olduğu gibi çalışır ve dosyaya kaydetmek, bir UI iletişim kutusu göstermek ya da eksik yazı tiplerini otomatik olarak gömmek için uyarlayabilirsiniz.

Sonraki adımda, **Word belgesini** özel yazı tipi kaynaklarıyla (ör. kurumsal yazı tipleri klasörü ekleyerek) nasıl yükleyeceğinizi veya eksik yazı tiplerini doğrudan dosyaya gömerek makineler arasında düzeni korumayı keşfetmek isteyebilirsiniz. Her iki konu da burada ele aldıklarınız üzerine doğal olarak inşa edilir.

Kodlamaktan keyif alın ve PDF'leriniz her zaman istediğiniz gibi görünsün!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}