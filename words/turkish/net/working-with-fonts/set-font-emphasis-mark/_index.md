---
title: Yazı Tipi Vurgu İşaretini Ayarla
linktitle: Yazı Tipi Vurgu İşaretini Ayarla
second_title: Aspose.Words Belge İşleme API'si
description: Bu ayrıntılı, adım adım kılavuzla Aspose.Words for .NET kullanarak Word belgelerinde yazı tipi vurgu işaretlerinin nasıl ayarlanacağını öğrenin. .NET geliştiricileri için mükemmeldir.
weight: 10
url: /tr/net/working-with-fonts/set-font-emphasis-mark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yazı Tipi Vurgu İşaretini Ayarla

## giriiş

Bugünkü eğitimde, Aspose.Words for .NET kullanarak bir Word belgesinde yazı tipi vurgu işaretlerinin nasıl ayarlanacağına derinlemesine iniyoruz. İster belirli bir metni benzersiz bir işaretle altını çizmek isteyin, ister sadece belirli kelimeleri öne çıkarmak isteyin, bu kılavuz sizin için her şeyi kapsayacaktır. O halde, kemerlerinizi bağlayın ve başlayalım!

## Ön koşullar

Ayrıntılara dalmadan önce, aşağıdaki ön koşulların işaretlendiğinden emin olun:

-  Aspose.Words for .NET Kütüphanesi: Aspose.Words for .NET kütüphanesinin yüklü olduğundan emin olun. Buradan indirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio benzeri çalışan bir geliştirme ortamı.
- .NET Framework: .NET Framework'ün yüklü olduğundan emin olun.

## Ad Alanlarını İçe Aktar

Aspose.Words for .NET ile çalışmak için gerekli ad alanlarını içe aktarmanız gerekir. Bunları kod dosyanızın en üstüne ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Şimdi, süreci basit adımlara bölelim. Word belgenizde yazı tipi vurgu işaretlerini ayarlamak için her adımı dikkatlice izleyin.

## Adım 1: Belgeyi ve DocumentBuilder'ı Başlatın

İlk önce, yeni bir belge ve bir DocumentBuilder başlatmanız gerekir. DocumentBuilder sınıfı, belgeye metin ve diğer öğeleri eklemek için yöntemler sağlar.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Yeni bir Belge Başlat
Document document = new Document();

// DocumentBuilder'ı belgeyle başlatın
DocumentBuilder builder = new DocumentBuilder(document);
```

## Adım 2: Yazı Tipi Vurgu İşaretini Ayarla

DocumentBuilder hazır olduğunda, artık yazı tipi vurgu işaretini ayarlayabilirsiniz. Bu örnekte, "UnderSolidCircle" vurgu işaretini kullanacağız.

```csharp
// Yazı tipi vurgusu işaretini ayarlayın
builder.Font.EmphasisMark = EmphasisMark.UnderSolidCircle;

// Vurgu işaretiyle metni yazın
builder.Write("Emphasis text");
builder.Writeln();
```

## Adım 3: Biçimlendirmeyi Temizle ve Normal Metin Ekle

Vurgu işaretini ayarladıktan sonra, herhangi bir vurgu olmadan biraz normal metin eklemek isteyebilirsiniz. Bunun için biçimlendirmeyi temizlemeniz gerekir.

```csharp
// Yazı tipi biçimlendirmesini temizle
builder.Font.ClearFormatting();

// Normal metin yaz
builder.Write("Simple text");
```

## Adım 4: Belgeyi Kaydedin

İhtiyacınız olan tüm metni ve biçimlendirmeyi ekledikten sonra, son adım belgeyi kaydetmektir. Belgenizi kaydetmek istediğiniz yolu ve dosya adını belirtin.

```csharp
// Belgeyi kaydet
document.Save(dataDir + "WorkingWithFonts.SetFontEmphasisMark.docx");
```

## Çözüm

İşte bu kadar! Aspose.Words for .NET kullanarak bir Word belgesinde yazı tipi vurgu işaretlerini ayarlamak bu kadar basit. Sadece birkaç satır kodla metninizi öne çıkarabilir ve belgelerinize profesyonel bir dokunuş katabilirsiniz. İhtiyaçlarınıza uygun farklı vurgu işaretleri ve stilleri denemekten çekinmeyin.

## SSS

### Yazı tipi vurgu işaretleri nelerdir?

Yazı tipi vurgu işaretleri, metni öne çıkarmak için eklenen özel sembollerdir. Noktalar, daireler ve diğer dekoratif işaretler içerebilirler.

### Aspose.Words for .NET ile diğer vurgu işaretlerini kullanabilir miyim?

 Evet, Aspose.Words for .NET çeşitli vurgu işaretlerini destekler. Aşağıdakilere başvurarak farklı seçenekleri keşfedebilirsiniz:[belgeleme](https://reference.aspose.com/words/net/).

### Aspose.Words for .NET'i kullanmak ücretsiz mi?

 Aspose.Words for .NET tam işlevsellik için bir lisans gerektirir. Ücretsiz deneme alabilirsiniz[Burada](https://releases.aspose.com/) veya bir lisans satın alın[Burada](https://purchase.aspose.com/buy).

### Aspose.Words for .NET desteğini nasıl alabilirim?

 Aspose topluluğundan ve destek ekibinden destek almak için şu adresi ziyaret edebilirsiniz:[destek forumu](https://forum.aspose.com/c/words/8).

### Aspose.Words for .NET'i diğer .NET framework'leriyle birlikte kullanabilir miyim?

Evet, Aspose.Words for .NET, .NET Core ve .NET 5/6 dahil olmak üzere çeşitli .NET çerçeveleriyle uyumludur.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
