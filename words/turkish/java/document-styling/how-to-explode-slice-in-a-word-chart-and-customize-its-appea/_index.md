---
category: general
date: 2026-10-04
description: Word grafiğinde dilimi patlatmayı, pasta grafiği dilimini patlatmayı
  ve halka grafiği boyutunu adım adım bir Java örneğiyle öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: tr
lastmod: 2026-10-04
og_description: Word grafiğinde dilimi nasıl patlatır ve Java ile pasta ya da halka
  grafikleri nasıl özelleştirirsiniz. Word'de grafiği değiştirmek için tam örneği
  izleyin.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Word grafiğinde dilimi nasıl patlatılır – tam Java rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Word grafiğinde dilimi patlatma ve görünümünü özelleştirme
url: /tr/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word grafiğinde dilimi patlatma ve görünümünü özelleştirme

If you need to **how to explode slice** in a Word chart, this guide shows you exactly how. Whether you’re preparing a sales presentation or a financial report, exploding a pie‑chart slice or adjusting a doughnut hole can make the most important data stand out. In the following sections you’ll also learn how to **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size**, and **customize pie chart word** documents using Aspose.Words for Java.

Bu öğreticiyi, bir `.docx` dosyasını yükleyen, bir pasta grafiğinin ilk dilimini patlatan, donut deliği boyutunu değiştiren ve sonucu kaydeden eksiksiz, çalıştırmaya hazır bir Java programı ile tamamlayacaksınız. Hiç dış script ya da manuel düzenleme gerekmez.

## Önkoşullar

- Geliştirme makinenizde yüklü Java 17 veya daha yeni bir sürüm.  
- Bağımlılıkları yönetmek için Maven 3.6+ (veya Gradle).  
- Aspose.Words for Java kütüphanesi (ücretsiz deneme sürümü geliştirme için çalışır).  
- En az bir grafik (pasta veya donut) içeren bir Word belgesi (`input.docx`).

## Adım 1: Aspose.Words'ı projenize ekleyin

If you use Maven, add the following dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

For Gradle, place this in `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Kütüphane sürümünüzü güncel tutun; yeni sürümler ek grafik türleri desteği ekler ve performansı artırır.

## Adım 2: Grafik içeren Word belgesini yükleyin

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Neden önemli:** Belgeyi yüklemek, Aspose.Words'un gezinebileceği bellek içi bir temsil oluşturur. Bu nesne olmadan grafik düğümlerine erişemezsiniz.

## Adım 3: Belgedeki ilk grafiği alın

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Açıklama:** `NodeType.SHAPE`, grafikler dahil tüm çizim nesnelerini kapsar. `true` argümanı, Aspose'a yinelemeli arama yapmasını söyler; böylece grafik bir tablo içinde iç içe olsa bile ilk grafik bulunur.

## Adım 4: Pasta grafiğinin ilk dilimini patlatın

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**Nasıl çalışır:** `setExplosion` yöntemi, dilimin merkezden ne kadar uzağa hareket edeceğini belirleyen sayısal bir değer alır. `20` değeri, grafiğin düzenini bozmadan görsel olarak fark edilir.

## Adım 5: Donut grafiği için donut deliği boyutunu ayarlayın

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Neden faydalı:** Çok sayıda veri noktanız olduğunda daha büyük bir donut deliği okunabilirliği artırabilir. `setDoughnutHoleSize` yöntemi yüzde (0‑100) bekler.

## Adım 6: Değiştirilmiş belgeyi kaydedin

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Beklenen çıktı

- İlk pasta grafiğinin ilk dilimi dışa doğru kaydırılır ve öne çıkar.
- Grafik bir donut ise, merkezi delik grafiğin yarıçapının %40'ına genişler.
- Ortaya çıkan `PieChart.docx` dosyası Microsoft Word, LibreOffice veya uyumlu herhangi bir görüntüleyicide açılabilir; programlı olarak uyguladığınız görsel değişiklikleri gösterir.

## Tam, çalıştırılabilir örnek

Aşağıda tüm program tek bir blokta verilmiştir. `ChartExploder.java` dosyasına kopyalayın, dosya yollarını ayarlayın ve `mvn compile exec:java` (veya IDE'nizin çalıştırma yapılandırması) ile çalıştırın.

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

Bu kodu çalıştırmak, **modify chart in Word**, **explode pie chart slice** ve **change doughnut chart size** işlemlerini otomatik olarak gerçekleştirecektir.

## Yaygın sorular ve kenar durumları

| Question | Answer |
|----------|--------|
| *Belge birden fazla grafik içeriyorsa ne olur?* | Örnek, **ilk** grafiği hedefler (`NodeType.SHAPE, 0`). Diğer grafiklerle çalışmak için indeksi değiştirin veya `doc.getChildNodes(NodeType.SHAPE, true)` üzerinden döngü yapın ve `shape.getChart() != null` ile filtreleyin. |
| *İlk dilim dışındaki bir dilimi patlatabilir miyim?* | Evet. İstenen seriye `chart.getSeries().get(seriesIndex)` ile erişin ve `setExplosion(value)` metodunu çağırın. İndeksler sıfır‑tabanlıdır. |
| *Bu, Word 2007‑2021 dosyalarıyla çalışır mı?* | Aspose.Words, `.doc`, `.docx`, `.dot` ve `.dotx` dosyalarını destekler. Kütüphane dosya formatını soyutladığı için aynı kod tüm sürümlerde çalışır. |
| *Grafik bir çubuk ya da çizgi grafiği ise ne olur?* | `setExplosion` ve `setDoughnutHoleSize` yalnızca pasta tipi grafiklerde uygulanabilir. Grafik tipi farklı olduğunda kod bu işlemleri güvenli bir şekilde atlar. |
| *Aspose.Words için bir lisansa ihtiyacım var mı?* | Ücretsiz bir değerlendirme lisansı 30‑günlük sınırlamayı kaldırır ancak bir filigran ekler. Üretim için, filigranı kaldırmak ve tam işlevselliği açmak amacıyla bir lisans satın alın. |

## Sonuç

Artık Word grafiğinde **how to explode slice** nasıl yapılacağını, **modify chart in Word** ve **change doughnut chart size** işlemlerinin Aspose.Words for Java ile nasıl yapılacağını biliyorsunuz. Tam örnek, belgeyi yüklemek, grafiği bulmak, görsel ayarlamaları uygulamak ve sonucu kaydetmek gibi tam iş akışını gösterir; böylece bu adımları herhangi bir raporlama veya belge‑oluşturma hattına entegre edebilirsiniz.

**Next steps**

- Renkleri değiştirme, veri etiketleri ekleme veya grafik türlerini değiştirme (`chart.setChartType(ChartType.BAR_CLUSTERED)`) gibi diğer grafik özelleştirmelerini keşfedin.  
- Bu mantığı Aspose.PDF ile birleştirerek aynı raporun PDF sürümünü oluşturun.  
- Bir dizindeki dosyalar üzerinde döngü oluşturarak bir belge topluluğu için süreci otomatikleştirin.

Tasarım yönergelerinize uyması için farklı patlama değerleri veya donut delik yüzdeleriyle denemeler yapmaktan çekinmeyin. İyi kodlamalar!

## Sonra Ne Öğrenmelisiniz?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}