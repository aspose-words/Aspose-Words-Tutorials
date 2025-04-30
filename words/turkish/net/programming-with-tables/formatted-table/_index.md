---
"description": "Bu ayrıntılı adım adım kılavuzla Aspose.Words for .NET kullanarak Word belgelerinde tabloların nasıl oluşturulacağını ve biçimlendirileceğini öğrenin."
"linktitle": "Biçimlendirilmiş Tablo"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Biçimlendirilmiş Tablo"
"url": "/tr/net/programming-with-tables/formatted-table/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Biçimlendirilmiş Tablo

## giriiş

Word belgelerinde tabloları programatik olarak oluşturmak ve biçimlendirmek zorlu bir görev gibi görünebilir, ancak Aspose.Words for .NET ile bu basit ve yönetilebilir hale gelir. Bu eğitimde, Aspose.Words for .NET kullanarak bir Word belgesinde biçimlendirilmiş bir tablonun nasıl oluşturulacağını göstereceğiz. Ortamınızı kurmaktan belgenizi güzel biçimlendirilmiş bir tabloyla kaydetmeye kadar her şeyi ele alacağız.

## Ön koşullar

Koda dalmadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1. Aspose.Words for .NET Kütüphanesi: Buradan indirin [Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio benzeri bir IDE.
3. .NET Framework: Bilgisayarınızda .NET Framework'ün yüklü olduğundan emin olun.

## Ad Alanlarını İçe Aktar

Gerçek kodu yazmadan önce gerekli ad alanlarını içe aktarmanız gerekir:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Adım 1: Belge Dizininizi Ayarlayın

Öncelikle belgenizin kaydedileceği yolu tanımlamanız gerekiyor.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Yer değiştirmek `"YOUR DOCUMENT DIRECTORY"` belgeyi kaydetmek istediğiniz gerçek yol ile.

## Adım 2: Belgeyi ve Belge Oluşturucuyu Başlatın

Şimdi yeni bir belge ve bir DocumentBuilder nesnesi başlatın.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

The `DocumentBuilder` belge oluşturma sürecini basitleştiren bir yardımcı sınıftır.

## Adım 3: Tabloyu Başlatın

Daha sonra, tabloyu oluşturmaya başlayın `StartTable` yöntem.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Tabloyu başlatmak için bir hücre eklemek gereklidir.

## Adım 4: Tablo Genelinde Biçimlendirmeyi Uygulayın

Tüm tabloyu etkileyen biçimlendirme uygulayabilirsiniz. Örneğin, sol girintiyi ayarlama:

```csharp
table.LeftIndent = 20.0;
```

## Adım 5: Başlık Satırını Biçimlendirin

Başlık satırının yüksekliğini, hizalamasını ve diğer özelliklerini ayarlayın.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

Bu adımda, arka plan rengini, yazı tipi boyutunu ve hizalamayı ayarlayarak başlık satırını öne çıkarıyoruz.

## Adım 6: Ek Başlık Hücreleri Ekle

Başlık satırına daha fazla hücre ekle:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Adım 7: Gövde Satırlarını Biçimlendirin

Başlığı ayarladıktan sonra tablonun gövdesini biçimlendirin:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Adım 8: Gövde Satırlarını Ekle

İçeriği olan gövde satırlarını ekleyin:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Ek satırlar için tekrarlayın:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Adım 9: Belgeyi Kaydedin

Son olarak belgeyi belirtilen dizine kaydedin:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Bu, biçimlendirilmiş tabloyu içeren bir Word belgesi oluşturacak ve kaydedecektir.

## Çözüm

İşte karşınızda! Bu adımları izleyerek, Aspose.Words for .NET kullanarak Word belgesinde iyi biçimlendirilmiş bir tablo oluşturabilirsiniz. Bu güçlü kütüphane, Word belgelerini programatik olarak yönetmenizi kolaylaştırarak size zaman ve emek kazandırır.

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, Word belgelerini programlı olarak oluşturmak, düzenlemek ve dönüştürmek için güçlü bir kütüphanedir.

### Farklı satırlar için farklı renkler kullanabilir miyim?
Evet, farklı satırlara veya hücrelere renkler de dahil olmak üzere farklı biçimlendirmeler uygulayabilirsiniz.

### Aspose.Words for .NET ücretsiz mi?
Aspose.Words for .NET ücretli bir kütüphanedir, ancak bir tane alabilirsiniz [ücretsiz deneme](https://releases.aspose.com/).

### Aspose.Words for .NET desteğini nasıl alabilirim?
Destek alabilirsiniz [Aspose topluluk forumları](https://forum.aspose.com/c/words/8).

### Aspose.Words for .NET ile başka türde belgeler oluşturabilir miyim?
Evet, Aspose.Words for .NET, PDF, HTML ve TXT dahil olmak üzere çeşitli belge biçimlerini destekler.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}