---
title: Tablo ve Hücreyi Farklı Kenarlıklarla Biçimlendir
linktitle: Tablo ve Hücreyi Farklı Kenarlıklarla Biçimlendir
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak tabloları ve hücreleri farklı kenarlıklarla nasıl biçimlendireceğinizi öğrenin. Word belgelerinizi özelleştirilmiş tablo stilleri ve hücre gölgelendirmesiyle geliştirin.
weight: 10
url: /tr/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tablo ve Hücreyi Farklı Kenarlıklarla Biçimlendir

## giriiş

Tablo ve hücrelerin kenarlıklarını özelleştirerek Word belgelerinizin daha profesyonel görünmesini hiç denediniz mi? Denemediyseniz, harika bir şey sizi bekliyor! Bu eğitim, Aspose.Words for .NET kullanarak tabloları ve hücreleri farklı kenarlıklarla biçimlendirme sürecini adım adım anlatacak. Tablolarınızın görünümünü yalnızca birkaç satır kodla değiştirme gücüne sahip olduğunuzu hayal edin. İlginizi çekti mi? Hadi başlayalım ve bunu nasıl kolaylıkla başarabileceğinizi inceleyelim.

## Ön koşullar

Başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:
- C# programlamanın temellerini anlamak.
- Bilgisayarınızda Visual Studio yüklü olmalıdır.
-  Aspose.Words for .NET kütüphanesi. Eğer henüz yüklemediyseniz, indirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
-  Geçerli bir Aspose lisansı. Ücretsiz deneme veya geçici lisansı şu adresten alabilirsiniz:[Burada](https://purchase.aspose.com/temporary-license/).

## Ad Alanlarını İçe Aktar

Aspose.Words for .NET ile çalışmak için, gerekli ad alanlarını projenize içe aktarmanız gerekir. Aşağıdaki using yönergelerini kod dosyanızın en üstüne ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## Adım 1: Belgeyi ve DocumentBuilder'ı Başlatın

Öncelikle yeni bir belge oluşturmanız ve belge içeriğini oluşturmaya yardımcı olan DocumentBuilder'ı başlatmanız gerekiyor. 

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 2: Bir Tablo Oluşturmaya Başlayın

Daha sonra DocumentBuilder'ı kullanarak tablo oluşturmaya başlayın ve ilk hücreyi ekleyin.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

## Adım 3: Tablo Kenarlıklarını Ayarlayın

Tüm tablo için sınırları ayarlayın. Bu adım, aksi belirtilmediği sürece tablo içindeki tüm hücrelerin tutarlı bir sınır stiline sahip olmasını sağlar.

```csharp
// Tüm tablonun sınırlarını belirleyin.
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## Adım 4: Hücre Gölgelendirmesini Uygula

Hücrelere görsel olarak belirgin hale getirmek için gölgelendirme uygulayın. Bu örnekte, ilk hücrenin arka plan rengini kırmızıya ayarlayacağız.


```csharp
// Bu hücre için hücre gölgelendirmesini ayarlayın.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## Adım 5: Farklı Gölgelendirmeye Sahip Başka Bir Hücre Ekle

İkinci hücreyi ekleyin ve farklı bir gölgelendirme rengi uygulayın. Bu, tabloyu daha renkli ve okunması daha kolay hale getirir.

```csharp
builder.InsertCell();
// İkinci hücre için farklı bir hücre gölgelendirmesi belirtin.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## Adım 6: Hücre Biçimlendirmesini Temizle

Bir sonraki hücrelerin aynı stilleri devralmamasını sağlamak için önceki işlemlerden kalan hücre biçimlendirmesini temizleyin.


```csharp
// Önceki işlemlerden kalan hücre biçimlendirmesini temizle.
builder.CellFormat.ClearFormatting();
```

## Adım 7: Belirli Hücreler için Kenarlıkları Özelleştirin

Belirli hücreler için kenarlıkları özelleştirerek onları öne çıkarın. Burada, yeni satırın ilk hücresi için daha büyük kenarlıklar ayarlayacağız.

```csharp
builder.InsertCell();
// Bu satırın ilk hücresi için daha büyük kenarlıklar oluşturun. Bu farklı olacaktır
// Masaya konulan sınırlara göre.
builder.CellFormat.Borders.Left.LineWidth = 4.0;
builder.CellFormat.Borders.Right.LineWidth = 4.0;
builder.CellFormat.Borders.Top.LineWidth = 4.0;
builder.CellFormat.Borders.Bottom.LineWidth = 4.0;
builder.Writeln("Cell #3");
```

## Adım 8: Son Hücreyi Ekle

Son hücreyi ekleyin ve biçimlendirmesinin temizlendiğinden emin olun, böylece tablonun varsayılan stilleri kullanılır.

```csharp
builder.InsertCell();
builder.CellFormat.ClearFormatting();
builder.Writeln("Cell #4");
```

## Adım 9: Belgeyi Kaydedin

Son olarak belgeyi belirtilen dizine kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.FormatTableAndCellWithDifferentBorders.docx");
```

## Çözüm

İşte bu kadar! Aspose.Words for .NET kullanarak tabloları ve hücreleri farklı kenarlıklarla nasıl biçimlendireceğinizi öğrendiniz. Tablo kenarlıklarını ve hücre gölgelendirmesini özelleştirerek belgelerinizin görsel çekiciliğini önemli ölçüde artırabilirsiniz. O halde devam edin, farklı stilleri deneyin ve belgelerinizi öne çıkarın!

## SSS

### Her hücre için farklı kenarlık stilleri kullanabilir miyim?
 Evet, her hücre için farklı kenarlık stilleri ayarlayabilirsiniz.`CellFormat.Borders` mülk.

### Bir tablodan tüm kenarlıkları nasıl kaldırabilirim?
 Kenarlık stilini şu şekilde ayarlayarak tüm kenarlıkları kaldırabilirsiniz:`LineStyle.None`.

### Her hücre için farklı kenarlık renkleri belirlemek mümkün müdür?
 Kesinlikle! Her hücre için kenarlık rengini, şunu kullanarak özelleştirebilirsiniz:`CellFormat.Borders.Color` mülk.

### Hücre arka planı olarak resim kullanabilir miyim?
Aspose.Words hücre arka planı olarak doğrudan resimleri desteklemese de, bir hücreye resim ekleyebilir ve hücre alanını kaplayacak şekilde boyutunu ayarlayabilirsiniz.

### Bir tablodaki hücreleri nasıl birleştiririm?
 Hücreleri birleştirmek için şunu kullanabilirsiniz:`CellFormat.HorizontalMerge` Ve`CellFormat.VerticalMerge` özellikler.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
