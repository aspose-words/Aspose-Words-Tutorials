---
category: general
date: 2026-11-22
description: Java'da pasta grafiği oluşturun ve grafik boyutunu ayarlamayı, veri etiketleri
  eklemeyi, yüzde göstermeyi ve net bir görsel etki için ilk dilimi döndürmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: tr
lastmod: 2026-11-22
og_description: Java'da pasta grafiği oluşturun, ardından grafik boyutunu ayarlayın,
  veri etiketlerinde yüzde değerlerini gösterin ve ilk dilimi döndürün—hepsi tek bir
  çalıştırılabilir örnekte.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Java'da özel boyut, etiket ve döndürme ile pasta grafiği oluştur
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Java'da özel boyut, veri etiketleri ve döndürme ile pasta grafiği oluştur
url: /tr/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java'da Özel Boyut, Veri Etiketleri ve Döndürme ile Pasta Grafiği Oluşturma

Java'da **create pie chart** ihtiyacınız varsa, bu kılavuz sizi tüm süreç boyunca yönlendirecek. **set chart size**, **show percentages pie chart**, **data labels pie chart** eklemeyi ve **rotate pie chart slice** yaparak ilk dilimin 45 derece açıyla başlamasını öğreneceksiniz.

Örnek, PowerPoint dosyalarını manipüle etmek için yaygın olarak kullanılan bir kütüphane olan **Aspose.Slides for Java**'ı kullanıyor. Aynı kavramlar diğer grafik kütüphanelerine de uygulanabilir; yalnızca API çağrılarını araç setinizdeki eşdeğerleriyle değiştirin.

## Önkoşullar

* Java 17 veya daha yeni bir sürüm yüklü  
* Bağımlılık yönetimi için Maven 3.8+ (veya Gradle)  
* Java sözdizimi hakkında temel bir anlayış  
* Aspose.Slides for Java ikili dosyasına erişim (resmi siteden ücretsiz deneme sürümünü edinebilirsiniz)

Bağımlılığı `pom.xml` dosyanıza ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Pasta grafiği oluşturma – tam örnek

Aşağıdaki program, özel boyutlu, yüzde veri etiketli ve ilk dilimi döndürülmüş bir pasta grafiği içeren bir PowerPoint slaytı oluşturur.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Her adımın önemi

| Adım | Amaç | Anahtar kelimelerle ilişkisi |
|------|------|------------------------------|
| **Grafik ekle** | **Create pie chart** – görseli oluşturacak temel nesne. | *create pie chart* gereksinimini doğrudan karşılar. |
| **Boyutları ayarla** | `addChart(..., 400, 300)` çağrısı **set chart size**'ı gösterir. | Genişliği (400 px) ve yüksekliği (300 px) kontrol eder. |
| **Yüzdeleri göster** | `setShowPercentage(true)` grafiği her dilimde **show percentages pie chart** yapar. | Kullanıcılar genellikle ham değerler yerine yüzde değerlerine ihtiyaç duyar. |
| **Veri etiketleri ekle** | `DataLabelFormat` yapılandırması istenen görünürlükte **data labels pie chart** ekler. | Etiketler okunabilirliği artırır ve özelleştirilebilir. |
| **Dilimi döndür** | `setFirstSliceAngle(45)` grafiği döndürerek ilk dilimin 45 derece açıyla başlamasını sağlar, **rotate pie chart slice** gereksinimini karşılar. | Belirli bir dilimin görsel vurgusunu artırır. |

## Adım adım açıklama

### 1. Bir pasta grafiği ekleyin ve grafik boyutunu ayarlayın

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*`addChart` yöntemi grafiği oluşturur ve aynı anda **set chart size**'ı 400 × 300 puana ayarlar.*  
Farklı bir boyuta ihtiyacınız varsa, son iki argümanı değiştirin.

### 2. Grafiği veri ile doldurun

Demo üç kategori ve tek bir seri ekler. Gerektiğinde sabit kodlanmış sayıları bir veritabanı, CSV veya kullanıcı girdisinden gelen verilerle değiştirin.

### 3. Her dilimde yüzde değerlerini göster

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*`setShowPercentage(true)`'ı etkinleştirmek, grafiğin **show percentages pie chart** otomatik olarak her dilimin toplam içindeki payını hesaplamasını sağlar.*

### 4. Ayrıntılı veri etiketleri ekleyin

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Diğer etiket seçeneklerini (`setShowValue`, `setShowSeriesName` vb.) değiştirerek **add data labels pie chart** deneyimini özelleştirebilirsiniz.

### 5. İlk dilimi döndürün

```java
chart.setFirstSliceAngle(45);
```

*`setFirstSliceAngle(45)` çağrısı **rotate pie chart slice** yaparak ilk segmentin 45 derece açıyla başlamasını sağlar ve öne çıkar.*

### 6. Sonucu kaydedin ve görüntüleyin

Programı çalıştırdığınızda `output/PieChartDemo.pptx` oluşturulur. Son pasta grafiğini görmek için PowerPoint veya uyumlu bir görüntüleyicide açın:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Özel boyut, yüzde etiketleri ve döndürülmüş bir ilk dilim içeren oluşturulmuş bir pasta grafiğinin ekran görüntüsü"}

Yukarıdaki görüntü **create pie chart** sonucunu gösterir, boyut, etiketler, yüzde değerleri ve döndürmenin doğru uygulandığını doğrular.

## Yaygın varyasyonlar ve uç durumlar

| Durum | Ayarlama |
|-------|----------|
| **Farklı grafik boyutları** | `addChart` içindeki genişlik/yükseklik parametrelerini değiştirin. |
| **Çoklu seriler** | Ek `IChartSeries` nesneleri ekleyin; her seri kendi etiket ayarlarına sahip olabilir. |
| **Özel etiket formatı** | `series.getDataLabelFormat().setNumberFormat("0.0%")` kullanarak ondalık basamakları kontrol edin. |
| **Başka bir açıya döndürme** | `setFirstSliceAngle`'a herhangi bir tam sayı (0‑360) gönderin. |
| **Görüntü olarak dışa aktar** | Kaydettikten sonra raster bir sürüm için `chart.writeAsSvg(outPath)` veya `chart.writeAsPng(outPath)` çağırın. |

> **Pro tip:** Bir döngüde birçok grafik oluşturmayı planlıyorsanız, aynı `Presentation` nesnesini yeniden kullanın ve yalnızca grafik verilerini değiştirin. Bu, bellek yükünü azaltır ve işleme hızını artırır.

## Sonuç

Artık Java'da **create pie chart**, **set chart size**, **show percentages pie chart**'ı etkinleştirme, **add data labels pie chart** ekleme ve **rotate pie chart slice** yaparak daha iyi görsel vurgu elde etme konusunda bilgi sahibisiniz. Tam ve çalıştırılabilir örnek, baştan sona, başlangıçtan son PowerPoint dosyasını kaydetmeye kadar her adımı gösterir.

### Sıradaki adımlar?

* Aynı `ChartType` enum'ını kullanarak diğer grafik türlerini (Bar, Line, Area) keşfedin.  
* Gösterge tabloları için tek bir slaytta birden fazla grafiği birleştirin.  
* Web uygulamalarında kullanmak üzere grafikleri PNG veya SVG olarak dışa aktarın.  

Renkler, lejandlar ve animasyon efektleriyle denemeler yapmaktan çekinmeyin—veri görselleştirmeleriniz yalnızca hayal gücünüzle sınırlıdır. İyi grafikler!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Word'de pasta grafiği ekleme – veri etiketi yüzde ekleme](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Java'da pasta dilimini patlatma – Aspose.Words grafik öğreticisi](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Java'da Pasta Grafiği Ekle – Patlatma, Döndürme ve Dilimleri Vurgulama](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}