---
title: Tabloyu Doğrudan Ekle
linktitle: Tabloyu Doğrudan Ekle
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak tabloları doğrudan Word belgelerine nasıl ekleyeceğinizi öğrenin. Belge oluşturmanızı kolaylaştırmak için ayrıntılı, adım adım kılavuzumuzu izleyin.
weight: 10
url: /tr/net/programming-with-tables/insert-table-directly/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tabloyu Doğrudan Ekle

## giriiş
Programatik olarak tablo oluşturmak oldukça zorlu olabilir, özellikle de karmaşık belge yapılarıyla uğraşırken. Ama endişelenmeyin, sizin için bunu parçalara ayırmak için buradayız! Bu kılavuzda, .NET için Aspose.Words kullanarak bir tabloyu doğrudan bir Word belgesine ekleme adımlarını ele alacağız. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, bu eğitim süreci kolayca ustalaşmanıza yardımcı olacak.

## Ön koşullar

Koda dalmadan önce, başlamak için ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım. İşte hızlı bir kontrol listesi:

1.  Aspose.Words for .NET Kütüphanesi: Aspose.Words for .NET kütüphanesini indirip kurduğunuzdan emin olun. Bunu şu adresten alabilirsiniz:[indirme sayfası](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio benzeri bir geliştirme ortamı.
3. C# Temel Bilgileri: C# programlamanın temellerini anlamak.
4. Belge Dizini: Belgelerinizi kaydedeceğiniz dizin yolu.

Bu ön koşullar sağlandığında kodlamaya başlamaya hazırsınız!

## Ad Alanlarını İçe Aktar

Öncelikle gerekli ad alanlarını içe aktaralım. Bu ad alanları bize Word belgeleriyle çalışmak için gereken sınıfları ve yöntemleri sağlayacaktır.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Artık ad alanlarımız hazır olduğuna göre, heyecan verici kısma geçelim: Tabloları doğrudan bir Word belgesine oluşturma ve ekleme.

## Adım 1: Belgeyi Ayarlama

Yeni bir Word belgesi oluşturarak başlayalım. Tablomuz buraya eklenecek.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

 Bu kod yeni bir Word belgesi başlatır. Değiştirmeniz gerekecek`"YOUR DOCUMENT DIRECTORY"` belge dizininize giden gerçek yol ile.

## Adım 2: Tablo Nesnesini Oluşturma

Sonra, tablo nesnesini yaratıyoruz. Burada tablomuzun yapısını tanımlayacağız.

```csharp
// Tablo nesnesini oluşturarak başlıyoruz. Belge nesnesini geçirmemiz gerektiğini unutmayın
// her düğümün kurucusuna. Bunun nedeni, oluşturduğumuz her düğümün ait olması gerektiğidir
// bir belgeye.
Table table = new Table(doc);
doc.FirstSection.Body.AppendChild(table);
```

Burada yeni bir tablo oluşturup bunu belgemizin ilk bölümünün gövdesine ekliyoruz.

## Adım 3: Satır ve Hücre Ekleme

Bir tablo satırlardan ve hücrelerden oluşur. Bu öğeleri adım adım ekleyelim.

### Bir Satır Ekleme

```csharp
// Burada EnsureMinimum'ı çağırarak bizim için satırları ve hücreleri oluşturabiliriz. Bu yöntem kullanılır
// belirtilen düğümün geçerli olduğundan emin olmak için. Bu durumda, geçerli bir tablonun en az bir Satır ve bir hücreye sahip olması gerekir.
// Bunun yerine satır ve tabloyu kendimiz oluşturacağız.
// Eğer bir algoritma içerisinde tablo oluşturuyor olsaydık bunu yapmanın en iyi yolu bu olurdu.
Row row = new Row(doc);
row.RowFormat.AllowBreakAcrossPages = true;
table.AppendChild(row);
```

Bu kod yeni bir satır oluşturur ve bunu tablomuza ekler.

### Satıra Hücre Ekleme

Şimdi satırımıza birkaç hücre ekleyelim. 

```csharp
Cell cell = new Cell(doc);
cell.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
cell.CellFormat.Width = 80;
cell.AppendChild(new Paragraph(doc));
cell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 1 Text"));
row.AppendChild(cell);
```

Bu kod parçasında bir hücre oluşturuyoruz, arka plan rengini açık mavi olarak ayarlıyoruz ve genişliğini tanımlıyoruz. Sonra, metnimizi tutmak için hücreye bir paragraf ve bir koşu ekliyoruz.

## Adım 4: Hücrelerin Klonlanması

Hücre ekleme işlemini hızlandırmak için mevcut hücreleri klonlayabiliriz.

```csharp
// Daha sonra tablodaki diğer hücreler ve satırlar için de aynı işlemi tekrarlayacağız.
//Mevcut hücreleri ve satırları klonlayarak da işleri hızlandırabiliriz.
row.AppendChild(cell.Clone(false));
row.LastCell.AppendChild(new Paragraph(doc));
row.LastCell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 2 Text"));
```

Bu kod mevcut hücreyi klonlar ve satıra ekler. Daha sonra yeni hücreye bir paragraf ve bir çalıştırma ekleriz.

## Adım 5: Otomatik Uyum Ayarlarını Uygulama

Son olarak, sütunların sabit genişliklere sahip olmasını sağlamak için tablomuza otomatik uyum ayarlarını uygulayalım.

```csharp
// Artık otomatik uyum ayarlarından istediklerimizi uygulayabiliriz.
table.AutoFit(AutoFitBehavior.FixedColumnWidths);
```

## Adım 6: Belgeyi Kaydetme

Masamız hazır olduğuna göre artık belgeyi kaydetmenin zamanı geldi.

```csharp
doc.Save(dataDir + "WorkingWithTables.InsertTableDirectly.docx");
```

Bu kod tablo eklenmiş halde belgeyi kaydeder.

## Çözüm

Tebrikler! Aspose.Words for .NET kullanarak bir tabloyu doğrudan bir Word belgesine başarıyla eklediniz. Bu işlem karmaşık tabloları programatik olarak oluşturmak için kullanılabilir ve belge otomasyon görevlerinizi çok daha kolay hale getirir. İster raporlar, ister faturalar veya başka bir belge türü üretiyor olun, tabloları nasıl yöneteceğinizi anlamak önemli bir beceridir.

## SSS

### Aspose.Words for .NET'i nasıl indirebilirim?
 Aspose.Words for .NET'i şu adresten indirebilirsiniz:[indirme sayfası](https://releases.aspose.com/words/net/).

### Satın almadan önce Aspose.Words for .NET'i deneyebilir miyim?
 Evet, talep edebilirsiniz[ücretsiz deneme](https://releases.aspose.com/) satın almadan önce kütüphaneyi değerlendirmek.

### Aspose.Words for .NET'i nasıl satın alabilirim?
Aspose.Words for .NET'i şu adresten satın alabilirsiniz:[satın alma sayfası](https://purchase.aspose.com/buy).

### Aspose.Words for .NET'in belgelerini nerede bulabilirim?
 Belgeler mevcuttur[Burada](https://reference.aspose.com/words/net/).

### Aspose.Words for .NET kullanırken desteğe ihtiyacım olursa ne olur?
 Destek için şu adresi ziyaret edebilirsiniz:[Aspose.Words forumu](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
