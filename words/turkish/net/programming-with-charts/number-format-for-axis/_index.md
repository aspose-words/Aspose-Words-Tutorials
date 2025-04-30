---
"description": "Bu adım adım kılavuzla Aspose.Words for .NET kullanarak grafik eksen numaralarını nasıl biçimlendireceğinizi öğrenin. Belgenizin okunabilirliğini ve profesyonelliğini zahmetsizce artırın."
"linktitle": "Bir Grafikteki Eksen İçin Sayı Biçimi"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Bir Grafikteki Eksen İçin Sayı Biçimi"
"url": "/tr/net/programming-with-charts/number-format-for-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Bir Grafikteki Eksen İçin Sayı Biçimi

## giriiş

Merhaba! Belgelerinizdeki grafiklerle hiç çalıştınız mı ve eksenlerinizdeki sayıları daha profesyonel görünmeleri için biçimlendirebilmeyi istediniz mi? Şanslısınız! Bu eğitimde, .NET için Aspose.Words'ü kullanarak tam olarak bunu nasıl başarabileceğinizi derinlemesine inceleyeceğiz. Bu güçlü kütüphane, Word belgelerini çocuk oyuncağı gibi yönetmenizi sağlar. Ve bugün, bu grafik eksenlerine özel sayı biçimleriyle bir makyaj yapmaya odaklanıyoruz.

## Ön koşullar

Başlamadan önce, ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım. İşte hızlı bir kontrol listesi:

- Aspose.Words for .NET: Yüklü olduğundan emin olun. Değilse, [buradan indirin](https://releases.aspose.com/words/net/).
- .NET Framework: Uyumlu bir .NET Framework'ün yüklü olduğundan emin olun.
- Geliştirme Ortamı: Visual Studio gibi bir IDE mükemmel çalışacaktır.
- Temel C# Bilgisi: Bu, kodlama örneklerini takip etmenize yardımcı olacaktır.

## Ad Alanlarını İçe Aktar

İlk önce, projenize gerekli ad alanlarını içe aktarmanız gerekir. Bu, bir ev inşa etmeden önce temelleri atmak gibidir. Aşağıdaki using yönergelerini kod dosyanızın en üstüne ekleyin:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Reporting;
```

Şimdi süreci basit ve takip edilmesi kolay adımlara bölelim.

## Adım 1: Belgeyi Ayarlama

Başlık: Belgenizi Başlatın

Öncelikle yeni bir belge ve bir belge oluşturucu oluşturmanız gerekir. Bu adımı, şaheserinize başlamadan önce tuvalinizi ve fırçanızı hazırlamak olarak düşünün.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Burada, `dataDir` son dosyayı kaydedeceğiniz belge dizininize giden yoldur. `Document` Ve `DocumentBuilder` Aspose.Words'den Word belgeleri oluşturmanıza ve düzenlemenize yardımcı olan sınıflardır.

## Adım 2: Bir Grafik Ekleme

Başlık: Belgenize Bir Grafik Ekleyin

Sonra, belgenize bir grafik ekleyelim. Sihir burada başlıyor. Boş tuvalimiz olarak işlev görecek bir sütun grafiği ekleyeceğiz.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

The `InsertChart` yöntem, belirtilen türde (bu durumda Sütun) ve boyutlarda bir grafiği belgeye ekler.

## Adım 3: Grafik Serisini Özelleştirme

Başlık: Grafiğinizi Verilerle Doldurun

Şimdi, grafiğimize biraz veri eklememiz gerekiyor. Bu adım, grafiğinizi anlamlı bilgilerle doldurmaya benzer.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1900000, 850000, 2100000, 600000, 1500000 });
```

Burada, beş veri noktasıyla "Aspose Serisi 1" adlı yeni bir seri ekliyoruz. `Series.Clear` Bu yöntem, yeni serimizi eklemeden önce önceden var olan tüm verilerin kaldırılmasını sağlar.

## Adım 4: Eksen Numaralarını Biçimlendirme

Başlık: Eksen Sayılarınızı Güzelleştirin

Son olarak, Y eksenindeki sayıları daha okunabilir hale getirmek için biçimlendirelim. Bu, sanat eserinize son rötuşları yapmak gibidir.

```csharp
chart.AxisY.NumberFormat.FormatCode = "#,##0";
```

The `FormatCode` özellik, eksendeki sayılar için özel bir biçim ayarlamanıza olanak tanır. Bu örnekte, `#,##0` binler için büyük sayıların virgülle gösterilmesini sağlar.

## Adım 5: Belgeyi Kaydetme

Başlık: Başyapıtınızı Kaydedin

Artık her şey ayarlandığına göre, belgenizi kaydetme zamanı geldi. Bu adım, çalışmanızın görkemli ifşasıdır.

```csharp
doc.Save(dataDir + "WorkingWithCharts.NumberFormatForAxis.docx");
```

Burada, `Save` yöntem, belgeyi belirtilen yola dosya adıyla kaydeder `WorkingWithCharts.NumberFormatForAxis.docx`.

## Çözüm

İşte bu kadar! Aspose.Words for .NET kullanarak grafiğinizin Y eksenindeki sayıları başarıyla biçimlendirdiniz. Bu, grafiklerinizin daha profesyonel görünmesini sağlamanın yanı sıra okunabilirliğini de artırır. Aspose.Words, çarpıcı Word belgelerini programatik olarak oluşturmanıza yardımcı olabilecek çok sayıda özellik sunar. Öyleyse, neden daha fazlasını keşfedip başka neler yapabileceğinizi görmüyorsunuz?

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, geliştiricilerin Word belgelerini programlı bir şekilde oluşturmalarına, düzenlemelerine ve dönüştürmelerine olanak tanıyan güçlü bir kütüphanedir.

### Eksen numaralarının yanı sıra grafiğin diğer yönlerini de biçimlendirebilir miyim?
Kesinlikle! Aspose.Words for .NET, başlıkları, etiketleri biçimlendirmenize ve hatta grafiğin görünümünü özelleştirmenize olanak tanır.

### Aspose.Words for .NET için ücretsiz deneme sürümü mevcut mu?
Evet, alabilirsiniz [ücretsiz deneme burada](https://releases.aspose.com/).

### Aspose.Words for .NET'i C# dışındaki diğer .NET dilleriyle birlikte kullanabilir miyim?
Evet, Aspose.Words for .NET, VB.NET ve F# dahil olmak üzere tüm .NET dilleriyle uyumludur.

### Daha detaylı dokümanları nerede bulabilirim?
Ayrıntılı dokümantasyon şu adreste mevcuttur: [Aspose.Words for .NET dokümantasyon sayfası](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}