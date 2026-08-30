---
category: general
date: 2026-07-03
description: Java'da uyarı geri aramasını kaydederek Word belgelerini işlerken eksik
  yazı tiplerini tespit edin. Aspose.Words uyarı işleme ve yazı tipi ikame tespiti
  hakkında bilgi edinin.
draft: false
keywords:
- register warning callback
- detect missing fonts
- font substitution warning
- Aspose.Words warning callback
- Java missing font detection
- document font handling
language: tr
og_description: Java'da eksik yazı tiplerini tespit etmek için uyarı geri çağrısını
  kaydedin. Bu kılavuz, Aspose.Words ile yazı tipi ikame uyarılarını nasıl yakalayacağınızı
  gösterir.
og_title: Java'da uyarı geri çağrısını kaydet – Eksik yazı tiplerini tespit et
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  headline: Register warning callback in Java – Detect missing fonts easily
  type: TechArticle
- description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  name: Register warning callback in Java – Detect missing fonts easily
  steps:
  - name: Why this matters
    text: '* **Visibility:** Without a callback, the substitution happens silently,
      and you might ship a document with the wrong appearance. * **Automation:** In
      batch pipelines you can log every missing‑font incident and later feed the list
      to a font‑installation script. * **Compliance:** Some industries (e.g'
  - name: Expected console output
    text: 'Assuming `input.docx` references the font *“Comic Sans MS”* which isn’t
      installed, you’ll see something like:'
  - name: Multiple missing fonts
    text: If a document references several unavailable fonts, the callback will fire
      once per font. You can aggregate the messages into a list if you need a summary
      report later.
  - name: Controlling substitution behavior
    text: 'Sometimes you *do* want to force a particular fallback font. Use `FontSettings`
      before loading the document:'
  - name: Performance considerations
    text: 'Registering a warning callback introduces a tiny overhead—only a few nanoseconds
      per warning. In high‑throughput services (e.g., converting thousands of docs
      per hour) the impact is negligible. However, if you’re processing millions,
      consider disabling warnings after you’ve verified the font set is '
  - name: Cross‑platform notes
    text: The callback works identically on Windows, macOS, and Linux. The only difference
      is the set of fonts available on each OS. If you run the same job on multiple
      agents, you might see different substitution messages. To keep results deterministic,
      ship a **custom font folder** and point Aspose.Words to
  type: HowTo
tags:
- Aspose.Words
- Java
- Fonts
title: Java'da uyarı geri çağrısını kaydedin – Eksik yazı tiplerini kolayca tespit
  edin
url: /tr/java/document-loading-and-saving/register-warning-callback-in-java-detect-missing-fonts-easil/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da uyarı geri çağrısını kaydedin – Eksik yazı tiplerini kolayca tespit edin

Hiç **uyarı geri çağrısını kaydetmenin** nasıl yapılacağını ve Word belgelerini dönüştürürken ya da düzenlerken **eksik yazı tiplerini tespit** edebileceğinizi merak ettiniz mi? Tek başınıza değilsiniz. Eksik yazı tipleri, düzeni sessizce bozabilir, şık bir raporu karışık bir hâle getirebilir ve çoğu geliştirici, son PDF beklenmedik göründüğünde bile bunun farkına varmaz.  

Bu öğreticide, Aspose.Words for Java’nın uyarı sistemine nasıl bağlanacağınızı, sinir bozucu yazı tipi‑ikame uyarılarını yakalayacağınızı ve bunları kaydedebileceğinizi ya da ihtiyacınıza göre tepki verebileceğinizi gösteren, tamamen çalıştırılabilir bir örnek üzerinden adım adım ilerleyeceğiz. “Belgelere bakın” gibi belirsiz yönlendirmeler yok—sadece saf, kopyala‑yapıştır kod ve her satırın mantığı.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* **Java 17** (veya daha yeni bir JDK) ve `JAVA_HOME` ayarlanmış.  
* **Aspose.Words for Java** JAR’ı (resmi siteden indirin veya Maven ile çekin).  
* Makinenizde **yüklü olmayan** bir yazı tipine referans veren bir `.docx` örnek dosya—bu uyarıyı tetikleyecek.  
* Sevdiğiniz IDE ya da basit bir metin editörü ve komut satırı derleme araçları.

Hepsi bu. Ekstra framework, dış hizmet yok. Hazır mısınız? Başlayalım.

## Adım 1: Projeyi kurun ve Aspose.Words ekleyin

Maven kullanıyorsanız, `pom.xml` dosyanıza aşağıdaki bağımlılığı ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- use the latest stable version -->
</dependency>
```

Gradle için, `build.gradle` dosyanıza şu satırı ekleyin:

```groovy
implementation 'com.aspose:aspose-words:24.10'
```

Manuel yolu tercih ediyorsanız, `aspose-words-24.10.jar` dosyasını sınıf yolunuza (classpath) koyun.  
**İpucu:** JAR’ı `src` klasörünüzün yanına yerleştirin; bu, daha sonra `javac` komutunu basitleştirir.

## Adım 2: Eksik yazı tipleri içerebilecek belgeyi yükleyin

İlk olarak, kaynak dosyayı gösteren bir `Document` nesnesi oluşturursunuz. Bu adım basittir, ancak kütüphane dosyayı tarayıp *potansiyel* olarak eksik yazı tiplerini keşfettiği yerdir.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // Adjust the path to point at your test document
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – Aspose.Words will start parsing it now
        Document doc = new Document(inputPath);
```

Burada `Document`, Aspose.Words işlemlerinin giriş noktasıdır. Yapıcı çalıştığında, kütüphane belgenin XML’ini ayrıştırır, yazı tiplerini çözer ve eğer bir yazı tipi bulunamazsa, daha sonra yakalayabileceğimiz bir uyarıyı *kuyruğa* ekler.

## Adım 3: Yazı tipi‑ikame uyarılarını yakalamak için uyarı geri çağrısını kaydedin

Şimdi gösterinin yıldızı: **uyarı geri çağrısını kaydetmek**. Aspose.Words, `IWarningCallback` arayüzünün bir uygulamasını takmanıza izin verir. Motor, eksik bir yazı tipi gibi işaretlenmesi gereken bir durumla karşılaştığında, sizin `warning` metodunuzu çağırır.

```java
        // Register the warning callback
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We’re only interested in font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                }
            }
        });
```

### Neden önemli?

* **Görünürlük:** Geri çağrı olmadan ikame sessizce gerçekleşir ve belgeyi hatalı bir görünüme sahip olarak dağıtabilirsiniz.  
* **Otomasyon:** Toplu işlem hatlarında her eksik‑yazı tipi olayını kaydedebilir ve daha sonra bu listeyi bir yazı tipi kurulum betiğine besleyebilirsiniz.  
* **Uyumluluk:** Bazı sektörler (ör. hukuk) orijinal yazı tiplerinin kullanıldığını ya da doğru şekilde ikame edildiğini kanıtlamanızı ister.

`WarningType.FONT_SUBSTITUTION` üzerine filtre uyguladığımıza dikkat edin. Aspose.Words birçok uyarı türü üretir—düzen taşması, kullanımdan kaldırılmış özellikler vb.—ancak sadece bir yazı tipinin eksik olduğunu söyleyenleri ilgilendiririz. Bu, konsolu temiz tutar ve **eksik yazı tiplerini tespit etme** amacına odaklanır.

## Adım 4: Belgeyi kaydedin ve geri çağrının tetiklenmesini sağlayın

`save` metodunu çağırdığınızda, motor tembel yüklemeyi tamamlar ve kaydetme sırasında keşfedilen her eksik yazı tipi için uyarı geri çağrısını tetikler.

```java
        // Save the document – this is where the warning callback gets invoked
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("✅ Document saved to " + outputPath);
    }
}
```

### Beklenen konsol çıktısı

`input.docx` dosyası *“Comic Sans MS”* yazı tipine referans veriyorsa ve bu yazı tipi yüklü değilse, aşağıdakine benzer bir çıktı görürsünüz:

```
⚠️ Font substituted: Font 'Comic Sans MS' is not available. Substituted with 'Arial'.
✅ Document saved to YOUR_DIRECTORY/output.docx
```

Kaynak belge zaten yalnızca yüklü yazı tipleri içeriyorsa, uyarı satırı hiç görünmez—yani **eksik yazı tiplerini tespit etme** sessizce başarılı olur.

![Console output showing register warning callback in action and detect missing fonts](register-warning-callback-output.png)

*Görsel alt metni: uyarı geri çağrısı çıktısı, eksik yazı tiplerini tespit etmeyi gösteriyor*

## Adım 5: Kenar durumları ve en iyi uygulama ipuçları

### Birden fazla eksik yazı tipi

Bir belge birden fazla bulunamayan yazı tipine referans veriyorsa, geri çağrı her bir yazı tipi için bir kez çalışır. Daha sonra özet rapor oluşturmak isterseniz mesajları bir listeye toplayabilirsiniz.

```java
List<String> missingFonts = new ArrayList<>();
doc.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        missingFonts.add(info.getDescription());
    }
});
// After saving
if (!missingFonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    missingFonts.forEach(System.out::println);
}
```

### İkame davranışını kontrol etme

Bazen belirli bir yedek yazı tipini zorlamak isteyebilirsiniz. Belgeyi yüklemeden önce `FontSettings` kullanın:

```java
FontSettings settings = new FontSettings();
settings.setSubstitutionSettings(new FontSubstitutionSettings()
        .addSubstitutes("Comic Sans MS", "Times New Roman"));
doc.setFontSettings(settings);
```

Şimdi geri çağrı hâlâ tetiklenir, ancak hangi yazı tipinin kullanılacağını tam olarak bilirsiniz.

### Performans değerlendirmeleri

Uyarı geri çağrısı kaydetmek çok az bir ek yük getirir—her uyarı için sadece birkaç nanosaniye. Saatte binlerce belge dönüştüren yüksek hacimli servislerde etkisi ihmal edilebilir. Ancak milyonlarca belge işliyorsanız, yazı tipi setinizin tamam olduğunu doğruladıktan sonra uyarıları devre dışı bırakmayı düşünün:

```java
doc.setWarningCallback(null); // turn off after initial scan
```

### Platformlar arası notlar

Geri çağrı Windows, macOS ve Linux’ta aynı şekilde çalışır. Tek fark, her işletim sisteminde mevcut olan yazı tipi setidir. Aynı işi birden fazla ajan üzerinde çalıştırıyorsanız, farklı ikame mesajları görebilirsiniz. Sonuçların deterministik olmasını istiyorsanız, **özel bir yazı tipi klasörü** gönderin ve Aspose.Words’u `FontSettings.setFontsFolder("path/to/fonts", true);` ile bu klasöre yönlendirin.

## Tam, çalıştırılabilir örnek

Aşağıda, `src/main/java/FontWarningDemo.java` içine kopyalayıp yapıştırabileceğiniz tam Java sınıfı yer alıyor. Gerekli tüm import’ları, hata yönetimini ve yorum satırlarını içerir; doğrudan çalıştırabilirsiniz.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

/**
 * Demonstrates how to register a warning callback in Aspose.Words for Java
 * to detect missing fonts during document processing.
 */
public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Paths – adjust to your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // 2️⃣ Load the document (parsing begins here)
        Document doc = new Document(inputPath);

        // 3️⃣ Optional: set a custom font folder if you ship fonts with your app
        // FontSettings fs = new FontSettings();
        // fs.setFontsFolder("fonts", true);
        // doc.setFontSettings(fs);

        // 4️⃣ Register the warning callback to catch missing‑font warnings
        List<String> missingFonts = new ArrayList<>();
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Log to console
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                    // Collect for later reporting
                    missingFonts.add(info.getDescription());
                }
            }
        });

        // 5️⃣ Save the document – triggers the callback
        doc.save(outputPath);
        System.out.println("✅ Document saved to " + outputPath);

        // 6️⃣ Post‑save reporting (if any fonts were missing)
        if (!missingFonts.isEmpty()) {
            System.out.println("\nSummary of missing fonts:");
            missingFonts.forEach(System.out::println);
        } else {
            System.out.println("\nNo missing fonts detected.");
        }
    }
}
```

Derleyin ve çalıştırın:

```bash
javac -cp "aspose-words-24.10.jar" FontWarningDemo.java
java -cp ".:aspose-words-24.10.jar" FontWarningDemo
```

Herhangi bir uyarı satırı (varsa) ardından başarı mesajını görmelisiniz.

## Sonuç

Java’da **uyarı geri çağrısını kaydetmeyi** ve Aspose.Words ile çalışırken **eksik yazı tiplerini tespit etmeyi** öğrendiniz. Kütüphanenin uyarı sistemine bağlanarak yazı tipi‑ikame olayları hakkında tam görünürlük elde eder, uyumluluk için bunları kaydedebilir ve gerektiğinde programatik olarak yazı tiplerini değiştirebilirsiniz.  

Bundan sonra şunları keşfedebilirsiniz:

* **Eksik yazı tiplerini** bir dosya topluluğu üzerinde döngü ya da paralel akışlarla tespit etme.  
* Geri çağrıyı bir günlükleme çerçevesi (SLF4J, Log4j) ile entegre ederek üretim‑düzeyi raporlar oluşturma.  
* `FontSettings` kullanarak kurumsal bir yazı tipi paleti zorunlu kılma ve istenmeyen ikameleri önleme.

Deneyin—giriş belgesini değiştirin, farklı eksik‑yazı tipi senaryolarını deneyin ve geri çağrının nasıl davrandığını görün. Sorunla karşılaşırsanız, aşağıya yorum bırakın; kodlamanın tadını çıkarın!


## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakın ilişkili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose Words Java Callback Custom Savings](/words/hindi/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}