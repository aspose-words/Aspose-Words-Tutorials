---
category: general
date: 2026-07-19
description: Aspose.Words for C# kullanarak pasta grafik dilimini patlatın. Pasta
  dilimini nasıl patlatacağınızı, halka deliği boyutunu nasıl ayarlayacağınızı ve
  grafik veri noktalarını hızlıca nasıl değiştireceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: tr
lastmod: 2026-07-19
og_description: Aspose.Words for C# ile pasta grafik dilimini patlatın. Bu kılavuz,
  pasta dilimini nasıl patlatacağınızı, halka deliği boyutunu nasıl ayarlayacağınızı
  ve grafik veri noktalarını verimli bir şekilde nasıl değiştireceğinizi gösterir.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: C#'da Pasta Grafik Dilimini Patlatma – Aspose.Words Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: C# ve Aspose.Words ile Pasta Grafik Dilimini Patlatma – Tam Kılavuz
url: /tr/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Aspose.Words Kullanarak Pasta Grafik Dilimini Patlatma – Tam Kılavuz

C# kullanarak bir Word belgesinde **pasta dilimini patlatma** nasıl yapılacağını hiç merak ettiniz mi? Tek başınıza değilsiniz. Satış sunumu hazırlıyor ya da anket sonuçlarını görselleştiriyor olun, patlatılmış bir dilim gözleri tam istediğiniz yere çeker. Bu öğreticide tüm süreci adım adım göstereceğiz—belgeyi yükleme, grafiği çekme, ilk dilimi patlatma, bir doughnut deliğini ayarlama ve hatta grafik veri noktalarını değiştirme.

Ayrıca arıyor olabileceğiniz ikincil kavramları da ekleyeceğiz: **pasta dilimini nasıl patlatılır**, **doughnut deliği boyutunu ayarlama**, ve **grafik veri noktalarını değiştirme**. Gereksiz ayrıntı yok, sadece eksiksiz, kopyala‑yapıştır hazır bir çözüm.

---

## Gereksinimler

- **Aspose.Words for .NET** (2026‑07‑19 tarihine kadar olan en yeni sürüm). NuGet üzerinden `Install-Package Aspose.Words` komutuyla edinebilirsiniz.
- **.NET 6+** projesi (veya hâlâ eski sürüm kullanıyorsanız .NET Framework 4.7.2+).
- İçinde zaten bir pasta veya doughnut grafiği bulunan bir Word dosyası (`Chart.docx`). Eğer yoksa, Word'de hızlıca bir grafik oluşturup kaydedin.

Hepsi bu—ekstra kütüphane yok, COM interop yok, sadece saf yönetilen kod.

---

## Pasta Grafik Dilimini Patlatma – Adım‑Adım Uygulama

Aşağıda görevi küçük adımlara bölüyoruz. Her bölüm net bir başlık, bir kod parçacığı ve *neden* yaptığımızı açıklayan kısa bir açıklamaya sahip.

### Adım 1: Aspose.Words'ı Yükleyin ve Referans Gösterin

İlk olarak, Aspose.Words paketini projenize ekleyin. Package Manager Console'da:

```powershell
Install-Package Aspose.Words
```

> **Pro tip:** Visual Studio'nun yerleşik NuGet UI'sini kullanıyorsanız, “Aspose.Words” aratın ve Install'a tıklayın. Bu, en yeni hata düzeltmelerini ve grafikleri kutudan çıkar çıkmaz kullanabilme yeteneğini sağlar.

### Adım 2: Grafiği İçeren Word Belgesini Yükleyin

Değiştirmek istediğiniz grafiği içeren `.docx` dosyasına işaret eden bir `Document` nesnesine ihtiyacımız var.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Neden önemli:** `Document`, Aspose.Words'taki her işlemin giriş noktasıdır. Grafikleri erken kontrol ederek, daha sonra bir dilimi patlatmaya çalıştığınızda null referans hatasından kaçınmış oluruz.

### Adım 3: İlk Grafik Düğümünü Alın

Çoğu örnek tek bir grafik varsayar, bu yüzden ilkini alacağız. Birden fazla grafiğiniz varsa, indeksi buna göre ayarlayın.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Not:** Bir grafik varlığını doğruladıktan sonra `Chart` tipine dönüşüm güvenlidir. Bu nesne, serilere, veri noktalarına ve grafik‑türü‑özel ayarlara erişim sağlar.

### Adım 4: Pasta Grafiğinin İlk Dilimini Patlatın

Şimdi gösterinin yıldızı—**pasta dilimini nasıl patlatılır**. İlk veri noktasının `Exploded` özelliğini ayarlayacağız.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Neden işe yarar:** `Exploded`, Word'e o dilimi merkezden uzaklaştırmasını söyler ve klasik “patlatılmış pasta” etkisini oluşturur. Özellik boolean tipindedir, bu yüzden `true` olarak ayarlamak yeterlidir.

### Adım 5: Doughnut Deliği Boyutunu Ayarlayın (Eğer Doughnut Grafiği ise)

Grafiğiniz bir doughnut ise, **doughnut deliği boyutunu ayarlamak** isteyebilirsiniz. Deliğin boyutu, grafiğin yarıçapının bir yüzdesidir.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **Sayı ne anlama geliyor:** `30` değeri, iç çemberin toplam yarıçapın %30'unu kaplayacağı ve dış halkanın daha kalın kalacağı anlamına gelir.

### Adım 6: Grafik Veri Noktalarını Değiştirin (İsteğe Bağlı)

Bazen **grafik veri noktalarını değiştirmek** gerekir—belki temel sayıları güncellediniz ve görselin bunu yansıtmasını istiyorsunuz.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Bunu neden yaparsınız:** Bir veri noktasının değerini değiştirmek, dilim yüzdelerini otomatik olarak yeniden hesaplar ve Word'de manuel düzenleme yapmadan grafiği doğru tutar.

### Adım 7: Değiştirilen Belgeyi Kaydedin

Son olarak, değişiklikleri diske yazın. Orijinali üzerine yazabilir veya yeni bir dosya oluşturabilirsiniz—size kalmış.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **İpucu:** `SaveFormat.Docx` kullanarak açıkça belirtebilirsiniz, ancak `Save(string)` dosya uzantısından formatı otomatik algılar.

---

## Beklenen Sonuç

Microsoft Word'de `FormattedChart.docx` dosyasını açtığınızda şunları görmelisiniz:

- Pasta grafiğinin ilk dilimi **dışarı doğru patlatılmış**.
- Grafik bir doughnut ise, merkezi delik artık yarıçapın **%30**'unu kaplıyor.
- Değiştirilen veri noktaları, ayarladığınız yeni değerleri yansıtıyor.

Aşağıda patlatılmış dilimin nasıl göründüğünün bir taslağı (sadece illüstrasyon amaçlı) yer almaktadır.

![Aspose.Words ile C#'ta oluşturulmuş patlatılmış pasta grafik dilimi](exploded-pie-slice.png)

*Alt metin:* **patlatılmış pasta grafik dilimi** Word belgesinde çekilmiş bir segmenti gösterir.

---

## Yaygın Sorular & Kenar Durumlar

**Grafik bir pasta veya doughnut değilse ne olur?**  
Kod, `Exploded` veya `HoleSize` uygulamadan önce `ChartType`'ı kontrol eder. Çubuk, çizgi veya alan grafiklerinde bu özellikler bulunmadığından, mantık bunları güvenle atlar.

**Birden fazla dilimi patlatabilir miyim?**  
Kesinlikle. `chart.PieChartData.Series[0].DataPoints` üzerinden döngü yaparak istediğiniz indekslerde `Exploded = true` ayarlayabilirsiniz.

**Kültüre özgü sayı formatları konusunda endişelenmeli miyim?**  
Aspose.Words sayısal değerleri locale bağımsız olarak double tipinde saklar, bu yüzden virgül ve nokta sorunlarından etkilenmezsiniz.

**Üstbilgi/altbilgi içinde gömülü grafikler ne olur?**  
Tüm grafikleri almak için `doc.GetChildNodes(NodeType.Chart, true)` kullanın, ardından her düğümün `ParentNode`'unu inceleyerek nerede bulunduğunu kontrol edin. Aynı patlatma mantığı uygulanır.

---

## Sonuç

Artık Aspose.Words ile C#'ta **pasta grafik dilimini patlatma** için sağlam, kopyala‑yapıştır hazır bir çözümünüz var. Tüm iş akışını kapsadık—belgeyi yüklemek, grafiği almak, dilimi patlatmak, **doughnut deliği boyutunu ayarlamak**, **grafik veri noktalarını değiştirmek** ve son olarak dosyayı kaydetmek.

Denemekten çekinmeyin: farklı bir dilimi patlatmayı deneyin, delik boyutunu %45'e ayarlayın veya birden fazla veri noktasını aynı anda güncelleyin. Aspose.Words API bu ayarlamaları zahmetsiz kılar ve değişiklikler Word dosyasını açtığınızda anında görünür.

---

### Sıradaki Adımlar?

- **Patlatılmış dilimi biçimlendirin** (dolgu rengini, kenarlığı değiştirin veya veri etiketi ekleyin). “Aspose.Words chart formatting” için arama yapın.
- **Birden fazla belgeyi toplu işleme** otomatikleştirin—bir klasörü döngüyle işleyin, dilimleri patlatın ve yeni sürümler kaydedin.
- **Aspose.Slides** ile birleştirin, aynı grafiği bir PowerPoint sunumunda kullanmanız gerekiyorsa.

Grafik manipülasyonu hakkında daha fazla sorunuz mu var, ya da diğer grafik türlerine daha derinlemesine dalmak mı istiyorsunuz? Aşağıya yorum bırakın, iyi kodlamalar!

---

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}