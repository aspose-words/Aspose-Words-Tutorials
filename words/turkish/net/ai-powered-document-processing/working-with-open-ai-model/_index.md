---
"description": "OpenAI'nin güçlü modelleriyle Aspose.Words for .NET'i kullanarak verimli belge özetlemenin kilidini açın. Şimdi bu kapsamlı kılavuza dalın."
"linktitle": "Açık AI Modeli ile Çalışma"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Açık AI Modeli ile Çalışma"
"url": "/tr/net/ai-powered-document-processing/working-with-open-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Açık AI Modeli ile Çalışma

## giriiş

Günümüzün dijital dünyasında içerik kraldır. İster öğrenci, ister iş profesyoneli veya hevesli bir yazar olun, belgeleri etkili bir şekilde düzenleme, özetleme ve oluşturma becerisi paha biçilemezdir. İşte tam bu noktada Aspose.Words for .NET kütüphanesi devreye girerek belgeleri bir profesyonel gibi yönetmenizi sağlar. Bu kapsamlı eğitimde, belgeleri etkili bir şekilde özetlemek için Aspose.Words'ü OpenAI modelleriyle birlikte nasıl kullanacağınızı derinlemesine inceleyeceğiz. Belge yönetimi potansiyelinizi açığa çıkarmaya hazır mısınız? Hadi başlayalım!

## Ön koşullar

Kolları sıvayıp kodlara dalmadan önce, yerinde olması gereken birkaç temel şey var:

### .NET Çerçevesi
Aspose.Words ile uyumlu bir .NET framework sürümünde çalıştığınızdan emin olun. Genellikle .NET 5.0 ve üzeri mükemmel çalışmalıdır.

### Aspose.Words for .NET Kütüphanesi
Aspose.Words kütüphanesini indirip yüklemeniz gerekecek. Bunu şuradan edinebilirsiniz: [bu bağlantı](https://releases.aspose.com/words/net/).

### OpenAI API Anahtarı
Belge özetleme için OpenAI'nin dil modellerini entegre etmek için bir API Anahtarına ihtiyacınız olacak. Bunu OpenAI platformuna kaydolarak ve anahtarınızı hesap ayarlarınızdan alarak alabilirsiniz.

### Geliştirme için IDE
Visual Studio gibi bir Entegre Geliştirme Ortamı (IDE) kurmak, .NET uygulamaları geliştirmek için idealdir.

### Temel Programlama Bilgisi
C# ve nesne yönelimli programlamaya dair temel bir anlayışa sahip olmak, kavramları daha kolay kavramanıza yardımcı olacaktır.

## Paketleri İçe Aktar

Artık her şeyi sıraladığımıza göre, paketlerimizi içe aktaralım. Visual Studio projenizi açın ve gerekli kütüphaneleri ekleyin. Bunu nasıl yapabileceğinizi burada bulabilirsiniz:

### Aspose.Words Paketini Ekle

Aspose.Words paketini NuGet Paket Yöneticisi aracılığıyla ekleyebilirsiniz. Bunu şu şekilde yapabilirsiniz:
- Çözüm için Araçlar -> NuGet Paket Yöneticisi -> NuGet Paketlerini Yönet'e gidin.
- "Aspose.Words"ü arayın ve Yükle'ye tıklayın.

### Sistem Ortamını Ekle

Şunları eklediğinizden emin olun: `System` çevre değişkenlerini işlemek için ad alanı:
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### Aspose.Words'ü ekleyin

Daha sonra Aspose.Words ad alanını C# dosyanıza ekleyin:
```csharp
using Aspose.Words;
```

### OpenAI Kütüphanesini Ekle

OpenAI ile arayüz oluşturmak için bir kütüphane kullanıyorsanız (REST istemcisi gibi), bunu da eklediğinizden emin olun. Bunu, Aspose.Words'ü eklediğimiz şekilde NuGet üzerinden eklemeniz gerekebilir.

Ortamımızı hazırladığımıza ve gerekli paketleri içe aktardığımıza göre, şimdi belge özetleme sürecini adım adım inceleyelim.

## Adım 1: Belge Dizinlerinizi Tanımlayın

Belgelerinizle oynamaya başlamadan önce, belgelerinizin ve eserlerinizin bulunacağı dizinleri ayarlamanız gerekir:

```csharp
// Belge Dizininiz
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Eserler Dizininiz
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
Bu, gerektiğinde yolları kolayca değiştirebildiğiniz için kodunuzu daha yönetilebilir hale getirir. `MyDir` giriş belgelerinizin saklandığı yer burasıdır, `ArtifactsDir` Oluşturulan özetleri kaydedeceğiniz yer burasıdır.

## Adım 2: Belgelerinizi Yükleyin

Sonra, özetlemek istediğiniz belgeleri yükleyeceksiniz. Bu, Aspose.Words ile basittir:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
Belgelerinizin adlarının kullanmayı planladığınız adlarla eşleştiğinden emin olun, aksi takdirde hatalarla karşılaşırsınız!

## Adım 3: API Anahtarınızı Alın

Artık belgeleriniz yüklendiğine göre, OpenAI API anahtarınızı çekme zamanı. Bunu güvenli tutmak için ortam değişkenlerinden alacaksınız:
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
Yetkisiz kullanıcıları uzak tutmak için API anahtarınızı güvenli bir şekilde yönetmeniz önemlidir.

## Adım 4: Bir OpenAI Model Örneği Oluşturun

API anahtarınız hazır olduğunda artık OpenAI modelinin bir örneğini oluşturabilirsiniz. Belge özetleme için Gpt4OMini modelini kullanacağız:

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
Bu adım, belgelerinizi özetlemek için gereken beyin gücünü oluşturarak, yapay zeka destekli özetleme olanağı sağlar.

## Adım 5: Tek Bir Belgeyi Özetleyin

İlk önce ilk belgeyi özetleyelim. Sihir burada gerçekleşiyor:

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
Burada şunu kullanıyoruz: `Summarize` modelin yöntemi. `SummaryLength.Short` parametresi kısa bir özet istediğimizi belirtiyor — hızlı bir genel bakış için mükemmel!

## Adım 6: Birden Fazla Belgeyi Özetleyin

Hırslı hissediyor musunuz? Birden fazla belgeyi aynı anda özetleyebilirsiniz. Ne kadar kolay olduğuna bir bakın:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
Bu özellik özellikle birden fazla dosyayı karşılaştırmak için kullanışlıdır. Belki bir toplantıya hazırlanıyorsunuz ve birkaç uzun rapordan özlü notlara ihtiyacınız var. Bu sizin yeni en iyi arkadaşınız!

## Çözüm

Aspose.Words for .NET ve OpenAI ile belgeleri özetlemek yalnızca yararlı bir beceri değil; aynı zamanda oldukça güçlendirici. Bu kılavuzu izleyerek, uzun ve karmaşık metinleri özlü özetlere dönüştürdünüz ve kendinize zaman ve emek kazandırdınız. İster müşterileriniz için netlik sağlayın, ister o önemli sunuma hazırlanın, artık bunu verimli bir şekilde yapmak için gereken araçlara sahipsiniz.

Öyleyse ne bekliyorsunuz? Belgelerinize güvenle dalın ve ağır işi teknolojiye bırakın!

## SSS

### Aspose.Words for .NET nedir?  
Aspose.Words for .NET, geliştiricilerin belgeleri programlı bir şekilde oluşturmasını, düzenlemesini ve dönüştürmesini sağlayan güçlü bir kütüphanedir.

### OpenAI için API anahtarına ihtiyacım var mı?  
Evet, modellerini kullanarak özetleme yeteneklerine erişmek için geçerli bir OpenAI API anahtarına sahip olmanız gerekir.

### Birden fazla belgeyi aynı anda özetleyebilir miyim?  
Kesinlikle! Tek bir çağrıda birden fazla belgeyi özetleyebilirsiniz, bu da kapsamlı raporlar için idealdir.

### Aspose.Words'ü nasıl kurarım?  
Visual Studio'daki NuGet Paket Yöneticisi'ni kullanarak "Aspose.Words" ifadesini aratarak kurulumunu yapabilirsiniz.

### Aspose.Words için ücretsiz deneme sürümü var mı?  
Evet, Aspose.Words'ün ücretsiz deneme sürümüne şu adresten erişebilirsiniz: [web sitesi](https://releases.aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}