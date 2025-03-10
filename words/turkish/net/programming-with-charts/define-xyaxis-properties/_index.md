---
title: Bir Grafikte XY Eksen Özelliklerini Tanımlayın
linktitle: Bir Grafikte XY Eksen Özelliklerini Tanımlayın
second_title: Aspose.Words Belge İşleme API'si
description: Bu adım adım kılavuzla .NET için Aspose.Words'ü kullanarak bir grafikte XY ekseni özelliklerini nasıl tanımlayacağınızı öğrenin. .NET geliştiricileri için mükemmeldir.
weight: 10
url: /tr/net/programming-with-charts/define-xyaxis-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bir Grafikte XY Eksen Özelliklerini Tanımlayın

## giriiş

Grafikler, verileri görselleştirmek için güçlü bir araçtır. Dinamik grafiklerle profesyonel belgeler oluşturmanız gerektiğinde, Aspose.Words for .NET paha biçilmez bir kütüphanedir. Bu makale, Aspose.Words for .NET kullanarak bir grafikte XY ekseni özelliklerini tanımlama sürecinde size yol gösterecek ve her adımı açıklık ve anlaşılırlık kolaylığı sağlamak için parçalara ayıracaktır.

## Ön koşullar

Kodlamaya başlamadan önce, yerine getirmeniz gereken birkaç ön koşul vardır:

1. Aspose.Words for .NET: Aspose.Words for .NET kitaplığına sahip olduğunuzdan emin olun.[buradan indirin](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio gibi entegre bir geliştirme ortamına (IDE) ihtiyacınız var.
3. .NET Framework: Geliştirme ortamınızın .NET geliştirmeye uygun olduğundan emin olun.
4. Temel C# Bilgisi: Bu kılavuz, C# programlama konusunda temel bir anlayışa sahip olduğunuzu varsayar.

## Ad Alanlarını İçe Aktar

Başlamak için, projenize gerekli ad alanlarını içe aktarmanız gerekir. Bu, belgeler ve grafikler oluşturmak ve düzenlemek için gereken tüm sınıflara ve yöntemlere erişiminizin olmasını sağlar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Süreci basit adımlara böleceğiz ve her adım, bir grafikte XY ekseninin özelliklerini tanımlamanın belirli bir bölümüne odaklanacak.

## Adım 1: Belgeyi ve Belge Oluşturucuyu Başlatın

 İlk olarak yeni bir belge başlatmanız ve`DocumentBuilder` nesne.`DocumentBuilder` belgeye içerik eklemeye yardımcı olur.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 2: Bir Grafik Ekle

Sonra, belgeye bir grafik ekleyeceksiniz. Bu örnekte, bir Alan grafiği kullanacağız. Grafiğin boyutlarını gerektiği gibi özelleştirebilirsiniz.

```csharp
// Tablo ekle
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## Adım 3: Varsayılan Seriyi Temizle ve Özel Veri Ekle

Varsayılan olarak, grafikte bazı önceden tanımlanmış seriler olacaktır. Bunları temizleyeceğiz ve özel veri serilerimizi ekleyeceğiz.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## Adım 4: X Eksen Özelliklerini Tanımlayın

Şimdi, X ekseni için özellikleri tanımlamanın zamanı geldi. Bu, kategori türünü ayarlamayı, eksen geçişini özelleştirmeyi ve işaret işaretlerini ve etiketleri ayarlamayı içerir.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; // ekseninin (yüzlerce) gösterge birimleriyle ölçülmüştür.
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## Adım 5: Y Eksen Özelliklerini Tanımlayın

Benzer şekilde, Y ekseni için özellikleri ayarlayacaksınız. Bu, işaret etiketi konumunu, büyük ve küçük birimleri, görüntüleme birimini ve ölçeklemeyi ayarlamayı içerir.

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## Adım 6: Belgeyi Kaydedin

Son olarak, belgeyi belirtilen dizine kaydedin. Bu, özelleştirilmiş grafikle Word belgesini oluşturacaktır.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Çözüm

Aspose.Words for .NET kullanarak Word belgelerinde grafikler oluşturmak ve özelleştirmek, ilgili adımları anladığınızda basittir. Bu kılavuz, bir grafikte XY ekseni özelliklerini tanımlama sürecinde, belgeyi başlatmaktan son ürünü kaydetmeye kadar size yol göstermiştir. Bu becerilerle, belgelerinizi geliştiren ayrıntılı, profesyonel görünümlü grafikler oluşturabilirsiniz.

## SSS

### Aspose.Words for .NET ile hangi tür grafikler oluşturabilirim?
Alan, Çubuk, Çizgi, Pasta gibi çeşitli grafik türleri oluşturabilirsiniz.

### Aspose.Words for .NET'i nasıl yüklerim?
 Aspose.Words for .NET'i şu adresten indirebilirsiniz:[Burada](https://releases.aspose.com/words/net/)ve verilen kurulum talimatlarını izleyin.

### Grafiklerimin görünümünü özelleştirebilir miyim?
Evet, Aspose.Words for .NET, renkler, yazı tipleri ve eksen özellikleri de dahil olmak üzere grafiklerin kapsamlı bir şekilde özelleştirilmesine olanak tanır.

### Aspose.Words for .NET için ücretsiz deneme sürümü mevcut mu?
 Evet, ücretsiz deneme alabilirsiniz[Burada](https://releases.aspose.com/).

### Daha fazla öğretici ve dokümanı nerede bulabilirim?
 Daha fazla öğretici ve ayrıntılı dokümanı şu adreste bulabilirsiniz:[Aspose.Words for .NET dokümantasyon sayfası](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
