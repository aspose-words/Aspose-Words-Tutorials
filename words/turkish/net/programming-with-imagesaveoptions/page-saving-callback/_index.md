---
"description": "Ayrıntılı, adım adım kılavuzumuzla Aspose.Words for .NET'i kullanarak bir Word belgesinin her sayfasını ayrı bir PNG resmi olarak kaydetmeyi öğrenin."
"linktitle": "Sayfa Kaydetme Geri Araması"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Sayfa Kaydetme Geri Araması"
"url": "/tr/net/programming-with-imagesaveoptions/page-saving-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sayfa Kaydetme Geri Araması

## giriiş

Merhaba! Bir Word belgesinin her sayfasını ayrı resimler olarak kaydetme ihtiyacı hissettiniz mi hiç? Belki büyük bir raporu kolayca sindirilebilir görsellere bölmek istiyorsunuz veya belki de önizleme için küçük resimler oluşturmanız gerekiyor. Nedeniniz ne olursa olsun, .NET için Aspose.Words kullanmak bu görevi kolaylaştırır. Bu kılavuzda, bir belgenin her sayfasını ayrı bir PNG resmi olarak kaydetmek için bir sayfa kaydetme geri araması ayarlama sürecinde size yol göstereceğiz. Hemen başlayalım!

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. Aspose.Words for .NET: Eğer henüz yapmadıysanız, buradan indirip kurun [Burada](https://releases.aspose.com/words/net/).
2. Visual Studio: Herhangi bir sürüm işe yarar, ancak bu kılavuz için Visual Studio 2019'u kullanacağım.
3. Temel C# Bilgisi: Takip edebilmek için temel C# bilgisine sahip olmanız gerekir.

## Ad Alanlarını İçe Aktar

Öncelikle gerekli ad alanlarını içe aktarmamız gerekiyor. Bu, her seferinde tam ad alanını yazmadan gerekli sınıflara ve yöntemlere erişmemize yardımcı olur.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Adım 1: Belge Dizininizi Ayarlayın

Tamam, belge dizininize giden yolu tanımlayarak başlayalım. Giriş Word belgenizin bulunduğu ve çıktı resimlerinin kaydedileceği yer burasıdır.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Adım 2: Belgenizi Yükleyin

Sonra, işlemek istediğiniz belgeyi yükleyeceğiz. Belgenizin ("Rendering.docx") belirtilen dizinde olduğundan emin olun.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Adım 3: Görüntü Kaydetme Seçeneklerini Yapılandırın

Resimleri kaydetme seçeneklerini yapılandırmamız gerekiyor. Bu durumda sayfaları PNG dosyaları olarak kaydediyoruz.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

Burada, `PageSet` kaydedilecek sayfa aralığını belirtir ve `PageSavingCallback` özel geri çağırma sınıfımıza işaret eder.

## Adım 4: Sayfa Kaydetme Geri Aramasını Uygulayın

Şimdi, her sayfanın nasıl kaydedileceğini işleyen geri çağırma sınıfını uygulayalım.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

Bu sınıf şunları uygular: `IPageSavingCallback` arayüz ve içinde `PageSaving` yöntemi ile, kaydedilen her sayfa için adlandırma desenini tanımlarız.

## Adım 5: Belgeyi Resim Olarak Kaydedin

Son olarak yapılandırdığımız seçenekleri kullanarak belgeyi kaydediyoruz.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Çözüm

Ve işte oldu! Aspose.Words for .NET kullanarak bir Word belgesinin her sayfasını ayrı bir PNG resmi olarak kaydetmek için bir sayfa kaydetme geri aramasını başarıyla ayarladınız. Bu teknik, sayfa önizlemeleri oluşturmaktan raporlar için ayrı sayfa resimleri oluşturmaya kadar çeşitli uygulamalar için inanılmaz derecede faydalıdır. 

Keyifli kodlamalar!

## SSS

### Sayfaları PNG dışındaki formatlarda kaydedebilir miyim?  
Evet, sayfaları JPEG, BMP ve TIFF gibi farklı formatlarda kaydedebilirsiniz. `SaveFormat` içinde `ImageSaveOptions`.

### Ya sadece belirli sayfaları kaydetmek istersem?  
Kaydetmek istediğiniz sayfaları ayarlayarak belirtebilirsiniz. `PageSet` parametre içinde `ImageSaveOptions`.

### Görüntü kalitesini özelleştirmek mümkün mü?  
Kesinlikle! Şu gibi özellikler ayarlayabilirsiniz: `ImageSaveOptions.JpegQuality` Çıktı görüntülerinin kalitesini kontrol etmek için.

### Büyük belgeleri nasıl verimli bir şekilde yönetebilirim?  
Büyük belgelerde, bellek kullanımını etkili bir şekilde yönetmek için sayfaları toplu olarak işlemeyi düşünün.

### Aspose.Words for .NET hakkında daha fazla bilgiyi nerede bulabilirim?  
Şuna bir göz atın: [belgeleme](https://reference.aspose.com/words/net/) Kapsamlı kılavuzlar ve örnekler için.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}