---
date: '2026-01-14'
description: Aspose.Words Java ile sayfa numaralandırmayı nasıl yeniden başlatacağınızı
  öğrenin ve LayoutCollector'ı kullanarak sayfalama verilerini çıkarın, sayfa düzenini
  güncelleyin ve sayfaları resim olarak render edin.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
title: Aspose.Words Java ile Sayfa Numaralandırmayı Yeniden Başlatma – LayoutCollector
  ve LayoutEnumerator
url: /tr/java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java ile Sayfa Numaralandırmayı Yeniden Başlatma – LayoutCollector & LayoutEnumerator

## Giriş

Büyük Java tabanlı belgelerde **sayfa numaralandırmayı yeniden başlatma** konusunda zorlanıyor ve aynı zamanda sayfalama analizine ya da sayfaları resim olarak render etmeye mi ihtiyacınız var? **Aspose.Words for Java** ile `LayoutCollector` ve `LayoutEnumerator`ı kullanarak sadece sayfa numaralandırmayı yeniden başlatmakla kalmaz, aynı zamanda **sayfalama verilerini çıkartabilir**, **sayfa düzenini güncelleyebilir** ve **ön izlemeler veya PDF'ler için sayfaları resim olarak render** edebilirsiniz. Bu kılavuz, kütüphaneyi kurmaktan belge render'ını tam kontrol eden geri aramaları (callback) uygulamaya kadar her adımı size gösterir.

**Öğrenecekleriniz**
- `LayoutCollector`ı kullanarak sayfalama verilerini çıkartma ve sayfa aralıklarını belirleme.
- `LayoutEnumerator` ile belge düzeninde gezinme.
- Sayfa‑düzeni geri aramaları (callback) uygulayarak **sayfaları resim olarak render** etme.
- Sürekli bölümlerde **sayfa numaralandırmayı yeniden başlatma** düzen seçenekleriyle.
- **Sayfa düzenini** verimli bir şekilde güncelleme ipuçları.

## Hızlı Yanıtlar
- **Java belgesinde sayfa numaralandırmayı nasıl yeniden başlatırım?** `doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(...)` kullanın ve `doc.updatePageLayout()` çağırın.
- **Hangi sınıf sayfalama verilerini çıkarır?** `LayoutCollector` herhangi bir düğüm için başlangıç/bitiş sayfa indekslerini sağlar.
- **Her sayfayı resim olarak render edebilir miyim?** Evet—`IPageLayoutCallback` uygulayın ve `ImageSaveOptions` kullanın.
- **Sayfa düzenini manuel olarak güncellemem gerekiyor mu?** Düzen seçeneklerini değiştirdikten sonra her zaman `doc.updatePageLayout()` çağırın.
- **Hangi Aspose.Words sürümü gereklidir?** Örnekler Aspose.Words for Java 25.3 (veya daha yenisi) ile çalışır.

## Sayfa Numaralandırmayı Yeniden Başlatma nedir?

Sayfa numaralandırmayı yeniden başlatma, belgenin belirli bir bölümünde yeni bir numaralandırma dizisine başlamanızı sağlar; bu, bölümler, ekler veya sözleşmeler gibi ayrı numaralandırma gerektiren raporlar, kitaplar veya sözleşmeler için kritiktir. Aspose.Words, bu davranışı manuel sayfa‑kırılım hilelerine ihtiyaç duymadan kontrol etmenizi sağlayan bir düzen seçeneği sunar.

## Neden LayoutCollector ve LayoutEnumerator kullanmalı?

- **LayoutCollector** sayfalama ayrıntılarına programatik erişim sağlar, **sayfalama verilerini çıkartma** gibi işlemleri (herhangi bir düğümün ilk ve son sayfası) mümkün kılar.
- **LayoutEnumerator** görsel düzen ağacında gezinmenizi sağlar, sayfaları, paragrafları veya satırları özel render veya analiz için kolayca bulmanızı mümkün kılar.
- Birlikte, pahalı PDF dönüşümleri veya manuel hesaplamalar gerektiren karmaşık düzen görevlerini basitleştirir.

## Ön Koşullar

### Gerekli Kütüphaneler ve Sürümler
Aspose.Words for Java sürüm 25.3 (veya daha yenisi) yüklü olduğundan emin olun.

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
- Java Development Kit (JDK) yüklü.
- IntelliJ IDEA, Eclipse veya tercih ettiğiniz herhangi bir Java IDE.
- Geçerli bir Aspose.Words lisansı (değerlendirme için ücretsiz deneme yeterli).

### Bilgi Ön Koşulları
Temel Java programlama bilgisi yeterlidir.

## Aspose.Words Kurulumu
İlk olarak, Aspose.Words kütüphanesini projenize entegre edin. Ücretsiz deneme lisansını [buradan](https://releases.aspose.com/words/java/) alabilir veya test için geçici bir lisans kullanabilirsiniz.

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

Kütüphane hazır olduğunda, temel özelliklere dalabiliriz.

## Uygulama Kılavuzu

### Özellik 1: Sayfa Aralığı Analizi için LayoutCollector Kullanımı
`LayoutCollector` özelliği, düğümlerin sayfalar arasında nasıl yayıldığını belirlemenizi sağlar; bu, **sayfalama verilerini çıkartma** için temel oluşturur.

#### Genel Bakış
`LayoutCollector`ı kullanarak herhangi bir düğümün başlangıç ve bitiş sayfa indekslerini alabilir ve toplam sayfa sayısını hesaplayabilirsiniz.

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
- **`DocumentBuilder`** metin ve sayfa/bölüm kırılımları ekler.
- **`updatePageLayout()`** sayfalama verilerinin doğru olması için düzen bilgilerini yeniden hesaplar.

### Özellik 2: LayoutEnumerator ile Gezinme
`LayoutEnumerator`, görsel düzen ağacında verimli bir şekilde gezinmenizi sağlar.

#### Genel Bakış
Sayfalar, paragraflar, satırlar ve diğer düzen varlıkları arasında dolaşabilirsiniz; bu, özel render veya tanılamalar için faydalıdır.

#### Uygulama Adımları

**1. Document ve LayoutEnumerator'ı Başlatma**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

**2. İleri ve Geri Yönlü Gezinme**
```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Traverse forward
traverseLayoutForward(layoutEnumerator, 1);

// Traverse backward
traverseLayoutBackward(layoutEnumerator, 1);
```

#### Açıklama
- **`moveParent()`** enumerator'ı üst varlığa (bu örnekte sayfa seviyesine) taşır.
- Rekürsif gezinme yöntemleri tüm düzen hiyerarşisini keşfetmenizi sağlar.

### Özellik 3: Sayfa Düzeni Geri Aramaları (Callbacks)
Düzen olaylarını izlemek ve gerektiğinde **sayfaları resim olarak render** etmek için geri aramalar (callback) uygulayın.

#### Genel Bakış
`IPageLayoutCallback` arayüzü, belgenin bir kısmı yeniden akışa (reflow) girdiğinde ya da dönüşüm tamamlandığında sizi bilgilendirir.

#### Uygulama Adımları

**1. Geri Aramayı Ayarlama**
```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();
```

**2. Geri Arama Metodlarını Uygulama**
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
- **`notify()`** düzen olaylarına yanıt verir.
- **`ImageSaveOptions`** ve `PageSet` birlikte **sayfaları resim olarak render** etmenizi (bu örnekte PNG) sağlar.

### Özellik 4: Sürekli Bölümlerde Sayfa Numaralandırmayı Yeniden Başlatma
Birden fazla bölümün sürekli akış içinde olduğu durumlarda sayfa numaralandırmayı kontrol edin.

#### Genel Bakış
`ContinuousSectionRestart` seçeneğini ayarlayarak, sayfa numaralarının yeni bir sayfada mı yoksa kesintisiz devam mı edeceğine karar verebilirsiniz.

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
- **`setContinuousSectionPageNumberingRestart()`** Aspose.Words'a sürekli bölümlerde numaralandırmanın nasıl ele alınacağını söyler.
- Seçeneği değiştirdikten sonra **sayfa düzenini güncelle** değişikliklerin uygulanmasını sağlayın.

## Pratik Uygulamalar
1. **Belge Sayfalama Analizi** – `LayoutCollector`ı kullanarak içeriğin sayfalara nasıl dağıldığını denetleyin ve kenar boşluklarını veya kırılımları buna göre ayarlayın.
2. **PDF Render'ı** – `LayoutEnumerator`ı geri arama ile birleştirerek PDF dönüşümünden önce yüksek doğruluklu sayfa resimleri oluşturun.
3. **Dinamik Belge Güncellemeleri** – (ör. bir tablo genişlediğinde) düzen olaylarına yanıt verin ve etkilenen sayfaları otomatik olarak yeniden render edin.
4. **Çok‑Bölümlü Raporlar** – **sayfa numaralandırmayı yeniden başlat** özelliğini kullanarak her bölümün kendi numaralandırma şemasına sahip olmasını sağlayın, aynı zamanda akıcı bir akış koruyun.

## Performans Düşünceleri
- `updatePageLayout()` çağırmadan önce kullanılmayan bölümleri veya gizli içeriği kaldırarak işleme süresini kısaltın.
- Büyük belgeler için tüm dosyayı belleğe yüklemekten kaçınmak amacıyla akış (streaming) API'lerini kullanın.
- Yalnızca sayfa‑seviyesi bilgiye ihtiyacınız varsa `LayoutEnumerator` içinde rekürsif derinliği sınırlayın.

## Yaygın Sorunlar ve Çözümler
| Sorun | Neden | Çözüm |
|-------|-------|------|
| `layoutCollector.getNumPagesSpanned()` 0 döndürüyor | Düzen güncellenmemiş | Sorgulamadan önce `doc.updatePageLayout()` çağırın |
| Geri aramada resimler üretilmiyor | `ImageSaveOptions` yapılandırması eksik | `saveOptions.setPageSet(new PageSet(pageIndex))` ayarlandığından emin olun |
| Sayfa numaraları yeniden başlamıyor | Yanlış `ContinuousSectionRestart` değeri | Gerçek yeniden başlatma için `ContinuousSectionRestart.FROM_NEW_PAGE_ONLY` kullanın |

## Sık Sorulan Sorular

**S: Belirli bir paragrafın tam sayfa numarasını çıkarabilir miyim?**  
C: Evet—paragraf düğümünün başlangıç sayfasını almak için `LayoutCollector`ı kullanın ve verinin güncel olduğundan emin olmak için `doc.updatePageLayout()` çağırın.

**S: `update page layout` belge içeriğini etkiler mi?**  
C: Hayır. Yalnızca düzen bilgilerini yeniden hesaplar; gerçek metin ve biçimlendirme değişmez.

**S: Büyük bir belgenin tüm sayfalarını verimli bir şekilde resim olarak nasıl render ederim?**  
C: `IPageLayoutCallback`ı uygulayın ve her sayfayı sırayla işleyin; I/O‑ağırlıklı kaydetme için çok‑iş parçacıklı (multi‑threaded) yaklaşımı isteğe bağlı olarak kullanın.

**S: Yalnızca belirli bölümler için numaralandırmayı yeniden başlatmak mümkün mü?**  
C: Evet—`updatePageLayout()` çağırmadan önce ilgili bölümün düzen seçeneklerine `setContinuousSectionPageNumberingRestart` uygulayın.

**S: `LayoutCollector` hangi Aspose.Words sürümünde tanıtıldı?**  
C: `LayoutCollector` 2020'nin başındaki sürümlerde mevcuttu; örnekler sürüm 25.3 ile çalışır.

## Sonuç
**Sayfa numaralandırmayı yeniden başlatma**, `LayoutCollector` ve `LayoutEnumerator`ı ustaca kullanarak Aspose.Words for Java’da gelişmiş metin işleme için güçlü bir araç setine sahip oldunuz. **Sayfalama verilerini çıkartma**, **sayfaları resim olarak render** etme ya da bölümler arasında sayfa numaralandırmayı kontrol etme ihtiyacınız olsun, bu API'ler yüksek performanslı ve programatik kontrol sunar.

---

**Son Güncelleme:** 2026-01-14  
**Test Edilen Sürüm:** Aspose.Words for Java 25.3  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}