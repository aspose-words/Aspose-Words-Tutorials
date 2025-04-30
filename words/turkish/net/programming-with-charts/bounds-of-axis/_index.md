---
"description": "Aspose.Words for .NET kullanarak bir grafikteki eksenin sınırlarını nasıl ayarlayacağınızı ve eksende görüntülenen değer aralığını nasıl kontrol edeceğinizi öğrenin."
"linktitle": "Bir Grafikteki Eksen Sınırları"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Bir Grafikteki Eksen Sınırları"
"url": "/tr/net/programming-with-charts/bounds-of-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Bir Grafikteki Eksen Sınırları

## giriiş

.NET'te grafiklerle profesyonel belgeler mi oluşturmak istiyorsunuz? Doğru yerdesiniz! Bu kılavuz, bir grafikteki eksenin sınırlarını belirlemek için .NET için Aspose.Words'ü kullanma sürecinde size yol gösterecek. Kütüphaneye yeni olsanız bile kolayca takip edebilmeniz için her adımı parçalara ayıracağız. Hadi başlayalım!

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

- Aspose.Words for .NET: Şunları yapabilirsiniz: [indirmek](https://releases.aspose.com/words/net/) en son sürümü kullanın veya [ücretsiz deneme](https://releases.aspose.com/).
- .NET Framework: Sisteminizde .NET'in yüklü olduğundan emin olun.
- IDE: Visual Studio benzeri bir geliştirme ortamı.

Her şey hazır olduğunda bir sonraki adımlara geçebiliriz.

## Ad Alanlarını İçe Aktar

Başlamak için gerekli ad alanlarını içe aktarmanız gerekir. Bunlar Aspose.Words kütüphanesine ve grafik özelliklerine erişmenizi sağlayacaktır.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Adım 1: Belge Dizininizi Ayarlayın

İlk önce, belgenizin kaydedileceği dizini ayarlamanız gerekir. Bu basit bir adımdır ancak dosyalarınızı düzenlemek için çok önemlidir.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Adım 2: Yeni Bir Belge Oluşturun

Sonra, yeni bir belge nesnesi oluşturun. Bu belge, grafiğiniz için kapsayıcı görevi görecektir.

```csharp
Document doc = new Document();
```

## Adım 3: Belge Oluşturucuyu Başlatın

DocumentBuilder sınıfı, belgeleri oluşturmanın hızlı ve kolay bir yolunu sağlar. Bunu belgenizle başlatın.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 4: Bir Grafik Ekle

Şimdi, belgenize bir grafik ekleme zamanı. Bu örnekte, bir Sütun grafiği kullanacağız.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Adım 5: Mevcut Seriyi Temizle

Temiz bir sayfa ile başladığınızdan emin olmak için, grafikteki mevcut serileri temizleyin.

```csharp
chart.Series.Clear();
```

## Adım 6: Grafiğe Veri Ekleme

Burada, grafiğe veri ekliyoruz. Bu, seri adını ve veri noktalarını belirtmeyi içerir.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

## Adım 7: Eksen Sınırlarını Ayarlayın

Y ekseninin sınırlarını belirlemek, grafiğinizin doğru şekilde ölçeklenmesini sağlar.

```csharp
chart.AxisY.Scaling.Minimum = new AxisBound(0);
chart.AxisY.Scaling.Maximum = new AxisBound(6);
```

## Adım 8: Belgeyi Kaydedin

Son olarak belgenizi belirtilen dizine kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithCharts.BoundsOfAxis.docx");
```

Ve işte bu kadar! Aspose.Words for .NET kullanarak bir grafik içeren bir belgeyi başarıyla oluşturdunuz. 

## Çözüm

.NET için Aspose.Words'ü kullanarak belgelerinizde kolayca grafikler oluşturabilir ve düzenleyebilirsiniz. Bu adım adım kılavuz, bir grafikteki eksenin sınırlarını nasıl ayarlayacağınızı göstererek veri sunumunuzu daha kesin ve profesyonel hale getirir. İster raporlar, ister sunumlar veya başka bir belge oluşturun, Aspose.Words ihtiyacınız olan araçları sağlar.

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, .NET çerçevesini kullanarak Word belgelerini programlı bir şekilde oluşturmanıza, değiştirmenize ve dönüştürmenize olanak tanıyan bir kütüphanedir.

### Aspose.Words for .NET'i nasıl kurarım?
Buradan indirebilirsiniz [Burada](https://releases.aspose.com/words/net/) ve verilen kurulum talimatlarını izleyin.

### Aspose.Words'ü ücretsiz kullanabilir miyim?
Evet, kullanabilirsiniz [ücretsiz deneme](https://releases.aspose.com/) veya bir tane al [geçici lisans](https://purchase.aspose.com/temporary-license/).

### Aspose.Words for .NET için dokümanları nerede bulabilirim?
Ayrıntılı dokümantasyon mevcuttur [Burada](https://reference.aspose.com/words/net/).

### Aspose.Words için nasıl destek alabilirim?
Ziyaret edebilirsiniz [destek forumu](https://forum.aspose.com/c/words/8) yardım için.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}