---
category: general
date: 2026-01-11
description: Aspose.Words for Java kullanarak yazı tipi ikame uyarılarını nasıl yakalayacağınızı
  öğrenin. Bu adım adım öğretici ayrıca LoadOptions ve uyarı geri çağrımlarını da
  kapsar.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: tr
og_description: Aspose.Words for Java ile yazı tipi ikame uyarılarını yakalayın. Güvenilir
  belge yüklemesi için LoadOptions ve bir uyarı geri çağrısı ayarlamak üzere bu kılavuzu
  izleyin.
og_title: Java'da Yazı Tipi Değişimi Uyarılarını Yakalama – Tam Kılavuz
tags:
- Aspose.Words
- Java
- Document Processing
title: Java'da Aspose.Words ile Yazı Tipi Değiştirme Uyarılarını Yakalama – Tam Kılavuz
url: /tr/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yazı Tipi Değiştirme Uyarılarını Yakalama – Tam Java Öğreticisi

Hiç eksik yazı tipleri içeren bir Word belgesi açarken **yazı tipi değiştirme uyarılarını yakalamak** gerekti mi? Bu, özellikle PDF oluştururken veya her bir tipografinin yüklü olmadığı bir sunucuda yazdırma yaparken sık karşılaşılan bir sorundur. İyi haber? Aspose.Words for Java bunu zahmetsiz hâle getiriyor—sadece bir `LoadOptions` nesnesi yapılandırın ve bir uyarı geri araması ekleyin. Bu rehberde tam olarak nasıl yapılacağını, neden önemli olduğunu ve uyarı tetiklendiğinde ne bekleyeceğinizi göreceksiniz.

Ayrıca **Aspose.Words yazı tipi değiştirme**, **Java uyarı geri araması** ve **LoadOptions kullanımı** gibi ilgili konulara da değineceğiz. Sonunda, eksik‑yazı tipi olaylarını kaydeden, böylece sonraki işlemlerinizin sizi şaşırtmayacağı hazır‑çalışır bir kod parçacığına sahip olacaksınız.

## Önkoşullar

İlerlemeye başlamadan önce şunların yüklü olduğundan emin olun:

- Java 17 (veya herhangi bir yeni JDK) yüklü ve yapılandırılmış.
- Aspose.Words for Java 23.10 (veya daha yeni) sınıf yolunuzda.
- Yerel olarak bulunmayan bir yazı tipine referans veren bir Word belgesi (ör. `DocWithMissingFont.docx`).
- Java try/catch bloklarıyla temel aşinalık—karmaşık bir şey değil.

Bu maddeler size yabancı geliyorsa, bir an durun ve kütüphaneyi Maven Central’dan kurun:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Temel hazırlıklar tamam, şimdi koda geçelim.

## Adım 1: **Yazı Tipi Değiştirme Uyarılarını Yakalamak** için Bir Uyarı Geri Araması Ayarlayın

İlk olarak, Aspose.Words eksik bir yazı tipiyle karşılaştığında çağıracağı bir geri aramaya ihtiyacınız var. İşte **yazı tipi değiştirme uyarılarını yakaladığımız** yer. Geri arama, `IWarningCallback` arayüzünü uygular ve `WarningType` değerini kontrol eder.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Neden önemli:** Bir geri arama olmadan, Aspose.Words eksik yazı tipini sessizce varsayılan bir yazı tipiyle değiştirir ve görsel çıktının değiştiğini asla öğrenemezsiniz. Uyarıyı yakalayarak, eksik yazı tipi kritikse kaydedebilir, uyarı gönderebilir veya yüklemeyi iptal edebilirsiniz.

## Adım 2: **LoadOptions**’ı Yapılandırın ve Geri Aramayı Kaydedin

Şimdi bir `LoadOptions` örneği oluşturup `FontWarningCallback`’imizi ekliyoruz. Bu adım, **LoadOptions kullanımının** temelini oluşturur ve her belge yüklemesinin aynı uyarı filtresinden geçmesini sağlar.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**İpucu:** Aynı `LoadOptions` nesnesini birden fazla belge için yeniden kullanabilirsiniz; bu, birkaç satır tekrarı tasarrufu sağlar ve uygulamanızda tutarlı **belge yükleme uyarıları** işlenmesini garantiler.

## Adım 3: Belgeyi Yükleyin ve Çıktıyı Gözlemleyin

Geri arama bağlandıktan sonra, Word dosyanızı basitçe yükleyin. Belge yüklü olmayan bir yazı tipine referans veriyorsa, geri arama tetiklenir ve ayrıntılar konsola yazdırılır.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Beklenen Konsol Çıktısı

`DocWithMissingFont.docx` eksik yazı tipi olarak *“Comic Sans MS”*’i referans veriyorsa, aşağıdakine benzer bir çıktı görürsünüz:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Belge **hiç eksik yazı tipi içermiyorsa**, konsol yalnızca son satırı gösterir ve geri aramanızın yanlış pozitif üretmediğini doğrular.

## Adım 4: Kenar Durumlarını ve Yaygın Tuzakları Ele Alma

### Birden Çok Eksik Yazı Tipi

Bir belge birden fazla bulunmayan yazı tipi kullanıyorsa, geri arama her bir yazı tipi için bir kez çalışır. Her biri kendi `source` ve `description` değerine sahip bir dizi mesaj alırsınız. Ek bir kod gerekmez—yalnızca kayıt sisteminizin hızlı ardışık çağrıları kaldırabildiğinden emin olun.

### Uyarıları Bastırma

Nadiren belirli değiştirmeleri göz ardı etmek isteyebilirsiniz (ör. belirli bir yedekleme kabul edilebilir). Geri arama mantığını şu şekilde genişletin:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### İş Parçacığı Güvenliği

Aspose.Words `LoadOptions` varsayılan olarak iş parçacığı‑güvenli değildir. Belgeleri paralel olarak yüklüyorsanız, her iş parçacığı için ayrı bir `LoadOptions` örneği oluşturun veya geri aramayı senkronize ederek yarış koşullarını önleyin.

## Adım 5: Sonuç Belgesindeki Değiştirilen Yazı Tipini Doğrulama

Yüklemeden sonra, değiştirmenin gerçekten gerçekleştiğini doğrulamak isteyebilirsiniz. API, tüm run’ları dolaşmanıza ve etkili yazı tipi adını incelemenize izin verir:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

Bu kod parçacığı, her metin run’unun son yazı tipini yazdırır. Otomatik PDF dönüşüm hatları kurarken kullanışlı bir kontrol noktasıdır.

## Tam Çalışan Örnek

Her şeyi bir araya getirdiğimizde, işte eksiksiz, hazır‑çalışır program:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Bunu `FontSubstitutionInfo.java` olarak kaydedin, `javac` ile derleyin ve `java FontSubstitutionInfo` ile çalıştırın. Uyarı mesajlarını (varsa) ardından run listesi ve son yazı tiplerini göreceksiniz.

## Görsel Yardım

![Yazı tipi değiştirme uyarılarını gösteren konsol çıktısının ekran görüntüsü](/images/font-substitution-warning.png "yazı tipi değiştirme uyarılarını yakalama örneği")

*Alt metin:* **yazı tipi değiştirme uyarılarını yakalama** – eksik yazı tipli bir belge yüklendikten sonra konsol çıktısı.

## Sonuç

Artık Aspose.Words for Java kullanarak **yazı tipi değiştirme uyarılarını yakalamayı** biliyorsunuz. Bir `LoadOptions` nesnesi yapılandırıp özel bir `IWarningCallback` sağlayarak, aksi takdirde sessizce belge görünümünü etkileyebilecek eksik‑yazı tipi olaylarını tam olarak görebilirsiniz. Bu teknik, **Aspose.Words yazı tipi değiştirme** işleyişine doğrudan bağlanır, güvenilir **belge yükleme uyarıları** sağlar ve iş kurallarınıza göre kaydetme, uyarı gönderme veya iptal etme esnekliği sunar.

### Sıradaki Adımlar

- Diğer uyarı türleri (ör. `DEPRECATED_FEATURE`) için **Java uyarı geri araması** desenlerini keşfedin.
- Bu yaklaşımı **PDF dönüşümü** ile birleştirerek değiştirilen yazı tiplerinin düzeni bozmadığından emin olun.
- **LoadOptions kullanımı** üzerine daha derinlemesine dalın—`Password`, `Encoding` ve `ResourceLoadingCallback` gibi gelişmiş senaryoları deneyin.

Geri aramayı istediğiniz gibi özelleştirmekten, uyarıları bir kayıt çerçevesine yönlendirmekten veya kritik bir yazı tipi eksikse özel bir istisna fırlatmaktan çekinmeyin. Gökyüzü sınırdır ve şimdi üzerine inşa edebileceğiniz sağlam bir temele sahipsiniz.

İyi kodlamalar, ve belgeleriniz her zaman beklediğiniz gibi render olsun!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}