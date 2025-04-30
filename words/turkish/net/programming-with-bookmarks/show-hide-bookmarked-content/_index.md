---
"description": "Bu ayrıntılı, adım adım kılavuzla Aspose.Words for .NET'i kullanarak Word belgelerinde yer imlerine eklenen içeriğin nasıl gösterileceğini ve gizleneceğini öğrenin."
"linktitle": "Word Belgesinde İşaretlenmiş İçeriği Göster Gizle"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Word Belgesinde İşaretlenmiş İçeriği Göster Gizle"
"url": "/tr/net/programming-with-bookmarks/show-hide-bookmarked-content/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesinde İşaretlenmiş İçeriği Göster Gizle

## giriiş

Aspose.Words for .NET ile belge düzenleme dünyasına dalmaya hazır mısınız? İster belge görevlerini otomatikleştirmek isteyen bir geliştirici olun, ister Word dosyalarını programatik olarak yönetme konusunda meraklı biri olun, doğru yerdesiniz. Bugün, Aspose.Words for .NET kullanarak bir Word belgesinde yer imlerine eklenen içeriğin nasıl gösterileceğini ve gizleneceğini inceleyeceğiz. Bu adım adım kılavuz, yer imlerine dayalı içerik görünürlüğünü kontrol etmede sizi uzman yapacaktır. Başlayalım!

## Ön koşullar

Ayrıntılara girmeden önce ihtiyacınız olacak birkaç şey var:

1. Visual Studio: .NET ile uyumlu herhangi bir sürüm.
2. Aspose.Words for .NET: İndirin [Burada](https://releases.aspose.com/words/net/).
3. C#'ın Temel Anlayışı: Basit bir "Merhaba Dünya" programı yazabiliyorsanız, hazırsınız demektir.
4. Yer İmleri İçeren Bir Word Belgesi: Bu eğitimde yer imleri içeren bir örnek belge kullanacağız.

## Ad Alanlarını İçe Aktar

İlk önce, gerekli ad alanlarını içe aktaralım. Bu, görevimiz için ihtiyacımız olan tüm araçlara sahip olmamızı sağlar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Bu ad alanlarını yerleştirdiğimize göre yolculuğumuza başlamaya hazırız.

## Adım 1: Projenizi Kurma

Tamam, Visual Studio'da projemizi kurarak başlayalım.

### Yeni Bir Proje Oluştur

Visual Studio'yu açın ve yeni bir Konsol Uygulaması (.NET Core) projesi oluşturun. "BookmarkVisibilityManager" gibi akılda kalıcı bir isim verin.

### .NET için Aspose.Words'ü ekleyin

Projenize Aspose.Words for .NET eklemeniz gerekecek. Bunu NuGet Paket Yöneticisi aracılığıyla yapabilirsiniz.

1. Araçlar > NuGet Paket Yöneticisi > Çözüm için NuGet Paketlerini Yönet'e gidin.
2. "Aspose.Words" ifadesini arayın.
3. Paketi kurun.

Harika! Artık projemiz kurulduğuna göre, belgemizi yüklemeye geçelim.

## Adım 2: Belgeyi Yükleme

Yer imlerini içeren Word belgesini yüklememiz gerekiyor. Bu eğitim için "Bookmarks.docx" adlı örnek bir belge kullanacağız.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

Bu kod parçacığı belge dizininize giden yolu ayarlar ve belgeyi şuraya yükler: `doc` nesne.

## Adım 3: Yer İşaretli İçeriği Göster/Gizle

Şimdi eğlenceli kısma geliyoruz - yer imlerine göre içeriği gösterme veya gizleme. Adı verilen bir yöntem oluşturacağız `ShowHideBookmarkedContent` Bunu halletmek için.

İşte yer imlerine eklenen içeriğin görünürlüğünü değiştirecek yöntem:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### Yöntemin Ayrıntılı Açıklaması

- Yer İşareti Alma: `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` yer imini getirir.
- Düğüm Gezinmesi: Yer imi içindeki düğümleri geziyoruz.
- Görünürlük Geçişi: Düğüm bir `Run` (birbirini izleyen bir metin dizisi), bunu ayarlıyoruz `Hidden` mülk.

## Adım 4: Yöntemin Uygulanması

Yöntemimiz hazır olduğuna göre, bunu yer imlerine göre içerik göstermek veya gizlemek için uygulayalım.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Bu kod satırı "MyBookmark1" adlı yer iminin içeriğini gizleyecektir.

## Adım 5: Belgeyi Kaydetme

Son olarak değiştirdiğimiz belgeyi kaydedelim.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Bu, belgeyi yaptığımız değişikliklerle kaydeder.

## Çözüm

Ve işte karşınızda! Aspose.Words for .NET kullanarak Word belgesinde yer imli içerikleri nasıl göstereceğinizi ve gizleyeceğinizi öğrendiniz. Bu güçlü araç, ister raporları otomatikleştirin, ister şablonlar oluşturun veya sadece Word dosyalarıyla uğraşın, belge düzenlemeyi çocuk oyuncağı haline getirir. İyi kodlamalar!

## SSS

### Birden fazla yer imini aynı anda açıp kapatabilir miyim?
Evet, arayabilirsiniz `ShowHideBookmarkedContent` Geçiş yapmak istediğiniz her yer imi için bir yöntem.

### İçeriği gizlemek belgenin yapısını etkiler mi?
Hayır, içeriği gizlemek yalnızca görünürlüğünü etkiler. İçerik belgede kalır.

### Bu yöntemi diğer içerik türleri için de kullanabilir miyim?
Bu yöntem özellikle metin çalıştırmalarını değiştirir. Diğer içerik türleri için düğüm geçiş mantığını değiştirmeniz gerekir.

### Aspose.Words for .NET ücretsiz mi?
Aspose.Words ücretsiz deneme sunuyor [Burada](https://releases.aspose.com/), ancak üretim kullanımı için tam lisans gereklidir. Bunu satın alabilirsiniz [Burada](https://purchase.aspose.com/buy).

### Sorun yaşarsam nasıl destek alabilirim?
Aspose topluluğundan destek alabilirsiniz [Burada](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}