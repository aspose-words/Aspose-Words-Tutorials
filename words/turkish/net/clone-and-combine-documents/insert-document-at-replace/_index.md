---
"description": "Ayrıntılı, adım adım kılavuzumuzla Aspose.Words for .NET kullanarak bir Word belgesini diğerine sorunsuz bir şekilde nasıl ekleyeceğinizi öğrenin. Belge işlemeyi kolaylaştırmak isteyen geliştiriciler için mükemmeldir."
"linktitle": "Değiştir'de Belge Ekle"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Değiştir'de Belge Ekle"
"url": "/tr/net/clone-and-combine-documents/insert-document-at-replace/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Değiştir'de Belge Ekle

## giriiş

Merhaba, belge ustaları! Kendinizi hiç bir Word belgesini diğerine sorunsuz bir şekilde nasıl ekleyeceğinizi anlamaya çalışırken kodların içinde buldunuz mu? Korkmayın, çünkü bugün bu görevi kolaylaştırmak için .NET için Aspose.Words dünyasına dalıyoruz. Bu güçlü kütüphaneyi kullanarak bul ve değiştir işlemi sırasında belirli noktalara belge ekleme konusunda ayrıntılı, adım adım bir kılavuzda ilerleyeceğiz. Bir Aspose.Words sihirbazı olmaya hazır mısınız? Hadi başlayalım!

## Ön koşullar

Koda geçmeden önce, yerinde olması gereken birkaç şey var:

- Visual Studio: Makinenizde Visual Studio'nun yüklü olduğundan emin olun. Eğer henüz yüklü değilse, şuradan indirebilirsiniz: [Burada](https://visualstudio.microsoft.com/).
- .NET için Aspose.Words: Aspose.Words kütüphanesine ihtiyacınız olacak. Bunu şuradan edinebilirsiniz: [Aspose web sitesi](https://releases.aspose.com/words/net/).
- Temel C# Bilgisi: C# ve .NET hakkında temel bir anlayışa sahip olmak bu eğitimi takip etmenize yardımcı olacaktır.

Tamam, bunları aradan çıkardığımıza göre, biraz kodla işimize bakalım!

## Ad Alanlarını İçe Aktar

İlk önce, Aspose.Words ile çalışmak için gerekli ad alanlarını içe aktarmamız gerekiyor. Bu, bir projeye başlamadan önce tüm araçlarınızı toplamak gibidir. C# dosyanızın en üstüne şu using yönergelerini ekleyin:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Artık ön koşullarımız hazır olduğuna göre, süreci küçük parçalara bölelim. Her adım kritik öneme sahiptir ve bizi hedefimize yaklaştıracaktır.

## Adım 1: Belgeler Dizinini Ayarlama

Öncelikle belgelerimizin saklandığı dizini belirtmemiz gerekiyor. Bu, büyük gösteriden önce sahneyi hazırlamak gibidir.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Yer değiştirmek `"YOUR DOCUMENT DIRECTORY"` dizininize giden yol ile. Belgelerinizin yaşayacağı ve nefes alacağı yer burasıdır.

## Adım 2: Ana Belgeyi Yükleyin

Sonra, içine başka bir belge eklemek istediğimiz ana belgeyi yükleriz. Bunu, tüm eylemin gerçekleşeceği ana sahnemiz olarak düşünün.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Bu kod belirtilen dizinden ana belgeyi yükler.

## Adım 3: Bul ve Değiştir Seçeneklerini Ayarlayın

Belgemizi eklemek istediğimiz belirli konumu bulmak için bul ve değiştir işlevini kullanırız. Bu, yeni eklememiz için tam noktayı bulmak için bir harita kullanmaya benzer.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Burada yönü geriye doğru ayarlıyoruz ve daha sonra tanımlayacağımız özel bir geri çağırma işleyicisi belirliyoruz.

## Adım 4: Değiştirme İşlemini Gerçekleştirin

Şimdi, ana belgemize belirli bir yer tutucu metni aramasını ve onu hiçbir şeyle değiştirmesini söylerken, başka bir belge eklemek için özel geri aramamızı kullanıyoruz.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Bu kod bul ve değiştir işlemini gerçekleştirir ve ardından güncellenen belgeyi kaydeder.

## Adım 5: Özel Bir Değiştirme Geri Çağırma İşleyicisi Oluşturun

Özel geri çağırma işleyicimiz sihrin gerçekleştiği yerdir. Bu işleyici, bul ve değiştir işlemi sırasında belge eklemenin nasıl gerçekleştirileceğini tanımlayacaktır.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // Eşleşme metnini içeren paragraftan sonra bir belge ekleyin.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // Eşleşen metni içeren paragrafı kaldırın.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

Burada eklenecek belgeyi yüklüyoruz ve ardından eklemeyi gerçekleştirmek için bir yardımcı metodu çağırıyoruz.

## Adım 6: Belge Ekleme Yöntemini Tanımlayın

Bulmacamızın son parçası, belgeyi belirtilen yere ekleyen yöntemdir.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // Ekleme hedefinin Paragraf mı yoksa Tablo mu olduğunu kontrol edin
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // Kaynak belgeden düğümleri içe aktarmak için bir NodeImporter oluşturun
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // Kaynak belgenin bölümlerindeki tüm blok düzeyindeki düğümler arasında döngü oluştur
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // Bir bölümün son boş paragrafını atla
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // Düğümü hedefe aktarın ve ekleyin
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

Bu yöntem, eklenecek düğümlerin belgeden içe aktarılması ve ana belgede doğru noktaya yerleştirilmesiyle ilgilenir.

## Çözüm

İşte karşınızda! Aspose.Words for .NET kullanarak bir belgeyi diğerine eklemek için kapsamlı bir kılavuz. Bu adımları izleyerek, belge birleştirme ve düzenleme görevlerini kolayca otomatikleştirebilirsiniz. İster bir belge yönetim sistemi oluşturuyor olun, ister yalnızca belge işleme iş akışınızı düzene sokmanız gereksin, Aspose.Words sizin güvenilir yardımcınızdır.

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, Word belgelerini programatik olarak düzenlemek için güçlü bir kütüphanedir. Word belgelerini kolaylıkla oluşturmanıza, değiştirmenize, dönüştürmenize ve işlemenize olanak tanır.

### Birden fazla belgeyi aynı anda ekleyebilir miyim?
Evet, bir belge koleksiyonu üzerinde yineleme yaparak birden fazla eklemeyi işleyecek şekilde geri çağırma işleyicisini değiştirebilirsiniz.

### Ücretsiz deneme imkanı var mı?
Kesinlikle! Ücretsiz deneme sürümünü şuradan indirebilirsiniz: [Burada](https://releases.aspose.com/).

### Aspose.Words için nasıl destek alabilirim?
Destek almak için şu adresi ziyaret edebilirsiniz: [Aspose.Words forumu](https://forum.aspose.com/c/words/8).

### Eklediğim belgenin formatını koruyabilir miyim?
Evet, `NodeImporter` sınıfı, düğümleri bir belgeden diğerine aktarırken biçimlendirmenin nasıl işleneceğini belirtmenize olanak tanır.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}