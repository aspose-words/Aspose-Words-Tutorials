---
"description": "Aspose.Words for .NET kullanarak Word belgelerini HTML olarak kaydederken CSS ve yazı tipleri gibi kaynakları nasıl dışa aktaracağınızı öğrenin. Adım adım kılavuzumuzu izleyin."
"linktitle": "İhracat Kaynakları"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "İhracat Kaynakları"
"url": "/tr/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# İhracat Kaynakları

## giriiş

Merhaba, teknoloji meraklısı arkadaşım! Word belgelerini HTML'ye dönüştürmeniz gerektiyse doğru yerdesiniz. Bugün, Aspose.Words for .NET'in harika dünyasına dalıyoruz. Bu güçlü kütüphane, Word belgeleriyle programatik olarak çalışmayı çok kolaylaştırıyor. Bu eğitimde, Aspose.Words for .NET kullanarak bir Word belgesini HTML olarak kaydederken yazı tipleri ve CSS gibi kaynakları dışa aktarma adımlarını ele alacağız. Eğlenceli ve bilgilendirici bir yolculuğa hazır olun!

## Ön koşullar

Koda dalmadan önce, başlamak için ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım. İşte hızlı bir kontrol listesi:

1. Visual Studio: Makinenizde Visual Studio'nun yüklü olduğundan emin olun. Bunu şuradan indirebilirsiniz: [Visual Studio web sitesi](https://visualstudio.microsoft.com/).
2. Aspose.Words for .NET: Aspose.Words for .NET kütüphanesine ihtiyacınız olacak. Eğer henüz almadıysanız, şu adresten ücretsiz deneme sürümünü edinin: [Aspose Sürümleri](https://releases.aspose.com/words/net/) veya buradan satın alın [Aspose Mağazası](https://purchase.aspose.com/buy).
3. Temel C# Bilgisi: C# hakkında temel bir anlayışa sahip olmak, kod örneklerini takip etmenize yardımcı olacaktır.

Hepsini anladınız mı? Harika! Gerekli ad alanlarını içe aktarmaya geçelim.

## Ad Alanlarını İçe Aktar

Aspose.Words for .NET'i kullanmak için projenize ilgili ad alanlarını eklemeniz gerekir. Bunu şu şekilde yapabilirsiniz:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Bu ad alanları, eğitimimizde kullanacağımız Aspose.Words sınıflarına ve metotlarına erişim için çok önemlidir.

Bir Word belgesini HTML olarak kaydederken kaynakları dışa aktarma sürecini parçalara ayıralım. Adım adım ilerleyeceğiz, böylece takip etmesi kolay olacak.

## Adım 1: Belge Dizininizi Ayarlayın

İlk önce, belgeler dizininize giden yolu belirtmeniz gerekir. Word belgenizin bulunduğu ve HTML dosyasının kaydedileceği yer burasıdır.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Yer değiştirmek `"YOUR DOCUMENT DIRECTORY"` dizininize giden gerçek yol ile.

## Adım 2: Word Belgesini Yükleyin

Sonra, HTML'ye dönüştürmek istediğiniz Word belgesini yükleyelim. Bu eğitim için, adlı bir belge kullanacağız `Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Bu kod satırı belgeyi belirtilen dizinden yükler.

## Adım 3: HTML Kaydetme Seçeneklerini Yapılandırın

CSS ve yazı tipleri gibi kaynakları dışa aktarmak için, şunu yapılandırmanız gerekir: `HtmlSaveOptions`Bu adım, HTML çıktınızın iyi yapılandırılmış olmasını ve gerekli kaynakları içermesini sağlamak için çok önemlidir.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/kaynaklar"
};
```

Her seçeneğin ne işe yaradığını inceleyelim:
- `CssStyleSheetType = CssStyleSheetType.External`: Bu seçenek, CSS stillerinin harici bir stil sayfasına kaydedilmesi gerektiğini belirtir.
- `ExportFontResources = true`: Bu, yazı tipi kaynaklarının dışa aktarılmasını sağlar.
- `ResourceFolder = dataDir + "Resources"`: Kaynakların (yazı tipleri ve CSS dosyaları gibi) kaydedileceği yerel klasörü belirtir.
- `ResourceFolderAlias = "http://example.com/resources"`: HTML dosyasında kullanılacak kaynak klasörü için bir takma ad belirler.

## Adım 4: Belgeyi HTML olarak kaydedin

Kaydetme seçenekleri yapılandırıldıktan sonra son adım belgeyi bir HTML dosyası olarak kaydetmektir. Bunu nasıl yapacağınız aşağıda açıklanmıştır:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Bu kod satırı, belgeyi dışa aktarılan kaynaklarla birlikte HTML formatında kaydeder.

## Çözüm

Ve işte oldu! Aspose.Words for .NET kullanarak bir Word belgesini HTML olarak kaydederken kaynakları başarıyla dışa aktardınız. Bu güçlü kütüphaneyle, Word belgelerini programatik olarak yönetmek çocuk oyuncağı haline geliyor. İster bir web uygulaması üzerinde çalışıyor olun, ister sadece belgeleri çevrimdışı kullanım için dönüştürmeniz gereksin, Aspose.Words sizin için her şeyi yapar.

## SSS

### Resimleri fontlar ve CSS ile birlikte dışarı aktarabilir miyim?
Evet, yapabilirsiniz! Aspose.Words for .NET görüntüleri dışa aktarmayı da destekler. Sadece yapılandırmayı unutmayın `HtmlSaveOptions` buna göre.

### Harici bir stil sayfası kullanmak yerine CSS'yi gömmenin bir yolu var mı?
Kesinlikle. Ayarlayabilirsiniz `CssStyleSheetType` ile `CssStyleSheetType.Embedded` eğer gömülü stilleri tercih ediyorsanız.

### Çıktı HTML dosyasının adını nasıl özelleştirebilirim?
İstediğiniz herhangi bir dosya adını belirtebilirsiniz. `doc.Save` yöntem. Örneğin, `doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Aspose.Words HTML dışında başka formatları da destekliyor mu?
Evet, PDF, DOCX, TXT ve daha fazlası dahil olmak üzere çeşitli formatları destekler. Şuraya göz atın: [belgeleme](https://reference.aspose.com/words/net/) Tam liste için.

### Daha fazla destek ve kaynağı nereden alabilirim?
Daha fazla yardım için şu adresi ziyaret edin: [Aspose.Words Destek Forumu](https://forum.aspose.com/c/words/8)Ayrıca ayrıntılı dokümanları ve örnekleri şu adreste bulabilirsiniz: [Aspose web sitesi](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}