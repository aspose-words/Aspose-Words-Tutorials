---
category: general
date: 2026-04-04
description: Aspose.Words for Java ile Word belgelerini yüklerken yazı tipi ikame
  uyarılarını yakalayın ve eksik yazı tiplerini otomatik olarak tespit edin. Bu adım
  adım kılavuzu izleyin.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: tr
og_description: Aspose.Words for Java ile Word belgelerini yüklerken yazı tipi değiştirme
  uyarılarını yakalayın ve birkaç kolay adımda eksik yazı tiplerini tespit edin.
og_title: Yazı Tipi Değiştirme Uyarılarını Yakala – Eksik Yazı Tiplerini Tespit Et
tags:
- Aspose.Words
- Java
- Document Processing
title: Yazı Tipi Değiştirme Uyarılarını Yakala – Eksik Yazı Tiplerini Tespit Et
url: /tr/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yazı Tipi Değiştirme Uyarılarını Yakalama – Eksik Yazı Tiplerini Tespit Etme

Bir Word dosyası açarken **yazı tipi değiştirme uyarılarını yakalamak** gerektiğinde, kritik bir yazı tipinin eksik olduğunu fark ettiniz mi? Yalnız değilsiniz. Birçok kurumsal iş akışında eksik bir yazı tipi, kusursuz biçimlendirilmiş bir raporu karışık bir karmaşaya dönüştürebilir ve tek ipucu, çoğu geliştiricinin hiç görmediği sessiz bir uyarıdır.

İyi haber şu ki Aspose.Words for Java, yükleme sürecine müdahale etmenizi ve **eksik yazı tiplerini tespit etmenizi** sağlar, böylece ileride sorun yaratmadan önce. Bu öğreticide, her değiştirme uyarısını doğrudan konsola yazdıran tam, çalıştırılabilir bir örnek üzerinden geçeceğiz; böylece doğru yazı tipini gömmek, değiştirmek ya da kullanıcıyı uyarmak konusunda karar verebilirsiniz.

Bu rehberin sonunda şunları nasıl yapacağınızı öğreneceksiniz:

* `LoadOptions` nesnesini özel bir uyarı geri aramasıyla (callback) yapılandırmak.
* Geri aramayı yalnızca yazı tipi değiştirme olaylarına yanıt verecek şekilde filtrelemek.
* Herhangi bir `.docx` dosyasını yüklemek ve uyarıları anında görmek.
* Çözümü uyarıları kaydetmek, istisna fırlatmak veya hatta eksik yazı tiplerini otomatik olarak kurmak için genişletmek.

Harici bir belgeye gerek yok—sadece birkaç satır Java kodu ve Aspose.Words JAR'ı.

## Gereksinimler

İçeriğe girmeden önce şunların kurulu olduğundan emin olun:

* Java 8 veya daha yeni bir sürüm kurulu (en son LTS sürümü en iyisidir).
* Aspose.Words for Java 23.11 veya daha yeni – Maven artefaktını ya da Aspose web sitesinden düz JAR'ı alabilirsiniz.
* Geliştirme makinenizde bulunmayan bir yazı tipine referans veren bir Word belgesi (ör. “MyFancyFont”).  
* Tercih ettiğiniz bir IDE ya da metin düzenleyici – Ben IntelliJ IDEA kullanıyorum, ancak Eclipse ya da VS Code da işinizi görecektir.

Eğer bunlardan herhangi biri size yabancı geliyorsa, önce durup kurun; öğreticinin geri kalan kısmı bunların hazır olduğunu varsayar.

---

## Aspose.Words Kullanarak Yazı Tipi Değiştirme Uyarılarını Yakalama

Çözümün çekirdeği bir `LoadOptions` örneğinde bulunur. Bir `IWarningCallback` atayarak, kütüphanenin yükleme aşamasında yaydığı her uyarıyı yakalayabiliriz.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**Neden bu çalışıyor:**  
`LoadOptions`, Aspose.Words'e gelen dosyanın nasıl işleneceğini söyler. `IWarningCallback` arayüzü, *her* uyarı için bir `WarningInfo` nesnesi alan bir kancadır. `info.getWarningType()` kontrol ederek `SUBSTITUTED_FONT` dışındaki her şeyi filtreleriz. `description` özelliği, “Font 'MyFancyFont' was substituted with 'Arial'” gibi insan tarafından okunabilir bir mesaj içerir.

### Beklenen konsol çıktısı

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

Eğer kaynak belge yüklü olmayan bir yazı tipine referans veriyorsa, aşağıdakine benzer bir şey göreceksiniz:

Eğer belge yalnızca makinede mevcut olan yazı tiplerini kullanıyorsa, geri arama sessiz kalır ve sadece son “Document loaded successfully.” satırını alırsınız.

---

## Belgenizde Eksik Yazı Tiplerini Tespit Etme

Şöyle düşünebilirsiniz: *“Değiştirme uyarısı eksik bir yazı tipine eşdeğer mi?”* Çoğu durumda evet—Aspose.Words eksik bir yazı tipini bir yedekle değiştirir ve bunu `SUBSTITUTED_FONT` aracılığıyla raporlar. Ancak, bir yazı tipi mevcut ama tam stil (kalın‑italik, belirli OpenType özellikleri) yoksa, ince bir değiştirme gerçekleşebilir.

Her boşluğu kesinlikle yakaladığınızdan emin olmak için, uyarı geri aramasını bir yükleme sonrası denetimle birleştirebilirsiniz:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**Pro ipucu:** Eğer hâlâ eksik yazı tipine referans veren koşullar (run) bulursanız, bunları anında değiştirebilirsiniz:

```java
font.setName("Arial"); // fallback
```

Böylece, orijinal uyarı bastırılmış olsa bile tutarlı bir görsel sonuç garantilemiş olursunuz.

---

## Yaygın Tuzaklar ve Nasıl Kaçınılır

| **Tuzak** | **Neden Olur** | **Çözüm** |
|-----------|----------------|-----------|
| **Geri aramayı ayarlamayı unutmak** | `LoadOptions` varsayılan olarak hiçbir işlem yapmayan bir geri arama kullanır, bu yüzden uyarılar kaybolur. | Yüklemeden önce her zaman `loadOptions.setWarningCallback(...)` çağırın. |
| **Yanlış uyarı tipini kullanmak** | `WarningType.SUBSTITUTED_FONT`, eksik yazı tiplerini bildiren tek enumdur. | `WarningType.SUBSTITUTED_FONT` üzerine *tam olarak* filtreleyin; diğer tipler (ör. `UNKNOWN_FILE_FORMAT`) alakasızdır. |
| **Dosya yollarını sabit kodlamak** | Yerel ortamda çalışır ancak CI/CD hatlarında kırılır. | Göreli bir yol kullanın veya dosya konumunu komut satırı argümanı olarak geçirin. |
| **Unicode yazı tiplerini görmezden gelmek** | Bazı eksik yazı tipleri yalnızca belirli karakterler için sorun oluşturur. | Desteklemeyi planladığınız tam karakter setini içeren bir belgeyle test edin. |
| **Yazı tipi yapılandırması olmayan başsız bir sunucuda çalıştırmak** | Sunucuda yedek yazı tipleri bulunmayabilir, bu da beklenmedik değişikliklere yol açar. | Sunucuya minimal bir ortak yazı tipi seti (Arial, Times New Roman) kurun. |

---

## Çözümü Genişletme

Artık **yazı tipi değiştirme uyarılarını yakalayabildiğinize** göre, şunları yapmak isteyebilirsiniz:

* **Uyarıları bir dosyaya kaydet** – `System.out.println` yerine SLF4J gibi bir logger kullanın.
* **İstisna fırlat** – eksik bir yazı tipinin derlemeyi başarısız etmesi gereken otomatik hat hatlarında faydalıdır:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Eksik yazı tiplerini otomatik kur** – gerekli TTF/OTF dosyasını çalışma zamanında indirip Java `GraphicsEnvironment`'a ekleyin. Bu daha ileri bir senaryo, ancak tamamen mümkündür.

---

## Diyagram (isteğe bağlı)

![Yazı tipi değiştirme uyarılarını yakalama akış diyagramı, Aspose.Words'ün eksik‑yazı tipi uyarılarını özel bir geri aramaya nasıl yönlendirdiğini gösterir](capture-font-substitution-warnings-diagram.png)

---

## Sonuç

Şimdiye kadar Aspose.Words for Java ile Word belgelerini yüklerken **yazı tipi değiştirme uyarılarını yakalama** ve **eksik yazı tiplerini tespit etme** konularını ele aldık. Bir `LoadOptions` nesnesi yapılandırıp küçük bir `IWarningCallback` uygulayarak, yazı tipi yedekleme sürecine tam görünürlük kazanırsınız; bu da eksik yazı tiplerini kaydetmenize, değiştirmenize veya işlemi iptal etmenize olanak tanır.

Kısaca: geri aramayı ayarlayın, `SUBSTITUTED_FONT` için filtreleyin, belgeyi yükleyin ve çıktıyı uygulamanızın ihtiyacına göre işleyin. Buradan, logging çerçevelerine, CI kontrollerine ya da hatta otomatik yazı tipi temini gibi genişletebilirsiniz.

Daha ileri gitmek ister misiniz? Şunları deneyin:

* **Yazı tiplerini gömmek** doğrudan kaydedilen belgeye (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` ile `FontEmbeddingMode.EMBED_ALL` kullanarak).
* **PDF oluşturmak** yazı tipleri düzeltildikten sonra, son çıktının tam istediğiniz gibi görünmesini sağlamak.
* **Tüm bir klasörü** eksik yazı tipleri için taramak ve özet bir rapor üretmek.

Şimdilik hepsi bu—iyi kodlamalar, ve belgelerinizin her zaman doğru yazı tipiyle görüntülenmesi dileğiyle!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}