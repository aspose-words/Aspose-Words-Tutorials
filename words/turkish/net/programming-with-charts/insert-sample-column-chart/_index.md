---
title: Aspose.Words for .NET kullanarak Word belgesine Örnek Sütun Grafiği ekleyin
weight: 410
limit:
description: Word dosyası oluşturma, DocumentBuilder.InsertChart ile varsayılan bir sütun grafiği ekleme, grafik nesnesine erişme ve .docx olarak kaydetme adım adım rehberi.
keywords: [Aspose.Words for .NET, insert column chart, documentbuilder inserchart, create word document with chart, save chart to docx, chart object Aspose.Words]
url: /net/programming-with-charts/insert-sample-column-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Word dosyası oluşturma, DocumentBuilder.InsertChart ile varsayılan
    bir sütun grafiği ekleme, grafik nesnesine erişme ve .docx olarak kaydetme adım
    adım rehberi.
  headline: Aspose.Words for .NET kullanarak Word belgesine Örnek Sütun Grafiği ekleyin
  type: TechArticle
- description: Word dosyası oluşturma, DocumentBuilder.InsertChart ile varsayılan
    bir sütun grafiği ekleme, grafik nesnesine erişme ve .docx olarak kaydetme adım
    adım rehberi.
  name: Aspose.Words for .NET kullanarak Word belgesine Örnek Sütun Grafiği ekleyin
  steps:
  - name: Boş bir Word belgesi ve onu düzenlemek için bir DocumentBuilder oluşturun.
    text: Boş bir Word belgesi ve onu düzenlemek için bir DocumentBuilder oluşturun.
  - name: Belgeye 432 × 252 nokta boyutunda bir sütun grafiği ekleyin.
    text: Belgeye 432 × 252 nokta boyutunda bir sütun grafiği ekleyin.
  - name: Gerekirse daha fazla özelleştirme için eklenen şekilden Chart nesnesini
      alın.
    text: Gerekirse daha fazla özelleştirme için eklenen şekilden Chart nesnesini
      alın.
  - name: Şimdi eklenmiş sütun grafiğini içeren belgeyi .docx dosyasına kaydedin.
    text: Şimdi eklenmiş sütun grafiğini içeren belgeyi .docx dosyasına kaydedin.
  type: HowTo
- questions:
  - answer: Boyutlar nokta (point) cinsinden belirtilir (1 point = 1/72 inç), yani
      432 pt ≈ 6 inç ve 252 pt ≈ 3,5 inç.
    question: InsertChart'teki genişlik ve yükseklik parametreleri (432, 252) için
      hangi birimler kullanılır?
  - answer: Evet—eklemeden sonra `chartContainer.Chart` aracılığıyla Chart nesnesine
      sahipsiniz; örnek verileri değiştirmek için SeriesCollection, Categories ve
      Values'ı değiştirebilirsiniz.
    question: InsertChart'ı varsayılan veri kümesiyle çağırdıktan sonra grafik verilerini
      değiştirebilir miyim?
  - answer: '`InsertChart` çağrısında `ChartType.Column` ifadesini `ChartType.Line`
      gibi başka bir enum değeriyle değiştirmeniz yeterlidir.'
    question: Aynı kodu kullanarak farklı bir grafik türü (ör. çizgi grafiği) eklemek
      mümkün mü?
  - answer: Hayır—`docBuilder.InsertChart` grafiği otomatik olarak bir `Shape` içine
      gömer; `wordDoc.Save` çağrısı grafiği belgeyle birlikte yazar.
    question: Belgeyi kaydetmeden önce grafiği gömmek için ek bir yöntem çağırmam
      gerekiyor mu?
  type: FAQPage
images:
- /net/programming-with-charts/insert-sample-column-chart/og-image.png
og_title: Bir Word belgesine Örnek Sütun Grafiği ekleyin
og_description: Aspose.Words for .NET ile birkaç dakika içinde bir Word belgesine hazır bir sütun grafiği ekleyin.
og_image_alt: Aspose.Words for .NET kullanılarak eklenmiş örnek bir sütun grafiği içeren Word belgesinin ekran görüntüsü
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak Word belgesine Örnek Sütun Grafiği ekleyin
Bu öğreticide, yeni bir Word belgesi oluşturma ve DocumentBuilder.InsertChart ile varsayılan bir sütun grafiği ekleme adımlarını izlersiniz. Ayrıca gömülü Chart nesnesini nasıl alıp daha fazla manipülasyon yapabileceğinizi göreceksiniz. Son olarak, rehber belgeyi .docx dosyası olarak nasıl kaydedeceğinizi gösterir.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-sample-column-chart" >}}


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

**Q: InsertChart'teki genişlik ve yükseklik parametreleri (432, 252) için hangi birimler kullanılır?**  
A: Boyutlar nokta (point) cinsinden belirtilir (1 point = 1/72 inç), yani 432 pt ≈ 6 inç ve 252 pt ≈ 3,5 inç.

**Q: InsertChart'ı varsayılan veri kümesiyle çağırdıktan sonra grafik verilerini değiştirebilir miyim?**  
A: Evet—eklemeden sonra `chartContainer.Chart` aracılığıyla Chart nesnesine sahipsiniz; örnek verileri değiştirmek için SeriesCollection, Categories ve Values'ı değiştirebilirsiniz.

**Q: Aynı kodu kullanarak farklı bir grafik türü (ör. çizgi grafiği) eklemek mümkün mü?**  
A: `InsertChart` çağrısında `ChartType.Column` ifadesini `ChartType.Line` gibi başka bir enum değeriyle değiştirmeniz yeterlidir.

**Q: Belgeyi kaydetmeden önce grafiği gömmek için ek bir yöntem çağırmam gerekiyor mu?**  
A: Hayır—`docBuilder.InsertChart` grafiği otomatik olarak bir `Shape` içine gömer; `wordDoc.Save` çağrısı grafiği belgeyle birlikte yazar.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}