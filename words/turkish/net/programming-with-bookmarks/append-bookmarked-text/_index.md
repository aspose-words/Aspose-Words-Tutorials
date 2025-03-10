---
title: Word Belgesinde İşaretli Metni Ekle
linktitle: Word Belgesinde İşaretli Metni Ekle
second_title: Aspose.Words Belge İşleme API'si
description: Bu adım adım kılavuzla Aspose.Words for .NET kullanarak Word belgesine yer imli metin eklemeyi öğrenin. Geliştiriciler için mükemmel.
weight: 10
url: /tr/net/programming-with-bookmarks/append-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesinde İşaretli Metni Ekle

## giriiş

Merhaba! Hiç Word belgesinde yer imlerine eklenmiş bir bölümden metin eklemeyi denediniz ve zor buldunuz mu? Şanslısınız! Bu eğitim, .NET için Aspose.Words'ü kullanarak süreci adım adım anlatacak. Kolayca takip edebilmeniz için bunu basit adımlara böleceğiz. Hadi başlayalım ve yer imlerine eklenmiş metni bir profesyonel gibi ekleyelim!

## Ön koşullar

Başlamadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

-  Aspose.Words for .NET: Yüklü olduğundan emin olun. Değilse,[buradan indirin](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio gibi herhangi bir .NET geliştirme ortamı.
- Temel C# Bilgisi: Temel C# programlama kavramlarını anlamak faydalı olacaktır.
- Yer İşaretleri Olan Word Belgesi: Metin eklemek için kullanacağımız, yer işaretleri olan bir Word belgesi.

## Ad Alanlarını İçe Aktar

İlk önce, gerekli ad alanlarını içe aktaralım. Bu, ihtiyacımız olan tüm araçların parmaklarımızın ucunda olmasını sağlayacaktır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Örneği ayrıntılı adımlara bölelim.

## Adım 1: Belgeyi Yükleyin ve Değişkenleri Başlatın

Tamam, Word belgemizi yükleyerek ve ihtiyacımız olan değişkenleri başlatarak başlayalım.

```csharp
// Kaynak ve hedef belgeleri yükleyin.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Belge içe aktarıcısını başlatın.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Kaynak belgede yer imini bulun.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Adım 2: Başlangıç ve Bitiş Paragraflarını Belirleyin

Şimdi, yer işaretinin başladığı ve bittiği paragrafları bulalım. Bu çok önemlidir çünkü metni bu sınırlar içinde ele almamız gerekir.

```csharp
// Bu, yer iminin başlangıcını içeren paragraftır.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Bu, yer iminin sonunu içeren paragraftır.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## Adım 3: Paragraf Ebeveynlerini Doğrulayın

Başlangıç ve bitiş paragraflarının aynı ebeveyne sahip olduğundan emin olmalıyız. Bu, işleri basit tutmak için basit bir senaryodur.

```csharp
// Kendimizi makul derecede basit bir senaryoyla sınırlayalım.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## Adım 4: Durdurulacak Düğümü Belirleyin

Sonra, metni kopyalamayı durduracağımız düğümü belirlememiz gerekiyor. Bu, paragraf sonundan hemen sonraki düğüm olacak.

```csharp
// Başlangıç paragrafından son paragrafa kadar (ve dahil) tüm paragrafları kopyalamak istiyoruz.
// dolayısıyla duracağımız nokta paragrafın sonundan bir sonraki noktadır.
Node endNode = endPara.NextSibling;
```

## Adım 5: Hedef Belgeye İşaretlenmiş Metni Ekleyin

Son olarak, başlangıç paragrafından bitiş paragrafından sonraki düğüme kadar düğümler arasında dolaşalım ve bunları hedef belgeye ekleyelim.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Bu, geçerli düğümün bir kopyasını oluşturur ve onu (geçerli hale getirir) bağlamda içe aktarır
    // Hedef belgenin. İçe aktarma, stilleri ve liste tanımlayıcılarını doğru şekilde ayarlamak anlamına gelir.
    Node newNode = importer.ImportNode(curNode, true);

    // İçe aktarılan düğümü hedef belgeye ekleyin.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Hedef belgeyi eklenen metinle birlikte kaydedin.
dstDoc.Save("appended_document.docx");
```

## Çözüm

Ve işte oldu! Aspose.Words for .NET kullanarak Word belgesinde yer imli bir bölümden metni başarıyla eklediniz. Bu güçlü araç belge düzenlemeyi çocuk oyuncağı haline getiriyor ve artık elinizde bir numara daha var. İyi kodlamalar!

## SSS

### Birden fazla yer iminden aynı anda metin ekleyebilir miyim?
Evet, her bir yer imi için işlemi tekrarlayabilir ve metni buna göre ekleyebilirsiniz.

### Başlangıç ve bitiş paragraflarının farklı ebeveynleri varsa ne olur?
Mevcut örnek, aynı ebeveyne sahip olduklarını varsayar. Farklı ebeveynler için daha karmaşık bir işleme ihtiyaç vardır.

### Eklenen metnin orijinal biçimini koruyabilir miyim?
 Kesinlikle!`ImportFormatMode.KeepSourceFormatting` orijinal biçimlendirmenin korunmasını sağlar.

### Hedef belgede belirli bir konuma metin eklemek mümkün müdür?
Evet, hedef belgedeki istediğiniz düğüme giderek metni herhangi bir konuma ekleyebilirsiniz.

### Yer imlerinden yeni bir bölüme metin eklemem gerekirse ne olur?
Hedef belgede yeni bir bölüm oluşturabilir ve metni oraya ekleyebilirsiniz.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
