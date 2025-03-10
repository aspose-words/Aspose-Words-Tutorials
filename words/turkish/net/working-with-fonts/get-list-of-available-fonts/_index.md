---
title: Mevcut Yazı Tiplerinin Listesini Alın
linktitle: Mevcut Yazı Tiplerinin Listesini Alın
second_title: Aspose.Words Belge İşleme API'si
description: Bu detaylı adım adım eğitimde Aspose.Words for .NET kullanarak kullanılabilir yazı tiplerinin listesini nasıl alacağınızı keşfedin. Yazı tipi yönetimi becerilerinizi artırın.
weight: 10
url: /tr/net/working-with-fonts/get-list-of-available-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mevcut Yazı Tiplerinin Listesini Alın

## giriiş

Word belgelerinizdeki yazı tiplerini yönetmekte zorlanıyor musunuz? Eğer bir .NET geliştiricisiyseniz, Aspose.Words for .NET sizi kurtarmak için burada! Bu güçlü kütüphane, yalnızca Word belgelerini programatik olarak oluşturmanıza ve düzenlemenize yardımcı olmakla kalmaz, aynı zamanda kapsamlı yazı tipi yönetimi yetenekleri de sunar. Bu kılavuzda, Aspose.Words for .NET kullanarak kullanılabilir yazı tiplerinin bir listesini nasıl alacağınıza dair adım adım bir eğitimde size yol göstereceğiz. Kolayca takip edebilmeniz için bunu sindirilebilir adımlara böleceğiz. Hadi, başlayalım ve yazı tipi yönetimini çocuk oyuncağı haline getirelim!

## Ön koşullar

Başlamadan önce ihtiyacınız olacak birkaç şey var:

-  Aspose.Words for .NET: Aspose.Words for .NET kütüphanesinin yüklü olduğundan emin olun. Buradan indirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
- Visual Studio: Bu örnekte geliştirme ortamı olarak Visual Studio kullanılmıştır.
- .NET Framework: Bilgisayarınızda .NET Framework'ün yüklü olduğundan emin olun.
- Belge Dizini: Belgelerinizin saklandığı dizin yolu.

## Ad Alanlarını İçe Aktar

Öncelikle gerekli namespace'leri projenize aktarın:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Adım 1: Yazı Tipi Ayarlarını Başlatın

İlk adım font ayarlarını başlatmaktır. Bu, belgeleriniz için font kaynaklarını yönetmenize olanak tanır.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: Bu sınıf, yazı tipi değiştirme ve yazı tipi kaynakları için ayarları belirtmek için kullanılır.
- fontSources: Mevcut font ayarlarından mevcut font kaynaklarının bir listesini oluşturuyoruz.

## Adım 2: Belge Dizinini Tanımlayın

Sonra, belge dizininize giden yolu belirtin. Aspose.Words'ün fontları arayacağı yer burasıdır.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

-  dataDir: Bu dize değişkeni, yazı tiplerinizin bulunduğu dizine giden yolu tutar. Değiştir`"YOUR DOCUMENT DIRECTORY"` gerçek yol ile.

## Adım 3: Özel Yazı Tipi Klasörü Ekle

Şimdi Aspose.Words'ün bu klasörde yazı tiplerini aramasını sağlamak için yeni bir klasör kaynağı ekleyin.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: Bu sınıf bir klasör yazı tipi kaynağını temsil eder. İkinci parametre (`true`) alt klasörlerde yazı tiplerinin yinelemeli olarak aranıp aranmayacağını belirtir.

## Adım 4: Yazı Tipi Kaynaklarını Güncelleyin

Özel yazı tipi klasörünü mevcut yazı tipi kaynakları listesine ekleyin ve yazı tipi ayarlarını güncelleyin.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): Özel font klasörünü mevcut font kaynaklarına ekler.
- updatedFontSources: Yazı tipi kaynaklarının listesini bir diziye dönüştürür.

## Adım 5: Yazı Tiplerini Alın ve Görüntüleyin

Son olarak mevcut yazı tiplerini alın ve ayrıntılarını görüntüleyin.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): Güncellenen listedeki ilk font kaynağından kullanılabilir fontların listesini alır.
-  fontInfo: Bir örneği`PhysicalFontInfo` Her yazı tipi hakkında ayrıntıları içeren.

## Çözüm

Tebrikler! Aspose.Words for .NET kullanarak kullanılabilir yazı tiplerinin listesini başarıyla aldınız. Bu eğitim, yazı tipi ayarlarını başlatmaktan yazı tipi ayrıntılarını görüntülemeye kadar her adımda size yol gösterdi. Bu bilgiyle artık Word belgelerinizdeki yazı tiplerini kolaylıkla yönetebilirsiniz. Unutmayın, Aspose.Words for .NET, belge işleme yeteneklerinizi önemli ölçüde artırabilecek güçlü bir araçtır. Bu yüzden devam edin ve geliştirme sürecinizi daha da verimli hale getirmek için daha fazla özelliği keşfedin.

## SSS

### Aspose.Words for .NET'i diğer .NET framework'leriyle birlikte kullanabilir miyim?
Evet, Aspose.Words for .NET, .NET Core ve .NET 5+ dahil olmak üzere çeşitli .NET çerçeveleriyle uyumludur.

### Aspose.Words for .NET'i nasıl yüklerim?
Visual Studio'daki NuGet Paket Yöneticisi'ni kullanarak "Aspose.Words" ifadesini aratarak kurulumunu yapabilirsiniz.

### Birden fazla özel yazı tipi klasörü eklemek mümkün müdür?
 Evet, birden fazla özel yazı tipi klasörü oluşturarak birden fazla özel yazı tipi klasörü ekleyebilirsiniz.`FolderFontSource` örnekleri ve bunları yazı tipi kaynakları listesine ekleme.

### Belirli bir font kaynağından font ayrıntılarını alabilir miyim?
 Evet, font kaynağının dizinini belirterek herhangi bir font kaynağından font ayrıntılarını alabilirsiniz.`updatedFontSources` sıralamak.

### Aspose.Words for .NET yazı tipi değiştirmeyi destekliyor mu?
Evet, orijinal yazı tipi mevcut olmasa bile metnin doğru şekilde işlenmesini sağlamak için yazı tipi değiştirmeyi destekler.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
