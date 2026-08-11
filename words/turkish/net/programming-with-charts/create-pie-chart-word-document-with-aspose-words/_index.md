---
category: general
date: 2026-08-10
description: Aspose.Words kullanarak pasta grafik Word belgesi oluşturun. Grafiği
  nasıl ekleyeceğinizi, pasta grafik renklerini nasıl özelleştireceğinizi ve C#'ta
  pasta dilimi rengini nasıl değiştireceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: tr
lastmod: 2026-08-10
og_description: Aspose.Words ile pasta grafik içeren Word belgesi oluşturun. Bu kılavuz,
  grafiği nasıl ekleyeceğinizi, pasta grafiği renklerini nasıl özelleştireceğinizi
  ve C# uygulamasında pasta dilimi rengini nasıl değiştireceğinizi açıklar.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Pasta grafiği Word belgesi oluşturma – Aspose.Words rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Aspose.Words ile pasta grafikli Word belgesi oluştur
url: /tr/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile Pasta Grafiği Word Belgesi Oluşturma

Programlı olarak **pasta grafiği Word belgesi** oluşturmanız gerekiyorsa, bu öğretici tam olarak nasıl yapılacağını gösterir. Aspose.Words for .NET kullanarak bir grafik eklemeyi, **pasta grafiği renklerini özelleştirmeyi** ve **pasta dilimi rengini değiştirmeyi** adım adım anlatacağız.

Tam, çalıştırılabilir bir örnek göreceksiniz; bu örneği Visual Studio’ya kopyalayıp çalıştırabilir ve oluşturulan *.docx* dosyasını hemen açarak stil verilen pasta grafiğini doğrulayabilirsiniz. Harici bir dokümantasyona ihtiyaç yok—gereken her şey bu rehberde.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 SDK veya daha yeni bir sürüm  
* Geçerli bir Aspose.Words for .NET lisansı (veya geçici değerlendirme anahtarı)  
* Visual Studio 2022 (veya herhangi bir C# IDE)  

Kod yalnızca `Aspose.Words` ve `Aspose.Words.Drawing.Charts` ad alanlarını kullanır; bu nedenle Aspose.Words kütüphanesi dışındaki ek NuGet paketlerine gerek yoktur.

## Pasta grafiği Word belgesi oluşturma – tam örnek

Aşağıdaki C# programı yeni bir Word belgesi oluşturur, bir pasta grafiği ekler, ilk iki dilimi stilize eder ve dosyayı kaydeder. Her adım ayrıntılı olarak açıklanmıştır.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Her adımın açıklaması

| Adım | Ne yapar | Neden önemlidir |
|------|----------|-----------------|
| **1** | Yeni bir `Document` ve bir `DocumentBuilder` oluşturur. | `DocumentBuilder`, grafikler gibi içerik eklemek için akıcı yöntemler sağlar. |
| **2** | `InsertChart` metodunu `ChartType.Pie` ve sabit bir boyutla çağırır. | `InsertChart`, **grafik ekleme** yöntemidir; genişlik/yükseklik belirlemek, grafiğin sayfada düzgün oturmasını sağlar. |
| **3** | Üç kategori ve sayısal değer içeren bir veri serisi ekler. | Veri olmadan bir pasta grafiği görünmez; doldurulması stil adımlarını gösterir. |
| **4** | İlk nokta için `Explosion` ayarlar. | Bir dilimi patlatmak, belirli bir bölüme dikkat çeker—ana veriyi vurgulamak için faydalıdır. |
| **5** | İlk iki nokta için `ForeColor` ayarlar. | Bu, **pasta grafiği renklerini özelleştirme**nin temelidir; herhangi bir `System.Drawing.Color` kullanılabilir. |
| **6** | Ek dilimler için **pasta dilimi rengini değiştirme** yöntemini gösterir. | Stil uygulamanın sadece ilk iki dilimle sınırlı olmadığını, her dilimi ayrı ayrı renklendirebileceğinizi gösterir. |
| **7** | Belgeyi `PieChartStyled.docx` olarak kaydeder. | Son çıktı Microsoft Word, Google Docs veya uyumlu herhangi bir görüntüleyicide açılabilir. |

#### Beklenen çıktı

`PieChartStyled.docx` dosyasını açtığınızda 400 × 300 pt boyutunda tek bir sayfa ve bir pasta grafiği görürsünüz:

* Dilim 1 (turuncu) dışarı doğru patlatılmıştır.  
* Dilim 2 (yeşil) patlatılmış dilimin yanında yer alır.  
* Dilim 3 (çelik‑mavisi) kalan bölümü doldurur.

Grafik, (30, 45, 25) veri değerlerini ve tanımladığınız özel renkleri yansıtır.

## Pasta grafiğini stilize etme – ek ipuçları

* **Tema renklerini kullanın** – `Color.Orange` gibi sabit kodlamalar yerine, renkleri belge temasından alabilirsiniz:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Veri etiketleri ekleyin** – grafikte yüzde değerlerini göstermek isterseniz:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Dinamik yeniden boyutlandırma** – grafik boyutunu sayfa kenar boşluklarına göre hesaplayın:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Bu varyasyonlar, temel örnek dışındaki **pasta stilizasyonu** esnekliğini gösterir.

## Yaygın sorular yanıtlandı

**S: Bu .NET Core ile çalışır mı?**  
C: Evet. Aspose.Words for .NET, .NET Core, .NET 5, .NET 6 ve sonraki sürümlerle uyumludur. Aynı NuGet paketini referans göstermeniz yeterlidir.

**S: Pasta yerine halka (donut) grafiği ihtiyacım olursa?**  
C: `ChartType.Pie` yerine `ChartType.Doughnut` kullanın. Aynı stil API’leri (`Explosion`, `ForeColor`) geçerlidir.

**S: Grafiği mevcut bir belgeye ekleyebilir miyim?**  
C: `new Document("Existing.docx")` ile mevcut dosyayı açın, o belge için bir `DocumentBuilder` oluşturun ve istediğiniz imleç konumunda `InsertChart` metodunu çağırın.

**S: Büyük veri setleriyle nasıl başa çıkılır?**  
C: Pasta grafikleri sınırlı sayıda kategori (genellikle < 10) için en uygunudur. Çok sayıda kategori için çubuk veya sütun grafiği düşünün.

## Tam kaynak kodu özeti

Aşağıda, kolay kopyala‑yapıştır için tek bir blokta tam program yer almaktadır:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Bu kodu çalıştırdığınızda, önceki bölümde açıklanan stil verilen pasta grafiği Word belgesi üretilir.

## Sonuç

Artık Aspose.Words kullanarak **pasta grafiği Word** belgeleri oluşturmayı, **pasta grafiği renklerini özelleştirmeyi** ve **pasta dilimi rengini programlı olarak değiştirmeyi** biliyorsunuz. Rehber, grafiği ekleme, veri doldurma, bir dilimi patlatma, özel renkler uygulama ve sonucu kaydetme konularını kapsadı.  

Bundan sonra, **pasta dışındaki grafik türlerini ekleme**, lejand ekleme veya birden çok grafik içeren çok sayfalı raporlar oluşturma gibi ilgili konuları keşfedebilirsiniz. Raporlama ihtiyaçlarınıza uygun farklı renk şemaları ve veri setleriyle deneyler yapın.

İyi kodlamalar!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Aspose.Words for .NET kullanarak Word'e Sütun Grafiği Ekle](/words/english/net/working-with-charts/insert-column-chart/)
- [Aspose.Words for .NET ile Word Belgesine Alan Grafiği Ekle](/words/english/net/working-with-charts/insert-area-chart/)
- [Aspose.Words for .NET kullanarak Word'e Dağılım Grafiği Oluştur](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}