---
title: Yatay Birleştirme
linktitle: Yatay Birleştirme
second_title: Aspose.Words Belge İşleme API'si
description: Bu ayrıntılı, adım adım eğitimle Aspose.Words for .NET'i kullanarak Word belgesindeki hücreleri yatay olarak nasıl birleştireceğinizi öğrenin.
weight: 10
url: /tr/net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yatay Birleştirme

## giriiş

Merhaba! .NET için Aspose.Words dünyasına dalmaya hazır mısınız? Bugün, çok kullanışlı bir özelliği ele alacağız: tablolarda yatay birleştirme. Kulağa biraz teknik gelebilir, ancak endişelenmeyin, arkanızdayım. Bu eğitimin sonunda, Word belgelerinizdeki hücreleri programatik olarak birleştirmede uzman olacaksınız. O halde, kollarımızı sıvayalım ve başlayalım!

## Ön koşullar

Ayrıntılara girmeden önce, elinizde olması gereken birkaç şey var:

1. Aspose.Words for .NET Kütüphanesi: Eğer henüz yapmadıysanız, Aspose.Words for .NET kütüphanesini indirin. Bunu alabilirsiniz[Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio gibi uygun bir geliştirme ortamının kurulu olduğundan emin olun.
3. Temel C# Bilgisi: C# programlamaya dair temel bir anlayışa sahip olmak faydalı olacaktır.

Bunları hallettikten sonra artık hazırsınız!

## Ad Alanlarını İçe Aktar

Koda dalmadan önce, gerekli ad alanlarının içe aktarıldığından emin olalım. C# projenizde şunları eklediğinizden emin olun:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Tamam, Aspose.Words for .NET kullanarak bir Word belgesinde tablo hücrelerini yatay olarak birleştirme sürecini inceleyelim.

## Adım 1: Belgenizi Ayarlama

 İlk önce, yeni bir Word belgesi oluşturmamız ve başlatmamız gerekiyor`DocumentBuilder`:

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Bu kod parçacığı yeni bir belge kurar ve hazırlar`DocumentBuilder` eylem için.

## Adım 2: İlk Hücreyi Ekleme

Daha sonra ilk hücreyi ekleyerek yatay birleştirme için işaretliyoruz:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

 Burada yeni bir hücre ekliyoruz ve hücrenin`HorizontalMerge`mülk`CellMerge.First`Bu hücrenin birleştirilmiş hücre dizisinin başlangıcı olduğunu gösterir.

## Adım 3: Birleştirilmiş Hücreyi Ekleme

Şimdi bir önceki hücreyle birleştirilecek hücreyi ekleyelim:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

 Bu hücre, kullanılarak önceki hücreyle birleştirilecek şekilde ayarlanır`CellMerge.Previous` Satırı nasıl sonlandırdığımıza dikkat edin`builder.EndRow()`.

## Adım 4: Birleştirilmemiş Hücreleri Ekleme

Farkı göstermek için, birleştirilmemiş birkaç hücre ekleyelim:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Burada, yatay birleştirme olmadan iki hücre ekliyoruz. Bu, hücrelerin birleştirilmiş bir dizinin parçası olmadıklarında nasıl davrandıklarını gösterir.

## Adım 5: Tablonun Tamamlanması

Son olarak tabloyu sonlandırıp belgeyi kaydediyoruz:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Bu kod parçacığı tabloyu tamamlar ve belgeyi belirtilen dizine kaydeder.

## Çözüm

İşte oldu! Aspose.Words for .NET kullanarak bir Word belgesindeki hücreleri yatay olarak birleştirme sanatında ustalaştınız. Bu adımları izleyerek, karmaşık tablo yapılarını kolaylıkla oluşturabilirsiniz. Belgelerinizi ihtiyaç duyduğunuz kadar dinamik ve esnek hale getirmek için Aspose.Words'ün yeteneklerini denemeye ve keşfetmeye devam edin. İyi kodlamalar!

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, geliştiricilerin .NET uygulamalarında Word belgelerini programlı bir şekilde oluşturmalarına, düzenlemelerine ve değiştirmelerine olanak tanıyan güçlü bir kütüphanedir.

### Aspose.Words for .NET ile hücreleri dikey olarak birleştirebilir miyim?
 Evet, hücreleri dikey olarak da birleştirebilirsiniz.`CellFormat.VerticalMerge` mülk.

### Aspose.Words for .NET'i kullanmak ücretsiz mi?
 Aspose.Words for .NET ücretsiz deneme sunuyor, ancak tam işlevsellik için bir lisans satın almanız gerekecek. Geçici bir lisans alabilirsiniz[Burada](https://purchase.aspose.com/temporary-license/).

### Aspose.Words for .NET hakkında daha fazla bilgi nasıl edinebilirim?
 Ayrıntılı belgeleri inceleyebilirsiniz[Burada](https://reference.aspose.com/words/net/).

### Aspose.Words for .NET için desteği nereden alabilirim?
 Herhangi bir sorunuz veya sorununuz varsa Aspose destek forumunu ziyaret edebilirsiniz[Burada](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
