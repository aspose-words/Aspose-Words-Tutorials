---
category: general
date: 2026-08-04
description: C#'ta Grafikler için Özel Veri Etiketi Yerleşimi, etiketleri grafik dilimlerinin
  ortasına yerleştirmenizi sağlar. Aspose.Words grafik API'sını kullanarak bu adım
  adım kılavuzu izleyin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: tr
lastmod: 2026-08-04
og_description: C#'ta Grafikler için Özel Veri Etiketi Yerleşimi, bir Word grafiğinin
  her dilimindeki tüm veri etiketlerini nasıl ortalayacağınızı gösterir. Aspose.Words
  ile grafik veri etiketi konumlandırmasını ustalaşın.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: C#'ta Grafikler için Özel Veri Etiketi Yerleşimi – adım adım kılavuz
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: C#'ta Grafikler İçin Özel Veri Etiketi Yerleşimi
url: /tr/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta Grafikler için Özel Veri Etiketi Yerleşimi

**Custom Data‑Label Placement for Charts** size Word belgesi içindeki bir grafikte her etiketin tam olarak nerede görüneceğini kontrol etmenizi sağlar. Bu öğreticide C# ve Aspose.Words chart API'si kullanarak her dilimin veri etiketlerini ortalamayı öğreneceksiniz.

Tam bir, çalıştırılabilir örnek alacaksınız; bu örnek bir `.docx` dosyasını yükler, ilk grafik şekline erişir, her etiketin `Position` değerini `Center` olarak değiştirir ve güncellenmiş belgeyi kaydeder. Harici referanslara gerek yok—sadece Aspose.Words for .NET kütüphanesi ve temel bir C# geliştirme ortamı yeterlidir.

**Öğrenecekleriniz**

* Bir grafik içeren Word belgesinin nasıl yükleneceği.  
* Aspose.Words chart API'si ile grafik şeklinin nasıl bulunacağı.  
* Grafikteki her seriye **grafik veri etiketi konumlandırması** nasıl uygulanacağı.  
* Etiketlerin ortalanmış olarak Word'de görünmesi için belgenin nasıl kaydedileceği.  

**Önkoşullar**

* .NET 6.0 (veya daha yeni) yüklü.  
* Visual Studio 2022 (veya herhangi bir C# IDE).  
* `Aspose.Words` NuGet paketine referans.  
* En az bir grafik içeren bir Word dosyası (`Chart.docx`).

---

## Grafikler için Özel Veri Etiketi Yerleşimi – adım 1: belgeyi yükleme

İlk işlem, grafiği içeren Word dosyasını açmaktır. `Document` Aspose.Words ile yapılacak tüm manipülasyonların giriş noktasıdır.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Bu adımın önemi*: Belge yüklenmeden grafik nesnesine ulaşamazsınız. Doğrulama, dosyada grafik bulunmadığında net bir hata mesajı verir ve daha sonra oluşabilecek null‑referans hatasını önler.

---

## Aspose.Words chart API'si ile grafik şekillerine erişim

Aspose.Words bir grafiği, içinde `Chart` nesnesi barındıran bir `Shape` olarak ele alır. Uygun alt düğümü tip dönüşümü yaparak ona ulaşabilirsiniz.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Bu adımın önemi*: `Chart` nesnesine doğrudan erişim, seriler, veri noktaları ve etiket özellikleri üzerinde tam kontrol sağlar. Şekil bir grafik değilse, kod bilgilendirici bir mesajla erken sonlanır.

---

## C#'ta grafik veri etiketi konumlandırmasını ayarlama

Şimdi her seriyi ve her veri etiketini dolaşarak `Position` değerini `Center` olarak ayarlayın. Bu, **Custom Data‑Label Placement for Charts** işleminin çekirdeğidir.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**İpucu**: Farklı bir konumlama (ör. sütun grafiği için `InsideEnd`) istiyorsanız, enum değerini ona göre değiştirin. `ChartDataLabelPosition` enum’u, Word tarafından desteklenen tüm standart konumları kapsar.

*Bu adımın önemi*: `label.Position` değerinin değiştirilmesi, temel OOXML temsili günceller; böylece belge Microsoft Word'de açıldığında etiket ortalanmış olarak görünür.

---

## Güncellenmiş etiketlerle Word belgesini kaydetme

Grafiği değiştirdikten sonra değişiklikleri bir dosyaya geri yazın. Orijinali üzerine yazabilir ya da yeni bir kopya oluşturabilirsiniz.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Bu adımın önemi*: Kaydetme, güncellenmiş OOXML'i diske yazar. `ChartLabelsCentered.docx` dosyasını Word'de açtığınızda her dilim etiketinin ortalanmış olduğunu göreceksiniz; bu da **Custom Data‑Label Placement for Charts** işleminin başarılı olduğunu kanıtlar.

---

## Kenar durumları ve varyasyonlar

| Durum | Nasıl ele alınır |
|-----------|---------------|
| **Aynı belgede birden fazla grafik** | `doc.GetChildNodes(NodeType.Shape, true)` üzerinden döngü kurun ve her şekil için `shape.HasChart` kontrol edin. |
| **Farklı grafik tipleri** (pie, doughnut, bar) | `ChartDataLabelPosition.Center` pie‑tipi grafiklerde çalışır. Bar/sütun grafiklerde `InsideEnd` veya `OutsideEnd` tercih edilebilir. |
| **Etiket metninin biçimlendirilmesi gerekiyor** | `label.TextProperties` üzerinden yazı tipi boyutu, renk veya kalınlık gibi özellikleri ayarlayın. |
| **.NET Core üzerinde çalıştırma** | Aspose.Words .NET Standard sürümüne referans verdiğinizden emin olun; API aynı kalır. |

---

## Tam çalışan örnek

Aşağıda bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz tam program yer almaktadır. Gerekli tüm `using` yönergeleri ve hata yönetimi dahildir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Beklenen sonuç**: `ChartLabelsCentered.docx` dosyasını Microsoft Word'de açın. Grafiğin her dilimi artık veri etiketini dilimin tam ortasında gösterir ve daha temiz bir görsel sunum elde edilir.

---

## Sonuç

Artık C#'ta **Custom Data‑Label Placement for Charts** çözümüne sahipsiniz. Belgeyi yükleyerek, Aspose.Words chart API'si ile grafiğe erişerek, her etiket için `ChartDataLabelPosition.Center` ayarlayarak ve dosyayı kaydederek, Word tabanlı herhangi bir grafiğin etiket konumlandırmasını otomatikleştirebilirsiniz.

Sonraki adımda, `InsideEnd` veya `OutsideEnd` gibi diğer **chart data label positioning** seçeneklerini keşfedebilir, **C# chart manipulation** ile renk değiştirme, lejand ekleme ya da sıfırdan grafik oluşturma gibi işlemleri deneyebilirsiniz. Bu genişletmeler, burada ele alınan tekniklere doğrudan dayanır ve Word belge grafiği otomasyonu becerilerinizi artırır. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakın konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım‑adım açıklamalar içerir.

- [Grafik Veri Etiketini Özelleştir](/words/english/net/programming-with-charts/chart-data-label/)
- [Grafikteki Veri Etiketinin Sayısını Biçimlendir](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}