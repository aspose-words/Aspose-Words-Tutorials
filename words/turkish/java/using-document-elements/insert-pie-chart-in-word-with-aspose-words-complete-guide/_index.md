---
category: general
date: 2026-07-26
description: Aspose.Words kullanarak bir Word belgesine pasta grafiği ekleyin. Sadece
  birkaç adımda grafiği nasıl ekleyeceğinizi, dilimi nasıl patlatacağınızı ve yüzde
  değerlerini nasıl göstereceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: tr
lastmod: 2026-07-26
og_description: Aspose.Words ile bir Word dosyasına pasta grafiği ekleyin. Bu kılavuzu
  izleyerek grafiği nasıl ekleyeceğinizi, dilimi nasıl patlatacağınızı ve yüzde değerlerini
  nasıl hızlıca göstereceğinizi öğrenin.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Word'e Pasta Grafiği Ekle – Adım Adım Aspose.Words Eğitimi
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Aspose.Words ile Word'e Pasta Grafiği Ekleme – Tam Rehber
url: /tr/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile Word'e Pasta Grafiği Ekleme – Tam Kılavuz

Bir Word raporuna **pasta grafiği eklemeniz** gerektiğinde nereden başlayacağınızı bilemediniz mi? Tek başınıza değilsiniz. Birçok iş uygulamasında pasta grafiğinin görsel etkisi, verileri anında sindirilebilir hâle getirir ve Aspose.Words bunu sadece birkaç satır kodla mümkün kılar.

Bu öğreticide **grafiği Word’e ekleme**, vurgulamak için bir dilimi “patlatma” ve veri etiketlerinde yüzde göstermek adımlarını adım adım inceleyeceğiz. Sonunda, herhangi bir .NET projesine ekleyebileceğiniz çalıştırmaya hazır bir örnek elde edeceksiniz.

---

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

- .NET 6.0 veya üzeri (kod .NET Core ve .NET Framework’te de çalışır)
- Aspose.Words for .NET NuGet paketi yüklü  
  ```bash
  dotnet add package Aspose.Words
  ```
- C# sözdizimi hakkında temel bilgi — karmaşık bir şey gerekmez
- Tercih ettiğiniz bir IDE (Visual Studio, Rider veya VS Code)

Hepsi bu kadar. Hadi işe koyulalım.

---

## Word Belgesine Pasta Grafiği Ekleme

İlk olarak yeni bir `Document` nesnesi ve bir `DocumentBuilder` oluşturmamız gerekiyor. Builder, Word tuvaline doğrudan yazan bir kalem gibi düşünülebilir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Neden önemli:** `Document`, .docx dosyasının tamamını temsil ederken `DocumentBuilder`, grafik, tablo ve metin gibi öğeleri eklemek için kullanışlı bir API sağlar. Bu, her **grafik ekleme** işleminin temelini oluşturur.

---

## Word’e Grafik Nasıl Eklenir

Artık bir builder’ımız olduğuna göre **pasta grafiği ekleyebilir**iz. `insertChart` metodu, grafik tipini ve istenen boyutları puan cinsinden alır (1 puan = 1/72 inç).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **İpucu:** Farklı bir boyuta ihtiyacınız varsa, sadece genişlik ve yükseklik değerlerini değiştirin. Grafik, sayfa kenar boşluklarına otomatik olarak uyum sağlayacaktır.

---

## Vurgulamak İçin Dilimi Patlatma

Sıkça yapılan bir görsel ayar, bir dilimi “patlatıp” dairenin dışına çıkarmaktır. Bu, okuyucunun gözünü en önemli bölüme çeker.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Neden dilim patlatılır?** Belirli bir kategoriyi—örneğin bir finansal raporda “Q1 geliri”—vurgulamak istediğinizde, dilimi patlatmak ekstra metin eklemeden hemen fark edilmesini sağlar.

---

## Veri Etiketlerinde Yüzde Gösterme

Çoğu pasta grafiği, her dilimin yüzde değerini gösterdiğinde daha anlaşılır olur. Aspose.Words bu özelliği tek bir özellik ile açmamıza izin verir.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Kısa not:** `ShowPercentage` bayrağı serideki tüm noktalar için geçerlidir, bu yüzden dilim başına ayrı ayrı ayarlama yapmanıza gerek yoktur.

---

## Grafiği İçeren Belgeyi Kaydetme

Son olarak belgeyi diske yazıyoruz. İstediğiniz bir klasörü seçin; sadece yolun var olduğundan emin olun.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

`PieChart.docx` dosyasını Microsoft Word’de açtığınızda, ilk dilimi patlatılmış ve yüzde değerleri gösterilmiş mükemmel bir pasta grafiği göreceksiniz—tam bir iş raporunda beklenen kalite.

---

## Tam Çalışan Örnek

Aşağıda kopyala‑yapıştır yapmaya hazır tam program yer alıyor. Konsol uygulaması olarak çalıştırın ve çıktı dosyasını kontrol edin.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Beklenen sonuç:** Oluşturulan `PieChart.docx` dosyasını açın. “Sales Q1” başlıklı üç dilimli bir pasta grafiği göreceksiniz; ilk dilim dışarıda ve dilimler “%30”, “%45” ve “%25” olarak etiketlenmiş. Görsel, sağladığımız verilerle tam uyumlu.

---

## Yaygın Sorular & Kenar Durumları

- **Birden fazla seri eklemem gerekirse?**  
  `chart.Series` koleksiyonuna ek `ChartSeries` nesneleri ekleyin. Her seri kendi veri kümesine, renklerine ve patlatma ayarlarına sahip olabilir.

- **Grafiğin renklerini değiştirebilir miyim?**  
  Evet. Her `ChartPoint` nesnesinin `Format.Fill.ForeColor` özelliğini istediğiniz `System.Drawing.Color` değerine ayarlayabilirsiniz.

- **Farklı grafik tipleri mümkün mü?**  
  `ChartType` enum’u bar, line, doughnut ve daha birçok tip içerir. İhtiyacınız olan görselle eşleşecek şekilde `ChartType.Pie` yerine başka bir tip kullanın.

- **Grafik, ekleme sonrası Word içinde düzenlenebilir mi?**  
  Kesinlikle. Word, grafiği yerel bir Office grafiği olarak kabul eder; kullanıcılar çift tıklayarak yerleşik grafik düzenleyicisini açabilir.

---

## Sonuç

Artık Aspose.Words kullanarak bir Word belgesine **pasta grafiği ekleme**, **grafiği Word’e ekleme**, **dilimi patlatma** ve **veri etiketlerinde yüzde gösterme** konularını adım adım biliyorsunuz. Yukarıdaki tam örnek çalıştırılmaya hazır ve özel veri, stil ya da ek serilerle genişletilebilir.

Bir sonraki adım için hazır mısınız? Pasta grafiğini bir doughnut grafiğiyle değiştirin ya da farklı veri setleriyle toplu raporlar üretin. Diğer görselleştirmelerle ilgileniyorsanız, **grafik ekleme** konusundaki bar ve line grafik rehberlerimize göz atın ya da daha derin özelleştirmeler için **add chart to word** API referansını inceleyin.

Kodlamanın tadını çıkarın, belgeleriniz her zaman mükemmel dilimlenmiş bir pasta gibi net olsun!

## Bir Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ilgili konuları kapsamaktadır. Her kaynak, adım adım açıklamalar ve tam çalışan kod örnekleri içerir; böylece ek API özelliklerini öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}