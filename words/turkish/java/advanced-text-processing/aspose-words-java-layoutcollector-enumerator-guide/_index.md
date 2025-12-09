---
date: '2025-11-13'
description: Aspose.Words for Java LayoutCollector ve LayoutEnumerator'ı kullanarak
  sayfa aralıklarını analiz etmeyi, düzen varlıklarında gezinmeyi, geri aramaları
  (callback) uygulamayı ve sayfa numaralandırmasını verimli bir şekilde yeniden başlatmayı
  öğrenin.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- page span analysis java
- traverse layout entities java
- page layout callbacks java
- restart page numbering java
- document pagination Java
- Aspose.Words layout API
- Java text processing
title: 'Aspose.Words Java: LayoutCollector ve LayoutEnumerator Rehberi'
url: /tr/java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java'da Uzmanlaşma: Metin İşleme için LayoutCollector ve LayoutEnumerator'ı Kapsamlı Rehber

## Giriş

Java uygulamalarınızda karmaşık belge düzenlerini yönetmekte zorluk mu yaşıyorsunuz? Bir bölümün kaç sayfa boyunca uzandığını belirlemek ya da düzen varlıklarını verimli bir şekilde dolaşmak gibi görevler göz korkutucu olabilir. **Aspose.Words for Java** ile `LayoutCollector` ve `LayoutEnumerator` gibi güçlü araçlara erişerek bu süreçleri basitleştirebilir, olağanüstü içerik sunmaya odaklanabilirsiniz. Bu kapsamlı rehberde, belge işleme yeteneklerinizi artırmak için bu özellikleri nasıl kullanacağınızı keşfedeceğiz.

**Öğrenecekleriniz:**
- Aspose.Words'ün `LayoutCollector`ını kesin sayfa kapsamı analizi için kullanma.
- `LayoutEnumerator` ile belgeleri verimli bir şekilde dolaşma.
- Dinamik render ve güncellemeler için layout geri aramalarını uygulama.
- Sürekli bölümlerde sayfa numaralandırmasını etkili bir şekilde kontrol etme.

Bu araçların belge işleme süreçlerinizi nasıl dönüştürebileceğine dalalım. Başlamadan önce, aşağıdaki önkoşullar bölümünü kontrol ettiğinizden emin olun.

## Önkoşullar

Bu rehberi takip edebilmek için aşağıdakilere sahip olduğunuzdan emin olun:

### Gerekli Kütüphaneler ve Sürümler
Aspose.Words for Java sürüm 25.3'ün kurulu olduğundan emin olun.

**Maven:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Ortam Kurulum Gereksinimleri
Şunlara ihtiyacınız olacak:
- Makinenizde yüklü Java Development Kit (JDK).
- Kodu çalıştırmak ve test etmek için IntelliJ IDEA veya Eclipse gibi bir IDE.

### Bilgi Önkoşulları
Java programlamaya temel bir anlayış, konuları etkili bir şekilde takip edebilmeniz için önerilir.

## Aspose.Words'ü Kurma
İlk olarak, Aspose.Words kütüphanesini projenize entegre ettiğinizden emin olun. Ücretsiz deneme lisansını [buradan](https://releases.aspose.com/words/java/) alabilir veya gerekirse geçici bir lisans tercih edebilirsiniz. Aspose.Words'ü Java'da kullanmaya başlamak için aşağıdaki gibi başlatın:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Set up the license (if available)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

Kurulumunuz tamamlandığında, `LayoutCollector` ve `LayoutEnumerator`'ın temel özelliklerine dalalım.

## Uygulama Kılavuzu

### Özellik 1: Sayfa Kapsamı Analizi için LayoutCollector Kullanımı
`LayoutCollector` özelliği, bir belgedeki düğümlerin sayfalar arasında nasıl yayıldığını belirlemenizi sağlar ve sayfalama analizine yardımcı olur.

#### Genel Bakış
`LayoutCollector`ı kullanarak herhangi bir düğümün başlangıç ve bitiş sayfa indekslerini ve toplam kaç sayfa kapsadığını öğrenebiliriz.

#### Uygulama Adımları

**1. Document ve LayoutCollector'ı Başlatma**
```java
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

**2. Belgeyi Doldurma**
Burada, birden fazla sayfaya yayılan içerik ekleyeceğiz:
```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

**3. Düzeni Güncelleme ve Metriği Almak**
```java
layoutCollector.clear();
doc.updatePageLayout();

assert layoutCollector.getNumPagesSpanned(doc) == 5;
```

#### Açıklama
- **`DocumentBuilder`:** Belgeye içerik eklemek için kullanılır.
- **`updatePageLayout()`:** Sayfa metriklerinin doğru olmasını sağlar.

### Özellik 2: LayoutEnumerator ile Dolaşma
`LayoutEnumerator`, bir belgenin düzen varlıklarını verimli bir şekilde dolaşmanızı sağlar ve her öğenin özellikleri ve konumu hakkında ayrıntılı bilgiler sunar.

#### Genel Bakış
Bu özellik, render ve düzenleme görevleri için faydalı olan düzen yapısını görsel olarak gezmenize yardımcı olur.

#### Uygulama Adımları

**1. Document ve LayoutEnumerator'ı Başlatma**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

**2. İleri ve Geri Dolaşma**
Belge düzenini dolaşmak için:
```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Traverse forward
traverseLayoutForward(layoutEnumerator, 1);

// Traverse backward
traverseLayoutBackward(layoutEnumerator, 1);
```

#### Açıklama
- **`moveParent()`:** Üst varlıklara geçiş yapar.
- **Dolaşma Yöntemleri:** Kapsamlı gezinme için özyinelemeli olarak uygulanmıştır.

### Özellik 3: Sayfa Düzeni Geri Aramaları
Bu özellik, belge işleme sırasında sayfa düzeni olaylarını izlemek için geri aramaları nasıl uygulayacağınızı gösterir.

#### Genel Bakış
`IPageLayoutCallback` arayüzünü kullanarak bir bölüm yeniden akışa girdiğinde veya dönüşüm tamamlandığında gibi belirli düzen değişikliklerine yanıt verebilirsiniz.

#### Uygulama Adımları

**1. Geri Aramayı Ayarlama**
```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();
```

**2. Geri Arama Yöntemlerini Uygulama**
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

        try (FileOutputStream stream = new FileOutputStream("YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }
}
```

#### Açıklama
- **`notify()`:** Düzen olaylarını işler.
- **`ImageSaveOptions`:** Render seçeneklerini yapılandırır.

### Özellik 4: Sürekli Bölümlerde Sayfa Numaralandırmasını Yeniden Başlatma
Bu özellik, sürekli bölümlerde sayfa numaralandırmasını kontrol ederek belgelerin sorunsuz akışını sağlar.

#### Genel Bakış
`ContinuousSectionRestart` kullanarak çok bölümlü belgelerde sayfa numaralarını etkili bir şekilde yönetebilirsiniz.

#### Uygulama Adımları

**1. Belgeyi Yükleme**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

**2. Sayfa Numaralandırma Seçeneklerini Yapılandırma**
```java
doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();
```

#### Açıklama
- **`setContinuousSectionPageNumberingRestart()`:** Sürekli bölümlerde sayfa numaralarının nasıl yeniden başlayacağını yapılandırır.

## Pratik Uygulamalar
Bu özelliklerin uygulanabileceği bazı gerçek dünya senaryoları:
1. **Belge Sayfalama Analizi:** `LayoutCollector`ı kullanarak içerik düzenini analiz edin ve optimal sayfalama için ayarlayın.
2. **PDF Renderlama:** `LayoutEnumerator`ı kullanarak PDF'leri doğru bir şekilde gezip renderlayın, görsel yapıyı koruyun.
3. **Dinamik Belge Güncellemeleri:** Belirli düzen değişikliklerinde eylemler tetiklemek için geri aramaları uygulayın, gerçek zamanlı belge işleme yeteneğini artırın.
4. **Çok Bölümlü Belgeler:** Raporlar veya kitaplar gibi belgelerde sürekli bölümlerde sayfa numaralandırmasını kontrol ederek profesyonel bir formatlama elde edin.

## Performans Düşünceleri
Optimal performans sağlamak için:
- Düzen analizinden önce gereksiz öğeleri kaldırarak belge boyutunu küçültün.
- İşlem süresini azaltmak için verimli dolaşma yöntemlerini kullanın.
- Özellikle büyük belgelerle çalışırken kaynak kullanımını izleyin.

## Sonuç
`LayoutCollector` ve `LayoutEnumerator`ı ustalıkla kullanarak Aspose.Words for Java'da güçlü yeteneklerin kilidini açtınız. Bu araçlar, karmaşık belge düzenlerini basitleştirmenin yanı sıra metni etkili bir şekilde yönetme ve işleme yeteneğinizi de artırır. Bu bilgiyle donanmış olarak, karşılaşacağınız her ileri düzey metin işleme zorluğunun üstesinden gelmeye hazırsınız.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}