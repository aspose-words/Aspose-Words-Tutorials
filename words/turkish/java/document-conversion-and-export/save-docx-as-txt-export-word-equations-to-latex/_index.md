---
category: general
date: 2026-05-04
description: Aspose.Words for Java kullanarak docx dosyasını hızlıca txt olarak kaydedin.
  Word'ü txt'ye dönüştürmeyi, satır sonlarını korumayı ve denklemleri LaTeX'e aktarmayı
  öğrenin.
draft: false
keywords:
- save docx as txt
- convert word to txt
- how to preserve line breaks
- convert docx to plain text
- export word equations latex
language: tr
og_description: Aspose.Words for Java ile docx dosyasını txt olarak kaydedin. Bu kılavuz,
  docx'i düz metne dönüştürmeyi, satır sonlarını korumayı ve denklemleri LaTeX olarak
  dışa aktarmayı gösterir.
og_title: docx'i txt olarak kaydet – Word denklemlerini LaTeX'e aktar
tags:
- aspose-words
- java
- txt-export
title: docx'i txt olarak kaydet – Word denklemlerini LaTeX'e dışa aktar
url: /tr/java/document-conversion-and-export/save-docx-as-txt-export-word-equations-to-latex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# docx dosyasını txt olarak kaydet – Word denklemlerini LaTeX'e dışa aktar

Word'de zahmetle yazdığınız matematiği kaybetmeden **docx dosyasını txt olarak kaydetmeyi** hiç merak ettiniz mi? Tek başınıza değilsiniz. Birçok geliştirici, denklemleri okunabilir tutarak bir Word dosyasını düz metne dökmek istiyor ve geleneksel kopyala‑yapıştır yöntemi sadece sembolleri bozuyor.  

Bu öğreticide, **Word'ü txt'ye dönüştüren**, her satır sonunu tam olarak olduğu gibi koruyan ve OfficeMath nesneleri için LaTeX üreten eksiksiz, çalıştırmaya hazır bir çözümü adım adım inceleyeceğiz. Sonunda, tüm bunları tek bir Java programı ile yapabileceksiniz—elle müdahale gerekmeyecek.

## Öğrenecekleriniz

- Aspose.Words for Java kullanarak **docx dosyasını txt olarak kaydetmeyi** nasıl yapacağınızı.
- `Satır sonlarını koruma` (`how to preserve line breaks`) konusunu göz önünde bulundurarak **word'ü txt'ye dönüştürmenin** doğru yolu.
- Sonuç `.txt` dosyasının temiz LaTeX işaretlemesi içermesi için **word denklemlerini latex olarak dışa aktarmayı**.
- Boş paragraflar veya gömülü resimler gibi uç durumları ele almak için ipuçları.
- Bugün projenize ekleyebileceğiniz tam, çalıştırılabilir bir kod örneği.

### Önkoşullar

- Makinenizde yüklü Java 8 veya daha üst bir sürüm.  
- **Aspose.Words for Java**'ın son sürümü (kod 23.12 ile test edilmiştir).  
- En az bir denklem (OfficeMath) içeren bir `.docx` dosyası.  
- Aspose bağımlılığını eklemek için Maven veya Gradle hakkında temel bilgi.

> **Pro tip:** Henüz bir lisansınız yoksa, Aspose değerlendirme filigranını kaldıran ücretsiz geçici bir lisans sunar.

---

## Adım 1: Projeyi Kurun ve Aspose.Words'ı Ekleyin

İlk olarak, yeni bir Maven (veya Gradle) projesi oluşturun. Aspose.Words bağımlılığını `pom.xml` dosyanıza ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Gradle tercih ediyorsanız, eşdeğeri şudur:

```groovy
implementation 'com.aspose:aspose-words:23.12'
```

Kütüphane sınıf yolunda olduğunda, **docx'i düz metne dönüştürmeye** hazırsınız.

## Adım 2: Word Belgesini Yükleyin

Kaynak `.docx` dosyasını yükleyerek başlayacağız. Bu, birçok yeni başlayanların `IOException`'ı ele almayı unuttuğu kısımdır; bu yüzden her şeyi bir try‑catch bloğuna sararız ya da kısaca `throws Exception` bildiririz.

```java
import com.aspose.words.*;

public class TxtMathExport {
    public static void main(String[] args) throws Exception {
        // Load the Word document containing equations
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Neden önemli:** `Document`, tüm dosya yapısını soyutlayarak bize paragraflara, koşulara (runs) ve denklemleri tutan gizli OfficeMath düğümlerine erişim sağlar.

## Adım 3: TXT Kaydetme Seçeneklerini Yapılandırın

Şimdi öğreticinin kalbi geliyor—Aspose'a metin dosyasının nasıl görünmesini istediğimizi tam olarak söylemek. İki ayar kritik:

1. **OfficeMathExportMode.LATEX** – her denklemi LaTeX sözdizimine dönüştürür.
2. **PreserveLineBreaks = true** – satır sonlarını orijinal Word dosyasındaki gibi tam olarak korur (`how to preserve line breaks`).

```java
        // Create TXT save options and set the math export mode to LaTeX
        TxtSaveOptions txtSaveOptions = new TxtSaveOptions();
        txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Preserve line breaks exactly as they appear in the source
        txtSaveOptions.setPreserveLineBreaks(true);
```

> **Açıklama:** Varsayılan olarak Aspose belgeyi düzleştirir ve çoğu biçimlendirmeyi kaldırır. `PreserveLineBreaks` ayarı, Word'deki her zor dönüşün çıktıda yeni bir satır olmasını sağlar; bu, metni daha sonra bir betiğe ya da sürüm kontrol sistemine beslediğinizde çok önemlidir.

## Adım 4: Belgeyi Düz Metin Dosyası Olarak Kaydedin

Son olarak, dönüştürülmüş içeriği diske yazıyoruz. `save` metodu hedef yolu ve az önce oluşturduğumuz seçenekleri alır.

```java
        // Save the document as a plain‑text file with the configured options
        document.save("YOUR_DIRECTORY/output.txt", txtSaveOptions);
    }
}
```

Hepsi bu—programı çalıştırın ve `output.txt` dosyasının kaynak dosyanızın yanında olduğunu göreceksiniz. Herhangi bir editörle açtığınızda şunları fark edeceksiniz:

- Normal paragraflar Word'de olduğu gibi görünür.
- Her denklem artık bir LaTeX dizesi, örn. `\int_{a}^{b} f(x)\,dx`.
- `setPreserveLineBreaks(true)` sayesinde ekstra boş satır yok.

![Save docx as txt example](image.png "Save docx as txt – sample output showing LaTeX equations")

### Beklenen Çıktı Örneği

`input.docx` dosyası *∑_{i=1}^{n} i = n(n+1)/2* denklemini içeriyorsa, `output.txt` içindeki ilgili satır şu şekilde görünecektir:

```
\sum_{i=1}^{n} i = \frac{n\,(n+1)}{2}
```

Diğer her şey düz kalır ve dosyayı sonraki işlemler için mükemmel kılar (örneğin, bir static‑site jeneratörüne ya da LaTeX derleyicisine beslemek).

---

## Sık Sorulan Sorular & Uç Durumlar

### Belge hiç denklem içermiyorsa ne olur?

`OfficeMathExportMode.LATEX` ayarı, OfficeMath düğümü olmadığında hiçbir şey yapmaz, bu yüzden çıktı sadece normal metin olur. Ek bir işlem gerekmez.

### Büyük belgeler (yüzlerce sayfa) nasıl işlenir?

Aspose çıktıyı akış olarak yazar, bu yüzden bellek tüketimi düşük kalır. Ancak, çok büyük dosyalar işliyorsanız JVM yığınını artırmak isteyebilirsiniz (`-Xmx2g` güvenli bir başlangıç noktasıdır).

### Denklemleri koruyarak HTML gibi diğer formatlara dışa aktarabilir miyim?

Kesinlikle. `TxtSaveOptions` yerine `HtmlSaveOptions` kullanın ve `setOfficeMathExportMode(OfficeMathExportMode.LATEX)` ayarlayın—aynı LaTeX işaretlemesi `<span>` etiketleri içinde gömülür.

### Bu macOS/Linux'ta çalışır mı?

Evet. Aspose.Words for Java platform bağımsızdır; sadece `JAVA_HOME` ortam değişkeninin uyumlu bir JDK'ya işaret ettiğinden emin olun.

---

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

Aşağıda, derlenip çalıştırılmaya hazır tam program yer alıyor. `YOUR_DIRECTORY` ifadesini `input.docx` dosyasını içeren gerçek klasörle değiştirin.

```java
import com.aspose.words.*;

public class TxtMathExport {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document containing equations
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create TXT save options and set the math export mode to LaTeX
        TxtSaveOptions txtSaveOptions = new TxtSaveOptions();
        txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Step 3: Preserve line breaks exactly as they appear in the source
        txtSaveOptions.setPreserveLineBreaks(true);

        // Step 4: Save the document as a plain‑text file with the configured options
        document.save("YOUR_DIRECTORY/output.txt", txtSaveOptions);
    }
}
```

Şununla çalıştırın:

```bash
mvn compile exec:java -Dexec.mainClass=TxtMathExport
```

veya Gradle kullanıyorsanız:

```bash
./gradlew run --args='YOUR_DIRECTORY/input.docx'
```

---

## Özet & Sonraki Adımlar

**docx dosyasını txt olarak kaydetmenin** her satır sonunu bozmadan ve Word denklemlerini temiz LaTeX'e dönüştürmenin nasıl yapılacağını gösterdik. Yaklaşım ölçeklenebilir, bellek sınırlarına saygı gösterir ve Java çalışan her işletim sisteminde çalışır.

Daha fazlasını mı arıyorsunuz?

- **docx'i düz metne dönüştürmek** diğer diller için (örneğin, Python) – aynı seçenek deseni geçerlidir.
- Bir klasördeki tüm `.docx` dosyalarını `File[]` nesneleri üzerinde döngü kurarak **toplu işleme**.
- Çıktıyı Hugo gibi bir static‑site jeneratörüne **entegre edin**, LaTeX parçacıkları MathJax ile render edilebilir.

`TxtSaveOptions` ile denemeler yapmaktan çekinmeyin—belirli bir karakter kümesi gerekiyorsa `setEncoding(Encoding.UTF_8)`'i değiştirebilir, başlık/altbilgi metnini tutmak için `setExportHeadersFooters(true)`'ı etkinleştirebilirsiniz.

Bir sorunla karşılaşırsanız, aşağıya yorum bırakın ya da Aspose'un resmi dokümantasyonuna bakın—beklenmedik derecede kapsamlı ve onlarca gerçek senaryo içeriyor.

Kodlamaktan keyif alın ve zengin Word dosyalarını hafif, LaTeX‑hazır metinlere dönüştürmenin sadeliğinin tadını çıkarın!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}