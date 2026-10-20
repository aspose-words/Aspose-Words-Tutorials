---
category: general
date: 2026-10-20
description: Aspose.Words kullanarak bir Word belgesinde pasta grafiği oluşturma –
  rengi ayarlama, dilimi patlatma ve Word belgesini kaydetme adım adım rehberi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: tr
lastmod: 2026-10-20
og_description: Aspose.Words ile bir Word belgesinde pasta grafiği oluşturun. Renk
  ayarlamayı, dilimi patlatmayı ve Word belgesini tek bir çalıştırılabilir örnekte
  kaydetmeyi öğrenin.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Word belgesinde pasta grafiği oluşturma – tam C# rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Aspose.Words ile bir Word belgesinde pasta grafiği nasıl oluşturulur
url: /tr/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile bir Word belgesinde pasta grafiği nasıl oluşturulur

Bir Word dosyası içinde **pasta grafiği oluşturmanız** gerektiğinde, bu kılavuz tam olarak nasıl yapılacağını gösterir. Özel bir renk ayarlamayı, vurgulama için bir dilimi patlatmayı ve sonunda **grafiği gömülü olarak Word belgesini kaydetmeyi** öğreneceksiniz.

Grafikleri programlı olarak oluşturmak, Word'ü açıp bir grafik ekleme ve görünümünü ayarlama gibi manuel adımları ortadan kaldırır. Bu öğreticinin sonunda, bir pasta grafiği oluşturan, özelleştiren ve sonucu diske yazan tam çalışan bir C# konsol uygulamanız olacak.

## Prerequisites

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 SDK veya daha yeni bir sürüm  
* Geçerli bir Aspose.Words for .NET lisansı (veya ücretsiz deneme anahtarı)  
* Visual Studio 2022 veya VS Code gibi bir IDE  

`Aspose.Words` dışındaki ek NuGet paketlerine ihtiyaç yoktur.

## How to create pie chart in a Word document

İlk adım bir `Document` ve bir `DocumentBuilder` örneği oluşturmaktır. Builder, grafik ekleme dahil yüksek‑seviye Word özelliklerine erişim sağlar.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

Bu noktada belge zaten temel bir pasta grafiği içeriyor. Sonraki bölümler **dilimi nasıl patlatılır**, **renk nasıl ayarlanır** ve **Word belgesi nasıl kaydedilir** konularını açıklıyor.

## How to explode slice for emphasis

Bir dilimi patlatmak, onu pastanın geri kalanından ayırarak okuyucunun dikkatini çeker. Aspose.Words API, patlatma mesafesini puan cinsinden belirtmenize olanak tanır.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Neden dilimi patlatmalısınız? “En çok satan ürün” gibi belirli bir kategoriyi vurgulayan raporlarda görsel ayrım, veri noktasını anında tanınabilir kılar.

## How to set color on a chart slice

Özel renkler marka tutarlılığı ve okunabilirliği artırır. Belirli bir veri noktasına herhangi bir `System.Drawing.Color` atayabilirsiniz.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Sadece önceden tanımlı renklerle sınırlı değilsiniz; kesin tonlar için `Color.FromArgb` değeri oluşturabilirsiniz.

## How to save Word document with the chart

Grafik istediğiniz gibi göründüğünde, dosyayı kalıcı hale getirmek basittir. `Document.Save` yöntemi, belirttiğiniz formatta belgeyi yazar—burada varsayılan `.docx` kullanıyoruz.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Program çalıştırıldığında `PieChart.docx` oluşturulur. Microsoft Word’de dosyayı açtığınızda, ilk dilimin patlatılmış ve kırmızı renkte olduğu bir pasta grafiği görürsünüz; bu, kodun tam olarak belirttiği şekildedir.

### Expected result

* `C:\Temp` içinde **PieChart.docx** adlı bir Word dosyası.  
* Belge, boyutu 400 × 300 point olan tek bir pasta grafiği içerir.  
* Dilim 0, 20 point kaydırılmış ve kırmızı renkle doldurulmuş, diğer dilimler ise varsayılan renklerini korur.  

Patlatma ve rengi, Word’de grafiği seçip dilim özelliklerini inceleyerek doğrulayabilirsiniz.

## Pro tips and common pitfalls

* **Pro tip:** Grafik başlığını veya lejandı değiştirmek istiyorsanız, kaydetmeden önce `pieChart.Title.Text` ve `pieChart.Legend` özelliklerini kullanın.  
* **Dikkat:** Varsayılan veri noktalarını temizlemeyi unutmak, ekstra ve istenmeyen dilimlere yol açabilir. Kendi verilerinizi eklemeden önce her zaman `Series[0].DataPoints.Clear()` çağırın.  
* **Performans ipucu:** Büyük belgelerde, birden çok builder oluşturmak yerine tek bir `DocumentBuilder` örneğini yeniden kullanın; bu bellek yükünü azaltır.

## How to create chart using Aspose.Words (additional context)

`InsertChart` yöntemi, pasta grafiklerinin yanı sıra sütun, çizgi ve alan grafikleri gibi birçok grafik türünü destekler. Farklı bir türe geçmek için `ChartType.Pie` yerine istenen enum değerini, örneğin `ChartType.Column`, kullanın. Dilim patlatma ve renk ayarlama gibi özelleştirme adımları aynı kalıpla devam eder, ancak tüm grafik türleri “explosion” özelliğini sunmaz.

## How to explode slice in other chart types

Sadece pasta‑türündeki grafikler `SetExplosion` metodunu sunar. Bunu bir çubuk grafik üzerinde çağırırsanız API bir `ArgumentException` fırlatır. Bu durumlarda, belirli bir çubuğu vurgulamak için veri etiketleri veya açıklama balonları kullanmayı düşünün.

## How to set color on a series instead of a single slice

Bir serideki tüm dilimlerin aynı rengi paylaşmasını istiyorsanız, veri noktaları üzerinde döngü yapın:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Bu yaklaşım, birden çok grafik arasında tutarlı bir renk şeması gerektiğinde kullanışlıdır.

## How to save Word document in other formats

Aspose.Words, PDF, HTML ve birçok başka formata dışa aktarabilir. `Save` içinde dosya uzantısını değiştirin ve isteğe bağlı olarak bir `SaveOptions` nesnesi geçin:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

Grafik render motoru, renkleri ve patlatma ayarlarını koruyarak grafiği hedef formata otomatik olarak dönüştürür.

## Conclusion

Artık bir Word belgesinde **pasta grafiği oluşturmayı**, **dilimi patlatma** ve **renk ayarlama** yoluyla görünümünü özelleştirmeyi ve sonunda **grafiği gömülü olarak Word belgesini kaydetmeyi** biliyorsunuz. Bu uçtan uca örnek, rapor üretimini, gösterge tablolarını veya görsel verilerin programlı olarak eklenmesi gereken herhangi bir senaryoyu otomatikleştirmeniz için sağlam bir temel sağlar.

### Next steps

* Diğer grafik türlerini (`ChartType.Column`, `ChartType.Line`) keşfederek raporlama araç kutunuzu genişletin.  
* Tek bir belgede birden çok grafik birleştirerek kapsamlı gösterge tabloları oluşturun.  
* Dilimlerde doğrudan yüzde veya değer göstermek için `ChartDataLabel` ile deney yapın.  

Kodu kendi veri kaynaklarınıza uyarlamaktan çekinmeyin—verileri bir veritabanından, bir API’den veya bir CSV dosyasından alıyor olun, aynı Aspose.Words iş akışı geçerlidir. İyi grafikler!

## What Should You Learn Next?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım‑adım açıklamalar içerir.

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}