---
title: Grafik Veri Etiketini Özelleştir
linktitle: Grafik Veri Etiketini Özelleştir
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak grafik veri etiketlerini adım adım nasıl özelleştireceğinizi öğrenin. .NET geliştiricileri için mükemmel.
weight: 10
url: /tr/net/programming-with-charts/chart-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Grafik Veri Etiketini Özelleştir

## giriiş

.NET uygulamalarınızı dinamik ve özelleştirilmiş belge işleme yetenekleriyle süslemek mi istiyorsunuz? Aspose.Words for .NET tam da aradığınız cevap olabilir! Bu kılavuzda, Word belgelerini oluşturmak, değiştirmek ve dönüştürmek için güçlü bir kütüphane olan Aspose.Words for .NET'i kullanarak grafik veri etiketlerini özelleştirmeye derinlemesine dalacağız. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, bu eğitim sizi her adımda yönlendirecek ve bu aracı etkili bir şekilde nasıl kullanacağınızı anlamanızı sağlayacaktır.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. Visual Studio: Visual Studio 2019 veya sonraki bir sürümünü yükleyin.
2. .NET Framework: .NET Framework 4.0 veya sonraki bir sürümüne sahip olduğunuzdan emin olun.
3.  Aspose.Words for .NET: Aspose.Words for .NET'i şuradan indirin ve yükleyin:[indirme bağlantısı](https://releases.aspose.com/words/net/).
4. Temel C# Bilgisi: C# programlamaya aşinalık şarttır.
5.  Geçerli Bir Lisans: Bir tane edinin[geçici lisans](https://purchase.aspose.com/temporary-license/) veya bir tane satın alın[satın alma bağlantısı](https://purchase.aspose.com/buy).

## Ad Alanlarını İçe Aktar

Başlamak için, gerekli ad alanlarını C# projenize aktarmanız gerekir. Bu adım, Aspose.Words tarafından sağlanan tüm sınıflara ve yöntemlere erişiminizin olmasını sağladığı için önemlidir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Charts;
```

## Adım 1: Belgeyi ve Belge Oluşturucuyu Başlatın

Word belgeleri oluşturmak ve düzenlemek için öncelikle bir örneğini başlatmamız gerekir.`Document` sınıf ve bir`DocumentBuilder` nesne.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Açıklama

- Belge belgesi: Belge sınıfının yeni bir örneğini oluşturur.
- DocumentBuilder oluşturucusu: DocumentBuilder, Belge nesnesine içerik eklemeye yardımcı olur.

## Adım 2: Bir Grafik Ekle

 Daha sonra, belgeye bir çubuk grafik ekleyeceğiz.`DocumentBuilder` nesne.

```csharp
Shape shape = builder.InsertChart(ChartType.Bar, 432, 252);
Chart chart = shape.Chart;
```

### Açıklama

- Şekil şekli: Grafiği belgede bir şekil olarak temsil eder.
- builder.InsertChart(ChartType.Bar, 432, 252): Belirtilen boyutlara sahip bir çubuk grafik ekler.

## Adım 3: Grafik Serisine Erişim

Veri etiketlerini özelleştirmek için öncelikle grafikteki serilere erişmemiz gerekiyor.

```csharp
ChartSeries series0 = shape.Chart.Series[0];
```

### Açıklama

- ChartSeries series0: Özelleştireceğimiz grafiğin ilk serisini alır.

## Adım 4: Veri Etiketlerini Özelleştirin

Veri etiketleri çeşitli bilgileri görüntülemek üzere özelleştirilebilir. Etiketleri, kategori adını ve yüzdesini gizlerken, efsane anahtarını, seri adını ve değerini gösterecek şekilde yapılandıracağız.

```csharp
ChartDataLabelCollection labels = series0.DataLabels;
labels.ShowLegendKey = true;
labels.ShowLeaderLines = true;
labels.ShowCategoryName = false;
labels.ShowPercentage = false;
labels.ShowSeriesName = true;
labels.ShowValue = true;
labels.Separator = "/";
```

### Açıklama

- ChartDataLabelCollection etiketleri: Serinin veri etiketlerine erişir.
- labels.ShowLegendKey: Efsane anahtarını görüntüler.
- labels.ShowLeaderLines: Veri noktalarının çok dışında konumlandırılan veri etiketleri için lider çizgilerini gösterir.
- labels.ShowCategoryName: Kategori adını gizler.
- labels.ShowPercentage: Yüzde değerini gizler.
- labels.ShowSeriesName: Seri adını görüntüler.
- labels.ShowValue: Veri noktalarının değerini görüntüler.
- labels.Separator: Veri etiketleri için ayırıcıyı ayarlar.

## Adım 5: Belgeyi Kaydedin

Son olarak belgeyi belirtilen dizine kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithCharts.ChartDataLabel.docx");
```

### Açıklama

- doc.Save: Belgeyi belirtilen adla belirtilen dizine kaydeder.

## Çözüm

 Tebrikler! Aspose.Words for .NET kullanarak grafik veri etiketlerini başarıyla özelleştirdiniz. Bu kitaplık, Word belgelerini programatik olarak işlemek için sağlam bir çözüm sunarak geliştiricilerin karmaşık ve dinamik belge işleme uygulamaları oluşturmasını kolaylaştırır.[belgeleme](https://reference.aspose.com/words/net/) Daha fazla özellik ve yeteneği keşfetmek için.

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, geliştiricilerin Word belgelerini programlı bir şekilde oluşturmalarına, değiştirmelerine ve dönüştürmelerine olanak tanıyan güçlü bir belge işleme kütüphanesidir.

### Aspose.Words for .NET'i nasıl yüklerim?
 Bunu şu adresten indirip kurabilirsiniz:[indirme bağlantısı](https://releases.aspose.com/words/net/). Verilen kurulum talimatlarını izleyin.

### Aspose.Words for .NET'i ücretsiz deneyebilir miyim?
 Evet, alabilirsiniz[ücretsiz deneme](https://releases.aspose.com/) veya bir[geçici lisans](https://purchase.aspose.com/temporary-license/)Ürünü değerlendirmek için.

### Aspose.Words for .NET, .NET Core ile uyumlu mudur?
Evet, Aspose.Words for .NET, .NET Core, .NET Standard ve .NET Framework ile uyumludur.

### Aspose.Words for .NET için desteği nereden alabilirim?
 Ziyaret edebilirsiniz[destek forumu](https://forum.aspose.com/c/words/8) Aspose topluluğundan ve uzmanlardan yardım ve destek için.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
