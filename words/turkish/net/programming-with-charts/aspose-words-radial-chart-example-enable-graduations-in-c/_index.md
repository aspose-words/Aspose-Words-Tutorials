---
category: general
date: 2026-10-13
description: C# ve Aspose.Words 24.9+ kullanarak bir radyal grafikte derecelendirmeleri
  nasıl etkinleştireceğinizi gösteren Aspose.Words radyal grafik örneği.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: tr
lastmod: 2026-10-13
og_description: C# ve en yeni 24.9+ kütüphanesi ile bir radyal grafikte derecelendirmeleri
  etkinleştirmeyi gösteren Aspose.Words radyal grafik örneği.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Aspose.Words radyal grafik örneği – C#'ta ölçek işaretlerini etkinleştirme
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Aspose.Words radyal grafik örneği: C#''ta ölçek işaretlerini etkinleştir'
url: /tr/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words radial chart örneği: C#'ta graduasyonları etkinleştirme

Eğer bir **aspose.words radial chart örneği** arıyorsanız, doğru yere geldiniz. Bu öğretici, Aspose.Words for .NET API'sını kullanarak bir radial chart için graduasyonları açmanın tam adımlarını size gösterir.

Radial chart'lar, günün saatine göre ölçümler veya mevsimsel trendler gibi döngüsel verileri görselleştirmek için faydalıdır. Varsayılan olarak graduasyonlar (dairesel eksen etrafındaki işaretler) gizlidir, bu da chart'ı okumayı zorlaştırabilir. Bunları etkinleştirmek tek satırlık bir değişikliktir, ancak doğru nesne modelini ve özelliği destekleyen sürümü bilmeniz gerekir.

Bu rehberde şunları öğreneceksiniz:

* Radial chart içeren bir Word belgesini yükleyin.  
* Aspose.Words chart API'sı aracılığıyla chart şekline erişin.  
* **Graduations visibility** özelliğini açın (**Aspose.Words version 24.9**'dan itibaren kullanılabilir).  
* Değiştirilen belgeyi kaydedin ve sonucu doğrulayın.

Tam, çalıştırılabilir kod dahil edilmiştir, böylece yeni bir konsol projesine kopyalayıp yapıştırarak etkisini hemen görebilirsiniz.

![Aspose.Words radial chart örneği graduasyonlarla](https://example.com/images/radial-chart-graduations.png "Aspose.Words radial chart örneği graduasyonların etkinleştirildiğini gösteriyor")

## Önkoşullar

| Gereksinim | Neden önemlidir |
|-------------|----------------|
| .NET 6.0 or later | Aspose.Words for .NET 24.9+, .NET Standard 2.0 hedefler ve .NET 6+ üzerinde çalışır. |
| Aspose.Words for .NET **24.9** or newer | `IsGraduationsVisible` özelliği sürüm 24.9'da tanıtıldı. Daha eski sürümler `MissingMemberException` hatası verir. |
| A Word document (`RadialChart.docx`) that contains a radial chart | Örnek mevcut bir chart'ı değiştirir; sıfırdan bir chart oluşturmak ayrı bir konudur. |
| A C# IDE (Visual Studio, Rider, VS Code) | .NET projelerini derleyebilen herhangi bir IDE çalışır. |
| NuGet package `Aspose.Words` | `dotnet add package Aspose.Words --version 24.9.0` (veya daha yeni) komutuyla yükleyin. |

> **Pro tip:** 24.9'a yükseltemiyorsanız, diğer chart özelliklerini hâlâ değiştirebilirsiniz, ancak graduasyonlar gizli kalır çünkü API bu bayrağı sunmaz.

## Aspose.Words radial chart örneği – adım adım kılavuz

Aşağıdaki bölümler süreci ayrı, takip etmesi kolay adımlara ayırır. Her adım, ihtiyacınız olan tam kodu ve adımın *neden* var olduğuna dair kısa bir açıklama içerir.

### Adım 1: Radial chart içeren belgeyi yükleyin

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Neden önemli:**  
`Document` **Aspose.Words chart API**'nin giriş noktasıdır. DOCX dosyasını belleğe yükler ve her düğüme—paragraflar, tablolar ve chart şekilleri—erişmenizi sağlar. Dosya bulunamazsa, `Document` bir `FileNotFoundException` fırlatır; bu, üretim kodunda ele alınmalıdır.

### Adım 2: Belgedeki ilk chart şekli alın

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Neden önemli:**  
Chart'lar `Shape` düğümleri olarak depolanır. `NodeType.Shape` ile `GetChild` yöntemi DOM'u dolaşır ve ilk eşleşen şekli döndürür. `Chart` tipine dönüştürmek, `RadialChart` gibi chart‑özel özelliklere erişmenizi sağlar. Null kontrolü, belge bir chart içermediğinde net bir hata almanızı sağlar; bu, şablonları yeniden kullanırken sık karşılaşılan bir kenar durumudur.

### Adım 3: Radial chart'ta graduasyonları etkinleştirin

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Neden önemli:**  
`IsGraduationsVisible` dairesel eksen etrafındaki işaretleri kontrol eder. `true` olarak ayarlandığında chart graduasyonları çizer, değerleri hassas bir şekilde ölçmek isteyen izleyiciler için okunabilirliği artırır. Bu özellik `RadialChart` altında bulunur; `RadialChart`, `Chart`'ın bir alt tipidir. Bunu radial olmayan bir chart'ta (ör. bar chart) denerseniz, `RadialChart` özelliği `null` olur, bu yüzden daha karmaşık senaryolarda önce chart tipini doğrulamalısınız.

#### Radial olmayan chart'ların işlenmesi (isteğe bağlı)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Bu koruma, kaynak belgenin farklı chart tipleri içerebileceği durumlarda kodu daha dayanıklı hâle getirir.

### Adım 4: Değiştirilen belgeyi kaydedin

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Neden önemli:**  
`Save` çağrısı, bellek içindeki DOM'u bir .docx dosyasına yazar ve chart üzerindeki değişikliği kalıcı hâle getirir. Çıktı dosyası Microsoft Word, LibreOffice veya DOCX destekleyen herhangi bir görüntüleyicide açılabilir. Görüntülenen radial chart, graduasyonların görünür olduğu şekilde olacaktır.

## Tam, çalıştırılabilir örnek

Aşağıda, bir .NET konsol projesinin `Program.cs` dosyasına yapıştırabileceğiniz tam program yer almaktadır.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Beklenen çıktı

`RadialChart_Graduations.docx` dosyasını Word'de açtığınızda, radial chart dairesel eksen etrafında işaretler (graduations) gösterir; bu, önceki ekranda gösterilen ekran görüntüsüne benzer. Chart'ın geri kalan kısmı (veri serileri, lejand, başlık) değişmeden kalır.

## Yaygın varyasyonlar ve kenar durumları

| Durum | Çözüm |
|-----------|----------|
| **Older Aspose.Words version (< 24.9)** | En son NuGet paketine yükseltin. `IsGraduationsVisible` özelliği daha eski sürümlerde yoktur. |
| **Multiple charts in the same document** | Uygun `index` ile `doc.GetChild(NodeType.Shape, index, true)` kullanın veya `doc.GetChildNodes(NodeType.Shape, true)` üzerinde döngü yaparak `ChartType.Radial` ile filtreleyin. |
| **Chart created programmatically** | `DocumentBuilder` kullanarak bir chart ekleyin, ardından `RadialChart.IsGraduationsVisible` özelliğini ayarlayın. |

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanıza ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Word Belgesinde Chart Serisi Verilerini Güncelleme Aspose.Words for .NET ile](/words/english/net/programming-with-charts/modify-chart-series/)
- [Word Belgesinden Chart Serisini Kaldırma Aspose.Words for .NET ile](/words/english/net/programming-with-charts/remove-chart-series/)
- [Sütun Chart'ta Plot Alanı Kenarlığını Gizleme Aspose.Words for .NET ile](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}