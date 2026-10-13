---
title: Aspose.Words for .NET kullanarak bir Word grafiğinde İkincil Y Eksenini Para Birimi Olarak Biçimlendirin
weight: 710
limit:
description: Aspose.Words for .NET ile bir Word çizgi grafiğinde ikincil Y eksenini para birimi olarak eklemeyi ve biçimlendirmeyi öğrenin.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET ile bir Word çizgi grafiğinde ikincil Y eksenini
    para birimi olarak eklemeyi ve biçimlendirmeyi öğrenin.
  headline: Aspose.Words for .NET kullanarak bir Word grafiğinde İkincil Y Eksenini
    Para Birimi Olarak Biçimlendirin
  type: TechArticle
- description: Aspose.Words for .NET ile bir Word çizgi grafiğinde ikincil Y eksenini
    para birimi olarak eklemeyi ve biçimlendirmeyi öğrenin.
  name: Aspose.Words for .NET kullanarak bir Word grafiğinde İkincil Y Eksenini Para
    Birimi Olarak Biçimlendirin
  steps:
  - name: Yeni boş bir Word belgesi ve onu düzenlemek için bir DocumentBuilder oluşturun.
    text: Yeni boş bir Word belgesi ve onu düzenlemek için bir DocumentBuilder oluşturun.
  - name: Belgeye 450×250 puan boyutunda bir çizgi grafik ekleyin ve onun Chart nesnesini
      alın.
    text: Belgeye 450×250 puan boyutunda bir çizgi grafik ekleyin ve onun Chart nesnesini
      alın.
  - name: Aspose'un yeni bir grafiğe eklediği varsayılan yer tutucu serisini kaldırın.
    text: Aspose'un yeni bir grafiğe eklediği varsayılan yer tutucu serisini kaldırın.
  - name: Çeyrek etiketlerini tanımlayın ve grafiğe örnek değerlerle bir birincil
      veri serisi ekleyin.
    text: Çeyrek etiketlerini tanımlayın ve grafiğe örnek değerlerle bir birincil
      veri serisi ekleyin.
  - name: Line türünde bir ikincil seri grubu oluşturun ve bunu ikincil eksen grubuna
      atayın.
    text: Line türünde bir ikincil seri grubu oluşturun ve bunu ikincil eksen grubuna
      atayın.
  - name: İkincil X eksenini gizleyin, böylece sadece ikincil Y ekseni görünür.
    text: İkincil X eksenini gizleyin, böylece sadece ikincil Y ekseni görünür.
  - name: İkincil Y ekseni başlığını gösterin ve metnini \"Sales (USD)\" olarak ayarlayın.
    text: İkincil Y ekseni başlığını gösterin ve metnini \"Sales (USD)\" olarak ayarlayın.
  - name: İkincil Y ekseninin sayı biçimini iki ondalık basamaklı bir para birimi
      desenine ayarlayın ve kaynağın biçimlendirmesinden bağlantısını kaldırın.
    text: İkincil Y ekseninin sayı biçimini iki ondalık basamaklı bir para birimi
      desenine ayarlayın ve kaynağın biçimlendirmesinden bağlantısını kaldırın.
  - name: İkincil gruba yardımcı bir seri ekleyin; bu seri ikincil Y eksenine karşı
      çizilecek verileri sağlar.
    text: İkincil gruba yardımcı bir seri ekleyin; bu seri ikincil Y eksenine karşı
      çizilecek verileri sağlar.
  - name: Tamamlanan belgeyi geçerli dizinde ProfitChart.docx adlı bir dosyaya kaydedin.
    text: Tamamlanan belgeyi geçerli dizinde ProfitChart.docx adlı bir dosyaya kaydedin.
  type: HowTo
- questions:
  - answer: Grafik, Aspose.Words'un eklediği varsayılan yer tutucu serisini tutar;
      bu yüzden özelleştirilmiş \"Main Series\" istenmeyen veri noktalarıyla birlikte
      görünür.
    question: '`lineChart.Series.Clear()` çağrısını atlamam durumunda ne olur?'
  - answer: '`secondarySeriesGroup.AxisX.Hidden = false;` olarak ayarlayın (veya `true`
      olarak ayarlayan satırı basitçe atlayın).'
    question: İkincil X eksenini gizlemek yerine nasıl gösterebilirim?
  - answer: Evet – format dizesini değiştirin, örneğin euro için `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = \\"€#,##0.00\\";` ya da bölgenize uygun bir desen ayarlayın.
    question: İkincil Y ekseni için farklı bir para birimi simgesi veya biçimi kullanabilir
      miyim?
  - answer: '`IsLinkedToSource` true olduğunda eksen, temel veri kaynağından sayı
      biçimini devralır ve herhangi bir özel `FormatCode`''u geçersiz kılar; false
      olarak ayarlamak, grafiğin belirttiğiniz biçimi kullanmasını zorlar.'
    question: Özel bir sayı biçimi uygularken neden `IsLinkedToSource = false` ayarlamam
      gerekiyor?
  - answer: Evet, eksenin hangi tarafta çizileceğini kontrol etmek için `secondarySeriesGroup.AxisY.Position
      = AxisPosition.Left;` (veya varsayılan için `Right`) atayın.
    question: İkincil Y eksenini grafiğin sol tarafına taşımak mümkün mü?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Bir Grafiğin İkincil Eksenini Para Birimi Olarak Biçimlendirin
og_description: Bir Word çizgi grafiğine ikincil Y ekseni eklemeyi ve iki ondalık basamakla para birimi şeklinde stil vermeyi öğrenin.
og_image_alt: Aspose.Words for .NET kullanarak ikincil Y ekseni para birimi olarak biçimlendirilmiş bir Word çizgi grafiğini gösteren ekran görüntüsü
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak bir Word grafiğinde İkincil Y Eksenini Para Birimi Olarak Biçimlendirin
Bu öğreticide, Aspose.Words for .NET kullanarak bir Word belgesi oluşturmayı, bir çizgi grafik eklemeyi, ikincil Y ekseni eklemeyi, bu ekseni iki ondalık basamaklı para birimi olarak biçimlendirmeyi ve ona ikincil bir veri serisi bağlamayı göreceksiniz. İkincil ekseni para birimi olarak biçimlendirmek, finansal verileri birincil seriyle birlikte net bir şekilde sunmanızı sağlar. Oluşturulan belgede grafiğin doğrudan nasıl oluşturulduğunu görmek için adım adım kodu izleyin.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: `lineChart.Series.Clear()` çağrısını atlamam durumunda ne olur?**  
A: Grafik, Aspose.Words'un eklediği varsayılan yer tutucu serisini tutar; bu yüzden özelleştirilmiş \"Main Series\" istenmeyen veri noktalarıyla birlikte görünür.

**Q: İkincil X eksenini gizlemek yerine nasıl gösterebilirim?**  
A: `secondarySeriesGroup.AxisX.Hidden = false;` olarak ayarlayın (veya `true` olarak ayarlayan satırı basitçe atlayın).

**Q: İkincil Y ekseni için farklı bir para birimi simgesi veya biçimi kullanabilir miyim?**  
A: Evet – format dizesini değiştirin, örneğin euro için `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = \\"€#,##0.00\\";` ya da bölgenize uygun bir desen ayarlayın.

**Q: Özel bir sayı biçimi uygularken neden `IsLinkedToSource = false` ayarlamam gerekiyor?**  
A: `IsLinkedToSource` true olduğunda eksen, temel veri kaynağından sayı biçimini devralır ve herhangi bir özel `FormatCode`'u geçersiz kılar; false olarak ayarlamak, grafiğin belirttiğiniz biçimi kullanmasını zorlar.

**Q: İkincil Y eksenini grafiğin sol tarafına taşımak mümkün mü?**  
A: Evet, eksenin hangi tarafta çizileceğini kontrol etmek için `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (veya varsayılan için `Right`) atayın.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}