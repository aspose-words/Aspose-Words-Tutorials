---
category: general
date: 2026-08-07
description: Aspose.Words kullanarak Java'da pasta dilimini nasıl patlatılır. Pasta
  grafiğine lider çizgileri eklemeyi, Word grafiği oluşturmayı ve pasta grafiği dilimlerini
  özelleştirmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: tr
lastmod: 2026-08-07
og_description: Java'da Aspose.Words ile pasta dilimini dışarı çıkarmak. Bu rehber,
  pasta grafiğine lider çizgileri eklemeyi, Word grafikleri oluşturmayı ve net görsel
  etki için pasta dilimlerini özelleştirmeyi gösterir.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Java'da pasta dilimini nasıl ayırılır – Aspose.Words rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Java'da pasta dilimini nasıl patlatılır – Aspose.Words grafik öğreticisi
url: /tr/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da pasta dilimini patlatma – Aspose.Words grafik öğreticisi

Java kullanarak bir Word belgesinde **pasta dilimini nasıl patlatacağınızı** öğrenmeniz gerekiyorsa, bu öğretici ihtiyacınızı karşılayacak. Ayrıca **pasta grafiklerine lider çizgileri eklemeyi**, **java create word chart** nesnelerini ve **pasta grafik dilimlerini özelleştirmeyi** göstereceğiz, böylece profesyonel bir sonuç elde edersiniz. Bu rehberin sonunda, herhangi bir Java projesine ekleyebileceğiniz tam, çalıştırılabilir bir örnek elde edeceksiniz.

![Java’da pasta dilimini patlatma – Aspose.Words grafik](/images/pie-chart-exploded.png)

## Önkoşullar

* Java Development Kit (JDK) 8 veya üzeri.
* Bağımlılık yönetimi için Maven veya Gradle.
* Aspose.Words for Java lisansı (ücretsiz deneme sürümü öğrenme amaçları için çalışır).
* Java sözdizimi ve nesne‑yönelimli kavramlara temel aşinalık.

> **İpucu:** Aspose.Words ücretsiz deneme sürümü sunsa da, bir lisans satın almak oluşturulan belgelerden değerlendirme filigranını kaldırır.

## Bu öğreticide neler ele alınıyor

* Sıfırdan yeni bir Word belgesi oluşturma.  
* `DocumentBuilder` kullanarak bir **pie chart** ekleme.  
* **pie slice** patlatma ile bir veri noktasını vurgulama.  
* **pie** grafiğine daha net etiketleme için lider çizgileri ekleme.  
* Dilimin görünümünü, renkler ve kenarlıklar gibi, özelleştirme.  
* Belgeyi diske kaydetme ve sonucu doğrulama.

---

## Aspose.Words ile Java’da pie slice patlatma

İlk adım, grafik nesnesini ayarlamak ve istenen dilimi patlatmaktır. Aspose.Words, grafiği `Shape` sınıfı aracılığıyla sunar ve her dilim bir `ChartPoint`’tir. `Explosion` özelliğini ayarlayarak dilimin ne kadar dışarı doğru hareket edeceğini kontrol edersiniz.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Neden çalışıyor:**  
`setExplosion(20)` grafik motoruna dilimi grafiğin merkezinden 20 puan uzaklaştırmasını söyler. Değer görecelidir; daha büyük sayılar daha dramatik bir etki yaratır. Dizini değiştirerek (`get(1)`, `get(2)`, …) istediğiniz herhangi bir dilimi patlatabilirsiniz.

## Daha net etiketler için pie’e lider çizgileri ekleme

Lider çizgileri, bir dilimin etiketini kenarına bağlar; bu, dilimler patlatıldığında veya grafikte birçok küçük bölüm olduğunda özellikle faydalıdır. `setLeaderLines(true)` çağrısı bu özelliği tüm seri için etkinleştirir.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Neden lider çizgilere ihtiyacınız var:**  
Bir dilim patlatıldığında, varsayılan etiket diğer öğelerle çakışabilir. Lider çizgileri, dilimden metin kutusuna kısa bir çizgi çizerek etiketin okunabilirliğini korur.

## Java’da Word grafik oluşturma – veri serileri ekleme

Verisiz bir grafik pek işe yaramaz. Seriyi kategoriler ve değerlerle doldurmalısınız. Aşağıda pazar payını temsil eden üç kategori ekliyoruz.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Açıklama:**  
`ChartSeries` hem kategorileri (dilim adları) hem de sayısal değerleri tutar. `ShowCategoryName` ve `ShowPercentage` özelliklerini etkinleştirmek, grafiği kendi kendine açıklayıcı hâle getirir; bu da daha önce eklediğimiz lider çizgilerle güzel bir uyum sağlar.

## Patlatmanın ötesinde pie chart dilimlerini özelleştirme

Bir dilimi patlatmanın ötesinde, genellikle renkleri, kenarlıkları ayarlamak veya bir dilimi tamamen gizlemek istersiniz. Aşağıdaki kod parçacığı üç yaygın özelleştirmeyi gösterir:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Neden dilimleri özelleştirirsiniz:**  
Özel renkler, grafiğin kurumsal marka ile uyumlu olmasını sağlar, kenarlıklar ise basılı sayfalarda okunabilirliği artırır. Bir dilimi gizlemek, veri modelini korurken görsel çıktıda bir kategoriyi geçici olarak çıkarmak istediğinizde faydalıdır.

## Belgeyi kaydetme ve sonucu doğrulama

Son olarak, belgeyi diske yazın. Oluşturulan `.docx` dosyasını Microsoft Word, LibreOffice veya formatı destekleyen herhangi bir görüntüleyicide açabilirsiniz.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Beklenen çıktı:**  
`PieChartDemo.docx` dosyasını açtığınızda, ilk dilimin (Product A) dışarı doğru patlatıldığını, lider çizgilerin her dilimden etiketine doğru işaret ettiğini ve dilimlerin özel yeşil, mavi ve turuncu renklerde göründüğünü göreceksiniz. Gizli dilim (Product C) görünmeyecek, ancak yüzde değerleri hâlâ %100’e toplamaktadır çünkü veri grafik serisinde kalmaktadır.

---

## Tam, çalıştırılabilir örnek

Aşağıda, Aspose.Words bağımlılığını projenize ekledikten sonra kopyalayıp yapıştırıp çalıştırabileceğiniz tam program yer almaktadır.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Bağımlılık (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for Java kullanarak sütun grafiği oluşturma](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words Java ile Word Belgelerini Yükleme: Kapsamlı Rehber](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Aspose.Words for Java’da DocumentBuilder kullanarak form alanları oluşturma ve içerik ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}