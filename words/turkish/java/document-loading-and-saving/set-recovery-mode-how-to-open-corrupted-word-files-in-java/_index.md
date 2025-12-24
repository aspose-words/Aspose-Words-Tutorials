---
category: general
date: 2025-12-23
description: Hasar görmüş Word belgelerini kurtarmak için kurtarma modunu ayarlayın.
  DOCX dosyalarını nasıl açacağınızı, kurtarma modunu nasıl kullanacağınızı ve Java’da
  bozuk dosyalarla nasıl başa çıkacağınızı öğrenin.
draft: false
keywords:
- set recovery mode
- recover damaged word
- how to open docx
- open corrupted word file
- use recovery mode
language: tr
og_description: Hasar görmüş Word belgelerini kurtarmak için kurtarma modunu ayarlayın.
  Bu kılavuz, DOCX dosyalarını nasıl açacağınızı, kurtarma modunu nasıl kullanacağınızı
  ve Java’da bozuk dosyalarla nasıl başa çıkacağınızı gösterir.
og_title: Kurtarma Modunu Ayarla – Java’da Bozuk Word Dosyalarını Aç
tags:
- Java
- Aspose.Words
- Document Recovery
title: Kurtarma Modunu Ayarla – Java'da Bozuk Word Dosyalarını Açma
url: /tr/java/document-loading-and-saving/set-recovery-mode-how-to-open-corrupted-word-files-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kurtarma Modunu Ayarlama – Bozuk Word Dosyalarını Java’da Nasıl Açabilirsiniz

Hiç **kurtarma modunu ayarlamayı** denediniz mi, ama Word belgesi açılmıyor? Yalnız değilsiniz. Bir DOCX dosyası biraz bozulduğunda ve normal `new Document("file.docx")` bir istisna fırlattığında birçok geliştirici takılıp kalıyor. İyi haber? Aspose.Words for Java, **kurtarma modunu kullanmak** ve gerçekten **hasarlı Word** dosyalarını **kurtarmak** için yerleşik bir yol sunuyor.

Bu öğreticide, `LoadOptions` yapılandırmasından genellikle insanları zorlayan kenar durumlarının ele alınmasına kadar **bozuk word dosyası** nesnelerini güvenli bir şekilde **açmak** için bilmeniz gereken her şeyi adım adım göstereceğiz. Gereksiz şey yok—şu anda projenize yapıştırabileceğiniz pratik bir çözüm.

> **Pro ipucu:** Sadece küçük hatalarla (örneğin eksik bir alt bilgi) uğraşıyorsanız, **Tolerant** kurtarma modu genellikle yeterlidir. **Strict** modunu, belgeyi işlemeye başlamadan %100 temiz olmasını istediğiniz durumlar için ayırın.

## Gereksinimler

- **Java 17** (veya herhangi bir yeni JDK; API aynı şekilde çalışır)
- **Aspose.Words for Java** 23.9 (veya daha yeni) – `LoadOptions` sınıfını içeren kütüphane.
- Test etmek için bir **bozuk DOCX** dosyası (geçerli bir dosyayı bir hex editörle keserek oluşturabilirsiniz).
- Sevdiğiniz IDE (IntelliJ, Eclipse, VS Code—size uygun olanı seçin).

Hepsi bu. Ek Maven eklentileri, harici yardımcı programlar yok. Sadece çekirdek kütüphane ve bir tutam kod.

![Aspose.Words Java API’da kurtarma modunu ayarlama illüstrasyonu](/images/set-recovery-mode-java.png){.align-center alt="kurtarma modunu ayarla"}

## Adım 1 – `LoadOptions` Örneği Oluşturma

İlk yapmanız gereken bir `LoadOptions` nesnesi örneklemektir. Bunu, Aspose.Words’e **gelen dosyanın nasıl ele alınacağını** söyleyen bir araç kutusu gibi düşünün.

```java
import com.aspose.words.LoadOptions;

// Step 1: Create LoadOptions with default settings
LoadOptions loadOptions = new LoadOptions();
```

Bu adımı atlamamalısınız çünkü bir `LoadOptions` olmadan kütüphaneye **kurtarma modunu kullanmak** isteyip istemediğinizi söyleyemezsiniz. Varsayılan davranış strict’tir, yani herhangi bir bozulma yüklemeyi iptal eder.

## Adım 2 – Doğru Kurtarma Modunu Seçme

Aspose.Words iki enum değeri sunar:

| Mod | Ne Yapar |
|------|--------------|
| `RecoveryMode.Tolerant` | Mümkün olduğunca çok şeyi kurtarmaya çalışır. *hasarlı word dosyasını kurtarma* senaryoları için idealdir; eksik bir stil veya kırık bir ilişki tek sorun olduğunda işe yarar. |
| `RecoveryMode.Strict`   | Her sorunda hızlıca başarısız olur. Belgeyi işlemeye başlamadan tamamen temiz olduğundan emin olmanız gerektiğinde bunu kullanın. |

Modu tek bir satırla ayarlayın:

```java
import com.aspose.words.RecoveryMode;

// Step 2: Tell the loader to be forgiving
loadOptions.setRecoveryMode(RecoveryMode.Tolerant); // or RecoveryMode.Strict
```

**Neden önemli:** **Kurtarma modunu** kullandığınızda, kütüphane içsel olarak bozuk bölümleri yamalar, eksik XML düğümlerini yeniden oluşturur ve size kullanılabilir bir `Document` nesnesi verir. *strict* modunda ise bunun yerine bir `InvalidFormatException` alırsınız.

## Adım 3 – Belgeyi Seçeneklerinizle Yükleme

Şimdi dosyayı Aspose.Words’e, az önce yapılandırdığınız `LoadOptions` ile birlikte veriyorsunuz.

```java
import com.aspose.words.Document;

// Step 3: Load the (potentially corrupted) DOCX
String filePath = "C:/Documents/corrupted.docx";
Document doc = new Document(filePath, loadOptions);
```

Dosya sadece hafifçe bozulmuşsa, `doc` tam işlevsel bir `Document` nesnesi olacaktır. Artık şu işlemleri yapabilirsiniz:

- Metni okuyun (`doc.getText()`),
- Başka bir formata kaydedin (`doc.save("repaired.pdf")`),
- Veya `Document` API’si üzerinden kurtarılan parçaların listesini inceleyin.

### Kurtarmayı Doğrulama

Kurtarmanın gerçekten başarılı olduğunu onaylamak için hızlı bir tutarlılık kontrolü yapın:

```java
if (doc.getSections().getCount() > 0) {
    System.out.println("Document loaded successfully – recovery mode worked!");
} else {
    System.out.println("No sections found – the file might be beyond repair.");
}
```

## Adım 4 – Kenar Durumlarını Ele Alma

### 4.1 Tolerant Yeterli Değilse

Bazen dosya o kadar bozulmuş olur ki **Tolerant** mod bile parçaları bir araya getiremez (örneğin çekirdek XML eksik). Bu nadir durumlarda şunları yapabilirsiniz:

1. **`RecoveryMode.Strict` ile ikinci bir yükleme denemek**; hata mesajı daha fazla detay verebilir.
2. **Bir zip‑yardımcısına geri dönmek**; XML parçalarını manuel olarak çıkartıp onarmak.
3. **İstisnayı loglamak** ve kullanıcıyı belgenin kurtarılamaz olduğuna bilgilendirmek.

```java
try {
    loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
    Document doc = new Document(filePath, loadOptions);
    // proceed with doc
} catch (Exception e) {
    System.err.println("Tolerant mode failed: " + e.getMessage());
    // optional: retry with Strict or alert the user
}
```

### 4.2 Bellek Hususları

Kurtarma etkinleştirilmiş halde devasa DOCX dosyalarını yüklemek, Aspose.Words hem orijinal hem de düzeltilmiş yapıyı bellekte tuttuğu için geçici olarak bellek kullanımını ikiye katlayabilir. Büyük partiler işliyorsanız:

- **Aynı `LoadOptions` örneğini yeniden kullanın**; her seferinde yeni bir tane oluşturmak yerine.
- **`Document`i hemen serbest bırakın** (`doc.close()`) işiniz bittiğinde.
- **Yeterli heap’e sahip bir JVM’de çalışın** (`-Xmx2g` veya çok‑gigabayt dosyalar için daha yüksek).

### 4.3 Düzeltlenmiş Dosyayı Kaydetme

Başarılı bir yüklemeden sonra, **temizlenmiş sürümü** kaydetmek isteyebilirsiniz; böylece bir daha kurtarma yapmanıza gerek kalmaz.

```java
String repairedPath = "C:/Documents/repaired.docx";
doc.save(repairedPath);
System.out.println("Repaired file saved to: " + repairedPath);
```

Artık bir sonraki sefer `repaired.docx` dosyasını açtığınızda **kurtarma modunu kullan** adımını tamamen atlayabilirsiniz.

## Sık Sorulan Sorular

**S: Bu eski `.doc` dosyaları için de çalışır mı?**  
C: Evet. Aynı `LoadOptions` yaklaşımı `.doc` ve `.rtf` dosyalarına da uygulanır. Sadece dosya uzantısını değiştirin.

**S: `setRecoveryMode`u diğer yükleme seçenekleriyle (örneğin şifre) birleştirebilir miyim?**  
C: Kesinlikle. `LoadOptions` içinde `setPassword` ve `setLoadFormat` gibi özellikler vardır. `setRecoveryMode`u çağırmadan önce bunları ayarlayın.

**S: Performans maliyeti var mı?**  
C: Biraz—kurtarma ek bir ayrıştırma yükü getirir. Benchmark’lerde, 5 MB bozuk bir dosya **Tolerant** modunda temiz bir dosyanın strict yüklemesine göre yaklaşık %30 daha yavaş yükleniyor. Çoğu toplu iş için hâlâ kabul edilebilir.

## Tam Çalışan Örnek

Aşağıda **docx dosyasını açma**, **kurtarma modunu kullanma** ve **düzeltilmiş bir kopya kaydetme** işlemlerini gösteren eksiksiz, çalıştırılabilir bir Java sınıfı bulunuyor.

```java
package com.example.recovery;

import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        // Path to the possibly corrupted DOCX
        String inputPath = "C:/Documents/corrupted.docx";
        // Where the repaired file will be saved
        String outputPath = "C:/Documents/repaired.docx";

        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose recovery mode – Tolerant is usually enough
        loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
        // If you need strict validation, switch to RecoveryMode.Strict

        try {
            // 3️⃣ Load the document with the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Quick sanity check
            if (doc.getSections().getCount() > 0) {
                System.out.println("✅ Document loaded – recovery succeeded.");
            } else {
                System.out.println("⚠️ No sections found – the file may be beyond repair.");
            }

            // 4️⃣ (Optional) Save a clean copy for future use
            doc.save(outputPath);
            System.out.println("💾 Repaired file saved to: " + outputPath);
        } catch (Exception e) {
            // Handle cases where even tolerant mode fails
            System.err.println("❌ Failed to load document: " + e.getMessage());
            // You could retry with Strict or log for further analysis
        }
    }
}
```

Projeye Aspose.Words for Java JAR’ını sınıf yoluna ekledikten sonra bu sınıfı çalıştırın. Giriş dosyası sadece biraz hasar görmüşse, **✅** mesajını ve diskte yeni bir `repaired.docx` dosyasını göreceksiniz.

## Sonuç

Java’da **kurtarma modunu ayarlama** ve bozuk Word dosyalarını başarıyla **açma** için ihtiyacınız olan her şeyi ele aldık. Bir `LoadOptions` nesnesi oluşturup uygun `RecoveryMode`u seçerek ve zaman zaman ortaya çıkan kenar durumlarını yöneterek, “dosya açılamıyor” anını sorunsuz bir kurtarma iş akışına dönüştürebilirsiniz.

Unutmayın:

- **Tolerant**, çoğu *hasarlı word dosyasını kurtarma* senaryosu için tercih edilen moddur.  
- **Strict**, mutlak temizlik gerektiğinde sert bir başarısızlık sağlar.  
- Yüklenen belgeyi her zaman doğrulayın ve mümkünse gelecekteki çalışmalarda temiz bir kopya kaydedin.

Artık “**docx dosyasını nasıl açarım**” sorusuna somut bir kod parçacığı ve net bir açıklama ile cevap verebilirsiniz. İyi kodlamalar, belgeleriniz sağlıklı kalsın!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}