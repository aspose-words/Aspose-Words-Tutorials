---
category: general
date: 2026-09-27
description: Java'da radyal bir grafik oluşturun ve grafiği Word'e ekleyin. Grafik
  boyutunu ayarlamayı, veri serisi eklemeyi ve boş bir Word belgesi oluşturmayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: tr
lastmod: 2026-09-27
og_description: Java'da radyal grafik oluşturun, ardından grafiği Word'e ekleyin.
  Bu kılavuz, grafik boyutunu nasıl ayarlayacağınızı, veri serisi ekleyeceğinizi ve
  boş bir Word belgesi oluşturacağınızı gösterir.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Java ile radyal grafik oluşturun ve grafiği Word'e ekleyin
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Java ile radyal grafik oluştur ve grafiği Word'e ekle
url: /tr/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Radial grafik oluşturun ve Java ile Word'e grafik ekleyin

Java kullanarak bir Word dosyasında **radial grafik oluşturmanız** gerekiyorsa, bu öğretici size tam olarak nasıl yapılacağını gösterir. **Grafiği Word'e ekleme**, grafiğin boyutlarını ayarlama ve sıfırdan **boş bir Word belgesi** oluşturma konularını göreceksiniz.

Belgeyi başlatmaktan veri serisi eklemeye ve son `.docx` dosyasını kaydetmeye kadar gerekli tüm adımları adım adım inceleyeceğiz. Sonunda radial grafik içeren tam işlevsel bir Word dosyanız olacak ve gelecekteki özelleştirmeler için **grafik boyutunu nasıl ayarlayacağınızı** ve **veri serisi grafiği eklemeyi** anlayacaksınız.

## Önkoşullar

* Java 17 veya üzeri (kod, modern bir JDK ile derlenir)
* Aspose.Words for Java 24.9 veya daha yeni – `setShowGraduations` yöntemi yalnızca bu sürümden itibaren mevcuttur
* Aspose.Words JAR dosyasını ekleyebilen bir IDE veya yapı aracı (Maven/Gradle)
* Java sözdizimi ve Maven/Gradle bağımlılık yönetimi konusunda temel bilgi

> **Pro ipucu:** Maven kullanıyorsanız, `pom.xml` dosyanıza aşağıdakileri ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Adım 1: Boş bir Word belgesi oluşturun

Boş bir belge, grafiğin yerleştirileceği tuvaldir. `Document` sınıfı, tüm `.docx` dosyasını temsil eder.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Boş bir belge oluşturmak, önceden var olan içeriğin grafik düzenine müdahale etmesini önler.

## Adım 2: DocumentBuilder'ı başlatın

`DocumentBuilder`, belgeye nesneler, metin ve diğer öğeler eklemek için kullanışlı yöntemler sunar.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder daha sonra **grafiği Word'e eklemek** için kullanılacak.

## Adım 3: Radial grafiği oluşturun

Aspose.Words birçok grafik türünü destekler; `ChartType.RADIAL` radial (polar) bir grafik oluşturur.

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

Bu noktada grafik var ancak veri, boyut veya görsel seçenekleri yoktur.

## Adım 4: Grafik'e bir veri serisi ekleyin

Veri serisi olmayan bir grafik boştur. `add` yöntemi bir seri adı ve değer dizisi alır.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

`add` metodunu tekrarlayarak birden fazla seri ekleyebilirsiniz. Bu, **veri serisi grafiği ekleme** gereksinimini karşılar.

## Adım 5: Graduasyonları etkinleştirin (isteğe bağlı)

Graduasyonlar, okunabilirliği artıran radial ızgara çizgileridir. Yalnızca 24.9 sürümünden itibaren mevcuttur.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Daha eski bir Aspose.Words sürümü kullanıyorsanız, bu satır bir istisna fırlatır—bu yüzden önce kütüphane sürümünüzü doğrulayın.

## Adım 6: Grafiğin boyutlarını ayarlayın

Grafik boyutunu kontrol etmek, sayfa kenar boşluklarına güzelce sığmasını sağlar. Bu, **grafik boyutunu nasıl ayarlayacağınız** konusunu ele alır.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Genişlik ve yükseklik değerlerini düzen tasarım ihtiyaçlarınıza göre ayarlayabilirsiniz. Unutmayın, 1 point ≈ 1/72 inç.

## Adım 7: Grafiği Word belgesine ekleyin

Şimdi grafik yerleştirilmeye hazır. `DocumentBuilder`'ın `insertChart` yöntemi eklemeyi gerçekleştirir.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Bu, **grafiği word'e ekleme** işleminin çekirdeğidir.

## Adım 8: Belgeyi kaydedin

Son olarak, belgeyi diske yazın. Dosya, az önce oluşturduğunuz radial grafiği içerecek.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Programı çalıştırmak, projenin çalışma dizininde `RadialChart.docx` dosyasını üretir. Microsoft Word'de dosyayı açtığınızda üç veri noktasına ve görünür graduasyonlara sahip bir radial grafik gösterilir.

### Beklenen çıktı

* `RadialChart.docx` adlı bir Word dosyası
* Dosyanın içinde, 400 × 300 point boyutunda bir radial grafik içeren tek sayfa
* Grafik, **Series 1** başlıklı bir seri ve **10, 20, 30** değerlerini gösterir
* Graduasyonlar (radial ızgara çizgileri) grafiğin etrafında görünür

## Yaygın varyasyonlar ve kenar durumları

| Durum | Ne değiştirilmeli | Sebep |
|-----------|----------------|--------|
| **Birden fazla seri** | Her seri için `chart.getSeries().add(...)` çağırın | Karşılaştırmalı veri görselleştirmesine olanak tanır |
| **Farklı grafik türü** | `ChartType.RADIAL` yerine `ChartType.COLUMN` (veya başka bir) ile değiştirin | Verilerinizi en iyi temsil eden grafik türünü kullanın |
| **Özel renkler** | `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` erişin | Görsel marka kimliğini artırır |
| **Eski Aspose.Words sürümü** | `setShowGraduations` satırını atlayın veya kütüphaneyi yükseltin | `NoSuchMethodError` hatasını önler |
| **Farklı bir formata kaydetme** | `doc.save("RadialChart.pdf", SaveFormat.PDF)` kullanın | DOCX yerine PDF oluşturur |

## Tam çalıştırılabilir örnek

Aşağıda tam, bağımsız Java programı yer almaktadır. `RadialChartExample.java` adlı bir dosyaya kopyalayın, Aspose.Words bağımlılığını ekleyin ve çalıştırın.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Sonuç

Artık programlı olarak **radial grafik oluşturmayı**, **veri serisi grafiği eklemeyi**, **grafik boyutunu nasıl ayarlayacağınızı** kontrol etmeyi ve **grafiği Word'e eklemeyi** bir **boş Word belgesi** ile başlayarak biliyorsunuz. Örnek, Aspose.Words for Java 24.9 kullanıyor, ancak aynı kavramlar benzer bir API sunan diğer grafik kütüphanelerine de uygulanabilir.

### Sonraki adımlar

* Diğer grafik türlerini keşfedin (`ChartType.PIE`, `ChartType.LINE`, vb.) – bu, ikincil anahtar kelime **grafiği word'e ekleme** ile bağlantılıdır.
* Eksen etiketlerini, lejandları ve renkleri marka yönergelerinize göre özelleştirin.
* Grafikleri veritabanı sorgularından veya CSV dosyalarından dinamik olarak oluşturun.
* Oluşturulan `.docx` dosyasını dağıtım için PDF'ye dönüştürün (`doc.save("output.pdf", SaveFormat.PDF)`).

Boyutlarla, seri verileriyle ve stil seçenekleriyle denemeler yapmaktan çekinmeyin; ihtiyacınız olan tam görseli oluşturun. Kodlamanın tadını çıkarın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for Java kullanarak sütun grafiği nasıl oluşturulur](/words/english/java/document-conversion-and-export/using-charts/)
- [Word Belgesi Java – Gölge Efektiyle Dikdörtgen Şekil Ekleme](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Bir Word Belgesine Alan Grafiği Ekleme](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}