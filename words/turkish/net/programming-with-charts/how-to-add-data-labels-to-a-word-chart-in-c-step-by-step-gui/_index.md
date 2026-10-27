---
category: general
date: 2026-08-04
description: Aspose.Words ile C#’ta veri etiketleri nasıl eklenir. Grafik düzenlemeyi,
  grafik veri etiketlerini ortalamayı, grafikte yüzde göstermeyi ve grafik veri etiketlerini
  özelleştirmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: tr
lastmod: 2026-08-04
og_description: C# kullanarak Aspose.Words ile veri etiketleri nasıl eklenir. Bu öğreticide
  grafiği nasıl düzenleyeceğinizi, veri etiketlerini nasıl ortalayacağınızı, grafikte
  yüzde nasıl göstereceğinizi ve veri etiketlerini nasıl özelleştireceğinizi gösterir.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: C#'ta Word grafiğine veri etiketleri ekleme – tam rehber
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: C#'ta Word grafiğine veri etiketleri ekleme – adım adım rehber
url: /tr/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta bir Word grafiğine veri etiketleri ekleme – adım adım rehber

Eğer bir Word belgesi içinde yer alan bir grafiğe **how to add data labels** eklemeniz gerekiyorsa, bu rehber çalıştırmanız gereken tam kodu gösterir. Grafik özelliklerini nasıl düzenleyeceğinizi, grafik veri etiketlerini ortalamayı, grafikte yüzde göstermeyi ve herhangi bir senaryo için grafik veri etiketlerini özelleştirmeyi göreceksiniz.

Bu öğretici, mevcut bir grafiği değiştirmek için gereken her şeyi kapsar; belgeyi yüklemekten değişiklikleri kalıcı hale getirmeye kadar. Harici referanslara gerek yok—sadece Aspose.Words for .NET kütüphanesi ve temel bir C# geliştirme ortamı yeterlidir.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 (veya daha yeni bir sürüm) yüklü.
* Aspose.Words for .NET sürüm 23.9 veya daha yeni bir sürüm.  
  NuGet üzerinden şu şekilde kurabilirsiniz:

```bash
dotnet add package Aspose.Words
```

* En az bir grafik içeren bir Word dosyası (`input.docx`).

## C#'ta bir Word grafiğine veri etiketleri ekleme

Aşağıdaki bölümler, her adımı size adım adım gösterir. Birincil anahtar kelime **how to add data labels** anlatım içinde ve kod yorumlarında doğal olarak yer alır, önerilen yoğunlukta kalır.

### Adım 1 – Grafiği içeren Word belgesini yükleyin

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Bu adımın önemi*: `Document` nesnesi tüm Word dosyasını temsil eder. Yüklemek, grafikleri barındıran şekiller de dahil olmak üzere her düğüme erişim sağlar.

### Adım 2 – Belgede ilk grafiği alın

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Bu adımın önemi*: Grafikler `Shape` düğümleri içinde depolanır. Alınan düğüm `Shape` tipine dönüştürülüp `GetChart()` çağrıldığında, serileri, eksenleri ve etiket koleksiyonlarını ortaya çıkaran bir `Chart` nesnesi elde edilir.

### Adım 3 – Veri etiketi özelleştirmesini etkinleştirin ve grafikte yüzde gösterin

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Bu adımın önemi*: `ShowPercentage` ayarı, Aspose.Words'e her dilimin toplam içindeki katkısını hesaplayıp göstermesini söyler. Bu, ikincil anahtar kelime **show percentages in chart** ile doğrudan ilgilidir.

### Adım 4 – Etiket yerleşimini her veri noktasının ortasına değiştirin

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Bu adımın önemi*: `Position` özelliği, etiketin veri noktasına göre nerede görüneceğini kontrol eder. `Center` kullanmak, ikincil anahtar kelime **center chart data labels** gereksinimini karşılar ve pasta ya da halka grafiklerde okunabilirliği artırır.

### Adım 5 – Grafik veri etiketlerini daha da özelleştirin (isteğe bağlı)

Daha fazla kontrol gerekiyorsa, yazı tipi, renk veya kılavuz çizgilerini ayarlayabilirsiniz:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Bu ayarlar, ikincil anahtar kelime **customize chart data labels**'ı gösterir ve görünümü marka yönergelerine göre nasıl uyarlayabileceğinizi demonstrasyon eder.

### Adım 6 – Değiştirilen belgeyi kaydedin

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Bu adımın önemi*: Kaydetme, güncellenmiş grafiği Word belgesine yazar ve dosya Microsoft Word'de açıldığında yeni veri etiketlerinin görünür olmasını sağlar.

## Tam, çalıştırılabilir örnek

Aşağıda kopyalayıp yapıştırıp çalıştırabileceğiniz eksiksiz bir program yer alıyor. Gerekli tüm `using` yönergeleri ve her satırı açıklayan yorumlar içerir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Beklenen sonuç

`output.docx` dosyasını Microsoft Word'de açtığınızda grafik şu şekilde görüntülenecek:

* Her dilimin yanında yüzde değerleri (ör. **25 %**, **40 %**, …).
* Etiketler her veri noktasının ortasında konumlandırılmış.
* Uyguladığınız ek stilizasyonlar, örneğin kalın kırmızı metin gibi.

Bu görsel ipuçları, özellikle sunumlarda veya raporlarda grafiği daha kolay yorumlamanızı sağlar.

## Veri etiketlerinin ötesinde grafik özelliklerini düzenleme

Bu rehberin odak noktası **how to add data labels** olsa da, **how to edit chart** gibi başlık, lejand konumu veya eksen biçimlendirme gibi ayarları da değiştirmek isteyebilirsiniz. `Chart` nesnesi `Title`, `Legend` ve `AxisX/AxisY` gibi özellikler sunar. Örneğin, grafik başlığını değiştirmek için:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Tüm grafik değişiklikleri aynı desenle yapılır: grafiği alın, özelliklerini ayarlayın, ardından belgeyi kaydedin.

## Yaygın tuzaklar ve en iyi uygulama ipuçları

| Tuzak | Neden olur | Önerilen çözüm |
|---|---|---|
| Grafik bir grup şeklin içinde. | `GetChild(NodeType.Shape, …)` dış grubu döndürür, içteki grafiği değil. | `shape.HasChart` özelliğine sahip bir şekil için özyinelemeli arama yapın. |
| Kaydetme sonrası veri etiketleri görünmüyor. | `ShowValue` veya `ShowPercentage` `true` olarak ayarlanmamış. | Gerektiği gibi hem `ShowValue` hem de `ShowPercentage` değerlerini açıkça `true` yapın. |
| Küçük dilimlerde etiketler çakışıyor. | Ortalanmış konum kalabalığa neden olabilir. | Dış konum için `ChartDataLabelPosition.OutSideEnd` kullanın veya `LeaderLines` özelliğini etkinleştirin. |

Bu ipuçlarını uygulayarak farklı grafik tiplerinde tutarlı sonuçlar elde edebilirsiniz.

## Sonuç

Artık C# kullanarak bir Word grafiğine **how to add data labels** ekleyebileceğinizi biliyorsunuz. Öğreticide grafiği almayı, etiket görünürlüğünü etkinleştirmeyi, etiketleri ortalamayı, yüzde göstermeyi ve görünümü özelleştirmeyi ele aldık. Bu bilgiyle aynı zamanda **how to edit chart** detaylarını, **center chart data labels**, **show percentages in chart** ve **customize chart data labels** gibi işlemleri de gerçekleştirebilirsiniz.

Daha fazlasını keşfetmeye hazır mısınız? Birden fazla seri ekleyin, koşullu biçimlendirme uygulayın veya grafiği resim olarak dışa aktarın. Aspose.Words API, kapsamlı grafik manipülasyon yetenekleri sunar—veriniz için mükemmel görsel temsili bulmak için deneyin.

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Grafik Veri Etiketini Özelleştir](/words/english/net/programming-with-charts/chart-data-label/)
- [Bir Grafikte Veri Etiketleri İçin Varsayılan Seçenekleri Ayarla](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Bir Grafikte Tek Bir Veri Noktasını Özelleştir](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}