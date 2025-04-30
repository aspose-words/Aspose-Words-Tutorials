---
"description": "Bu kapsamlı kılavuzla Aspose.Words for .NET kullanarak Word belgelerindeki şekil revizyonlarını nasıl ele alacağınızı öğrenin. Değişiklikleri izleme, şekil ekleme ve daha fazlasında ustalaşın."
"linktitle": "Şekil Revizyonu"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Şekil Revizyonu"
"url": "/tr/net/working-with-revisions/shape-revision/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Şekil Revizyonu

## giriiş

Word belgelerini programatik olarak düzenlemek, özellikle şekilleri ele almak söz konusu olduğunda zorlu bir görev olabilir. İster raporlar oluşturun, ister şablonlar tasarlayın veya sadece belge oluşturmayı otomatikleştirin, şekil revizyonlarını izleme ve yönetme yeteneği çok önemlidir. Aspose.Words for .NET, bu süreci sorunsuz ve verimli hale getirmek için güçlü bir API sunar. Bu eğitimde, Word belgelerindeki şekilleri revize etmenin ayrıntılarına dalacağız ve belgelerinizi kolayca yönetmeniz için gereken araçlara ve bilgiye sahip olmanızı sağlayacağız.

## Ön koşullar

Koda dalmadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

- Aspose.Words for .NET: Aspose.Words kütüphanesinin yüklü olduğundan emin olun. [buradan indirin](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio gibi bir geliştirme ortamı kurmuş olmanız gerekir.
- C# Temel Anlayışı: C# programlama dili ve nesne yönelimli programlamanın temel kavramlarına aşinalık.
- Word Belgesi: Üzerinde çalışabileceğiniz bir Word belgesi veya eğitim sırasında kendiniz bir tane oluşturabilirsiniz.

## Ad Alanlarını İçe Aktar

Öncelikle gerekli ad alanlarını içe aktaralım. Bunlar bize Word belgelerini ve şekillerini işlemek için gereken sınıflara ve yöntemlere erişim sağlayacaktır.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Adım 1: Belge Dizininizi Ayarlama

Şekillerle çalışmaya başlamadan önce, belge dizinimize giden yolu tanımlamamız gerekir. Değiştirilmiş belgelerimizi buraya kaydedeceğiz.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Adım 2: Yeni Bir Belge Oluşturma

Şekilleri ekleyeceğimiz ve revize edeceğimiz yeni bir Word belgesi oluşturalım.

```csharp
Document doc = new Document();
```

## Adım 3: Satır İçi Şekil Ekleme

Belgemize revizyonları izlemeden satır içi bir şekil ekleyerek başlayacağız. Satır içi şekil, metinle birlikte akan bir şekildir.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Adım 4: Revizyonları İzlemeye Başlayın

Belgemizdeki değişiklikleri izlemek için revizyon izlemeyi etkinleştirmemiz gerekir. Bu, şekillerde yapılan değişiklikleri belirlemek için önemlidir.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Adım 5: Revizyonlarla Başka Bir Şekil Ekleme

Artık revizyon takibi etkinleştirildiğine göre, başka bir şekil ekleyelim. Bu sefer, tüm değişiklikler takip edilecek.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Adım 6: Şekilleri Alma ve Değiştirme

Belgedeki tüm şekilleri alabilir ve gerektiği gibi değiştirebiliriz. Burada şekilleri alacağız ve ilkini kaldıracağız.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Adım 7: Belgeyi Kaydetme

Değişikliklerimizi yaptıktan sonra belgeyi kaydetmemiz gerekir. Bu, tüm revizyonların ve değişikliklerin saklanmasını sağlar.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Adım 8: Şekil Taşıma Revizyonlarını Yönetme

Bir şekil taşındığında, Aspose.Words bunu bir revizyon olarak izler. Bu, şeklin iki örneği olacağı anlamına gelir: biri orijinal konumunda ve biri yeni konumunda.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Çözüm

Ve işte karşınızda! Aspose.Words for .NET kullanarak Word belgelerindeki şekil revizyonlarını nasıl ele alacağınızı başarıyla öğrendiniz. İster belge şablonlarını yönetiyor, ister raporları otomatikleştiriyor veya sadece değişiklikleri takip ediyor olun, bu beceriler paha biçilmezdir. Bu adım adım kılavuzu izleyerek, yalnızca temelleri öğrenmekle kalmadınız, aynı zamanda daha gelişmiş belge işleme tekniklerine ilişkin içgörü de kazandınız.

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, geliştiricilerin C# kullanarak Word belgelerini programlı bir şekilde oluşturmalarına, değiştirmelerine ve dönüştürmelerine olanak tanıyan güçlü bir kütüphanedir.

### Word belgesindeki diğer öğelerde yapılan değişiklikleri takip edebilir miyim?
Evet, Aspose.Words for .NET metin, tablolar ve daha fazlası dahil olmak üzere çeşitli öğelerdeki değişikliklerin izlenmesini destekler.

### Aspose.Words for .NET'in ücretsiz deneme sürümünü nasıl edinebilirim?
Aspose.Words for .NET'in ücretsiz deneme sürümünü edinebilirsiniz [Burada](https://releases.aspose.com/).

### Revizyonları programatik olarak kabul etmek veya reddetmek mümkün müdür?
Evet, Aspose.Words for .NET, revizyonları programlı olarak kabul etmek veya reddetmek için yöntemler sağlar.

### Aspose.Words for .NET'i C# dışındaki diğer .NET dilleriyle birlikte kullanabilir miyim?
Kesinlikle! Aspose.Words for .NET, VB.NET ve F# dahil olmak üzere herhangi bir .NET diliyle kullanılabilir.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}