---
category: general
date: 2026-11-15
description: Aspose.Words for Java ile bir Word belgesine pasta grafiği eklemeyi öğrenin.
  Donut dönüşümü, patlamış dilim ve tam kod örneği içerir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: tr
lastmod: 2026-11-15
og_description: Aspose.Words for Java kullanarak bir Word belgesine pasta grafiği
  ekleyin. Bu öğreticide bir dilimi patlatma ve grafiği halka (doughnut) grafiğine
  dönüştürme gösterilmektedir.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Java ile bir Word belgesine pasta grafiği ekleyin – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Java kullanarak bir Word belgesine pasta grafiği ekleme
url: /tr/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word belgesine pasta grafiği ekleme – tam Java rehberi

Programlı olarak **Word belgesine pasta grafiği eklemeniz** gerekiyorsa, bu öğretici Aspose.Words for Java ile bunu nasıl yapacağınızı adım adım gösterir. Tam iş akışını göreceksiniz: bir DOCX dosyasını yükleme, bir pasta grafiği oluşturma, ilk dilimi patlatma ve bir delik boyutu ayarlayarak grafiği halka (doughnut) grafiğine dönüştürme.

Kılavuz ayrıca birden fazla seri ekleme, renk özelleştirme ve zaten grafik içeren belgelerle çalışma gibi yaygın varyasyonları da kapsar; böylece kodu otomatik raporlama veya dinamik sunumlar gibi gerçek dünya projelerine uyarlayabilirsiniz.

## Önkoşullar

Başlamadan önce şunların kurulu olduğundan emin olun:

* Java 17 veya daha yeni bir sürüm (kod JDK 11+ ile de derlenebilir)
* Maven 3.6+ veya bağımlılık yönetimi için Gradle
* Aspose.Words for Java lisansı (ücretsiz deneme sürümü test için yeterlidir)
* Java sözdizimi ve Maven proje yapısı hakkında temel bilgi

## Adım 1: Maven projesini kurun ve Aspose.Words’u içe aktarın

Yeni bir Maven projesi oluşturun (veya mevcut bir projeye ekleyin) ve Aspose.Words bağımlılığını ekleyin:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **İpucu:** Gradle kullanıyorsanız eşdeğer satır `implementation 'com.aspose:aspose-words:24.9'` şeklindedir.

Bu bağımlılık, grafiklerle çalışmak için ihtiyaç duyacağınız `Document`, `Chart` ve `ChartType` sınıflarını getirir.

## Adım 2: Hedef belgeyi yükleyin

Mevcut bir `.docx` dosyasından başlayabilir veya yeni boş bir belge oluşturabilirsiniz. Aşağıdaki örnek, `src/main/resources` klasöründe bulunan `input.docx` adlı bir şablonu yüklüyor.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Dosya mevcut değilse, `new Document()` çağrısı bir dosya adı belirtilmediğinde Aspose.Words otomatik olarak yeni boş bir belge oluşturur.

## Adım 3: Pasta grafiği oluşturun ve belgeye ekleyin

Aspose.Words bir grafiği, bir paragrafın görünebileceği herhangi bir yere yerleştirilebilen bir şekil olarak ele alır. Aşağıdaki kod bir **pasta grafiği** oluşturur, tek bir veri serisi ekler ve grafiği ilk paragraftan sonra ekler.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Bu adımın önemi:**  
* `ChartType.PIE`, Aspose.Words’a geleneksel bir pasta grafiği çizmeyi söyler.  
* Hem kategori etiketleri hem de sayısal değerler içeren bir seri eklemek dilimleri otomatik olarak doldurur.  
* Grafiği bir `Paragraph` nesnesinin çocuğu olarak eklemek, belgenin akışını bozmadan kalmasını sağlar.

## Adım 4: İlk dilimi patlatıp vurgulayın

*Patlatılmış dilim*, belirli bir veri noktasına dikkat çeker. API, bir `ChartSeries` nesnesinde `setExplode(boolean)` metodunu sunar. İlk seriye (indeks 0) bu metodu uygulamak, ilk dilimin dışarı çıkmasını sağlar.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Sık sorulan soru:** *Birden fazla serim olsaydı ne yapmalıyım?*  
> Belirli bir seriyi indeksine göre hedefleyebilirsiniz; örneğin ikinci seri için `pieChart.getSeries().get(1).setExplode(true)` kullanabilirsiniz.

## Adım 5: Delik boyutunu ayarlayarak pasta grafiğini halka grafiğine dönüştürün

Halka grafiği, ortası boş bir pasta grafiğidir. Aspose.Words, delik boyutunu grafiğin yarıçapının yüzdesi olarak tanımlamanıza izin verir.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

`setHoleSize` metodu **0** (normal pasta) ile **100** (tamamen boş) arasında değer alır. **30‑40** civarında bir değer, görsel olarak dengeli bir halka sağlar.

## Adım 6: Kaydedin ve sonucu doğrulayın

Tüm değişikliklerden sonra belgeyi kaydedin. Aşağıdaki satır dosyayı `output` klasörüne yazar.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Beklenen çıktı

`final-pie-doughnut.docx` dosyasını Microsoft Word’de açın:

* İlk paragrafın bulunduğu yerde bir halka grafiği görünür.
* “Apples” dilimi patlatılmış (diğer dilimlerden hafifçe ayrılmış) olarak gösterilir.
* Grafik, *Apples*, *Bananas*, *Cherries*, *Dates* etiketli dört dilim ve sağladığınız yüzde değerlerini gösterir.

PDF çıktısı isterseniz, `SaveFormat` değerini `SaveFormat.PDF` olarak değiştirin.

## Kenar durumları ve varyasyonların ele alınması

### Birden fazla seri ekleme

Birden çok seri (ör. yığılmış halka) gerekiyorsa, bunları ardışık olarak ekleyin:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Özel renkler

Her dilime renk atamak için `ChartDataPoint.setFillFormat().setSolidFillColor()` metodunu kullanabilirsiniz:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Mevcut bir grafik ile çalışma

Belge zaten bir grafik içeriyorsa ve sadece onu değiştirmek istiyorsanız, grafik şeklinin konumunu bulun:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Lisans yönetimi

Aspose.Words üretim ortamında bir lisans gerektirir. `Aspose.Words.lic` dosyanızı sınıf yoluna (classpath) koyun ve uygulama başlangıcında yükleyin:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Lisans ayarlanmamışsa, oluşturulan belgeye bir filigran eklenir.

## Tam, çalıştırılabilir örnek

Aşağıda, tartışılan tüm adımları birleştiren tam Java sınıfı yer alıyor. `src/main/java/com/example/AddPieChart.java` içine kopyalayın ve `mvn compile exec:java` komutunu çalıştırın.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

Programı çalıştırdığınızda daha önce tarif edilen halka grafiği üretilir. `categories`, `values` veya `holeSize` değerlerini verinize göre ayarlayın.

## Sonuç

Artık Java ve Aspose.Words kullanarak **Word belgesine pasta grafiği eklemeyi** biliyorsunuz. Öğreticide belge yükleme, pasta grafiği oluşturma, bir dilimi patlatma, grafiği halka grafiğine dönüştürme ve birden fazla seri, özel renkler ve mevcut grafikler gibi yaygın varyasyonları ele alma konuları ele alındı. Bu temelle otomatik raporlama araçları, dinamik sunumlar oluşturabilir veya zengin görselleştirmeleri doğrudan Word dosyalarına gömebilirsiniz.

### Bir sonraki keşifleriniz

* **add bar chart to Word document** – benzer adımlar ancak `ChartType.BAR` kullanılır.  
* **customize chart legends and titles** – `pieChart.getTitle().setText("...")` ve `pieChart.getLegend().setPosition(LegendPosition.RIGHT)` metodlarını kullanın.  
* **export the Word document as PDF** – dağıtıma hazır dosyalar için `SaveFormat` değerini `PDF` olarak değiştirin.  
* **populate chart data from a database** – sabit dizileri JDBC sorgu sonuçlarıyla değiştirin.

Farklı grafik tipleri, veri kaynakları ve stil seçenekleriyle denemeler yapmaktan çekinmeyin. Kodlamanın tadını çıkarın!

## Bir Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayalı olarak yakın konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}