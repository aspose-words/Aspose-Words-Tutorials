---
title: Alan Grafiğini Word Belgesine Ekleme
linktitle: Alan Grafiğini Word Belgesine Ekleme
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak bir belgeye alan grafiğinin nasıl ekleneceğini öğrenin. Seri verilerini ekleyin ve belgeyi grafikle birlikte kaydedin.
weight: 10
url: /tr/net/programming-with-charts/insert-area-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Alan Grafiğini Word Belgesine Ekleme

## giriiş

Aspose.Words for .NET kullanarak Word belgesine alan grafiği eklemeye yönelik bu adım adım kılavuza hoş geldiniz. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, bu eğitim Word belgelerinizde çarpıcı ve bilgilendirici alan grafikleri oluşturmak için bilmeniz gereken her şeyi size anlatacaktır. Ön koşulları ele alacağız, gerekli ad alanlarını nasıl içe aktaracağınızı göstereceğiz ve sürecin her adımında sizi net, kolay takip edilebilir talimatlarla yönlendireceğiz.

## Ön koşullar

Başlamadan önce, başlamak için ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1.  Aspose.Words for .NET: Aspose.Words for .NET'in yüklü olduğundan emin olun. İndirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
2. .NET Framework: Bilgisayarınızda .NET Framework'ün yüklü olduğundan emin olun.
3. IDE: Kodunuzu yazmak ve çalıştırmak için Visual Studio benzeri bir Entegre Geliştirme Ortamı (IDE).
4. Temel C# Bilgisi: C# programlamaya dair temel bir anlayışa sahip olmak faydalı olacaktır.

Bu ön koşulları sağladığınızda, Word belgelerinizde güzel alan grafikleri oluşturmaya başlayabilirsiniz.

## Ad Alanlarını İçe Aktar

İlk önce gerekli ad alanlarını içe aktaralım. Bu ad alanları, .NET için Aspose.Words'de Word belgeleri ve çizelgeleriyle çalışmak için gereken sınıfları ve yöntemleri sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
```

Artık temel ad alanlarını içe aktardığımıza göre, adım adım belgemizi oluşturmaya ve alan grafiği eklemeye geçelim.

## Adım 1: Yeni bir Word Belgesi Oluşturun

Yeni bir Word belgesi oluşturarak başlayalım. Bu, alan grafiğimizi ekleyeceğimiz temel olacak.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

 Bu adımda yeni bir başlangıç yapıyoruz`Document` Word belgemizi temsil eden nesne.

## Adım 2: Bir Grafik Eklemek İçin DocumentBuilder'ı Kullanın

 Daha sonra şunu kullanacağız:`DocumentBuilder` Belgemize alan grafiği eklemek için sınıf.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
```

 Burada bir tane yaratıyoruz`DocumentBuilder` nesneyi seçin ve bunu belgeye belirli boyutlarda (432x252) bir alan grafiği eklemek için kullanın.

## Adım 3: Grafik Nesnesine Erişim

 Tabloyu ekledikten sonra, şuraya erişmemiz gerekiyor:`Chart` Alan grafiğimizi özelleştirmek için nesne.

```csharp
Chart chart = shape.Chart;
```

 Bu kod satırı şunu alır:`Chart` Az önce eklediğimiz şekilden nesne.

## Adım 4: Seri Verilerini Grafiğe Ekleyin

Şimdi, grafiğimize biraz veri ekleme zamanı. Tarihler ve karşılık gelen değerlerle bir seri ekleyeceğiz.

```csharp
chart.Series.Add("Aspose Series 1", new []
{
    new DateTime(2002, 05, 01),
    new DateTime(2002, 06, 01),
    new DateTime(2002, 07, 01),
    new DateTime(2002, 08, 01),
    new DateTime(2002, 09, 01)
}, 
new double[] { 32, 32, 28, 12, 15 });
```

Bu adımda, bir dizi tarih ve karşılık gelen değerler içeren "Aspose Series 1" adlı bir dizi ekliyoruz.

## Adım 5: Belgeyi Kaydedin

Son olarak eklenen alan grafiğinin bulunduğu belgemizi kaydedeceğiz.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertAreaChart.docx");
```

Bu kod satırı belgeyi belirtilen dizine belirtilen dosya adıyla kaydeder.

## Çözüm

Tebrikler! Aspose.Words for .NET kullanarak bir Word belgesine alan grafiğini başarıyla eklediniz. Bu kılavuz, ortamınızı kurmaktan son belgeyi kaydetmeye kadar her adımda size yol gösterdi. Aspose.Words for .NET ile Word belgelerinizde çok çeşitli grafikler ve diğer karmaşık öğeler oluşturabilir, raporlarınızı ve sunumlarınızı daha dinamik ve bilgilendirici hale getirebilirsiniz.

## SSS

### Aspose.Words for .NET'i diğer .NET dilleriyle birlikte kullanabilir miyim?
Evet, Aspose.Words for .NET, VB.NET gibi diğer .NET dillerini de destekler.

### Grafik görünümünü özelleştirmek mümkün mü?
Kesinlikle! Aspose.Words for .NET, grafiklerinizin görünümünü özelleştirmek için kapsamlı seçenekler sunar.

### Tek bir Word belgesine birden fazla grafik ekleyebilir miyim?
Evet, tek bir Word belgesine ihtiyacınız kadar grafik ekleyebilirsiniz.

### Aspose.Words for .NET diğer grafik türlerini destekliyor mu?
Evet, Aspose.Words for .NET çubuk, çizgi, pasta ve daha fazlası dahil olmak üzere çeşitli grafik türlerini destekler.

### Aspose.Words for .NET için geçici lisansı nereden alabilirim?
 Geçici lisansı şuradan alabilirsiniz:[Burada](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
