---
category: general
date: 2026-06-27
description: Aspose.Words kullanarak Java'da font ikame uyarılarını nasıl yakalayacağınızı
  öğrenin. Bu adım adım öğretici, uyarı geri çağrıları ve LoadOptions kullanımını
  da kapsar.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: tr
og_description: Java'da Aspose.Words ile yazı tipi ikame uyarılarını yakalayın. Uyarı
  geri çağrımlarını ayarlamak, LoadOptions kullanmak ve eksik yazı tiplerini ele almak
  için bu kılavuzu izleyin.
og_title: Java’da Yazı Tipi Değiştirme Uyarılarını Yakalama – Aspose.Words Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Aspose.Words ile Java'da Yazı Tipi Değiştirme Uyarılarını Yakalama – Tam Kılavuz
url: /tr/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java'da Aspose.Words ile Yazı Tipi Değiştirme Uyarılarını Yakalama – Tam Kılavuz

Egzotik yazı tipleri kullanan bir DOCX dosyasını yüklerken **yazı tipi değiştirme uyarılarını yakalamak** gerektiğinde hiç oldu mu? Tek başınıza değilsiniz. Gerçek dünyadaki birçok projede—otomatik rapor üreteçleri veya toplu belge dönüştürücüler gibi—eksik yazı tipleri sessiz değişikliklere neden olur ve bu da düzen bütünlüğünü bozabilir.

Neyse ki, Aspose.Words bu uyarıları dinlemenin temiz bir yolunu sunar. Bu öğreticide **LoadOptions** yapılandırmasını, bir **Aspose.Words warning callback** bağlamasını ve her *yazı tipi değiştirme* bildirimini konsola yazdırmayı adım adım göstereceğiz. Sonunda bir yazı tipinin ne zaman değiştiğini ve programatik olarak nasıl tepki vereceğinizi tam olarak bileceksiniz.

> **Neler elde edeceksiniz:** tamamen çalıştırılabilir bir Java kod parçacığı, her parçanın *neden* önemli olduğuna dair bir açıklama ve özel yazı tipi dizinleri gibi uç durumları ele almanız için ipuçları.

## Önkoşullar ve Gerekenler

Before we dive in, make sure you have:

- Java 8 veya daha yeni bir sürüm yüklü olduğundan emin olun (kod Java 11+ ile de çalışır).
- En son Aspose.Words for Java JAR (resmi siteden veya Maven Central'dan indirin).
- Makinenizde yüklü olmayan yazı tiplerine referans veren bir DOCX dosyası (örneğin Aspose demo setinde bulabileceğiniz *font‑rich.docx*).
- İyi bir IDE (IntelliJ IDEA, Eclipse veya hatta Java uzantılarına sahip VS Code).

Aspose.Words dışındaki dış kütüphanelere gerek yoktur ve örnek sade bir `main` metodunda çalışır.

## Adım 1: LoadOptions'ı Ayarlayın – Özel Yükleme İçin Giriş Noktası

`LoadOptions`, Aspose.Words'ün bir belgeyi *nasıl* okuyacağını belirten yapılandırma çantasıdır. Varsayılan olarak eksik yazı tiplerini sessizce değiştirir, ancak bir uyarı geri çağrısı ile bu davranışı değiştirebilirsiniz.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Neden önemli:** `LoadOptions` olmadan belge sessizce yüklenir ve eksik yazı tiplerini göremezsiniz. Bir örnek oluşturarak uyarı sistemi için bir kanca elde edersiniz.

## Adım 2: *Yazı Tipi Değiştirme Uyarılarını Yakalamak* için Bir Uyarı Geri Çağrısı Tanımlayın

Aspose.Words uyarı olaylarını `IWarningCallback` arayüzü üzerinden gönderir. Bunu satır içinde (veya ayrı bir sınıf olarak) uygulayın ve `WarningType.FONT_SUBSTITUTION` için filtreleyin.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Açıklama:**  
- `info.getWarningType()` uyarının kategorisini size söyler.  
- `WarningType.FONT_SUBSTITUTION` bizim ilgilendiğimiz enum değeridir.  
- `info.getDescription()` insan tarafından okunabilir bir mesaj içerir, örneğin *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

Açıklamayı yazdırarak, gerçek zamanlı olarak **yazı tipi değiştirme uyarılarını yakalarsınız**.

## Adım 3: Yapılandırılmış LoadOptions Kullanarak Belgeyi Yükleyin

Artık geri çağrı yerinde, DOCX dosyanızı yükleyin. Uyarı geri çağrısı ayrıştırma sırasında otomatik olarak tetiklenir.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

`YOUR_DIRECTORY`'yi test dosyanızın gerçek yolu ile değiştirin. `Document` yapıcı çalıştığında, eksik herhangi bir yazı tipi önceki adımda tanımlanan geri çağrıyı tetikler ve konsolda değiştirme mesajlarını görürsünüz.

## Adım 4: Yüklenen Belgeyi Doğrulayın (İsteğe Bağlı ama Faydalı)

Yüklemeden sonra belgenin bütünlüğünü—sayfa sayısı, metin çıkarımı vb.—doğrulamak isteyebilirsiniz. Bu adım uyarı yakalamak için gerekli değildir, ancak değişikliklerin etkisini görmenize yardımcı olur.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Bir yazı tipi değiştirildiyse, düzen biraz kayabilir; sayfa sayısını kontrol etmek bu tür değişiklikleri ortaya çıkarabilir.

## Adım 5: İleri Düzey – Değiştirilen Yazı Tiplerini Programatik Olarak İşlemek

Bazen sadece uyarıyı kaydetmek istemezsiniz—yedek bir yazı tipi eklemeniz veya stil ayarlamanız gerekebilir. Aşağıda benimseyebileceğiniz hızlı bir desen var.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Aspose.Words'ü orijinal yazı tiplerini içeren bir klasöre yönlendirerek değişikliği tamamen *önleyebilirsiniz*. Klasör eksikse, uyarı geri çağrısı hâlâ olayı yakalar ve size bir yedek strateji sunar.

## Tam Çalışan Örnek

Hepsini bir araya getirerek, işte tam ve çalıştırmaya hazır program:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Beklenen konsol çıktısı** (eksik bir yazı tipiyle karşılaşıldığında):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Tüm yazı tipleri mevcutsa, geri çağrı sessiz kalır—hiçbir şey yazdırılmaz, bu da tam olarak beklenen durumdur.

## Yaygın Tuzaklar ve Profesyonel İpuçları

| Tuzak | Neden olur | Çözüm |
|---------|----------------|-----|
| **Geri çağrı hiç tetiklenmiyor** | Geri çağrıyı `LoadOptions`'a eklemeyi unuttunuz **veya** `loadOptions` geçirmeden `Document`'in varsayılan yapıcısını kullandınız. | Her zaman `loadOptions.setWarningCallback(...)` çağırın **ve** `new Document(path, loadOptions)` aşırı yüklemesini kullanın. |
| **Çok fazla uyarı günlük dosyasını kirletiyor** | Birçok eksik yazı tipine sahip büyük belgeler, her değişiklik için bir uyarı üretir. | `info.getDescription()` içinde belirli yazı tipi adlarını kontrol ederek daha fazla filtreleyin veya uyarıları daha sonra işlemek üzere bir listede toplayın. |
| **Değiştirilen yazı tipleri düzeni etkiler** | Yedek yazı tipi farklı ölçülere (boyut, boşluk) sahip olabilir. | Özel bir yazı tipi klasörü sağlayın (Bkz. Adım 5) veya yüklemeden sonra belgenin stilini ayarlayın. |
| **Başsız bir sunucuda çalıştırma** | Varsayılan yazı tipi yedeklemesi, sunucuda yüklü olmayan sistem yazı tiplerine dayanabilir. | Gerekli yazı tiplerini uygulamanızla birlikte dağıtın ve `FontSettings`'i o klasöre yönlendirin. |

## Sıkça Sorulan Sorular

**S: Bu PDF veya diğer formatlarla çalışır mı?**  
C: Evet. Uyarı geri çağrısı format bağımsızdır; Aspose.Words'un yüklediği herhangi bir belge türü (DOC, DOCX, RTF, HTML vb.) için tetiklenir. Tek fark, ortaya çıkabilecek uyarı setidir.

**S: *Görüntü çözünürlüğü* uyarıları gibi diğer uyarı türlerini yakalayabilir miyim?**  
C: Kesinlikle. `warning` metodunun içinde, `info.getWarningType()`'ı `WarningType.IMAGE_RESOLUTION` gibi diğer enum değerleri için inceleyin. Ardından bunları uygun şekilde işleyin.

**S: Belge yüklendikten sonra değiştirilen yazı tiplerinin listesini ihtiyacım olursa?**  
C: Geri çağrı içinde her `info.getDescription()`'ı bir `List<String>` içinde saklayın. Yüklemeden sonra, kaydedebileceğiniz, izleme hizmetine gönderebileceğiniz veya bir yazı tipi indirme rutinini tetiklemek için kullanabileceğiniz bir koleksiyonunuz olur.

## Sonuç

Artık Java'da Aspose.Words kullanarak **yazı tipi değiştirme uyarılarını nasıl yakalayacağınızı**, her parçanın neden önemli olduğunu ve çözümü gerçek dünya senaryolarına nasıl genişletebileceğinizi biliyorsunuz. `LoadOptions`, bir `Aspose.Words warning callback` ve isteğe bağlı `FontSettings` kullanarak eksik yazı tiplerini tam olarak görebilir ve belge dönüştürme hatlarınızı güvenilir tutabilirsiniz.

Bir sonraki adıma hazır mısınız? `System.out.println`'ı SLF4J gibi bir logger ile değiştirin veya uyarı listesini toplu dönüşümden önce kullanıcıları bilgilendiren bir UI'ye entegre edin. Ayrıca **Aspose.Words warning callback**'i *desteklenmeyen özellikler* veya *yüksek çözünürlüklü görüntü* uyarıları gibi diğer uyarı türleri için keşfedebilirsiniz.  

Kodlamaktan keyif alın ve PDF'lerinizin bir daha beklenmedik yazı tipi değişiklikleriyle karşılaşmamasını dileriz!

![Yakalanan yazı tipi değiştirme uyarılarının konsol çıktısını gösteren ekran görüntüsü](image-placeholder.png "yazı tipi değiştirme uyarılarını yakala")

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words'de Yazı Tipi Değiştirme Uyarılarını Etkinleştirme – Tam Kılavuz](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Aspose.Words for Java'da LoadOptions Nasıl Ayarlanır](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words for Java ile PDF Belgeleri Nasıl Oluşturulur | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}