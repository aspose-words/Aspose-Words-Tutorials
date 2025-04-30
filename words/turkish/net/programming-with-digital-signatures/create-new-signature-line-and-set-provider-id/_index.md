---
"description": "Aspose.Words for .NET kullanarak Word belgelerinde yeni bir imza satırı oluşturmayı ve sağlayıcı kimliğini ayarlamayı öğrenin. Adım adım kılavuz."
"linktitle": "Yeni İmza Satırı Oluşturun ve Sağlayıcı Kimliğini Ayarlayın"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Yeni İmza Satırı Oluşturun ve Sağlayıcı Kimliğini Ayarlayın"
"url": "/tr/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Yeni İmza Satırı Oluşturun ve Sağlayıcı Kimliğini Ayarlayın

## giriiş

Merhaba teknoloji meraklıları! Word belgelerinize programatik olarak nasıl imza satırı ekleyeceğinizi hiç merak ettiniz mi? İşte bugün .NET için Aspose.Words kullanarak tam da buna dalacağız. Bu kılavuz, her adımda size yol gösterecek ve Word belgelerinizde yeni bir imza satırı oluşturmayı ve sağlayıcı kimliğini ayarlamayı çocuk oyuncağı haline getirecek. Belge işlemeyi otomatikleştiriyor veya sadece iş akışınızı kolaylaştırmak istiyorsanız, bu eğitim tam size göre.

## Ön koşullar

Ellerimizi kirletmeden önce ihtiyacımız olan her şeye sahip olduğumuzdan emin olalım:

1. Aspose.Words for .NET: Henüz yapmadıysanız indirin [Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio veya herhangi bir C# geliştirme ortamı.
3. .NET Framework: .NET Framework'ün yüklü olduğundan emin olun.
4. PFX Sertifikası: Belgeleri imzalamak için bir PFX sertifikasına ihtiyacınız olacak. Güvenilir bir sertifika yetkilisinden alabilirsiniz.

## Ad Alanlarını İçe Aktar

Öncelikle C# projenize gerekli ad alanlarını aktaralım:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Tamam, asıl konuya gelelim. İşte yeni bir imza satırı oluşturmak ve sağlayıcı kimliğini ayarlamak için her adımın ayrıntılı bir dökümü.

## Adım 1: Yeni Bir Belge Oluşturun

Başlamak için yeni bir Word belgesi oluşturmamız gerekiyor. Bu, imza satırımızın tuvali olacak.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Bu kod parçacığında yeni bir tane başlatıyoruz `Document` ve bir `DocumentBuilder`. `DocumentBuilder` belgemize öğeler eklememize yardımcı olur.

## Adım 2: İmza Satırı Seçeneklerini Tanımlayın

Sonra, imza satırımız için seçenekleri tanımlıyoruz. Bu, imzalayanın adını, unvanını, e-postasını ve diğer ayrıntıları içerir.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Bu seçenekler imza satırını kişiselleştirerek net ve profesyonel hale getirir.

## Adım 3: İmza Satırını Ekle

Seçeneklerimiz ayarlandıktan sonra artık imza satırını belgeye ekleyebiliriz.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

Burada, `InsertSignatureLine` metodu imza satırını ekler ve buna benzersiz bir sağlayıcı kimliği atarız.

## Adım 4: Belgeyi Kaydedin

İmza satırını ekledikten sonra belgeyi kaydedelim.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Bu, belgenizi yeni eklenen imza satırıyla kaydeder.

## Adım 5: İmzalama Seçeneklerini Ayarlayın

Şimdi, belgeyi imzalamak için seçenekleri ayarlamamız gerekiyor. Bunlara imza satırı kimliği, sağlayıcı kimliği, yorumlar ve imzalama zamanı dahildir.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Bu seçenekler belgenin doğru bilgilerle imzalanmasını sağlar.

## Adım 6: Sertifika Sahibi Oluşturun

Belgeyi imzalamak için bir PFX sertifikası kullanacağız. Bunun için bir sertifika sahibi oluşturalım.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

Değiştirdiğinizden emin olun `"morzal.pfx"` gerçek sertifika dosyanızla ve `"aw"` sertifika şifrenizle.

## Adım 7: Belgeyi İmzalayın

Son olarak dijital imza aracını kullanarak belgeyi imzalıyoruz.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Bu, belgeyi imzalar ve yeni bir dosya olarak kaydeder.

## Çözüm

Ve işte oldu! Aspose.Words for .NET kullanarak Word belgesinde yeni bir imza satırı oluşturdunuz ve sağlayıcı kimliğini ayarladınız. Bu güçlü kütüphane, belge işleme görevlerini yönetmeyi ve otomatikleştirmeyi inanılmaz derecede kolaylaştırır. Deneyin ve iş akışınızı nasıl kolaylaştırabileceğini görün.

## SSS

### İmza satırının görünümünü özelleştirebilir miyim?
Kesinlikle! Çeşitli seçenekleri ayarlayabilirsiniz `SignatureLineOptions` İhtiyaçlarınıza uygun.

### PFX sertifikam yoksa ne olur?
Güvenilir bir sertifika yetkilisinden bir tane edinmeniz gerekecek. Belgeleri dijital olarak imzalamak için gereklidir.

### Bir belgeye birden fazla imza satırı ekleyebilir miyim?
Evet, ekleme işlemini farklı seçeneklerle tekrarlayarak ihtiyacınız kadar imza satırı ekleyebilirsiniz.

### Aspose.Words for .NET, .NET Core ile uyumlu mudur?
Evet, Aspose.Words for .NET, .NET Core'u destekler ve bu da onu farklı geliştirme ortamları için çok yönlü hale getirir.

### Dijital imzalar ne kadar güvenli?
Aspose.Words ile oluşturulan dijital imzalar, geçerli ve güvenilir bir sertifika kullanmanız koşuluyla son derece güvenlidir.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}