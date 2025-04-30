---
"description": "Bu adım adım kılavuzla Aspose.Words for .NET kullanarak Word belgelerinde grafiklerin nasıl oluşturulacağını ve özelleştirileceğini öğrenin. Veri görselleştirme için mükemmeldir."
"linktitle": "Şekil Kullanarak Grafik Oluşturun ve Özelleştirin"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Şekil Kullanarak Grafik Oluşturun ve Özelleştirin"
"url": "/tr/net/programming-with-charts/create-chart-using-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Şekil Kullanarak Grafik Oluşturun ve Özelleştirin

## giriiş

Belgelerinizde grafikler oluşturmak ve özelleştirmek, günümüzün veri odaklı dünyasında önemli bir beceridir. Grafikler, karmaşık bilgileri daha kolay sindirilebilir hale getirerek verileri görselleştirmeye yardımcı olabilir. Aspose.Words for .NET, Word belgelerini programatik olarak oluşturmanıza ve düzenlemenize olanak tanıyan güçlü bir kütüphanedir. Bu eğitimde, Aspose.Words for .NET kullanarak bir çizgi grafiği oluşturma ve özelleştirme sürecini adım adım anlatacağız. Bu kılavuzun sonunda, profesyonel görünümlü grafikleri kolaylıkla oluşturabileceksiniz.

## Ön koşullar

Koda dalmadan önce aşağıdakilerin mevcut olduğundan emin olun:

- Aspose.Words for .NET Kütüphanesi: İndirebilirsiniz [Burada](https://releases.aspose.com/words/net/).
- Visual Studio: .NET'i destekleyen herhangi bir sürüm.
- Temel C# Bilgisi: C# temellerini anlamak, eğitimi takip etmenize yardımcı olacaktır.

## Ad Alanlarını İçe Aktar

Başlamak için gerekli ad alanlarını içe aktarmanız gerekir. Bu adım, .NET için Aspose.Words tarafından sağlanan sınıfları ve yöntemleri kullanmanıza olanak tanıdığı için önemlidir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Adım 1: Yeni Bir Belge Oluşturun

Öncelikle yeni bir Word belgesi oluşturmanız gerekiyor. Bu belge grafiğiniz için tuval görevi görecek.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 2: Bir Grafik Ekle

Daha sonra belgeye bir çizgi grafiği ekleyeceksiniz. `DocumentBuilder.InsertChart` Bu amaçla şu yöntem kullanılmaktadır.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

## Adım 3: Grafik Başlığını Özelleştirin

Grafik başlığını özelleştirmek, görüntülenen veriler için bağlam sağlamaya yardımcı olabilir. Aşağıdaki kodu kullanarak başlığı gösterebilir ve metnini ayarlayabilirsiniz:

```csharp
chart.Title.Show = true;
chart.Title.Text = "Line Chart Title";
chart.Title.Overlay = false;
// Başlık metni olarak null veya boş değer belirtildiğinde otomatik olarak oluşturulan başlığın gösterileceğini lütfen unutmayın.
```

## Adım 4: Efsanenin Konumunu Ayarlayın

Efsane, grafiğinizdeki farklı veri serilerini tanımlamanıza yardımcı olur. Pozisyonunu ve kaplama ayarlarını şu şekilde özelleştirebilirsiniz:

```csharp
chart.Legend.Position = LegendPosition.Left;
chart.Legend.Overlay = true;
```

## Adım 5: Belgeyi Kaydedin

Son olarak belgeyi kaydetmeniz gerekir. Bu adım tüm değişikliklerinizin dosyaya yazılmasını sağlar.

```csharp
doc.Save(dataDir + "WorkingWithCharts.CreateChartUsingShape.docx");
```

## Çözüm

Bu eğitimde, Aspose.Words for .NET kullanarak bir Word belgesinde çizgi grafiğinin nasıl oluşturulacağını ve özelleştirileceğini ele aldık. Adım adım kılavuzu izleyerek artık verilerinizi etkili bir şekilde ileten görsel olarak çekici grafikler oluşturabilirsiniz. Aspose.Words for .NET, grafikleri özel ihtiyaçlarınıza göre uyarlamanıza olanak tanıyan çok çeşitli özelleştirme seçenekleri sunar.

## SSS

### Aspose.Words for .NET'i diğer grafik türlerini oluşturmak için kullanabilir miyim?

Evet, Aspose.Words for .NET, çubuk grafikler, pasta grafikler ve daha fazlası dahil olmak üzere çeşitli grafik türlerini destekler. Belgeleri inceleyebilirsiniz [Burada](https://reference.aspose.com/words/net/) Daha detaylı bilgi için.

### Satın almadan önce Aspose.Words for .NET'i nasıl deneyebilirim?

Ücretsiz deneme sürümünü şuradan indirebilirsiniz: [Burada](https://releases.aspose.com/). Bu, satın alma işlemi yapmadan önce kütüphaneyi ve özelliklerini test etmenizi sağlar.

### Sorunla karşılaşırsam destek alabileceğim bir yol var mı?

Kesinlikle. Aspose topluluk forumları aracılığıyla desteğe erişebilirsiniz [Burada](https://forum.aspose.com/c/words/8)Topluluk ve Aspose personeli çok duyarlı.

### Aspose.Words for .NET için lisans nasıl satın alabilirim?

Lisansı doğrudan Aspose web sitesinden satın alabilirsiniz [Burada](https://purchase.aspose.com/buy)Farklı ihtiyaçlara uygun çeşitli lisanslama seçenekleri mevcuttur.

### Kısa süreli bir proje için geçici lisansa ihtiyacım olursa ne olur?

Aspose, talep edebileceğiniz geçici lisanslar sunar [Burada](https://purchase.aspose.com/temporary-license/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}