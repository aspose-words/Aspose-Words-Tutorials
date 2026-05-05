---
category: general
date: 2026-05-04
description: Aspose Words LoadOptions'ın bozuk Word dosyalarını nasıl kurtarabileceğini,
  kurtarma modunu nasıl kullanacağını, bozuk docx dosyalarını nasıl onaracağını ve
  tek bir öğreticide Word sayfa sayısını nasıl alacağınızı öğrenin.
draft: false
keywords:
- aspose words loadoptions
- recover corrupted word
- use recovery mode
- repair corrupted docx
- get word page count
language: tr
og_description: Bozuk Word dosyalarını kurtarmak için Aspose.Words LoadOptions'ı ustalaştırın,
  doğru kurtarma modunu seçin, bozuk docx dosyasını onarın ve sayfa sayısını alın.
og_title: aspose words loadoptions – Bozuk Word Belgelerini Kurtar
tags:
- Aspose.Words
- Java
- Document Recovery
title: aspose words loadoptions – Java’da Bozuk Word Belgelerini Kurtarın
url: /tr/java/document-loading-and-saving/aspose-words-loadoptions-recover-corrupted-word-docs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose words loadoptions – Bozuk Word Belgelerini Java’da Kurtarın

Hiç bir Word dosyasını açmaya çalıştığınızda aniden yüklenmediğini gördünüz mü? Bir müşteriniz size **bozuk bir docx** gönderdiğinde ve onu kurtarıp kurtaramayacağınızı bilmediğinizde o iç sıkıntısı… İyi haber? **aspose words loadoptions** ile Aspose.Words’e belge bozuk olduğunda nasıl davranması gerektiğini, bir istisna fırlatmasını mı yoksa sessiz bir düzeltme denemesi mi yapacağını söyleyebilirsiniz.  

Bu rehberde `LoadOptions` kullanarak **bozuk Word** dosyalarını **kurtarmayı**, **kurtarma modunu** ayarlamayı, **bozuk docx’i** otomatik olarak **tamir etmeyi** ve sonunda kurtarılan belgenin **sayfa sayısını** almayı göstereceğiz. Harici bir araç yok, sadece saf Java ve Aspose.Words.

## Gereksinimler

- **Aspose.Words for Java** (v24.12 veya sonrası) – en yeni sürüm birkaç ekstra güvenlik kontrolü ekli.
- Bir **Java IDE** (IntelliJ IDEA, Eclipse veya `javac` ile çalışan basit bir metin editörü).
- Test etmek istediğiniz **bozuk DOCX** (biz ona `Corrupted.docx` diyeceğiz).
- **Java sözdizimi hakkında temel bilgi** – karmaşık bir şey değil, sadece klasik `public static void main`.

> **İpucu:** Orijinal dosyanın bir yedeğini alın; kurtarma denemeleri bazen ikili dosyanın bölümlerini yeniden yazabilir.

## Adım 1: LoadOptions Oluşturun – Kurtarmanın Kalbi

İlk yapmanız gereken bir `LoadOptions` nesnesi örneklemektir. Bu nesne kontrol panelinizdir; Aspose.Words’e dosyayla karşılaştığında nasıl davranması gerektiğini söyler.

```java
// Step 1: Initialise LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Bu adım neden kritik? Çünkü `LoadOptions` olmadan kütüphane varsayılan davranışına döner; bu da hataları sessizce görmezden gelmesine ya da daha da kötüsü, daha sonra çökebilecek kısmen‑yüklenmiş bir belge döndürmesine yol açabilir. Seçenekleri açıkça yapılandırarak deterministik hata yönetimi elde edersiniz.

## Adım 2: Doğru Kurtarma Modunu Seçin

Aspose.Words iki kurtarma stratejisi sunar:

| Mod | Davranış |
|------|-----------|
| `RecoveryMode.STRICT` | Belge tam olarak onarılamazsa bir istisna fırlatır. |
| `RecoveryMode.REPAIR` | Dosyayı düzeltmeye çalışır ve bazı içerikler kaybolsa bile yüklemeye devam eder. |

**Bozuk word dosyasını kurtarma** senaryosunda düzeltmenin başarılı olup olmadığını bilmek istiyorsanız, `STRICT` en güvenli seçimdir. Daha esnek bir yaklaşım isterseniz `REPAIR`’a geçin.

```java
// Step 2: Set the recovery mode
loadOptions.setRecoveryMode(RecoveryMode.STRICT);
// loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // Uncomment to attempt automatic repair
```

> **Neden biri diğerine tercih edilir?**  
> *STRICT* size net bir sinyal verir—belge kullanılabilir ya da kullanıcıyı uyarmanız gerekir. *REPAIR* ise toplu işlerde bir iki görüntüyü kaybetmeyi göze alabileceğiniz durumlar için kullanışlıdır.

## Adım 3: Muhtemelen Bozuk Belgeyi Yükleyin

Şimdi `LoadOptions` ile yapılandırdığınız nesneyi geçirerek dosyayı açıyorsunuz. Dosya onarılamazsa ve `STRICT` seçtiyseniz bir istisna fırlatılacak; aksi takdirde bir `Document` nesnesi elde edeceksiniz.

```java
// Step 3: Load the document with the configured options
Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);
```

Yolun mutlak ya da proje köküne göre göreceli olduğuna dikkat edin. `Document` sınıfı tüm Word dosyasını soyutlayarak sayfa sayısı, bölümler gibi bilgileri sorgulamayı ve hatta kurtarma sonrası içeriği düzenlemeyi kolaylaştırır.

## Adım 4: Yüklemeyi Doğrulayın – Word Sayfa Sayısını Alın

Hızlı bir bütünlük kontrolü olarak Aspose.Words’e belgenin kaç sayfa olduğunu sorun. Sayı sıfırdan farklıysa büyük ihtimalle **bozuk docx’i tamir ettiniz** demektir.

```java
// Step 4: Output the page count to confirm successful loading
System.out.println("Loaded successfully, page count = " + document.getPageCount());
```

Tipik çıktı:

```
Loaded successfully, page count = 12
```

Eğer belge `STRICT` altında gerçekten okunamazsa, kod bu satıra gelmeden bir istisna fırlatır. Bu da `sayfa sayısı` kontrolünü hem bir doğrulama hem de sonraki mantık (ör. web görüntüleyicide sayfalama) için faydalı bir bilgi haline getirir.

## Tam Çalışan Örnek

Aşağıda tüm parçaları bir araya getiren, çalıştırılmaya hazır Java programı bulunuyor. `RecoveryModeDemo.java` adlı bir dosyaya kopyalayıp yapıştırın, yolu ayarlayın ve `javac RecoveryModeDemo.java && java RecoveryModeDemo` komutlarıyla çalıştırın.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to control how the file is opened
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Choose strict recovery – an exception is thrown if the file cannot be repaired
        loadOptions.setRecoveryMode(RecoveryMode.STRICT);
        // loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // alternative: attempt repair and continue

        // Step 3: Load the possibly‑corrupted document using the configured options
        Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // Step 4: Verify that the document was loaded (e.g., output its page count)
        System.out.println("Loaded successfully, page count = " + document.getPageCount());
    }
}
```

### Beklenen Sonuç

- **Dosya kurtarılabilir ise:** konsol sayfa sayısını yazdırır ve `Document` nesnesiyle güvenle işlem yapmaya devam edebilirsiniz.
- **Dosya onarılamazsa (STRICT modu):** bir `com.aspose.words.UnsupportedFileFormatException` (veya benzeri) fırlatılır; bunu yakalayıp nazikçe işleyebilirsiniz.

## Sık Sorulan Sorular & Kenar Durumları

### Hata detaylarını tam olarak kaydetmem gerekirse ne yapmalıyım?

Yükleme kodunu bir `try‑catch` bloğuna alın ve `e.getMessage()`’ı loglayın. Böylece eksik parça, kırık ilişki ya da bozuk akış gibi net bir neden elde edersiniz.

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    System.out.println("Pages: " + doc.getPageCount());
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
}
```

### Sadece belirli bölümleri (ör. metin ama resimler değil) kurtarabilir miyim?

Aspose.Words ince ayarlı kurtarma seçenekleri sunmaz, ancak yükleme sonrası `NodeType` elemanları üzerinde döngü kurarak `NodeType.SHAPE` (resimler) olanları atabilirsiniz.

### Eski `.doc` dosyalarıyla çalışır mı?

Evet. `LoadOptions` tüm Word formatları (`.doc`, `.docx`, `.dot`, `.dotx`) için çalışır. Aynı kurtarma mantığı geçerlidir.

### Şifre korumalı dosyalar nasıl ele alınır?

Dosya şifreli ise `LoadOptions` şifreyi atlamaz. Şifreyi `loadOptions.setPassword("yourPassword")` ile sağlamalısınız. Kurtarma modu yalnızca şifre çözme başarılı olduğunda devreye girer.

## Üretim İçin İpuçları

- **Seçilen kurtarma modunu loglayın** – Daha sonra belirli bir dosyanın neden başarılı ya da başarısız olduğunu denetlerken yardımcı olur.
- **Orijinal dosyayı asla üzerine yazmayın** – Kurtarılan belgeyi yeni bir konuma kaydedin (`document.save("Recovered.docx")`).
- **Doğrulama ile birleştirin** – Kurtarma sonrası hızlı bir yazım‑denetimi veya yapısal doğrulama çalıştırarak belgenin iş kurallarınıza uygunluğunu kontrol edin.
- **Toplu işleme** – Birçok dosyayla uğraşırken her birini döngü içinde işleyin, istisnaları ayrı ayrı yakalayın ve başarı‑başarısızlık özet raporu tutun.

## Sonuç

Artık **aspose words loadoptions** kullanarak **bozuk Word** belgelerini **kurtarmak**, **kurtarma modunu** katı ya da esnek şekilde seçmek, isteğe bağlı olarak **bozuk docx’i tamir etmek** ve sonunda **kurtarılan dosyanın sayfa sayısını** almak için eksiksiz bir tarifiniz var. Yaklaşım deterministik, mevcut Java iş akışlarına kolayca entegre edilebilir ve kırık ikili dosyalarla karşılaştığınızda kütüphanenin ne kadar agresif davranacağını tam kontrol etmenizi sağlar.

Daha ileri gitmeye hazır mısınız? Bir toplu işte `RecoveryMode.STRICT` yerine `REPAIR` kullanın ya da örneği otomatik olarak kurtarılan dosyayı güvenli bir klasöre kaydedecek şekilde genişletin. Olanaklar sınırsızdır ve Aspose.Words ile en inatçı Word dosyası hatalarını bile yönetebilirsiniz.

İyi kodlamalar, ve belgeleriniz her zaman sorunsuz yüklensin!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}