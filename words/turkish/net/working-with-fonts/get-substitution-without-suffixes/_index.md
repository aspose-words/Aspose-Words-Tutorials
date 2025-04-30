---
"description": "Aspose.Words for .NET'te son ekler olmadan font değişimini nasıl yöneteceğinizi öğrenin. Belgelerinizin her seferinde mükemmel görünmesini sağlamak için adım adım kılavuzumuzu izleyin."
"linktitle": "Ekler Olmadan İkame Edin"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Ekler Olmadan İkame Edin"
"url": "/tr/net/working-with-fonts/get-substitution-without-suffixes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ekler Olmadan İkame Edin

## giriiş

Aspose.Words for .NET kullanarak font değiştirmeyi yönetmeye yönelik bu kapsamlı kılavuza hoş geldiniz. Belgelerinizde fontların düzgün görünmemesiyle ilgili sorun yaşadıysanız, doğru yerdesiniz. Bu eğitim, son ekler olmadan font değiştirmeyi etkili bir şekilde halletmeniz için sizi adım adım bir süreçten geçirecektir.

## Ön koşullar

Eğitime başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

- Temel C# Bilgisi: C# programlamayı anlamak adımları takip etmeyi ve uygulamayı kolaylaştıracaktır.
- Aspose.Words for .NET Kütüphanesi: Kütüphaneyi şu adresten indirin ve yükleyin: [indirme bağlantısı](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Kodunuzu yazmak ve çalıştırmak için Visual Studio gibi bir geliştirme ortamı kurun.
- Örnek Belge: Örnek bir belge (örneğin, `Rendering.docx`) bu eğitim sırasında çalışılacak.

## Ad Alanlarını İçe Aktar

Öncelikle Aspose.Words tarafından sağlanan sınıflara ve metodlara erişmek için gerekli namespace'leri import etmemiz gerekiyor.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Adım 1: Belge Dizinini Tanımlayın

Başlamak için belgenizin bulunduğu dizini belirtin. Bu, üzerinde çalışmak istediğiniz belgeyi bulmanıza yardımcı olur.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Adım 2: İkame Uyarı İşleyicisini Ayarlayın

Sonra, belge işleme sırasında bir font değişimi gerçekleştiğinde bizi bilgilendirecek bir uyarı işleyicisi ayarlamamız gerekiyor. Bu, font sorunlarını yakalamak ve ele almak için çok önemlidir.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Adım 3: Özel Yazı Tipi Kaynakları Ekleyin

Bu adımda, Aspose.Words'ün doğru fontları bulup kullanabilmesini sağlamak için özel font kaynakları ekleyeceğiz. Bu, özel dizinlerde depolanan belirli fontlarınız varsa özellikle yararlıdır.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

Bu kodda:
- Mevcut yazı tipi kaynaklarını alıyoruz ve yeni bir tane ekliyoruz `FolderFontSource` özel yazı tipi dizinimize işaret ediyor (`C:\\MyFonts\\`).
- Daha sonra font kaynaklarını bu yeni listeye göre güncelliyoruz.

## Adım 4: Belgeyi Kaydedin

Son olarak, font değiştirme ayarlarını uyguladıktan sonra belgeyi kaydedin. Bu eğitim için, bunu PDF olarak kaydedeceğiz.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Adım 5: Uyarı İşleyici Sınıfını Oluşturun

Uyarıları etkili bir şekilde işlemek için, aşağıdakileri uygulayan özel bir sınıf oluşturun: `IWarningCallback` arayüz. Bu sınıf, herhangi bir yazı tipi değiştirme uyarısını yakalayacak ve günlüğe kaydedecektir.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

Bu sınıfta:
- The `Warning` yöntem, yazı tipi değiştirmeyle ilgili uyarıları yakalar.
- The `FontWarnings` koleksiyon bu uyarıları daha sonra incelenmek veya kaydedilmek üzere depolar.

## Çözüm

Artık Aspose.Words for .NET kullanarak eksiz font değiştirme işlemini yönetme sürecinde ustalaştınız. Bu bilgi, sistemde mevcut fontlardan bağımsız olarak belgelerinizin amaçlanan görünümünü korumasını sağlayacaktır. Aspose.Words'ün gücünden tam olarak yararlanmak için farklı ayarlar ve kaynaklarla denemeler yapmaya devam edin.

## SSS

### Birden fazla özel dizindeki yazı tiplerini nasıl kullanabilirim?

Birden fazla ekleyebilirsiniz `FolderFontSource` örneklere `fontSources` yazı tipi kaynaklarını listeleyin ve buna göre güncelleyin.

### Aspose.Words for .NET'in ücretsiz deneme sürümünü nereden indirebilirim?

Ücretsiz deneme sürümünü şuradan indirebilirsiniz: [Aspose ücretsiz deneme sayfası](https://releases.aspose.com/).

### Birden fazla uyarı türünü kullanarak işleyebilir miyim? `IWarningCallback`?

Evet, `IWarningCallback` arayüzü sadece yazı tipi değiştirmeyi değil, çeşitli uyarı tiplerini de yönetmenize olanak tanır.

### Aspose.Words için desteği nereden alabilirim?

Destek için şu adresi ziyaret edin: [Aspose.Words destek forumu](https://forum.aspose.com/c/words/8).

### Geçici lisans satın almak mümkün müdür?

Evet, geçici bir lisans alabilirsiniz. [geçici lisans sayfası](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}