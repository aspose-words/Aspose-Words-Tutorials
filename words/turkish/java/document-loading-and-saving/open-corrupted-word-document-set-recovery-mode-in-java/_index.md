---
category: general
date: 2026-05-26
description: Java'da Aspose.Words ile bozuk Word belgesini açın. Kurtarma modunu nasıl
  ayarlayacağınızı ve bozuk Word dosyalarını güvenilir bir şekilde nasıl kurtaracağınızı
  öğrenin.
draft: false
keywords:
- open corrupted word document
- set recovery mode
- how to recover corrupted word file
- Aspose.Words Java
- document recovery Java
language: tr
og_description: Aspose.Words kullanarak Java'da bozuk Word belgesini açın. Bu kılavuz,
  kurtarma modunu nasıl ayarlayacağınızı ve bozuk Word dosyalarını verimli bir şekilde
  nasıl kurtaracağınızı gösterir.
og_title: Bozuk Word Belgesini Aç – Java'da Kurtarma Modunu Ayarla
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  headline: Open Corrupted Word Document – Set Recovery Mode in Java
  type: TechArticle
- description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  name: Open Corrupted Word Document – Set Recovery Mode in Java
  steps:
  - name: Why each line matters
    text: '* **`LoadOptions loadOptions = new LoadOptions();`** – without this object
      Aspose.Words uses default recovery, which *rejects* corrupted files. Creating
      it gives you the hook to change that behavior. * **`setRecoveryMode(...)`**
      – this is the **set recovery mode** call that decides whether warnings '
  - name: 1. File Not Found
    text: 'If the path is wrong, `Document` throws a `FileNotFoundException`. Wrap
      the load in a try‑catch block and log a friendly message:'
  - name: 2. Irrecoverable Corruption
    text: Even with `RECOVER_WITH_WARNINGS`, some structures are beyond repair. In
      that case Aspose.Words still loads what it can, but you’ll see warnings like
      “Cannot read paragraph properties”. Pay attention to the console output; those
      warnings often point to missing sections that you may need to reconstru
  - name: 3. Large Files and Performance
    text: Recovery adds a small overhead because the library parses the file twice—once
      to detect issues, again to rebuild. For multi‑gigabyte documents, consider streaming
      the file or increasing the JVM heap (`-Xmx2g`) to avoid `OutOfMemoryError`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word
title: Bozuk Word Belgesini Aç – Java’da Kurtarma Modunu Ayarla
url: /tr/java/document-loading-and-saving/open-corrupted-word-document-set-recovery-mode-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bozuk Word Belgesini Aç – Java’da Kurtarma Modunu Ayarlama

Hiç bozuk bir Word belgesini açmaya çalışıp programın bir istisna ile takıldığını gördünüz mü? Yalnız değilsiniz—bu kırık .docx dosyaları gerçekten can sıkıcı olabilir. İyi haber şu ki Aspose.Words for Java, **bozuk word belgesini aç**manız için ince ayar kontrolü sunar; uygulama çökmeden, uyarı ister, sessiz kurtarma ister ya da kesin reddetme tercih edebilirsiniz.

Bu öğreticide, doğru `LoadOptions` oluşturulmasından, uygun **set recovery mode** değerinin seçilmesine ve belgenin gerçekten yüklendiğinin doğrulanmasına kadar tüm süreci adım adım göstereceğiz. Sonunda, **bozuk word dosyasını nasıl kurtarılır** sorusunun programatik cevabını, manuel kopyala‑yapıştıra gerek kalmadan bileceksiniz.

> **Gereksinimler**  
> * Java 8 veya daha yeni (API Java 11 ile de çalışır)  
> * Aspose.Words for Java 23.9 (veya en son sürüm)  
> * Örnek bir bozuk .docx dosyası—elinizde yoksa geçerli bir dosyanın adını değiştirerek bozulmuş gibi taklit edebilirsiniz  

Haydi başlayalım.

## Bozuk Word Belgesini Aç – Adım‑Adım Genel Bakış

Aşağıda uygulayacağımız yüksek seviyeli akış yer alıyor:

1. **`LoadOptions` oluştur** – bu nesne Aspose.Words’e sorunla karşılaştığında nasıl davranacağını söyler.  
2. **Kurtarma modunu ayarla** – `RECOVER_WITH_WARNINGS`, `RECOVER_WITHOUT_WARNINGS` veya `REJECT_CORRUPTED` seçeneklerinden birini seç.  
3. **Belgeyi yükle** – yapılandırılmış seçenekleri kullan.  
4. **Yüklemenin başarılı olduğunu doğrula** (ör. sayfa sayısını yazdır).  

Her adım ayrıntılı olarak açıklanacak ve IDE’nize doğrudan kopyalayıp yapıştırabileceğiniz kod parçacıkları sunulacak.

## Farklı Senaryolar İçin Kurtarma Modunu Ayarlama

Aspose.Words, `LoadOptions.RecoveryMode` içinde üç kurtarma stratejisi tanımlar:

| Mod | Davranış | Ne zaman kullanılmalı |
|------|-----------|------------------------|
| `RECOVER_WITH_WARNINGS` | Belgeyi yüklemeye çalışır, ancak ortaya çıkan sorunları konsolda uyarı olarak gösterir. | Hangi hataların oluştuğunu görmek, ancak işlemi durdurmak istemediğiniz durumlar. |
| `RECOVER_WITHOUT_WARNINGS` | Yapabildiği kadar sessizce düzeltir ve uyarıları bastırır. | Logların temiz kalması gereken üretim ortamları. |
| `REJECT_CORRUPTED` | Bozukluk tespit edildiği anda bir istisna fırlatır. | Hızlı başarısız olması gereken katı doğrulama hatları. |

Doğru modu seçmek, **set recovery mode** işlemini doğru yapmanın özüdür. Çoğu hata ayıklama oturumunda `RECOVER_WITH_WARNINGS` en uygun seçimdir çünkü hangi bölümlerin onarıldığını net bir şekilde gösterir.

## Aspose.Words Kullanarak Bozuk Word Dosyasını Nasıl Kurtarılır

Aşağıda **tam, çalıştırılabilir bir Java programı** yer alıyor; tüm süreci gösteriyor. `RecoveryModeDemo.java` dosyasına yapıştırın, yolu ayarlayın ve çalıştırın.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions – this controls recovery
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // -------------------------------------------------
        // Step 2: Choose the recovery behavior
        // -------------------------------------------------
        // Option A – show warnings (great for debugging)
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);

        // Uncomment ONE of the alternatives below if you need a different behavior:
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITHOUT_WARNINGS);
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.REJECT_CORRUPTED);

        // -------------------------------------------------
        // Step 3: Load the potentially corrupted document
        // -------------------------------------------------
        // Replace the placeholder with the actual path to your .docx file
        String corruptedPath = "C:/temp/corrupted.docx";
        Document doc = new Document(corruptedPath, loadOptions);

        // -------------------------------------------------
        // Step 4: Verify that the document is usable
        // -------------------------------------------------
        System.out.println("Document loaded successfully!");
        System.out.println("Page count = " + doc.getPageCount());

        // Bonus: you can now save the repaired file if you wish
        doc.save("C:/temp/recovered.docx");
        System.out.println("Recovered file saved as recovered.docx");
    }
}
```

### Her satırın önemi

* **`LoadOptions loadOptions = new LoadOptions();`** – bu nesne olmadan Aspose.Words varsayılan kurtarmayı kullanır ve bozuk dosyaları *reddeder*. Oluşturmak, davranışı değiştirme kancasını sağlar.  
* **`setRecoveryMode(...)`** – bu, **set recovery mode** çağrısıdır; uyarıların gösterilip gösterilmeyeceğini veya bir istisna oluşturulup oluşturulmayacağını belirler.  
* **`new Document(path, loadOptions);`** – kurduğumuz `LoadOptions` nesnesini kabul eden yapıcı, kütüphanenin bozuk dosyayla nasıl başa çıkacağını baştan bilir.  
* **`doc.getPageCount()`** – hızlı bir bütünlük kontrolü. Belge yüklendi ve sayfa sayısı döndürdüyse, **bozuk word dosyasını nasıl kurtarılır** sorusunun cevabını almışsınız demektir.  
* **`doc.save(...)`** – isteğe bağlı ama kullanışlı; onarılmış sürümü daha sonra kullanmak üzere diske yazabilirsiniz.

## Yaygın Kenar Durumlarını Ele Alma

### 1. Dosya Bulunamadı

Yol hatalıysa, `Document` bir `FileNotFoundException` fırlatır. Yüklemeyi try‑catch bloğuna alın ve dostça bir mesaj kaydedin:

```java
try {
    Document doc = new Document(corruptedPath, loadOptions);
    // proceed...
} catch (FileNotFoundException e) {
    System.err.println("The file was not found: " + corruptedPath);
}
```

### 2. Geri Döndürülemez Bozukluk

`RECOVER_WITH_WARNINGS` kullanılsa bile bazı yapılar tamir edilemez. Bu durumda Aspose.Words mümkün olanı yükler, ancak “Cannot read paragraph properties” gibi uyarılar görürsünüz. Konsol çıktısına dikkat edin; bu uyarılar genellikle manuel olarak yeniden oluşturmanız gereken eksik bölümleri işaret eder.

### 3. Büyük Dosyalar ve Performans

Kurtarma, kütüphanenin dosyayı iki kez ayrıştırması gerektiği için küçük bir ek yük getirir—ilk seferde sorunları tespit eder, ikinci seferde yeniden oluşturur. Çok‑gigabaytlık belgeler için dosyayı akış olarak işlemek ya da JVM yığınını (`-Xmx2g`) artırmak (`OutOfMemoryError` önlemek) akıllıca olur.

## Pro İpuçları – Kurtarmayı Sağlamlaştırma

* **Uyarıları bir dosyaya kaydet** – `System.err` çıktısını bir logger’a yönlendirerek neyin düzeltildiğine dair bir denetim izi oluşturun.  
* **Kurtarmadan sonra doğrula** – `doc.updatePageLayout();` çalıştırıp ardından sayfa sayısını tekrar kontrol edin; bazı durumlarda bozuk bölümler düzeltildikten sonra düzen değişebilir.  
* **Toplu kurtarma otomasyonu** – demoyu bir döngü içinde, aynı `LoadOptions` ile bir klasördeki tüm bozuk dosyaları işleyebilecek şekilde paketleyin.

## Sonuç

Artık Aspose.Words for Java kullanarak **bozuk word dosyasını nasıl kurtarılır** sorusunun tam cevabını biliyorsunuz. Bir `LoadOptions` örneği oluşturup, senaryonuza uygun **set recovery mode** değerini ayarlayarak ve belgeyi bu seçeneklerle yükleyerek, uygulamanızın çökmeden **bozuk word belgesini aç**masını sağlayabilirsiniz. Yukarıdaki örnek kod, sayfa sayısını yazdıran ve temizlenmiş bir kopyayı kaydeden eksiksiz, çalıştırılabilir bir çözümdür.

Sırada ne? Kurtarma modunu `RECOVER_WITHOUT_WARNINGS` olarak değiştirip konsol çıktısını karşılaştırın ya da şifreli belgeleri yüklemeyi deneyin (parola sağlamak için ek bir adım gerekir).


## İlgili Öğreticiler

- [Aspose.Words Java&#58; Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)
- [How to Compare Two Word Files with Aspose.Words for Java](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}