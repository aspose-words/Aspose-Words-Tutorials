---
"description": "Aspose.Words for .NET'te Font Geri Dönüş Ayarlarını nasıl ayarlayacağınızı öğrenin. Bu kapsamlı kılavuz, belgelerinizdeki tüm karakterlerin doğru şekilde görüntülenmesini sağlar."
"linktitle": "Yazı Tipi Yedek Ayarlarını Ayarla"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Yazı Tipi Yedek Ayarlarını Ayarla"
"url": "/tr/net/working-with-fonts/set-font-fallback-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Yazı Tipi Yedek Ayarlarını Ayarla

## giriiş

Farklı diller veya özel karakterler gibi çeşitli metin öğeleri içeren belgelerle çalışırken, bu öğelerin doğru şekilde görüntülendiğinden emin olmak çok önemlidir. Aspose.Words for .NET, orijinal font belirli karakterleri desteklemediğinde fontları değiştirmek için kuralları tanımlamaya yardımcı olan Font Fallback Settings adlı güçlü bir özellik sunar. Bu kılavuzda, adım adım bir eğitimde Aspose.Words for .NET kullanarak Font Fallback Settings'in nasıl ayarlanacağını inceleyeceğiz.

## Ön koşullar

Eğitime başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:

- Temel C# Bilgisi: C# programlama dili ve .NET framework'üne aşinalık.
- Aspose.Words for .NET: Şuradan indirin ve kurun: [indirme bağlantısı](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Kodunuzu yazıp çalıştırabileceğiniz Visual Studio benzeri bir kurulum.
- Örnek Belge: Örnek bir belgeniz olsun (örneğin, `Rendering.docx`) test edilmeye hazır.
- Yazı Tipi Geri Dönüş Kuralları XML: Yazı tipi geri dönüş kurallarını tanımlayan bir XML dosyası hazırlayın.

## Ad Alanlarını İçe Aktar

Aspose.Words'ü kullanmak için gerekli ad alanlarını içe aktarmanız gerekir. Bu, belge işleme için gereken çeşitli sınıflara ve yöntemlere erişim sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## Adım 1: Belge Dizinini Tanımlayın

Öncelikle belgenizin saklandığı dizini tanımlayın. Bu, belgenizi bulmak ve işlemek için önemlidir.

```csharp
// Belgeler dizinine giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Adım 2: Belgeyi Yükleyin

Belgenizi bir Aspose.Words'e yükleyin `Document` nesne. Bu adım, belgeyle programlı olarak çalışmanıza olanak tanır.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Adım 3: Yazı Tipi Ayarlarını Yapılandırın

Yeni bir tane oluştur `FontSettings` nesne ve yazı tipi geri dönüş ayarlarını bir XML dosyasından yükleyin. Bu XML dosyası yazı tipi geri dönüşü için kuralları içerir.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## Adım 4: Yazı Tipi Ayarlarını Belgeye Uygula

Yapılandırılanı atayın `FontSettings` belgeye. Bu, belgenin işlenmesi sırasında yazı tipi yedek kurallarının uygulanmasını sağlar.

```csharp
doc.FontSettings = fontSettings;
```

## Adım 5: Belgeyi Kaydedin

Son olarak belgeyi kaydedin. Font yedek ayarları, uygun font değişimini sağlamak için kaydetme işlemi sırasında kullanılacaktır.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## XML Dosyası: Yazı Tipi Geri Dönüş Kuralları

Yazı tipi yedek kurallarını tanımlayan XML dosyanızın nasıl görünmesi gerektiğine dair bir örnek aşağıda verilmiştir:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## Çözüm

Bu adımları izleyerek, Aspose.Words for .NET'te Font Fallback Ayarlarını etkili bir şekilde ayarlayabilir ve kullanabilirsiniz. Bu, orijinal font belirli karakterleri desteklemese bile belgelerinizin tüm karakterleri doğru şekilde görüntülemesini sağlar. Bu ayarları uygulamak belgelerinizin kalitesini ve okunabilirliğini büyük ölçüde artıracaktır.

## SSS

### S1: Font Fallback Nedir?

Font Geri Dönüşü, orijinal fontun belirli karakterleri desteklememesi durumunda fontların değiştirilmesine olanak tanıyan ve tüm metin öğelerinin düzgün görüntülenmesini sağlayan bir özelliktir.

### S2: Birden fazla yedek yazı tipi belirleyebilir miyim?

Evet, XML kurallarında birden fazla yedek yazı tipi belirtebilirsiniz. Aspose.Words, karakteri destekleyen bir yazı tipi bulana kadar her yazı tipini belirtilen sırayla kontrol edecektir.

### S3: Aspose.Words for .NET'i nereden indirebilirim?

Bunu şuradan indirebilirsiniz: [Aspose indirme sayfası](https://releases.aspose.com/words/net/).

### S4: Yazı tipi geri dönüş kuralları için XML dosyasını nasıl oluştururum?

XML dosyası herhangi bir metin düzenleyicisi kullanılarak oluşturulabilir. Bu eğitimde verilen örnekte gösterilen yapıyı takip etmelidir.

### S5: Aspose.Words için destek mevcut mu?

Evet, destek bulabilirsiniz [Aspose.Words destek forumu](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}