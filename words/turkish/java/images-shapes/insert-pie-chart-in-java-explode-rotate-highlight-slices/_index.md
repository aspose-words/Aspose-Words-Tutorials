---
category: general
date: 2026-07-20
description: Java’da adım adım kılavuzla pasta grafiği ekleyin. Dilimi nasıl patlatacağınızı,
  pasta grafiğini nasıl döndüreceğinizi, pasta grafiği dilimini nasıl vurgulayacağınızı
  ve dilimi nasıl özelleştireceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: tr
lastmod: 2026-07-20
og_description: Java'da pasta grafiği ekleyin ve dilimi patlatma, grafiği döndürme,
  dilimi vurgulama ve dilimi özelleştirerek şık görsel raporlar oluşturmayı öğrenin.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Java'da Pasta Grafiği Ekle – Patlat, Döndür ve Vurgula
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Java'da Pasta Grafiği Ekle – Dilimleri Patlat, Döndür ve Vurgula
url: /tr/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da Pasta Grafiği Ekle – Dilimi Patlat, Döndür ve Vurgula

Java raporuna **pasta grafiği eklemek** gerektiğinde ama tek bir dilimin nasıl öne çıkarılacağını bilemediğiniz oldu mu? Tek başınıza değilsiniz. İster bir gösterge paneli oluşturuyor olun, fatura üretiyor olun ya da sadece anket sonuçlarını görselleştiriyor olun, iyi tasarlanmış bir pasta grafiği ham sayıları anında anlaşılır bir içgörüye dönüştürebilir.

Bu öğreticide, **pasta grafiği ekleme**, **dilimi patlatma**, **pasta grafiğini döndürme** ve hatta **pasta dilimini vurgulama** konularını gösteren, çalıştırmaya hazır tam bir örnek göreceksiniz. Sonunda, popüler *JFreeChart* kütüphanesini (veya benzer bir API'yi) kullanan herhangi bir Java projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız.

## Prerequisites

- Java 17 veya daha yeni (kod eski sürümlerle de derlenir, ancak kısalık için modern `var` sözdizimini kullanacağız).  
- `org.jfree:jfreechart` bağımlılığını çekmek için Maven veya Gradle.  
- Java sınıfları ve bir grafik oluşturucusunun kavramı hakkında temel bir anlayış.  

Eğer bir Maven projesine hiç kütüphane eklemediyseniz, bunu `pom.xml` dosyanıza ekleyin:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

Hepsi bu kadar—ekstra kurulum gerekmez.

## Step 1: Insert Pie Chart – Create the Builder and Chart Object

İlk olarak: grafik üretmeyi bilen bir *builder* (fabrika gibi) gerekir. JFreeChart'ta bu işi `ChartFactory` yapar.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

Neden veri kümesiyle başlıyoruz? Çünkü grafik, sayılar etrafında dönen bir görsel sarmalayıcıdır. **pasta grafiği ekleyerek** burada zaten 400 × 300 boyutunda bir tuval (canvas) elde ediyoruz; boyut daha sonra görüntüye render edildiğinde uygulanacak.

## Step 2: How to Explode Slice – Emphasize the First Segment

Grafik artık mevcut, ilk dilimin öne çıkmasını sağlayalım. Bir dilimi patlatmak, onu çemberden biraz uzaklaştırarak okuyucunun dikkatini çeker.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Metod adında **how to explode slice** ifadesini kullandığımıza dikkat edin; bu, amacın net olmasını sağlar. `setExplodePercent` metodu bir anahtar (dilim etiketi) ve bir yüzde alır, böylece “patlatma” mesafesini ihtiyaca göre ayarlayabilirsiniz.

## Step 3: How to Rotate Pie Chart – Change the Starting Angle

Varsayılan bir pasta grafiği 12:00 konumundan başlar. Bazen ilk dilimin başka bir konumda başlamasını istersiniz—belki bir tasarım taslağıyla hizalamak ya da başka bir grafikle eşleştirmek için.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

`rotateChart(chart, 45)` çağrısı, tüm pastayı döndürerek “Apples” diliminin 45 derece açıyla başlamasını sağlar; bu tam da **how to rotate pie chart** gereksiniminin istediği şeydir.

## Step 4: Highlight Pie Chart Slice – Custom Colors and Labels

Patlatmanın ötesinde, bir dilime benzersiz bir renk ya da kalın bir etiket vererek gerçekten **highlight pie chart slice** yapmak isteyebilirsiniz.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Burada, boyasını ve etiket stilini değiştirerek **customize pie chart slice** yaptık. Rengi ya da yazı tipini marka paletinize uygun şekilde değiştirmekten çekinmeyin.

## Step 5: Render the Chart to an Image (Optional but Handy)

Çoğu gerçek dünya uygulaması grafiği PNG, JPEG ya da hatta PDF olarak ihtiyaç duyar. Aşağıda grafiği bir dosyaya yazmanın hızlı bir yolu var.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

Tam akışı çalıştırdığınızda aşağıdaki gibi bir 400 × 300 PNG oluşur:

![Insert pie chart example](image.png){: alt="Patlatılmış ve döndürülmüş dilim gösteren pasta grafiği örneği"}

## Full Working Example

Hepsini bir araya getirerek, kopyalayıp yeni bir Java sınıfına yapıştırıp çalıştırabileceğiniz bir `main` metodu:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Expected Output

Programı çalıştırdığınızda **fruit-pie.png** adlı bir dosya oluşturulur. Açın ve şunları göreceksiniz:

- “Fruit Distribution” başlıklı 400 × 300 bir pasta grafiği.  
- “Apples” dilimi %15 oranında dışarı patlatıldı.  
- Tüm grafik döndürülerek “Apples” diliminin 45 derece konumda başlaması sağlandı.  
- Patlatılmış  

## What Should You Learn Next?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalarla tam çalışan kod örnekleri içerir.

- [Java için Aspose.Words kullanarak sütun grafiği oluşturma](/words/english/java/document-conversion-and-export/using-charts/)
- [Scatter Grafiği Ekle](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Area Grafiği Ekle](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}