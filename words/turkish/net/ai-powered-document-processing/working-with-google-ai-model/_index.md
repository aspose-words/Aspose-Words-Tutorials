---
"description": "Aspose.Words for .NET ve Google AI ile belge işleme sürecinizi bir üst seviyeye taşıyın ve zahmetsizce özlü özetler oluşturun."
"linktitle": "Google AI Modeli ile Çalışma"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Google AI Modeli ile Çalışma"
"url": "/tr/net/ai-powered-document-processing/working-with-google-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Google AI Modeli ile Çalışma

## giriiş

Bu makalede, Aspose.Words ve Google'ın AI modellerini kullanarak belgelerin nasıl adım adım özetleneceğini inceleyeceğiz. Uzun bir raporu yoğunlaştırmak veya birden fazla kaynaktan içgörüler çıkarmak istiyorsanız, sizin için buradayız.

## Ön koşullar

Pratik kısma dalmadan önce, başarıya hazır olduğunuzdan emin olalım. İhtiyacınız olanlar şunlardır:

1. Temel C# ve .NET Bilgisi: Programlama kavramlarına aşinalık, örnekleri daha iyi kavramanıza yardımcı olacaktır.
   
2. Aspose.Words for .NET Kütüphanesi: Bu güçlü kütüphane, Word belgelerini sorunsuz bir şekilde oluşturmanıza ve düzenlemenize olanak tanır. [buradan indirin](https://releases.aspose.com/words/net/).

3. Google AI Modeli için API Anahtarı: AI modellerini kullanmak için kimlik doğrulaması için bir API anahtarına ihtiyacınız var. Bunu ortam değişkenlerinizde güvenli bir şekilde saklayın.

4. Geliştirme Ortamı: Çalışan bir .NET ortamının (Visual Studio veya başka bir IDE) kurulu olduğundan emin olun.

5. Örnek Belge: Özetlemeyi test etmek için örnek Word belgelerine (örneğin, "Büyük belge.docx", "Belge.docx") ihtiyacınız olacak.

Temelleri ele aldığımıza göre şimdi koda geçelim!

## Paketleri İçe Aktar

Aspose.Words ile çalışmak ve Google AI modellerini entegre etmek için gerekli ad alanlarını içe aktarmanız gerekir. Bunu şu şekilde yapabilirsiniz:

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Artık gerekli paketler içe aktarıldığına göre, belgeleri özetleme sürecini adım adım inceleyelim.

## Adım 1: Belge Dizininizi Ayarlama

Belgeleri işlemeden önce dosyalarımızın nerede bulunduğunu belirtmemiz gerekir. Bu adım, Aspose.Words'ün belgelere erişebilmesini sağlamak için çok önemlidir.

```csharp
// Belge Dizininiz
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// ArtifactsDir Dizininiz
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

Yer değiştirmek `"YOUR_DOCUMENT_DIRECTORY"` Ve `"YOUR_ARTIFACTS_DIRECTORY"` belgelerinizin saklandığı sisteminizdeki gerçek yollarla. Bu, belgeleri okumak ve kaydetmek için temel oluşturacaktır.

## Adım 2: Belgeleri Yükleme

Daha sonra özetlemek istediğimiz belgeleri yüklememiz gerekiyor. Bu durumda, daha önce belirttiğimiz iki belgeyi yükleyeceksiniz.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

The `Document` Aspose.Words'den gelen sınıf, Word dosyalarını belleğe yüklemenize olanak tanır. Dosya adlarının dizininizdeki gerçek belgelerle eşleştiğinden emin olun, aksi takdirde dosya bulunamadı hatalarıyla karşılaşırsınız!

## Adım 3: API Anahtarını Alma

AI modelini kullanmak için API Anahtarınızı almanız gerekir. Bu, Google AI hizmetlerine erişim geçişiniz olarak işlev görür.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

Bu kod satırı, ortam değişkenlerinizde sakladığınız API anahtarını getirir. Güvenlik nedeniyle API anahtarları gibi hassas bilgileri kodunuzun dışında tutmak iyi bir uygulamadır.

## Adım 4: Bir AI Model Örneği Oluşturma

Şimdi, AI modelinin bir örneğini oluşturma zamanı. Burada hangi modeli kullanacağınızı seçebilirsiniz—bu örnekte, GPT-4 Mini modelini tercih ediyoruz.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

Bu satır, belge özetleme için kullanacağınız AI modelini belirler. Danıştığınızdan emin olun [belgeler](https://reference.aspose.com/words/net/) Farklı modeller ve yetenekleri hakkında ayrıntılı bilgi için.

## Adım 5: Tek Bir Belgeyi Özetleme

İlk belgeyi özetlemeye odaklanalım. Burada kısa bir özet almayı seçebiliriz.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

Bu adımda şunu kullanırız: `Summarize` AI model örneğinden ilk belgenin yoğunlaştırılmış halini almak için yöntem. Özet uzunluğu kısa olarak ayarlanmıştır, ancak bunu ihtiyaçlarınıza göre özelleştirebilirsiniz. Son olarak, özetlenen belge yapıtlar dizininize kaydedilir.

## Adım 6: Birden Fazla Belgeyi Özetleme

Birden fazla belgeyi aynı anda özetlemek mi istiyorsunuz? Aspose.Words bunu da kolaylaştırır!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

Burada, şunu çağırıyoruz: `Summarize` yöntem yine, ancak bu sefer bir dizi belgeyle. Bu size her iki dosyanın özünü kapsayan uzun bir özet verecektir. Daha önce olduğu gibi, sonuç belirtilen artifacts dizinine kaydedilir.

## Çözüm

Ve işte karşınızda! Aspose.Words for .NET ve Google'ın AI modellerini kullanarak belgeleri özetlemek için bir ortamı başarıyla kurdunuz. Belgeleri yüklemekten özlü özetler oluşturmaya kadar, bu adımlar büyük miktarda metni etkili bir şekilde yönetmek için kolaylaştırılmış bir yaklaşım sunar.

## SSS

### Aspose.Words nedir?
Aspose.Words, .NET kullanarak Word belgeleri oluşturmak, değiştirmek ve dönüştürmek için güçlü bir kütüphanedir.

### Google AI için API anahtarı nasıl alabilirim?
Genellikle Google Cloud'a kaydolup gerekli API servislerini etkinleştirerek bir API anahtarı edinebilirsiniz.

### Birden fazla belgeyi aynı anda özetleyebilir miyim?
Evet! Gösterildiği gibi, özetleme metoduna bir dizi belge geçirebilirsiniz.

### Hangi tür özetler oluşturabilirim?
İhtiyaçlarınıza göre kısa, orta ve uzun özetler arasından seçim yapabilirsiniz.

### Daha fazla Aspose.Words kaynağını nerede bulabilirim?
Şuna bir göz atın: [belgeleme](https://reference.aspose.com/words/net/) Daha fazla örnek ve rehberlik için.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}