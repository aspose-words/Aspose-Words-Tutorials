---
title: Word Belgesinde Grafik Eksenini Gizle
linktitle: Word Belgesinde Grafik Eksenini Gizle
second_title: Aspose.Words Belge İşleme API'si
description: Ayrıntılı, adım adım eğitimimiz ile Aspose.Words for .NET'i kullanarak Word belgesinde grafik eksenini nasıl gizleyeceğinizi öğrenin.
weight: 10
url: /tr/net/programming-with-charts/hide-chart-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesinde Grafik Eksenini Gizle

## giriiş

Dinamik ve görsel olarak çekici Word belgeleri oluşturmak genellikle çizelgeler ve grafikler eklemeyi içerir. Bu tür senaryolardan biri daha temiz bir sunum için çizelge eksenini gizlemeyi gerektirebilir. Aspose.Words for .NET bu tür görevler için kapsamlı ve kullanımı kolay bir API sağlar. Bu eğitim, Aspose.Words for .NET kullanarak bir Word belgesinde bir çizelge eksenini gizleme adımlarında size rehberlik edecektir.

## Ön koşullar

Eğitime başlamadan önce aşağıdaki ön koşullara sahip olduğunuzdan emin olun:

-  Aspose.Words for .NET: Buradan indirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio gibi .NET geliştirmeyi destekleyen herhangi bir IDE.
- .NET Framework: Bilgisayarınızda .NET Framework'ün yüklü olduğundan emin olun.
- Temel C# Bilgisi: C# programlama diline aşinalık faydalı olacaktır.

## Ad Alanlarını İçe Aktar

Aspose.Words for .NET ile çalışmaya başlamak için projenize gerekli ad alanlarını içe aktarmanız gerekir. Bunu şu şekilde yapabilirsiniz:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Süreci basit ve takip edilmesi kolay adımlara bölelim.

## Adım 1: Belgeyi ve Belge Oluşturucuyu Başlatın

İlk adım yeni bir Word belgesi oluşturmayı ve DocumentBuilder nesnesini başlatmayı içerir.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Bu adımda, belgenin kaydedileceği yolu tanımlarız. Daha sonra yeni bir`Document` nesne ve bir`DocumentBuilder` Belgemizi oluşturmaya başlama nesnesi.

## Adım 2: Bir Grafik Ekle

 Daha sonra, belgeye bir grafik ekleyeceğiz.`DocumentBuilder` nesne.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

 Burada, belirtilen boyutlara sahip bir sütun grafiği ekliyoruz.`InsertChart` yöntem bir döndürür`Shape` grafiği içeren nesne.

## Adım 3: Mevcut Seriyi Temizle

Grafiğe yeni veri eklemeden önce mevcut serileri temizlememiz gerekiyor.

```csharp
chart.Series.Clear();
```

Bu adım, grafikteki varsayılan verilerin kaldırılmasını ve daha sonra ekleyeceğimiz yeni verilere yer açılmasını sağlar.

## Adım 4: Seri Verilerini Ekleyin

Şimdi kendi veri serimizi grafiğe ekleyelim.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

Bu adımda, "Aspose Serisi 1" başlıklı bir seri ekliyoruz ve buna karşılık gelen kategoriler ve değerler ekleniyor.

## Adım 5: Y Eksenini Gizle

 Grafiğin Y eksenini gizlemek için, basitçe şunu ayarlarız:`Hidden` Y ekseninin özelliği`true`.

```csharp
chart.AxisY.Hidden = true;
```

Bu kod satırı Y eksenini gizleyerek grafikte görünmez hale getirir.

## Adım 6: Belgeyi Kaydedin

Son olarak belgeyi belirtilen dizine kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithCharts.HideChartAxis.docx");
```

Bu komut, grafik içeren Word belgesini belirtilen yola kaydeder.

## Çözüm

Tebrikler! Aspose.Words for .NET kullanarak bir Word belgesinde bir grafik eksenini nasıl gizleyeceğinizi başarıyla öğrendiniz. Bu güçlü kütüphane, Word belgelerini programatik olarak yönetmeyi kolaylaştırır. Bu adımları izleyerek, minimum çabayla özelleştirilmiş ve profesyonel görünümlü belgeler oluşturabilirsiniz.

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, .NET uygulamaları içerisinde Word belgeleri oluşturmak, düzenlemek, dönüştürmek ve düzenlemek için güçlü bir API'dir.

### Bir grafikte hem X hem de Y eksenlerini gizleyebilir miyim?
 Evet, her iki ekseni de ayarlayarak gizleyebilirsiniz.`Hidden` ikisinin de mülkü`AxisX` Ve`AxisY` ile`true`.

### Aspose.Words for .NET için ücretsiz deneme sürümü mevcut mu?
 Evet, ücretsiz deneme alabilirsiniz[Burada](https://releases.aspose.com/).

### Daha fazla dokümanı nerede bulabilirim?
 Aspose.Words for .NET hakkında ayrıntılı belgeler bulabilirsiniz[Burada](https://reference.aspose.com/words/net/).

### Aspose.Words for .NET desteğini nasıl alabilirim?
 Aspose topluluğundan destek alabilirsiniz[Burada](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
