---
category: general
date: 2026-10-13
description: C# kullanarak bir Word belgesindeki grafik etiketlerini programlı olarak
  nasıl ayarlayacağınızı öğrenin. Bu rehber, Aspose.Words grafik manipülasyonu ve
  etiket hizalamasını kapsar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: tr
lastmod: 2026-10-13
og_description: C# kullanarak bir Word belgesindeki grafik etiketlerini programlı
  olarak ayarlayın. Etiket yerleşimini, hizalamasını ve daha fazlasını değiştirmek
  için bu eksiksiz öğreticiyi izleyin.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Word'de grafik etiketlerini programlı olarak ayarlama – C# adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: C# ile bir Word belgesindeki grafik etiketlerini programlı olarak ayarlama
url: /tr/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile bir Word belgesindeki grafik etiketlerini programlı olarak ayarlama

Bir Word belgesinde **grafik etiketlerini programlı olarak ayarlamanız** gerekiyorsa, bu rehber C# ile bunu tam olarak nasıl yapacağınızı gösterir. Raporlar oluşturuyor, gösterge tablolarını otomatikleştiriyor veya şablonları özelleştiriyor olun, .docx dosyasındaki bir grafiğin etiket yerleşimini ve hizalamasını değiştiren tam, çalıştırılabilir bir örnek göreceksiniz.

Ayrıca **Aspose.Words grafik manipülasyonu** tekniklerini nasıl kullanacağınızı, birden fazla seriyi nasıl yöneteceğinizi ve **C# grafik veri etiketi** nesneleriyle çalışırken yaygın tuzaklardan nasıl kaçınacağınızı öğreneceksiniz.

## Önkoşullar

* .NET 6.0 (veya daha yeni) yüklü  
* Visual Studio 2022 (veya herhangi bir C# IDE)  
* **Aspose.Words for .NET** NuGet paketi (`Install-Package Aspose.Words`)  
* En az bir grafik içeren bir Word belgesi (`input.docx`)  

Bu öğeler, değiştireceğimiz **Word belgesi grafik örneği** için gereklidir.

## Adım 1: Projeyi kurun ve ad alanlarını içe aktarın

Yeni bir konsol projesi oluşturun ve gerekli `using` yönergelerini ekleyin. Bu, **grafik etiketlerini programlı olarak ayarlama** ortamını hazırlar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Bu adım neden?*  
Belgeyi yüklemek, grafiklerin şekil düğümleri olarak depolandığı iç **Word belgesi grafik örneği** ağacına erişmenizi sağlar.

## Adım 2: İlk grafik şekline ulaşın

Grafikler `Shape` düğümleri olarak depolanır. Aşağıdaki kod, belge içindeki ilk grafiği alır; bu, etiket ayarlamalarımızın hedefidir.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Bu adım neden?*  
`GetChild` yöntemi, özyinelemeli olarak (`true`) arama yapar ve `Shape` tipinde ilk düğümü döndürür. `Chart` tipine dönüştürmek, grafik‑özel API ile çalışmamızı sağlar.

## Adım 3: Değiştirmek istediğiniz veri etiketine erişin

Bir grafikteki her seri, bir veri etiketi koleksiyonuna sahiptir. Basit bir grafik için genellikle ilk etiket yeterlidir. Aşağıdaki kod, ona nasıl ulaşılacağını gösterir.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Bu adım neden?*  
`ChartSeries`, bir nokta serisini temsil eder. `DataLabelCollection`, o seri için etiketleri tutar ve yerleşim ile hizalama üzerinde kesin kontrol sağlar.

## Adım 4: Etiket yerleşimini ve hizalamasını değiştirin

Şimdi **grafik etiketlerini programlı olarak ayarlıyoruz**; konumu, yatay hizalamayı ve dikey hizalamayı ayarlayarak. Bu özellikler, Word arayüzünde gördüğünüz seçeneklere karşılık gelir.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Bu ayarlar neden?*  

* `OutsideEnd`, etiketi her çubuk veya sütunun sonunun hemen dışına yerleştirir, okunabilirliği artırır.  
* `HorizontalAlignment.Center`, metni noktanın üzerine ortalar, `VerticalAlignment.Top` ise etiketin üst kenarını veri noktasına hizalar, diğer öğelerle çakışmayı önler.

### İpucu
Bir grafikte birden fazla seri varsa, `chart.Series` üzerinden döngü yaparak aynı ayarları her `DataLabelCollection`a uygulayın. Bu, tüm grafik boyunca tutarlı bir görünüm sağlar.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Adım 5: Değiştirilen belgeyi kaydedin

Etiketleri ayarladıktan sonra, değişiklikleri yeni bir dosyaya kaydedin. Bu, **grafik etiketi konumunu değiştirme** sürecini tamamlar.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

`output.docx` dosyasını açtığınızda, her grafik etiketinin veri noktasının dış ucuna, yatay olarak ortalanmış ve dikey olarak üstte hizalanmış şekilde taşındığını göreceksiniz.

## Kenar durumları ve varyasyonlar

| Durum | Dikkat edilmesi gerekenler | Önerilen yaklaşım |
|-----------|-------------------|----------------------|
| **Aynı belgede birden fazla grafik** | `GetChild` yalnızca ilk grafiği döndürür. | Tüm grafik şekillerini yinelemek için `doc.GetChildNodes(NodeType.Shape, true)` kullanın. |
| **Veri etiketi olmayan seriler** | `DataLabelCollection` boş olabilir. | Koleksiyona erişmeden önce `series.HasDataLabels` kontrol edin. |
| **Farklı grafik türleri** (pie, line, scatter) | Tüm `DataLabelPosition` değerleri geçerli değildir. | En iyi yerleşimi otomatik olarak belirleyen grafikler için `DataLabelPosition.Auto` kullanın. |
| **Yerelleştirme** | Hizalama sabitleri dil bağımsızdır, ancak render edilen metin sağ‑dan‑sola desteğe ihtiyaç duyabilir. | RTL dillerine ihtiyacınız varsa `dataLabel.TextDirection` ayarlayın. |

## Tam, çalıştırılabilir örnek

Aşağıda, kopyalayıp yapıştırıp çalıştırabileceğiniz tam program bulunmaktadır. `YOUR_DIRECTORY` ifadesini gerçek bir klasör yolu ile değiştirin.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Beklenen sonuç:** `output.docx` dosyasını açtığınızda, her grafik etiketi veri noktasının dışına, yatay olarak ortalanmış ve dikey olarak üstte hizalanmış olduğunu göreceksiniz—tam olarak **grafik etiketlerini programlı olarak ayarlama** etkisi.

## Sonuç

Artık C# kullanarak bir Word belgesinde **grafik etiketlerini programlı olarak ayarlamayı** biliyorsunuz. Eğitimde şunlar ele alındı:

* **Aspose.Words grafik manipülasyonu** ile bir belge yükleme  
* **C# grafik veri etiketi** erişimi  
* **grafik etiketi konumunu değiştirme** ve hizalamanın değiştirilmesi  
* Dosyayı kaydetme ve yaygın kenar durumlarını ele alma  

Buradan, etiket yazı tiplerini özelleştirme, koşullu biçimlendirme ekleme veya toplu işlemde birden fazla grafiği güncelleme gibi daha gelişmiş senaryoları keşfedebilirsiniz. Raporlarınıza en uygun stili bulmak için farklı `DataLabelPosition` seçenekleriyle deneyler yapın.

---

*Otomatik raporlama hattınızı geliştirmeye hazır mısınız? Etiketlere özel sayı formatları eklemeyi veya grafiği PDF'lerde kullanmak üzere bir görüntü olarak dışa aktarmayı deneyin.*

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki eğitimler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for .NET kullanarak Sütun Grafiğinde Tek Tip Veri Etiketleri Ayarlama](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Grafikte Veri Etiketleri İçin Varsayılan Seçenekleri Ayarlama](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Aspose.Words for .NET kullanarak Word Belgesindeki Grafik Seri Verilerini Güncelleme](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}