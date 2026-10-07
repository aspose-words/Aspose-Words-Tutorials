---
category: general
date: 2026-10-07
description: Aspose.Words kullanarak C#'ta Word belgesi oluşturmayı ve pasta grafiği
  eklemeyi öğrenin. Kılavuz ayrıca özel grafik etiketleriyle Word dosyası oluşturmayı
  da gösterir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: tr
lastmod: 2026-10-07
og_description: C#'te Word belgesi oluşturun ve pasta grafiği ekleyin. Tamamen özelleştirilmiş
  grafik etiketleriyle Word dosyası oluşturmak için bu adım adım kılavuzu izleyin.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: C#'ta özelleştirilmiş bir pasta grafiğiyle Word belgesi oluşturun
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: C#'ta özelleştirilmiş bir pasta grafiği ile Word belgesi nasıl oluşturulur
url: /tr/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta özelleştirilmiş bir pasta grafiği ile Word belgesi oluşturma

Programlı olarak **create word document** oluşturmanız gerekiyorsa, bu öğreticide Aspose.Words for .NET kullanarak **insert pie chart** eklemeyi ve veri etiketlerini özelleştirmeyi öğreneceksiniz. Ayrıca tamamen biçimlendirilmiş bir grafik içeren **generate word file** nasıl oluşturulacağını, proje kurulumundan son belgeyi kaydetmeye kadar her şeyi kapsayan bir şekilde öğreneceksiniz.

Kılavuz, bir grafik eklemek, etiket konumlarını ayarlamak, lider çizgilerini etkinleştirmek ve sonunda sonucu bir `.docx` dosyası olarak kaydetmek için gereken her adımı anlatır. Aspose.Words kütüphanesinin ötesinde harici bir araç gerekmez ve tam kaynak kodu sağlanmıştır, böylece kopyalayıp yapıştırarak anında çalıştırabilirsiniz.

## Önkoşullar

* .NET 6.0 SDK veya daha yeni bir sürüm yüklü  
* Geçerli bir Aspose.Words for .NET lisansı (veya ücretsiz deneme anahtarı)  
* Visual Studio 2022 veya Visual Studio Code gibi bir IDE  

Ayrıca projenize aşağıdaki NuGet paketlerini eklemeniz gerekir:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Bu paketler, aşağıdaki örneklerde kullanılan `Document`, `DocumentBuilder` ve grafik‑ile ilgili sınıfları ortaya çıkarır.

## Word belgesi oluşturma ve bir grafik ekleme

İlk adım, **create word document** ve içerik eklemenizi sağlayan bir `DocumentBuilder` elde etmektir. Builder, belge içinde konumlandırılmış bir imleç gibi çalışır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` nesnesi tüm Word dosyasını temsil ederken, `DocumentBuilder` `InsertChart` gibi nesneleri doğrudan belge akışına yerleştiren yöntemler sunar.

## Belgeye pasta grafiği ekleme

Builder hazır olduğuna göre, belirli bir boyutta **insert pie chart** yapabilirsiniz. Grafik, builder'ın mevcut konumuna eklenir.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` bir `Chart` nesnesi döndürür; bu nesneyi daha fazla manipüle edebilirsiniz. Örnek veri, çeyrek satışları temsil eden dört dilim oluşturur.

## Pasta grafiği veri etiketlerini özelleştirme

Grafiği daha okunabilir kılmak için, genellikle **customize pie chart** etiketlerini dışa konumlandırıp lider çizgileri göstermeniz gerekir. İşte `ChartDataLabelCollection` devreye girer.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

`Position` değerini `OutsideEnd` olarak ayarlamak, her etiketi dilimin kenarının ötesine taşır; `ShowLeaderLines` ise etiketi dilime bağlayan bir çizgi çizer. İsteğe bağlı `ShowValue` ve `ShowPercentage` bayrakları, okuyuculara hem ham sayıları hem de yüzde değerlerini sunar.

**Pro tip:** Etiket yazı tipini biçimlendirmeniz gerekiyorsa, `dataLabels.Font` kullanarak boyut, renk ve stil ayarlayın. Bu, grafiğin kurumsal markanızla eşleşmesini sağlar.

## Word dosyasını kaydetme ve oluşturma

Grafik tamamen yapılandırıldıktan sonra, `Document` örneğini diske kaydederek **generate word file** yapabilirsiniz. Modern Word sürümleriyle en yüksek uyumluluk için `.docx` formatını seçin.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

`CustomPieChart.docx` dosyasını açtığınızda, dört dilimli bir pasta grafiği göreceksiniz; her dilim dışarıda etiketlenmiş, lider çizgileriyle bağlanmış ve hem değer hem de yüzde gösteriyor.

![C# ile oluşturulmuş özelleştirilmiş bir pasta grafiği içeren Word belgesinin ekran görüntüsü](image-placeholder.png)

*Görsel, **create word document** öğreticisinin son sonucunu göstermektedir.*

## Yaygın varyasyonlar ve uç durumlar

| Senaryo | Kodu nasıl uyarlamalısınız |
|----------|----------------------|
| **Çoklu seri** | `pieChart.Series`'e ek `ChartSeries` nesneleri ekleyin. Her seri, bağımsız biçimlendirme için kendi `DataLabels` koleksiyonuna sahip olabilir. |
| **Farklı grafik boyutu** | `InsertChart(width, height)` içindeki genişlik ve yükseklik parametrelerini değiştirin. Değerler puan cinsindendir (1 pt ≈ 1/72 in). |
| **Grafik başlığı** | Açıklayıcı bir başlık eklemek için `pieChart.Title.Text = "Quarterly Sales"` kullanın. |
| **PDF olarak dışa aktar** | Grafik oluşturulduktan sonra `document.Save("Report.pdf", SaveFormat.Pdf);` çağırın. |
| **Lisans yönetimi** | Lisans dosyanızı (`Aspose.Words.lic`) uygulama klasörüne koyun ve belgeyi oluşturmadan önce `new License().SetLicense("Aspose.Words.lic");` ile yükleyin. |

Bu varyasyonlar, basit raporlardan karmaşık panolara kadar birçok gerçek dünya senaryosunda **how to add pie chart** sorusuna yanıt vermenizi sağlar.

## Sonuç

Artık Aspose.Words for .NET kullanarak **create word document**, **insert pie chart** ve **customize pie chart** etiketlerini nasıl yapacağınızı biliyorsunuz. Tam örnek, temiz bir iş akışını gösterir: belgeyi başlatma, bir grafik ekleme, veri‑etiket konumlandırmasını ayarlama, lider çizgilerini etkinleştirme ve sonunda **generate word file** yaparak herkesle paylaşılabilir bir dosya oluşturma.

Farklı grafik tipleri (`ChartType.Column`, `ChartType.Line`) ile deney yaparak veya markanıza uygun özel renk paletleri uygulayarak bu öğreticiyi genişletmeyi deneyin. Sorunlarla karşılaşırsanız, Aspose.Words belgelerine başvurun veya “how to add pie chart” gibi çoklu seri ve dinamik veri kaynaklarıyla ilgili konuları keşfedin.

Kodlamaktan keyif alın, sonuçlarınızı paylaşmaktan veya yorumlarda takip soruları sormaktan çekinmeyin!

## Sonra Ne Öğrenmelisin?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Word Belgesine Sütun Grafiği Ekleme](/words/english/net/programming-with-charts/insert-column-chart/)
- [Word Belgesine Alan Grafiği Ekleme](/words/english/net/programming-with-charts/insert-area-chart/)
- [Word Belgesine Dağılım Grafiği Ekleme](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}