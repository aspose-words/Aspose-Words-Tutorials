---
category: general
date: 2026-09-08
description: Boş bir Word belgesi oluşturun ve Aspose.Words ile Word’e grafik ekleyin.
  Radar grafiği nasıl ekleyeceğinizi, derecelendirmeleri nasıl etkinleştireceğinizi
  öğrenin ve dosyayı kaydedin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: tr
lastmod: 2026-09-08
og_description: Boş bir Word belgesi oluşturun ve Aspose.Words kullanarak Word'e grafik
  ekleyin. Bu öğreticide radar grafiği nasıl ekleyeceğiniz, eksenleri nasıl yapılandıracağınız
  ve belgeyi nasıl kaydedeceğiniz gösterilmektedir.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Boş bir Word belgesi oluşturun ve bir radar grafiği ekleyin – adım adım
  rehber
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Boş Word belgesi oluşturma ve Word'e grafik ekleme
url: /tr/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş Word belgesi oluşturma ve Word'e grafik ekleme

Bir rapor, şablon veya otomatik posta birleştirme için **boş Word belgesi oluşturmanız** gerekiyorsa, bu kılavuz C# ve Aspose.Words ile tüm süreci adım adım anlatır. Ayrıca **Word'e grafik eklemeyi**, özellikle **radar grafiği eklemeyi**, graduasyonları açmayı ve sonucu .docx dosyası olarak kaydetmeyi öğreneceksiniz.

Bu öğretici, proje kurulumundan son doğrulama adımına kadar her şeyi kapsar. Sonunda, herhangi bir .NET uygulamasına eklenebilecek yeniden kullanılabilir bir kod snippet'ine sahip olacaksınız. Aspose.Words ile ilgili önceden deneyim gerekmez, ancak temel C# bilgisine ve güncel bir .NET SDK'sına sahip olmalısınız.

## Önkoşullar

- .NET 6.0 SDK veya daha yeni bir sürüm  
- Aspose.Words for .NET (NuGet paketi `Aspose.Words`)  
- Visual Studio 2022 veya VS Code gibi bir IDE  
- Belgenin kaydedileceği klasöre yazma izni  

Kütüphaneyi aşağıdaki komutla kurabilirsiniz:

```bash
dotnet add package Aspose.Words
```

## Adım 1: Boş Word belgesi oluşturma

İlk adım, bellekte **boş Word belgesi oluşturmak**tır. `Document` sınıfı tüm dosyayı temsil ederken, `DocumentBuilder` içerik eklemek için akıcı bir API sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` boş başlar, böylece grafiği yerleştirebileceğiniz temiz bir tuvaliniz olur. Bu aşamada belgeyi boş tutmak, aynı kodu farklı şablonlar için yeniden kullanmayı kolaylaştırır.

## Adım 2: Word'e grafik ekleme

Sonra, `InsertChart` metodunu çağırarak **Word'e grafik ekliyoruz**. Metod, grafik tipini ve istenen boyutları point cinsinden (1 point = 1/72 inç) gerektirir.

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar`, Aspose.Words'e radyal bir grafik oluşturmasını söyler; bu, çok değişkenli verileri dairesel bir düzenlemede göstermek için idealdir. Boyut değerleri (400 × 300) çoğu dikey sayfa için uygundur, ancak düzeninize göre ayarlayabilirsiniz.

## Adım 3: Radar grafiği ekleme ve graduasyonları yapılandırma

Şimdi **radar grafiği ekliyoruz** ve kategori (X) ile değer (Y) eksenlerinde graduasyonları (işaretçileri) etkinleştiriyoruz. Graduasyonlar, her veri noktasının tam konumunu göstererek okunabilirliği artırır.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

`HasGraduations` özelliğini `true` olarak ayarlamak eksenlerde işaretçileri çizer. İsteğe bağlı `GraduationStep` radyal eksendeki işaretçiler arasındaki boşluğu kontrol eder; 10 adım, her 10 derecede bir işaretçi anlamına gelir.

### Pro ipucu
Veri etiketlerini göstermeniz gerekiyorsa, `radarChart.Series[0].HasDataLabel = true;` kodunu çağırın. Bu, her noktanın yanına sayısal değeri ekler ve sunumlar için faydalıdır.

## Adım 4: Grafiği örnek veri ile doldurma (isteğe bağlı)

Veri olmadan bir radar grafiği görünmez. Aşağıda örnek değerler serisi eklemenin hızlı bir yolu verilmiştir. Bu bloğu kendi veri kaynağınızla değiştirebilirsiniz.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

`Add` metodunun her çağrısı seriye bir nokta ekler. Noktaların sırası, daire etrafındaki açısal konumlara karşılık gelir.

## Adım 5: Grafiği içeren belgeyi kaydetme

Son olarak, belgeyi diske kaydedin. `Save` metodu .docx dosyasını otomatik olarak yazar, grafiği ve tüm biçimlendirmeyi korur.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Programı çalıştırmak, içinde tam işlevsel bir radar grafiği bulunan **boş Word belgesi** oluşturur. Sonucu görmek için dosyayı Microsoft Word'de açın.

![Radar chart in Word document](radar_chart.png){alt="Boş Word belgesine eklenmiş radar grafiği"}

## Yaygın varyasyonlar ve uç durumlar

| Durum | Ne değiştirilmeli |
|-----------|----------------|
| **Farklı grafik boyutu** | `InsertChart`'in genişlik/yükseklik parametrelerini ayarlayın. |
| **Diğer grafik türleri** | `ChartType.Radar`'ı `ChartType.Column`, `ChartType.Pie` vb. ile değiştirin ve aynı graduation mantığını koruyun. |
| **Akışa kaydetme** | `document.Save(Stream, SaveFormat.Docx)` kullanın. |

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Word Belgesine Alan Grafiği Ekle | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Aspose.Words for .NET Kullanarak Word Dağılım Grafiği Oluştur](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Aspose.Words for .NET Kullanarak Word'e Sütun Grafiği Ekle](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}