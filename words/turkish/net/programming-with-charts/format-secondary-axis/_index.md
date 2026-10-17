---
title: Aspose.Words for .NET kullanarak Word line chart'larında Secondary X‑Axis'i biçimlendirin ve Display Units'i bin olarak ayarlayın.
weight: 710
limit:
description: Aspose.Words for .NET ile bir Word line chart oluşturun, ikincil X‑axis ekleyin, display unit'ını bin olarak ayarlayın ve özel bir sayısal format uygulayın.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET ile bir Word line chart oluşturun, ikincil X‑axis
    ekleyin, display unit'ını bin olarak ayarlayın ve özel bir sayısal format uygulayın.
  headline: Aspose.Words for .NET kullanarak Word line chart'larında Secondary X‑Axis'i
    biçimlendirin ve Display Units'i bin olarak ayarlayın.
  type: TechArticle
- description: Aspose.Words for .NET ile bir Word line chart oluşturun, ikincil X‑axis
    ekleyin, display unit'ını bin olarak ayarlayın ve özel bir sayısal format uygulayın.
  name: Aspose.Words for .NET kullanarak Word line chart'larında Secondary X‑Axis'i
    biçimlendirin ve Display Units'i bin olarak ayarlayın.
  steps:
  - name: Yeni bir Document ve bir DocumentBuilder oluşturun ve Word dosyasını oluşturmaya
      başlayın.
    text: Yeni bir Document ve bir DocumentBuilder oluşturun ve Word dosyasını oluşturmaya
      başlayın.
  - name: Belgeye 500×300 boyutunda bir line chart ekleyin ve Chart nesnesini elde
      edin.
    text: Belgeye 500×300 boyutunda bir line chart ekleyin ve Chart nesnesini elde
      edin.
  - name: Aspose.Words'ün otomatik olarak eklediği varsayılan demo serisini kaldırın.
    text: Aspose.Words'ün otomatik olarak eklediği varsayılan demo serisini kaldırın.
  - name: X‑axis için kullanılacak kategori etiketlerinin bir dizisini tanımlayın.
    text: X‑axis için kullanılacak kategori etiketlerinin bir dizisini tanımlayın.
  - name: Etiketleri ve değerleri kullanarak "Main Data" adlı birincil veri serisini
      ekleyin.
    text: Etiketleri ve değerleri kullanarak "Main Data" adlı birincil veri serisini
      ekleyin.
  - name: Line tipinde bir secondary series group oluşturun ve onu secondary axis
      group'a atayın.
    text: Line tipinde bir secondary series group oluşturun ve onu secondary axis
      group'a atayın.
  - name: İkincil X‑axis'in display unit'ını bin olarak ayarlayın, böylece değerler
      K olarak gösterilir.
    text: İkincil X‑axis'in display unit'ını bin olarak ayarlayın, böylece değerler
      K olarak gösterilir.
  - name: İkincil X‑axis'in tick etiketlerine "#,##0.0" özel sayısal formatını uygulayın.
    text: İkincil X‑axis'in tick etiketlerine "#,##0.0" özel sayısal formatını uygulayın.
  - name: İsteğe bağlı olarak secondary group'a yardımcı bir veri serisi ekleyin.
    text: İsteğe bağlı olarak secondary group'a yardımcı bir veri serisi ekleyin.
  - name: Belgeyi .docx dosyası olarak kaydedin.
    text: Belgeyi .docx dosyası olarak kaydedin.
  type: HowTo
- questions:
  - answer: Hayır – `AxisX` ayarları `ChartSeriesGroup`'a aittir, bu yüzden `secondaryGroup.AxisX.DisplayUnit.Unit`
      ve `secondaryGroup.AxisX.NumberFormat.FormatCode` değerlerini serileri eklemeden
      önce ya da sonra ayarlayabilirsiniz; yapılandırma her iki durumda da grup eksenine
      uygulanır.
    question: İkincil X‑axis üzerinde display unit ve number format ayarlamadan önce
      secondary series eklemem gerekiyor mu?
  - answer: Evet – herhangi bir `AxisBuiltInUnit` değerini atayabilirsiniz, örneğin
      `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` ifadesi
      eksen değerlerini bin yerine milyon olarak gösterir.
    question: İkincil X‑axis için milyonlar gibi farklı bir built‑in unit kullanabilir
      miyim?
  - answer: Hayır – format kodu yalnızca değiştirdiğiniz eksene (`secondaryGroup.AxisX.NumberFormat.FormatCode`)
      uygulanır, bu yüzden birincil X‑axis varsayılan biçimini korur.
    question: Özel format "#,##0.0" birincil X‑axis etiketlerini etkiler mi?
  - answer: Grafik, eklediğiniz serilerin yanı sıra varsayılan demo serisini de içerecek
      ve bu ekstra çizgilere ve uyumsuz kategorilere yol açabilir; koleksiyonu temizlemek
      yalnızca istediğiniz verilerin görünmesini sağlar.
    question: '`lineChart.Series.Clear();` ile demo serisini temizlemeyi unutsam ne
      olur?'
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Secondary X‑Axis'i biçimlendirin ve Units'i bin olarak ayarlayın.
og_description: Bir Word line chart'a secondary X‑axis ekleyin ve etiketlerini bin olarak özel bir desenle biçimlendirin.
og_image_alt: Aspose.Words for .NET kullanarak bir Word line chart'a secondary X‑axis eklemeyi ve etiketlerini bin birimlerde gösterecek şekilde biçimlendirmeyi gösteren rehber.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak Word line chart'larında Secondary X‑Axis'i biçimlendirin ve Display Units'i bin olarak ayarlayın.
Bu öğretici, içinde bir line chart bulunan bir Word belgesi oluşturmayı, ikincil X‑axis eklemeyi ve bu ekseni bin değerler gösterecek şekilde yapılandırmayı adım adım gösterir. Ayrıca ikincil eksen etiketlerine özel bir sayısal format uygulamayı öğrenerek verinin nasıl sunulduğu üzerinde hassas kontrol elde edersiniz. Word raporlarınızdaki çoklu eksenli grafiklerin okunabilirliğini artırmak için adımları izleyin.

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

**Q: İkincil X‑axis üzerinde display unit ve number format ayarlamadan önce secondary series eklemem gerekiyor mu?**  
A: Hayır – `AxisX` ayarları `ChartSeriesGroup`'a aittir, bu yüzden `secondaryGroup.AxisX.DisplayUnit.Unit` ve `secondaryGroup.AxisX.NumberFormat.FormatCode` değerlerini serileri eklemeden önce ya da sonra ayarlayabilirsiniz; yapılandırma her iki durumda da grup eksenine uygulanır.

**Q: İkincil X‑axis için milyonlar gibi farklı bir built‑in unit kullanabilir miyim?**  
A: Evet – herhangi bir `AxisBuiltInUnit` değerini atayabilirsiniz, örneğin `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` ifadesi eksen değerlerini bin yerine milyon olarak gösterir.

**Q: Özel format "#,##0.0" birincil X‑axis etiketlerini etkiler mi?**  
A: Hayır – format kodu yalnızca değiştirdiğiniz eksene (`secondaryGroup.AxisX.NumberFormat.FormatCode`) uygulanır, bu yüzden birincil X‑axis varsayılan biçimini korur.

**Q: `lineChart.Series.Clear();` ile demo serisini temizlemeyi unutsam ne olur?**  
A: Grafik, eklediğiniz serilerin yanı sıra varsayılan demo serisini de içerecek ve bu ekstra çizgilere ve uyumsuz kategorilere yol açabilir; koleksiyonu temizlemek yalnızca istediğiniz verilerin görünmesini sağlar.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}