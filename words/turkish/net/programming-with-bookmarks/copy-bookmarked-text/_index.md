---
title: Word Belgesinde İşaretlenmiş Metni Kopyala
linktitle: Word Belgesinde İşaretlenmiş Metni Kopyala
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word belgeleri arasında yer imli metni zahmetsizce kopyalayın. Bu adım adım kılavuzla nasıl yapacağınızı öğrenin.
weight: 10
url: /tr/net/programming-with-bookmarks/copy-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesinde İşaretlenmiş Metni Kopyala

## giriiş

Belirli bölümleri bir Word belgesinden diğerine kopyalamanız gerektiğini hiç fark ettiniz mi? Şanslısınız! Bu eğitimde, Aspose.Words for .NET kullanarak yer imli metni bir Word belgesinden diğerine nasıl kopyalayacağınızı göstereceğiz. İster dinamik bir rapor oluşturun ister belge oluşturmayı otomatikleştirin, bu kılavuz sizin için süreci basitleştirecektir.

## Ön koşullar

Başlamadan önce, aşağıdakilere sahip olduğunuzdan emin olun:

-  Aspose.Words for .NET Kütüphanesi: Buradan indirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio veya herhangi bir .NET geliştirme ortamı.
- Temel C# Bilgisi: C# programlama ve .NET framework'üne aşinalık.

## Ad Alanlarını İçe Aktar

Başlamak için, projenize gerekli ad alanlarının aktarıldığından emin olun:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Adım 1: Kaynak Belgeyi Yükle

İlk önce kopyalamak istediğiniz yer imli metni içeren kaynak belgeyi yüklemeniz gerekiyor.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

 Burada,`dataDir` belge dizininize giden yoldur ve`Bookmarks.docx` kaynak belgedir.

## Adım 2: Yer İşaretini Tanımlayın

Daha sonra kaynak belgeden kopyalamak istediğiniz yer imini belirleyin.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

 Yer değiştirmek`"MyBookmark1"` yer iminizin gerçek adıyla.

## Adım 3: Hedef Belgeyi Oluşturun

Şimdi yer imlerine eklenen metnin kopyalanacağı yeni bir belge oluşturun.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Adım 4: Yer İşaretli İçeriği İçe Aktar

 Stillerin ve biçimlendirmenin korunduğundan emin olmak için şunu kullanın:`NodeImporter` Yer imlerine eklenen içeriği kaynak belgeden hedef belgeye aktarmak için.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Adım 5: AppendBookmarkedText Yöntemini Tanımlayın

İşte sihir burada gerçekleşiyor. Yer imlerine eklenen metnin kopyalanmasını işleyecek bir yöntem tanımlayın:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## Adım 6: Hedef Belgeyi Kaydedin

Son olarak kopyalanan içeriği doğrulamak için hedef belgeyi kaydedin.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Çözüm

Ve işte bu kadar! Aspose.Words for .NET kullanarak yer imli metni bir Word belgesinden diğerine başarıyla kopyaladınız. Bu yöntem, belge düzenleme görevlerini otomatikleştirmek, iş akışınızı daha verimli ve akıcı hale getirmek için güçlüdür.

## SSS

### Birden fazla yer imini aynı anda kopyalayabilir miyim?
Evet, birden fazla yer imi arasında dolaşabilir ve her birini kopyalamak için aynı yöntemi kullanabilirsiniz.

### Yer imi bulunamazsa ne olur?
 The`Range.Bookmarks` mülk geri dönecek`null`, bu nedenle istisnalardan kaçınmak için bu durumu ele aldığınızdan emin olun.

### Orijinal yer iminin biçimini koruyabilir miyim?
 Kesinlikle! Kullanarak`ImportFormatMode.KeepSourceFormatting` orijinal biçimlendirmenin korunmasını sağlar.

### Yer imlerine eklenen metnin boyutunda bir sınır var mı?
Belirli bir sınır yoktur, ancak çok büyük belgelerde performans değişebilir.

### Farklı Word belge biçimleri arasında metin kopyalayabilir miyim?
Evet, Aspose.Words çeşitli Word formatlarını destekler ve yöntem bu formatlarda çalışır.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
