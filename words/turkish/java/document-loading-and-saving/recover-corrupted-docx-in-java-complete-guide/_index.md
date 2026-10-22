---
category: general
date: 2026-06-20
description: Aspose.Words ile Java’da bozuk docx dosyalarını kurtarın. Kurtarma modunu
  nasıl ayarlayacağınızı ve sorunsuz açma için belgeyi kurtarma ile nasıl yükleyeceğinizi
  öğrenin.
draft: false
keywords:
- recover corrupted docx
- set recovery mode
- load document with recovery
- open word with recovery
- open corrupted docx
language: tr
og_description: Aspose.Words kullanarak Java’da bozuk docx dosyalarını kurtarın. Bu
  öğreticide kurtarma modunu nasıl ayarlayacağınız, belgeyi kurtarma ile nasıl yükleyeceğiniz
  ve bozuk docx dosyasını güvenli bir şekilde nasıl açacağınız gösterilmektedir.
og_title: Java'da bozuk docx dosyasını kurtarın – Tam Kılavuz
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Recover corrupted docx files in Java with Aspose.Words. Learn how to
    set recovery mode and load document with recovery for seamless opening.
  headline: Recover corrupted docx in Java – Complete Guide
  type: TechArticle
- description: Recover corrupted docx files in Java with Aspose.Words. Learn how to
    set recovery mode and load document with recovery for seamless opening.
  name: Recover corrupted docx in Java – Complete Guide
  steps:
  - name: '**Instantiate `LoadOptions`** – this object holds all the flags you want
      the loader to respect.'
    text: '**Instantiate `LoadOptions`** – this object holds all the flags you want
      the loader to respect.'
  - name: '**Call `setRecoveryMode`** – we chose `RECOVER` because we want the best
      chance of opening the file.'
    text: '**Call `setRecoveryMode`** – we chose `RECOVER` because we want the best
      chance of opening the file.'
  - name: '**Pass the options to the `Document` constructor** – Aspose.Words reads
      the file, applies the recovery logic, and returns a usable `Document` object.'
    text: '**Pass the options to the `Document` constructor** – Aspose.Words reads
      the file, applies the recovery logic, and returns a usable `Document` object.'
  - name: Open Word → *File* → *Open*.
    text: Open Word → *File* → *Open*.
  - name: Select the corrupted `.docx`.
    text: Select the corrupted `.docx`.
  - name: Click the dropdown arrow next to *Open* and choose **Open and Repair**.
    text: Click the dropdown arrow next to *Open* and choose **Open and Repair**.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Recovery
- DOCX
title: Java'da bozuk docx dosyasını kurtarma – Tam Kılavuz
url: /tr/java/document-loading-and-saving/recover-corrupted-docx-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da bozuk docx dosyalarını kurtarma – Tam Kılavuz

Hiç **bozuk docx** dosyalarını **kurtarmaya** çalıştınız ve bir duvara çarptınız mı? Bu öğreticide **kurtarma modunu ayarlama** ve **kurtarmalı belge yükleme** sayesinde Aspose.Words for Java kullanarak bozuk docx dosyasını sağlıklı bir Word belgesi gibi açabileceksiniz.  

Eğer bazı DOCX dosyalarının Word’da açılmayı reddetmesinin nedenini merak ettiyseniz, cevap genellikle normal yükleyicinin başa çıkamadığı gizli hasarlardır. Kütüphaneyi eklemekten sayfa sayısını doğrulamaya kadar ihtiyacınız olan adımları adım adım göstereceğiz ve “dosya bozuk” uyarısı almaktan kurtulacaksınız.

## Öğrenecekleriniz

- Aspose.Words’a kırık bir dosyayı ne kadar agresif onaracağını söylemek için **kurtarma modunu ayarlama** nasıl yapılır.  
- **Kurtarmalı belge yükleme** için gereken tam kod ve ciddi hasarları nazikçe ele alma.  
- **Kurtarma ile Word açma** senaryoları için ipuçları ve dosya kurtarılamadığında ne yapılacağı.  
- IDE’nize kopyalayıp yapıştırabileceğiniz tam, çalıştırılabilir bir örnek.  

### Önkoşullar

- Java 8 veya daha yeni bir sürüm yüklü.  
- Maven veya Gradle (Maven’ı ele alacağız).  
- Test etmek istediğiniz bozuk bir `.docx` dosyası (Microsoft Word’da açılmayan herhangi bir dosya yeterli).  

Aspose API’si hakkında derin bir bilgi gerekmez—sadece temel Java becerileri yeterli. Hadi başlayalım.

![bozuk docx örneği](recover_corrupted_docx.png "bozuk docx ekran görüntüsü")

## Adım 1: Aspose.Words for Java’yı Projenize Ekleyin

İlk iş, projenizin Aspose.Words JAR’ına sahip olması. Maven kullanıyorsanız, aşağıdakini `pom.xml` dosyanıza ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Gradle kullanıcıları şunu ekleyebilir:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

**İpucu:** En yeni sürüm için her zaman Aspose web sitesini kontrol edin; yeni sürümler genellikle daha iyi kurtarma algoritmaları içerir.

## Adım 2: Kurtarma Modunu Ayarlama – Bozuk Dosyaları Düzeltmenin Anahtarı

Kütüphane artık hazır, bozulma ile karşılaştığında **nasıl** davranacağını ona söylemeniz gerekiyor. İşte `setRecoveryMode` burada devreye giriyor. `RecoveryMode` enum’ı iki seçenek sunar:

| Mod | Açıklama |
|------|-------------|
| `RECOVER` | Mümkün olduğunca çok şeyi düzeltmeye çalışır ve kısmen onarılmış bir belge döndürür. |
| `REJECT` | Ciddi bir sorun tespit edildiğinde bir istisna fırlatır; temiz bir başlangıç gerektiğinde kullanışlıdır. |

Aşağıdaki kod, affedici `RECOVER` seçeneğiyle **kurtarma modunu ayarlar**:

```java
import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create LoadOptions and set the desired recovery mode
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // Use RECOVER to attempt fixing,
                                                          // REJECT to fail on severe damage

        // Step 2.2: Load the possibly corrupted document using the configured options
        Document doc = new Document("C:/files/corrupted.docx", loadOptions);

        // Step 2.3: Work with the loaded document (e.g., display page count)
        System.out.println("Loaded with " + doc.getPageCount() + " pages");
    }
}
```

**Neden önemli:** Kurtarma modu ayarlanmadan Aspose.Words varsayılan olarak `REJECT` kullanır; bu da programınızın bozuk bir parçayı gördüğü anda istisna fırlatacağı anlamına gelir. **Kurtarma modunu ayarlayarak**, kütüphaneye eksik XML düğümlerini yamalama, eksik ilişkileri geri yükleme ve genel olarak dosyayı “temizleme” izni vermiş olursunuz.

## Adım 3: Kurtarmalı Belge Yükleme – Hepsini Bir Araya Getirme

Yukarıdaki snippet zaten **kurtarmalı belge yükleme** gösteriyor, ancak açıklık getirmek için adımlara bakalım:

1. **`LoadOptions` nesnesi oluşturma** – bu nesne, yükleyicinin dikkate almasını istediğiniz tüm bayrakları tutar.  
2. **`setRecoveryMode` çağrısı** – `RECOVER` seçtik çünkü dosyanın açılma şansını en üst düzeye çıkarmak istiyoruz.  
3. **Seçenekleri `Document` yapıcısına geçirme** – Aspose.Words dosyayı okur, kurtarma mantığını uygular ve kullanılabilir bir `Document` nesnesi döndürür.

Daha savunmacı bir yaklaşım tercih ediyorsanız, yüklemeyi bir try‑catch bloğuna sarabilir ve `RECOVER` istenmeyen sonuç verirse `REJECT`’a geri dönebilirsiniz:

```java
try {
    Document doc = new Document("C:/files/corrupted.docx", loadOptions);
    System.out.println("Recovered document has " + doc.getPageCount() + " pages.");
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
    // Optional: retry with REJECT mode to see if the file is beyond repair
}
```

## Adım 4: Onarılmış Belgeyi Doğrulama

Belge yüklendikten sonra içeriğin mantıklı göründüğünden emin olmak isteyeceksiniz. Yaygın kontroller şunlardır:

- **Sayfa sayısı** – hızlı bir mantık kontrolü (`doc.getPageCount()`).  
- **Metin çıkarma** – `doc.getText()` ile ana gövdenin bütünlüğünü kontrol edin.  
- **Bir kopya kaydetme** – kurtarılan sürümü daha sonra incelemek üzere diske yazın.

```java
// Save the recovered file for manual verification
doc.save("C:/files/recovered.docx");

// Print first 200 characters of text to the console
String preview = doc.getText().substring(0, Math.min(200, doc.getText().length()));
System.out.println("Preview of recovered text:\n" + preview);
```

Ön izleme bozuk görünüyorsa, dosya geri döndürülemez bir hasar almış demektir. Bu durumda, bozuk verinin yayılmasını önlemek için `REJECT` modunu kullanmayı düşünün.

## Adım 5: İsteğe Bağlı – Kurtarma ile Word Açma (Manuel Yaklaşım)

Bazen kod yazmak istemezsiniz; sadece **kurtarma ile word açma** işlemini manuel olarak yapmanız yeterlidir. Microsoft Word kendine ait bir “Aç ve Onar” özelliği sunar:

1. Word → *Dosya* → *Aç*.  
2. Bozuk `.docx` dosyasını seçin.  
3. *Aç* düğmesinin yanındaki açılır oka tıklayın ve **Aç ve Onar** seçeneğini seçin.

Bu yöntem birçok kullanıcı için işe yarasa da, az önce ele aldığımız Java yaklaşımının otomasyon ve toplu işleme yeteneklerinden yoksundur. Ara sıra düzeltmeler için manuel yöntemi, yüzlerce dosyayı programatik olarak işlemek gerektiğinde ise Aspose.Words’u tercih edin.

## Kenar Durumları ve Yaygın Tuzaklar

- **Şiddetli bozulma** – Dosya temel `[Content_Types].xml` dosyasını kaybetmişse, `RECOVER` bile yardımcı olamaz. Bir istisna bekleyin ve kullanıcıyı bilgilendirin.  
- **Şifre korumalı dosyalar** – Kurtarma modu şifrelemeyi atlamaz. Kurtarmaya çalışmadan önce `LoadOptions.setPassword("yourPwd")` ile şifreyi sağlamalısınız.  
- **Büyük belgeler** – `RECOVER` ile devasa bir DOCX yüklemek daha fazla bellek tüketebilir. `OutOfMemoryError` alırsanız JVM heap’ini (`-Xmx2g`) artırmayı düşünün.  

## Tam Çalışan Örnek

Aşağıda doğrudan derleyip çalıştırabileceğiniz tam program yer alıyor. Dosya yolunu bozuk DOCX’inizin konumuyla değiştirin.

```java
import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        try {
            // Create LoadOptions and set recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // Attempt to fix

            // Load the corrupted document
            Document doc = new Document("C:/files/corrupted.docx", loadOptions);

            // Verify and display basic info
            System.out.println("Recovered document loaded successfully.");
            System.out.println("Page count: " + doc.getPageCount());

            // Save a clean copy
            doc.save("C:/files/recovered.docx");
            System.out.println("Recovered file saved as recovered.docx");

            // Show a short text preview
            String text = doc.getText();
            System.out.println("Text preview (first 200 chars):");
            System.out.println(text.substring(0, Math.min(200, text.length())));
        } catch (Exception ex) {
            System.err.println("Failed to recover the document: " + ex.getMessage());
        }
    }
}
```

**Beklenen çıktı (kurtarma başarılı olduğunda):**

```
Recovered document loaded successfully.
Page count: 12
Recovered file saved as recovered.docx
Text preview (first 200 chars):
Lorem ipsum dolor sit amet, consectetur adipiscing elit...
```

Belge onarılamazsa, bir yığın izleme mesajı yerine net bir hata mesajı göreceksiniz; bu da çevreleyen `try‑catch` sayesinde mümkün.

## Sonuç

Artık Aspose.Words kullanarak Java’da **bozuk docx** dosyalarını **kurtarma** konusunda bilgi sahibisiniz. **Kurtarma modunu** `RECOVER` olarak **ayarlayıp** ardından **kurtarmalı belge yükleme** yaparak, bir Word dosyasının açılmasını engelleyen birçok yaygın sorunu otomatik olarak düzeltebilirsiniz. Programatik olarak **kurtarma ile word açma** ihtiyacınız olsun ya da **bozuk docx** dosyasını manuel olarak açmak isteyin, burada ele aldığımız teknikler size sağlam bir temel sunar.

**Sonraki adımlar:**  

- Deneyin


## Bir Sonraki Öğrenmeniz Gerekenler?


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve ilgili konuları derinlemesine ele alan içeriklerdir. Her kaynak, adım adım açıklamalar ve tam çalışan kod örnekleri içerir; böylece API özelliklerini daha iyi kavrayabilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Recover corrupted docx – Complete Guide to Fix and Process Documents](/words/english/java/document-loading-and-saving/recover-corrupted-docx-complete-guide-to-fix-and-process-doc/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to Merge Multiple DOCX Files Using Aspose.Words for Java](/words/english/java/document-merging/using-document-merging/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}