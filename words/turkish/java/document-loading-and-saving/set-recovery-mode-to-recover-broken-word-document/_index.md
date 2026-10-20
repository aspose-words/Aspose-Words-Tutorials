---
category: general
date: 2026-02-15
description: Kurtarma modunu ayarlamak, belgeyi kurtarma ile yüklemenizi sağlar; bu
  sayede bozuk Word belgesini kurtarmak ve kurtarma Word belgesi hatalarını düzeltmek
  kolaylaşır.
draft: false
keywords:
- set recovery mode
- recover broken word document
- load document with recovery
- recover word document errors
language: tr
og_description: Kurtarma modunu ayarlamak, kurtarma ile bir belge yüklemenin anahtarıdır;
  bu sayede Java’da bozuk Word belge hatalarını kurtarabilirsiniz.
og_title: Kurtarma Modunu Ayarla – Bozuk Word Belgesini Hızlıca Kurtar
tags:
- Aspose.Words
- Java
- Document Recovery
title: Kırık Word belgesini kurtarmak için kurtarma modunu ayarla
url: /tr/java/document-loading-and-saving/set-recovery-mode-to-recover-broken-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set recovery mode – Aspose.Words ile Bozuk Bir Word Belgesini Nasıl Kurtarabilirsiniz

Hiç bir Word dosyasını açmaya çalıştınız mı ve aniden yüklenmeyi reddediyor? Bozuk bir *.docx* dosyasına bakıyor ve sıfırdan başlamanız gerekip gerekmediğini merak ediyor olabilirsiniz. İyi haber? Aspose.Words'ta **set recovery mode**, *load document with recovery* yapmanın zarif bir yolunu sunar ve içeriğin çoğunu sağlam tutar.  

Bu öğreticide tam olarak nasıl **set recovery mode** yapacağınızı, *RELAXED* seçeneğinin bozuk dosyalar için genellikle en iyi seçim olmasının nedenini ve hâlâ ortaya çıkabilen ara sıra *recover word document errors* nasıl ele alınacağını öğreneceksiniz. Harici araçlar yok, sadece saf Java ve birkaç satır kod.

> **Ne elde edeceksiniz:** bozuk bir Word dosyasını yükleyen, okunamayan bölümleri atlayan ve sonraki işleme hazır kullanılabilir bir `Document` nesnesi bırakan tam, çalıştırılabilir bir örnek.

---

## Önkoşullar

Before we jump in, make sure you have:

- **Aspose.Words for Java** (v24.9 veya daha yeni) Maven veya manuel JAR aracılığıyla projenize eklenmiş.
- Test etmek istediğiniz **bozuk .docx** dosyası (`Corrupted.docx` olarak adlandıralım).
- Temel Java bilgisi – Word‑işleme sihirbazı olmanıza gerek yok, sadece bir `main` metoduyla rahat olmanız yeterli.

Eğer bunlardan herhangi birine sahip değilseniz, en son Aspose.Words JAR dosyasını [resmi siteden](https://products.aspose.com/words/java) alın ve sınıf yolunuza ekleyin. Hepsi bu—ekstra bağımlılık yok.

## Adım 1: Kurtarma Modlarını Anlamak

Aspose.Words offers two recovery strategies:

| Mod | Davranış | Ne zaman kullanılmalı |
|------|----------|------------------------|
| **RELAXED** | Okunamayan bölümleri atlar, geri kalanını tutar. | Çoğu bozuk dosya – **recover broken word document** istiyorsunuz ve istisna istemiyorsunuz. |
| **STRICT** | Her hatada bir istisna fırlatır. | Mükemmel, hatasız bir yükleme garantilemeniz gerektiğinde (bozuk kaynaklar için nadir). |

> **Pro ipucu:** *RELAXED*, “sadece bir şeyler geri al” senaryoları için varsayılandır, *STRICT* ise bir hatanın süreci durdurması gereken otomatik hatlıklarda faydalıdır.

## Adım 2: Bir `LoadOptions` Nesnesi Oluşturun ve **set recovery mode**

İşte anahtar kelimenin kodda göründüğü yer. Dosyayı yüklemeden önce bir `LoadOptions` örneğinde açıkça **set recovery mode** yapıyoruz.

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions and choose a recovery mode.
        // RELAXED will skip unreadable parts, while STRICT throws an exception.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // <-- set recovery mode

        // 2️⃣ Load the potentially corrupted document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 3️⃣ Verify that the document loaded and optionally save a cleaned copy.
        System.out.println("Document loaded successfully. Page count: " + doc.getPageCount());
        doc.save("Recovered.docx");
    }
}
```

**Neden önemli:** `setRecoveryMode` çağrısıyla Aspose.Words'a dosyayı ne kadar agresif kurtarmaya çalışması gerektiğini söylersiniz. Bu çağrı olmadan kütüphane varsayılan olarak *STRICT* olur, ki bu da sorunun ilk işaretinde işlemi durdurur—*recover broken word document* iş akışının amacını bozar.

## Adım 3: Yüklemeyi Doğrulayın – Gerçekten **recover broken word document** yaptık mı?

Yüklemeden sonra `Document` nesnesini inceleyebilirsiniz:

```java
// Check if any sections were dropped
int sections = doc.getSections().getCount();
System.out.println("Sections recovered: " + sections);
```

Konsol makul bir bölüm sayısı gösteriyorsa, başarılı bir şekilde *load document with recovery* yaptınız demektir. Pratikte, çoğu metin, tablo ve görselin korunduğunu, bozuk parçaların ise basitçe kaybolduğunu fark edeceksiniz.

## Adım 4: Kalan **recover word document errors** Sorunlarını Zarifçe Ele Alın

*RELAXED* modunda bile, birkaç uç durum hâlâ uyarı verebilir. Uygulamanızın çalışmaya devam etmesi için yüklemeyi bir try‑catch bloğuna alın:

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    // Continue processing...
} catch (Exception ex) {
    System.err.println("Recovery failed: " + ex.getMessage());
    // Optionally fallback to a backup copy or notify the user.
}
```

**Bu ne zaman olur?** Dosya o kadar hasarlıysa ki rahat bir ayrıştırıcı bile geçerli bir belge yapısı tanımlayamazsa, Aspose.Words yine bir istisna fırlatır. Bu nadir anlarda, kullanıcıdan farklı bir kopya sağlamasını isteyebilirsiniz.

## Adım 5: Kurtarılan Dosyayı Kaydedin (İsteğe Bağlı)

Çoğu geliştirici, aşağıdaki `save` çağrısıyla bozuk parçaları içermeyen temiz bir `.docx` oluşturup bunu sonraki sistemlere teslim etmek ister.

```java
doc.save("Recovered.docx");
System.out.println("Recovered file saved as Recovered.docx");
```

Artık Microsoft Word, Google Docs veya başka bir görüntüleyicide açılabilen bir **recover broken word document**'a sahipsiniz—hata iletişim kutuları yok.

## Görsel Genel Bakış (Resim)

![set recovery mode akışını gösteren diyagram – bozuk dosyadan kurtarılmış belgeye](https://example.com/images/recovery-flow.png "set recovery mode akış diyagramı")

*Alt metin, birincil anahtar kelimeyi açıkça içerir, bu da arama motorları ve ekran okuyucular için faydalıdır.*

## Yaygın Sorular & Uç Durumlar

| Soru | Cevap |
|------|-------|
| *Bozuk bölümleri adli analiz için saklamam gerekirse ne olur?* | `LoadOptions.setRecoverMode(LoadOptions.RecoveryMode.STRICT)` kullanın ve istisnayı yakalayın. İstisna mesajı sorunlu bölümler hakkında detaylar içerir. |
| *RELAXED ve STRICT arasında çalışma zamanında geçiş yapabilir miyim?* | Kesinlikle—her yüklemeden önce istediğiniz modla yeni bir `LoadOptions` örneği oluşturmanız yeterlidir. |
| *Bu eski .doc dosyalarıyla çalışır mı?* | Evet. Aynı `LoadOptions` hem `.doc` hem de `.docx` formatlarına uygulanır. |
| *Performans cezası var mı?* | Minimum. Ek ayrıştırma yükü, tam bir belge yüklemesinin maliyetiyle karşılaştırıldığında ihmal edilebilir. |

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) {
        try {
            // Step 1 – configure recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // set recovery mode

            // Step 2 – load the corrupted file
            Document doc = new Document("Corrupted.docx", loadOptions);

            // Step 3 – optional verification
            System.out.println("Loaded! Pages: " + doc.getPageCount());

            // Step 4 – save a clean copy
            doc.save("Recovered.docx");
            System.out.println("Saved recovered document as Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
        }
    }
}
```

Programı çalıştırın, bozuk dosyanıza yönlendirin ve çıktıyı izleyin. Her şey sorunsuz giderse, sayfa sayısının yazdırıldığını ve kaynak dosyanızın yanında yeni bir `Recovered.docx` belgesi görüneceğini göreceksiniz.

## Sonuç

Aspose.Words'ta **set recovery mode** yapmanız için gereken her şeyi ele aldık; doğru `RecoveryMode` enum'ını seçmekten hâlâ ortaya çıkabilecek birkaç *recover word document errors* ele almaya kadar. Yukarıdaki adımları izleyerek güvenilir bir şekilde **load document with recovery** yapabilir, bozuk bir dosyanın iyi bölümlerini koruyabilir ve sonraki işlemler için temiz bir sürüm üretebilirsiniz.

Bir sonraki zorluğa hazır mısınız? **set recovery mode**'u Aspose.Words'un **document cleaning** API'leriyle birleştirmeyi deneyin—gizli paragrafları kaldırma, bozuk bağlantıları düzeltme veya hatta kurtarılan dosyayı tek seferde PDF'ye dönüştürme. Olanaklar sınırsızdır ve artık bozuk Word dosyalarını doğrudan ele almak için sağlam bir temele sahipsiniz.

Kodlamaktan keyif alın, ve belgeleriniz sağlıklı kalsın!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}