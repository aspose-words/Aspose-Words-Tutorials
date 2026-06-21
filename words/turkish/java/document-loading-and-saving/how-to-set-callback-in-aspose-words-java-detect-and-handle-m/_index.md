---
category: general
date: 2026-06-20
description: Aspose.Words Java'da eksik fontları tespit etmek ve belge yüklemeyi özelleştirmek
  için geri aramayı (callback) nasıl ayarlayacağınızı öğrenin. Font ikame uyarılarını
  adım adım nasıl yöneteceğinizi keşfedin.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: tr
og_description: Aspose.Words Java'da eksik fontları tespit etmek, ikameleri işlemek
  ve belge yüklemeyi özelleştirmek için geri çağırma (callback) nasıl ayarlanır. Kodlu
  tam rehber.
og_title: callback nasıl ayarlanır – Aspose.Words Java'da Eksik Yazı Tiplerini Tespit
  Et
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: Aspose.Words Java'da callback nasıl ayarlanır – Eksik Yazı Tiplerini Algılamak
  ve İşlemek
url: /tr/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java’da geri çağırma (callback) nasıl ayarlanır – Eksik Yazı Tiplerini Algıla ve İşle

Hiç **geri çağırma (callback) nasıl ayarlanır** diye merak ettiniz mi Aspose.Words Java’da, böylece PDF veya DOCX’inizi bozabilecek eksik yazı tiplerini önceden tespit edebilirsiniz? Tek başınıza değilsiniz. Eksik yazı tipi uyarıları sessizce yerleşimi bozabilir ve uygun bir uyarı geri çağırması olmadan, son belge hatalı görünene kadar bunu fark etmeyebilirsiniz.  

Bu öğreticide, **eksik yazı tiplerini algılayan**, **eksik yazı tiplerini sorunsuz bir şekilde işleyen** ve bir uyarı geri çağırmasıyla **belge yüklemeyi özelleştirmenizi** gösteren tam, çalıştırmaya hazır bir örnek üzerinden geçeceğiz. Sonunda, ekstra dokümantasyon aramaya gerek kalmadan herhangi bir projeye ekleyebileceğiniz bağımsız bir Java sınıfına sahip olacaksınız.

## What You’ll Need

- Java 8 veya daha yeni (kod Java 11+ ile de çalışır)  
- Aspose.Words for Java kütüphanesi (sürüm 23.9 veya üzeri)  
- Yüklü olmayan bir yazı tipine referans veren bir DOCX dosyası (ör. özel bir kurumsal yazı tipi)  

Eğer Aspose.Words’ı Maven projenize henüz eklemediyseniz, sadece şunu ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Hepsi bu—ekstra eklenti yok, yerel bağımlılık yok.

---

## Step 1: Understand the WarningCallback Mechanism

**Uyarı geri çağırması**, bir belge yüklenirken veya kaydedilirken beklenmedik bir şey olduğunda Aspose.Words’ın size seslenme şeklidir. `IWarningCallback`’i uygulayarak, neyin kaydedileceği, yoksayılacağı ya da bir istisna haline getirileceği üzerinde tam kontrol elde edersiniz.

> **Neden önemli:**  
> Bir yazı tipi eksik olduğunda, Aspose bir yedek yazı tipi kullanır. Görsel sonuç, özellikle marka odaklı PDF’lerde dramatik şekilde farklı olabilir. `WarningType.FONT_SUBSTITUTION` yakalayarak, tam yazı tipi adını kaydedebilir, iptal edip etmeyeceğinize karar verebilir veya kendi özel yazı tipinizi programatik olarak atayabilirsiniz.

---

## Step 2: Create a LoadOptions Instance

`LoadOptions`, belge yüklemeyi özelleştirmenin giriş noktasıdır. Dosyayı gerçekten yüklemeden önce geri çağırmayı bu nesneye ekleyeceksiniz.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Bu noktada `loadOptions` sadece basit bir kapsayıcı—henüz bir şey gerçekleşmedi. Gerçek sihir, geri çağırmayı bağladığımızda başlar.

---

## Step 3: Implement and Attach the Callback

Aşağıda, `IWarningCallback`’i uygulayan kompakt bir anonim sınıf yer alıyor. Bir yazı tipi ikamesi gerçekleştiğinde konsola dostça bir satır yazdırır.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Pro ipucu:** **Eksik yazı tiplerini** bir yedekle değiştirerek ele almak istiyorsanız, `LoadOptions` üzerine `FontSettings` ayarlayabilir ve eksik yazı tiplerini bilinen bir yedekle eşleyebilirsiniz.

---

## Step 4: Load the Document with Your Custom Options

Geri çağırma artık bağlandığına göre, belgeyi yükleyin. Dosya, yüklü olmayan bir yazı tipine referans veriyorsa, uyarı konsola yazdırılacaktır.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

Programı çalıştırdığınızda konsol şu şekilde bir çıktı verebilir:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Bu satır, **eksik yazı tiplerini başarıyla algıladığınızı** ve artık **eksik yazı tiplerini istediğiniz gibi işleyebileceğinizi** kanıtlar.

---

## Step 5: Optional – Replace Missing Fonts with a Known Font

Eksik bir yazı tipini otomatik olarak, örneğin `Times New Roman` ile değiştirmek isterseniz, bir `FontSettings` nesnesi ekleyebilirsiniz:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Şimdi belge yüklenecek ve `MyCustomFont` referansı sessizce `Times New Roman` ile değiştirilecektir. Konsol hâlâ neyin değiştirildiğini bildirecek, böylece süreçten haberdar olacaksınız.

---

## Full Working Example

Aşağıda, yukarıdaki tüm adımları birleştiren tek bir Java sınıfı bulunuyor. IDE’nize kopyalayıp yapıştırın, `docPath`’i ayarlayın ve çalıştırın.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Beklenen çıktı**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Artık **eksik yazı tiplerini algılayabilir**, **eksik yazı tiplerini işleyebilir** ve **belge yüklemeyi özelleştirebilirsiniz**—hepsi **geri çağırmayı (callback) doğru şekilde ayarlamayı** öğrenerek.

---

## Frequently Asked Questions

### What if I want the program to stop loading when a font is missing?

`warning` metodunun içinde bir istisna fırlatın:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

Alt kısımdaki `catch` bloğu bunu yakalar ve kullanıcıyı nasıl kaydedeceğinize ya da uyaracağınıza karar verebilirsiniz.

### Does this work for PDFs generated from DOCX?

Kesinlikle. Geri çağırma **yükleme** aşamasında tetiklenir ve bu, tüm çıktı formatları (`save` ile PDF, DOCX, HTML vb.) için aynıdır. Kaynak belgeyi aynı `LoadOptions` ile yüklerseniz, eksik yazı tiplerini nihai PDF’yi etkilemeden yakalarsınız.

### Can I capture other warning types (e.g., image conversion)?

Evet—`WarningInfo.getWarningType()` diğer enum değerleriyle, örneğin `WarningType.IMAGE_CONVERSION` ile karşılaştırılabilir. Geri çağırmada daha fazla `if` dalı eklemeniz yeterli.

### Is there a performance impact?

İhmal edilebilir. Geri çağırma, yükleme sırasında senkron olarak çalışır ve ek kontroller hafiftir. Binlerce belge yüklüyorsanız, üretim ortamında uyarıları devre dışı bırakmak için `loadOptions.setWarningCallback(null);` ayarlamayı düşünebilirsiniz.

---

## Visual Overview

![geri çağırma örneği Aspose.Words Java’da nasıl ayarlanır](https://example.com/images/callback-diagram.png "geri çağırma örneği")

*Şema akışı gösterir: `LoadOptions` → `IWarningCallback` → Belge yükleme → Yazı tipi ikamesi işleme.*

---

## Wrap‑Up

**Aspose.Words Java’da geri çağırma (callback) nasıl ayarlanır** konusunu ele aldık, **eksik yazı tiplerini algılamayı** gösterdik, **eksik yazı tiplerini işleme** yollarını sunduk ve `LoadOptions` ile **belge yüklemeyi özelleştirmeyi** açıkladık.  

Bu bilgiyle, belge iş akışlarınızı sessiz yazı tipi değişimlerine karşı koruyabilir, marka tutarlılığını sağlayabilir ve bir şeyler ters gittiğinde kullanıcılarınıza net geri bildirim verebilirsiniz.

### What’s Next?

- Birden çok eksik yazı tipini toplu olarak eşlemek için **yazı tipi ikame tablolarını** keşfedin.  
- Bu geri çağırmayı **belge doğrulama** ile birleştirerek stil kılavuzlarını zorunlu kılın.  
- `System.out` yerine bir log dosyasına ya da izleme sistemine yazan **özel uyarı geri çağırmaları** deneyin.  

Denemeler yapın ve geri çağırmayı kendi projelerinizde nasıl özelleştirdiğinizi bize bildirin. İyi kodlamalar!

---


## What Should You Learn Next?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakın konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalar ve tam çalışan kod örnekleri içerir.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}