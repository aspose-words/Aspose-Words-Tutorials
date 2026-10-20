---
title: Aspose.Words for .NET kullanarak bir Word Document'ten Chart Series kaldırma
weight: 510
limit:
description: Aspose.Words for .NET ile bir Word belgesindeki sütun grafiğinden belirli bir veri serisini nasıl sileceğinizi öğrenin.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET ile bir Word belgesindeki sütun grafiğinden belirli
    bir veri serisini nasıl sileceğinizi öğrenin.
  headline: Aspose.Words for .NET kullanarak bir Word Document'ten Chart Series kaldırma
  type: TechArticle
- description: Aspose.Words for .NET ile bir Word belgesindeki sütun grafiğinden belirli
    bir veri serisini nasıl sileceğinizi öğrenin.
  name: Aspose.Words for .NET kullanarak bir Word Document'ten Chart Series kaldırma
  steps:
  - name: Yeni bir Word Document oluşturun ve ona bağlı bir DocumentBuilder oluşturun.
    text: Yeni bir Word Document oluşturun ve ona bağlı bir DocumentBuilder oluşturun.
  - name: 432×252 puan boyutunda bir sütun grafik ekleyin ve daha sonraki işlemler
      için Chart nesnesini alın.
    text: 432×252 puan boyutunda bir sütun grafik ekleyin ve daha sonraki işlemler
      için Chart nesnesini alın.
  - name: Kaldırılması gereken serinin sıfır‑tabanlı indeksini tanımlayın (ikinci
      seri).
    text: Kaldırılması gereken serinin sıfır‑tabanlı indeksini tanımlayın (ikinci
      seri).
  - name: İndeks geçerli ise, grafiğin Series koleksiyonunda RemoveAt metodunu çağırarak
      o seriyi silin.
    text: İndeks geçerli ise, grafiğin Series koleksiyonunda RemoveAt metodunu çağırarak
      o seriyi silin.
  - name: Güncellenen belgeyi bir .docx dosyasına kaydedin.
    text: Güncellenen belgeyi bir .docx dosyasına kaydedin.
  type: HowTo
- questions:
  - answer: '`if` kontrolü (`targetSeriesIdx < columnChart.Series.Count`) başarısız
      olur, bu yüzden `RemoveAt` hiç çağrılmaz ve grafik değişmeden kalır.'
    question: Grafikteki seri sayısına eşit bir indeks verirsem ne olur?
  - answer: Evet, `columnChart.Series.RemoveAt` işleminden sonra açıklama, kalan serileri
      yansıtacak şekilde yeniden oluşturulur, böylece kaldırılan giriş açıklamadan
      kaybolur.
    question: Bir seriyi kaldırmak, grafik açıklamasını otomatik olarak günceller
      mi?
  - answer: Kod, `Series` koleksiyonunu destekleyen herhangi bir grafik türü için
      çalışır; grafiği eklerken sadece `ChartType.Column` ifadesini istediğiniz tipe
      değiştirin.
    question: Aynı kodu bir çizgi veya pasta grafiğinden seri silmek için kullanabilir
      miyim?
  - answer: Sıfır serili bir grafik hâlâ geçerli bir `Shape` olup kaydedilir, ancak
      ortaya çıkan belgede boş görünür.
    question: Bir grafikteki tek seriyi kaldırırsam, grafik hâlâ doğru şekilde kaydedilir
      mi?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Bir Word Document'te Chart Series silme
og_description: Aspose.Words for .NET kullanarak bir Word grafiğinden veri serisini çıkarmak için adım adım rehber.
og_image_alt: Aspose.Words for .NET kullanarak bir Word belgesindeki sütun grafiğinden belirli bir veri serisini nasıl sileceğinizi gösteren rehber
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak bir Word Document'ten Chart Series kaldırma
Bu öğreticide bir Word belgesi nasıl oluşturulur, DocumentBuilder ile bir sütun grafik eklenir ve ardından ChartSeriesCollection.RemoveAt yöntemiyle o grafikten belirli bir veri serisi nasıl silinir gösterilir. Sonunda, istenmeyen serinin kaldırıldığı kaydedilmiş bir belgeye sahip olacaksınız ve .NET kodundan doğrudan grafik içeriği üzerinde hassas kontrol elde edeceksiniz.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: Grafikteki seri sayısına eşit bir indeks verirsem ne olur?**  
A: `if` kontrolü (`targetSeriesIdx < columnChart.Series.Count`) başarısız olur, bu yüzden `RemoveAt` hiç çağrılmaz ve grafik değişmeden kalır.

**Q: Bir seriyi kaldırmak, grafik açıklamasını otomatik olarak günceller mi?**  
A: Evet, `columnChart.Series.RemoveAt` işleminden sonra açıklama, kalan serileri yansıtacak şekilde yeniden oluşturulur, böylece kaldırılan giriş açıklamadan kaybolur.

**Q: Aynı kodu bir çizgi veya pasta grafiğinden seri silmek için kullanabilir miyim?**  
A: Kod, `Series` koleksiyonunu destekleyen herhangi bir grafik türü için çalışır; grafiği eklerken sadece `ChartType.Column` ifadesini istediğiniz tipe değiştirin.

**Q: Bir grafikteki tek seriyi kaldırırsam, grafik hâlâ doğru şekilde kaydedilir mi?**  
A: Sıfır serili bir grafik hâlâ geçerli bir `Shape` olup kaydedilir, ancak ortaya çıkan belgede boş görünür.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}