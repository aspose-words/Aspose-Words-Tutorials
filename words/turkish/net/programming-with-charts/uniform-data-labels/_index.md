---
title: Aspose.Words for .NET kullanarak bir sütun grafikte Tekdüze Veri Etiketleri ayarlayın
weight: 110
limit:
description: Aspose.Words for .NET ile bir Word sütun grafiği oluşturmayı ve tüm serilere tekdüze veri etiketi yazı tipi boyutu ve rengi uygulamayı öğrenin.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET ile bir Word sütun grafiği oluşturmayı ve tüm
    serilere tekdüze veri etiketi yazı tipi boyutu ve rengi uygulamayı öğrenin.
  headline: Aspose.Words for .NET kullanarak bir sütun grafikte Tekdüze Veri Etiketleri
    ayarlayın
  type: TechArticle
- description: Aspose.Words for .NET ile bir Word sütun grafiği oluşturmayı ve tüm
    serilere tekdüze veri etiketi yazı tipi boyutu ve rengi uygulamayı öğrenin.
  name: Aspose.Words for .NET kullanarak bir sütun grafikte Tekdüze Veri Etiketleri
    ayarlayın
  steps:
  - name: Yeni boş bir Word belgesi ve onu düzenlemek için bir DocumentBuilder oluşturun.
    text: Yeni boş bir Word belgesi ve onu düzenlemek için bir DocumentBuilder oluşturun.
  - name: Belgeye 500×300 boyutlarında bir sütun grafik ekleyin ve onun Chart nesnesini
      elde edin.
    text: Belgeye 500×300 boyutlarında bir sütun grafik ekleyin ve onun Chart nesnesini
      elde edin.
  - name: Aspose.Words'ün yeni bir grafiğe eklediği varsayılan örnek seriyi kaldırın.
    text: Aspose.Words'ün yeni bir grafiğe eklediği varsayılan örnek seriyi kaldırın.
  - name: Kategori etiketlerini tanımlayın ve grafiğe iki veri serisi (Item Alpha
      ve Item Beta) ve değerlerini ekleyin.
    text: Kategori etiketlerini tanımlayın ve grafiğe iki veri serisi (Item Alpha
      ve Item Beta) ve değerlerini ekleyin.
  - name: Tüm veri etiketlerine uygulanacak temel yazı tipi boyutu ve rengini ayarlayın.
    text: Tüm veri etiketlerine uygulanacak temel yazı tipi boyutu ve rengini ayarlayın.
  - name: Her seri için veri etiketlerini etkinleştirin, sayısal değeri gösterin ve
      önceden tanımlanmış yazı tipi boyutu ve rengini uygulayın.
    text: Her seri için veri etiketlerini etkinleştirin, sayısal değeri gösterin ve
      önceden tanımlanmış yazı tipi boyutu ve rengini uygulayın.
  - name: Belgeyi bir .docx dosyasına kaydedin.
    text: Belgeyi bir .docx dosyasına kaydedin.
  type: HowTo
- questions:
  - answer: '`InsertChart` varsayılan bir örnek seri içeren bir grafik oluşturur;
      bunu temizlemek, o yer tutucuyu kaldırır ve grafik yalnızca eklediğiniz serileri
      (`Item Alpha` ve `Item Beta`) gösterir.'
    question: '`chart.Series.Clear()` metodunu kendi serilerimi eklemeden önce neden
      çağırmam gerekiyor?'
  - answer: '`Color.White` ifadesini herhangi bir `System.Drawing.Color` değeriyle,
      örneğin `Color.Black` veya `Color.FromArgb(255, 30, 144, 255)` ile değiştirin;
      yeni renk, döngü içinde `series.DataLabels.Font.Color` aracılığıyla uygulanır.'
    question: Veri etiketi rengini beyazın dışındaki bir renge nasıl değiştirebilirim?
  - answer: Veri etiketleri gizlenecek, bu yüzden uyguladığınız yazı tipi ayarları
      görünmez olacaktır; etiketlerin (ve stilinin) görünmesi için `HasDataLabels`
      değerini `true` olarak tutmanız gerekir.
    question: Yazı tipi boyutu ve rengini yapılandırdıktan sonra `series.HasDataLabels
      = false` ayarlarsam ne olur?
  - answer: Evet—her `ChartSeries` kendi `DataLabels` nesnesine sahiptir, bu yüzden
      ilk döngüden sonra eklenen herhangi bir seriye de `HasDataLabels`, `ShowValue`
      ve yazı tipi özellikleri ayarlanmalıdır; bunu ya tekrar döngü yaparak ya da
      stil ayarlarını bir yardımcı metoda çıkararak yapabilirsiniz.
    question: Kodda daha sonra başka bir seri eklersem seriler üzerinden tekrar döngü
      yapmam gerekir mi?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Word grafiğine Tekdüze Veri Etiketleri Uygulayın
og_description: Aspose.Words for .NET ile her grafik etiketine aynı yazı tipi boyutu ve rengi hızlıca verin.
og_image_alt: Aspose.Words for .NET kullanılarak oluşturulan, tüm veri etiketlerinin aynı yazı tipi boyutu ve rengi paylaştığı bir sütun grafik içeren Word belgesini gösteren rehber.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak bir sütun grafikte Tekdüze Veri Etiketleri ayarlayın
Bu öğreticide, Aspose.Words for .NET ile bir Word belgesi oluşturma, bir sütun grafik ekleme ve özel veri serileri ekleme gösterilmektedir. Ardından, grafikteki her serinin aynı etiketleri göstermesi için varsayılan veri etiketi yazı tipi boyutu ve rengini tanımlama gösterilir. Tek bir stil uygulayarak tüm grafik boyunca tutarlı bir görsel görünüm sağlarsınız.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: `chart.Series.Clear()` metodunu kendi serilerimi eklemeden önce neden çağırmam gerekiyor?**  
A: `InsertChart` varsayılan bir örnek seri içeren bir grafik oluşturur; bunu temizlemek, o yer tutucuyu kaldırır ve grafik yalnızca eklediğiniz serileri (`Item Alpha` ve `Item Beta`) gösterir.

**Q: Veri etiketi rengini beyazın dışındaki bir renge nasıl değiştirebilirim?**  
A: `Color.White` ifadesini herhangi bir `System.Drawing.Color` değeriyle, örneğin `Color.Black` veya `Color.FromArgb(255, 30, 144, 255)` ile değiştirin; yeni renk, döngü içinde `series.DataLabels.Font.Color` aracılığıyla uygulanır.

**Q: Yazı tipi boyutu ve rengini yapılandırdıktan sonra `series.HasDataLabels = false` ayarlarsam ne olur?**  
A: Veri etiketleri gizlenecek, bu yüzden uyguladığınız yazı tipi ayarları görünmez olacaktır; etiketlerin (ve stilinin) görünmesi için `HasDataLabels` değerini `true` olarak tutmanız gerekir.

**Q: Kodda daha sonra başka bir seri eklersem seriler üzerinden tekrar döngü yapmam gerekir mi?**  
A: Evet—her `ChartSeries` kendi `DataLabels` nesnesine sahiptir, bu yüzden ilk döngüden sonra eklenen herhangi bir seriye de `HasDataLabels`, `ShowValue` ve yazı tipi özellikleri ayarlanmalıdır; bunu ya tekrar döngü yaparak ya da stil ayarlarını bir yardımcı metoda çıkararak yapabilirsiniz.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}