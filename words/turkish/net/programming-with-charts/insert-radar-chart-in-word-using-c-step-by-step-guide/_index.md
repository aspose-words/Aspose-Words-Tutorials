---
category: general
date: 2026-09-14
description: C# ile Word’e radar grafiği ekleyin. Grafik başlığını nasıl ayarlayacağınızı,
  birden fazla seriyi nasıl ekleyeceğinizi ve sadece birkaç satırda programatik olarak
  grafiği nasıl oluşturacağınızı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert radar chart
- set chart title
- create radar chart word
- multiple series radar chart
- create chart programmatically
language: tr
lastmod: 2026-09-14
og_description: C# kullanarak Word'e radar grafiği ekleyin. Bu öğreticide grafik başlığını
  ayarlama, birden fazla seri ekleme ve grafiği programlı olarak oluşturma yöntemleri
  gösterilmektedir.
og_image_alt: Screenshot of a Word document displaying a radar chart with sales data
og_title: C# ile Word'e radar grafiği ekleme – hızlı programlama rehberi
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Insert radar chart in Word with C#. Learn how to set chart title, add
    multiple series, and create the chart programmatically in just a few lines.
  headline: Insert radar chart in Word using C# – step‑by‑step guide
  type: TechArticle
tags:
- radar chart
- C#
- Aspose.Words
title: C# kullanarak Word'e radar grafiği ekleme – adım adım rehber
url: /tr/net/programming-with-charts/insert-radar-chart-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# kullanarak Word'e radar grafiği ekleme – adım adım kılavuz

Word belgesine **radar grafiği eklemeniz** gerekiyorsa, bu kılavuz C# ile programlı olarak nasıl yapılacağını gösterir. Ayrıca **grafik başlığını ayarlamayı**, **çoklu seri radar grafiği eklemeyi** ve dosyayı IDE'nizden çıkmadan kaydetmeyi öğreneceksiniz.

Bu öğretici, proje kurulumundan son `doc.Save` çağrısına kadar her şeyi kapsar, böylece tam örneği kopyalayıp yapıştırarak hemen çalıştırabilirsiniz. Harici belge aramaya gerek yok.

## Önkoşullar

* .NET 6 (veya daha yeni bir sürüm) yüklü.
* Geçerli bir Aspose.Words for .NET lisansı (veya geçici bir değerlendirme anahtarı).
* Visual Studio 2022 veya tercih ettiğiniz herhangi bir C# IDE.

> **Pro ipucu:** Ücretsiz deneme sürümünü kullanıyorsanız, değerlendirme filigranını önlemek için ilk `Document` oluşturulmadan önce lisansı ayarlamayı unutmayın.

## Adım 1: Word belgesine radar grafiği ekleme

İlk işlem, yeni bir `Document` ve bir `DocumentBuilder` oluşturmaktır. Builder, belgenin içeriğine erişim sağlar ve **radar grafiğini** tam olarak ihtiyacınız olan yere yerleştirmenize olanak tanır.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank Word document.
Document doc = new Document();

// DocumentBuilder provides methods to insert content.
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a radar (radial) chart at the current cursor position.
Chart chart = builder.InsertChart(ChartType.Radar);
```

*Bu adımın önemi:* `InsertChart` bir grafik nesnesi oluşturur ve belge kaydedilmeden önce tamamen yapılandırabilirsiniz. `ChartType.Radar` kullanmak, Word'e bir sütun ya da çizgi grafiği yerine radyal bir grafik oluşturmasını söyler.

## Adım 2: Grafik başlığını ve eksen derecelendirmelerini ayarlama

Başlıksız bir grafik kafa karıştırıcı olabilir. Burada **grafik başlığını** “Sales Radar” olarak ayarlıyoruz ve her iki eksende de derecelendirmeleri etkinleştiriyoruz (Aspose.Words 24.9 ve sonrası için kullanılabilir).

```csharp
// Give the chart a meaningful title.
chart.Title.Text = "Sales Radar";

// Enable graduations (grid lines) on both X and Y axes.
chart.AxisX.HasGraduations = true;
chart.AxisY.HasGraduations = true;
```

*Bu adımın önemi:* Başlık, okuyuculara bağlam sağlar ve derecelendirmeler, her veri noktasının ölçek üzerindeki konumunu göstererek okunabilirliği artırır.

## Adım 3: Radar grafiği için çoklu seri oluşturma

**Çoklu seri radar grafiği**, farklı dönemleri yan yana karşılaştırmanıza olanak tanır. Aşağıda iki seri ekliyoruz—Q1 ve Q2—her biri üç veri noktasına sahip.

```csharp
// Series 1: Q1 data.
chart.Series.Add(
    "Q1",                                 // Series name
    new[] { "Jan", "Feb", "Mar" },        // Category labels
    new[] { 10, 20, 30 }                  // Values
);

// Series 2: Q2 data.
chart.Series.Add(
    "Q2",
    new[] { "Jan", "Feb", "Mar" },
    new[] { 15, 25, 35 }
);
```

*Bu adımın önemi:* Çoklu seri eklemek, aynı radar üzerinde veri setlerini karşılaştırmanın nasıl yapılacağını gösterir; bu, satış, performans veya anket sonuçları için yaygın bir gereksinimdir.

## Adım 4: Word belgesini programlı olarak kaydetme

Son olarak, **grafiği programlı olarak oluşturur** ve belgeyi diske kaydedersiniz. `Save` yöntemi, Microsoft Word'de açılabilen bir `.docx` dosyası yazar.

```csharp
// Define the output path. Adjust the directory as needed.
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "RadialGraduations.docx"
);

// Save the document containing the radar chart.
doc.Save(outputPath);
```

`RadialGraduations.docx` dosyasını açtığınızda, “Sales Radar” başlıklı ve iki seri (Q1 ve Q2) Ocak‑Mart aylarına göre çizilmiş bir radar grafiği göreceksiniz.

### Beklenen çıktı

![Radar chart in Word](https://example.com/radar-chart.png){: .align-center alt="İki veri serisi içeren radar grafiği gösteren Word belgesi"}

Ekran görüntüsü (veya gerçek dosya), grafiğin doğru şekilde eklendiğini, başlıklandırıldığını ve doldurulduğunu doğrular.

## Tam, çalıştırılabilir örnek

Her şeyi bir araya getirerek, derleyip çalıştırabileceğiniz bağımsız bir program burada:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a radar chart.
        Chart chart = builder.InsertChart(ChartType.Radar);

        // 3. Set chart title and enable axis graduations.
        chart.Title.Text = "Sales Radar";
        chart.AxisX.HasGraduations = true;
        chart.AxisY.HasGraduations = true;

        // 4. Add two data series.
        chart.Series.Add("Q1", new[] { "Jan", "Feb", "Mar" }, new[] { 10, 20, 30 });
        chart.Series.Add("Q2", new[] { "Jan", "Feb", "Mar" }, new[] { 15, 25, 35 });

        // 5. Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialGraduations.docx"
        );
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Programı çalıştırın, oluşturulan dosyayı açın ve **radar grafiği ekleme** işleminin başarılı olduğunu doğrulayın.

## Yaygın sorular ve uç durumlar

| Soru | Cevap |
|------|-------|
| **Eklemeden sonra grafik tipini değiştirebilir miyim?** | Evet. `InsertChart` işleminden sonra, `chart.Type`'a yeni bir `ChartType` atayabilirsiniz. Ancak, grafiği baştan doğru tipte oluşturmak daha verimlidir. |
| **İki seriden fazla ihtiyacım olursa ne yapmalıyım?** | `chart.Series.Add` metodunu her ek seri için çağırın. Grafik, göstergeyi ve renkleri otomatik olarak ayarlayacaktır. |
| **Renkleri veya işaretçileri nasıl özelleştiririm?** | Dolgu renkleri için `chart.Series[i].Format.Fill.ForeColor`, işaretçi stilleri için `chart.Series[i].Marker` kullanın. |
| **API .NET Framework ile uyumlu mu?** | Aynı kod .NET Framework 4.7+ ile çalışır; sadece uygun Aspose.Words DLL'ini referans gösterin. |
| **Daha eski bir Aspose.Words sürümü kullanıyorsam ne olur?** | Derecelendirmeler (`HasGraduations`) 24.9'da tanıtıldı. Daha eski sürümler için, `chart.AxisX.MajorGridLines` ve `chart.AxisY.MajorGridLines` kullanarak ızgara çizgilerini manuel ekleyebilirsiniz. |

## Sonuç

Artık C# kullanarak Word belgesine **radar grafiği eklemeyi**, **grafik başlığını ayarlamayı**, **çoklu seri radar grafiği eklemeyi** ve **grafiği programlı olarak oluşturmayı** biliyorsunuz. Bu uçtan uca çözüm, raporlamayı, gösterge panellerini veya kategorilerin görsel karşılaştırmasının gerektiği herhangi bir senaryoyu otomatikleştirmenizi sağlar.

Sonra, **grafik renklerini özelleştirme**, **grafikleri resim olarak dışa aktarma** veya **grafikleri PDF dosyalarına gömme** gibi ilgili konuları keşfedin. Farklı veri setleriyle deneme yaparak radar görselleştirmenin nasıl uyduğunu görün.

Kodlamanın tadını çıkarın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Word'de Sütun Grafiği Ekleme (Aspose.Words for .NET Kullanarak)](/words/english/net/working-with-charts/insert-column-chart/)
- [Word'de Balon Grafiği Ekleme (Aspose.Words for .NET Kullanarak)](/words/english/net/working-with-charts/insert-bubble-chart/)
- [Word Belgesine Alan Grafiği Ekleme | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}