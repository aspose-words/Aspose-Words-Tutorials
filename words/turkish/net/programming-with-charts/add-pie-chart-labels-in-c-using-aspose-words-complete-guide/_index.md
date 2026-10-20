---
category: general
date: 2026-07-20
description: Aspose.Words for .NET ile pasta grafik etiketleri ekleyin. Pasta grafik
  etiketlerini nasıl değiştireceğinizi, yüzde etiketlerini nasıl göstereceğinizi ve
  grafik serisi etiketlerini nasıl hızlı bir şekilde güncelleyeceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: tr
lastmod: 2026-07-20
og_description: Aspose.Words ile C#'ta pasta grafik etiketleri ekleyin. Sadece birkaç
  adımda pasta grafik etiketlerini değiştirmeyi, yüzde etiketlerini göstermeyi ve
  grafik serisi etiketlerini güncellemeyi ustalaşın.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: C#'de pasta grafik etiketleri ekleyin – Aspose.Words Tam Öğretici
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Aspose.Words kullanarak C#'de pasta grafik etiketleri ekleme – Tam Kılavuz
url: /tr/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Aspose.Words kullanarak pasta grafik etiketleri ekleme – Tam Kılavuz

C# kullanarak bir Word belgesine **pasta grafik etiketleri** eklemek mi istiyorsunuz? Aspose.Words ile **pasta grafik etiketlerini** kolayca **değiştirebilir** ve **pasta grafik yüzdelerini** dosyanın içinde doğrudan görüntüleyebilirsiniz—Word'de manuel ayarlama yapmanıza gerek kalmaz.  

Bu öğreticide, **yüzde etiketlerini** göstermek, konumlarını yeniden ayarlamak ve dinamik veriler için **grafik serisi etiketlerini** güncellemek için tam adımları anlatacağız. Sonunda, herhangi bir .NET projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız.

> **Hızlı önizleme:** Kılavuzu izledikten sonra, kaydedilen `.docx` dosyasını açtığınızda, her dilimin yüzdeyle etiketlendiği ve okunabilirliği en üst düzeye çıkarmak için dilimin dışına konumlandırılmış bir pasta grafik göreceksiniz.

---

## İhtiyacınız Olanlar

- **Aspose.Words for .NET** (2026 itibarıyla en son sürüm). NuGet'ten alabilirsiniz: `Install-Package Aspose.Words`.
- **Word belgesi** içinde zaten bir pasta veya halka grafik bulunan (biz ona `Chart.docx` diyeceğiz).
- **C#** ve Visual Studio (veya sevdiğiniz IDE) hakkında temel bilgi.

Hepsi bu—ekstra kütüphane yok, COM interop yok, sadece saf yönetilen kod.

---

## Pasta grafik etiketleri ekleme – Tam Uygulama

Aşağıda, bir belgeyi yükleyen, ilk pasta grafiğini değiştiren ve sonucu kaydeden **tam, çalıştırılabilir** bir C# konsol programı bulunmaktadır. Her satır yorumlanmıştır, böylece sadece **ne** yaptığımızı değil, **neden** yaptığımızı da anlayacaksınız.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Beklenen Sonuç

`ChartWithCustomLabels.docx` dosyasını Microsoft Word'de açın. Pasta grafiğini **her dilimin dışına konumlandırılmış yüzde etiketleriyle** görmelisiniz. Etiketler “35 %”, “20 %” gibi görünecek ve grafiği anında anlaşılır kılacaktır.

---

## Pasta grafik etiketlerini değiştirme: konumlandırma ve biçimlendirme

Yüzdeleri göstermeden sadece **pasta grafik etiketlerini değiştirmek** istiyorsanız, `Position` özelliğini aşağıdakilerden birine ayarlayabilirsiniz:

| Position Enum | Visual Effect |
|---------------|---------------|
| `InsideEnd`   | Etiketler dilimin içinde, kenarın tam üzerinde yer alır. |
| `Center`      | Etiketler dilimin ortasında görünür (küçük pastalar için iyidir). |
| `OutsideEnd`  | Etiketler dilimin dışındadır ve bir gösterge çizgisiyle bağlanır (bizim varsayılan). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Pro ipucu:** `OutsideEnd`, grafikte çok sayıda dilim olduğunda en iyi çalışır; metin çakışmalarını önler.

---

## Pasta grafiğinde yüzde etiketlerini gösterme

`ShowPercentage` özelliği bir **boolean bayrağı**dır. `true` olarak ayarlandığında, Aspose.Words her dilimin temel veri kaynağına göre katkısını hesaplar.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

Hem ham sayıları **hem** yüzdeyi istiyorsanız, `ShowValue` ile birlikte de kullanabilirsiniz:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

Her iki bayrak da etkinleştirildiğinde, etiket “45 % (120)” şeklinde görünür.

---

## Dinamik veri için grafik serisi etiketlerini güncelleme

Genellikle grafikleri anlık olarak oluşturursunuz—örneğin aylık satışlar veya anket sonuçları. **Grafik serisi etiketlerini** programlı olarak güncellemek için, veri etiketlerine dokunmadan önce `Series` koleksiyonunu değiştirin:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

Bu kod parçacığı, sadece ilk seriyi değil, herhangi bir seriyi **grafik serisi etiketlerini** güncellemenin nasıl yapılacağını gösterir. Gerçek ve tahmin verilerini birleştiren raporlar oluştururken kullanışlıdır.

---

## Kenar Durumları ve Yaygın Tuzaklar

| Situation | What to Watch For | Fix |
|-----------|-------------------|-----|
| **Grafik bir pasta/halkalı değil** | `Position` görsel bir etki göstermeyebilir. | `chart.Type`'ın `ChartType.Pie` veya `ChartType.Doughnut` olduğundan emin olun. |
| **Grafik bulunamadı** | `GetChild` `null` döndürür. | Bir koruma koşulu ekleyin (koda bakın) ve yardımcı bir mesaj kaydedin. |
| **Eski Word sürümü** | Bazı etiket özellikleri göz ardı edilir. | Tam destek garantisi için `.docx` (modern format) olarak kaydedin. |
| **Dilimin sayısı çok fazla** | `OutsideEnd` ile bile etiketler çakışabilir. | Dilimin sayısını azaltmayı veya grafik boyutunu artırmayı düşünün. |

---

## Tam Çalışan Örnek (Kopyala‑Yapıştır)

Aşağıda, yeni bir konsol projesine kopyalayabileceğiniz **tam program** bulunmaktadır. `YOUR_DIRECTORY` kısmını `Chart.docx` dosyasının bulunduğu klasörle değiştirmeniz yeterlidir.



## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalarla birlikte tam çalışan kod örnekleri içerir; böylece ek API özelliklerini öğrenebilir ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Bir Grafikte Veri Etiketleri İçin Varsayılan Seçenekleri Ayarlama](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Bir Grafikte Tek Seri Özelleştirme](/words/english/net/programming-with-charts/single-chart-series/)
- [Aspose.Words for .NET Kullanarak Word'e Sütun Grafiği Ekleme](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}