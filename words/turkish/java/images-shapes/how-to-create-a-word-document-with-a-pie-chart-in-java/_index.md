---
category: general
date: 2026-09-18
description: Aspose.Words for Java kullanarak bir Word belgesi oluşturmayı ve pasta
  grafiği eklemeyi öğrenin. Pasta grafiğini döndürme ve Word dosyası oluşturma adımlarını
  içerir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: tr
lastmod: 2026-09-18
og_description: Java kullanarak bir Word belgesi oluşturun ve içine bir pasta grafiği
  ekleyin. Pasta grafiğini döndürmek, dilimleri patlatmak ve bir Word dosyası oluşturmak
  için bu kılavuzu izleyin.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Pasta grafikli bir Word belgesi oluşturun – adım adım Java rehberi
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Java’da pasta grafikli bir Word belgesi nasıl oluşturulur
url: /tr/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java’da pasta grafikli bir Word belgesi nasıl oluşturulur

Verileri görselleştiren bir **Word belgesi** oluşturmanız gerekiyorsa, bu kılavuz Aspose.Words for Java ile bunu nasıl yapacağınızı gösterir. Bir pasta grafik eklemeyi, bir dilimi patlatmayı, grafiği döndürmeyi ve sonunda **Word dosyası** oluşturmayı öğreneceksiniz; bu dosyayı Microsoft Word’de açabilirsiniz.

Metin ve grafiklerin birleştirildiği raporlar ayrı bir grafik aracına ihtiyaç duymaz. Bu öğreticinin sonunda, tam yapılandırılmış bir pasta grafik içeren .docx dosyasını oluşturan çalıştırılabilir bir programınız olacak.

## Önkoşullar

- Java 17 veya daha yeni bir sürüm (kod Java 8+ ile de derlenebilir)
- Bağımlılık yönetimi için Maven veya Gradle
- Aspose.Words for Java lisansı (bu örnek için ücretsiz deneme sürümü yeterlidir)
- Java sözdizimine temel aşinalık

## Adım 1: Maven projesini ayarlama

Yeni bir Maven projesi oluşturun ve `pom.xml` dosyasına Aspose.Words bağımlılığını ekleyin:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **İpucu:** Sürüm numarasını güncel tutun; yeni sürümler grafik‑tipi iyileştirmeleri ve hata düzeltmeleri içerir.

## Adım 2: Yeni bir Word belgesi oluşturma

Programatik olarak **Word belgesi oluştururken** ilk işlem bir `Document` nesnesi örneklemektir. Bu nesne, .docx dosyasının tamamını bellekte temsil eder.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

`Document` sınıfı, tüm Word‑işleme özellikleri için giriş noktasıdır. Bu aşamada diske bir dosya yazılmaz; her şey RAM’de gerçekleşir ve `save` çağrıldığında dosya oluşturulur.

## Adım 3: Pasta grafik ekleme

Bir `DocumentBuilder`, belgeye içerik eklemenizi sağlar. `insertChart` ile doğrudan **pasta grafik** nesneleri ekleyebilirsiniz.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` Aspose.Words’e bir pasta grafik oluşturmasını söyler. Boyutlar puan (point) cinsindendir (1 pt ≈ 1/72 in). Bu çağrıdan sonra grafik yeni bir paragrafta görünür.

## Adım 4: Grafik verileriyle doldurma

Bir pasta grafik, bir dizi değere ihtiyaç duyar. Burada üç kategori ekliyoruz: “Apples”, “Bananas” ve “Cherries”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

`add` metodu seriyi oluşturur ve otomatik olarak lejand (legend) girdileri ekler. Bu deseni herhangi bir sayısal veri kümesi için yeniden kullanabilirsiniz.

## Adım 5: İlk dilimi vurgulama

Bir dilimi patlatmak, belirli bir değere dikkat çeker. İlk dilim (indeks 0) 20 puan kadar patlatılır.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Seriye `explode` uygulamak tüm grafiği etkiler, bu yüzden yalnızca ilk veri noktası kaydırılır.

## Adım 6: Pasta grafiği döndürme

Grafiği döndürmek, özellikle en büyük dilim üstte olmadığında görsel dengeyi artırır. `setRotationAngle` metodu derece cinsinden bir açı bekler.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

45° döndürme, başlangıç açısını saat yönünde kaydırır ve grafiği birçok yerleşimde daha okunaklı hâle getirir.

## Adım 7: Belgeyi kaydetme ve Word dosyası oluşturma

Son olarak belgeyi diske yazın. Bu adım **Word dosyası oluşturur** ve Microsoft Word, LibreOffice veya uyumlu herhangi bir görüntüleyicide açılabilir.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save` metodu .docx uzantısını otomatik algılar ve Word‑uyumlu bir paket yazar. `output` klasörü var olmalıdır; yoksa program içinde oluşturabilirsiniz.

### Beklenen çıktı

Programı çalıştırdıktan sonra `output/PieChart.docx` dosyasını açın. Şunları görmelisiniz:

- 400 × 300 pt boyutunda tek bir sayfa içinde pasta grafik.
- “Apples” dilimi 20 pt dışarı doğru patlatılmış.
- Tüm grafik 45° saat yönünde döndürülmüş.
- Üç meyve kategorisini gösteren bir lejand.

## Yaygın varyasyonlar ve kenar durumları

### Birden fazla grafik ekleme

Birden fazla grafik ihtiyacınız varsa, imleci taşıdıktan sonra `builder.insertChart` metodunu tekrar çağırın:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Grafik renklerini değiştirme

Serinin `getPoints()` koleksiyonu üzerinden dilim renklerini özelleştirebilirsiniz:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Büyük veri kümeleriyle çalışma

10’dan fazla dilim içeren veri kümeleri için görselliği korumak amacıyla bir halka grafik (`ChartType.DOUGHNUT`) kullanmayı düşünün.

## Sonuç

Artık Aspose.Words for Java kullanarak **Word belgesi oluşturma**, **pasta grafik ekleme**, **pasta grafiği döndürme** ve **Word dosyası üretme** konularını biliyorsunuz. Tam çözüm, belge başlatmadan dosya çıktısına kadar tüm iş akışını gösterir; her adımın “nasıl” ve “neden” yönlerini kapsar.

Sonraki adımda, **veritabanından pasta grafik verisi oluşturma**, veri etiketleri ekleme veya grafiği resim olarak dışa aktarma gibi ilgili konuları keşfedin. Farklı grafik tipleri (çubuk, çizgi, halka) ile deney yaparak Word‑otomasyon araç setinizi genişletin.


## Sonra Ne Öğrenmelisiniz?


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakın ilişkili konuları kapsar. Her kaynak, adım adım açıklamalarla birlikte tam çalışan kod örnekleri içerir; böylece ek API özelliklerini öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}