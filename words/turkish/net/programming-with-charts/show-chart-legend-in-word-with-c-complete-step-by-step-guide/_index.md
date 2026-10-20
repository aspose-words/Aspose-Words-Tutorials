---
category: general
date: 2026-06-02
description: C# kullanarak bir Word belgesinde grafik açıklama kutusunu göster. Açıklama
  kutusunu eklemeyi, önceden ayarlanmış grafik stilini uygulamayı ve Word grafik görsellerini
  dakikalar içinde özelleştirmeyi öğrenin.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: tr
og_description: Word belgesinde grafik açıklamasını anında gösterin. Bu rehber, bir
  açıklama eklemeyi, önceden ayarlanmış grafik stilini uygulamayı ve uç durumları
  ele almayı adım adım gösterir.
og_title: Word'de Grafik Açıklamasını Göster – Tam C# Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: C# ile Word'de Grafik Lejantını Göster – Tam Adım Adım Kılavuz
url: /tr/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de C# ile Grafik Açıklamasını Göster – Tam Adım‑Adım Kılavuz

Bir Word belgesi içinde yer alan bir grafiğe **açıklama (legend) eklemenin** nasıl yapılacağını hiç merak ettiniz mi? Tek başınıza değilsiniz. Birçok raporda eksik bir açıklama verileri anlaşılmaz kılar ve bunu düzeltmek zor olmamalı.  

Bu öğreticide Aspose.Words for .NET kullanarak bir Word dosyasında **grafik açıklamasını gösterecek**, önceden tanımlı bir grafik stilini uygulayacak ve açıklamanın tam istediğiniz yerde görünmesini sağlayacağız. Sonunda, herhangi bir C# projesine ekleyebileceğiniz çalıştırılabilir bir örnek elde edeceksiniz.

## Bu Kılavuzda Neler Ele Alınıyor

Tüm iş akışını adım adım inceleyeceğiz:

1. İçinde zaten bir grafik bulunan mevcut *.docx* dosyasını yükleyin.  
2. İlk grafiği (veya hedeflediğiniz herhangi bir grafiği) alın.  
3. Görseli profesyonel bir görünüme kavuşturmak için **önceden tanımlı grafik stilini uygulayın**.  
4. **Grafik açıklamasını gösterin**, sağ tarafa konumlandırın ve Waterfall (Şelale) grafikleri gibi özel durumları yönetin.  
5. Değiştirilen belgeyi kaydedin.

Harici araçlar, UI ile manuel ayarlamalar yok—sadece saf kod. Tek ön koşul, Aspose.Words NuGet paketine (versiyon 23.10 veya daha yeni) referans ve temel C# bilgisi.

---

## Ön Koşullar

- .NET 6.0 veya üzeri (örnek .NET Framework 4.7.2 ile de çalışır).  
- Aspose.Words for .NET kütüphanesi yüklü (`Install-Package Aspose.Words`).  
- En az bir grafik içeren bir Word dosyası (`input.docx`).  
- Visual Studio, Rider veya tercih ettiğiniz herhangi bir IDE.

---

## Adım 1: Projeyi Oluşturun ve Belgeyi Yükleyin

İlk olarak bir console uygulaması oluşturun (veya kodu mevcut bir projeye entegre edin). `using` yönergelerini ekleyin ve `.docx` dosyasını yükleyin.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Neden önemli:** Belgeyi yüklemek temeldir. Bir `Document` örneği olmadan Aspose.Words'un sunduğu grafik nesnelerine ulaşamazsınız.

---

## Adım 2: Hedef Grafiği Alın

Grafikler, belge ağacındaki düğümler olarak depolanır. `GetChild` metodu derin bir arama yapar ve grafiğin nerede bulunduğuna bakılmaksızın ilk grafiği getirir (başlık, gövde, alt bilgi vb.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **İpucu:** Birden fazla grafiğiniz varsa, indeks `0` yerine `1`, `2` … kullanın veya `doc.GetChildNodes(NodeType.Chart, true)` üzerinden döngü yapın.

---

## Adım 3: Önceden Tanımlı Görsel Stili Uygulayın

İyi görünümlü bir grafik genellikle bir stil ile başlar. Aspose.Words, yüzlerce yerleşik stile sahiptir; `ChartStyle.Style12` temiz ve modern bir seçenektir.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Nasıl çalışır:** `Style` özelliği, UI’da gördüğünüz yerleşik Word grafik stillerine karşılık gelir. Bir ön ayar seçmek, renk, yazı tipi ve işaretçi ayarlarını manuel yapmaktan sizi kurtarır.

---

## Adım 4: Açıklamayı Etkinleştirip Konumlandırın

Şimdi gösterinin yıldızı—**grafik açıklamasını göster**. Açıklamayı açıyoruz, ardından grafiğin sağ tarafına yerleştiriyoruz.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Neden sağ?** Açıklamayı sağa koymak veri alanını geniş tutar; bu özellikle çubuk veya sütun grafiklerde faydalıdır.

---

## Adım 5: Waterfall Grafiklerini İşleyin (Özel Durum)

Waterfall (Şelale) grafikleri biraz farklı davranır; açıklama varsayılan olarak gizli olabilir. Aşağıdaki koruma ifadesi, grafik tipi Waterfall olduğunda açıklamanın görünür olmasını sağlar.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Köşe durumu notu:** Bazı eski Word sürümleri Waterfall grafiklerinde `HasLegend` özelliğini görmez, bu yüzden `Legend.Show` değerini açıkça ayarlamak görünürlüğü garantiler.

---

## Adım 6: Değiştirilen Belgeyi Kaydedin

Son olarak değişiklikleri diske yazın. Orijinal dosyanın üzerine yazabilir ya da yeni bir dosya oluşturabilirsiniz.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

Programı çalıştırdığınızda `output.docx` dosyası sağda görünür bir açıklama ve `Style12` stiliyle oluşturulmuş bir grafik içerir. Sonucu doğrulamak için dosyayı Word’de açın.

---

## Tam Çalışan Örnek (Tüm Adımlar Birleştirilmiş)

Aşağıda eksiksiz, çalıştırmaya hazır kod yer alıyor. `Program.cs` (veya herhangi bir C# dosyası) içine kopyalayıp dosya yollarını ayarlayın.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Beklenen çıktı:** `output.docx` dosyasını açtığınızda orijinal grafik sağa hizalanmış bir açıklama ve modern `Style12` stiliyle görüntülenir. Tüm veri serileri net bir şekilde etiketlenmiş olur, böylece grafik anında anlaşılır hâle gelir.

---

## Sık Sorulan Sorular (SSS)

### Belirli bir grafiğe (ilk değil) nasıl açıklama eklenir?

`GetChild(NodeType.Chart, 0, true)` ifadesindeki `0` indeksini hedef grafiğinizin sıfır‑tabanlı konumuyla değiştirin veya tüm grafik düğümleri üzerinde döngü kurun:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Açıklamayı sağ yerine alt tarafa koyabilir miyim?

Elbette. `LegendPosition` enum değerini değiştirmeniz yeterli:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### Grafik zaten bir açıklamaya sahipse, onu gizlemek istersem ne yapmalıyım?

`HasLegend` özelliğini `false` olarak ayarlayın:

```csharp
chart.HasLegend = false;
```

### Bu kod Word 2010, 2016 ve sonrası sürümlerle çalışır mı?

Evet. Aspose.Words, altında yatan Word sürümünü soyutladığı için aynı kod tüm modern .docx dosyalarında sorunsuz çalışır.

---

## Pro İpuçları & Yaygın Tuzaklar

- **Pro ipucu:** Stil uygulandıktan sonra `Chart.Series` koleksiyonu üzerinden bireysel öğeleri (renkler, veri etiketleri vb.) hâlâ ayarlayabilirsiniz. Stil, sağlam bir temel sağlar.  
- **Dikkat:** Grafik bir tablo hücresi içinde ise açıklama sıkışık görünebilir. Açıklamayı konumlandırmadan önce grafiğin boyutunu (`chart.Width`, `chart.Height`) artırmayı düşünün.  
- **Performans notu:** Yüzlerce MB büyüklüğündeki büyük belgeleri yüklemek bellek yoğun olabilir. Sadece grafik manipülasyonu yapacaksanız `LoadOptions` ile `LoadFormat.Docx` belirterek yükleme yükünü azaltabilirsiniz.

---

## Sonraki Adımlar

Artık **grafik açıklamasını eklemeyi** ve **önceden tanımlı grafik stilini uygulamayı** Word içinde C# ile yapabildiğinize göre aşağıdaki konuları keşfedebilirsiniz:

- **Özel grafik renkleri** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Veri etiketi biçimlendirme** (`chart.Series[i].HasDataLabel = true`).  
- **Grafiği resim olarak dışa aktarma** (`chart.ToImage()`), başka bir yerde gömmek için faydalı.  

Bu konular aynı nesne modeline dayanır, öğrenme eğrisi oldukça hafif olacaktır.

---

## Sonuç

C# kullanarak Word belgesinde **grafik açıklamasını göster** ve **önceden tanımlı grafik stilini uygula** konusundaki temiz, uçtan uca çözümümüzü gösterdik. Belgeyi yükleyip grafiği alıp stili uygulayıp açıklamayı etkinleştirerek ve Waterfall özel durumlarını ele alarak, herhangi bir iş raporu için hazır, şık bir grafik elde ettiniz.  

Farklı `ChartStyle` değerleri veya açıklama konumlarıyla denemeler yapmaktan çekinmeyin—veri görselleştirmenizin en iyi sunumu hak ediyor. Herhangi bir sorunla karşılaşırsanız aşağıya yorum bırakın; mutlu kodlamalar!  


## Bir Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakın konuları kapsar. Her kaynak, adım adım açıklamalar ve tam çalışan kod örnekleri içerir; böylece API özelliklerini daha iyi kavrayabilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}