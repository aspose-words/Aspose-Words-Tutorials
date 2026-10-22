---
category: general
date: 2026-09-21
description: C# kullanarak bir Word çizgi grafiğinde serileri nasıl biçimlendireceğinizi
  öğrenin. Bir Word belgesi oluşturmayı, bir çizgi grafiği eklemeyi ve özel bir sayı
  formatı uygulamayı keşfedin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: tr
lastmod: 2026-09-21
og_description: C# kullanarak Word çizgi grafiğinde serileri nasıl biçimlendireceğinizi
  öğrenin. Bu öğreticide, bir Word belgesi oluşturmayı, bir çizgi grafiği eklemeyi
  ve özel bir sayı biçimi uygulamayı gösteriyoruz.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: C# ile Word çizgi grafiğinde serileri nasıl biçimlendirilir – adım adım
  kılavuz
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: C# ile Word çizgi grafiğinde serileri nasıl biçimlendiririz?
url: /tr/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Word satır grafiğinde serileri biçimlendirme

Word satır grafiğinde **serileri nasıl biçimlendireceğinizi** öğrenmek istiyorsanız, bu kılavuz size eksiksiz, çalıştırmaya hazır bir çözüm sunar. **Word belgesi oluşturmayı**, **satır grafiği eklemeyi** ve Y‑değerlerine **özel sayı biçimi uygulamayı** Aspose.Words for .NET ile göreceksiniz.  

Grafik nesne modelini anladıktan sonra Word otomasyonu oldukça basit hale gelir. Bu öğreticinin sonunda, veri serileri yüzde olarak iki ondalık basamakla gösterilen bir satır grafiği içeren bir Word dosyanız olacak.

## Başaracaklarınız

* Programatik olarak boş bir `.docx` dosyası oluşturun.  
* 400 × 300 point boyutunda bir satır grafiği ekleyin.  
* Grafiğin ilk veri serisine erişin.  
* `#,##0.00%` biçim kodunu uygulayarak Y‑değerlerinin yüzde olarak gösterilmesini sağlayın.  

Aspose.Words NuGet paketinin dışındaki hiçbir dış araç gerekmemektedir.

## Önkoşullar

* .NET 6.0 SDK veya daha yenisi.  
* Visual Studio 2022 (veya herhangi bir C# IDE).  
* Aspose.Words for .NET 23.10 veya daha yenisi – `dotnet add package Aspose.Words` komutuyla kurun.  

Kod, Aspose.Words'un platform bağımsız olması nedeniyle Windows, Linux ve macOS'ta çalışır.

## Aspose.Words ile Word belgesi oluşturma

İlk adım bir `Document` nesnesi örneklemektir. Bu nesne, bellek içinde tüm Word dosyasını temsil eder.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

* **Neden önemli**: `Document`, tüm Word‑işleme işlemlerinin giriş noktasıdır. Onsuz paragraf, tablo veya grafik ekleyemezsiniz.

## Belgeye satır grafiği ekleme

`DocumentBuilder`, `Document` içine içerik yazar. `InsertChart` çağrısı, mevcut sayfada bir grafik şekli oluşturur.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

* **Neden önemli**: `InsertChart`, seriler, eksenler ve biçimlendirme üzerinde tam kontrol sağlayan bir `Chart` nesnesi döndürür. Boyut parametreleri point cinsindendir (1 point = 1/72 inç).

## İlk veri serisine erişme

Her grafik bir veya daha fazla `ChartSeries` içerir. İlk seri indeks 0'da bulunur.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

* **Neden önemli**: `ChartSeries` nesnesi, satır grafiğindeki tek bir çizgi için Y‑değerlerini, X‑değerlerini ve biçimlendirme seçeneklerini tutar. Bu nesnenin değiştirilmesi, verinin görsel temsilini değiştirir.

## Seriye özel sayı biçimi uygulama

`FormatCode` özelliği, sayısal değerlerin nasıl gösterileceğini kontrol eder. `#,##0.00%` olarak ayarlandığında Word, değerleri iki ondalık basamaklı yüzde olarak işler.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

* **Neden önemli**: Özel bir format olmadan Word, ham ondalık sayıları gösterir (ör. `0.15`). Biçim kodu bunları `15.00%`'e dönüştürür; bu, iş raporlarının sıkça talep ettiği bir biçimdir.

## Belgeyi kaydetme ve sonucu doğrulama

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

`FormattedSeriesLineChart.docx` dosyasını Microsoft Word'de açtığınızda, Y‑ekseni etiketlerinin `15.00%`, `30.00%`, `45.00%` ve `60.00%` olarak göründüğü bir satır grafiği göreceksiniz. Grafik boyutu, `InsertChart` içinde verilen boyutlarla eşleşir.

### Beklenen çıktı ekran görüntüsü

> *Görsel: Yüzde‑biçimli Y‑ekseni değerlerine sahip bir satır grafiği gösteren bir Word belge sayfası.*  
> *(Alt metin: Yüzde‑biçimli Y‑ekseni değerlerine sahip bir satır grafiği gösteren bir Word belgesinin ekran görüntüsü)*

## Yaygın varyasyonlar ve uç durumlar

| Durum | Ayar |
|-----------|------------|
| **Birden fazla seri** | `chart.Series` içinde döngü yaparak her seri için `FormatCode` ayarlayın. |
| **Farklı grafik türü** | `ChartType.Line` yerine `ChartType.Column`, `ChartType.Pie` vb. kullanın. |
| **Bölge‑spesifik ayırıcılar** | `CultureInfo`‑bilinçli biçim dizgileri kullanın, ör. Fransız yerel ayarları için `"# ##0,00 %"`. |
| **Dinamik veri kaynağı** | Biçimi uygulamadan önce `series.YValues` değerlerini bir veritabanı veya CSV dosyasından doldurun. |

**Pro ipucu:** Biçimi **Y‑değerlerini ekledikten sonra** uygulayın. Önce biçimi değiştirip ardından değer eklemek de çalışır, ancak daha sonra uygulamak, biçimin son veri kümesine uygulanmasını garanti eder.

## Özet

Artık C# kullanarak bir Word satır grafiğinde **serileri nasıl biçimlendireceğinizi** biliyorsunuz. Öğreticide şunlar ele alındı:

* Word belgesi oluşturma (`create word document`).  
* Satır grafiği ekleme (`insert line chart`, `add chart to word`).  
* Grafiğin ilk serisine erişme.  
* Yüzdeleri göstermek için özel bir sayı biçimi uygulama (`apply custom number format`).

## Sonraki adımlar

* Farklı `ChartType` değerleriyle deney yaparak diğer görselleştirmelerin nasıl davrandığını görün.  
* `chart.Title`, `chart.AxisX.Title` ve `chart.AxisY.Title` kullanarak başlıklar, eksen etiketleri ve lejand ekleyin.  
* Grafiği bir görüntü olarak dışa aktar (`chart.Save` ile `SaveFormat.Png`) ve web raporlarında kullanın.  

Bu deseni, gösterge panoları, finansal raporlar veya programatik grafik gerektiren herhangi bir belge oluşturmak için özgürce uyarlayabilirsiniz. İyi kodlamalar!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Word'de Aspose.Words for .NET kullanarak Satır Grafiği Oluşturma](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Word Belgesine Sütun Grafiği Ekleme](/words/english/net/programming-with-charts/insert-column-chart/)
- [Word Belgesine Alan Grafiği Ekleme | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}