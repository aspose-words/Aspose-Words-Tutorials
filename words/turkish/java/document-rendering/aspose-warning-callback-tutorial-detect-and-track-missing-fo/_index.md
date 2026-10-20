---
category: general
date: 2026-03-17
description: Aspose uyarı geri çağırma öğreticisini öğrenerek, Java belgelerinde eksik
  yazı tiplerini tespit edin ve izleyin; tam ve çalıştırılabilir bir örnekle.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: tr
og_description: Aspose uyarı geri çağırma öğreticisini öğrenerek eksik fontları tespit
  edin ve Java Word iş akışınızda eksik fontları izleyin.
og_title: aspose uyarı geri çağırma öğreticisi – Eksik Yazı Tiplerini Tespit Et
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: aspose uyarı geri arama öğreticisi – Eksik Yazı Tiplerini Algıla ve İzle
url: /tr/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – Eksik Yazı Tiplerini Algıla ve İzle

Word dosyalarını Aspose.Words ile dönüştürürken veya düzenlerken **eksik yazı tiplerini algılamayı** hiç merak ettiniz mi? Tek başınıza değilsiniz. Gerçek projelerde, istenmeyen bir yazı tipi düzen bozulmalarına yol açabilir ve **eksik yazı tiplerini izlemek** için güvenilir bir yönteme ihtiyacınız olur.  

İyi haber? **aspose warning callback tutorial** tam da bu yazı‑tipi ikame uyarılarını anında yazdıran temiz bir programatik kanca sunar. Bu rehberde geri çağırmayı (callback) nasıl ayarlayacağınızı, bir belgeyi nasıl yükleyeceğinizi ve uyarıların nasıl çalıştığını Java’da adım adım göstereceğiz.

Bu makalenin sonunda eksik yazı tiplerini otomatik olarak tespit edebilecek, kaydedebilecek ve bir yedek eklemeye ya da kaynak dosyalarınızı ayarlamaya karar verebileceksiniz. Harici bir araç gerekmez.

## Önkoşullar

- **Java 8+** (kod, herhangi bir yeni JDK ile derlenebilir)
- **Aspose.Words for Java** sürüm 23.10 veya üzeri – Aspose portalından indirin ya da Maven bağımlılığını ekleyin.
- Bilerek yüklü olmayan bir yazı tipine referans veren örnek bir DOCX (ör. Linux makinede “Comic Sans MS”).

Hepsi bu—ekstra kütüphane, karmaşık yapı adımı yok.

## Adım 1: Bir Uyarı Geri Çağrısı (Callback) Kaydet – aspose warning callback tutorial’ın Çekirdeği

İlk olarak tutorial, bir uyarı dinleyicisi nasıl eklenir gösterir. Aspose.Words, karşılaştığı her sorun için bir `WarningInfo` nesnesi oluşturur ve `WarningSource.FONT_SUBSTITUTION` bayrağı, bir yazı tipinin ikame edildiği anı tam olarak bildirir.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Neden önemli:** Geri çağırma olmadan Aspose sessizce eksik yazı tiplerini değiştirir ve hangi karakterlerin hatalı görünebileceğini asla öğrenemezsiniz. Uyarıyı kaydederek **eksik yazı tiplerini erken algılayabilir** ve doğru olanı gömmeye karar verebilirsiniz.

> **Pro ipucu:** Uyarıları daha sonra raporlamak istiyorsanız, doğrudan yazdırmak yerine bir `List<WarningInfo>` içinde saklayın.

## Adım 2: Belgeyi Yükle – Eksik Yazı Tiplerinin Gizlenebileceği Yer

Şimdi, makinede bulunmayan yazı tiplerine referans verebilecek DOCX’i yüklüyoruz. Yükleme işlemi, eksik bir yazı tipi varsa uyarı geri çağrısını tetikler.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**Arka planda ne oluyor?** Aspose, belgenin stil tanımlarını ayrıştırır, her metin çalışmasını tarar ve sistemin yazı tipi deposunu kontrol eder. Tam eşleşme bulunamadığında bir ikame seçer ve az önce bağladığımız uyarıyı yayar.

## Adım 3: Belgeyi Kaydet – Uyarıları Boşaltma

Son olarak belgeyi kaydediyoruz. Kaydetme işlemi de yazı tiplerini yeniden değerlendirir, bu yüzden yükleme sırasında yayılmamış uyarılar burada ortaya çıkar.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Programı çalıştırdığınızda aşağıdaki gibi bir konsol çıktısı göreceksiniz:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

Bu çıktı, **aspose warning callback tutorial**’ın çalıştığını kanıtlar; **eksik yazı tiplerini algılayıp** artık **eksik yazı tiplerini izlediğinizi** gösterir.

## Word Belgesinde Eksik Yazı Tiplerini Algılamak – Temel Bilgilerin Ötesinde

Geri çağırma yöntemi tek seferlik çalıştırmalar için harika, ancak bazen yeniden kullanılabilir bir yardımcı araca ihtiyacınız olur. İşte herhangi bir projeye ekleyebileceğiniz hızlı bir sarmalayıcı:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

Şöyle çağırın:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

Artık bir CI boru hattına ya da bir UI’ye besleyebileceğiniz, **eksik yazı tiplerini algılayan** yeniden kullanılabilir bir metodunuz var.

## Aspose.Words ile Eksik Yazı Tiplerini İzlemek – Takımlar İçin Raporlama

Büyük bir ekipte, birçok belge üzerindeki eksik yazı tiplerinin CSV raporunu üretmek isteyebilirsiniz. Önceki yardımcı aracı basit dosya döngüsüyle birleştirin:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

Bu betiği çalıştırdığınızda, her geliştiricinin üretime bir belge göndermeden önce göz atabileceği bir **eksik yazı tiplerini izleme** CSV’si elde edersiniz.

## Yaygın Tuzaklar ve Kaçınma Yöntemleri

| Tuzak | Neden Oluşur | Çözüm |
|---------|----------------|-----|
| **Geri çağırma çalışmıyor** | Geri çağırmayı **belgeyi yüklemeden önce** ayarlamayı unuttunuz. | `Document.setWarningCallback` satırını `main` metodunun en üstüne koyun. |
| **Sadece ilk uyarı görünüyor** | Aspose, uyarıları `Document` örneği başına önbelleğe alır. | Her dosya için yeni bir `Document` nesnesi oluşturun veya çalıştırmalar arasında geri çağırmayı sıfırlayın. |
| **Günlükte yanlış yazı tipi adı** | Açıklama ek metin içerir (“Font … not found”). | CSV örneğinde gösterildiği gibi regex ile temizleyin. |
| **Büyük toplu işlemlerde performans düşüşü** | Geri çağırma her metin çalışması için çalışır, bu maliyetli olabilir. | Kontrolü ön‑uç adımına sınırlayın; sadece tespit gerekiyorsa kaydetme adımını atlayın. |

## Beklenen Sonuçlar ve Doğrulama

1. **Konsol çıktısı** – Her eksik yazı tipi için en az bir “Font substitution warning” satırı görmelisiniz.  
2. **CSV raporu** – Toplu betik tamamlandığında `missing-fonts-report.csv` dosyasını açın ve her satırın belge adını ve eksik yazı tipini listelendiğini doğrulayın.  
3. **Kaydedilen belge** – Çıktı DOCX, ikame yazı tipleriyle renderlanır; ancak görsel düzen orijinalden farklı olabilir.

Bu adımlardan biri beklendiği gibi çalışmazsa, Aspose.Words JAR dosyasının sınıf yolunda (classpath) olduğundan ve `input.docx` dosyasının gerçekten işletim sisteminizde bulunmayan bir yazı tipine referans verdiğinden emin olun.

## Sonuç

Bir **aspose warning callback tutorial**’ı tamamlayarak Java uygulamalarında **eksik yazı tiplerini algılamayı** ve **eksik yazı tiplerini izlemeyi** gösterdiniz. Bir uyarı dinleyicisi kaydederek, belgeyi yükleyerek ve isteğe bağlı olarak bulguları dışa aktararak, üretime geçmeden önce yazı tipiyle ilgili sorunların tam görünürlüğünü elde ettiniz.

İleride şunları keşfedebilirsiniz:

- `LoadOptions.setFontSubstitution` ile eksik yazı tipini doğrudan gömmek.
- `FontSettings` sınıfını kullanarak eksik yazı tiplerini belirli ikamelerle eşlemek.
- CSV raporunu CI/CD boru hattına entegre ederek belgelerde belgelenmemiş yazı tipleri bulunduğunda derlemeyi durdurmak.

Deneyin, geri çağırmaları kendi günlükleme çerçevenize göre uyarlayın ve belge iş akışınızın çok daha sağlam hale geldiğini izleyin. İyi kodlamalar!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}