---
title: Yazı Tipleri Klasörlerini Varsayılan Örnek Olarak Ayarla
linktitle: Yazı Tipleri Klasörlerini Varsayılan Örnek Olarak Ayarla
second_title: Aspose.Words Belge İşleme API'si
description: Bu adım adım eğitimle Aspose.Words for .NET'te varsayılan örnek için font klasörlerini nasıl ayarlayacağınızı öğrenin. Word belgelerinizi zahmetsizce özelleştirin.
weight: 10
url: /tr/net/working-with-fonts/set-fonts-folders-default-instance/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yazı Tipleri Klasörlerini Varsayılan Örnek Olarak Ayarla

## giriiş

Merhaba, kodlayıcı arkadaşım! .NET'te Word belgeleriyle çalışıyorsanız, muhtemelen yazı tiplerinizin tam olarak doğru olmasının önemini biliyorsunuzdur. Bugün, .NET için Aspose.Words kullanarak varsayılan örnek için yazı tipi klasörlerinin nasıl ayarlanacağına derinlemesine bakıyoruz. Tüm özel yazı tiplerinizin parmaklarınızın ucunda olduğunu ve belgelerinizin tam olarak hayal ettiğiniz gibi göründüğünü hayal edin. Kulağa harika geliyor, değil mi? Hadi başlayalım!

## Ön koşullar

Ayrıntılara dalmadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:
-  Aspose.Words for .NET: Kütüphanenin kurulu olduğundan emin olun. Eğer kurulu değilse,[buradan indirin](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio veya herhangi bir .NET uyumlu IDE.
- Temel C# Bilgisi: C# programlamayı rahatça anlayabiliyor olmalısınız.
- Font Klasörü: Özel fontlarınızı içeren bir dizin.

## Ad Alanlarını İçe Aktar

İlk önce gerekli ad alanlarını içe aktaralım. Bu, fonts klasörünü ayarlamak için gereken sınıflara ve yöntemlere erişimde yardımcı olur.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Süreci basit ve anlaşılır adımlara bölelim.

## Adım 1: Veri Dizinini Tanımlayın

Her büyük yolculuk tek bir adımla başlar ve bizimki belgenizin saklandığı dizini tanımlamakla başlar. Aspose.Words'ün Word belgenizi arayacağı yer burasıdır.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Burada, değiştirin`"YOUR DOCUMENT DIRECTORY"` belge dizininize giden gerçek yol ile. Kaynak belgenizin bulunduğu ve çıktının kaydedileceği yer burasıdır.

## Adım 2: Fontlar Klasörünü Ayarlayın

 Şimdi, Aspose.Words'e özel yazı tiplerinizi nerede bulacağını söyleyelim. Bu, yazı tipleri klasörünü kullanarak ayarlayarak yapılır`FontSettings.DefaultInstance.SetFontsFolder` yöntem.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

 Bu satırda,`"C:\\MyFonts\\"` özel yazı tipleri klasörünüze giden yoldur. İkinci parametre,`true`, bu klasördeki yazı tiplerinin tekrarlı olarak taranması gerektiğini belirtir.

## Adım 3: Belgenizi Yükleyin

 Yazı tipleri klasörü ayarlandıktan sonraki adım Word belgenizi Aspose.Words'e yüklemektir. Bu,`Document` sınıf.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Burada,`dataDir + "Rendering.docx"` Word belgenizin tam yolunu ifade eder. Belgenizin belirtilen dizinde olduğundan emin olun.

## Adım 4: Belgeyi Kaydedin

Son adım, font klasörünü ayarladıktan sonra belgenizi kaydetmektir. Bu, özel fontlarınızın çıktıda doğru şekilde uygulanmasını sağlar.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Bu satır, belgenizi özel yazı tiplerinin uygulandığı bir PDF olarak kaydeder. Çıktı dosyası, kaynak belgenizle aynı dizinde yer alacaktır.

## Çözüm

İşte oldu! Aspose.Words for .NET'te varsayılan örnek için font klasörlerini ayarlamak, basit adımlara böldüğünüzde çocuk oyuncağı. Bu kılavuzu izleyerek, Word belgelerinizin tüm özel fontlarınız yerindeyken tam olarak istediğiniz gibi görünmesini sağlayabilirsiniz. Hadi, deneyin ve belgelerinizin parlamasını sağlayın!

## SSS

### Birden fazla font klasörü ayarlayabilir miyim?
 Evet, kullanarak birden fazla yazı tipi klasörü ayarlayabilirsiniz.`SetFontsFolders` Klasör yollarının dizisini kabul eden yöntem.

### Aspose.Words belgeleri kaydetmek için hangi dosya biçimlerini destekler?
Aspose.Words DOCX, PDF, HTML, EPUB ve daha fazlası dahil olmak üzere çeşitli formatları destekler.

### Aspose.Words'de online fontları kullanmak mümkün müdür?
Hayır, Aspose.Words şu anda yalnızca yerel yazı tipi dosyalarını desteklemektedir.

### Özel yazı tiplerimin kaydedilen PDF'e gömülmesini nasıl sağlayabilirim?
 Ayarlayarak`FontSettings` Doğru şekilde ve yazı tiplerinin mevcut olduğundan emin olduktan sonra Aspose.Words bunları PDF çıktısına gömecektir.

### Belirtilen klasörde bir font bulunamazsa ne olur?
Belirtilen yazı tipi bulunamazsa Aspose.Words yedek yazı tipini kullanacaktır.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
