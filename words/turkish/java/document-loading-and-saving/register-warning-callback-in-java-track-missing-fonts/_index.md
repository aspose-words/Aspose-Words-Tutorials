---
category: general
date: 2026-05-30
description: Java'da uyarı geri aramasını kaydederek eksik yazı tiplerini izleyin
  ve Aspose.Words ile belge yüklemeyi özelleştirin. Tam adım adım çözümü öğrenin.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: tr
og_description: Java'da eksik fontları izlemek ve belge yüklemeyi özelleştirmek için
  uyarı geri çağrısını kaydedin. Kod ve açıklamalarla tam rehber.
og_title: Java'da uyarı geri çağrısını kaydet – Eksik yazı tiplerini izleyin
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Java'da uyarı geri çağrısını kaydet – Eksik fontları izleyin
url: /tr/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da Uyarı Geri Çağrısını Kaydet – Eksik Yazı Tiplerini İzle

Hiç **eksik yazı tiplerini** Aspose.Words for Java ile bir Word belgesi yüklerken izlemek istediğinizi merak ettiniz mi? Belki sessiz yazı tipi ikamelerini gördünüz ve “Düzenim neye dönüştü?” diye düşündünüz. İyi haber şu ki tahmin etmenize gerek yok. **Uyarı geri çağrısını kaydederek**, belge okunduğu anda her yazı tipi ikameleri olayını yakalayabilir ve **belge yüklemeyi** iş akışınıza uygun şekilde özelleştirebilirsiniz.

Bu öğreticide, geri çağrının nasıl ayarlanacağını, neden önemli olduğunu ve işlem hattınızın geri kalanını nasıl temiz tutacağınızı gösteren gerçek bir örnek üzerinden ilerleyeceğiz. Sonunda, her eksik‑yazı‑tipi uyarısını yazdıran ve işlenmiş bir belge kopyası kaydeden çalıştırılabilir bir Java sınıfına sahip olacaksınız. Harici referanslara gerek yok – sadece saf, çalıştırılabilir kod.

> **Neler elde edeceksiniz:**  
> • Aspose.Words kullanan tam bir Java programı  
> • Her satırın adım‑adım açıklamaları  
> • Şifreli dosyalar veya büyük toplular gibi kenar durumlarını ele alma ipuçları  
> • Herhangi bir `.docx` dosyasında çalıştırabileceğiniz hızlı bir bütünlük kontrolü

## Gereksinimler

İlerlemeye başlamadan önce şunların yüklü olduğundan emin olun:

- **Java 17** (veya herhangi bir güncel JDK) ve `JAVA_HOME` ayarlanmış.  
- **Aspose.Words for Java** JAR dosyası sınıf yolunuzda. En yeni sürümü Maven Central deposundan alabilirsiniz:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- Makinenizde yüklü olmayan yazı tipleri içerdiğini düşündüğünüz bir örnek Word belgesi (`input.docx`).  
- Kullanımına alışkın olduğunuz bir IDE veya komut‑satırı yapı aracı (Maven/Gradle).

Hepsi bu. Ekstra yazı tiplerine, ek hizmetlere gerek yok – sadece saf Java ve Aspose.Words.

## Neden uyarı geri çağrısı kaydedilir?

**Uyarı geri çağrısını**, belge yükleme süreciniz için bir güvenlik kamerası gibi düşünün. Aspose.Words eksik bir glifle karşılaştığında bir istisna fırlatmaz; sessizce bir yedek yazı tipine geçer. Bu sessiz ikame, özellikle marka‑kritik PDF’lerde veya faturalar gibi belgelerde düzeninizi bozabilir. Bir geri çağrı kaydederek:

1. **Gerçek zamanlı içgörü elde edin** – her `FONT_SUBSTITUTION` uyarısı anında iletilir.  
2. **Kaydedin veya tepki verin** – bir dosyaya loglayabilir, bir alarm tetikleyebilir veya hatta programatik olarak yazı tipini değiştirebilirsiniz.  
3. **Temiz çıktı sağlayın** – eksik yazı tiplerini bilmek, belgeyi yayınlamadan önce kaynağını düzeltmenize olanak tanır.

Kısacası, geri çağrı gizli bir sorunu görünür hâle getirir ve belge iş akışınızı çok daha güvenilir kılar.

## Adım 1 – Belge yüklemesini özelleştirmek için `LoadOptions` oluşturun

İlk yaptığımız şey `LoadOptions` nesnesini örneklemek. Bu nesne, şifre yönetiminden **uyarı geri çağrısı kaydetme** özelliğine kadar ihtiyaç duyabileceğiniz tüm yükleme‑zamanı ayarlarının kapısıdır.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

Neden doğrudan `new Document("file.docx")` çağırmıyoruz? Çünkü `LoadOptions` olmadan yükleme olaylarına bağlanma şansını kaybedersiniz. `LoadOptions`, Aspose.Words’in **belge yüklemeyi özelleştirmenize** izin verdiği tek yerdir.

## Adım 2 – Eksik yazı tiplerini izlemek için bir uyarı geri çağrısı kaydedin

Şimdi gösterinin yıldızı geliyor: **uyarı geri çağrısını** kaydediyoruz; bu, `IWarningCallback` arayüzünü uygular. `warning` metodunda `WarningType.FONT_SUBSTITUTION` için filtreleme yapıp yardımcı bir mesaj yazdırıyoruz.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

Dikkat edilmesi gereken birkaç nokta:

- **Neden `IWarningCallback`?** Aspose.Words tüm uyarı tipleri için kullandığı arayüzdür ve size birçok olası soruna tek bir giriş noktası sunar.  
- **Filtreleme çok önemlidir** – `if` kontrolü olmadan eksik resimler, kullanımdan kaldırılmış özellikler gibi uyarılar da görürsünüz ve loglarınız dağılır.  
- **İş parçacığı güvenliği** – geri çağrı, belgeyi yükleyen aynı iş parçacığında çalışır, bu yüzden sonuçları daha sonra toplamak isterseniz ortak yapıların güncellenmesi güvenlidir.

Bu snippet **uyarı geri çağrısını kaydeder** ve bu noktadan itibaren her eksik‑yazı‑tipi olayı `stdout`’a yazdırılır. Bu, **eksik yazı tiplerini izleme** işleminin çekirdeğidir.

## Adım 3 – Yapılandırılmış `LoadOptions` ile belgeyi yükleyin

Geri çağrı yerinde olduğunda, nihayet dosyayı yüklüyoruz. Belge, sahip olmadığınız bir yazı tipine referans veriyorsa, geri çağrı belge nesnesi tam olarak oluşturulmadan önce tetiklenir.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

`YOUR_DIRECTORY` kısmını makinenizdeki gerçek yol ile değiştirin. `Document` yapıcı dosyayı okur, `loadOptions` içinde bir şifre belirlediyseniz uygular ve her eksik yazı tipi için uyarı geri çağrısını tetikler. Çıktı şöyle olur:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Bu satır, **eksik yazı tiplerini izlediğinizi** kanıtlar.

## Adım 4 – Belgeyi işlemeye devam edin (isteğe bağlı)

Bu aşamada belgeyi istediğiniz gibi manipüle edebilirsiniz – metin değiştirme, resim ekleme ya da ikame edilen yazı tiplerini programatik olarak değiştirme. Geri çağrı zaten sorunlu yazı tiplerinin bir listesini verdiği için, örneğin bir yedek yazı tipi gömebilirsiniz:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

Sadece **eksik yazı tiplerini izleme** ihtiyacınız varsa bu bölümü atlayabilirsiniz. Önemli olan, artık bilinçli bir karar vermeniz için gerekli bilgiye sahip olmanızdır.

## Adım 5 – İşlenmiş belgeyi kaydedin

Son olarak belgeyi kalıcı hale getirin. Orijinali üzerine yazabilir, yeni bir konuma kaydedebilir veya PDF’ye dışa aktarabilirsiniz – hepsi daha önce yakaladığınız uyarı verilerini kaybetmeden.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

Tüm sınıfı çalıştırdığınızda, her eksik yazı tipi için konsol çıktısı ve aynı klasörde `processed.docx` adlı yeni bir dosya elde edersiniz.

## Tam Çalışan Örnek

Aşağıda IDE’nize kopyalayıp yapıştırabileceğiniz tam Java sınıfı yer alıyor. Tartıştığımız her şeyi ve küçük bir `main` metodu sarmalayıcısını içeriyor.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Beklenen Çıktı

Programı, sisteminizde yüklü olmayan bir yazı tipi kullanan bir belgeye karşı çalıştırdığınızda şu benzeri bir çıktı görürsünüz:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

Eğer belge **hiç eksik yazı tipi içermiyorsa**, konsol sadece son “Document saved successfully.” satırına kadar sessiz kalır – tam da iyi bir **uyarı geri çağrısı kaydetme** uygulamasının beklediği gibi.

## Profesyonel İpuçları & Yaygın Tuzaklar

- **Birden fazla geri çağrı?** Aspose.Words yalnızca bir uyarı işleyicisine izin verir. Hem dosyaya hem de konsola loglamak isterseniz, uyarıyı birden çok hedefe yönlendiren birleşik bir geri çağrı uygulayın.  
- **Büyük toplular** – yüzlerce dosya işlerken tek bir `LoadOptions` örneğini yeniden kullanın; dosya başına yeni bir örnek oluşturmak gereksiz yük getirir.  
- **Şifreli belgeler** – yüklemeden önce şifreyi `LoadOptions` üzerine ayarlayın, aksi takdirde `IncorrectPasswordException` geri çağrıdan önce fırlatılır.  
- **Performans** – geri çağrı senkron çalışır. Uzaktaki bir servise log gönderiyorsanız, mesajları biriktirip yükleme tamamlandıktan sonra boşaltın, I/O darboğazlarını önleyin.  
- **Yazı tipi yedekleme** – sistem yazı tiplerinden önce değerlendirilmesini istediğiniz özel yazı tipleriniz varsa, bir `FontSource` koleksiyonu sağlayabilirsiniz.

## Sonuç

Java’da **uyarı geri çağrısını kaydetmeyi**, etkili bir şekilde **eksik yazı tiplerini izlemeyi** ve Aspose.Words ile **belge yüklemeyi özelleştirmeyi** öğrendiniz. Çözüm tek bir `main` metodu ile çalıştırılabilir, dış bağımlılık gerektirmez ve aksi takdirde fark edilmeyen yazı tipi ikameleri hakkında anında görünürlük sağlar.

Sonraki adımlar? Uyarıları denetim amaçlı bir CSV dosyasına yazmak için geri çağrıyı genişletin, ya da eksik yazı tiplerini otomatik olarak gömen bir toplu işleyici oluşturun. Ayrıca `IMAGE_SUBSTITUTION` ya da `DEPRECATED_FEATURE` gibi diğer uyarı tiplerini de keşfedebilirsiniz – aynı desen geçerli olur.

İyi kodlamalar, ve belgeleriniz her zaman istediğiniz gibi render olsun!

![Uyarı geri çağrısı diyagramı](register-warning-callback.png "Uyarı geri çağrısı akışı")


## Bir Sonraki Öğrenmeniz Gerekenler

- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Customize Theme Colors & Fonts in Aspose.Words Java: A Comprehensive Guide](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}