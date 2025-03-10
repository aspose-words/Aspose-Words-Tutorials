---
title: Yazı Tipi Değiştirmeyi Etkinleştir Devre Dışı Bırak
linktitle: Yazı Tipi Değiştirmeyi Etkinleştir Devre Dışı Bırak
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word belgelerinde yazı tipi değişimini nasıl etkinleştireceğinizi veya devre dışı bırakacağınızı öğrenin. Belgelerinizin tüm platformlarda tutarlı görünmesini sağlayın.
weight: 10
url: /tr/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yazı Tipi Değiştirmeyi Etkinleştir Devre Dışı Bırak

## giriiş

Word belgenizde özenle seçtiğiniz fontların başka bir bilgisayarda görüntülendiğinde değiştirildiği bir durumla hiç karşılaştınız mı? Can sıkıcı, değil mi? Bu, sistemin eksik bir fontu kullanılabilir bir fontla değiştirdiği bir işlem olan font değiştirme nedeniyle olur. Ancak endişelenmeyin! Aspose.Words for .NET ile font değiştirmeyi kolayca yönetebilir ve kontrol edebilirsiniz. Bu eğitimde, Word belgelerinizde font değiştirmeyi etkinleştirme veya devre dışı bırakma adımlarında size yol göstereceğiz ve belgelerinizin her zaman istediğiniz gibi görünmesini sağlayacağız.

## Ön koşullar

Adımlara geçmeden önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

-  Aspose.Words for .NET: En son sürümü indirin[Burada](https://releases.aspose.com/words/net/).
- Visual Studio: .NET'i destekleyen herhangi bir sürüm.
- Temel C# bilgisi: Bu, kodlama örneklerini takip etmenize yardımcı olacaktır.

## Ad Alanlarını İçe Aktar

Başlamak için, projenize gerekli ad alanlarının aktarıldığından emin olun. Bunları C# dosyanızın en üstüne ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Şimdi süreci basit ve yönetilebilir adımlara bölelim.

## Adım 1: Projenizi Kurun

Öncelikle, Visual Studio'da yeni bir proje kurun ve Aspose.Words for .NET kütüphanesine bir referans ekleyin. Daha önce yapmadıysanız, şuradan indirin:[Aspose web sitesi](https://releases.aspose.com/words/net/).

## Adım 2: Belgenizi Yükleyin

Sonra, çalışmak istediğiniz belgeyi yükleyin. Bunu nasıl yapacağınız aşağıda açıklanmıştır:

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

 Yer değiştirmek`"YOUR DOCUMENT DIRECTORY"` belge dizininize giden gerçek yol ile. Bu kod belgeyi belleğe yükler, böylece onu düzenleyebilirsiniz.

## Adım 3: Yazı Tipi Ayarlarını Yapılandırın

 Şimdi bir tane oluşturalım`FontSettings` yazı tipi değiştirme ayarlarını yönetme nesnesi:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Adım 4: Varsayılan Yazı Tipi İkamesini Ayarla

Varsayılan yazı tipi değişimini istediğiniz bir yazı tipine ayarlayın. Orijinal yazı tipi mevcut değilse bu yazı tipi kullanılacaktır:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

Bu örnekte varsayılan yazı tipi olarak Arial'ı kullanıyoruz.

## Adım 5: Yazı Tipi Bilgisi Değişimini Devre Dışı Bırakın

Sistemin eksik fontları mevcut olanlarla değiştirmesini engelleyen font bilgisi değiştirme özelliğini devre dışı bırakmak için aşağıdaki kodu kullanın:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Adım 6: Yazı Tipi Ayarlarını Belgeye Uygula

Şimdi bu ayarları belgenize uygulayın:

```csharp
doc.FontSettings = fontSettings;
```

## Adım 7: Belgenizi Kaydedin

Son olarak, değiştirdiğiniz belgeyi kaydedin. İstediğiniz herhangi bir biçimde kaydedebilirsiniz. Bu eğitim için, onu PDF olarak kaydedeceğiz:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Çözüm

İşte bu kadar! Bu adımları izleyerek, Aspose.Words for .NET kullanarak Word belgelerinizdeki font değiştirmeyi kolayca kontrol edebilirsiniz. Bu, belgelerinizin nerede görüntülenirse görüntülensin amaçlanan görünüm ve hissiyatını korumasını sağlar.

## SSS

### Arial dışında başka fontlar kullanabilir miyim?

 Kesinlikle! Sisteminizde mevcut olan herhangi bir yazı tipini, yazı tipi adını değiştirerek belirtebilirsiniz.`DefaultFontName` mülk.

### Belirtilen varsayılan yazı tipi mevcut değilse ne olur?

Varsayılan yazı tipi mevcut değilse, Aspose.Words uygun bir yedek bulmak için sistem geri dönüş mekanizmasını kullanacaktır.

### Font değiştirmeyi devre dışı bıraktıktan sonra tekrar etkinleştirebilir miyim?

 Evet, değiştirebilirsiniz`Enabled` mülkiyeti`FontInfoSubstitution` geri dönmek`true` Eğer font değişimini tekrar etkinleştirmek istiyorsanız.

### Hangi yazı tiplerinin değiştirildiğini kontrol etmenin bir yolu var mı?

Evet, Aspose.Words, yazı tipi değişimlerini günlüğe kaydetme ve izleme yöntemleri sunarak hangi yazı tiplerinin değiştirildiğini görmenizi sağlar.

### Bu yöntemi DOCX dışındaki diğer belge formatları için de kullanabilir miyim?

Kesinlikle! Aspose.Words çeşitli formatları destekler ve bu yazı tipi ayarlarını desteklenen tüm formatlara uygulayabilirsiniz.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
