---
category: general
date: 2026-08-14
description: Aspose.Words kullanarak Java ile Word’de pasta grafiği oluşturun. Grafiğe
  seri verisi eklemeyi ve sadece birkaç satırda pasta dilimini döndürmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: tr
lastmod: 2026-08-14
og_description: Aspose.Words kullanarak Java ile Word'te pasta grafiği oluşturun.
  Bu öğreticide, grafiğe seri verileri ekleme ve pasta dilimini hızlıca döndürme gösterilmektedir.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Java ile Word’de pasta grafiği oluşturma – tam kodlama rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Java ile Word'de Pasta Grafiği Oluşturma – Adım Adım Rehber
url: /tr/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de pasta grafiği oluşturma – adım adım rehber

Programlı olarak **Word'de pasta grafiği oluşturmanız** gerektiğinde, bu rehber Java ve Aspose.Words ile nasıl yapılacağını tam olarak gösterir. Grafiği eklemekten veri noktalarını eklemeye ve ilk dilimi döndürmeye kadar tam iş akışını öğreneceksiniz.

Bir `.docx` dosyasında doğrudan grafik oluşturmak, manuel kopyala‑yapıştır adımını ortadan kaldırır ve raporlar, faturalar veya panolar otomatikleştirmenizi sağlar. Ayrıca **grafiğe seri verisi ekleme** ve **pasta grafiği dilimini döndürme** konularını da ele alacağız.

## Word'de pasta grafiği oluşturma – genel bakış

Aspose.Words for Java, bir Word belgesine grafik nesnesi ekleyebilen akıcı bir `DocumentBuilder` API'si sunar. Seçtiğiniz grafik türü varsayılan düzeni belirler ve serileri, renkleri, açıları özelleştirebilir, hatta tek bir metod çağrısıyla halka (doughnut) şekline geçebilirsiniz.

### Neden Aspose.Words kullanmalı?

* **Microsoft Office gerekmez** – kütüphane herhangi bir sunucu ya da CI ortamında çalışır.  
* **Tam .docx uyumluluğu** – oluşturulan grafik, Word'de manuel olarak oluşturulanla aynı görünür.  
* **Tek dosya bağımlılığı** – sadece JAR dosyasını ekleyin, hazırsınız.

## Grafiğe seri verisi ekleme

Verisiz bir grafik sadece bir yer tutucudur. `Chart` nesnesi bir `Series` koleksiyonu sunar; her seri, dilimlere (pasta için) ya da noktalara (çizgi grafiği için) karşılık gelen sayısal değerlerin bir listesini tutar. Veri eklemek basittir:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**Kodun yaptığı:**  
* `chart.getSeries()` bir `List<ChartSeries>` döndürür.  
* `get(0)` ilk seriyi seçer; çünkü bir pasta grafiği tanım gereği yalnızca bir seri içerir.  
* `add(double)` bir veri noktası ekler. Değerler, grafik render edildiğinde %100’e toplamlanan yüzde değerlerine otomatik olarak dönüştürülür.

> **İpucu:** Veri kaynağınız üçten fazla kategori içeriyorsa, aynı şekilde değer eklemeye devam edin. Aspose.Words otomatik olarak ek dilimler oluşturur.

## Pasta grafiği dilimini döndürme

Bazen belirli bir dilimin, en önemli segmentin izleyiciye bakacak şekilde belirli bir açıdan başlamasını istersiniz. `setFirstSliceAngle(double)` metodu tüm grafiği döndürür, böylece ilk dilimin başlangıç konumu değişir:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

Açı, dikey eksenden saat yönünde derece cinsinden ölçülür. Varsayılan `0` değeri, ilk dilimi üstte konumlandırır. Bir dilimi vurgulamak ya da tasarım kılavuzuna uymak için değeri ayarlayın.

> **Sık sorulan soru:** *Döndürme veri sırasını etkiler mi?*  
> Hayır. Veri sırası aynı kalır; sadece görsel başlangıç konumu değişir.

## Tam Java örneği

Aşağıda, bir Word belgesi içinde pasta grafiği oluşturan, seri verisi ekleyen, dilimi döndüren ve dosyayı kaydeden, çalıştırmaya hazır tam bir program yer alıyor. Gerekli tüm importlar listelenmiştir; kodu herhangi bir IDE'ye kopyalayabilirsiniz.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Beklenen çıktı

* `output` klasöründe **PieChart.docx** adlı bir dosya oluşur.  
* Microsoft Word'de dosyayı açtığınızda üç dilimli ( %40, %30, %30 ) renkli bir pasta grafiği görürsünüz.  
* Grafik, saat yönünde 45° döndürülmüş olduğundan, ilk dilim dikey eksenin biraz sağında başlar.

## Yaygın hatalar ve en iyi uygulamalar

| Sorun | Neden ortaya çıkar | Çözüm |
|-------|--------------------|------|
| **Grafik boş görünüyor** | Belge, grafiğin tam olarak render edilmeden kaydedildi. | Tüm grafik değişikliklerinden **sonra** `doc.save()` çağırın. |
| **Dilime değerler %100’e ulaşmıyor** | Yüzdeyi temsil etmeyen ham sayılar eklemek ölçeklendirme sorunlarına yol açar. | Bölümün mantıklı parçalarını temsil eden değerler sağlayın veya yüzde hesaplamasını Aspose.Words’e bırakın. |
| **Döndürme etkisiz** | `ChartType.DOUGHNUT` kullanıp `holeSize` ayarlamadan döndürme efekti gizlenebilir. | Grafiği `PIE` olarak tutun veya açı ayarlamasından sonra `holeSize` değerini düzenleyin. |
| **Dosya yolu hataları** | Göreceli yollar Windows ve Linux'ta farklı çözülebilir. | Üretim kodunda `Paths.get("output", "PieChart.docx").toString()` ya da mutlak bir yol kullanın. |

### Üretim kullanımı için ipuçları

* **`DocumentBuilder`'ı yeniden kullanın** – aynı belgede birden fazla grafik eklemek için `insertChart` metodunu tekrar çağırabilirsiniz.  
* **Stil** – `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` ile yüzde değerlerini doğrudan grafiğe ekleyin.  
* **Performans** – Grafiği bir kez oluşturup (`chart.deepClone()`) birden çok yerde aynı grafiği klonlayarak kullanın.

## Pasta grafiği dilimini döndürme – ileri senaryolar

* **Dinamik açı** – En büyük dilimin üstte başlamasını sağlamak için açıyu veri üzerinden hesaplayın.  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Çoklu seriler** – Pasta grafiği normalde tek seri içerir, ancak Aspose.Words birden fazla seri ekleyerek yığılmış pasta grafikleri oluşturmanıza izin verir. Döndürme hâlâ yalnızca ilk seriye uygulanır.

## Sonuç

Artık Java kullanarak **Word'de pasta grafiği oluşturmayı**, **grafiğe seri verisi eklemeyi** ve **görsel vurgulama için pasta grafiği dilimini döndürmeyi** biliyorsunuz. Tam örnek, belge başlatmadan son `.docx` dosyasını kaydetmeye kadar tüm iş akışını gösteriyor; böylece grafik oluşturmayı herhangi bir otomatik raporlama hattına entegre edebilirsiniz.

### Sırada ne var?

* Otomasyon araç setinizi genişletmek için diğer grafik türlerini keşfedin (`ChartType.BAR`, `ChartType.LINE`).  
* Her alıcı için kişiselleştirilmiş raporlar üretmek üzere **mail merge** ile grafik oluşturmayı birleştirin.  
* Kurumsal markanıza uyum sağlamak için **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`) ile derinlemesine çalışın.

Farklı veri setleri, açı değerleri ve grafik stilleriyle denemeler yapmaktan çekinmeyin. Kodlamanın tadını çıkarın!

## Bir sonraki öğrenmeniz gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımları keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}