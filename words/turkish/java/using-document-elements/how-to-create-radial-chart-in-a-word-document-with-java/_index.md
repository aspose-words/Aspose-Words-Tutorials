---
category: general
date: 2026-09-18
description: Java kullanarak bir Word belgesinde radyal grafik oluşturmayı, grafik
  veri etiketlerini eklemeyi ve tam bir kod örneğiyle seri verilerini eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: tr
lastmod: 2026-09-18
og_description: Java kullanarak bir Word belgesinde radyal grafik oluşturun, grafik
  veri etiketlerini ekleyin ve tek bir öğreticide seri verilerini ekleyin.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Java ile Word’de radyal grafik oluşturma – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Java ile bir Word belgesinde radyal grafik nasıl oluşturulur
url: /tr/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java ile Word belgesinde radyal grafik nasıl oluşturulur

## İhtiyacınız olanlar

* Java 17 veya daha yeni  
* Aspose.Words for Java (version 23.12 veya daha yeni)  
* Maven/Gradle bağımlılıklarını çözebilen bir IDE veya derleme aracı  

Bu ön koşullar yüklü olduğunda örneği ek yapılandırma gerektirmeden çalıştırabilirsiniz.

## Word belgesinde radyal grafik oluşturma

İlk adım, grafiği barındıracak boş bir Word dosyası oluşturmaktır. Boş bir belge temiz bir tuval sağlar ve istenmeyen stillerden kaçınır.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` tüm .docx dosyasını temsil eder, `DocumentBuilder` ise paragraf, tablo ve grafik gibi öğeleri eklemek için yöntemler sağlar.

## Grafiği ekleme

Sonra grafiği kendisini ekliyorsunuz. `insertChart` yöntemi bir grafik nesnesi oluşturur ve bunu builder'ın mevcut imleç konumuna yerleştirir.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Polar grafik, veri noktalarını merkezi bir eksen etrafında gösterir; bu, döngüsel bilgileri göstermek için idealdir. Boyutlar nokta cinsinden ifade edilir (1 pt ≈ 1/72 inç).

## Grafiğe seri verileri ekleme

Seri verisi olmayan bir grafik boştur. Bir seriyi manuel olarak ekleyebilir veya bir veri kaynağına bağlayabilirsiniz. Aşağıdaki örnek, üç veri noktasına sahip tek bir seri ekler.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` bir seri adı, kategori etiketlerinin bir listesi ve karşılık gelen sayısal değerlerin bir listesini alır. Bu bloğu tekrarlayarak ek seriler ekleyebilirsiniz (`addSeriesData`).

## İlk seriye grafik veri etiketleri ekleme

Veri etiketleri, noktalara üzerine gelmeden grafiği okunabilir kılar. Aşağıdaki satır, ilk seri için değer etiketlerini açar.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

`showValue` değerini `true` olarak ayarlamak, her noktanın değerini doğrudan grafikte gösterir. Aynı `DataLabelFormat` nesnesi üzerinden kategori adlarını, yüzdeleri veya lider çizgilerini de etkinleştirebilirsiniz.

## Word dosyasını kaydetme

Grafik yapılandırıldıktan sonra belgeyi diske yazın. Uygulamanızın erişebileceği bir konum seçin.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

`RadialChart.docx` dosyası artık veri etiketlerine sahip tam işlevsel bir radyal grafik içeriyor.

## Tam çalışan örnek

Aşağıda, kopyalayıp derleyip çalıştırabileceğiniz bağımsız bir program bulunmaktadır. Boş bir Word belgesi oluşturulmasından veri etiketli bir radyal grafiğin kaydedilmesine kadar tam iş akışını gösterir.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Beklenen sonuç**

`output/RadialChart.docx` dosyasını Microsoft Word'de açtığınızda, *Quarterly Sales* başlıklı bir radyal grafik göreceksiniz. Her nokta, işaretçinin yanında sayısal değerini (ör. “15000”) gösterir.

## Yaygın varyasyonlar ve uç durumlar

| Durum | Önerilen değişiklik |
|-----------|--------------------|
| Farklı bir grafik türüne ihtiyacınız var | `ChartType.POLAR` yerine herhangi bir diğer `ChartType` enum değerini (ör. `ChartType.COLUMN`) kullanın. |
| Grafiğin harici bir Excel aralığı kullanması gerekiyor | Grafiği oluşturduktan ve çalışma kitabını yükledikten sonra `chart.setDataRange("Sheet1!A1:B5")` kullanın. |
| Lejandı gizlemek istiyorsunuz | `chart.getLegend().setVisible(false);` |
| Belgenin PDF olarak kaydedilmesi gerekiyor | `doc.save("RadialChart.pdf");` çağrısı – Aspose.Words grafiği otomatik olarak dönüştürür. |

## Profesyonel ipuçları

* **Builder'ı yeniden kullanın** – `builder.insertChart` metodunu tekrar tekrar çağırarak aynı belgede birden fazla grafik ekleyebilirsiniz.  
* **Performans** – Çok sayıda grafik oluştururken, tek bir `DocumentBuilder` örneği oluşturup yeniden kullanarak nesne tahsis yükünü azaltabilirsiniz.  
* **Stil** – Grafik görünümü (renkler, çizgi kalınlığı) `Chart` nesnesinin `getSeries().get(i).getFormat()` metodlarıyla kontrol edilir. Kurumsal marka ile uyumlu olması için bu ayarlarla deneyler yapın.  

## Sonuç

Artık Java ile bir Word belgesinde radyal grafik nasıl oluşturulur, seri verileri nasıl eklenir ve dosyayı kaydetmeden önce grafik veri etiketlerinin nasıl ekleneceğini biliyorsunuz. Tam örnek, ek seriler, özel stiller veya alternatif çıktı formatlarıyla genişletilebilir.

Harici veri kaynaklarından **grafik ekleme**, önceden tanımlı şablonlarla **boş word** belgeleri oluşturma ve veritabanlarından dinamik olarak **seri verisi ekleme** gibi ilgili konuları keşfedin. Farklı grafik türleriyle deney yaparak verilerinizi en iyi şekilde ileten görselleştirmeyi bulun.

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words for Java kullanarak sütun grafiği nasıl oluşturulur](/words/english/java/document-conversion-and-export/using-charts/)
- [Java ile Word Belgesi Oluşturma – Gölge Efektiyle Dikdörtgen Şekil Ekleme](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Grafikte Veri Etiketleri için Varsayılan Seçenekleri Ayarlama](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}