---
title: Word Belgesine Dağılım Grafiği Ekleme
linktitle: Word Belgesine Dağılım Grafiği Ekleme
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET ile Word'e dağılım grafiğinin nasıl ekleneceğini öğrenin. Belgelerinize görsel veri gösterimlerini entegre etmek için kolay adımlar.
weight: 10
url: /tr/net/programming-with-charts/insert-scatter-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesine Dağılım Grafiği Ekleme

## giriiş

Bu eğitimde, Word belgenize bir dağılım grafiği eklemek için Aspose.Words for .NET'i nasıl kullanacağınızı öğreneceksiniz. Dağılım grafikleri, iki değişkene dayalı olarak veri noktalarını etkili bir şekilde görüntüleyebilen, belgelerinizi daha ilgi çekici ve bilgilendirici hale getiren güçlü görsel araçlardır.

## Ön koşullar

Aspose.Words for .NET ile dağılım grafikleri oluşturmaya başlamadan önce, aşağıdaki ön koşullara sahip olduğunuzdan emin olun:

1.  Aspose.Words for .NET'in Kurulumu: Aspose.Words for .NET'i şu adresten indirin ve kurun:[Burada](https://releases.aspose.com/words/net/).
   
2. Temel C# Bilgisi: C# programlama dili ve .NET framework'üne aşinalık faydalı olacaktır.

## Ad Alanlarını İçe Aktar

Başlamak için, C# projenize gerekli ad alanlarını içe aktarmanız gerekir:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

Şimdi, Aspose.Words for .NET kullanarak Word belgenize dağılım grafiği ekleme sürecini parçalara ayıralım:

## Adım 1: Belgeyi ve Belge Oluşturucuyu Başlatın

 İlk olarak, yeni bir örneğini başlatın`Document` sınıf ve`DocumentBuilder` Belgenizi oluşturmaya başlamak için sınıfınıza gidin.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 2: Dağılım Grafiğini Ekleyin

 Kullanın`InsertChart` yöntemi`DocumentBuilder` Belgeye dağılım grafiği eklemek için sınıf.

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## Adım 3: Grafiğe Veri Serileri Ekleyin

Şimdi, dağılım grafiğinize veri serileri ekleyin. Bu örnek, belirli veri noktalarına sahip bir seri eklemeyi gösterir.

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## Adım 4: Belgeyi Kaydedin

 Son olarak, değiştirilen belgeyi istediğiniz konuma kaydetmek için şunu kullanın:`Save` yöntemi`Document` sınıf.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## Çözüm

Tebrikler! Aspose.Words for .NET kullanarak Word belgenize bir dağılım grafiği eklemeyi başarıyla öğrendiniz. Dağılım grafikleri, veri ilişkilerini görselleştirmek için mükemmel araçlardır ve Aspose.Words ile bunları belgelerinize zahmetsizce entegre ederek netliği ve anlayışı artırabilirsiniz.

## SSS

### Aspose.Words kullanarak dağılım grafiğinin görünümünü özelleştirebilir miyim?
Evet, Aspose.Words renkler, eksenler ve etiketler gibi grafik özelliklerinin kapsamlı bir şekilde özelleştirilmesine olanak tanır.

### Aspose.Words Microsoft Word'ün farklı sürümleriyle uyumlu mudur?
Aspose.Words, Microsoft Word'ün çeşitli sürümlerini destekleyerek platformlar arası uyumluluğu garanti altına alır.

### Aspose.Words diğer grafik türlerini destekliyor mu?
Evet, Aspose.Words çubuk grafikler, çizgi grafikler ve pasta grafikler dahil olmak üzere çok çeşitli grafik türlerini destekler.

### Dağılım grafiğindeki verileri program aracılığıyla dinamik olarak güncelleyebilir miyim?
Kesinlikle, Aspose.Words API çağrılarını kullanarak grafik verilerini dinamik olarak güncelleyebilirsiniz.

### Aspose.Words için daha fazla yardım veya desteği nereden alabilirim?
 Daha fazla yardım için şu adresi ziyaret edin:[Aspose.Words destek forumu](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
