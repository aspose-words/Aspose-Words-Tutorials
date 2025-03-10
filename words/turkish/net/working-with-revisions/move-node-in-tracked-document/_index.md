---
title: İzlenen Belgede Düğümü Taşı
linktitle: İzlenen Belgede Düğümü Taşı
second_title: Aspose.Words Belge İşleme API'si
description: Ayrıntılı, adım adım kılavuzumuzla Aspose.Words for .NET kullanarak izlenen bir Word belgesindeki düğümleri nasıl taşıyacağınızı öğrenin. Geliştiriciler için mükemmel.
weight: 10
url: /tr/net/working-with-revisions/move-node-in-tracked-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# İzlenen Belgede Düğümü Taşı

## giriiş

Merhaba, Aspose.Words meraklıları! Revizyonları izlerken bir Word belgesinde bir düğümü taşımanız gerektiyse doğru yerdesiniz. Bugün, bunu .NET için Aspose.Words kullanarak nasıl başaracağınıza derinlemesine bakıyoruz. Sadece adım adım süreci öğrenmekle kalmayacak, aynı zamanda belge düzenlemenizi sorunsuz ve verimli hale getirmek için bazı ipuçları ve püf noktaları da edineceksiniz.

## Ön koşullar

Ellerimizi biraz kodla kirletmeden önce, ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

-  Aspose.Words for .NET: İndirin[Burada](https://releases.aspose.com/words/net/).
- .NET Ortamı: Uyumlu bir .NET geliştirme ortamı kurduğunuzdan emin olun.
- Temel C# Bilgisi: Bu eğitimde C# hakkında temel bir anlayışa sahip olduğunuzu varsayıyoruz.

Her şeyi anladınız mı? Harika! İçe aktarmamız gereken ad alanlarına geçelim.

## Ad Alanlarını İçe Aktar

İlk önce, gerekli ad alanlarını içe aktarmamız gerekiyor. Bunlar Aspose.Words ile çalışmak ve belge düğümlerini yönetmek için önemlidir.

```csharp
using Aspose.Words;
using System;
```

Tamam, süreci yönetilebilir adımlara bölelim. Her adım, her noktada ne olduğunu anlamanızı sağlamak için ayrıntılı olarak açıklanacaktır.

## Adım 1: Belgeyi Başlatın

 Başlamak için yeni bir belge başlatmamız ve bir`DocumentBuilder` birkaç paragraf eklemek için.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Birkaç paragraf ekleniyor
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// İlk paragraf sayısını kontrol edin
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Adım 2: Revizyonları İzlemeye Başlayın

Sonra, revizyonları izlemeye başlamamız gerekiyor. Bu, belgede yapılan değişiklikleri görmemizi sağladığı için önemlidir.

```csharp
// Revizyonları izlemeye başla
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## Adım 3: Düğümleri Taşı

Şimdi görevimizin temel kısmına geliyoruz: bir düğümü bir yerden başka bir yere taşımak. Üçüncü paragrafı taşıyacağız ve ilk paragraftan önce yerleştireceğiz.

```csharp
// Taşınacak düğümü ve bitiş aralığını tanımlayın
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// Düğümleri tanımlanan aralıkta taşıyın
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## Adım 4: Revizyonları İzlemeyi Durdurun

Düğümleri taşıdıktan sonra revizyonları izlemeyi bırakmamız gerekiyor.

```csharp
// Revizyonları izlemeyi durdur
doc.StopTrackRevisions();
```

## Adım 5: Belgeyi Kaydedin

Son olarak, değiştirdiğimiz belgeyi belirtilen dizine kaydedelim.

```csharp
// Değiştirilen belgeyi kaydet
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// Son paragraf sayısını çıktı olarak ver
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Çözüm

Ve işte karşınızda! Aspose.Words for .NET kullanarak izlenen bir belgedeki bir düğümü başarıyla taşıdınız. Bu güçlü kütüphane, Word belgelerini programatik olarak yönetmenizi kolaylaştırır. İster oluşturuyor, ister düzenliyor veya değişiklikleri izliyor olun, Aspose.Words sizin için her şeyi yapar. O halde devam edin ve deneyin. İyi kodlamalar!

## SSS

### Aspose.Words for .NET nedir?

Aspose.Words for .NET, Word belgeleriyle programatik olarak çalışmak için bir sınıf kütüphanesidir. Geliştiricilerin .NET uygulamaları içinde Word belgeleri oluşturmasına, düzenlemesine, dönüştürmesine ve yazdırmasına olanak tanır.

### Aspose.Words kullanarak bir Word belgesindeki revizyonları nasıl takip edebilirim?

 Düzeltmeleri izlemek için şunu kullanın:`StartTrackRevisions` yöntem üzerinde`Document` nesne. Bu, belgede yapılan tüm değişiklikleri göstererek revizyon izlemeyi etkinleştirecektir.

### Aspose.Words'de birden fazla düğümü taşıyabilir miyim?

Evet, üzerlerinde yineleme yaparak ve şu yöntemleri kullanarak birden fazla düğümü taşıyabilirsiniz:`InsertBefore` veya`InsertAfter` onları istenilen yere yerleştirmek.

### Aspose.Words'de revizyonları izlemeyi nasıl durdurabilirim?

 Kullanın`StopTrackRevisions` yöntem üzerinde`Document` revizyonların izlenmesini durdurmaya yönelik nesne.

### Aspose.Words for .NET hakkında daha fazla dokümanı nerede bulabilirim?

 Ayrıntılı dokümanları bulabilirsiniz[Burada](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
