---
title: Bir Grafikteki Veri Etiketleri İçin Varsayılan Seçenekleri Ayarlama
linktitle: Bir Grafikteki Veri Etiketleri İçin Varsayılan Seçenekleri Ayarlama
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak bir grafikteki veri etiketleri için varsayılan seçenekleri nasıl ayarlayacağınızı öğrenin. Grafikleri zahmetsizce oluşturmak ve özelleştirmek için adım adım kılavuzumuzu izleyin.
weight: 10
url: /tr/net/programming-with-charts/default-options-for-data-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bir Grafikteki Veri Etiketleri İçin Varsayılan Seçenekleri Ayarlama

## giriiş

Merhaba! Belge otomasyonu dünyasına dalmak için heyecanlı mısınız? Bugün, çarpıcı belgeleri programatik olarak oluşturmak için Aspose.Words for .NET'i nasıl kullanacağınızı keşfedeceğiz. Aspose.Words, Word belgelerini kolaylıkla düzenlemenize olanak tanıyan güçlü bir kütüphanedir ve bu eğitimde, bir grafikteki veri etiketleri için varsayılan seçenekleri ayarlamaya odaklanacağız. İster deneyimli bir geliştirici olun ister yeni başlayan, bu kılavuz sizi kısa sürede çalışır duruma getirmek için her adımda yönlendirecektir.

## Ön koşullar

Başlamadan önce, bu öğreticiyi takip etmek için ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım. İşte hızlı bir kontrol listesi:

- Visual Studio veya herhangi bir .NET uyumlu IDE: Kodunuzu burada yazacak ve çalıştıracaksınız.
-  Aspose.Words for .NET: Şunları yapabilirsiniz:[en son sürümü indirin](https://releases.aspose.com/words/net/) ve projenize kurun.
- C# programlamanın temel bilgisi: Bu rehber yeni başlayanlara uygun olsa da, C# ile ilgili biraz bilgi sahibi olmak faydalı olacaktır.
- .NET Framework yüklü: Bilgisayarınızda .NET Framework'ün kurulu olduğundan emin olun.
-  Aspose.Words için geçici bir lisans: Bir tane edinin[Burada](https://purchase.aspose.com/temporary-license/) tüm işlevlerin kilidini açmak için.

Bu ön koşulları yerine getirdikten sonra artık yola çıkmaya hazırız!

## Ad Alanlarını İçe Aktar

İlk önce projemizi kuralım ve gerekli ad alanlarını içe aktaralım. Bu ad alanları Aspose.Words işlevselliğine erişmek için çok önemlidir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Adım 1: Yeni Bir Belge Oluşturun


 Yolculuk yeni bir belge oluşturmak ve bir belgeyi başlatmakla başlar.`DocumentBuilder` .`DocumentBuilder` sınıfı, belge içeriğini kolayca düzenlemek için bir dizi yöntem sağlar.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Yeni bir belge oluştur
Document doc = new Document();

// DocumentBuilder'ı Başlat
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Açıklama

 Bu adımda, içeriğimizi eklemek ve biçimlendirmek için kullanacağımız belgeyi ve oluşturucuyu ayarladık.`dataDir` değişkeni, son belgemizi kaydedeceğimiz yolu tutar.

## Adım 2: Bir Grafik Ekle

 Daha sonra, belgemize bir pasta grafiği ekleyeceğiz.`InsertChart` yöntemi`DocumentBuilder` sınıf bunu çok kolaylaştırıyor.

```csharp
// Pasta grafiği ekle
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Grafik nesnesine erişin
Chart chart = shape.Chart;
```

### Açıklama

Burada, belgemize bir pasta grafiği ekliyoruz.`InsertChart` method, parametre olarak grafik türü, genişlik ve yükseklik gerektirir. Grafiği ekledikten sonra, daha fazla işlem yapmak için grafik nesnesine erişiriz.

## Adım 3: Grafik Serisini Özelleştirin

Şimdi, grafikteki mevcut serileri temizleyeceğiz ve özel serimizi ekleyeceğiz. Bu seri veri noktalarımızı temsil edecek.

```csharp
// Mevcut grafik serisini temizle
chart.Series.Clear();

// Grafiğe yeni seriler ekle
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Açıklama

Bu adımda, önceden var olan tüm serileri temizleyerek grafiğimizin boş olduğundan emin oluyoruz. Ardından, pasta grafiğimizde görüntülenecek özel kategoriler ve değerler içeren yeni bir seri ekliyoruz.

## Adım 4: Veri Etiketleri için Varsayılan Seçenekleri Ayarlayın

Veri etiketleri, grafiğinizi bilgilendirici hale getirmek için çok önemlidir. Yüzde, değer gösterme ve ayırıcıyı özelleştirme seçeneklerini ayarlayacağız.

```csharp
// Veri etiketleri koleksiyonuna erişin
ChartDataLabelCollection labels = series.DataLabels;

// Veri etiketi seçeneklerini ayarla
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Açıklama

 Burada, şuraya erişiyoruz:`DataLabels`Her veri etiketinde görüntülenen görünümü ve bilgileri özelleştirmek için serimizin özelliği. Hem yüzdeyi hem de değeri göstermeyi, lider çizgilerini gizlemeyi ve özel bir ayırıcı ayarlamayı seçtik.

## Adım 5: Belgeyi Kaydedin

Son olarak, belgemizi belirtilen dizine kaydedeceğiz. Bu adım, tüm değişikliklerimizin bir dosyaya yazılmasını sağlar.

```csharp
// Belgeyi kaydet
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Açıklama

 Bu son adımda, belgemizi kullanarak kaydediyoruz`Save` yöntem. Belge belirtilen dizine kaydedilecektir`dataDir`"WorkingWithCharts.DefaultOptionsForDataLabels.docx" adıyla.

## Çözüm

İşte karşınızda! Aspose.Words for .NET kullanarak özelleştirilmiş bir pasta grafiğine sahip bir Word belgesini başarıyla oluşturdunuz. Bu güçlü kütüphane, belge oluşturma ve düzenlemeyi otomatikleştirmeyi kolaylaştırarak size zaman ve emek kazandırır. İster raporlar, ister faturalar veya başka herhangi bir tür belge üretiyor olun, Aspose.Words sizin için her şeyi yapar.

 Keşfetmekten çekinmeyin[Aspose.Words belgeleri](https://reference.aspose.com/words/net/) daha fazla özellik ve örnek için. İyi kodlamalar!

## SSS

### Aspose.Words'ü ücretsiz kullanabilir miyim?
Aspose.Words'ü ücretsiz olarak kullanabilirsiniz[geçici lisans](https://purchase.aspose.com/temporary-license/) veya özelliklerini kullanarak keşfedin[ücretsiz deneme](https://releases.aspose.com/).

### Aspose.Words için nasıl destek alabilirim?
 Destek almak için:[Aspose.Words destek forumu](https://forum.aspose.com/c/words/8).

### Başka türde grafikler ekleyebilir miyim?
 Evet, Aspose.Words çubuk, çizgi ve sütun grafikleri gibi çeşitli grafik türlerini destekler.[belgeleme](https://reference.aspose.com/words/net/) Daha detaylı bilgi için.

### Aspose.Words .NET Core ile uyumlu mu?
 Evet, Aspose.Words .NET Core ile uyumludur. Daha fazla bilgiyi şurada bulabilirsiniz:[belgeleme](https://reference.aspose.com/words/net/).

### Aspose.Words için lisansı nasıl satın alabilirim?
 Lisansı şuradan satın alabilirsiniz:[Aspose mağazası](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
