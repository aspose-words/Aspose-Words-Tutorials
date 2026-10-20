---
title: Aspose.Words for .NET kullanarak Word belgesine Custom Column Chart ekleyin.
weight: 310
limit:
description: Bir Word dosyası oluşturun, bir column chart ekleyin, verilerini özel bir diziyle değiştirin, bir başlık ekleyin ve kaydedin—hepsi Aspose.Words for .NET ile.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Bir Word dosyası oluşturun, bir column chart ekleyin, verilerini özel
    bir diziyle değiştirin, bir başlık ekleyin ve kaydedin—hepsi Aspose.Words for
    .NET ile.
  headline: Aspose.Words for .NET kullanarak Word belgesine Custom Column Chart ekleyin.
  type: TechArticle
- description: Bir Word dosyası oluşturun, bir column chart ekleyin, verilerini özel
    bir diziyle değiştirin, bir başlık ekleyin ve kaydedin—hepsi Aspose.Words for
    .NET ile.
  name: Aspose.Words for .NET kullanarak Word belgesine Custom Column Chart ekleyin.
  steps:
  - name: Yeni bir Document ve ona bağlı bir DocumentBuilder oluşturun.
    text: Yeni bir Document ve ona bağlı bir DocumentBuilder oluşturun.
  - name: Belgeye 432x252 puan boyutunda bir column chart ekleyin ve Chart nesnesini
      elde edin.
    text: Belgeye 432x252 puan boyutunda bir column chart ekleyin ve Chart nesnesini
      elde edin.
  - name: Grafikten otomatik olarak oluşturulan örnek seriyi kaldırın.
    text: Grafikten otomatik olarak oluşturulan örnek seriyi kaldırın.
  - name: Her seri için X‑eksen kategori etiketlerini ve lejand girişlerini tanımlayın.
    text: Her seri için X‑eksen kategori etiketlerini ve lejand girişlerini tanımlayın.
  - name: Her satır bir serinin değerlerini tutan iki boyutlu bir dizi oluşturun.
    text: Her satır bir serinin değerlerini tutan iki boyutlu bir dizi oluşturun.
  - name: Her seriyi döngüyle işleyin, matristen satır değerlerini çıkarın ve seriyi
      ilgili lejand girişi ve X‑eksen etiketleriyle grafiğe ekleyin.
    text: Her seriyi döngüyle işleyin, matristen satır değerlerini çıkarın ve seriyi
      ilgili lejand girişi ve X‑eksen etiketleriyle grafiğe ekleyin.
  - name: Grafik başlığı metnini 'Half‑Yearly Revenue' olarak ayarlayın ve görünür
      yapın.
    text: Grafik başlığı metnini 'Half‑Yearly Revenue' olarak ayarlayın ve görünür
      yapın.
  - name: Özel grafiği içeren belgeyi bir .docx dosyasına kaydedin.
    text: Özel grafiği içeren belgeyi bir .docx dosyasına kaydedin.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` değer dizisinin uzunluğunun X‑eksen etiket sayısına
      eşit olmasını bekler ve her **legend entry** için tam bir seri eklemelisiniz;
      uyumsuzluk çalışma zamanında bir `ArgumentException` fırlatır.'
    question: '`dataMatrix` içindeki satır veya sütunlar `legendEntries` veya `xLabels`
      uzunluklarıyla eşleşmezse ne olur?'
  - answer: Evet—`docBuilder.InsertChart` içindeki `ChartType.Column` ifadesini başka
      bir `ChartType` (ör. `ChartType.Line`) ile değiştirin; sonraki `Series.Add`
      çağrıları yeni grafiği aynı şekilde doldurur.
    question: Aynı veri doldurma mantığıyla, örneğin bir line chart gibi farklı bir
      grafik türü kullanabilir miyim?
  - answer: '`InsertChart` tarafından döndürülen `Shape` nesnesinin `Width` ve `Height`
      özelliklerini ayarlayın (ör. `chartContainer.Width = 500; chartContainer.Height
      = 300;`).'
    question: Grafik eklendikten sonra boyutunu nasıl değiştiririm?
  - answer: Her seriyi ekledikten sonra `chartObj.Series[i].HasDataLabel = true;`
      ayarlayın veya `chartObj.Series` üzerinde döngü yaparak `HasDataLabel` özelliğini
      etkinleştirip değerleri grafikte gösterin.
    question: Grafiğin her sütununda veri etiketlerini hızlıca göstermek mümkün mü?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Word belgesine Custom Column Chart ekleyin.
og_description: Bir grafiğin varsayılan verilerini kendi dizinizle değiştirin ve birkaç saniye içinde bir başlık ayarlayın.
og_image_alt: Aspose.Words for .NET kullanılarak oluşturulan özel bir column chart içeren Word belgesinin ekran görüntüsü.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak Word belgesine Custom Column Chart ekleyin.
Bu öğreticide, bir Word belgesi oluşturma, bir column chart ekleme, varsayılan verileri temizleme ve grafiği iki boyutlu bir diziden özel değerlerle doldurma—her satırı bir seriye, her sütunu bir kategoriye eşleştirerek—adım adım gösterilmektedir. Dosyayı kaydetmeden önce bir grafik başlığı eklemeyi de göreceksiniz. Word dosyanızda doğrudan tam özelleştirilmiş bir grafik üretmek için adımları izleyin.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: `dataMatrix` içindeki satır veya sütunlar `legendEntries` veya `xLabels` uzunluklarıyla eşleşmezse ne olur?**  
A: `Chart.Series.Add` değer dizisinin uzunluğunun X‑eksen etiket sayısına eşit olmasını bekler ve her **legend entry** için tam bir seri eklemelisiniz; uyumsuzluk çalışma zamanında bir `ArgumentException` fırlatır.

**Q: Aynı veri doldurma mantığıyla, örneğin bir line chart gibi farklı bir grafik türü kullanabilir miyim?**  
A: Evet—`docBuilder.InsertChart` içindeki `ChartType.Column` ifadesini başka bir `ChartType` (ör. `ChartType.Line`) ile değiştirin; sonraki `Series.Add` çağrıları yeni grafiği aynı şekilde doldurur.

**Q: Grafik eklendikten sonra boyutunu nasıl değiştiririm?**  
A: `InsertChart` tarafından döndürülen `Shape` nesnesinin `Width` ve `Height` özelliklerini ayarlayın (ör. `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: Grafiğin her sütununda veri etiketlerini hızlıca göstermek mümkün mü?**  
A: Her seriyi ekledikten sonra `chartObj.Series[i].HasDataLabel = true;` ayarlayın veya `chartObj.Series` üzerinde döngü yaparak `HasDataLabel` özelliğini etkinleştirip değerleri grafikte gösterin.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}