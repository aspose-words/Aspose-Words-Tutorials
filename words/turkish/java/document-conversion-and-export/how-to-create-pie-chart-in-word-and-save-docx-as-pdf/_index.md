---
category: general
date: 2026-11-15
description: Java kullanarak bir Word belgesinde pasta grafiği oluşturmayı ve docx
  dosyasını PDF olarak kaydetmeyi öğrenin. Bu rehber ayrıca Word'ü PDF'ye dönüştürmeyi
  ve grafiği nasıl ekleyeceğinizi kapsar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: tr
lastmod: 2026-11-15
og_description: Java ile bir Word dosyasında pasta grafiği oluşturun ve docx'i PDF
  olarak kaydedin. Word'ü PDF'ye dönüştürmek ve grafik eklemek için bu adım adım öğreticiyi
  izleyin.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Word'de pasta grafiği oluşturun ve docx'i PDF olarak kaydedin – Java rehberi
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Word'de pasta grafiği nasıl oluşturulur ve docx PDF olarak nasıl kaydedilir
url: /tr/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'te pasta grafiği oluşturma ve docx'i PDF olarak kaydetme

If you need to **create pie chart** inside a Word document and then **save docx as PDF**, this tutorial shows you exactly how. You’ll see a complete, runnable example that converts a .docx file to a PDF while embedding a pie chart, so you can answer “how to add chart” without hunting for scattered snippets.

Word belgesi içinde **create pie chart** oluşturmanız ve ardından **save docx as PDF** yapmanız gerekiyorsa, bu öğretici tam olarak nasıl yapılacağını gösterir. .docx dosyasını bir PDF'ye dönüştüren ve içine bir pasta grafiği yerleştiren eksiksiz, çalıştırılabilir bir örnek göreceksiniz, böylece “how to add chart” sorusuna dağınık kod parçacıkları aramadan yanıt bulabilirsiniz.

In this guide you’ll learn to:

* Mevcut bir *.docx* dosyasını yükleyin (veya sıfırdan başlayın)  
* Aspose.Words for Java'yı **create pie chart** oluşturmak ve verileri doldurmak için kullanın  
* **Save docx as PDF** grafiği doğru şekilde render edilerek  
* Grafikler dahil olduğunda **convert word to pdf** inceliklerini anlayın  

The steps work with Aspose.Words 2024‑x.x and Java 17, but the concepts apply to any library that supports Word chart manipulation.

## Önkoşullar

| Gereksinim | Neden önemli |
|-------------|----------------|
| Java 17 (or later) | En son Aspose.Words JAR tarafından gereklidir |
| Maven or Gradle build tool | Maven veya Gradle yapı aracı |
| Aspose.Words for Java (latest version) | `Document`, `Chart` ve `ChartType` sınıflarını sağlar |
| An input **.docx** file (or a blank document) | Grafiği bu dosyaya eklenecek |

Add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). Example for Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Adım 1: Word belgesini yükleyin (veya yeni bir tane oluşturun)

The first action is to obtain a `Document` instance. If you already have a template, pass its path; otherwise create an empty document.

İlk adım bir `Document` örneği elde etmektir. Zaten bir şablonunuz varsa, yolunu geçin; aksi takdirde boş bir belge oluşturun.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Why this step?* The `Document` object is the container for all Word content, including charts. Loading an existing file lets you preserve surrounding text and styles while adding a new visual element.

*Neden bu adım?* `Document` nesnesi, grafikler dahil tüm Word içeriğinin konteyneridir. Mevcut bir dosyayı yüklemek, etrafındaki metin ve stilleri korumanıza ve yeni bir görsel öğe eklemenize olanak tanır.

## Adım 2: **Create pie chart** – “how to create chart”ın temeli

Now we instantiate a `Chart` object with `ChartType.PIE`. This automatically creates a pie chart placeholder that you can later fill with data.

Şimdi `ChartType.PIE` ile bir `Chart` nesnesi oluşturuyoruz. Bu, daha sonra veri ile doldurabileceğiniz bir pasta grafik yer tutucusunu otomatik olarak oluşturur.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Explanation*: `ChartType.PIE` tells Aspose.Words to use a pie‑chart template. The chart is added to the document’s body, so it appears where you need it. This satisfies the “how to add chart” requirement in a single call.

*Açıklama*: `ChartType.PIE`, Aspose.Words'e bir pasta‑grafik şablonu kullanmasını söyler. Grafik, belgenin gövdesine eklenir, böylece ihtiyacınız olan yerde görünür. Bu, “how to add chart” gereksinimini tek bir çağrıyla karşılar.

## Adım 3: Grafiği doldurun – “how to add chart” sorusuna veriyle yanıt vererek

A pie chart is meaningless without series data. Use the `Series` collection to add categories and values.

Seri verileri olmadan bir pasta grafiği anlamsızdır. Kategorileri ve değerleri eklemek için `Series` koleksiyonunu kullanın.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Why this matters*: Each call to `add` creates a slice of the pie. The first argument is the label, the second is the numeric value. You can replace these with dynamic data from a database or CSV file.

*Neden önemli?*: `add` metodunun her çağrısı pastanın bir dilimini oluşturur. İlk argüman etiket, ikinci argüman sayısal değerdir. Bunları bir veritabanı veya CSV dosyasından gelen dinamik verilerle değiştirebilirsiniz.

### İsteğe Bağlı: Görünümü özelleştirme (gerekli değil ama faydalı)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

These tweaks illustrate how you can **how to create chart** with a professional look, without leaving the Java code.

Bu ince ayarlar, Java kodundan çıkmadan **how to create chart** profesyonel bir görünümle nasıl yapabileceğinizi gösterir.

## Adım 4: **Save docx as PDF** – “convert word to pdf”ın son kısmı

Once the chart is embedded, export the document to PDF. Aspose.Words renders the chart as a vector graphic, preserving quality.

Grafik eklendikten sonra belgeyi PDF olarak dışa aktarın. Aspose.Words, grafiği vektörel bir grafik olarak render eder ve kaliteyi korur.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Key point*: The `save` method automatically converts the Word file to PDF, handling chart rasterization, font embedding, and page layout. This fulfills the **save docx as pdf** goal and demonstrates a reliable way to **convert word to pdf** when charts are present.

*Önemli nokta*: `save` metodu, Word dosyasını otomatik olarak PDF'ye dönüştürür, grafik rasterlemesi, font gömme ve sayfa düzenini yönetir. Bu, **save docx as pdf** hedefini gerçekleştirir ve grafiklerin bulunduğu durumlarda **convert word to pdf** için güvenilir bir yol gösterir.

### Beklenen çıktı

Programı çalıştırmak `output.pdf` dosyasını üretir ve şu içeriği barındırır:

* `input.docx`'in orijinal içeriği (varsa)  
* *Sales Distribution Q1* başlıklı tamamen render edilmiş bir pasta grafiği  
* Verilerle eşleşen doğru dilim yüzdeleri (40 %, 30 %, 30 %)

PDF'yi herhangi bir görüntüleyicide açın; Word dosyasında gördüğünüzle aynı net pasta grafiğini görmelisiniz.

## Yaygın tuzaklar ve nasıl kaçınılır

| Sorun | Neden | Çözüm |
|-------|-------|-----|
| Grafik PDF'de boş görünüyor | Yazı tipi veya grafik render ayarları eksik | En son Aspose.Words sürümünü kullandığınızdan emin olun; gerekli render kütüphanelerini içinde barındırır. |
| Veri değerleri yanlış yuvarlanıyor | Büyük sayılar için tam sayı değerleri kullanmak | `double` değerler sağlayın veya seriye eklemeden önce sayıları ölçeklendirin. |
| Çıktı PDF'i çok büyük | Görüntüler yüksek DPI'da gömülmüş | Görüntü de gömüyorsanız `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)` ayarlayın. |
| “convert word to pdf” `UnsupportedOperationException` hatası veriyor | Eski bir Java sürümü (< 11) kullanmak | Aspose.Words 24.x'in gerektirdiği Java 17 veya daha yeni bir sürüme yükseltin. |

## Pro ipucu: Grafik oluşturma mantığını yeniden kullanın

If you need to add multiple charts to the same document, extract the chart‑building code into a helper method:

Aynı belgeye birden fazla grafik eklemeniz gerekiyorsa, grafik oluşturma kodunu bir yardımcı metoda çıkarın:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Now you can call `doc.getFirstSection().getBody().appendChild(createPieChart(...));` for each dataset, keeping your code DRY (Don’t Repeat Yourself).

Artık her veri kümesi için `doc.getFirstSection().getBody().appendChild(createPieChart(...));` çağrısı yapabilirsiniz, kodunuzu DRY (Kendini Tekrarlama) tutarak.

## Sonuç

You now know how to **create pie chart** inside a Word document, populate it with data, and **save docx as PDF** using Java. This end‑to‑end example covers the entire **convert word to pdf** workflow, answers **how to add chart**, and demonstrates **how to create chart** programmatically.  

From here you might explore:

* `ChartType.BAR`, `ChartType.LINE` ile çubuk veya çizgi grafik ekleme – başka bir **how to create chart** senaryosu.  
* PNG veya HTML gibi diğer formatlara (`SaveFormat.PNG`, `SaveFormat.HTML`) dışa aktarma.  
* Grafikleri eklemeden önce tablolar veya yer tutucularla giriş belgesini dinamik olarak oluşturma.

Feel free to experiment with different data sets, styling options, or even embedding multiple charts per page. Happy coding!

## Sonra Ne Öğrenmelisiniz?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to save word as pdf and create accessible PDF in Java](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [How to create chart in Word with Java and Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}