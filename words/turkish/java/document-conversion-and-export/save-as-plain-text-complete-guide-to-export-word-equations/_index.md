---
category: general
date: 2026-05-30
description: Denklemleri koruyarak düz metin olarak kaydetmeyi ve docx'i txt'ye dönüştürmeyi
  öğrenin. Word denklemlerini dışa aktaran adım adım Java örneği.
draft: false
keywords:
- save as plain text
- convert docx to txt
- export word equations
- save word as txt
- convert word with equations
language: tr
og_description: 'Düz metin olarak kaydetme öğreticisi: docx''i txt''ye dönüştürme,
  Word denklemlerini dışa aktarma ve Aspose.Words kullanarak Word''ü txt olarak kaydetme.'
og_title: Düz metin olarak kaydet – Java’da Word denklemlerini dışa aktar
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Learn how to save as plain text and convert docx to txt while preserving
    equations. Step‑by‑step Java example with export word equations.
  headline: save as plain text – Complete Guide to Export Word Equations
  type: TechArticle
- description: Learn how to save as plain text and convert docx to txt while preserving
    equations. Step‑by‑step Java example with export word equations.
  name: save as plain text – Complete Guide to Export Word Equations
  steps:
  - name: Expected Output
    text: 'Open `MathSample.txt` in any editor and you’ll see something like:'
  - name: What if the target system doesn’t support Unicode?
    text: 'If you need an ASCII‑only fallback, switch the export mode to `OfficeMathExportMode.TEXT`.
      The equations will be rendered as plain text approximations (e.g., “sum(i=1
      to n) i”). Just replace the line:'
  - name: Can I batch‑process a folder of DOCX files?
    text: Absolutely. Wrap the loading and saving logic inside a `File[] files = new
      File("inputFolder").listFiles();` loop. Remember to handle exceptions per file
      to avoid the whole batch stopping on a single corrupt document.
  - name: What about tables or images?
    text: '`TxtSaveOptions` strips non‑text elements by design. If you need a richer
      export (e.g., CSV for tables), consider `CsvSaveOptions` instead. Images are
      omitted because plain text cannot embed binary data.'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Conversion
title: Düz metin olarak kaydet – Word denklemlerini dışa aktarma tam rehberi
url: /tr/java/document-conversion-and-export/save-as-plain-text-complete-guide-to-export-word-equations/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# düz metin olarak kaydet – Denklemlerle DOCX Dönüştürme için Full‑Stack Eğitimi

Hiç **düz metin olarak kaydet**meniz gerekti ama Word dosyanızda bozulmuş matematik formülleri var mı? Tek başınıza değilsiniz. Araştırma makalelerini arşivliyor, bir arama indeksine besliyor ya da sadece bir sözleşmenin hafif bir sürümüne ihtiyacınız olsun, zorluk, bu OfficeMath nesnelerinin dönüşüm sonrası okunabilir kalmasını sağlamaktır.

İşte mesele şu ki—çoğu basit dönüştürücü denklem gliflerini okunamaz semboller olarak döker. Bu rehberde **convert docx to txt** işlemini denklemleri Unicode olarak koruyarak nasıl yapacağınızı tam olarak göstereceğiz; temelde *export word equations* işlemini temiz, aranabilir bir formatta gerçekleştireceksiniz. Sonunda **saves word as txt** yapan, çalıştırmaya hazır bir Java kod parçacığına sahip olacaksınız.

## Bu Eğitimde Neler Ele Alınıyor

- Gerekli bağımlılıklar (Aspose.Words for Java)  
- **TxtSaveOptions** ayarlarıyla dışa aktarma modunu kontrol etme  
- **convert word with equations** işlemini güvenli bir şekilde yapan tam, çalıştırılabilir bir Java programı  
- Yaygın tuzaklar (yazı tipi sorunları, eksik Unicode desteği) ve bunlardan nasıl kaçınılır  
- Sonraki adımlar: satır sonlarını ayarlama, tabloları işleme ve toplu işleme  

Harici dokümantasyon bağlantılarına ihtiyaç yok—gereken her şey burada.

## Ön Koşullar

- Makinenizde Java 8 veya daha yeni bir sürüm yüklü  
- Bağımlılık yönetimi için Maven veya Gradle (örnekte Maven kullanacağız)  
- En az bir OfficeMath nesnesi (denklem) içeren bir DOCX dosyası  

Eğer bunlara sahipseniz, hemen başlayalım.

## Adım 1: Aspose.Words Bağımlılığını Ekleyin

İlk olarak Aspose.Words for Java kütüphanesini alın. Bu ticari bir ürün, ancak geliştirme için çalışan ücretsiz geçici bir lisans sunuyorlar.

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Pro ipucu:** Maven kullanmıyorsanız `aspose-words-24.9.jar` dosyasını sınıf yolunuza (classpath) yerleştirin.

## Adım 2: Kaynak Belgeyi Yükleyin

Şimdi **load the source document** işlemini yapacağız. `Document` sınıfı, gömülü denklemler içeren `.docx` dahil olmak üzere tüm Word formatlarını okuyabilir.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class DocxToTxtConverter {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
        // ... we'll add the save logic next
    }
}
```

`document` değişken adının bir Word dosyasını temsil etmesi, kodun kendini açıklayıcı olmasını sağlıyor.

## Adım 3: Denklem Dışa Aktarma İçin TxtSaveOptions’u Yapılandırın

**export word equations** iş akışının kalbi `TxtSaveOptions` içinde yer alır. Varsayılan olarak Aspose OfficeMath’u atar, ancak bunu `OfficeMathExportMode.UNICODE` ile değiştirebiliriz.

```java
import com.aspose.words.TxtSaveOptions;
import com.aspose.words.OfficeMathExportMode;

// Inside main after loading the document
TxtSaveOptions txtSaveOptions = new TxtSaveOptions();
txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.UNICODE);
```

Modu `UNICODE` olarak ayarlamak, Aspose’a her denklemi Unicode temsili (ör. “∑”, “√”) olarak oluşturmasını söyler. Bu sayede düz metin dosyası hâlâ insanlar tarafından *okunabilir* ve araçlar tarafından aranabilir olur.

## Adım 4: Belgeyi Düz Metin Olarak Kaydedin

Son olarak, yapılandırılmış seçenekleri kullanarak **save as plain text** işlemini gerçekleştiriyoruz. Bu adım, ana anahtar kelimenin gerçekten parladığı yerdir.

```java
// Step 4: Save the document as a plain‑text file with the configured options
document.save("YOUR_DIRECTORY/MathSample.txt", txtSaveOptions);
System.out.println("Conversion complete! File saved as plain text.");
```

Bu tek satır, ağır işi yapar: bir `.txt` dosyası yazar, denklemleri korur ve satır sonlarına saygı gösterir. Artık **convert docx to txt** işlemini matematiği koruyarak başarıyla tamamladınız.

## Tam Çalışan Örnek

Hepsini bir araya getirerek, IDE’nize kopyalayıp yapıştırabileceğiniz tam program aşağıdadır.

```java
import com.aspose.words.Document;
import com.aspose.words.TxtSaveOptions;
import com.aspose.words.OfficeMathExportMode;

public class DocxToTxtConverter {
    public static void main(String[] args) throws Exception {
        // Load the DOCX that contains equations
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Prepare TXT save options: export OfficeMath as Unicode
        TxtSaveOptions txtSaveOptions = new TxtSaveOptions();
        txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.UNICODE);

        // Save as plain text
        document.save("YOUR_DIRECTORY/MathSample.txt", txtSaveOptions);

        System.out.println("Conversion complete! File saved as plain text.");
    }
}
```

### Beklenen Çıktı

Herhangi bir editörde `MathSample.txt` dosyasını açın; aşağıdakine benzer bir şey göreceksiniz:

```
This is a sample paragraph.
∑_{i=1}^{n} i = n(n+1)/2
Another line of text.
```

Denklem, uygun bir Unicode toplam sembolü olarak görünür; bu da **export word equations** bayrağının çalıştığını kanıtlar.

## Yaygın Sorular ve Kenar Durumlar

### Hedef sistem Unicode’u desteklemiyorsa ne olur?

ASCII‑only bir geri dönüşüm gerekiyorsa, dışa aktarma modunu `OfficeMathExportMode.TEXT` olarak değiştirin. Denklemler, düz metin yaklaşımları (ör. “sum(i=1 to n) i”) şeklinde renderlanır. Sadece şu satırı değiştirin:

```java
txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.TEXT);
```

### DOCX dosyalarının bir klasörünü toplu işleyebilir miyim?

Kesinlikle. Yükleme ve kaydetme mantığını `File[] files = new File("inputFolder").listFiles();` döngüsü içine sarın. Tek bir bozuk belge nedeniyle tüm toplu işlemin durmasını önlemek için dosya başına istisna yakalamayı unutmayın.

### Tablolar ya da görseller hakkında ne söyleyebilirsiniz?

`TxtSaveOptions` tasarım gereği metin dışı öğeleri atar. Daha zengin bir dışa aktarma (ör. tablolar için CSV) istiyorsanız `CsvSaveOptions` kullanmayı düşünün. Görseller çıkarılır çünkü düz metin ikili veri gömemez.

## Güvenilir Dönüşümler İçin Pro İpuçları

- **License early**: Aspose, 30 gün sonra lisans olmadan çalıştırırsanız bir uyarı verir. `main` metodunun başına `License license = new License(); license.setLicense("Aspose.Words.lic");` ekleyin.  
- **UTF‑8 encoding**: Kütüphane varsayılan olarak UTF‑8 yazar. Farklı bir kod sayfasına ihtiyacınız varsa `txtSaveOptions.setEncoding(Encoding.getEncoding("windows-1252"));` ayarlayın.  
- **Line endings**: Windows‑stilinde CRLF için `txtSaveOptions.setSaveFormat(SaveFormat.TEXT);` çağırın (varsayılan zaten platforma özgü satır sonlarını kullanır).

## Görsel Genel Bakış

![save as plain text workflow diagram](placeholder.png){alt="save as plain text workflow showing load, configure options, and save steps"}

Diagram, az önce kodladığımız üç adımlı hattı gösterir: Yükle → Yapılandır → Kaydet.

## Sonuç

Artık **save as plain text** yaparken **convert docx to txt** ve tüm denklemleri eksiksiz tutmayı biliyorsunuz. Anahtar, `TxtSaveOptions`’ı `OfficeMathExportMode.UNICODE` ile yapılandırmak; bu da **export word equations** işlemini temiz, aranabilir bir formatta gerçekleştirmenizi sağlar. Bu temelle **save word as txt** kolayca yapabilir, klasörleri toplu işleyebilir veya farklı ortamlar için dışa aktarma modunu ayarlayabilirsiniz.

Sırada ne var? Kullanıcıların aracı herhangi bir klasöre yönlendirebileceği bir komut satırı arayüzü eklemeyi deneyin ya da tabloları CSV’ye çekmek için `CsvSaveOptions` ile deneyler yapın. **convert word with equations** olasılıkları sonsuzdur ve artık sağlam, atıf değerinde bir başlangıç noktanız var.

İyi kodlamalar, ve düz metin dönüşümleriniz daima kayıpsız olsun!

## Sonraki Öğrenmeniz Gerekenler

- [Save Document as TXT – Quick Guide to Exporting Word Math](/words/english/java/document-conversion-and-export/save-document-as-txt-quick-guide-to-exporting-word-math/)
- [Convert docx to markdown – Export Math Equations to LaTeX with Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [How to Export LaTeX from Word: Convert DOCX to Markdown & Save as PDF](/words/english/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}