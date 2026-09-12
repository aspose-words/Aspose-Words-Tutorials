---
category: general
date: 2026-09-11
description: Aspose.Words ile grafik etiketi düzenleme öğreticisi; grafik etiketi
  konumunu değiştirme, grafik veri etiketini özelleştirme, grafik kategori adını gizleme
  ve grafik etiketi değerini gösterme.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: tr
lastmod: 2026-09-11
og_description: Grafik etiketi düzenleme öğreticisi, Aspose.Words for .NET kullanarak
  grafik etiket konumunu değiştirme, grafik veri etiketini özelleştirme, grafik kategori
  adını gizleme ve grafik etiket değerini gösterme konularında size adım adım rehberlik
  eder.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: Grafik etiketi düzenleme öğreticisi – C#'ta Word grafik etiketlerini özelleştirme
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Grafik etiketi düzenleme öğreticisi – C#'ta Word grafik etiketlerini değiştir
url: /tr/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Grafik etiketini düzenleme öğreticisi – C# ile Word grafik etiketlerini değiştirme

Bir Word belgesi için **grafik etiketi düzenleme öğreticisi**'ne ihtiyacınız varsa, bu kılavuz Aspose.Words for .NET kullanarak grafik etiketi konumunu nasıl değiştireceğinizi, grafik veri etiketini nasıl özelleştireceğinizi, grafik kategori adını nasıl gizleyeceğinizi ve grafik etiketi değerini nasıl göstereceğinizi tam olarak gösterir. Herhangi bir C# projesine ekleyebileceğiniz tam, çalıştırılabilir bir örnek göreceksiniz.

Grafik etiketleriyle çalışmak, raporlar, faturalar veya gösterge tabloları programlı olarak oluşturulurken yaygın bir gereksinimdir. Bu öğretici, belgeyi yüklemekten değişiklikleri kalıcı hale getirmeye kadar her adımı kapsar—böylece manuel düzenleme yapmadan şık grafikler üretebilirsiniz.

## Önkoşullar

* .NET 6.0 veya daha yeni bir sürüm yüklü  
* Geçerli bir Aspose.Words for .NET lisansı (veya geçici değerlendirme anahtarı)  
* Visual Studio 2022 veya herhangi bir C# uyumlu IDE  
* En az bir grafik içeren bir Word dosyası (`Chart.docx`)

`Aspose.Words` dışındaki ek NuGet paketlerine gerek yok.

## Adım 1: Projeyi kurun ve ad alanlarını içe aktarın

Create a new console application and add the Aspose.Words NuGet package:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

Open `Program.cs` and import the required namespaces:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

Bu ad alanları, Word dosyalarını işlemek için `Document` sınıfına ve grafik öğelerini manipüle etmek için `Chart` sınıflarına erişmenizi sağlar.

## Adım 2: Grafik içeren Word belgesini yükleyin

The first actionable line loads the source document. Replace `YOUR_DIRECTORY` with the actual path where `Chart.docx` resides.

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

Belgeyi yüklemek, üzerinde gezinebileceğiniz ve değiştirebileceğiniz bellek içi bir temsil oluşturur.

## Adım 3: Belgedeki ilk grafiği alın

Charts are stored as child nodes of type `NodeType.Chart`. The `GetChild` method searches the document tree and returns the chart you want to edit.

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

Belge birden fazla grafik içeriyorsa, farklı bir grafik hedeflemek için indeksi değiştirebilirsiniz.

## Adım 4: İlk serinin veri etiketine erişin ve özelleştirin

Every chart series has a `DataLabel` object that controls how the label appears. The code below demonstrates the four key customizations required by the tutorial’s secondary keywords.

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**Bu ayarların önemi**

* `DataLabelPosition.Center`, etiketi varsayılan nokta dışı konumundan veri noktasının ortasına taşır; bu, noktalar sıkışık olduğunda grafiğin okunmasını kolaylaştırır.  
* Özel bir `Separator` ayarlamak, seri adı, değer ve diğer bölümlerin nasıl birleştirileceğini kontrol etmenizi sağlar.  
* Kategori adını gizlemek (`ShowCategoryName = false`), kategori eksenden zaten belli olduğunda görsel karmaşayı azaltır.  
* `ShowValue` etkinleştirildiğinde gerçek veri değeri görünür; bu, finansal veya istatistiksel raporlar için sıkça gereklidir.

## Adım 5: Değiştirilen belgeyi kaydedin

After adjusting the label properties, persist the changes back to a new file:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

Yeni dosya (`CustomLabelChart.docx`), aynı grafik düzenine sahiptir ancak tanımladığınız etiket görünümünü içerir.

## Tam kaynak kodu

Below is the complete, ready‑to‑run program. Copy it into `Program.cs`, adjust the file paths, and execute the project.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### Beklenen sonuç

`CustomLabelChart.docx` dosyasını Microsoft Word'de açın. Grafiğin ilk serisinin etiketinin her veri noktasının ortasında, yalnızca sayısal değeri gösterdiğini ve “; ” ayırıcıyı kullandığını görmelisiniz. Kategori adları artık değerlerin yanında görünmeyecek.

## Yaygın sorular ve uç durumlar

| Soru | Cevap |
|----------|--------|
| **Belge hiç grafik içermiyorsa ne olur?** | Örnek, `null` bir grafik olup olmadığını kontrol eder ve konsol mesajı ile nazikçe çıkar. |
| **Birden fazla seri için etiketleri düzenleyebilir miyim?** | Evet. `chart.Series` üzerinde döngü yaparak her `Series[i].DataLabel` için aynı `DataLabel` ayarlarını uygulayabilirsiniz. |
| **Etiketin yazı tipi stilini nasıl değiştiririm?** | `label.Font` kullanın (örnek: `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **`DataLabelPosition.Center` tüm grafik türleri için destekleniyor mu?** | Çoğu 2‑B grafik türü bunu destekler. 3‑B grafiklerde bazı konumlar Word tarafından göz ardı edilebilir. |
| **Aspose.Words için lisansa ihtiyacım var mı?** | Değerlendirme modu çalışır ancak bir filigran ekler. Lisans, filigranı kaldırır ve tam işlevselliği açar. |

## Profesyonel ipuçları

* **Toplu işleme:** Yükleme ve kaydetme mantığını, giriş ve çıkış yollarını kabul eden bir metoda sarın. Bu, bir döngüde onlarca belgeyi işlemeyi kolaylaştırır.  
* **Performans:** Aynı dosyada birden fazla grafik değiştirirken tekrar tekrar I/O yapmamak için tek bir `Document` örneğini yeniden kullanın.  
* **Test:** CI boru hatlarında çıktıyı doğrulamanız gerekiyorsa, etiket değişikliklerini otomatik bir görsel fark (ör. başsız bir Word görüntüleyici) ile doğrulayın.

## Sonraki adımlar

Now that you can **edit chart label tutorial** basics, consider exploring:

* **Diğer seriler veya farklı grafik türleri için grafik etiketi konumunu değiştirin**  
* **Grafik veri etiketi** biçimlendirmesini, örneğin sayı formatları, yazı tipi renkleri veya arka plan doldurmaları gibi özelleştirin  
* **Grafik kategori adını gizleyin** ancak çoklu seri grafiklerde seri adını göstermeye devam edin  
* **Grafik etiketi değerini** pasta grafiklerde yüzde değerleriyle birlikte gösterin  

These topics deepen your control over Word chart aesthetics and prepare you for advanced reporting scenarios.

*Kodlamanın keyfini çıkarın! Bu öğreticiyi faydalı bulduysanız, ekip arkadaşlarınızla paylaşın veya GitHub'da iyileştirmeler katkıda bulunun.*

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Grafik Veri Etiketini Özelleştir](/words/english/net/programming-with-charts/chart-data-label/)
- [Grafik Veri Etiketi](/words/german/net/programming-with-charts/chart-data-label/)
- [Grafik Veri Etiketi](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}