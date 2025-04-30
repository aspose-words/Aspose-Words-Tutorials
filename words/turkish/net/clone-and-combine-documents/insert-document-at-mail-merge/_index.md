---
"description": "Bu kapsamlı, adım adım eğitimde Aspose.Words for .NET kullanarak birleştirme alanlarına belgelerin nasıl ekleneceğini öğrenin."
"linktitle": "Belgeyi Posta Birleştirmede Ekle"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Belgeyi Posta Birleştirmede Ekle"
"url": "/tr/net/clone-and-combine-documents/insert-document-at-mail-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Belgeyi Posta Birleştirmede Ekle

## giriiş

Aspose.Words for .NET ile belge otomasyonu dünyasına hoş geldiniz! Bir posta birleştirme işlemi sırasında ana belgedeki belirli alanlara belgeleri dinamik olarak nasıl ekleyeceğinizi hiç merak ettiniz mi? Doğru yerdesiniz. Bu eğitim, Aspose.Words for .NET kullanarak belgeleri posta birleştirme alanlarına ekleme sürecinde adım adım size rehberlik edecektir. Her parçanın mükemmel bir şekilde yerine oturduğu bir bulmacayı bir araya getirmek gibidir. Hadi başlayalım!

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. Aspose.Words for .NET: Şunları yapabilirsiniz: [en son sürümü buradan indirin](https://releases.aspose.com/words/net/). Lisans satın almanız gerekiyorsa bunu yapabilirsiniz [Burada](https://purchase.aspose.com/buy)Alternatif olarak, bir tane alabilirsiniz [geçici lisans](https://purchase.aspose.com/temporary-license/) veya bir deneyin [ücretsiz deneme](https://releases.aspose.com/).
2. Geliştirme Ortamı: Visual Studio veya herhangi bir C# IDE.
3. Temel C# Bilgisi: C# programlamaya aşinalık bu eğitimi çok kolaylaştıracaktır.

## Ad Alanlarını İçe Aktar

İlk önce, gerekli ad alanlarını içe aktarmanız gerekecek. Bunlar projenizin yapı taşları gibidir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Süreci yönetilebilir adımlara bölelim. Her adım bir öncekinin üzerine inşa edilecek ve sizi eksiksiz bir çözüme götürecektir.

## Adım 1: Dizininizi Kurma

Belgeleri eklemeye başlamadan önce, belgeler dizininize giden yolu tanımlamanız gerekir. Belgeleriniz burada saklanır.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Adım 2: Ana Belgeyi Yükleme

Sonra, ana belgeyi yükleyeceksiniz. Bu belge, diğer belgelerin ekleneceği birleştirme alanlarını içerir.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Adım 3: Alan Birleştirme Geri Aramasını Ayarlama

Birleştirme işlemini yönetmek için bir geri çağırma işlevi ayarlamanız gerekir. Bu işlev, belirtilen birleştirme alanlarına belge eklemekten sorumlu olacaktır.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Adım 4: Posta Birleştirmeyi Çalıştırma

Şimdi posta birleştirmeyi yürütme zamanı. Sihir burada gerçekleşir. Birleştirme alanını ve bu alana eklenmesi gereken belgeyi belirteceksiniz.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Adım 5: Belgeyi Kaydetme

Posta birleştirme tamamlandıktan sonra, değiştirilen belgeyi kaydedeceksiniz. Bu yeni belge, eklenen içeriği tam istediğiniz yerde bulunduracaktır.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Adım 6: Geri Arama İşleyicisini Oluşturma

Geri çağırma işleyicisi, birleştirme alanı için özel işlem yapan bir sınıftır. Alan değerinde belirtilen belgeyi yükler ve geçerli birleştirme alanına ekler.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## Adım 7: Belgeyi Ekleme

Bu yöntem belirtilen belgeyi geçerli paragrafa veya tablo hücresine ekler.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## Çözüm

Ve işte oldu! Aspose.Words for .NET kullanarak bir posta birleştirme işlemi sırasında belgeleri belirli alanlara başarıyla eklediniz. Bu güçlü özellik, özellikle büyük miktarda belgeyle uğraşırken size bir ton zaman ve emek kazandırabilir. Bunu, sizin için tüm ağır işleri halleden kişisel bir asistanınız varmış gibi düşünün. O halde devam edin ve deneyin. İyi kodlamalar!

## SSS

### Farklı birleştirme alanlarına birden fazla belge ekleyebilir miyim?
Evet, yapabilirsiniz. Uygun birleştirme alanlarını ve karşılık gelen belge yollarını belirtmeniz yeterlidir. `MailMerge.Execute` yöntem.

### Eklenen belgeyi ana belgeden farklı bir biçimde biçimlendirmek mümkün müdür?
Kesinlikle! Şunu kullanabilirsiniz: `ImportFormatMode` parametre içinde `NodeImporter` Biçimlendirmeyi kontrol etmek için.

### Birleştirme alanı adı dinamik ise ne olur?
Dinamik birleştirme alan adlarını, geri çağırma işleyicisine parametre olarak geçirerek işleyebilirsiniz.

### Bu yöntemi farklı dosya formatlarında kullanabilir miyim?
Evet, Aspose.Words DOCX, PDF ve daha fazlası dahil olmak üzere çeşitli dosya formatlarını destekler.

### Belge ekleme işlemi sırasında oluşan hataları nasıl çözebilirim?
Oluşabilecek istisnaları yönetmek için geri çağırma işleyicinizde hata işlemeyi uygulayın.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}