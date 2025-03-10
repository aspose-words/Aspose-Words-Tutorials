---
title: Dipnot ve Sonnot Pozisyonunu Ayarla
linktitle: Dipnot ve Son Not Pozisyonunu Ayarla
second_title: Aspose.Words Belge İşleme API'si
description: Bu ayrıntılı adım adım kılavuzla Aspose.Words for .NET'i kullanarak Word belgelerinde dipnot ve sonnot konumlarının nasıl ayarlanacağını öğrenin.
weight: 10
url: /tr/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dipnot ve Sonnot Pozisyonunu Ayarla

## giriiş

Word belgeleriyle çalışıyorsanız ve dipnotları ve son notları etkili bir şekilde yönetmeniz gerekiyorsa, Aspose.Words for .NET sizin için en iyi kütüphanedir. Bu eğitim, Aspose.Words for .NET kullanarak bir Word belgesinde dipnot ve son not konumlarını ayarlama konusunda size yol gösterecektir. Takip etmeyi ve uygulamayı kolaylaştırmak için her adımı parçalara ayıracağız.

## Ön koşullar

Eğitime başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

-  Aspose.Words for .NET Kütüphanesi: Buradan indirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
- Visual Studio: Güncel herhangi bir sürüm sorunsuz çalışacaktır.
- Temel C# Bilgisi: Temelleri anlamak, konuyu daha kolay takip etmenize yardımcı olacaktır.

## Ad Alanlarını İçe Aktar

Öncelikle C# projenize gerekli namespace'leri import edin:

```csharp
using System;
using Aspose.Words;
```

## Adım 1: Word Belgesini Yükleyin

Başlamak için Word belgenizi Aspose.Words Belge nesnesine yüklemeniz gerekir. Bu, belgenin içeriğini düzenlemenize olanak tanır.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

Bu kodda şunu değiştirin:`"YOUR DOCUMENT DIRECTORY"` Belgenizin bulunduğu gerçek yol ile.

## Adım 2: Dipnot Pozisyonunu Ayarlayın

Sonra, dipnotların konumunu ayarlayacaksınız. Aspose.Words for .NET, dipnotları sayfanın altına veya metnin altına yerleştirmenize olanak tanır.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

 Burada, dipnotların metnin altında görünmesini ayarladık. Eğer sayfanın altında olmasını tercih ediyorsanız, şunu kullanın:`FootnotePosition.BottomOfPage`.

## Adım 3: Son Not Konumunu Ayarlayın

Benzer şekilde, dipnotların konumunu ayarlayabilirsiniz. Dipnotlar bölümün sonunda veya belgenin sonunda konumlandırılabilir.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

 Bu örnekte, dipnotlar her bölümün sonuna yerleştirilir. Bunları belgenin sonuna yerleştirmek için şunu kullanın:`EndnotePosition.EndOfDocument`.

## Adım 4: Belgeyi Kaydedin

Son olarak, değişiklikleri uygulamak için belgeyi kaydedin. Çıktı belgesi için doğru dosya yolunu ve adını belirttiğinizden emin olun.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

Bu satır değiştirilen belgeyi belirttiğiniz dizine kaydeder.

## Çözüm

Aspose.Words for .NET kullanarak Word belgelerinde dipnot ve sonnot konumlarını ayarlamak, adımları öğrendikten sonra basittir. Bu kılavuzu izleyerek, dipnotların ve sonnotların tam olarak istediğiniz yere konumlandırılmasını sağlayarak belgelerinizi ihtiyaçlarınıza göre özelleştirebilirsiniz.

## SSS

### Bireysel dipnotlar veya sonnotlar için farklı konumlar belirleyebilir miyim?

Hayır, Aspose.Words for .NET bir belgedeki tüm dipnotların ve son notların konumunu aynı şekilde ayarlar.

### Aspose.Words for .NET Word belgelerinin tüm sürümleriyle uyumlu mudur?

Evet, Aspose.Words for .NET, DOC, DOCX, RTF ve daha fazlası dahil olmak üzere çok çeşitli Word belge biçimlerini destekler.

### Aspose.Words for .NET'i diğer programlama dilleriyle birlikte kullanabilir miyim?

Aspose.Words for .NET, .NET uygulamaları için tasarlanmıştır, ancak C#, VB.NET gibi .NET destekli herhangi bir dille kullanabilirsiniz.

### Aspose.Words for .NET için ücretsiz deneme sürümü mevcut mu?

 Evet, ücretsiz deneme alabilirsiniz[Burada](https://releases.aspose.com/).

### Aspose.Words for .NET için daha detaylı dokümanları nerede bulabilirim?

 Ayrıntılı dokümantasyon mevcuttur[Burada](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
