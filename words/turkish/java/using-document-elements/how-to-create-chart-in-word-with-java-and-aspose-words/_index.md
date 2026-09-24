---
category: general
date: 2026-09-24
description: Java kullanarak Word'de grafik oluşturmayı, radyal bir grafik eklemeyi
  ve Aspose.Words ile belgeyi docx olarak kaydetmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: tr
lastmod: 2026-09-24
og_description: Java ve Aspose.Words ile Word'de grafik oluşturun. Bu öğreticide,
  radyal bir grafik eklemeyi, verileri özelleştirmeyi ve belgeyi docx olarak kaydetmeyi
  gösterir.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Java ile Word'de grafik oluşturma – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: Java ve Aspose.Words ile Word’de grafik nasıl oluşturulur
url: /tr/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java ve Aspose.Words ile Word'de Grafik Oluşturma

Java uygulamasından **create chart in Word** ihtiyacınız varsa, bu kılavuz sizi sürecin tamamı boyunca yönlendirecek. Radial bir grafik eklemeyi, isteğe bağlı olarak serilerini doldurmayı ve sonunda Aspose.Words for Java kütüphanesini kullanarak **save document as docx** işlemini göreceksiniz.

Bir Word dosyası içinde görsel veri oluşturmak, raporlama, faturalama veya otomatik belge üretimi için yaygın bir gereksinimdir. Bu öğreticinin sonunda, **create word document java** projeleriyle **add chart to Word** dosyalarına manuel düzenleme yapmadan grafik ekleyebileceksiniz.

## Önkoşullar

* Java Development Kit (JDK) 8 veya daha yeni bir sürüm.
* Bağımlılık yönetimi için Maven veya Gradle.
* IntelliJ IDEA, Eclipse veya VS Code gibi bir IDE.
* Geçerli bir Aspose.Words for Java lisansı (ücretsiz deneme sürümü geliştirme için çalışır).

Bu araçlar, aşağıdaki kod örnekleri için temel oluşturur.

## Adım 1: Maven projesini kurun

Yeni bir Maven projesi oluşturun (veya mevcut bir projeyi güncelleyin) ve Aspose.Words bağımlılığını `pom.xml` dosyanıza ekleyin:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

`mvn clean install` komutunu çalıştırmak, kütüphaneyi indirir ve `Document`, `DocumentBuilder` ve `ChartType` gibi sınıfları sınıf yolunda kullanılabilir hale getirir.

> **Pro tip:** Kütüphane sürümünü güncel tutun. Yeni sürümler daha fazla grafik tipi ekler ve render performansını artırır.

## Adım 2: Yeni bir Word belgesi oluşturun

**create chart in Word** için ilk programatik adım, boş bir `Document` nesnesi oluşturmaktır. Bu nesne, tüm `.docx` paketini temsil eder.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` bir imleç gibi çalışır; mevcut ekleme noktasını bilir ve metin, tablo ve grafikler için yöntemler sunar. Bu noktada **created word document java** stilinde – içerik eklemeye hazır temiz bir tuval elde etmiş olursunuz.

## Adım 3: Radial grafik ekleyin

Aspose.Words birçok grafik tipini destekler. **insert radial chart** yapmak için `insertChart` metodunu `ChartType.RADIAL` ile çağırın. Metot ayrıca genişlik ve yüksekliği puan cinsinden (1 point ≈ 1/72 inch) ister.

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

Dönen `Shape` nesnesi altında yatan grafik nesnesini içerir. Grafik, Word'deki radial grafikler için varsayılan olan 24.9° düzenine göre otomatik olarak ölçeklendirmeleri çizer.

### Neden radial grafik kullanmalı?

Radial grafik, veriyi bir daire etrafında sarar ve böylece döngüsel desenleri (ör. aylık satışlar, saat‑yüzü metrikleri) göstermek için idealdir. Aynı API çubuk, pasta veya çizgi grafikleri ekleyebilir, ancak radial tip ekstra stil kodu olmadan ayırt edici bir görünüm sağlar.

## Adım 4: (İsteğe Bağlı) Grafiğin seri verilerini doldurun

Grafiğin gerçek değerleri göstermesini istiyorsanız, seri ve nokta eklemeniz gerekir. Aşağıdaki kod parçası üç veri noktasına sahip tek bir seri ekler:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

İhtiyacınız kadar nokta eklemek için `add` çağrılarını tekrarlayabilirsiniz. Aspose.Words görsel temsili otomatik olarak günceller, böylece radial dilimler yeni değerlere göre ayarlanır.

> **Common question:** *Veritabanından veri bağlamam gerekirse ne olur?*  
> Satırları alın, döngüyle gezin ve döngü içinde `series.getDataPoints().add(value, label)` metodunu çağırın. API iş parçacığı‑güvenlidir ve sağladığınız herhangi bir `ResultSet` ile çalışır.

## Adım 5: Belgeyi DOCX olarak kaydedin

Grafik hazır olduğunda, son adım **save document as docx** işlemidir. `save` metodu çıktı formatını dosya uzantısından belirler.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Oluşturulan dosya, Microsoft Word, LibreOffice veya DOCX formatını destekleyen herhangi bir görüntüleyicide açılabilen tam işlevsel bir radial grafik içerir. `.docx` uzantısını kullandığımız için Word dosyayı Open XML formatında kaydeder; bu, Word belgeleri için modern standarttır.

### Sonucu doğrulama

`RadialChartDemo.docx` dosyasını Word'de açın:

1. Ortalanmış bir radial grafik içeren tek bir sayfa görmelisiniz.
2. Seri verisi eklediyseniz, grafik Q1‑Q4 olarak etiketlenmiş dört dilim gösterir.
3. Grafiğe sağ‑tıklayın → **Edit Data** (Veriyi Düzenle) seçeneğiyle temel veri tablosunu doğrulayın.

Grafik boş görünüyorsa, serileri eklemeden önce `chart.getChart()` çağırdığınızdan ve belge oluşturucunun imlecinin grafiği eklemek istediğiniz konumda olduğundan emin olun.

## Adım 6: Grafiklerle çalışmak için ileri ipuçları

| Tip | Neden önemli |
|-----|----------------|
| **Set chart style** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | Her öğeyi manuel olarak biçimlendirmeye gerek kalmadan görsel tutarlılığı artırır. |
| **Resize after insertion** – `chart.setWidth(500); chart.setHeight(350);` | Sayfa düzenine göre grafik boyutunu hassas bir şekilde ayarlamanızı sağlar. |
| **Add a title** – `chart.getChart().getTitle().setText("Revenue Overview");` | Belgeyi çevreleyen metin olmadan gören okuyuculara bağlam sağlar. |
| **Export to PDF** – `doc.save("RadialChartDemo.pdf");` | Dağıtım için düzenlenemez bir sürüme ihtiyaç duyduğunuzda faydalıdır. |
| **License handling** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | Üretim sürümlerinde değerlendirme filigranını önler. |

Bu iyileştirmeler isteğe bağlıdır ancak **add chart to Word** öğrendikten sonra grafiği nasıl daha da özelleştirebileceğinizi gösterir.

## Sonuç

Artık Java kullanarak **create chart in Word**, **insert radial chart**, isteğe bağlı olarak veri ekleme ve **save document as docx** işlemlerini gösteren eksiksiz, bağımsız bir örneğe sahipsiniz. Aynı desen diğer grafik tipleri için de çalışır; bu nedenle öğreticiyi ihtiyacınıza göre çubuk, çizgi veya pasta grafiklerine genişletebilirsiniz.

Sonraki adımda şunları keşfedebilirsiniz:

* **create word document java** projeleri, tablolar, görseller ve birden fazla grafik birleştirir.
* **save document as docx** ile **save document as pdf**'i birlikte kullanarak çok‑formatlı raporlama.
* REST API'lerinden veya veritabanlarından dinamik veri ekleyerek grafiklerinizi zenginleştirme.

Stil seçenekleri, grafik boyutları ve veri kaynaklarıyla denemeler yapmaktan çekinmeyin. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Java için Aspose.Words ile sütun grafik nasıl oluşturulur](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words ile boş Word belgesi oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Java ile Word Belgesi Oluşturma – Gölge Efektiyle Dikdörtgen Şekil Ekle](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}