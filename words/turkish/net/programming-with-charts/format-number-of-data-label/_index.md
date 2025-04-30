---
"description": "Bu adım adım kılavuzla Aspose.Words for .NET kullanarak grafiklerdeki veri etiketlerini nasıl biçimlendireceğinizi öğrenin. Word belgelerinizi zahmetsizce geliştirin."
"linktitle": "Bir Grafikteki Veri Etiketinin Sayısını Biçimlendir"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Bir Grafikteki Veri Etiketinin Sayısını Biçimlendir"
"url": "/tr/net/programming-with-charts/format-number-of-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Bir Grafikteki Veri Etiketinin Sayısını Biçimlendir

## giriiş

İlgi çekici ve bilgilendirici belgeler oluşturmak genellikle iyi biçimlendirilmiş veri etiketlerine sahip grafikler eklemeyi içerir. Word belgelerinizi gelişmiş grafiklerle geliştirmek isteyen bir .NET geliştiricisiyseniz, Aspose.Words for .NET bunu başarmanıza yardımcı olacak harika bir kütüphanedir. Bu eğitim, Aspose.Words for .NET kullanarak bir grafikteki sayı etiketlerini biçimlendirme sürecini adım adım anlatacaktır.

## Ön koşullar

Koda dalmadan önce, yerine getirmeniz gereken birkaç ön koşul vardır:

- Aspose.Words for .NET: Aspose.Words for .NET kütüphanesinin yüklü olduğundan emin olun. Henüz yüklemediyseniz, [buradan indirin](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: .NET geliştirme ortamını kurmuş olmanız gerekir. Visual Studio şiddetle tavsiye edilir.
- Temel C# Bilgisi: Bu eğitim C# kodunu yazmayı ve anlamayı içerdiğinden, C# programlamaya aşinalık şarttır.
- Geçici Lisans: Aspose.Words'ü herhangi bir sınırlama olmaksızın kullanmak için, [geçici lisans](https://purchase.aspose.com/temporary-license/).

Şimdi, bir grafikteki sayı etiketlerinin biçimlendirilmesinin adım adım sürecine bir göz atalım.

## Ad Alanlarını İçe Aktar

İlk önce, Aspose.Words for .NET ile çalışmak için gerekli ad alanlarını içe aktarmamız gerekiyor. C# dosyanızın en üstüne aşağıdaki satırları ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Adım 1: Belge Dizininizi Ayarlayın

Word belgenizi düzenlemeye başlamadan önce, belgenizin kaydedileceği dizini belirtmeniz gerekir. Bu, daha sonraki kaydetme işlemi için önemlidir.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Yer değiştirmek `"YOUR DOCUMENT DIRECTORY"` belge dizininize giden gerçek yol ile.

## Adım 2: Belgeyi ve Belge Oluşturucuyu Başlatın

Bir sonraki adım yeni bir tane başlatmaktır `Document` ve bir `DocumentBuilder`. `DocumentBuilder` Belgenin içeriğini oluşturmamızı sağlayan yardımcı bir sınıftır.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 3: Belgeye Bir Grafik Ekleyin

Şimdi, belgeye bir grafik ekleyelim `DocumentBuilder`Bu eğitimde örnek olarak bir Çizgi grafiği kullanacağız.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Burada belirli bir genişlik ve yüksekliğe sahip bir Çizgi grafiği ekliyoruz ve grafik başlığını ayarlıyoruz.

## Adım 4: Varsayılan Seriyi Temizle ve Yeni Seri Ekle

Varsayılan olarak, grafikte önceden oluşturulmuş bazı seriler olacaktır. Bunları temizlememiz ve belirli veri noktalarıyla kendi serimizi eklememiz gerekir.

```csharp
// Varsayılan olarak oluşturulan seriyi sil.
chart.Series.Clear();

// Özel veri noktalarıyla yeni seriler ekleyin.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Adım 5: Veri Etiketlerini Etkinleştir

Veri etiketlerini grafikte görüntüleyebilmek için, bunları serimiz için etkinleştirmemiz gerekir.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Adım 6: Veri Etiketlerini Biçimlendirin

Bu eğitimin özü veri etiketlerini biçimlendirmektir. Her veri etiketine ayrı ayrı farklı sayı biçimleri uygulayabiliriz.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Para birimi biçimi
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Tarih biçimi
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Yüzde formatı
```

Ayrıca, bir veri etiketinin biçimini bir kaynak hücreye bağlayabilirsiniz. Bağlandığında, `NumberFormat` genel olarak sıfırlanacak ve kaynak hücreden devralınacaktır.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Adım 7: Belgeyi Kaydedin

Son olarak belgeyi belirtilen dizine kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Bu, belgenizi belirtilen adla kaydeder ve biçimlendirilmiş veri etiketlerine sahip grafiğinizin korunmasını sağlar.

## Çözüm

Aspose.Words for .NET kullanarak bir grafikteki veri etiketlerini biçimlendirmek, Word belgelerinizin okunabilirliğini ve profesyonelliğini büyük ölçüde artırabilir. Bu adım adım kılavuzu izleyerek artık bir grafik oluşturabilir, veri serileri ekleyebilir ve veri etiketlerini ihtiyaçlarınızı karşılayacak şekilde biçimlendirebilirsiniz. Aspose.Words for .NET, Word belgelerinin kapsamlı bir şekilde özelleştirilmesine ve otomasyonuna olanak tanıyan güçlü bir araçtır ve bu da onu .NET geliştiricileri için paha biçilmez bir varlık haline getirir.

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, C# kullanarak Word belgelerini programlı olarak oluşturmak, düzenlemek ve dönüştürmek için güçlü bir kütüphanedir.

### Aspose.Words for .NET ile diğer grafik türlerini biçimlendirebilir miyim?
Evet, Aspose.Words for .NET çubuk, sütun, pasta ve daha fazlası dahil olmak üzere çeşitli grafik türlerini destekler.

### Aspose.Words for .NET için geçici lisansı nasıl alabilirim?
Geçici bir lisans alabilirsiniz [Burada](https://purchase.aspose.com/temporary-license/).

### Excel'de veri etiketlerini kaynak hücrelere bağlamak mümkün müdür?
Evet, veri etiketlerini kaynak hücrelere bağlayabilir, böylece sayı biçiminin kaynak hücreden alınmasına olanak sağlayabilirsiniz.

### Aspose.Words for .NET için daha detaylı dokümanları nerede bulabilirim?
Kapsamlı dokümanları bulabilirsiniz [Burada](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}