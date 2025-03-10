---
title: Grup Şekli Ekle
linktitle: Grup Şekli Ekle
second_title: Aspose.Words Belge İşleme API'si
description: Bu kapsamlı, adım adım eğitimle Aspose.Words for .NET'i kullanarak Word belgelerine grup şekillerinin nasıl ekleneceğini öğrenin.
weight: 10
url: /tr/net/programming-with-shapes/add-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Grup Şekli Ekle

## giriiş

Zengin görsel öğelere sahip karmaşık belgeler oluşturmak bazen göz korkutucu bir görev olabilir, özellikle de grup şekilleriyle uğraşırken. Ama korkmayın! Aspose.Words for .NET bu süreci basitleştirir ve çocuk oyuncağı haline getirir. Bu eğitimde, Word belgelerinize grup şekilleri ekleme adımlarında size yol göstereceğiz. Başlamaya hazır mısınız? Hadi başlayalım!

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  Aspose.Words for .NET: Bunu şu adresten indirebilirsiniz:[Aspose sürüm sayfası](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio veya .NET ile uyumlu herhangi bir IDE.
3. C# Temel Anlayışı: C# programlamaya aşinalık bir avantajdır.

## Ad Alanlarını İçe Aktar

Başlamak için, projemize gerekli ad alanlarını içe aktarmamız gerekir. Bu ad alanları, Word belgelerini Aspose.Words ile işlemek için gereken sınıflara ve yöntemlere erişim sağlar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Adım 1: Belgeyi Başlatın

İlk önce ilk şeyler, yeni bir Word belgesi başlatalım. Bunu, grup şekillerimizi ekleyeceğimiz boş bir tuval oluşturmak olarak düşünün.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

 Burada,`EnsureMinimum()` belge için gereken en az düğüm kümesini ekler.

## Adım 2: GroupShape Nesnesini Oluşturun

 Daha sonra, bir tane oluşturmamız gerekiyor`GroupShape`nesne. Bu nesne, diğer şekiller için bir kap görevi görecek ve onları bir arada gruplamamıza olanak tanıyacak.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Adım 3: GroupShape'e Şekiller Ekleyin

 Şimdi, bireysel şekilleri ekleyelim`GroupShape` konteyner. Bir vurgu kenarlık şekliyle başlayacağız ve ardından bir eylem düğmesi şekli ekleyeceğiz.

### Vurgu Kenarlık Şekli Ekleme

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

 Bu kod parçacığı, 100 birim genişliğinde ve yüksekliğinde bir vurgu kenarlığı şekli oluşturur ve bunu`GroupShape`.

### Bir Eylem Düğmesi Şekli Ekleme

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

 Burada bir eylem düğmesi şekli oluşturuyoruz, konumlandırıyoruz ve bunu sayfamıza ekliyoruz.`GroupShape`.

## Adım 4: GroupShape Boyutlarını Tanımlayın

 Şekillerimizin gruba iyi uyduğundan emin olmak için, şekillerimizin boyutlarını ayarlamamız gerekir.`GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

 Bu, genişliğini ve yüksekliğini tanımlar`GroupShape` 200 birim olarak belirler ve koordinat boyutunu buna göre ayarlar.

## Adım 5: GroupShape'i Belgeye Ekleyin

 Şimdi, bizimkini ekleyelim`GroupShape` kullanarak belgeye girin`DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` Belgeye şekiller de dahil olmak üzere düğümler eklemenin kolay bir yolunu sağlar.

## Adım 6: Belgeyi Kaydedin

Son olarak belgeyi belirttiğiniz dizine kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

Ve işte oldu! Grup şekillerinin bulunduğu belgeniz hazır.

## Çözüm

Word belgelerinize grup şekilleri eklemek karmaşık bir süreç olmak zorunda değil. Aspose.Words for .NET ile, şekilleri kolaylıkla oluşturabilir ve düzenleyebilir, belgelerinizi görsel olarak daha çekici ve işlevsel hale getirebilirsiniz. Bu eğitimde özetlenen adımları izleyin ve kısa sürede profesyonel olun!

## SSS

### Bir GroupShape'e ikiden fazla şekil ekleyebilir miyim?
 Evet, ihtiyacınız olduğu kadar çok şekil ekleyebilirsiniz.`GroupShape` Sadece şunu kullanın`AppendChild` Her şekil için bir yöntem.

### Bir GroupShape içindeki şekilleri biçimlendirmek mümkün müdür?
 Kesinlikle! Her şekil, mevcut özellikler kullanılarak ayrı ayrı şekillendirilebilir.`Shape` sınıf.

### GroupShape'i belge içerisinde nasıl konumlandırabilirim?
 Konumlandırabilirsiniz`GroupShape` ayarlayarak`Left` Ve`Top` özellikler.

### GroupShape içindeki şekillere metin ekleyebilir miyim?
 Evet, şekillere metin ekleyebilirsiniz.`AppendChild` bir yöntem eklemek için`Paragraph` içeren`Run` metinli düğümler.

### Kullanıcı girdisine göre şekilleri dinamik olarak gruplamak mümkün müdür?
Evet, kullanıcı girdisine göre özellikleri ve yöntemleri buna göre ayarlayarak şekilleri dinamik olarak oluşturabilir ve gruplayabilirsiniz.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
