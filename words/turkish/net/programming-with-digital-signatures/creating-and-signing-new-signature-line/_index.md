---
title: Yeni İmza Hattı Oluşturma ve İmzalama
linktitle: Yeni İmza Hattı Oluşturma ve İmzalama
second_title: Aspose.Words Belge İşleme API'si
description: Bu adım adım eğitimle Aspose.Words for .NET kullanarak bir Word belgesinde imza satırının nasıl oluşturulacağını ve dijital olarak imzalanacağını öğrenin. Belge otomasyonu için mükemmeldir.
weight: 10
url: /tr/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Yeni İmza Hattı Oluşturma ve İmzalama

## giriiş

Merhaba! Bir Word belgeniz var ve bir imza satırı eklemeniz ve ardından dijital olarak imzalamanız gerekiyor. Kulağa zor geliyor mu? Hiç de değil! .NET için Aspose.Words sayesinde bunu yalnızca birkaç satır kodla sorunsuz bir şekilde başarabilirsiniz. Bu eğitimde, ortamınızı kurmaktan belgenizi yepyeni bir imzayla kaydetmeye kadar tüm süreci size anlatacağız. Hazır mısınız? Hadi başlayalım!

## Ön koşullar

Koda geçmeden önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:
1.  Aspose.Words for .NET - Şunları yapabilirsiniz[buradan indirin](https://releases.aspose.com/words/net/).
2. .NET Geliştirme Ortamı - Visual Studio şiddetle tavsiye edilir.
3. İmzalanacak Bir Belge - Basit bir Word belgesi oluşturun veya mevcut bir belgeyi kullanın.
4.  Bir Sertifika Dosyası - Bu, dijital imzalar için gereklidir. Bir`.pfx` dosya.
5. İmza Satırı İçin Görseller - İsteğe bağlı olarak imza için bir görsel dosyası.

## Ad Alanlarını İçe Aktar

Öncelikle gerekli ad alanlarını içe aktarmamız gerekiyor. Bu adım, Aspose.Words işlevlerini kullanmak için ortamı ayarladığı için önemlidir.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Adım 1: Belge Dizinini Ayarlama

Her projenin iyi bir başlangıca ihtiyacı vardır. Belge dizininize giden yolu ayarlayalım. Belgelerinizin kaydedileceği ve alınacağı yer burasıdır.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Adım 2: Yeni Bir Belge Oluşturma

Şimdi Aspose.Words kullanarak yeni bir Word belgesi oluşturalım. Bu, imza satırını ekleyeceğimiz tuvalimiz olacak.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 3: İmza Satırını Ekleme

 İşte sihir burada gerçekleşir. Belgemize bir imza satırı ekleriz.`DocumentBuilder` sınıf.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Adım 4: İmza Satırıyla Belgeyi Kaydetme

İmza satırı yerleştirildiğinde, belgeyi kaydetmemiz gerekir. Bu, imzalamaya geçmeden önceki ara bir adımdır.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Adım 5: İmzalama Seçeneklerini Ayarlama

Şimdi, belgeyi imzalamak için seçenekleri ayarlayalım. Bu, imza satırı kimliğini ve kullanılacak resmi belirtmeyi içerir.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Adım 6: Sertifikanın Yüklenmesi

Dijital imzalar bir sertifika gerektirir. Burada, belgeyi imzalamak için kullanılacak sertifika dosyasını yüklüyoruz.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Adım 7: Belgenin İmzalanması

 Bu son adımdır. Şunu kullanırız:`DigitalSignatureUtil`Belgeyi imzalamak için sınıf. İmzalanan belge yeni bir adla kaydedilir.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Çözüm

İşte karşınızda! Bu adımlarla, yeni bir Word belgesini başarıyla oluşturdunuz, bir imza satırı eklediniz ve Aspose.Words for .NET kullanarak dijital olarak imzaladınız. Belge otomasyonunu kolaylaştıran güçlü bir araçtır. Sözleşmeler, anlaşmalar veya herhangi bir resmi belgeyle uğraşıyor olun, bu yöntem bunların güvenli bir şekilde imzalanmasını ve doğrulanmasını sağlar.

## SSS

### İmza satırında başka resim formatları kullanabilir miyim?
Evet, PNG, JPG, BMP gibi çeşitli resim formatlarını kullanabilirsiniz.

###  Birini kullanmak gerekli mi?`.pfx` file for the certificate?
 Evet, bir`.pfx` Dosya, sertifikalar ve özel anahtarlar da dahil olmak üzere kriptografik bilgileri depolamak için kullanılan yaygın bir formattır.

### Tek bir belgeye birden fazla imza satırı ekleyebilir miyim?
Kesinlikle! Her imza için ekleme adımını tekrarlayarak birden fazla imza satırı ekleyebilirsiniz.

### Dijital sertifikam yoksa ne olur?
Güvenilir bir sertifika kuruluşundan dijital sertifika almanız veya OpenSSL gibi araçları kullanarak bir sertifika oluşturmanız gerekecektir.

### Belgedeki dijital imzayı nasıl doğrularım?
İmzalanmış belgeyi Word'de açıp imza ayrıntılarına giderek imzanın gerçekliğini ve bütünlüğünü doğrulayabilirsiniz.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
