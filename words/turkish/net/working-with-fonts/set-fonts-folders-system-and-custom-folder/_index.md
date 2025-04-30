---
"description": "Aspose.Words for .NET kullanarak Word belgelerinde sistem ve özel yazı tipi klasörlerinin nasıl ayarlanacağını öğrenin ve belgelerinizin farklı ortamlarda doğru şekilde görüntülenmesini sağlayın."
"linktitle": "Yazı Tipleri Klasör Sistemi ve Özel Klasör Ayarla"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Yazı Tipleri Klasör Sistemi ve Özel Klasör Ayarla"
"url": "/tr/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Yazı Tipleri Klasör Sistemi ve Özel Klasör Ayarla

## giriiş

Benzersiz bir yazı tipi stiliyle bir belge oluşturduğunuzu ve yazı tiplerinin başka bir bilgisayarda doğru şekilde görüntülenmediğini fark ettiğinizi düşünün. Sinir bozucu, değil mi? İşte yazı tipi klasörlerini yapılandırmanın devreye girdiği yer burasıdır. .NET için Aspose.Words ile belgelerinizin her zaman amaçlandığı gibi görünmesini sağlamak için sistem ve özel yazı tipi klasörleri tanımlayabilirsiniz. Bunu nasıl başarabileceğinize bir bakalım.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

- Aspose.Words for .NET Kütüphanesi: Henüz yapmadıysanız indirin [Burada](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio benzeri bir IDE.
- Temel C# Bilgisi: C#'a aşina olmak, kod örneklerini takip etmenize yardımcı olacaktır.

## Ad Alanlarını İçe Aktar

Öncelikle projenize gerekli namespace'leri import edin:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Şimdi süreci basit adımlara bölelim.

## Adım 1: Belgeyi Yükleyin

Başlamak için Word belgenizi bir Aspose.Words'e yükleyin `Document` nesne. Bu belge, yazı tipi klasörlerini ayarlamak isteyeceğiniz belge olacaktır.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Adım 2: Yazı Tipi Ayarlarını Başlatın

Yeni bir örnek oluşturun `FontSettings`Bu nesne font kaynaklarını yönetmenize olanak tanır.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Adım 3: Sistem Yazı Tipi Kaynaklarını Alın

Varsayılan sistem yazı tipi kaynaklarını alın. Bir Windows makinesinde, bu genellikle "Windows\Fonts" dizinini içerir.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Adım 4: Özel Bir Yazı Tipi Klasörü Ekleyin

Ek yazı tiplerinizi içeren özel bir klasör ekleyin. Bu, sistem yazı tipleri dizininde yüklü olmayan belirli yazı tipleriniz varsa yararlıdır.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Adım 5: Yazı Tipi Kaynaklarını Güncelleyin

Yazı tipi kaynaklarının listesini bir diziye geri dönüştürün ve şunu ayarlayın: `FontSettings` nesne.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Adım 6: Yazı Tipi Ayarlarını Belgeye Uygula

Son olarak, yapılandırılanı uygulayın `FontSettings` Belgenize ekleyin ve PDF gibi istediğiniz formatta kaydedin.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Çözüm

İşte bu kadar! Bu adımları izleyerek, Word belgelerinizin doğru yazı tiplerini kullandığından emin olabilirsiniz, ister sistem yazı tipleri ister belirli bir dizinde saklanan özel yazı tipleri olsun. Bu kurulum, belgenizin görünümünün farklı ortamlarda bütünlüğünü korumaya yardımcı olur.

## SSS

### Bir yazı tipi hem sistemde hem de özel klasörlerde eksik olursa ne olur?

Aspose.Words eksik yazı tipini değiştirmek için varsayılan bir yazı tipi kullanacak ve böylece belgenin okunabilirliğini koruyacaktır.

### Birden fazla özel yazı tipi klasörü ekleyebilir miyim?

Evet, oluşturma sürecini tekrarlayarak birden fazla özel yazı tipi klasörü ekleyebilirsiniz. `FolderFontSource` nesneleri yazı tipi kaynakları listesine ekleyerek.

### Özel yazı tipi klasörleri için ağ yollarını kullanmak mümkün müdür?

Evet, bir ağ yolu belirtebilirsiniz `FolderFontSource` inşaatçı.

### Aspose.Words belgeleri kaydetmek için hangi dosya biçimlerini destekler?

Aspose.Words DOCX, PDF, HTML ve daha fazlası dahil olmak üzere çeşitli formatları destekler.

### Yazı tipi değiştirme bildirimlerini nasıl işlerim?

Yazı tipi değiştirme bildirimlerini kullanarak işleyebilirsiniz. `FontSettings` sınıfın `FontSubstitutionWarning` etkinlik.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}