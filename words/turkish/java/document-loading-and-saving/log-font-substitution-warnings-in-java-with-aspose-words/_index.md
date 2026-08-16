---
category: general
date: 2026-06-17
description: Aspose.Words kullanarak Java’da yazı tipi ikame uyarılarını kaydedin
  – belge yüklenirken eksik yazı tiplerini yakalayın ve çıktınızın tutarlı olmasını
  sağlayın.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: tr
og_description: Aspose.Words ile Java’da yazı tipi ikame uyarılarını günlüğe kaydedin.
  Belge yüklenirken eksik yazı tipi uyarılarını yakalamayı öğrenin ve PDF’lerinizi
  kusursuz tutun.
og_title: Java’da Yazı Tipi Değişimi Uyarılarını Günlüğe Kaydet – Tam Rehber
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Java'da Aspose.Words ile Yazı Tipi Değiştirme Uyarılarını Günlüğe Kaydet
url: /tr/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da Yazı Tipi Değiştirme Uyarılarını Günlüğe Kaydet – Tam Kılavuz

Sunucu üzerinde bulunmayan bir yazı tipini bir Word belgesi çektiğinde **yazı tipi değiştirme uyarılarını** günlüğe kaydetmeyi hiç merak ettiniz mi? Sessizce değiştirilen eksik yazı tipleri konusunda yalnız değilsiniz. İyi haber? Aspose.Words for Java, bir belge yüklendiği anda bu değişiklikleri yakalamanız için temiz bir yol sunuyor.

Bu öğreticide, bir uyarı geri aramasını nasıl kaydedeceğinizi, yazı tipi değiştirme uyarılarını nasıl filtreleyeceğinizi ve bunları konsola (ya da tercih ettiğiniz herhangi bir logger’a) nasıl yazdıracağınızı gösteren uygulamalı bir örnek üzerinden ilerleyeceğiz. Sonunda, **Aspose.Words Java** kullanan herhangi bir Java projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız.

## Öğrenecekleriniz

- Uyarıları yakalamak için **LoadOptions** nasıl yapılandırılır.
- Sadece **font substitution** olaylarına yanıt veren bir **IWarningCallback** nasıl uygulanır.
- Eksik yazı tiplerinin net bir denetim iziyle korunarak belgeyi güvenli bir şekilde nasıl yüklersiniz.
- Çözümü dosya tabanlı loglara veya izleme sistemlerine genişletmek için ipuçları.

### Önkoşullar

- Java 8 veya daha yenisi (kod Java 11+ ile de çalışır).
- Aspose.Words for Java kütüphanesi (versiyon 23.10 veya üzeri tavsiye edilir).
- Makinenizde yüklü olmayan bir yazı tipine referans veren bir örnek `.docx` (ör. `MissingFont.docx`).

Ek bir framework gerekmez—sadece saf Java ve Aspose.JAR’lar.

---

## Adım 1: Aspose.Words Java için LoadOptions’u Yapılandırma

Herhangi bir uyarıyı yakalamadan önce bir **LoadOptions** örneğine ihtiyacınız var. Bu nesne, Aspose.Words’ın gelen dosyayı işlerken nasıl davranacağını belirler.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Bu adım neden kritik? Bir `LoadOptions` nesnesi olmadan kütüphane eksik yazı tiplerini sessizce değiştirir ve siz hiçbir iz görmezsiniz. Açıkça bir tane oluşturduğunuzda, **uyarı geri araması** oluşturma kapısını açarsınız; böylece sadece ilgilendiğiniz şeyleri günlüğe kaydedebilirsiniz.

> **Pro ipucu:** Bir toplu işlemde birden çok belge yüklüyorsanız, gereksiz nesne yaratımını önlemek için tek bir `LoadOptions` örneğini yeniden kullanın.

---

## Adım 2: Yazı Tipi Değiştirme İçin Bir Uyarı Geri Araması Uygulama

Aspose.Words, `IWarningCallback` arayüzü ile birlikte gelir. Bunu uyguladığınızda motor bir `WarningInfo` ürettiğinde ne yapacağınızı belirleyebilirsiniz. Bizim senaryomuzda sadece `WarningType.FONT_SUBSTITUTION` olaylarına yanıt vermek istiyoruz.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

Dikkat edilmesi gereken birkaç nokta:

1. **Filtreleme** – `if` ifadesi, ilgili olmayan uyarıları (ör. yerleşim sorunları) görmezden gelerek logun düzenli kalmasını sağlar.
2. **İş parçacığı güvenliği** – Geri arama, belgeyi yükleyen aynı iş parçacığında çalışır; bu yüzden basit bir konsol çıktısı için ekstra senkronizasyona gerek yoktur. Paylaşılan bir logger’a yazıyorsanız, onun iş parçacığı‑güvenli olduğundan emin olun.
3. **Genişletilebilirlik** – Dosyaya yazmak mı istiyorsunuz? `System.out.println` ifadesini `java.util.logging.Logger` veya üçüncü‑taraf bir logging çerçevesi ile değiştirin.

---

## Adım 3: Yapılandırılmış Seçeneklerle Belgeyi Yükleme

Geri arama yerinde olduğuna göre Word dosyanızı yükleyin. Aspose.Words belgeyi ayrıştırdığında, eksik bir yazı tipi varsa yukarıda tanımladığınız geri arama tetiklenir.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Kaynak dosya yüklü olmayan bir yazı tipine referans veriyorsa, aşağıdaki gibi bir çıktı göreceksiniz:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Bu satır, **log font substitution warnings** aradığınız şeydir. Şimdi bunu kullanabilirsiniz—belki bir kullanıcıyı uyarır, yedek bir stil sayfasına geçersiniz ya da sadece uyumluluk için bir kayıt tutarsınız.

---

## Adım 4: Normal İşleme Devam Etme

Yükleme tamamlandıktan sonra belge, diğer `Document` nesneleri gibi davranır. Bölümleri inceleyebilir, metin çıkarabilir ya da PDF’ye dönüştürebilirsiniz. Uyarı günlüğü, yükleme aşamasında otomatik olarak gerçekleşir; ek bir kod eklemenize gerek yoktur.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

Konsol artık hem (varsa) yazı tipi‑değiştirme uyarısını **hem** bölüm sayısını gösterecek, belgenin tam olarak işlevsel olduğunu onaylayacaktır.

---

## İleri Düzey İpuçları ve Kenar Durumları

### Konsol Yerine Dosyaya Günlük Yazma

Kalıcı bir log isterseniz `System.out.println` çağrısını bir `FileWriter` ile değiştirin:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

Üretim kodunda `IOException`’ı uygun şekilde ele almayı unutmayın.

### Döngüde Birden Fazla Belge İşleme

Bir klasördeki belgeleri işlerken aynı geri aramayı yeniden kullanabilirsiniz:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Geri arama `loadOptions`a bağlı olduğundan, her yineleme otomatik olarak yazı tipi‑değiştirme olaylarını günlüğe kaydeder.

### Gömülü Yazı Tipleriyle Çalışma

Aspose.Words, gömülü olmayan yazı tiplerini yerleştirmenize izin verir:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Gömme etkin olsa bile, uyarı geri araması hâlâ çalışır ve neyin değiştirildiğine dair görünürlük sağlar.

---

## Tam Çalışan Örnek

Aşağıda, doğrudan çalıştırabileceğiniz tam program yer alıyor. `FontSubstitutionDiagnostics.java` adlı bir sınıfa yapıştırın, dosya yolunu ayarlayın ve çalıştırın.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Beklenen çıktı** (kaynak belge eksik bir yazı tipine referans veriyorsa):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

Hem konsol hem de `font_substitution_log.txt` uyarıyı içerecek, güvenilir bir denetim izi oluşturacaktır.

---

## Sonuç

Java’da Aspose.Words kullanarak **yazı tipi değiştirme uyarılarını** nasıl günlüğe kaydedeceğinizi gösterdik. `LoadOptions`u yapılandırarak, bir `IWarningCallback` bağlayarak ve belgeyi yükleyerek, aksi takdirde fark edilmeyen eksik‑yazı tipi olaylarına tam görünürlük kazandınız. Bundan sonra şunları yapabilirsiniz:

- Uyarıları merkezi bir logging servisine yönlendirme.
- Kalite‑kontrol hatları için uyarı tetikleme.
- Bu tekniği PDF dönüşümü veya mail‑merge gibi diğer **document loading** stratejileriyle birleştirme.

Deney yapmaktan çekinmeyin—konsol logger’ını SLF4J ile değiştirin, zaman damgaları ekleyin ya da uyarıları bir izleme panosuna gönderin. Temel desen aynı kalır ve artık Java‑tabanlı belge iş akışlarınızda sağlam bir yazı tipi yönetimi temeline sahipsiniz.

Paylaşmak istediğiniz bir varyasyon var mı? Belki bunu Spring Boot ya da bir bulut fonksiyonu ile entegre ettiniz. Aşağıya yorum bırakın, sohbeti sürdürelim. İyi kodlamalar!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayalı olarak yakın konuları kapsar. Her kaynak, kendi projelerinizde ek API özelliklerini ustalaşmanız ve alternatif uygulama yaklaşımlarını keşfetmeniz için adım‑adım açıklamalar ve tam çalışan kod örnekleri içerir.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}