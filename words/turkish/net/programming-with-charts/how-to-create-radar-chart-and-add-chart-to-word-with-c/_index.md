---
category: general
date: 2026-09-05
description: C# kullanarak Word'de radar grafiği oluşturun. Boş bir Word belgesi oluşturmayı,
  radar grafiği eklemeyi, grafik boyutunu ayarlamayı ve tik işaretlerini hızlıca etkinleştirmeyi
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: tr
lastmod: 2026-09-05
og_description: C# kullanarak Word’de radar grafiği oluşturun. Bu kılavuz, boş bir
  Word belgesi oluşturmayı, radar grafiği eklemeyi, grafik boyutunu ayarlamayı ve
  işaretçileri etkinleştirmeyi dakikalar içinde gösterir.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Word'de radar grafiği oluşturma – adım adım C# rehberi
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: C# ile radar grafiği oluşturma ve grafiği Word’e ekleme
url: /tr/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Radar Grafiği Oluşturma ve Word'e Grafik Ekleme

Eğer bir Word dosyası içinde **radar grafiği oluşturmanız** gerekiyorsa, bu rehber tüm süreci adım adım anlatır. **Boş bir Word belgesi oluşturma**, radar grafiği ekleme, **grafik boyutunu Word içinde ayarlama** ve eksen işaretlerini etkinleştirme işlemlerini sadece birkaç C# satırıyla öğrenebileceksiniz.

Raporlara görsel veri eklemek yaygın bir gereksinimdir ve Aspose.Words kullanmak bunu oldukça basitleştirir. Aşağıdaki adımlarda ayrıca **grafiği Word belgesine programlı olarak ekleme** konusunu da ele alıyoruz; böylece panoları, finansal özetleri veya veri odaklı herhangi bir içeriği otomatikleştirebilirsiniz.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 veya daha yeni bir sürüm  
* Aspose.Words for .NET lisansı (veya ücretsiz deneme) – bu kütüphane öğreticide kullanılan `Document`, `DocumentBuilder` ve grafik API'lerini sağlar  
* Visual Studio 2022 (veya herhangi bir C# IDE)  

> **İpucu:** Test yapıyorsanız, Aspose.Words DLL dosyasını projenizin `bin` klasörüne koyun ve NuGet üzerinden referans verin (`Install-Package Aspose.Words`).

## Word belgesinde radar grafiği nasıl oluşturulur

İlk adım, grafiği barındıracak **boş bir Word belgesi oluşturmak**tır. Bu, temiz bir tuval sağlar ve içerik eklenmeden önce belgenin meta verilerini kontrol etmenize imkan tanır.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Neden önemli:* Boş bir `Document` nesnesi, gizli stillerin veya bölümlerin grafik düzeniyle çakışmasını engeller. Ayrıca gerektiğinde belge özelliklerini (yazar, başlık vb.) sonradan ayarlamanıza da olanak verir.

## Aspose.Words ile Word'e grafik nasıl eklenir

Sonra bir `DocumentBuilder` oluşturun. Builder, belgeye metin, resim ve grafik eklemenizi sağlayan temel araçtır.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

Şimdi **radar grafiği ekleyebilir** ve imlecin bulunduğu konuma yerleştirebilirsiniz. `InsertChart` metodu bir `ChartType` enum değeri, genişlik ve yükseklik (puan) parametrelerini kabul eder.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*Neden 400 × 300?* Bu boyutlar, standart A4 sayfasında net ve okunabilir bir grafik elde etmenizi sağlar. Düzeniniz farklı bir en‑boy oranı gerektiriyorsa, **grafik boyutunu Word içinde ayarlama** adımıyla boyutu daha sonra değiştirebilirsiniz.

## Word içinde grafik boyutunu ayarlama

Ekleme sonrası boyutu ince ayar yapmak isterseniz, grafiğin `Width` ve `Height` özelliklerini değiştirebilirsiniz. Bu, çevredeki metin veya sayfa kenar boşlukları farklı bir görsel denge talep ettiğinde faydalıdır.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Not:** `InsertChart` aşırı yüklemesi zaten boyutu ayarlar; bu nedenle yukarıdaki kod isteğe bağlıdır ve tamlık açısından gösterilmiştir.

## Radial eksende işaretçileri etkinleştirme

Radar grafiği, radial eksen açıkça işaretlenmiş olduğunda en faydalı olur. Aşağıdaki ayarlar işaretçileri açar ve aralığı 30 dereceye ayarlar; bu, tipik pusula‑stili radar ekranlarıyla uyumludur.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Neden önemli:* İşaretlemeler, okuyucuların her açıdaki değerleri kolayca tahmin etmesini sağlar ve veriye aşina olmayan paydaşların okunurluğunu artırır.

## Grafiği içeren belgeyi kaydetme

Son olarak belgeyi diske yazın. İstediğiniz herhangi bir klasörü seçebilirsiniz; sadece yolun mevcut olduğundan emin olun.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

`RadialChart.docx` dosyasını Microsoft Word’de açtığınızda, sayfanın ortasında belirtilen boyutta, her 30 derecede bir işaretçi bulunan tam olarak render edilmiş bir radar grafiği göreceksiniz.

### Beklenen çıktı

* **RadialChart.docx** adında bir `.docx` dosyası  
* İlk sayfada 400 × 300 puan boyutunda bir radar grafiği  
* X‑ekseni (radial eksen) 0°, 30°, 60°, …, 330° işaretçilerini gösterir  

Artık `radarChart.Series` üzerinden kendi veri serilerinizi ekleyerek yer tutucu verileri değiştirebilirsiniz – ancak bu, temel **radar grafiği ekleme** öğretisinin kapsamı dışındadır.

## Yaygın varyasyonlar ve kenar durumları

| Senaryo | Ayarlama |
|----------|------------|
| **Farklı grafik türü** | `ChartType.Radar` yerine `ChartType.Column`, `ChartType.Pie` vb. kullanın |
| **Birden fazla grafik** | `InsertChart` metodunu tekrarlı olarak çağırın; her çağrı yeni grafiği bir öncekinin sonrasına yerleştirir |
| **Büyük veri setleri** | `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` ile çok sayıda veri noktasını ekleyin |
| **PDF olarak kaydetme** | Grafik eklendikten sonra `document.Save("RadialChart.pdf", SaveFormat.Pdf);` kodunu çalıştırın |
| **.NET Core üzerinde çalıştırma** | `Aspose.Words.NETCore` paketine referans verdiğinizden emin olun; API kullanımı aynı kalır |

## Tam, çalıştırılabilir örnek

Aşağıda, bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz eksiksiz program yer almaktadır. Tüm adımları, isteğe bağlı boyut ayarlamalarını ve açıklamaları içerir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Programı çalıştırın, oluşan dosyayı açın ve radar grafiğinin tam olarak tarif edildiği gibi göründüğünü doğrulayın.

## Sonuç

Artık **radar grafiği oluşturma** ve **grafiği Word’e ekleme** işlemlerini C# kullanarak nasıl yapacağınızı biliyorsunuz. Eğitimde **boş bir Word belgesi oluşturma**, radar grafiği ekleme, **grafik boyutunu Word içinde ayarlama** ve eksen işaretlerini etkinleştirme konuları ele alındı. Bu temelle birden fazla grafik, özel veri serileri ekleme veya PDF’ye dışa aktarma gibi çözümler geliştirebilirsiniz.

### Sonraki adımlar

* `ChartType` ile diğer grafik türlerini keşfedin (ör. `Bar`, `Line`) – ilgili örnekler için **add radar chart** anahtar kelimesine bakın.

## Bir Sonraki Öğrenmeniz Gereken Konular

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve benzer konuları kapsayan kaynaklardır. Her biri, kendi projelerinizde ek API özelliklerini ustalaşmanız ve alternatif uygulama yaklaşımlarını keşfetmeniz için tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}