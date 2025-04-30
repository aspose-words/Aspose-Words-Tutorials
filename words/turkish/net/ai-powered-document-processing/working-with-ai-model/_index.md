---
"description": "Belgeleri AI ile özetlemek için Aspose.Words for .NET'i nasıl kullanacağınızı öğrenin. Belge yönetimini geliştirmek için kolay adımlar."
"linktitle": "AI Modeli ile Çalışma"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "AI Modeli ile Çalışma"
"url": "/tr/net/ai-powered-document-processing/working-with-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# AI Modeli ile Çalışma

## giriiş

Aspose.Words for .NET'in büyüleyici dünyasına hoş geldiniz! Belge yönetimini bir üst seviyeye taşımayı hiç istediyseniz, doğru yerdesiniz. Sadece birkaç satır kodla büyük belgeleri otomatik olarak özetleme yeteneğine sahip olduğunuzu hayal edin. Kulağa harika geliyor, değil mi? Bu kılavuzda, OpenAI'nin GPT'si gibi güçlü AI dil modelleri kullanarak belgelerin özetlerini oluşturmak için Aspose.Words'ü derinlemesine inceliyoruz. Uygulamalarınızı geliştirmek isteyen bir geliştirici veya yeni bir şeyler öğrenmek isteyen bir teknoloji meraklısı olun, bu eğitim tam size göre.

## Ön koşullar

Kolları sıvayıp kodlamaya başlamadan önce, elinizde olması gereken birkaç temel şey var:

1. Visual Studio Kurulu: Bilgisayarınızda Visual Studio'nun kurulu olduğundan emin olun. Zaten yüklü değilse ücretsiz olarak indirebilirsiniz.
  
2. .NET Framework: Aspose.Words için .NET Framework'ün uyumlu bir sürümünü kullandığınızdan emin olun. Hem .NET Framework'ü hem de .NET Core'u destekler.

3. .NET için Aspose.Words: Aspose.Words'ü indirip yüklemeniz gerekecek. En son sürümü edinebilirsiniz [Burada](https://releases.aspose.com/words/net/).

4. AI Modelleri için Bir API Anahtarı: AI özetini kullanmak için bir AI modeline erişmeniz gerekir. API anahtarınızı OpenAI veya Google gibi platformlardan alın.

5. Temel C# Bilgisi: Bu eğitimden en iyi şekilde faydalanmak için C# programlamanın temellerine dair bir anlayışa sahip olmak gerekir.

Her şey hazır mı? Harika! Eğlenceli kısma geçelim - gerekli paketlerimizi içe aktaralım.

## Paketleri İçe Aktar

Aspose.Words'ün güçlerinden yararlanmak ve AI modelleriyle çalışmak için, gerekli paketleri içe aktararak başlıyoruz. İşte nasıl yapılacağı:

### Yeni Bir Proje Oluştur

Öncelikle Visual Studio'yu başlatıp yeni bir Konsol Uygulaması projesi oluşturalım.

1. Visual Studio’yu açın.
2. “Yeni proje oluştur”a tıklayın.
3. Kurulumunuza bağlı olarak “Konsol Uygulaması (.NET Framework)” veya “Konsol Uygulaması (.NET Core)” seçeneğini belirleyin.
4. Projenize bir isim verin ve lokasyonunu belirtin.

### Aspose.Words ve AI Model Paketlerini Yükleyin

Aspose.Words'ü kullanmak için paketi NuGet üzerinden yüklemeniz gerekiyor.

1. Çözüm Gezgini’nde projenize sağ tıklayın ve “NuGet Paketlerini Yönet” seçeneğini seçin.
2. “Aspose.Words”ü arayın ve “Yükle”ye tıklayın.
3. Herhangi bir özel AI model paketi (OpenAI gibi) kullanıyorsanız, bunların da kurulu olduğundan emin olun.
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```
Tebrikler! Paketler hazır olduğuna göre, uygulamamıza daha derinlemesine inelim.

## Adım 1: Belge Dizinlerinizi Ayarlayın

Kodumuzda, belgelerimizin nerede saklanacağını ve çıktılarımızın nereye gideceğini yönetmek için dizinleri tanımlayacağız. 

```csharp
// Belge Dizininiz
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// ArtifactsDir Dizininiz
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

- Burada, değiştirin `YOUR_DOCUMENT_DIRECTORY` belgelerinizin saklandığı yer ve `YOUR_ARTIFACTS_DIRECTORY` özetlenen dosyaları kaydetmek istediğiniz yer.

## Adım 2: Belgeleri Yükleyin

Daha sonra özetlemek istediğimiz belgeleri programımıza yükleyeceğiz. Bu çocuk oyuncağı! İşte nasıl:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

- Dosya adlarını kaydettiğiniz şeye göre ayarlayın. Örnek, “Big document.docx” ve “Document.docx” adlı iki belgeniz olduğunu varsayar.

## Adım 3: AI Modelini Başlatın

Bir sonraki adımımız AI modeliyle bir bağlantı kurmaktır. Daha önce aldığınız API anahtarının devreye girdiği yer burasıdır.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

- API anahtarınızın bir ortam değişkeni olarak saklandığından emin olun. Bu, gizli sosunuzu güvende tutmak gibidir!

## Adım 4: İlk Belge için Bir Özet Oluşturun

Şimdi ilk belgemiz için bir özet oluşturalım. Özet uzunluğunu tanımlamak için parametreler de belirleyeceğiz.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

- Bu kod parçası ilk belgeyi özetler ve çıktıyı belirtilen yapıtlar dizininize kaydeder. Özet uzunluğunu istediğiniz gibi değiştirmekten çekinmeyin!

## Adım 5: Birden Fazla Belge İçin Bir Özet Oluşturun

Maceracı hissediyor musunuz? Ayrıca birden fazla belgeyi aynı anda özetleyebilirsiniz! İşte nasıl yapacağınız:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

- İşte böyle, aynı anda iki belgeyi özetliyorsunuz! Verimlilikten bahsediyorsunuz, değil mi?

## Çözüm

İşte karşınızda! Bu kılavuzu takip ederek, .NET için Aspose.Words ve güçlü AI modellerini kullanarak belgeleri özetleme sanatında ustalaştınız. Kişisel kullanım veya profesyonel uygulamalara entegre etme olsun, size tonlarca zaman kazandırabilecek heyecan verici bir özellik. Hadi, otomasyonun gücünü serbest bırakın ve üretkenliğinizin nasıl yükseldiğini izleyin!

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, geliştiricilerin Word belgelerini programlı bir şekilde oluşturmalarına, değiştirmelerine, dönüştürmelerine ve işlemelerine olanak tanıyan güçlü bir kütüphanedir.

### Yapay zeka modelleri için API anahtarı nasıl edinebilirim?
OpenAI veya Google gibi AI sağlayıcılarından bir API anahtarı edinebilirsiniz. Bir hesap oluşturduğunuzdan ve anahtarınızı oluşturmak için talimatlarını izlediğinizden emin olun.

### Aspose.Words'ü diğer dosya formatlarında kullanabilir miyim?
Evet! Aspose.Words, DOCX, RTF ve HTML dahil olmak üzere çeşitli dosya biçimlerini destekleyerek, yalnızca metin belgelerinin ötesinde kapsamlı yetenekler sunar.

### Aspose.Words'ün ücretsiz bir versiyonu var mı?
Aspose, özelliklerini test etmenize olanak tanıyan ücretsiz bir deneme sunuyor. Bunu sitelerinden indirebilirsiniz.

### Aspose.Words için daha fazla kaynağı nerede bulabilirim?
Belgeleri kontrol edebilirsiniz [Burada](https://reference.aspose.com/words/net/) Kapsamlı rehberler ve içgörüler için.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}