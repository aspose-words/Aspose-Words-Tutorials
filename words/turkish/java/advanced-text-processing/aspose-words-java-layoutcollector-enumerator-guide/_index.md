---
date: '2025-11-12'
description: Aspose.Words for Java'nın LayoutCollector ve LayoutEnumerator'ını kullanarak
  sayfalama analizini öğrenin, belge düzeninde gezin, düzen geri aramaları uygulayın
  ve sürekli bölümlerde sayfa numaralandırmayı yeniden başlatın.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: tr
title: Aspose.Words Düzen Araçlarıyla Java Sayfalama Analizi
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java Sayfalama Analizi Aspose.Words Layout Araçlarıyla

## Introduction  

Eğer bir Java uygulamasında **sayfalama analizine** veya **belgenin düzenine gezinmeye** ihtiyacınız varsa, Aspose.Words for Java size iki güçlü API sunar: **`LayoutCollector`** ve **`LayoutEnumerator`**. Bu sınıflar, bir düğümün kaç sayfa kapladığını keşfetmenizi, her düzen öğesini gezmenizi, düzen olaylarına yanıt vermenizi ve hatta sürekli bölümlerde sayfa numaralandırmasını yeniden başlatmanızı sağlar. Bu rehberde her özelliği adım adım inceleyecek, gerçek dünya kod parçacıklarını gösterecek ve beklenen sonuçları açıklayacağız, böylece hemen uygulamaya koyabilirsiniz.

Öğrenecekleriniz:

* **LayoutCollector** kullanarak herhangi bir düğümün başlangıç ve bitiş sayfasını elde etme (layoutcollector page span)  
* **LayoutEnumerator** ile belge düzeninde gezinme (traverse document layout)  
* Sayfalama olaylarına yanıt vermek için **layout callback** uygulama (implement layout callback)  
* Sürekli bölümlerde sayfa numaralandırmasını yeniden başlatma (restart page numbering sections)  

Haydi başlayalım.

## Prerequisites  

### Required Libraries  

| Build Tool | Dependency |
|------------|------------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **Note:** Versiyon numarası uyumluluk için korunmuştur; kod, Aspose.Words for Java’nın herhangi bir yeni sürümüyle çalışır.

### Environment  

* JDK 8 veya daha yeni bir sürüm  
* IntelliJ IDEA veya Eclipse gibi bir IDE  

### Knowledge  

Temel Java programlama bilgisi ve Maven/Gradle’a aşinalık örnekleri takip etmek için yeterlidir.

## Setting Up Aspose.Words  

Herhangi bir layout API’sini çağırmadan önce kütüphane lisanslanmalı (veya deneme modunda kullanılmalıdır). Aşağıdaki kod parçacığı minimum başlatmayı gösterir:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*Kod herhangi bir belgeyi değiştirmez; yalnızca Aspose ortamını hazırlar.*  

Şimdi temel özelliklere dalalım.

## Feature 1: Using **LayoutCollector** to Analyze Pagination  

`LayoutCollector`, bir `Document` içindeki her düğümü kapladığı sayfalara eşler. Bu, **layoutcollector page span** kullanarak sayfalama analizi yapmanın en güvenilir yoludur.

### Step‑by‑step implementation  

1. **Yeni bir belge oluşturun ve bir LayoutCollector ekleyin.**  
2. **Sayfalama zorlayan içerik ekleyin** (ör. sayfa sonları, bölüm sonları).  
3. **`updatePageLayout()`** ile düzeni yenileyin.  
4. **Toplayıcıyı sorgulayarak** başlangıç sayfası, bitiş sayfası ve toplam sayfa aralığını alın.

#### 1️⃣ Initialize Document and LayoutCollector  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ Populate the Document  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ Update Layout and Retrieve Metrics  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Expected output**

```
Document spans 5 pages.
```

> **Why it works:** `updatePageLayout()` Aspose.Words’ın düzeni yeniden hesaplamasını zorlar; ardından `LayoutCollector` sayfa aralıklarını doğru bir şekilde raporlayabilir.

## Feature 2: Traversing Document Layout with **LayoutEnumerator**  

Özel renderleme veya analiz için **belge düzeninde gezinmeye** (traverse document layout) ihtiyaç duyduğunuzda, `LayoutEnumerator` sayfalar, paragraflar, satırlar ve kelimeler için ağaç benzeri bir görünüm sunar.

### Step‑by‑step implementation  

1. Düzen öğeleri içeren mevcut bir belgeyi yükleyin.  
2. Bir `LayoutEnumerator` örneği oluşturun.  
3. Kök `PAGE` öğesine geçin.  
4. Yardımcı metodları kullanarak düzeni ileri ve geri yürütün.

#### 1️⃣ Load Document and Create Enumerator  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

#### 2️⃣ Position on the Page Level  

```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);
```

#### 3️⃣ Forward Traversal (Depth‑First)  

```java
traverseLayoutForward(layoutEnumerator, 1);
```

#### 4️⃣ Backward Traversal  

```java
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Helper methods** (`traverseLayoutForward` / `traverseLayoutBackward`) her alt öğeyi ziyaret etmek ve türü ile sayfa indeksini yazdırmak için özyinelemeli olarak uygulanmıştır. İstatistik toplamak, grafik çizmek veya düzen özelliklerini değiştirmek için uyarlayabilirsiniz.

## Feature 3: Implementing **Layout Callbacks**  

Bazen Aspose.Words belgenin bir kısmını yerleştirmeyi tamamladığında bir işlem yapmak istersiniz. `IPageLayoutCallback` uygulamak, **layout callback** (implement layout callback) mantığını, örneğin her sayfayı bir resim olarak kaydetme gibi, gerçekleştirmenizi sağlar.

### Step‑by‑step implementation  

1. Belgenin `LayoutOptions`ına bir callback örneği atayın.  
2. Callback içinde `PART_REFLOW_FINISHED` ve `CONVERSION_FINISHED` olaylarını işleyin.  
3. `ImageSaveOptions` kullanarak mevcut sayfayı PNG’ye render edin.

#### 1️⃣ Register the Callback  

```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();                     // Triggers the callback events
```

#### 2️⃣ Callback Class  

```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }

    // You can add custom logic here for partFinished / conversionFinished
}
```

**What happens:** Her bir düzen parçası yeniden akışını tamamladığında, callback o sayfayı bir PNG dosyasına render eder ve sayfalama sürecinin görsel bir izini sunar.

## Feature 4: Restarting Page Numbering in **Continuous Sections**  

Belge sürekli bölümler içeriyorsa, sayfa numaralarının yalnızca yeni bir fiziksel sayfa başladığında yeniden başlamasını isteyebilirsiniz. Bu, `ContinuousSectionRestart` ayarıyla sağlanır.

### Step‑by‑step implementation  

1. Hedef belgeyi yükleyin.  
2. `ContinuousSectionPageNumberingRestart` seçeneğini değiştirin.  
3. Değişikliği uygulamak için `updatePageLayout()` tekrar çalıştırın.

#### 1️⃣ Load Document  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

#### 2️⃣ Configure Restart Behavior  

```java
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();            // Apply the new numbering rule
```

**Result:** Sayfa numaraları artık yeni bir fiziksel sayfa başladığında yeniden başlayacak, raporlar veya kitaplar için temiz ve profesyonel bir görünüm sağlayacaktır.

## Practical Applications  

| Scenario | Which API Helps | Benefit |
|----------|----------------|---------|
| **Uzun sözleşmeleri denetleme** | `LayoutCollector` | Hangi maddelerin birden fazla sayfaya yayıldığını hızlıca bulur. |
| **Özel PDF renderleme** | `LayoutEnumerator` | Düzen ağacını gezerek her satırı vektör grafik olarak dışa aktarır. |
| **Canlı belge önizlemesi** | Layout callbacks | Kullanıcı içerik eklerken sayfa görüntülerini anında üretir. |
| **Çok bölümlü raporlar** | Continuous section restart | Sayfa numaralarını manuel ayarlamaya gerek kalmadan mantıklı tutar. |

## Performance Tips  

* **`updatePageLayout()`** çağırmadan önce kullanılmayan düğümleri temizleyin – daha az öğe, daha hızlı sayfalama demektir.  
* **Bir LayoutCollector** örneğini birden fazla sorgu için yeniden kullanın, her seferinde yeniden oluşturmayın.  
* **LayoutEnumerator** kullanırken yalnızca sayfa düzeyindeki verilere ihtiyacınız varsa gezinme derinliğini sınırlayın.  
* **Akışları serbest bırakın** (callback örneğinde gösterildiği gibi) büyük belgelerde bellek sızıntılarını önlemek için.

## Conclusion  

`LayoutCollector`, `LayoutEnumerator`, layout callback’leri ve sürekli‑bölüm numaralandırma özelliklerini ustalıkla kullanarak **analyze pagination java**, **traverse document layout** ve **restart page numbering sections** konularında tam bir araç setine sahip oldunuz. Bu API’ler, profesyonel sonuçlar veren sağlam, yüksek performanslı metin işleme hatları oluşturmanıza olanak tanır.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}