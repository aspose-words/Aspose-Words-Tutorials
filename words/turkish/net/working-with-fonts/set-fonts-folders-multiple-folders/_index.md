---
title: Yazı Tipleri Klasörlerini Birden Fazla Klasöre Ayarla
linktitle: Yazı Tipleri Klasörlerini Birden Fazla Klasöre Ayarla
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word belgelerinizde birden fazla font klasörünün nasıl ayarlanacağını öğrenin. Bu adım adım kılavuz, belgelerinizin tam olarak ihtiyaç duyduğunuz fontları kullanmasını sağlar.
weight: 10
url: /tr/net/working-with-fonts/set-fonts-folders-multiple-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yazı Tipleri Klasörlerini Birden Fazla Klasöre Ayarla

## giriiş

Word belgelerinizde birden fazla font kaynağını nasıl yöneteceğinizi hiç merak ettiniz mi? Belki de farklı klasörlere dağılmış bir font koleksiyonunuz vardır ve belgelerinizin bunları sorunsuz bir şekilde kullanmasını sağlayacak bir yola ihtiyacınız vardır. Şanslısınız! Bugün, .NET için Aspose.Words kullanarak font klasörlerinin nasıl ayarlanacağına derinlemesine bakıyoruz. Bu kılavuz, belgelerinizin tam olarak istediğiniz gibi görünmesini sağlayarak sizi adım adım süreç boyunca yönlendirecektir.

## Ön koşullar

Başlamadan önce, ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım. İşte takip etmeniz gerekenler:

-  Aspose.Words for .NET: Eğer henüz yapmadıysanız, Aspose.Words for .NET'i indirin ve kurun. Bunu edinebilirsiniz[Burada](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio veya herhangi bir .NET uyumlu geliştirme ortamı.
- Temel C# Bilgisi: C# konusunda biraz bilgi sahibi olmak örnekleri takip etmenize yardımcı olacaktır.
- Yazı Tipi Dosyaları: Yazı tipi dosyalarınızın kolayca erişebileceğiniz dizinlerde saklandığından emin olun.

## Ad Alanlarını İçe Aktar

Öncelikle, C# projenize gerekli ad alanlarını içe aktaralım. Bu, ihtiyacınız olan tüm Aspose.Words işlevlerine erişiminizin olmasını sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Bu setle birlikte, Aspose.Words for .NET'te yazı tipi klasörlerini ayarlamaya yönelik adım adım kılavuza geçelim.

## Adım 1: Belgenizi Yükleyin

Tamam, çalışmak istediğiniz Word belgesini yükleyerek başlayalım. Belge yolunun hazır olduğundan emin olun. Bu örnek için "Rendering.docx" adlı bir belge kullanacağız.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Burada, belirtilen dizinden belgeyi yüklüyoruz. Oldukça basit, değil mi?

## Adım 2: FontSettings Nesnesini Oluşturun

 Daha sonra, bir tane oluşturmamız gerekiyor`FontSettings` nesne. Bu nesne, belgemiz için yazı tipi kaynaklarını yönetmemizi sağlayacaktır.

```csharp
FontSettings fontSettings = new FontSettings();
```

 Bu`FontSettings`nesnesi hangi font klasörlerini kullanacağımızı tanımlamamıza yardımcı olacaktır.

## Adım 3: Yazı Tipleri Klasörlerini Ayarlayın

Şimdi kritik kısım geliyor: font klasörlerini ayarlamak. Burası fontlarınızın bulunduğu dizinleri belirttiğiniz yerdir. Bu örnekte, "C:\MyFonts" dizininde fontlarımız var\" ve "D:\Çeşitli\Yazı Tipleri\".

```csharp
fontSettings.SetFontsFolders(new[] { @"C:\MyFonts\", @"D:\Misc\Fonts\" }, true);
```

İkinci parametre (`true` ) bu klasörlerin varsayılan yazı tipi kaynaklarını geçersiz kılacağını belirtir. Sistem yazı tipi kaynaklarını da tutmak istiyorsanız, aşağıdakilerin bir kombinasyonunu kullanabilirsiniz`GetFontSources` Ve`SetFontSources`.

## Adım 4: Yazı Tipi Ayarlarını Belgeye Uygula

Font klasörleri ayarlandığında, bu ayarları belgemize uygulamamız gerekir. Bu, belgenin işleme sırasında belirtilen fontları kullanmasını sağlar.

```csharp
doc.FontSettings = fontSettings;
```

## Adım 5: Belgeyi Kaydedin

Son olarak belgeyi kaydedelim. Fontları çalışırken görmek için PDF olarak kaydedeceğiz.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersMultipleFolders.pdf");
```

Ve işte oldu! Belgeniz için birden fazla font klasörünü başarıyla ayarladınız.

## Çözüm

Belgelerinizdeki yazı tiplerini yönetmek zorlu bir görev gibi görünebilir, ancak Aspose.Words for .NET ile bu çok kolay! Bu basit adımları izleyerek belgelerinizin profesyonel görünmesini sağlayabilir ve tam olarak ihtiyaç duyduğunuz yazı tiplerini kullanabilirsiniz. Belirli bir markalama gerektiren bir proje üzerinde çalışıyor olun veya belgenizin görünümü üzerinde daha fazla kontrole sahip olmak istiyor olun, yazı tipi klasörlerini ayarlamak ustalaşmaya değer bir beceridir.

## SSS

### Font klasörleri için ağ yollarını kullanabilir miyim?
Evet, font klasörleriniz için ağ yollarını kullanabilirsiniz. Sadece yolların uygulamanızdan erişilebilir olduğundan emin olun.

### Belirtilen klasörlerde bir font eksik olursa ne olur?
Bir yazı tipi eksikse, Aspose.Words belirtilen varsayılan yazı tipine geri döner veya yedek bir yazı tipi kullanır.

### Sistem yazı tiplerini geçersiz kılmadan yazı tipi klasörleri ekleyebilir miyim?
 Kesinlikle! Kullan`FontSettings.GetFontSources` mevcut kaynakları almak ve bunları özel klasörlerinizle birleştirmek için`FontSettings.SetFontSources`.

### Ekleyebileceğim font klasörlerinin sayısında bir sınırlama var mı?
Font klasörlerinin sayısında kesin bir sınır yoktur. Ancak, daha fazla klasörün font yükleme sürelerini artırabileceği için performansa dikkat edin.

### Belgemde hangi yazı tiplerinin kullanıldığını nasıl kontrol edebilirim?
 Kullanabilirsiniz`FontSettings.GetFontsSources` Belgeniz için şu anda ayarlanmış olan yazı tipi kaynaklarını alma ve inceleme yöntemi.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
