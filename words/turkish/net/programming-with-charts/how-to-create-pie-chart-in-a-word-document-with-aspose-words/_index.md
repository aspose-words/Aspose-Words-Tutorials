---
category: general
date: 2026-09-21
description: Aspose.Words kullanarak pasta grafiği oluşturmayı ve grafiği Word’e eklemeyi,
  pasta grafiğine veri etiketleri eklemeyi ve pasta grafiğinde yüzde değerlerini göstermeyi
  sadece birkaç adımda öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: tr
lastmod: 2026-09-21
og_description: Aspose.Words kullanarak Word'de pasta grafiği oluşturun, grafiği Word'e
  ekleyin, pasta grafiğine veri etiketleri ekleyin ve pasta grafiğinde yüzde değerlerini
  gösterin—hepsi net kod örnekleriyle.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Aspose.Words ile Word'de pasta grafiği oluşturma – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Aspose.Words ile bir Word belgesinde pasta grafiği nasıl oluşturulur
url: /tr/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile Word belgesinde pasta grafiği nasıl oluşturulur

Programlı olarak **pasta grafiği oluşturmanız** gerektiğinde, Aspose.Words bunu çok basit hâle getirir. Bu öğreticide **grafiği Word’e ekleme**, serileri yapılandırma, **pasta grafiğine veri etiketleri ekleme** ve sonunda **pasta grafiğinde yüzde gösterme** konularını göreceksiniz, böylece görsel tam değerleri aktarır. Sonunda, herhangi bir .NET projesine ekleyebileceğiniz tam, çalıştırılabilir bir örnek elde edeceksiniz.

Bu kılavuz, bilmeniz gereken her şeyi kapsar: gerekli NuGet paketleri, tam C# kaynağı, her API çağrısının neden önemli olduğuna dair açıklamalar ve grafiği özelleştirme ipuçları. Harici bir belgeye ihtiyaç yok—kopyalayın, çalıştırın ve uyarlayın.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 SDK veya daha yeni bir sürüm.  
* Visual Studio 2022 (veya .NET’i destekleyen herhangi bir IDE).  
* Aspose.Words for .NET lisansı (test için ücretsiz deneme sürümü yeterli).  
* C# ve Word belge yapıları hakkında temel bilgi.

Bu gereksinimlere sahipseniz, doğrudan koda geçebilirsiniz.

## Adım 1: Projeyi oluşturun ve Aspose.Words’u içe aktarın

Yeni bir konsol projesi oluşturun ve Aspose.Words NuGet paketini ekleyin:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

Paket, kullanacağımız `Chart` ve `ChartSeries` sınıflarını içeren `Aspose.Words.Drawing.Charts` ad alanını içerir.

> **İpucu:** Lisans dosyanızı (`Aspose.Words.lic`) proje kök dizinine koyun ve başlangıçta yükleyin; böylece değerlendirme filigranlarından kaçınmış olursunuz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Adım 2: Boş bir belge ve DocumentBuilder oluşturun

`Document`, Word dosyasını temsil ederken, `DocumentBuilder` içerik eklemek için akıcı bir API sağlar.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Neden önemli:** `DocumentBuilder`, mevcut ekleme noktasını tutar ve grafiğin belge akışında tam istediğiniz yerde görünmesini sağlar.

## Adım 3: Word belgesine bir pasta grafiği ekleyin

Şimdi **grafiği Word’e ekliyoruz**. `InsertChart` yöntemi, grafik türünü, genişliği ve yüksekliği (puan cinsinden) alır.

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

Bu aşamada grafik, varsayılan veri serisi olarak yer tutucu değerler (25, 25, 25, 25) içerir. İsterseniz daha sonra değiştirebilirsiniz.

## Adım 4: İlk seriye erişin ve veri etiketlerini özelleştirin

Bir pasta grafiğinde genellikle tek bir seri bulunur. **Pasta grafiğine veri etiketleri eklemek** için seriyi alıp yüzde gösterimini etkinleştiririz.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**`ShowPercentage` ayarlamamızın nedeni:** Bu bayrak, Aspose.Words’a her dilimin katkısını hesaplayıp yüzde olarak göstermesini söyler. `Position` özelliği ise etiketin dilimin üzerine çakışmamasını sağlar; bu, özellikle dilimler küçük olduğunda okunabilirliği artırır.

## Adım 5: (İsteğe bağlı) Yer tutucu verileri değiştirin

Belirli değerler kullanmak istiyorsanız, varsayılan noktaları şu şekilde değiştirin:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

Gösterilen yüzde değerleri, yeni değerleri yansıtacak şekilde otomatik olarak ayarlanır.

## Adım 6: Belgeyi kaydedin

Son olarak belgeyi diske yazın. Uzantı formatı belirler; `.docx` modern bir Word dosyası oluşturur.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

Programı çalıştırdığınızda **PieChart.docx** adlı bir dosya çıktı klasöründe oluşturulur. Microsoft Word’de açtığınızda, her dilimin yüzdeyle etiketlendiği bir pasta grafiği görürsünüz; etiketler dilimlerin dışına yerleştirilir.

### Beklenen çıktı

Oluşturulan belgeyi açtığınızda şunları görmelisiniz:

* 400 × 300 pt boyutunda tek bir pasta grafiği.  
* Dört dilim (veya eklediğiniz nokta sayısı kadar).  
* “%40”, “%30” gibi yüzde etiketleri, her dilimin dış kısmında gösterilir.

Etiketler dilimlerin içinde görünüyorsa, `ChartDataLabelPosition.OutsideEnd` değerinin doğru ayarlandığını kontrol edin.

## Adım 7: Yaygın varyasyonlar ve kenar durumları

### Grafiğe başlık ekleme

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Dilim renklerini değiştirme

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Boş bir seriyle başa çıkma

Veri kaynağınız boş olabilecekse, `IndexOutOfRangeException` hatasından kaçınmak için şu kontrolü ekleyin:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Word yerine PDF olarak dışa aktarma

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

Aynı grafik oluşturma mantığı geçerlidir; Aspose.Words Word düzenini otomatik olarak PDF’ye dönüştürür.

## Tam kaynak kodu

Aşağıda, çalıştırmaya hazır tam program yer alıyor. `Program.cs` dosyasına kopyalayıp `dotnet run` komutunu çalıştırın.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Sonuç

Artık Aspose.Words kullanarak bir Word dosyasında **pasta grafiği oluşturma**, **grafiği Word’e ekleme**, **pasta grafiğine veri etiketleri ekleme** ve **pasta grafiğinde yüzde gösterme** konularını biliyorsunuz. Örnek, proje kurulumundan son belgeye kadar tam iş akışını gösteriyor; böylece gösterge panelleri, raporlar veya otomatik fatura üretimi gibi senaryolara uyarlayabilirsiniz.  

Sonraki adımda, **grafiklerde yüzde gösterimi**, grafik renklerini özelleştirme veya belgeyi dağıtım için PDF’ye dönüştürme gibi ilgili konuları keşfedin. Aynı `InsertChart` yöntemiyle farklı grafik türlerini (Bar, Line) deneyerek otomasyon yeteneklerinizi genişletin.

İyi grafikler!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalar ve tam çalışan kod örnekleri içerir; böylece ek API özelliklerini öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Aspose.Words for .NET ile Word’e Sütun Grafiği Ekleme](/words/english/net/working-with-charts/insert-column-chart/)
- [Aspose.Words for .NET ile Word Scatter Grafiği Oluşturma](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Aspose.Words for .NET ile Word Belgesine Alan Grafiği Ekleme](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}