---
category: general
date: 2026-09-21
description: Boş bir Word belgesi oluşturun ve DocumentBuilder kullanarak bir Word
  dosyasına radar grafiği eklemeyi adım adım öğrenin – adım adım rehber.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: tr
lastmod: 2026-09-21
og_description: Aspose.Words ile boş bir Word belgesi oluşturun ve bir Word dosyasına
  radar grafiği ekleyin. Word belgesi grafiğini hızlı bir şekilde oluşturmak için
  bu öğreticiyi izleyin.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: Boş bir Word belgesi oluşturun ve bir radar grafiği ekleyin – tam C# rehberi
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: C# ile boş bir Word belgesi oluşturma ve radar grafiği ekleme
url: /tr/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile boş bir Word belgesi oluşturma ve radar grafiği ekleme

Eğer **boş bir Word belgesi oluşturma** ve içine bir radar (radial) grafik yerleştirme ihtiyacınız varsa, bu öğretici çalıştırmaya hazır bir çözüm sunar. Aspose.Words .NET'i kullanarak dosyayı nasıl oluşturacağınızı, grafiği nasıl ekleyeceğinizi ve sonucu nasıl kaydedeceğinizi birkaç kısa adımda göreceksiniz.

Boş bir belge, herhangi bir otomatik raporlama senaryosu için temiz bir tuval sağlar ve radar grafiği eklemek, çok boyutlu verileri doğrudan Word içinde görselleştirmenize olanak tanır. Bu rehberin sonunda, manuel düzenleme yapmadan bir Word belgesi grafiği oluşturabileceksiniz.

## Öğrenecekleriniz

* C# ile **boş bir Word belgesi oluşturma** programatik olarak nasıl yapılır.
* `DocumentBuilder` kullanarak **radar grafiği ekleme** için gereken tam kod.
* **grafik word dosyasına ekleme** ve boyutunu özelleştirme yolları.
* **Word belgesi grafiği oluşturma** ve çıktıyı doğrulama.
* **radial chart word** dosyalarına ekleme ipuçları, yaygın hatalar dahil.

### Önkoşullar

* .NET 6.0 veya üzeri (kod .NET Framework 4.6+ ile de çalışır).
* Aspose.Words for .NET (NuGet paketi `Aspose.Words` sürüm 23.9 veya daha yeni).
* C# ve Visual Studio ya da tercih ettiğiniz IDE hakkında temel bilgi.

## C# ile boş bir Word belgesi oluşturma

İlk adım, boş bir `Document` nesnesi oluşturmaktır. Bu nesne tamamen boş bir `.docx` dosyasını temsil eder.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` dosya yapısını oluşturur ancak henüz içinde bölüm veya sayfa bulunmaz. Aspose.Words, içerik eklemeye başladığınızda otomatik olarak varsayılan bir bölüm ekler; bu yüzden sonraki adım ekstra yapılandırma gerektirmez.

## Word dosyasına radar grafiği ekleme

Radar grafiği (radial chart olarak da bilinir), verileri merkezi bir noktadan yayılan eksenler üzerinde görselleştirir. Aspose.Words bu amaçla `DocumentBuilder.insertChart` metodunu sunar.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` bir `Chart` nesnesi döndürür; bu nesneyi daha da yapılandırabilirsiniz. Grafik, builder varsayılan olarak belgenin başlangıcında konumlandığı için boş belgenin ilk sayfasında görünür.

## Word dosyasına grafik ekleme – veri serileri ekleme

Veri olmadan bir grafik görünmez. Radar grafiğini anlamlı kılmak için bir veya daha fazla seri ekleyin.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

İhtiyacınız kadar seri ekleyebilirsiniz. Her seri ayrı bir isim taşıyabilir; bu isim grafik efsanesinde gösterilir. Veri noktaları radial eksenlere karşılık gelir; eklediğiniz sıraya göre daire etrafındaki konumları belirlenir.

## Word belgesi grafiği oluşturma – dosyayı kaydetme

Grafiği oluşturduktan sonra belgeyi diske kaydedin. Yazma izninizin olduğu bir konum seçin.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Oluşturulan `.docx` dosyasını Microsoft Word’de açtığınızda, 400 × 300 puan boyutunda bir radar grafiğiyle dolu boş bir sayfa göreceksiniz; grafik örnek veriyle doldurulmuş olacaktır.

### Beklenen çıktı

* Masaüstünüzde `RadialChartExample.docx` adlı bir dosya.
* İlk sayfada “Series 1” etiketiyle beş veri noktasına sahip bir radar grafiği.
* Belge boş başladığı için ek metin bulunmaz.

## Radial chart word ekleme – yaygın kenar durumlarıyla başa çıkma

### 1. Grafik boyutunu eklemeden sonra değiştirme

İlk boyutlar düzeninize uymuyorsa, grafiği şu şekilde yeniden boyutlandırın:

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. Grafiği belirli bir konuma ekleme

`InsertChart` çağırmadan önce builder imlecini bir yer imine, tablo hücresine veya paragrafına taşıyabilirsiniz.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. Grafik görünümünü özelleştirme

Aspose.Words tam grafik nesne modelini açığa çıkarır; başlıklar, eksen etiketleri ve renkler gibi özellikleri ayarlayabilirsiniz.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. Eksik fontlarla başa çıkma

Hedef ortam grafikte kullanılan bir fonta sahip değilse, Aspose.Words varsayılan bir fontla değiştirir. Tutarlılığı sağlamak için gerekli fontları gömmek gerekir:

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. Diğer formatlara dışa aktarma

Aynı belge, ekstra kod değişikliği yapmadan PDF, HTML veya PNG olarak kaydedilebilir:

```csharp
doc.Save("RadialChartExample.pdf");
```

## Tam, çalıştırılabilir örnek

Tüm parçaları bir araya getirdiğinizde kopyalayıp yapıştırıp çalıştırabileceğiniz tek bir program elde edersiniz.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Bu programı çalıştırın, oluşturulan dosyayı açın; dağıtıma hazır profesyonel bir radar grafiği göreceksiniz.

## Sonuç

Artık **boş bir Word belgesi oluşturma**, **radar grafiği ekleme** ve Aspose.Words kullanarak **Word belgesi grafiği oluşturma** konularını biliyorsunuz. Yukarıdaki adımları izleyerek herhangi bir otomatik raporlama hattına **radial chart word** dosyaları ekleyebilir, boyut, stil ve ek format dışa aktarmalarını özelleştirebilirsiniz.

**Sonraki adımlar**

* Diğer grafik türlerini keşfedin (`ChartType.Column`, `ChartType.Pie`) ve raporlama araç kutunuzu genişletin.
* `InsertChart` metodunu tekrar tekrar çağırarak tek bir sayfada birden fazla grafik birleştirin.
* Veri tabanı ya da CSV dosyasından veri çekerek serileri dinamik olarak doldurun.
* Koşullu veri etiketleri ve grafik şablonları gibi gelişmiş biçimlendirme seçenekleri için Aspose.Words belgelerini inceleyin.

Kodu denemekten, boyutları ayarlamaktan veya örnek verileri gerçek iş ölçütleriyle değiştirmekten çekinmeyin. İyi kodlamalar!

## Bir Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalarla tam çalışan kod örnekleri içerir; böylece ek API özelliklerini öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}