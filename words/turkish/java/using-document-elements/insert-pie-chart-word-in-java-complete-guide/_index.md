---
category: general
date: 2026-09-24
description: Aspose.Words for Java kullanarak bir DOCX dosyasına pasta grafiği ekleyin.
  Delik boyutunu ayarlamayı, pasta dilimini patlatmayı, pasta grafiği dilimini vurgulamayı
  öğrenin ve docx grafiğini zahmetsizce oluşturun.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: tr
lastmod: 2026-09-24
og_description: Aspose.Words for Java ile bir DOCX'e pasta grafiği ekleyin. Delik
  boyutunu ayarlamayı, pasta dilimini patlatmayı, pasta grafiği dilimini vurgulamayı
  ustalaşın ve dakikalar içinde DOCX grafiği oluşturun.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Java'da pasta grafiği ekleme – adım adım öğretici
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Java'da pasta grafiği kelimesi ekle – tam rehber
url: /tr/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da pie chart word ekleme – tam rehber

Eğer bir DOCX dosyasına **insert pie chart word** eklemeniz gerekiyorsa, bu öğretici Aspose.Words for Java ile bunu tam olarak nasıl yapacağınızı gösterir. Belge oluşturulmasından grafiğin dilimini patlatmaya, delik boyutunu sıfıra ayarlamaya ve dilimi vurgulamaya kadar tam iş akışını göreceksiniz.

Word belgelerinde grafiklerle çalışmak, genellikle normal metin işleme ile ayrı bir konu gibi hissettirir, ancak Aspose.Words ikisini birleştirir. Aşağıdaki adımlarda ayrıca **create docx chart** dosyalarının nasıl oluşturulacağını öğrenecek ve bu dosyaların Microsoft Word, Google Docs veya başka bir DOCX‑uyumlu görüntüleyicide açılmaya hazır olduğunu göreceksiniz.

## Başaracaklarınız

* **Insert pie chart word** boş bir belgeye ekleyin  
* **Set hole size** grafiği tam bir pasta hâline getirmek için (halka grafiği olmadan)  
* **Explode pie slice** belirli bir bölüme dikkat çekmek için  
* **Highlight pie chart slice** özel biçimlendirme ile vurgulayın  
* **Create docx chart** paylaşılabilir veya daha sonra düzenlenebilir  

### Önkoşullar

* Java 17 veya daha yeni (kod Java 8 ile de derlenir)  
* Aspose.Words for Java kütüphanesi (sürüm 23.9 veya daha yeni)  
* Aspose.Words bağımlılığını çözebilen bir IDE veya derleme aracı (Maven/Gradle)  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Aspose.Words kullanarak bir DOCX'e pie chart word ekleme

İlk adım, yeni bir boş belge oluşturmak ve bir `DocumentBuilder` almaktır. Builder, belgenin içerik akışına doğrudan erişim sağlar ve **insert pie chart word** işlemini çok basit hale getirir.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Bunun önemi
`Document` tüm Word dosyasını temsil ederken, `DocumentBuilder` düşük seviyeli XML ile uğraşmadan paragraflar, tablolar ve grafikler eklemenizi sağlayan yüksek seviyeli bir API'dir. Temiz bir belgeyle başlamak, eklediğiniz grafiğin tek içerik olmasını sağlar; bu, öğrenme veya şablon‑tabanlı raporlar oluşturma için mükemmeldir.

## Deliği sıfıra ayarlayarak tam bir pasta oluşturma

Varsayılan olarak, Aspose.Words bir pie chart istediğinizde bir doughnut grafiği oluşturur. Grafiği gerçek bir daire hâline getirmek için **set hole size** değerini `0` olarak ayarlamanız gerekir. Bu, iç deliği kaldırır ve klasik bir pasta görünümü sağlar.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Pratik ipucu
Daha sonra bir doughnut grafiğine geçmeye karar verirseniz, sadece `holeSize` değerini bir yüzdeye (ör. `30`) değiştirin. Aynı API her iki grafik türü için de çalışır.

## Dilimi patlatarak bir bölümü vurgulama

Bir dilimi patlatmak, görsel olarak öne çıkmasını sağlar. **explode pie slice** işlemi, seçilen dilimi grafiğin yarıçapının bir yüzdesi kadar dışarı doğru hareket ettirir.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Neden patlatılır?
Patlatılmış bir dilim, okuyucunun gözünü en önemli veri noktasına çeker—panolar veya yönetici özetleri için mükemmeldir. `20` değeri, yarıçapın %20'si anlamına gelir; bunu `0` (patlatma yok) ile `100` (tamamen ayrılmış) arasında ayarlayabilirsiniz.

## Pie chart dilimini özel biçimlendirme ile vurgulama

Patlatmanın ötesinde, doldurma rengi veya kenarlığını değiştirerek **highlight pie chart slice** isteyebilirsiniz. Demo kodu patlatmaya odaklansa da, aşağıdaki gibi genişletebilirsiniz:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Uzman notu
Belirli bir dilimin doldurma rengini değiştirmek, `DataPoint` nesnesine erişmeyi gerektirir. Birden fazla seriniz varsa, `series.getDataPoints()` üzerinden döngü yaparak stilleri koşullu olarak uygulayın.

## Oluşturulan docx grafiğini kaydetme ve doğrulama

Son olarak, `Document`'i kaydederek **create docx chart** yaparsınız. Oluşan dosya, biçimlendirilmiş pie chart'ı görmek için Microsoft Word'de açılabilir.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Beklenen çıktı
`PieChartFormatted.docx` dosyasını açtığınızda tek bir pie chart gösterilir:

* Grafik, 400 × 300 pt bir alanı kaplar.  
* Delik boyutu `0` olduğundan, grafik tam bir pasta.  
* İlk dilim %20 patlatılmış ve kırmızı renkte (isteğe bağlı biçimlendirme eklediyseniz).  

Artık dağıtılabilir, e-postalara gömülebilir veya programlı olarak daha fazla düzenlenebilen bir **create docx chart**'a sahipsiniz.

---

## Yaygın varyasyonlar ve kenar durumları

| Senaryo | Kodu nasıl uyarlarsınız |
|----------|----------------------|
| **Multiple series** | Seriler üzerinde `pieChart.getChart().getSeries()` döngüsü yapın ve her seri için `Explosion` veya `FillColor` ayarlayın. |
| **Dynamic data** | Serileri, `setExplosion` çağırmadan önce bir veritabanı veya CSV'den gelen değerlerle doldurun. |
| **Different chart size** | `insertChart(ChartType.PIE, width, height)` içindeki genişlik/yükseklik argümanlarını değiştirin. |
| **Export to PDF** | DOCX'i kaydettikten sonra aynı grafiğin PDF versiyonunu oluşturmak için `doc.save("output.pdf")` çağırın. |
| **Localization** | Etiketler için yerel‑spesifik sayı formatı kullanarak `DocumentBuilder.insertChart` metodunu kullanın. |

### Pro ipucu
`setHoleSize(0)` metodunu her zaman `insertChart` **sonrasında** çağırın. Eğer eklemeden önce ayarlarsanız, Aspose.Words grafiği oluşturduktan sonra varsayılan doughnut boyutuna geri dönecektir.

---

## Özet

Artık Java kullanarak bir Word belgesine **insert pie chart word** eklemeyi, tam pasta görünümü için **set hole size** ayarlamayı, dikkat çekmek için **explode pie slice** yapmayı ve özel renklerle **highlight pie chart slice** yapmayı biliyorsunuz. Tam örnek ayrıca dağıtıma hazır **create docx chart** dosyalarının nasıl oluşturulacağını da gösteriyor.

## Sonraki adımlar

* `ChartType` ile diğer grafik türlerini (`BAR`, `LINE`, `SCATTER`) keşfedin.  
* Grafik oluşturmayı mail merge ile birleştirerek kişiselleştirilmiş raporlar üretin.  
* Oluşturulan DOCX'i, isteğe bağlı olarak dosyayı dönen bir web servisine entegre edin.  

Sorunlarla karşılaşırsanız, uyumlu bir Aspose.Words sürümü kullandığınızdan ve çıktı dizininin var olduğundan ve yazılabilir olduğundan emin olun.

İyi kodlamalar!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}