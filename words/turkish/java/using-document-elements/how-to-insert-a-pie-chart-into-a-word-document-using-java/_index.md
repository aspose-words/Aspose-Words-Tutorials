---
category: general
date: 2026-09-27
description: Java ile bir Word belgesine pasta grafiği eklemeyi, Word’de pasta grafiği
  oluşturmayı ve net veri içgörüsü için pasta grafiğinde yüzde değerlerini göstermeyi
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: tr
lastmod: 2026-09-27
og_description: Java ile bir Word belgesine pasta grafiği nasıl eklenir. Bu kılavuz,
  Word’de pasta grafiği oluşturmayı, grafikte yüzde değerlerini göstermeyi ve lider
  çizgileri eklemeyi gösterir.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Java kullanarak bir Word belgesine pasta grafiği nasıl eklenir
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Java kullanarak bir Word belgesine pasta grafiği nasıl eklenir
url: /tr/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java kullanarak bir Word belgesine pasta grafiği ekleme

Bir Word dosyasına **pasta grafiği ekleme** ihtiyacınız varsa, bu kılavuz size sürecin tamamını adım adım gösterir. **Word’de pasta grafiği oluşturma**, dilimlerin üzerine yüzde değerlerini gösterme ve daha şık bir görünüm için lider çizgileri ekleme konularını öğreneceksiniz.

Word otomasyonu genellikle ağır gelebilir, ancak Aspose.Words for Java ile programatik olarak tam biçimlendirilmiş belgeler oluşturabilirsiniz. Bu öğreticinin sonunda, stilize bir pasta grafiği içeren bir Word belgesi üreten çalıştırılabilir bir Java kod parçasına sahip olacaksınız.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

- Java 17 veya daha yeni bir sürüm
- Bağımlılık yönetimi için Maven ya da Gradle
- Projenize eklenmiş Aspose.Words for Java (sürüm 23.11 veya daha yeni)
- Java sözdizimi hakkında temel bilgi

Grafik API’leriyle ilgili önceden bir deneyime ihtiyacınız yok; aşağıdaki adımlar proje kurulumundan nihai çıktıya kadar her şeyi kapsar.

## Adım 1: Maven bağımlılığını ekleyin

Aspose.Words kütüphanesini `pom.xml` dosyanıza ekleyin. Bu tek bağımlılık, `Document`, `DocumentBuilder` ve grafik sınıflarına erişim sağlar.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Gradle kullanıyorsanız eşdeğeri şu şekildedir:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **İpucu:** En son kararlı sürümü kullanarak hata düzeltmelerinden ve yeni grafik özelliklerinden faydalanın.

## Adım 2: Yeni bir belge ve builder oluşturun

`Document` nesnesi Word dosyasını temsil ederken, `DocumentBuilder` içerik eklemenizi sağlar. Bu, **Word belgesine grafik ekleme** için temel oluşturur.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder artık belge içinde istediğiniz yere nesneler yerleştirmeye hazır.

## Adım 3: Bir pasta grafiği ekleyin

Aspose.Words çeşitli grafik türlerini destekler; biz `ChartType.PIE` seçiyoruz. Boyut, puan cinsinden ifade edilir (1 puan = 1/72 inç).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

Bu aşamada grafik, yer tutucu değerlerle bir varsayılan veri serisi içerir. Gerektiğinde bu değerleri daha sonra değiştirebilirsiniz.

## Adım 4: Grafik serisine erişin

Bir pasta grafiğinin tek bir serisi vardır ve bu seri dilim değerlerini tutar. Biçimlendirme uygulamak için seriyi alın.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Adım 5: İlk dilimi patlatın

Bir dilimi patlatmak, belirli bir veri noktasına dikkat çeker. Ana metriği vurgulamak istediğinizde yaygın bir görsel ipucudur.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Adım 6: Her dilimde yüzde değerlerini gösterin

Yüzdeleri doğrudan grafiğin üzerine yerleştirmek veri içgörüsünü artırır. Bu, **pasta grafiğinde yüzde göster** gereksinimini karşılar.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Adım 7: Daha net etiketler için lider çizgileri ekleyin

Lider çizgileri, dilim etiketlerini ilgili bölümlerine bağlayarak belirsizliği ortadan kaldırır. Bu, **lider çizgileri ekleme** ihtiyacını karşılar.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Adım 8: Belgeyi kaydedin

Son olarak belgeyi diske yazın. Yazma izniniz olan herhangi bir klasörü seçebilirsiniz.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

Programı çalıştırdığınızda `output/PieFormatted.docx` oluşturulur. Dosyayı Microsoft Word’de açtığınızda:

- İlk dilim patlatılmış olarak görünür.
- Her dilim yüzde değerini gösterir.
- Lider çizgileri yüzde değerlerinden ilgili dilimlere doğru işaret eder.

### Beklenen çıktı

![Word’de biçimlendirilmiş pasta grafiği](/images/pie-formatted.png){: .center-image alt="Word belgesine eklenmiş biçimlendirilmiş pasta grafiği"}

Ekran görüntüsü (alt metin anahtar kelimeyi içerir), raporlar, teklifler veya gösterge tabloları için hazır, temiz ve veri odaklı bir pasta grafiğinin son halini gösterir.

## Yaygın varyasyonlar ve kenar durumları

### Dilim değerlerini değiştirme

Özel veri gerekiyorsa, varsayılan seri değerlerini şu şekilde değiştirin:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Çoklu seriler (donut grafiği)

Basit bir pasta grafiği tek seriye sahiptir, ancak Aspose.Words aynı zamanda birden fazla seriyle donut grafikleri de destekler. `ChartType.PIE` yerine `ChartType.DONUT` kullanın ve seri‑konfigürasyon adımlarını tekrarlayın.

### PDF’ye dışa aktarma

İş akışınız PDF gerektiriyorsa, grafik oluşturulduktan sonra `doc.save("output/PieFormatted.pdf");` çağrısını ekleyin. Görsel düzen aynı kalır.

## Tam kaynak kodu

Aşağıda IDE’nize kopyalayıp yapıştırabileceğiniz, bağımsız bir Java dosyası yer almaktadır.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Programı `mvn compile exec:java -Dexec.mainClass=PieChartExample` (veya eşdeğer Gradle komutu) ile derleyip çalıştırın. Oluşturulan Word dosyası tamamen biçimlendirilmiş pasta grafiğini içerir.

## Sonuç

Artık Java kullanarak bir Word belgesine **pasta grafiği ekleme**, **Word’de pasta grafiği oluşturma**, **pasta grafiğinde yüzde göster** ve **grafiği Word belgesine ekleme** konularını biliyorsunuz; ayrıca lider çizgileri ekleyerek grafiği daha okunabilir hâle getirdiniz. Tam örnek her adımı gösterir, kodun neden bu şekilde yazıldığını açıklar ve özelleştirme ipuçları sunar.

İleride keşfedebileceğiniz konular:

- Özel yazı tipleriyle veri etiketleri ekleme (**pasta grafiğinde yüzde göster** varyasyonları)
- Tek bir belgede birden fazla grafik birleştirme (**grafiği Word belgesine ekleme** kullanım senaryosu)
- Tablolar ve grafiklerle rapor otomasyonu

Renklerle, dilim sıralamalarıyla ya da PDF’ye dışa aktarmayla denemeler yapın. Kodlamanın tadını çıkarın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak ilgili konuları derinleştirir. Her kaynak, adım adım açıklamalar ve çalışan kod örnekleri içerir; böylece API özelliklerini daha iyi kavrayabilir ve projelerinizde alternatif uygulama yaklaşımları keşfedebilirsiniz.

- [Aspose.Words for Java ile sütun grafiği oluşturma](/words/english/java/document-conversion-and-export/using-charts/)
- [Word Belgesinde Grafik Eksenini Gizleme](/words/english/net/programming-with-charts/hide-chart-axis/)
- [.NET için Aspose.Words kullanarak Word’te Çizgi Grafiği Oluşturma](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}