---
category: general
date: 2026-10-10
description: Word dosyasında grafiği nasıl döndüreceğinizi ve tam bir Java örneğiyle
  Word'deki grafiği değiştirerek halka grafiğinin boyutunu nasıl ayarlayacağınızı
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: tr
lastmod: 2026-10-10
og_description: Aspose.Words for Java kullanarak bir Word dosyasındaki grafiği nasıl
  döndürür ve Word'de grafiği değiştirerek halka grafiğinin boyutunu nasıl değiştirirsiniz.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Word belgesinde grafiği nasıl döndürürsünüz – adım adım Java rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Aspose.Words kullanarak bir Word belgesindeki grafiği nasıl döndürürsünüz?
url: /tr/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words kullanarak bir Word belgesinde grafiği nasıl döndürürsünüz

Microsoft Word dosyası içinde **how to rotate chart** yapmanız gerekiyorsa, bu kılavuz tam adımları gösterir. Ayrıca **modify chart in Word** yaparak **change doughnut chart size** işlemini Java kodunuzdan çıkmadan öğrenebileceksiniz.

Word otomasyonu genellikle birbirinden bağımsız API çağrıları gibi hissettirse de, Aspose.Words ile bir grafiği diğer belge düğümleri gibi ele alabilirsiniz. Bu öğreticinin sonunda, mevcut bir `.docx` dosyasını yükleyen, bir doughnut grafiğini %45 döndüren, deliği yarıçapın %50’sine küçülten ve sonucu yeni bir dosya olarak kaydeden çalıştırılabilir bir programınız olacak.

## Gereksinimler

Başlamadan önce şunların yüklü olduğundan emin olun:

* Java 17 veya daha yeni bir sürüm.
* Bağımlılıkları yönetmek için Maven (veya Gradle).
* İçinde bir doughnut grafiği bulunan bir giriş Word belgesi (`input.docx`).
* Geçerli bir Aspose.Words for Java lisansı (veya değerlendirme modunu kullanın).

## Adım 1: Maven projesini kurun

Yeni bir Maven projesi oluşturun veya mevcut `pom.xml` dosyanıza aşağıdaki bağımlılığı ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

`mvn clean install` komutunu çalıştırmak, kütüphaneyi indirir ve sınıfları sınıf yolunuza ekler.

## Adım 2: Grafik içeren Word belgesini yükleyin

İlk işlem, mevcut belgeyi açmaktır. `Document` sınıfı tüm dosyayı temsil eder.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Dosyayı yüklemek **değişiklik yapmaz**; sadece sorgulayabileceğiniz ve düzenleyebileceğiniz bellek içi bir temsil oluşturur.

## Adım 3: Gezinti için bir DocumentBuilder oluşturun

`DocumentBuilder`, belge ağacında gezinmek için bir imleç‑gibi API sağlar. İlk grafik şekline ulaşmak için bunu kullanacağız.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder belge başında başlar, ancak gerektiğinde daha sonra istediğiniz herhangi bir düğüme taşıyabilirsiniz.

## Adım 4: İlk grafik şeklinin alınması

Grafikler `Shape` düğümleri olarak depolanır. `NodeType.SHAPE` tipindeki alt düğümleri filtreleyerek grafik nesnesini çıkarabiliriz.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Belge birden fazla grafik içeriyorsa, `getChildNodes` üzerinden döngü kurabilir ve her `Shape` için `hasChart()` kontrolü yaptıktan sonra tip dönüşümü yapabilirsiniz.

## Adım 5: Grafiği döndürme (how to rotate chart)

Bir doughnut grafiği, içinde bir delik bulunan bir pasta grafiğidir. Döndürmek, ilk dilimin başlangıç açısını değiştirir.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

`setStartAngle` metodu derece cinsinden bir double değer bekler. Pozitif değerler saat yönünde, negatif değerler saat yönünün tersine döndürür.

## Adım 6: Doughnut deliğinin boyutunu değiştirme (change doughnut chart size)

Delik boyutu, grafiğin yarıçapının bir kesri olarak ifade edilir. `0.5` değeri, deliğin toplam yarıçapın %50’sini kapladığını gösterir.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**İpucu:** Geçerli aralık `0.0` (deliksiz, yani normal pasta) ile `0.9` (çok ince halka) arasındadır. Bu aralığın dışındaki değerler `IllegalArgumentException` fırlatır.

## Adım 7: Değiştirilmiş belgeyi kaydedin

Son olarak, değişiklikleri diske yazın.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

`DoughnutFormatted.docx` dosyasını Microsoft Word’de açtığınızda, doughnut grafiğinin %45 döndüğünü ve deliğin yarı yarıya küçültüldüğünü göreceksiniz.

## Tam, çalıştırılabilir örnek

Tüm parçaları bir araya getirerek, IDE’nize kopyalayıp yapıştırabileceğiniz tam program aşağıdadır:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Beklenen çıktı

Programı çalıştırdığınızda şu çıktı alınır:

```
Chart rotated and doughnut size changed successfully.
```

`DoughnutFormatted.docx` dosyasını açtığınızda, ilk dilimin %45 konumunda başladığı ve iç yarıçapın dış yarıçapın yarısını kapladığı bir doughnut grafiği görürsünüz.

## Yaygın varyasyonlar ve kenar durumları

| Durum | Ayarlanacak şey | Neden önemlidir |
|-----------|----------------|----------------|
| **Birden fazla grafik** | `getChildNodes(NodeType.SHAPE, true)` üzerinden döngü kurun ve her `shape.hasChart()` kontrol edin | İlk grafik yerine hedeflediğiniz grafiği değiştirmenizi sağlar |
| **Bar veya çizgi grafiği** | `setStartAngle` uygulanmaz; diğer görsel ayarlamalar için `chart.getSeries().get(0).setFillFormat(...)` kullanın | Tüm grafik tipleri döndürmeyi desteklemez; sadece doughnut/pasta grafiklerinde başlangıç açısı vardır |
| **Doughnut deliği olmayan grafik** | `setDoughnutHoleSize` atlayın veya önce `chart.setChartType(ChartType.DONUT)` ile grafik tipini doughnut’a çevirin | Deliği olmayan bir grafiğin delik boyutunu değiştirmek istisna fırlatır |
| **Büyük belgeler** | Hedefli gezinme için `DocumentBuilder.moveToDocumentStart()` ve `builder.moveToNode(chartShape)` kullanın | İlgisiz düğümlerin tam taranmasını önleyerek performansı artırır |

## Güvenilir grafik manipülasyonu için profesyonel ipuçları

* **Grafik referansını önbelleğe alın** – Birden fazla özelliği değiştirmeyi planlıyorsanız, `chartShape.getChart()` çağrısını tekrarlamak yerine yerel bir `Chart` değişkeni tutun.
* **Giriş değerlerini doğrulayın** – `setStartAngle` veya `setDoughnutHoleSize` çağırmadan önce aralığı kontrol edin, böylece çalışma zamanı hatalarından kaçının.
* **Lisans kullanın** – Değerlendirme modu ilk sayfaya bir filigran ekler. `License license = new License(); license.setLicense("Aspose.Words.lic");` kodu lisansı uygulayarak bunu kaldırır.

## Sonraki adımlar

Artık **how to rotate chart** ve **change doughnut chart size** konularını bildiğinize göre, diğer **modify chart in Word** senaryolarını keşfedebilirsiniz:

* `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())` ile dilim renklerini değiştirin.
* `chart.getSeries().get(0).setHasDataLabel(true)` ile veri etiketleri ekleyin.
* `chart.toImage(300, 300, ImageType.PNG)` kullanarak grafiği bir görüntü olarak dışa aktarın.

Bu uzantıların hepsi aynı desen izler: `Chart` nesnesini elde edin, uygun ayarlayıcıyı çağırın ve belgeyi kaydedin.

---

**Artık Java kullanarak Word’de doughnut grafikleri döndürüp yeniden boyutlandırmayı öğrendiniz.** Kodu diğer grafik tipleri için uyarlayabilir, daha büyük belge‑oluşturma süreçlerine entegre edebilir veya PowerPoint otomasyonu için Aspose.Slides ile birleştirebilirsiniz. Kodlamanın tadını çıkarın!


## Bir sonraki öğrenmeniz gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımları keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}