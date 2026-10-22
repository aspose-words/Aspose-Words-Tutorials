---
category: general
date: 2026-10-13
description: 'Bir pasta grafiğini özelleştirdikten sonra değiştirilen belgeyi kaydedin:
  dilimleri patlatın, ilk dilimin açısını değiştirin ve yüzde etiketlerini C#''ta
  gösterin.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: tr
lastmod: 2026-10-13
og_description: C#'ta bir pasta grafiğini özelleştirdikten sonra değiştirilmiş belgeyi
  kaydedin. Pasta dilimlerini patlatmayı, ilk dilimin açısını değiştirmeyi ve yüzde
  etiketlerini göstermeyi öğrenin.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Değiştirilmiş belgeyi patlatılmış pasta dilimleriyle kaydet – C# rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: C#'ta patlatılmış pasta dilimleriyle değiştirilmiş belgeyi kaydet
url: /tr/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Patlatılmış pasta dilimlerine sahip belgeyi C#'ta kaydet

Word pasta grafiğini ayarladıktan sonra **save modified document** belgesini kaydetmeniz gerekiyorsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. Pasta dilimlerini patlatmayı, ilk dilimin açısını değiştirmeyi ve yüzde etiketlerini göstermeyi öğreneceksiniz — tüm bunlar birkaç satır C# kodu ile.

Grafikleri özelleştirmek, raporlar, faturalar veya panolar oluştururken yaygın bir gereksinimdir. Bu öğreticinin sonunda bir DOCX dosyasını yükleyebilecek, grafik görünümünü değiştirebilecek ve **save modified document** dağıtıma hazır hale getirebileceksiniz.

## Önkoşullar

- .NET 6.0 veya üzeri (kod .NET Framework 4.6+ ile de çalışır)
- Aspose.Words for .NET 23.10 veya daha yeni (ücretsiz deneme veya lisanslı kopya)
- Tek bir pasta grafiği içeren bir Word dosyası (`input.docx`)
- Visual Studio 2022 veya herhangi bir C# IDE

> **İpucu:** Aspose.Words NuGet paketi `dotnet add package Aspose.Words` komutuyla eklenir.

## Adım 1: Grafiği içeren Word belgesini yükleyin

İlk adım, kaynak DOCX dosyasını açmaktır. `Document` sınıfı, tüm Word dosyasını bellekte temsil eder.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

Belgeyi yüklemek, grafikleri barındıran şekiller de dahil olmak üzere her düğüme tam erişim sağlar.

## Adım 2: Belgeden ilk grafik şekline erişin

Grafikler `Shape` düğümleri içinde depolanır. İlk grafiği `GetChild` ile bulabilirsiniz.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Belge birden fazla grafik içeriyorsa, indeksi (`0`) ayarlayın veya koleksiyon içinde döngü yapın. Bu satır, değiştireceğiniz `Chart` nesnesine bir referans elde ettiğinizden emin olur.

## Adım 3: Pasta grafik dilimlerini patlatın

Bir dilimi patlatmak, onu pastanın geri kalanından ayırır ve grafiği daha okunaklı hâle getirir. `Explode` özelliği tüm seri için çalışır.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

`Explode` özelliğini `true` olarak ayarlamak, tüm seri için **exploded pie chart slices** oluşturur; bu, her dilimin öne çıkmasını istediğinizde faydalıdır.

## Adım 4: İlk dilimin açısını değiştirin

Bazen ilk dilimin özel bir açıdan başlaması gerekir; örneğin bir tasarım kılavuzuna uymak için.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

`FirstSliceAngle` özelliği **changes first slice** yönünü değiştirir, tüm pastayı döndürerek ilk dilimin 30 dereceden başlamasını sağlar.

## Adım 5: Pasta dilimlerinde yüzde etiketlerini gösterin

Her dilimin sayısal katkısını göstermek raporlarda sıkça istenir. `DataLabel.ShowPercentage` bayrağı yüzde değerlerini açar.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Bu adım, grafiğin üzerine doğrudan **show percentage labels** ekler ve aynı zamanda **display percentages pie** gereksinimini karşılar.

## Adım 6: Değiştirilmiş belgeyi kaydedin

Tüm özelleştirmeler uygulandıktan sonra değişiklikleri yeni bir dosyaya kalıcı hâle getirin. `Save` yöntemi güncellenmiş DOCX'i diske yazar.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Artık **save modified document** içinde patlatılmış bir pasta grafiği, döndürülmüş bir ilk dilim ve görünür yüzde etiketleri bulunuyor.

![Patlatılmış pasta dilimlerine ve yüzde etiketlerine sahip değiştirilen belge](/images/pie-chart-exploded.png "Patlatılmış pasta dilimlerine ve yüzde etiketlerine sahip değiştirilen belge")

*Ekran görüntüsü, belge kaydedildikten sonraki nihai çıktıyı göstermektedir.*

## Tam, çalıştırılabilir örnek

Parçaları bir araya getirerek, bir konsol projesine kopyalayıp‑yapıştırabileceğiniz tam program aşağıdadır:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Beklenen sonuç

`output.docx` dosyasını açtığınızda aşağıdaki özelliklere sahip bir pasta grafiği göreceksiniz:

- Her dilim hafifçe ayrılmıştır (**exploded pie chart slices**)
- İlk dilim 30 derece kayma ile başlar (**change first slice**)
- Her dilim katkısını yüzde olarak gösterir (**show percentage labels**, **display percentages pie**)
- Dosya, orijinali değiştirilmeden **save modified document** edilmiştir.

## Yaygın sorular ve kenar durumları

| Soru | Cevap |
|----------|--------|
| **Belgede grafik yoksa ne olur?** | Kod, `GetChild` sonrası `null` kontrolü yapar. Grafik yoksa programatik olarak bir grafik ekleyebilir veya net bir mesajla işlemi durdurabilirsiniz. |
| **Sadece tek bir dilimi patlatabilir miyim?** | Evet. `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` ifadesini, `i` dilim indeksini belirterek kullanabilirsiniz. |
| **Etiket formatını (ör. değer + %) nasıl değiştiririm?** | `chart.PieChart.DataLabel.ShowValue = true;` ve isteğe bağlı olarak `chart.PieChart.DataLabel.ShowPercentage = true;` ayarlarını yaparak ikisini birleştirebilirsiniz. |
| **Kaydetme sonrası grafik stili korunur mu?** | Aspose.Words, **save modified document** işlemi sırasında renkler ve yazı tipleri dahil tüm stil bilgilerini korur. |
| **Aynı dosyada birden fazla grafik işleyebilir miyim?** | `NodeType.Shape` olan tüm `Shape` düğümleri üzerinden döngü yapın ve `shape.HasChart` ile filtreleyin. Aynı adımları her grafik için uygulayın. |

## Sonuç

Artık Word içinde bir pasta grafiğini programatik olarak özelleştirdikten sonra **save modified document** nasıl yapılacağını biliyorsunuz. Kılavuz, **exploded pie chart slices**, **change first slice**, **show percentage labels** ve **display percentages pie** gereksinimlerini karşılayarak pasta dilimlerini patlatma, ilk dilimin açısını değiştirme ve yüzde etiketlerini gösterme konularını kapsadı.

Sonraki adım olarak şunları keşfetmeyi düşünebilirsiniz:

- Veri serilerini dinamik olarak ekleme (`chart.Series.Add(...)`)  
- Lejant konumunu ve grafik başlıklarını özelleştirme  
- Grafik stilini koruyarak DOCX'i PDF'e dönüştürme  

Farklı açıları, patlatma ayarlarını veya etiket formatlarını deneyerek raporlama ihtiyaçlarınıza uygun hâle getirin. İyi kodlamalar!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [C# ile Düzenlenmiş Belgeyi Kaydetme – Aspose.Words ile Adım Adım Kılavuz](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Aspose.Words for .NET Kullanarak Word Belgesinde Grafik Seri Verilerini Güncelleme](/words/english/net/programming-with-charts/modify-chart-series/)
- [Word Belgesine Sütun Grafiği Ekleme](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}