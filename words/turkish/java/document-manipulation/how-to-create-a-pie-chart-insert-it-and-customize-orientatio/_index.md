---
category: general
date: 2026-11-25
description: Java’da pasta grafiği oluşturmayı, pasta grafiğini bir Word belgesine
  eklemeyi, pasta dilimini patlatmayı ve grafik yönelimini değiştirmeyi net kod örnekleriyle
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: tr
lastmod: 2026-11-25
og_description: Java'da bir pasta grafiği oluşturun, pasta grafiğini bir belgeye ekleyin,
  pasta dilimini patlatın ve adım adım kodla grafik yönünü değiştirin.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Java’da pasta grafiği oluşturma – ekle, dilimi patlat ve döndür
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Java'da bir pasta grafiği oluşturma, ekleme ve yönünü özelleştirme
url: /tr/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java'da pasta grafiği oluşturma, ekleme ve yönünü özelleştirme

Bir Word belgesinde **pasta grafiği oluşturmanız** gerektiğinde, bu kılavuz tam olarak nasıl yapılacağını gösterir. **Pasta grafiği ekleme**, vurgulamak için bir dilimi patlatma ve basit bir döndürme ile **grafik yönünü değiştirme** işlemlerini göreceksiniz.

Bu öğretici, Aspose.Words for Java kütüphanesinin kurulumu’dan döndürülmüş ve patlatılmış bir pasta grafiği gösteren son `.docx` dosyasının üretilmesine kadar ihtiyacınız olan her şeyi kapsar. Harici bir belgeye ihtiyaç yok; sadece adımları izleyin ve kodu çalıştırın.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* Java 17 veya daha yeni bir sürüm.
* Bağımlılıkları yönetmek için Maven ya da Gradle.
* Geçerli bir Aspose.Words for Java lisansı (veya ücretsiz değerlendirme modu).

`pom.xml` (Maven) ya da `build.gradle` (Gradle) dosyanıza Aspose.Words bağımlılığını ekleyin. Maven için örnek:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Pro ipucu:** Kütüphane sürümünü güncel tutun; yazı zamanı itibarıyla (24.10) en son sürüm, grafik render’ı için hata düzeltmeleri içerir.

## Adım 1: Pasta grafiği oluşturma ve belgeye ekleme

İlk adım **pasta grafiği** nesnelerini oluşturup bir Word dosyasına gömmektir. Aşağıdaki kod basit bir belge oluşturur, bir grafik yer tutucusu ekler ve 400 × 300 piksel boyutunda bir pasta grafiği ekler.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Neden önemli:** `builder.insertChart` bir grafik yer tutucusu oluşturur; Aspose.Words belge kaydedildiğinde bunu otomatik olarak OOXML grafikine dönüştürür. `ChartType.PIE` argümanı, kütüphaneye bir pasta grafiği render etmesini söyler ve **pasta grafiği ekleme** gereksinimini karşılar.

## Adım 2: Bir dilimi patlatıp vurgulama

Bir dilimi patlatmak, belirli bir veri noktasına dikkat çeker. Aşağıdaki satır, ilk dilimi (indeks 0) 10 puan kadar patlatır:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

İndeksi değiştirerek farklı bir dilimi hedefleyebilir veya patlatma mesafesini daha hafif bir etki için ayarlayabilirsiniz. Dilimi patlatmak, Aspose.Words içinde **pasta dilimini patlatma** işleminin standart yoludur.

## Adım 3: Grafiği döndürerek yönünü değiştirme

Grafiği döndürmek, yeni bir görsel bakış açısı sağlar. `setRotationAngle` metodunu kullanarak tüm grafiği saat yönünde döndürebilirsiniz (açı derece cinsindendir).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

Yukarıdaki çağrı, **pasta grafiğini döndürme** ve **grafik yönünü değiştirme** gereksinimlerini karşılar. 0 ile 360 derece arasında herhangi bir açı kabul edilir.

## Tam çalıştırılabilir örnek

Her şeyi bir araya getirdiğimizde, bir pasta grafiği oluşturup bir dilimi patlatan ve grafiği döndüren tam, bağımsız bir program elde ederiz. IDE’nizden ya da komut satırından `java -cp <classpath> PieChartDemo` ile çalıştırın.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Beklenen çıktı

* Çalışma dizininde **CreatePieChartDemo.docx** adlı bir dosya oluşturulur.
* Microsoft Word ile dosyayı açtığınızda 400 × 300 piksel bir pasta grafiği görülür.
* İlk dilim (Q1) 10 puan dışarı kaydırılarak bir **pasta dilimini patlatma** etkisi yaratır.
* Tüm grafik 45 derece eğilir; bu da **grafik yönünü değiştirme** ve **pasta grafiğini döndürme** işlemlerini gösterir.

## Yaygın varyasyonlar ve kenar durumları

| Durum | Kodu nasıl uyarlamalısınız |
|-----------|-----------------------|
| **Farklı grafik boyutu** | `insertChart` içindeki `400, 300` argümanlarını değiştirin. |
| **Birden fazla seri** | `chart.getSeries()` üzerine daha fazla `ChartSeries` nesnesi ekleyin. |
| **Farklı bir dilimi patlatma** | İstenen `sliceIndex` ile `setExplode(sliceIndex, distance)` kullanın. |
| **Döndürme gerekmez** | `setRotationAngle` çağrısını atlayın ya da açıyı `0` olarak ayarlayın. |
| **DOCX yerine PDF dışa aktarımı** | Belgeyi oluşturduktan sonra `doc.save("output.pdf")` ile PDF formatını kullanın. |

> **Dikkat:** Negatif bir patlatma mesafesi `IllegalArgumentException` hatası oluşturur. Her zaman negatif olmayan bir değer sağlayın.

## Performans ipucu

Bir döngü içinde çok sayıda grafik üretiyorsanız, tek bir `DocumentBuilder` yeniden kullanın ve her yineleme için yalnızca `insertChart` çağırın. Bu, bellek kullanımını azaltır ve işleme süresini hızlandırır.

## Sonuç

Artık Aspose.Words for Java kullanarak **pasta grafiği oluşturma**, **pasta grafiği ekleme**, **pasta dilimini patlatma** ve **pasta grafiğini döndürme** konularını biliyorsunuz. Tam örnek, belgeyi başlatmadan döndürülmüş ve patlatılmış bir pasta grafiği görselleştiren bir dosyayı kaydetmeye kadar tüm iş akışını gösterir.

Sonraki adımda, **grafik yönünü değiştirme** üzerine 3‑D efektler uygulayabilir ya da **Bar** veya **Line** gibi diğer grafik tipleriyle deneyler yapabilirsiniz. Aynı API desenleri geçerlidir, bu yüzden bu öğreticiyi genişletmek oldukça basittir.

Verileri, dilim indeksini veya döndürme açısını kendi raporlama ihtiyaçlarınıza göre değiştirmekten çekinmeyin ve sonuçlarınızı toplulukla paylaşın!


## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalarla birlikte tam çalışan kod örnekleri içerir ve ek API özelliklerini hâkim olmanıza ve projelerinizde alternatif uygulama yaklaşımları keşfetmenize yardımcı olur.

- [Java kullanarak bir Word belgesine pasta grafiği ekleme](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Java’da pasta dilimini patlatma – Aspose.Words grafik öğreticisi](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}