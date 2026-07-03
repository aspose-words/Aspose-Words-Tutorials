---
category: general
date: 2026-07-03
description: Kurtarma modunu ayarlayarak Java’da bozuk Word dosyalarını kurtarın ve
  yükleme sonrası sayfa sayısını gösterin. Aspose.Words ile adım adım öğrenin.
draft: false
keywords:
- set recovery mode
- display page count
- recover corrupted word
- Aspose.Words Java
- document loading options
language: tr
og_description: Aspose.Words for Java'da kurtarma modunu ayarlayarak bozuk Word dosyalarını
  onarın ve sayfa sayısını görüntüleyin. Şimdi tam örneği inceleyin.
og_title: Aspose.Words for Java'da Kurtarma Modunu Ayarlama – Tam Kılavuz
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  headline: Set Recovery Mode in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  name: Set Recovery Mode in Aspose.Words for Java – Full Guide
  steps:
  - name: Why `RecoveryMode.PARSE`?
    text: '- **PARSE** – Aspose.Words parses whatever fragments it can understand,
      stitching together a partially functional document. Ideal when you need *any*
      content out of a broken file. - **SKIP** – The library skips over corrupted
      sections entirely, which can be faster but may discard more data.'
  - name: 1️⃣ Corrupted Header/Footer Sections
    text: Sometimes only the main body parses while headers and footers are lost.
      If you rely on those for branding, you may need to re‑inject them after recovery.
  - name: 2️⃣ Images That Won’t Load
    text: Embedded images often get stripped out when the zip container (the underlying
      `.docx` format) is damaged. You can catch this by iterating over `doc.getSections()`
      and checking `Section.getBody().getParagraphs()` for `Shape` objects.
  - name: 3️⃣ Large Documents and Memory
    text: Recovering a 200‑page corrupted file can be memory‑intensive. Consider increasing
      the JVM heap size (`-Xmx2g`) when you anticipate huge documents.
  - name: 4️⃣ License Restrictions
    text: The evaluation version caps certain features, but **recovery** is fully
      functional. However, the printed page count may be limited to a few pages in
      the trial. Always test with a licensed build for production.
  - name: Maven `pom.xml` snippet
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> </dependency> ```'
  - name: Java source file `RecoveryModeDemo.java`
    text: '```java import com.aspose.words.*;'
  type: HowTo
- questions:
  - answer: That usually means the file is beyond salvage—perhaps the zip container
      is completely broken. In such cases, you might need a third‑party repair tool
      before handing it to Aspose.Words.
    question: What if `RecoveryMode.PARSE` still throws an exception?
  - answer: 'Absolutely. Implement `IWarningCallback` to capture any warnings Aspose.Words
      emits during the parsing process. This gives you insight into which parts were
      skipped. ```java loadOptions.setWarningCallback(new IWarningCallback() { public
      void warning(WarningInfo info) { System.out.println("Warning: "'
    question: Can I combine `RecoveryMode.PARSE` with custom document loading callbacks?
  - answer: 'No. Aspose.Words works on a copy in memory; the source file remains untouched
      unless you explicitly call `doc.save()`. --- ## ## Wrap‑Up We’ve covered how
      to **set recovery mode** in Aspose.Words for Java, why `PARSE` is generally
      the best choice for salvaging a broken document, and how to **display'
    question: Does changing the recovery mode affect the original file?
  type: FAQPage
tags:
- Java
- Aspose.Words
- Word recovery
title: Aspose.Words for Java'da Kurtarma Modunu Ayarlama – Tam Kılavuz
url: /tr/java/document-loading-and-saving/set-recovery-mode-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java’da Kurtarma Modunu Ayarlama – Tam Kılavuz

Hiç **kurtarma modunu** Aspose.Words ile bozuk bir `.docx` dosyası yüklerken nasıl ayarlayacağınızı merak ettiniz mi? Açılmayan bozuk Word belgeleriyle yalnız değilsiniz. Bu öğreticide tam olarak bunu—kütüphaneyi **bozuk Word** dosyalarını kurtaracak şekilde nasıl yapılandıracağınızı ve ardından **başarıyla yüklü içeriğin sayfa sayısını** nasıl görüntüleyeceğinizi adım adım göstereceğiz.

Küçük bir `LoadOptions` ayarından, kurtarma görevini tamamlayan `System.out.println` satırına kadar her şeyi ele alacağız. Süslü bir giriş yok, sadece en yeni Aspose.Words 23.12 sürümüyle çalışan, kopyala‑yapıştır hazır bir çözüm.

## Öğrenecekleriniz

- Kurtarma modunun neden önemli olduğu ve Aspose.Words’ün sunduğu seçenekler.  
- Java kullanarak **kurtarma modunu** programlı olarak nasıl **ayarlayacağınız**.  
- Belge yüklendikten sonra **sayfa sayısını** nasıl **gösterileceği**, kurtarmanın başarılı olduğunu doğrulamak için.  
- Bozuk Word dosyalarıyla çalışırken sıkça karşılaşılan tuzaklar ve bunlardan nasıl kaçınılacağı.  

Başlamadan önce şunlara sahip olduğunuzdan emin olun:

1. Geçerli bir Aspose.Words for Java lisansı (veya geçici bir değerlendirme anahtarı).  
2. Makinenizde yüklü Java 17 veya daha yeni bir sürüm.  
3. Test etmek istediğiniz bozuk `Corrupted.docx` dosyası.  

Hepsi hazır mı? Harika—haydi işe koyulalım.

> **Pro ipucu:** Deneme sürümü kullanıyorsanız bile, kurtarma özellikleri lisanslı bir yapıda olduğu gibi aynı şekilde çalışır.

---

## ## Aspose.Words for Java ile Kurtarma Modunu Ayarlama

Çözümün kalbi `LoadOptions` sınıfında yer alır. Varsayılan olarak Aspose.Words bir belgeyi yüklemeye çalışır, ancak dosya ciddi şekilde bozulmuşsa ona *nasıl* davranması gerektiğini söylemeniz gerekir. İşte **kurtarma modunu ayarlama** burada devreye girer.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a LoadOptions instance – this object holds all the loading preferences.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose the recovery mode. PARSE attempts to salvage as much as possible,
        //    while SKIP simply skips unreadable parts.
        loadOptions.setRecoveryMode(RecoveryMode.PARSE);

        // 3️⃣ Load the document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 4️⃣ Finally, display the number of pages that were successfully recovered.
        System.out.println("Document loaded, page count = " + doc.getPageCount());
    }
}
```

### Neden `RecoveryMode.PARSE`?

- **PARSE** – Aspose.Words anlayabildiği parçaları ayrıştırır, kısmen işlevsel bir belge oluşturur. Bozuk bir dosyadan *herhangi* bir içerik elde etmeniz gerektiğinde idealdir.  
- **SKIP** – Kütüphane bozuk bölümleri tamamen atlar, bu daha hızlı olabilir ancak daha fazla veri kaybına yol açabilir.  

Çoğu gerçek dünya senaryosunda, **PARSE** daha güvenli bir seçimdir çünkü kurtarılabilir metin, resim ve biçimlendirme miktarını maksimize eder.

---

## ## Kurtarma Sonrası Sayfa Sayısını Görüntüleme

Belge yüklendikten sonra bir sonraki mantıklı adım, işlemin başarısını doğrulamaktır. En basit ama en bilgilendirici metrik sayfa sayısıdır. `Document.getPageCount()` metodu tam da bunu yapar.

```java
int pages = doc.getPageCount();
System.out.println("Document loaded, page count = " + pages);
```

Dosya tamamen okunamaz durumdaysa, Aspose.Words bu satıra ulaşmadan önce bir istisna fırlatır. Sayfa sayısı `0` ya da çok düşük bir sayı gösteriyorsa, genellikle kurtarma modunun dosyanın büyük bölümlerini atmak zorunda kaldığı anlamına gelir.

**Beklenen çıktı (örnek):**

```
Document loaded, page count = 12
```

Bu, kütüphanenin bozuk kaynaktan on iki sayfa yeniden oluşturabildiğini gösterir—bozuk bir `.docx` için oldukça sağlam bir sonuç.

---

## ## Kenar Durumları ve Yaygın Tuzaklar

### 1️⃣ Bozuk Üstbilgi/Altbilgi Bölümleri
Bazen yalnızca ana gövde ayrıştırılır, üstbilgi ve altbilgiler kaybolur. Eğer bunlar marka kimliğiniz için kritikse, kurtarmadan sonra yeniden eklemeniz gerekebilir.

### 2️⃣ Yüklenemeyen Görseller
Gömülü görseller, zip konteyneri (altındaki `.docx` formatı) hasar gördüğünde genellikle silinir. Bunu `doc.getSections()` üzerinden döngü kurup `Section.getBody().getParagraphs()` içinde `Shape` nesnelerini kontrol ederek yakalayabilirsiniz.

```java
for (Section sec : doc.getSections()) {
    for (Paragraph para : sec.getBody().getParagraphs()) {
        for (Node node : para.getChildNodes(NodeType.SHAPE, true)) {
            Shape shape = (Shape) node;
            System.out.println("Found image: " + shape.getName());
        }
    }
}
```

Döngü hiçbir şey yazdırmazsa, kurtarma modunun görselleri atmış olma ihtimali yüksektir.

### 3️⃣ Büyük Belgeler ve Bellek
200 sayfalık bozuk bir dosyayı kurtarmak bellek yoğun olabilir. Büyük belgeler bekliyorsanız JVM yığın boyutunu (`-Xmx2g`) artırmayı düşünün.

### 4️⃣ Lisans Kısıtlamaları
Değerlendirme sürümü bazı özellikleri sınırlar, ancak **kurtarma** tamamen işlevseldir. Ancak, deneme sürümünde yazdırılan sayfa sayısı birkaç sayfayla sınırlı olabilir. Üretim ortamı için her zaman lisanslı bir yapı ile test edin.

---

## ## Tam Uç‑Uç Örnek (Çalıştırılabilir)

Aşağıda, herhangi bir Maven ya da Gradle projesine ekleyebileceğiniz, bağımsız bir program yer alıyor. Aspose.Words 23.12 için gerekli bağımlılık bildirimi de dahildir.

### Maven `pom.xml` snippet’i

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Java kaynak dosyası `RecoveryModeDemo.java`

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) {
        try {
            // Initialize load options
            LoadOptions loadOptions = new LoadOptions();

            // Set recovery mode to PARSE – this is the key step to recover corrupted Word files.
            loadOptions.setRecoveryMode(RecoveryMode.PARSE);

            // Load the possibly damaged document
            Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

            // Display the page count to confirm how much content was recovered.
            System.out.println("Document loaded, page count = " + doc.getPageCount());

            // (Optional) Save the recovered document for further inspection.
            doc.save("YOUR_DIRECTORY/Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Ne yapıyor:**

1. **Kurtarma modunu ayarlıyor** – öğretimizin çekirdeği.  
2. Yapılandırılmış `LoadOptions` ile bozuk dosyayı yüklüyor.  
3. **Sayfa sayısını gösteriyor**, anında geri bildirim sağlıyor.  
4. Temizlenmiş bir sürüm (`Recovered.docx`) kaydediyor, böylece daha sonra Word’de açabilirsiniz.

Programı şu şekilde çalıştırın:

```bash
javac -cp "path/to/aspose-words-23.12.jar" RecoveryModeDemo.java
java -cp ".:path/to/aspose-words-23.12.jar" RecoveryModeDemo
```

Konsolda sayfa sayısının yazdırıldığını görmelisiniz; bu, kurtarmanın başarılı olduğunu doğrular.

---

## ## Görsel Genel Bakış (Resim)

![kurtarma modunu ayarlama akış diyagramı](https://example.com/images/recovery-mode-flow.png "Aspose.Words for Java’da kurtarma modunun nasıl çalıştığını gösteren diyagram")

*Alt metin, SEO uyumu için temel anahtar kelime **kurtarma modunu ayarlama** içerir.*

---

## ## Sıkça Sorulan Sorular

**S: `RecoveryMode.PARSE` hâlâ bir istisna fırlatıyorsa ne yapmalıyım?**  
C: Bu genellikle dosyanın kurtarılamayacak kadar hasarlı olduğu anlamına gelir—belki zip konteyneri tamamen bozulmuştur. Böyle durumlarda, Aspose.Words’e vermeden önce üçüncü‑taraf bir onarım aracı kullanmanız gerekebilir.

**S: `RecoveryMode.PARSE`ı özel belge yükleme geri çağırmalarıyla birleştirebilir miyim?**  
C: Kesinlikle. `IWarningCallback` uygulayarak Aspose.Words’ün ayrıştırma sırasında ürettiği uyarıları yakalayabilirsiniz. Bu, atlanan bölümler hakkında size bilgi verir.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    public void warning(WarningInfo info) {
        System.out.println("Warning: " + info.getDescription());
    }
});
```

**S: Kurtarma modunu değiştirmek orijinal dosyayı etkiler mi?**  
C: Hayır. Aspose.Words bellekte bir kopya üzerinde çalışır; kaynak dosya, `doc.save()` çağırmadığınız sürece dokunulmaz kalır.

---

## ## Özet

Aspose.Words for Java’da **kurtarma modunu** nasıl **ayarlayacağınızı**, bozuk bir belgeyi kurtarmak için genellikle `PARSE` seçeneğinin neden en iyi tercih olduğunu ve **sayfa sayısını** nasıl **göstererek** sonucun doğrulanacağını ele aldık. Tam örneği izleyerek, **bozuk Word** dosyalarını **kurtarabilecek** ve işlemin başarısını anında raporlayabilecek hazır bir çözüm elde ettiniz.

Sonraki adımlar? `RecoveryMode.SKIP`’i deneyerek farkı gözlemleyin, büyük çok‑bölümlü dosyalarla oynayın veya kullanıcı‑yüklemeli belgeleri otomatik olarak onaran bir web servisine bu mantığı entegre edin. Aynı desen PDF’ler (Aspose.PDF kullanarak) ve hatta düz metin kurtarma için diğer kütüphanelerle de çalışır—temel fikir: yükleyiciyi yapılandır, kurtarmayı dene, ardından sayfa sayısı gibi basit bir metrikle doğrula.

Keyifli kodlamalar, belgeleriniz sağlam kalsın!

## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalar ve tam çalışan kod örnekleri içerir, böylece ek API özelliklerini ustalaşabilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Aspose.Words for Java’da LoadOptions Nasıl Ayarlanır](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words Java: Word Belge İşleme İçin Kapsamlı Rehber](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Aspose.Words for Java ile Birden Çok Word Dosyasını Birleştirme](/words/english/java/document-manipulation/cloning-and-combining-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}