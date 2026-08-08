---
category: general
date: 2026-08-07
description: C#'ta hızlı bir şekilde pasta grafiği oluşturun. Pasta grafiği eklemeyi,
  veri etiketlerini eklemeyi, yüzdeyi gösteren grafiği ve grafik veri etiketlerini
  özelleştirmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: tr
lastmod: 2026-08-07
og_description: Aspose.Words ile C#’ta pasta grafik oluşturma. Bu öğreticide, pasta
  grafiği ekleme, veri etiketleri ekleme ve yüzde gösterimi yapma, ayrıca grafik veri
  etiketlerini özelleştirme gösterilmektedir.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: C#'ta pasta grafiği kelimesi oluştur – tam öğretici
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: C#'ta pie chart kelimesi oluşturma – adım adım rehber
url: /tr/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta pie chart word oluşturma – adım‑adım kılavuz

Eğer C#'ta **create pie chart word** belgeleri oluşturmanız gerekiyorsa, bu kılavuz eksiksiz, çalıştırmaya hazır bir çözüm sunar. **insert pie chart**, **add data labels pie** ve **show percentage chart** nasıl yapılacağını, ayrıca **customize chart data labels** ile nasıl şık bir görünüm elde edileceğini göreceksiniz.

Programatik olarak grafik oluşturmak, özellikle raporlar veya panolar otomatik olarak üretilmesi gerektiğinde, manuel düzenlemeden sizi kurtarır. Aşağıdaki bölümlerde Aspose.Words for .NET kullanarak bir Word dosyasına tamamen etiketlenmiş bir pasta grafiği yerleştirmek için gereken her şeyi öğreneceksiniz.

## Önkoşullar ve kurulum

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 SDK veya daha yeni bir sürüm.  
* Geçerli bir Aspose.Words for .NET lisansı (veya geçici bir değerlendirme anahtarı).  
* Visual Studio 2022 (veya C# destekleyen herhangi bir IDE).  

Projeye Aspose.Words NuGet paketini ekleyin:

```bash
dotnet add package Aspose.Words
```

> **Pro ipucu:** Çok sayıda grafik oluşturmayı planlıyorsanız, daha iyi performans için **Free‑Form Drawing** modunu (`DocumentBuilder.UseFreeFormDrawing = true`) etkinleştirin.

## Aspose.Words ile pie chart word oluşturma

İlk büyük adım, boş bir Word belgesi ve bir `DocumentBuilder` oluşturmaktır. Bu nesne, sonraki tüm eklemeleri yönlendirir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Neden önemli*: `Document`, tüm `.docx` dosyasını temsil ederken, `DocumentBuilder` paragraf, tablo ve grafik eklemek için akıcı bir API sağlar. Temiz bir belgeyle başlamak, gizli biçimlendirmelerin grafik düzenini etkilemesini önler.

## Belgeye pie chart ekleme

Şimdi istediğimiz boyutta bir pasta grafiği yerleştiriyoruz. `InsertChart` yöntemi, daha fazla yapılandırma yapabileceğimiz bir `Chart` nesnesi döndürür.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Neden önemli*: `ChartType.Pie` bayrağı, Aspose.Words'a dairesel bir grafik üretmesini söyler. Genişlik (`400`) ve yükseklik (`300`) puan cinsindendir, bu da görsel alan üzerinde hassas kontrol sağlar.

## Grafiği veri ile doldurma

Bir pasta grafiği en az bir sayı serisine ihtiyaç duyar. Burada üç kategori ekliyoruz: “Apples”, “Bananas” ve “Cherries”.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Neden önemli*: Her `AddCategory` çağrısı bir dilim oluşturur. Sayısal değer dilim boyutunu belirler, etiket ise veri etiketleri açıldığında gösterilen kategori adını oluşturur.

## add data labels pie ve show percentage chart

Grafiği bilgilendirici hâle getirmek için veri etiketlerini etkinleştiriyor, dilimlerin dışına konumlandırıyor ve Aspose.Words'tan hem kategori adını hem de yüzdeyi göstermesini istiyoruz.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Neden önemli*: `Position` değerini `OutsideEnd` olarak ayarlamak, özellikle dilimler küçükse okunabilirliği artırır. `ShowCategoryName` ve `ShowPercentage`'ı etkinleştirmek, **show percentage chart** gereksinimini karşılar ve **add data labels pie** hedefini yerine getirir.

## chart data labels'ı daha da özelleştirme (isteğe bağlı)

Yazı tipini değiştirmek, bir leader line eklemek veya legend'ı gizlemek isteyebilirsiniz. Aşağıdaki kod parçacığı yaygın özelleştirmeleri gösterir:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Neden önemli*: Etiket görünümünü özelleştirmek, grafiğin belge stil kılavuzunuza uymasını sağlar. Legend'ı kaldırmak, veri etiketleri zaten aynı bilgiyi ilettiğinde görsel karmaşayı azaltır.

## Özelleştirilmiş grafikle belgeyi kaydetme

Son olarak belgeyi diske yazıyoruz. Yazma izninizin olduğu bir yolu seçin.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

`ChartWithCustomLabels.docx` dosyasını Microsoft Word'de açtığınızda, her dilimin kategori adı ve yüzdeyle etiketlendiği, dilimin dışına konumlandırıldığı ve özel yazı tipi ayarlarıyla biçimlendirildiği bir pasta grafiği göreceksiniz.

### Beklenen çıktı

| Dilim   | Değer | Yüzde | Word'de gösterilen etiket |
|---------|-------|------------|---------------------------|
| Apples  | 40    | 40 %       | Apples – 40 %             |
| Bananas | 35    | 35 %       | Bananas – 35 %            |
| Cherries| 25    | 25 %       | Cherries – 25 %           |

Grafik, aşağıdaki görseldeki gibi görünmelidir:

![Word belgesi, her dilimin dışına yüzde etiketleri yerleştirilmiş bir pie chart gösteriyor](pie-chart-word.png "Create pie chart word example")

*Görsel alt metni, SEO için anahtar kelimeyi içerir.*

## Birden fazla seri ve kenar durumlarıyla başa çıkma

Temel örnek tek bir seri kullanır; bu, bir pasta grafiği için tipiktir. Birden fazla seri (ör. iki yılı karşılaştırma) göstermeniz gerekiyorsa şunları yapmalısınız:

1. Her ek seri için `chart.Series.Add()` çağırın.  
2. Her serinin aynı kategorileri kullandığından emin olun; aksi takdirde Aspose.Words bir `ArgumentException` fırlatır.  
3. İsteğe bağlı olarak, dilimleri ayırt etmek için `labels.ShowSeriesName = true` ayarlayın.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

Birden fazla seri mevcut olduğunda, grafik otomatik olarak **clustered pie** (diğer adıyla “pie of pies”) olarak render edilir. Etiketlerin okunabilirliğini doğrulamak için çıktıyı inceleyin.

## Yaygın tuzaklar ve nasıl önlenir

| Sorun | Sebep | Çözüm |
|---------|-------|-----|
| Etiketler dilimlerin üzerine biniyor | Küçük grafik alanı veya çok sayıda kategori | Grafik boyutlarını (`InsertChart(width, height)`) artırın veya `Position`'ı `InsideEnd` olarak değiştirin. |
| Yüzdeler 100 %'e ulaşmıyor | Veri yuvarlama hataları | `labels.ShowPercentage = true` kullanın (Aspose.Words otomatik olarak normalleştirir). |
| Grafik Word'de boş görünüyor | Lisans eksikliği veya değerlendirme süresi dolmuş | Belgeyi oluşturmadan önce geçerli bir Aspose.Words lisansı yüklendiğinden emin olun. |
| Yazı tipi renkleri Word temasıyla uyuşmuyor | Kod içinde özel yazı tipi ayarı | Özel yazı tipi ayarlarını kaldırın veya Word teması renkleriyle eşleştirin (`System.Drawing.Color.Black`). |

## Tam kaynak kodu (çalıştırılabilir)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Programı çalıştırdığınızda `ChartWithCustomLabels.docx` oluşturulur; bu dosya, **create pie chart word** örneğini içerir ve öğreticide listelenen tüm gereksinimleri karşılar.

## Sonuç

Artık Aspose.Words kullanarak C#'ta **create pie chart word** belgeleri oluşturmayı biliyorsunuz. Kılavuz, pasta grafiği ekleme, **add data labels pie**, **show percentage chart** ve **customize chart data labels** konularını kapsayarak profesyonel, veri odaklı bir Word dosyası üretmenizi sağladı.  

Buradan itibaren, mevcut paragraflara **insert pie chart** ekleme, **bar** veya **line** grafikler üretme, ya da farklı veri setleriyle toplu rapor oluşturma gibi ilgili konuları keşfedebilirsiniz. Çıktıyı kendi raporlama ihtiyaçlarınıza göre özelleştirmek için farklı etiket konumları, yazı tipi stilleri ve çoklu seri yapılandırmalarıyla deneyler yapın.

İyi grafikler!

## Bir Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}