---
category: general
date: 2026-10-07
description: Word'de bir pasta grafiği oluşturmayı, veri serisi eklemeyi ve grafiği
  Java kullanarak PNG olarak kaydetmeyi öğrenin. Hızlı sonuçlar için adım adım rehberi
  izleyin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: tr
lastmod: 2026-10-07
og_description: 'Word''de hızlıca pasta grafiği oluşturun: Bu öğreticide veri serisi
  ekleme, grafiği oluşturma ve Word grafiğini bir görüntü (PNG) olarak kaydetme adımları
  gösterilmektedir. Tam kod örneğini izleyin.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Word'de pasta grafiği oluşturun ve PNG olarak dışa aktarın – rehber
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Word'de pasta grafiği nasıl oluşturulur ve PNG olarak kaydedilir
url: /tr/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de pasta grafiği nasıl oluşturulur ve PNG olarak kaydedilir

Eğer bir Microsoft Word dosyası içinde **pie chart** nesneleri oluşturmanız gerekiyorsa, bu kılavuz Java ile bunu tam olarak nasıl yapacağınızı gösterir. Ayrıca **add data series**'i grafiğe eklemeyi ve **save chart as PNG**'yi öğrenerek görseli Word dışına yeniden kullanılabilir hale getireceksiniz.

Bir grafiği doğrudan bir belge içinde oluşturmak, verileri ayrı bir grafik aracına aktarmaktan sizi kurtarır. Bu öğreticinin sonunda, içinde bir pasta grafiği ve diskte eşleşen bir PNG görüntüsü bulunan tam işlevsel bir Word dosyanız olacak.

## Önkoşullar

* Java 17 veya daha yeni bir sürüm yüklü.
* **GroupDocs.Viewer for Java** (veya `Document`, `Chart`, `ChartType` ve `ImageSaveOptions` sınıflarını sağlayan uyumlu bir kütüphane).
* Kütüphane bağımlılığını ekleyebileceğiniz bir Maven veya Gradle projesi.
* Koddaki bir klasörden referans verebileceğiniz bir giriş Word belgesi (`input.docx`).

Maven kullanıyorsanız, bağımlılığı ekleyin (`VERSION`'ı en son sürümle değiştirin):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Word'de pasta grafiği nasıl oluşturulur

Çözümün temeli üç eylem etrafında döner:

1. Kaynak `.docx` dosyasını yükle.
2. **Add data series**'i `PIE` tipinde yeni bir `Chart` nesnesine ekle.
3. **Save chart as PNG**'yi yaparak Word belgesinin yanına bir görüntü dosyası elde et.

Aşağıda her adım ayrıntılı olarak açıklanmıştır, ardından ihtiyacınız olan tam Java kodu gelir.

### Adım 1: Kaynak belgeyi yükle

Grafiği barındıracak Word dosyasını açmalısınız. `Document` sınıfı `.docx` içeriğini belleğe okur.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Why this matters*: Belgeyi yüklemek değiştirilebilir bir model oluşturur. Sonraki tüm grafik işlemleri bu bellek içi temsili değiştirir ve daha sonra diske kaydedilir.

### Adım 2: Grafiğe veri serisi ekle

**pie chart** oluşturmak bir `Chart` örneğiyle başlar. Yapıcı, üst `Document` ve grafik tipini (`ChartType.PIE`) alır. Grafik nesnesi oluşturulduktan sonra, sayısal değerler ve isteğe bağlı etiketlerle doldurursunuz.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Why this matters*: `add` metodu **add data series**'i grafiğe ekler. `values` içindeki her giriş pasta dilimi olur, `categories` ise lejand etiketlerini sağlar. İstediğiniz sayıda nokta verebilirsiniz; kütüphane dilim açılarını otomatik olarak hesaplar.

### Adım 3: Grafiği PNG olarak kaydet

Grafik belgeye eklendikten sonra görsel temsili dışa aktarabilirsiniz. Alt grafik nesnesindeki `save` metodu bir PNG dosyasını dosya sistemine yazar.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Why this matters*: Grafiği PNG olarak kaydetmek, orijinal Word dosyasına ihtiyaç duymadan web sayfalarına, e-postalara veya raporlara gömülebilen bir raster görüntü sağlar. `ImageSaveOptions` nesnesi format, çözünürlük ve diğer dışa aktarma ayarlarını kontrol etmenizi sağlar.

## Word'de pasta grafiği oluşturma – görünümü özelleştirme

Temel adımların ötesinde, renkleri, başlıkları veya veri etiketlerini özelleştirmek isteyebilirsiniz. Çoğu kütüphane bir `ChartOptions` veya benzeri nesne sunar. İşte bir başlık ekleyen ve dilim renklerini değiştiren hızlı bir örnek:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Bu özelleştirmeler isteğe bağlıdır ancak **generate pie chart in Word**'ün markanıza uygun nasıl yapılacağını gösterir.

## Word grafiğini görüntü olarak kaydet – alternatif yaklaşımlar

Eğer sadece görüntüye ihtiyacınız varsa ve belge içinde grafik olmadan, grafik şeklinin Word dosyasına eklenmesini atlayabilir ve grafiği oluşturduktan sonra doğrudan `save` metodunu çağırabilirsiniz. Kod aynı kalır; sadece grafiği belgenin gövdesine ekleyen adımları atlamanız yeterlidir.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

Bu teknik, toplu bir işlemde birçok grafik oluştururken ve sadece PNG çıktısı önemli olduğunda faydalıdır.

## Tam çalıştırılabilir örnek

Aşağıdaki sınıfı projenize kopyalayın, dosya yollarını ayarlayın ve çalıştırın. Program şunları yapacak:

1. `input.docx` dosyasını yükle.
2. **Create a pie chart**, **add data series**, ve belgeye göm.
3. **Save the chart as PNG** (`radial.png`).
4. Değiştirilmiş Word dosyasını `output.docx` olarak kaydet.



## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri içerir.

- [Java için Aspose.Words kullanarak sütun grafiği nasıl oluşturulur](/words/english/java/document-conversion-and-export/using-charts/)
- [.NET için Aspose.Words kullanarak Word Dağılım Grafiği Oluşturma](/words/english/net/working-with-charts/insert-scatter-chart/)
- [.NET için Aspose.Words kullanarak Word'e Sütun Grafiği Ekleme](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}