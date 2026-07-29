---
category: general
date: 2026-07-29
description: Word belgesinde grafiği nasıl düzenlenir—grafik etiket konumunu değiştirmeyi,
  çubuk grafik etiketlerini ayarlamayı, grafik veri etiketlerini değiştirmeyi ve grafik
  etiket yazı tipini değiştirmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: tr
lastmod: 2026-07-29
og_description: Word'de grafiği hızlıca nasıl düzenlersiniz. Grafik etiket konumunu
  değiştirmeyi, çubuk grafik etiketlerini ayarlamayı, veri etiketlerini düzenlemeyi
  ve grafik etiket yazı tipini değiştirmeyi öğrenin.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Word'de Grafik Nasıl Düzenlenir – Etiketleri ve Yazı Tipini Değiştir
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Word''de Grafiği Nasıl Düzenlersiniz: Etiket Konumunu, Yazı Tipini ve Daha
  Fazlasını Değiştirin'
url: /tr/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Grafik Nasıl Düzenlenir: Etiket Konumunu, Yazı Tipini ve Daha Fazlasını Değiştirin

Word belgesinde grafiği düzenlemek, raporlarınızın şık görünmesini istediğinizde yaygın bir ihtiyaçtır. **change chart label position**'ı değiştirmekte ya da etiketleri sonsuz menüler arasında kaybolmadan okunabilir hâle getirmekte zorlandınız mı? Yalnız değilsiniz—çoğu geliştirici rapor oluşturmayı otomatikleştirirken bu engelle karşılaşır. Bu rehberde, C# ve Aspose.Words kütüphanesini kullanarak **adjust bar chart labels**, **modify chart data labels** ve **change chart label font**'u nasıl yapacağınızı gösteren tam, çalıştırılabilir bir örnek üzerinden ilerleyeceğiz.

## Öğrenecekleriniz

- Zaten bir çubuk grafik içeren bir .docx dosyasını yükleyin.  
- İlk grafik şekli alın ve veri‑etiket koleksiyonuna erişin.  
- **Change chart label position** ile çubukların daha temiz görünmesini sağlayın.  
- **Adjust bar chart labels** yazı tipi boyutunu daha iyi okunabilirlik için ayarlayın.  
- Değiştirilmiş belgeyi diske kaydedin.  

Harici araçlar yok, manuel UI adımları yok—sadece herhangi bir .NET projesine ekleyebileceğiniz saf kod. Sonunda, onlarca belge arasında yeniden kullanabileceğiniz bağımsız bir çözümünüz olacak.

> **Prerequisites**  
> - .NET 6.0 veya daha yenisi (kod .NET Framework 4.7+ üzerinde de çalışır).  
> - Aspose.Words for .NET (NuGet üzerinden temin edilebilir).  
> - Zaten bir çubuk grafik içeren bir Word dosyası (`BarChart.docx`).  

Eğer bunlardan herhangi birine sahip değilseniz, en yeni Aspose.Words paketini hemen edinin:

```bash
dotnet add package Aspose.Words
```

---

## Grafik Nasıl Düzenlenir: Grafiği Word Belgesinden Almak

**how to edit chart** nesneleriyle ilgili ilk adım, belgeyi yüklemek ve grafik şeklinin konumunu bulmaktır. Aspose.Words, grafikleri `Shape` düğümleri olarak ele alır, bu yüzden karşılaştığımız ilk grafiği almak için `GetChild`'i `NodeType.Shape` ile kullanabiliriz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Why this matters:**  
> `Chart` nesnesine doğrudan erişerek, dosyayı Word'de açmanın ve her etiketi manuel olarak ayarlamanın getirdiği yükten kaçınırsınız. Bu, herhangi bir **modify chart data labels** otomasyonunun temel taşıdır.

## Çubuk Grafik Etiketlerini Ayarlama: Grafik Etiket Konumunu Değiştirme

Artık `Chart` örneğine sahip olduğumuza göre, onun `DataLabelCollection`'ı üzerinde döngü yapalım. Amaç, **change chart label position**'ı değiştirerek her etiketin çubuğun tabanına düzgün bir şekilde oturmasını sağlamak, üstünde garip bir şekilde süzülmek yerine.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Pro tip:**  
> `InsideBase` dikey çubuk grafiklerde iyi çalışır. Yatay bir çubuk grafikle çalışıyorsanız, bunun yerine `InsideEnd` deneyin. Pozisyonlarla deneme yapmak ucuzdur—sadece kodu yeniden çalıştırın ve kaydedilen belgeyi açın.

## Grafik Etiket Yazı Tipini Değiştir: Okunabilirlik İçin Yazı Tipi Boyutunu Ayarla

Küçük bir yazı tipi, rapor netliğinin sessiz katilidir. **change chart label font** yapmak için, her `ChartDataLabel` üzerindeki `Font.Size` özelliğini ayarlamanız yeterlidir. Çoğu basılı rapor için ideal bir nokta olan 9 pt'ye yükselteceğiz.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Why we do this:**  
> Yazı tipi boyutunu ayarlamak, **modify chart data labels** en iyi uygulamalarının bir parçasıdır. Daha büyük yazı tipleri erişilebilirliği artırır ve manuel son‑işleme ihtiyacını azaltır.

## Güncellenmiş Belgeyi Kaydet

Pozisyonları ve yazı tiplerini ayarladıktan sonra, **how to edit chart**'in son adımı değişiklikleri kalıcı hâle getirmektir. Aspose.Words bunu tek satırda yapar.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

`BarChartCustomLabels.docx` dosyasını Word'de açın ve etiketlerin çubukların içinde sıkı bir şekilde yer aldığını, net 9 pt yazı tipiyle görüntülendiğini göreceksiniz. Artık küçük sayılara göz kırpmak zorunda kalmayacaksınız.

---

## Tam Çalışan Örnek (Tüm Adımlar Tek Dosyada)

Aşağıda, belgeyi yüklemekten güncellenmiş sürümü kaydetmeye kadar tüm akışı gösteren tam, çalıştırılabilir bir konsol programı bulunuyor. Yeni bir .NET konsol projesine kopyalayıp **F5** tuşuna basın.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Expected output** programı çalıştırdığınızda:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Oluşan dosyayı açın ve **adjust bar chart labels**'in çubukların içinde rahat bir yazı tipi boyutuyla konumlandığını göreceksiniz.

---

## Yaygın Sorular ve Kenar Durumları

### Belge birden fazla grafik içeriyorsa ne olur?

Yukarıdaki kod, *ilk* grafiği alır (`GetChild(NodeType.Shape, 0, true)`). Tüm grafikleri düzenlemek için tek alımı bir döngü ile değiştirin:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### Belirli bir seri için sadece **change chart label font** nasıl yapılır?

Her `ChartSeries` kendi `DataLabelCollection`'ına sahiptir. Bir seriyi indeksle hedefleyin:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Bu, pasta veya çizgi grafiklerle çalışır mı?

Evet—`ChartDataLabelPosition` `InsideEnd`, `OutsideEnd` ve `BestFit` gibi değerleri destekler. Bir pasta grafik için etiketlerin okunabilir kalmasını sağlamak amacıyla `OutsideEnd` tercih edebilirsiniz.

### Yerelleştirme (ör. farklı ondalık ayırıcılar) hakkında ne?

Aspose.Words, belgenin yerel ayarlarını dikkate alır. Belirli bir formatı zorunlu kılmanız gerekiyorsa, kaydetmeden önce `label.NumberFormat`'ı ayarlayın.

---

## Özet ve Sonraki Adımlar

**how to edit chart** nesnelerini bir Word belgesinde baştan sona ele aldık: dosyayı yükleme, grafiği alma, **changing chart label position**, **adjusting bar chart labels**, **modifying chart data labels** ve son olarak kaydetmeden önce **changing chart label font**. Tam örnek üretime hazırdır ve herhangi bir otomasyon hattına eklenebilir.

Daha ileriye gitmeye hazır mısınız? Aşağıdaki takip fikirlerini göz önünde bulundurun:

- **Add data label colors** (`dataLabel.Font.Color = Color.Blue;`).  
- **Show values as percentages** (`dataLabel.NumberFormat = "0%";`).  
- **Create charts programmatically** instead of loading existing ones.  

Bunların hepsi bugün kullandığımız aynı API yüzeyine dayanır, bu yüzden kendinizi evinizde gibi hissedeceksiniz.

Herhangi bir sorunla karşılaşırsanız, aşağıya yorum bırakın ya da daha derin grafik özelleştirme seçenekleri için Aspose.Words belgelerine göz atın. İyi kodlamalar ve güzel etiketlenmiş grafiklerin tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Grafik Veri Etiketini Özelleştir](/words/english/net/programming-with-charts/chart-data-label/)
- [Grafikte Veri Etiketi Sayısını Biçimlendir](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Grafik Veri Etiketi](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}