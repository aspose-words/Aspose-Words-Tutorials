---
title: İç içe geçmiş tablo
linktitle: İç içe geçmiş tablo
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET'i kullanarak Word belgelerinde iç içe tablolar oluşturmayı rehberimizle öğrenin. Karmaşık belge düzenlerini programatik olarak oluşturmak için mükemmeldir.
weight: 10
url: /tr/net/programming-with-tables/nested-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# İç içe geçmiş tablo

## giriiş

Hiç Word belgesinde programatik olarak iç içe geçmiş bir tablo oluşturma ihtiyacı hissettiniz mi? İster raporlar, ister faturalar veya ayrıntılı bir tablo yapısı gerektiren herhangi bir belge üretiyor olun, Aspose.Words for .NET en iyi arkadaşınız olabilir. Bu eğitimde, Aspose.Words for .NET kullanarak Word belgelerinde iç içe geçmiş tablolar oluşturma sürecine dalacağız. Ön koşullardan son kod uygulamasına kadar her şeyi ele alacağız. Hadi başlayalım!

## Ön koşullar

Koda geçmeden önce ihtiyacınız olacak birkaç şey var:

-  Aspose.Words for .NET: Buradan indirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio veya herhangi bir C# IDE.
- C# Temel Bilgileri: C# sözdizimi ve kavramlarının anlaşılması.

Devam etmeden önce bunların ayarlandığından emin olun.

## Ad Alanlarını İçe Aktar

İlk önce gerekli ad alanlarını içe aktaralım. Bu ad alanları Word belgeleriyle çalışmak için gereken sınıflara ve yöntemlere erişmemizi sağlayacak.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Adım 1: Belgeyi ve Belge Oluşturucuyu Başlatın

 Başlamak için yeni bir Word belgesi oluşturacağız ve başlatacağız`DocumentBuilder` Tabloyu oluşturmamıza yardımcı olacak nesne.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 2: Dış Tabloyu Oluşturun

Şimdi dış tabloyu oluşturalım. İlk hücreyi ekleyerek ve ona biraz içerik ekleyerek başlayacağız.

### Adım 2.1: Dış Tablonun İlk Hücresini Yerleştirin

```csharp
Cell cell = builder.InsertCell();
builder.Writeln("Outer Table Cell 1");
```

### Adım 2.2: Dış Tablonun İkinci Hücresini Yerleştirin

Daha sonra ikinci hücreyi ekleyeceğiz ve biraz içerik ekleyeceğiz.

```csharp
builder.InsertCell();
builder.Writeln("Outer Table Cell 2");
```

### Adım 2.3: Dış Tabloyu Sonlandırın

Tabloyu burada sonlandırmak önemlidir çünkü bu sayede iç içe geçmiş tabloyu ilk hücreden başlatabiliriz.

```csharp
builder.EndTable();
```

## Adım 3: İç Tabloyu Oluşturun

İç içe geçmiş bir tablo oluşturmak için, imleci dış tablonun ilk hücresine getirmemiz ve ardından iç tabloyu oluşturmaya başlamamız gerekir.

### Adım 3.1: Dış Tablonun İlk Hücresine Git

```csharp
builder.MoveTo(cell.FirstParagraph);
```

### Adım 3.2: İç Tablonun İlk Hücresini Ekleyin

Şimdi iç tablonun ilk hücresini ekleyelim ve biraz içerik ekleyelim.

```csharp
builder.InsertCell();
builder.Writeln("Inner Table Cell 1");
```

### Adım 3.3: İç Tablonun İkinci Hücresini Ekleyin

Son olarak ikinci hücreyi ekleyeceğiz ve biraz içerik ekleyeceğiz.

```csharp
builder.InsertCell();
builder.Writeln("Inner Table Cell 2");
```

### Adım 3.4: İç Tabloyu Sonlandırın

İç tabloyu sonlandırarak bitiriyoruz.

```csharp
builder.EndTable();
```

## Adım 4: Belgeyi Kaydedin

Son adım belgeyi belirttiğiniz dizine kaydetmektir.

```csharp
doc.Save(dataDir + "WorkingWithTables.NestedTable.docx");
```

## Çözüm

İşte karşınızda! Aspose.Words for .NET kullanarak bir Word belgesinde iç içe geçmiş bir tabloyu başarıyla oluşturdunuz. Bu güçlü kütüphane, Word belgelerini programatik olarak yönetmeyi inanılmaz derecede kolaylaştırır. İster karmaşık raporlar, ister basit tablolar üretiyor olun, Aspose.Words for .NET sizin için her şeyi yapar.

## SSS

### İç içe tablo nedir?

İç içe geçmiş tablo, bir tablonun içindeki tablodur. Formlar veya ayrıntılı veri sunumları gibi belgeler içinde karmaşık düzenler oluşturmak için kullanılır.

### .NET için Aspose.Words'ü neden kullanmalısınız?

Aspose.Words for .NET, Word belgelerini programlı olarak oluşturmak, değiştirmek ve dönüştürmek için sağlam bir özellik seti sunar ve bu da onu geliştiriciler için ideal bir seçim haline getirir.

### Daha fazla düzeyde iç içe tablo ekleyebilir miyim?

Evet, geçerli tabloyu sonlandırıp bir hücre içinde yeni bir tablo başlatma işlemini tekrarlayarak birden fazla düzeyde iç içe geçmiş tablo oluşturabilirsiniz.

### Aspose.Words for .NET Word'ün tüm sürümleriyle uyumlu mudur?

Aspose.Words for .NET, DOC, DOCX, RTF ve daha fazlası dahil olmak üzere çok çeşitli Word belge formatlarıyla uyumludur.

### Aspose.Words for .NET desteğini nasıl alabilirim?

 Destek alabilirsiniz[Aspose.Words Destek Forumu](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
