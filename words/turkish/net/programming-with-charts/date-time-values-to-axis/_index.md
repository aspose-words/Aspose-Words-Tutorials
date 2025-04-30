---
"description": "Bu kapsamlı adım adım kılavuzda, Aspose.Words for .NET kullanarak bir grafiğin eksenine tarih ve saat değerlerinin nasıl ekleneceğini öğrenin."
"linktitle": "Bir Grafiğin Eksenine Tarih Saat Değerleri Ekleme"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Bir Grafiğin Eksenine Tarih Saat Değerleri Ekleme"
"url": "/tr/net/programming-with-charts/date-time-values-to-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Bir Grafiğin Eksenine Tarih Saat Değerleri Ekleme

## giriiş

Belgelerde grafik oluşturmak, verileri görselleştirmenin güçlü bir yolu olabilir. Zaman serisi verileriyle uğraşırken, bir grafiğin eksenine tarih ve saat değerleri eklemek netlik açısından çok önemlidir. Bu eğitimde, .NET için Aspose.Words kullanarak bir grafiğin eksenine tarih ve saat değerleri ekleme sürecini adım adım anlatacağız. Bu adım adım kılavuz, ortamınızı kurmanıza, kodu yazmanıza ve sürecin her bir bölümünü anlamanıza yardımcı olacaktır. Hadi başlayalım!

## Ön koşullar

Başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:

1. Visual Studio veya herhangi bir .NET IDE: .NET kodunuzu yazmak ve çalıştırmak için bir geliştirme ortamına ihtiyacınız var.
2. Aspose.Words for .NET: Aspose.Words for .NET kütüphanesi yüklü olmalıdır. Buradan indirebilirsiniz [Burada](https://releases.aspose.com/words/net/).
3. Temel C# bilgisi: Bu eğitimde C# programlama hakkında temel bir anlayışa sahip olduğunuz varsayılmaktadır.
4. Geçerli bir Aspose lisansı: Geçici bir lisansı şu adresten alabilirsiniz: [Burada](https://purchase.aspose.com/temporary-license/).

## Ad Alanlarını İçe Aktar

Başlamak için, projenize gerekli ad alanlarının içe aktarıldığından emin olun. Bu adım, Aspose.Words sınıflarına ve yöntemlerine erişim için çok önemlidir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Adım 1: Belge Dizininizi Ayarlayın

Öncelikle belgenizin kaydedileceği dizini tanımlamanız gerekir. Bu, dosyalarınızı düzenlemek ve kodunuzun doğru şekilde çalışmasını sağlamak için önemlidir.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Adım 2: Yeni bir Belge ve DocumentBuilder Oluşturun

Sonra, yeni bir örnek oluşturun `Document` sınıf ve bir `DocumentBuilder` nesne. Bu nesneler belgenizi oluşturmanıza ve düzenlemenize yardımcı olacaktır.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 3: Belgeye Bir Grafik Ekleyin

Şimdi, şunu kullanarak belgenize bir grafik ekleyin: `DocumentBuilder` nesne. Bu örnekte bir sütun grafiği kullanıyoruz, ancak başka türleri de seçebilirsiniz.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Adım 4: Mevcut Seriyi Temizle

Boş bir sayfa ile başladığınızdan emin olmak için grafikteki mevcut serileri temizleyin. Bu adım özel veriler için önemlidir.

```csharp
chart.Series.Clear();
```

## Adım 5: Seriye Tarih ve Saat Değerleri Ekleyin

Tarih ve saat değerlerinizi grafik serisine ekleyin. Bu adım, tarihler ve karşılık gelen değerler için diziler oluşturmayı içerir.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## Adım 6: X Eksenini Yapılandırın

X ekseni için ölçeklendirmeyi ve işaret işaretlerini ayarlayın. Bu, tarihlerinizin doğru ve uygun aralıklarla görüntülenmesini sağlar.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## Adım 7: Belgeyi Kaydedin

Son olarak, belgenizi belirtilen dizine kaydedin. Bu adım işlemi sonlandırır ve belgeniz artık X ekseninde tarih ve saat değerleri olan bir grafik içermelidir.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Çözüm

Bir belgedeki grafiğin eksenine tarih ve saat değerleri eklemek, Aspose.Words for .NET ile basit bir işlemdir. Bu eğitimde özetlenen adımları izleyerek, zaman serisi verilerini etkili bir şekilde görselleştiren net ve bilgilendirici grafikler oluşturabilirsiniz. İster raporlar, ister sunumlar veya ayrıntılı veri gösterimi gerektiren herhangi bir belge hazırlıyor olun, Aspose.Words başarılı olmak için ihtiyaç duyduğunuz araçları sağlar.

## SSS

### Aspose.Words for .NET ile diğer grafik türlerini kullanabilir miyim?

Evet, Aspose.Words çizgi, çubuk, pasta ve daha fazlası dahil olmak üzere çeşitli grafik türlerini destekler.

### Grafiklerimin görünümünü nasıl özelleştirebilirim?

Grafiğin özelliklerine erişip stilleri, renkleri ve daha fazlasını ayarlayarak görünümü özelleştirebilirsiniz.

### Bir grafiğe birden fazla seri eklemek mümkün müdür?

Kesinlikle! Grafiğinize birden fazla seriyi, `Series.Add` Yöntemi farklı verilerle birden fazla kez deneyin.

### Grafik verilerini dinamik olarak güncellemem gerekirse ne yapmalıyım?

İhtiyaçlarınıza göre seri ve eksen özelliklerini programlı olarak düzenleyerek grafik verilerini dinamik olarak güncelleyebilirsiniz.

### Aspose.Words for .NET için daha detaylı dokümanları nerede bulabilirim?

Daha detaylı dokümanları bulabilirsiniz [Burada](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}