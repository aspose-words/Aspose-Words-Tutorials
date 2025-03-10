---
title: Docx'i Mhtml'e Dönüştürme ve E-posta Gönderme
linktitle: Docx'i Mhtml'e Dönüştürme ve E-posta Gönderme
second_title: Aspose.Words Belge İşleme API'si
description: Bu adım adım kılavuzda DOCX'i MHTML'e nasıl dönüştüreceğinizi ve Aspose.Words for .NET kullanarak e-postaları nasıl göndereceğinizi öğrenin. Kolay otomasyonla üretkenliğinizi artırın.
weight: 10
url: /tr/net/basic-conversions/docx-to-mhtml-and-sending-email/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Docx'i Mhtml'e Dönüştürme ve E-posta Gönderme

## giriiş

Günümüzün dijital çağında, belgeleri bir formattan diğerine dönüştürmek ve e-posta yoluyla göndermek yaygın bir görevdir. Bu makale, bir DOCX dosyasını MHTML formatına dönüştürme ve ardından Aspose.Words for .NET kullanarak e-posta olarak gönderme sürecini adım adım açıklayacaktır. Her adımı ayrıntılı, kolay takip edilebilir bir kılavuzda açıklayarak süreci baştan sona anlamanızı sağlayacağız. Hadi başlayalım!

## Ön koşullar

Başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:

1.  Aspose.Words for .NET: Aspose.Words for .NET kitaplığını şu adresten indirin ve yükleyin:[Aspose sürüm sayfası](https://releases.aspose.com/words/net/).
2.  Aspose.Email for .NET: Aspose.Email for .NET kitaplığını şu adresten indirin ve yükleyin:[Aspose sürüm sayfası](https://releases.aspose.com/email/net/).
3. .NET Framework: Bilgisayarınızda .NET Framework'ün yüklü olduğundan emin olun.
4. SMTP Sunucusu: E-posta göndermek için bir SMTP sunucusuna erişmeniz gerekir.

## Ad Alanlarını İçe Aktar

Projenizde Aspose.Words ve Aspose.Email kullanmak için gerekli ad alanlarını içe aktarmanız gerekir. Aşağıdaki using yönergelerini C# dosyanızın en üstüne ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Her bir bölümü net bir şekilde anlayabilmeniz için süreci birden fazla adıma bölelim.

## Adım 1: DOCX Belgesini Yükleyin

 Öncelikle dönüştürmek istediğiniz DOCX belgesini yüklemeniz gerekir.`Document` DOCX dosyanızı yüklemek için Aspose.Words'den sınıf.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Adım 2: Belgeyi MHTML olarak kaydedin

 Sonra, yüklenen belgeyi bir MHTML dosyası olarak kaydedin. Bu, şu şekilde yapılır:`Save` yöntemi`Document` sınıf.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Yayını başa sar, böylece Aspose.Email okuyabilir.
stream.Position = 0;
```

## Adım 3: Bir E-posta Mesajı Oluşturun

 Şimdi, Aspose.Email kullanarak MHTML akışından bir e-posta mesajı oluşturun.`MailMessage` Bu amaçla sınıf.

```csharp
// Akıştan bir Aspose.Email MIME e-posta mesajı oluşturun.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Adım 4: E-postayı gönderin

 Son olarak, e-postayı bir SMTP istemcisi kullanarak gönderin. SMTP istemcisini SMTP sunucunuzun ayrıntılarıyla yapılandırın ve`Send` Mesajı gönderme yöntemi.

```csharp
// Mesajı Aspose.Email kullanarak gönderin.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Çözüm

Tebrikler! Bir DOCX belgesini MHTML'ye başarıyla dönüştürdünüz ve Aspose.Words for .NET kullanarak e-postayla gönderdiniz. Bu işlem belgeyi yüklemeyi, MHTML'ye dönüştürmeyi, bir e-posta mesajı oluşturmayı ve bir SMTP istemcisi kullanarak göndermeyi içerir. Bu adımlarla, uygulamalarınızdaki belgelerin dönüştürülmesini ve e-postayla gönderilmesini kolayca otomatikleştirebilirsiniz.

## SSS

### Bu yöntemi diğer belge biçimlerini dönüştürmek için kullanabilir miyim?
Evet, Aspose.Words çeşitli formatları destekler ve DOC, DOCX, RTF ve daha fazlası gibi belgeleri MHTML'ye dönüştürebilirsiniz.

### E-postaya nasıl ek ekleyebilirim?
 Kullanabilirsiniz`Attachments` mülkiyeti`MailMessage` E-postanıza ekler eklemek için sınıf.

### Aspose.Words .NET Core ile uyumlu mu?
Evet, Aspose.Words .NET Core ile uyumludur. .NET Core uygulamalarında da kullanabilirsiniz.

### Aspose.Words ve Aspose.Email için lisansa ihtiyacım var mı?
 Evet, her iki kütüphane de lisans gerektirir. Geçici bir lisansı şuradan alabilirsiniz:[Aspose satın alma sayfası](https://purchase.aspose.com/temporary-license/) Değerlendirme amaçlı.

### Daha fazla dokümanı nerede bulabilirim?
 Aspose.Words için ayrıntılı dokümanları bulabilirsiniz[Burada](https://reference.aspose.com/words/net/) ve Aspose.Email için[Burada](https://reference.aspose.com/email/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
