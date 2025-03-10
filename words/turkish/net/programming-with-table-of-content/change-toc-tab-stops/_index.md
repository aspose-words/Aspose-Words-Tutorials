---
title: Word Belgesinde Toc Sekmesi Duraklarını Değiştir
linktitle: Word Belgesinde Toc Sekmesi Duraklarını Değiştir
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word belgelerindeki TOC sekme duraklarını nasıl değiştireceğinizi öğrenin. Bu adım adım kılavuz, profesyonel görünümlü bir İçindekiler Tablosu oluşturmanıza yardımcı olacaktır.
weight: 10
url: /tr/net/programming-with-table-of-content/change-toc-tab-stops/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesinde Toc Sekmesi Duraklarını Değiştir

## giriiş

Word belgelerinizdeki İçindekiler Tablosunu (TOC) nasıl canlandıracağınızı hiç merak ettiniz mi? Belki de o sekme duraklarının profesyonel bir dokunuş için mükemmel bir şekilde hizalanmasını istiyorsunuz. Doğru yerdesiniz! Bugün, .NET için Aspose.Words kullanarak TOC sekme duraklarını nasıl değiştirebileceğinizi derinlemesine inceliyoruz. Burada kalın ve TOC'nizin şık ve düzenli görünmesi için gereken tüm bilgi birikimiyle ayrılacağınıza söz veriyorum.

## Ön koşullar

Başlamadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1.  Aspose.Words for .NET: Şunları yapabilirsiniz:[buradan indirin](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio veya herhangi bir C# uyumlu IDE.
3. Word Belgesi: Özellikle, İçindekiler tablosu içeren belge.

Hepsini anladın mı? Harika! Hadi başlayalım.

## Ad Alanlarını İçe Aktar

İlk önce, gerekli ad alanlarını içe aktarmanız gerekecek. Bu, bir projeye başlamadan önce araçlarınızı paketlemek gibidir.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Bu süreci basit, sindirilebilir adımlara bölelim. Belgeyi yükleme, TOC sekmesi duraklarını değiştirme ve güncellenen belgeyi kaydetme aşamalarını ele alacağız.

## Adım 1: Belgeyi Yükleyin

Neden? Değiştirmek istediğimiz TOC'yi içeren Word belgesine erişmemiz gerekiyor.

Nasıl? Başlamanız için işte basit bir kod parçası:

```csharp
// Belgelerinizin dizinine giden yol
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// İçindekiler tablosunu içeren belgeyi yükleyin
Document doc = new Document(dataDir + "Table of contents.docx");
```

Belgenizin bir pasta gibi olduğunu ve biraz krema eklemek üzere olduğumuzu düşünün. İlk adım, pastayı kutudan çıkarmaktır.

## Adım 2: İçindekiler Paragraflarını Belirleyin

Neden? İçindekiler bölümünü oluşturan paragrafları belirlememiz gerekiyor. 

Nasıl? Paragrafları dolaşın ve stillerini kontrol edin:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        // İçindekiler paragrafı bulundu
    }
}
```

Bunu arkadaşlarınızı bulmak için bir kalabalığı taramak olarak düşünün. Burada, TOC girişleri olarak biçimlendirilmiş paragraflar arıyoruz.

## Adım 3: Sekme Duraklarını Değiştirin

Neden? İşte sihir burada gerçekleşir. Sekme duraklarını değiştirmek TOC'nize daha temiz bir görünüm kazandırır.

Nasıl? Mevcut sekme durağını kaldırın ve değiştirilmiş bir konuma yenisini ekleyin:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        TabStop tab = para.ParagraphFormat.TabStops[0];
        para.ParagraphFormat.TabStops.RemoveByPosition(tab.Position);
        para.ParagraphFormat.TabStops.Add(tab.Position - 50, tab.Alignment, tab.Leader);
    }
}
```

Bu, oturma odanızdaki mobilyaları tam istediğiniz gibi hissedene kadar ayarlamak gibi. O sekme duraklarını mükemmelliğe ulaştırmak için ayarlıyoruz.

## Adım 4: Değiştirilen Belgeyi Kaydedin

Neden? Tüm sıkı çalışmanızın kaydedilmesini ve görüntülenebilmesini veya paylaşılabilmesini sağlamak için.

Nasıl? Orijinalini olduğu gibi korumak için belgeyi yeni bir adla kaydedin:

```csharp
// Değiştirilen belgeyi kaydet
doc.Save(dataDir + "WorkingWithTableOfContent.ChangeTocTabStops.docx");
```

Ve işte! İçindekiler tablonuz artık sekme duraklarını tam olarak istediğiniz yerde bulunduruyor.

## Çözüm

Aspose.Words for .NET kullanarak bir Word belgesinde TOC sekme duraklarını değiştirmek, parçalara ayırdığınızda basittir. Belgenizi yükleyerek, TOC paragraflarını belirleyerek, sekme duraklarını değiştirerek ve belgeyi kaydederek cilalı ve profesyonel bir görünüm elde edebilirsiniz. Unutmayın, pratik mükemmelleştirir, bu yüzden istediğiniz düzeni elde etmek için farklı sekme durağı konumlarını denemeye devam edin.

## SSS

### Farklı TOC seviyeleri için sekme duraklarını ayrı ayrı değiştirebilir miyim?
Evet yapabilirsiniz! Sadece her bir belirli TOC seviyesini (Toc1, Toc2, vb.) kontrol edin ve buna göre ayarlayın.

### Belgemde birden fazla İçindekiler tablosu varsa ne olur?
Kod, tüm İçindekiler tarzı paragrafları tarar, bu nedenle belgede bulunan tüm İçindekiler'i değiştirir.

### İçindekiler girişine birden fazla sekme durağı eklemek mümkün müdür?
 Kesinlikle! Ayarlayarak ihtiyaç duyduğunuz kadar sekme durağı ekleyebilirsiniz.`para.ParagraphFormat.TabStops` koleksiyon.

### Sekme durağı hizalamasını ve lider stilini değiştirebilir miyim?
Evet, yeni bir sekme durağı eklerken farklı hizalamalar ve lider stilleri belirleyebilirsiniz.

### Aspose.Words for .NET'i kullanmak için lisansa ihtiyacım var mı?
 Evet, Aspose.Words for .NET'i deneme süresinin ötesinde kullanmak için geçerli bir lisansa ihtiyacınız var. Bir tane alabilirsiniz[geçici lisans](https://purchase.aspose.com/temporary-license/) veya[bir tane satın al](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
