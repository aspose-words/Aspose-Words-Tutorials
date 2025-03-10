---
title: Word Belgesinde Yer İşaretlerini Gizle'yi Göster
linktitle: Word Belgesinde Yer İşaretlerini Gizle'yi Göster
second_title: Aspose.Words Belge İşleme API'si
description: Adım adım kılavuzumuzla Aspose.Words for .NET kullanarak bir Word belgesindeki yer işaretlerini dinamik olarak nasıl göstereceğinizi veya gizleyeceğinizi öğrenin. Geliştiriciler için mükemmel.
weight: 10
url: /tr/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesinde Yer İşaretlerini Gizle'yi Göster

## giriiş

Hiç Word belgenizin belirli bölümlerini dinamik olarak gizlemeye veya göstermeye ihtiyaç duyduğunuzu fark ettiniz mi? Şanslısın! Aspose.Words for .NET ile belgelerinizdeki yer imlerine eklenmiş içeriğin görünürlüğünü kolayca yönetebilirsiniz. Bu eğitim, Aspose.Words for .NET kullanarak bir Word belgesindeki yer işaretlerini gösterme ve gizleme sürecinde size yol gösterecektir. Kodu adım adım inceleyeceğiz, bu nedenle ister deneyimli bir geliştirici olun, ister yeni başlayan biri olun, bu kılavuzu takip etmenin kolay olduğunu göreceksiniz.

## Önkoşullar

Koda dalmadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1.  Aspose.Words for .NET: Aspose.Words for .NET kütüphanesinin kurulu olduğundan emin olun. Değilse indirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio benzeri bir IDE.
3. Temel C# Bilgisi: C# programlamaya aşina olmak faydalı olacaktır.
4. Bir Word Belgesi: Yer işaretlerini içeren örnek bir Word belgesi.

## Ad Alanlarını İçe Aktar

Kodla başlamadan önce gerekli ad alanlarını içe aktarmanız gerekir. C# dosyanızın başına aşağıdakini ekleyin:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## 1. Adım: Belgenizi Yükleyin

Öncelikle yer işaretlerini içeren Word belgesini yüklemeniz gerekir. Bunu nasıl yapabileceğiniz aşağıda açıklanmıştır:

```csharp
// Belgeler dizininin yolu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Açıklama

- dataDir: Bu, Word belgenizin bulunduğu dizin yoludur.
-  Belge belgesi: Bu, yeni bir örneğini başlatır.`Document` belirttiğiniz dosyayla sınıf.

## 2. Adım: Yer İşaretli İçeriği Gösterme veya Gizleme

Daha sonra, yer imlerine eklenen içeriği göstermek veya gizlemek için bir yöntem tanımlayacağız. İşte tam yöntem:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD yer imi}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Açıklama

- Yer imi bm: Belgeden yer imini getirir.
- DocumentBuilder oluşturucu: Belgede gezinmeye ve belgeyi değiştirmeye yardımcı olur.
- Alan alanı: Yer iminin durumunu kontrol etmek için bir IF alanı ekler.
- Node currentNode: Alanın başlangıcını ve bitişini bulmak için düğümler arasında geçiş yapar.

## Adım 3: Göster/Gizle İşlevini Çalıştırın

 Şimdi aramanız gerekiyor`ShowHideBookmarkedContent` belgeyi, yer imi adını ve görünürlük bayrağını iletme yöntemi:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Açıklama

- doc: Belge nesneniz.
- "MyBookmark1": Göstermek/gizlemek istediğiniz yer iminin adı.
- false: Görünürlük bayrağı (göstermek için true, gizlemek için false).

## 4. Adım: Belgenizi Kaydedin

Son olarak değiştirilen belgeyi kaydedin:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Açıklama

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": Değişikliklerin kaydedileceği yeni belgenin yolu ve adı.

## Çözüm

İşte buyur! Aspose.Words for .NET'i kullanarak bir Word belgesindeki yer işaretlerini nasıl gösterip gizleyeceğinizi başarıyla öğrendiniz. Bu teknik, koşullu içeriğe sahip belgeleri dinamik olarak oluşturmak için inanılmaz derecede yararlı olabilir.

## SSS'ler

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, geliştiricilerin Word belgelerini programlı olarak oluşturmasına, değiştirmesine ve dönüştürmesine olanak tanıyan güçlü bir belge işleme kitaplığıdır.

### Aspose.Words for .NET'i nasıl edinebilirim?
 Aspose.Words for .NET'i şu adresten indirebilirsiniz:[Burada](https://releases.aspose.com/words/net/). Ücretsiz deneme sürümü de mevcuttur.

### Bu yöntemi diğer yer imi türleri için kullanabilir miyim?
Evet, bu yöntem, Word belgenizdeki herhangi bir yer iminin görünürlüğünü yönetecek şekilde uyarlanabilir.

### Belgem belirtilen yer işaretini içermiyorsa ne olur?
Yer imi mevcut değilse, yöntem bir hata verecektir. Göstermeye/gizlemeye çalışmadan önce yer iminin mevcut olduğundan emin olun.

### Sorunla karşılaşırsam nasıl destek alabilirim?
 Aspose topluluğundan destek alabilirsiniz[Burada](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
