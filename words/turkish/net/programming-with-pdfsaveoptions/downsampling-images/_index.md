---
"description": "Aspose.Words for .NET kullanarak görüntüleri alt örnekleme yoluyla PDF belge boyutunu azaltın. PDF'lerinizi daha hızlı yükleme ve indirme süreleri için optimize edin."
"linktitle": "Görüntüleri Aşağı Örnekleme ile PDF Belge Boyutunu Azaltın"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Görüntüleri Aşağı Örnekleme ile PDF Belge Boyutunu Azaltın"
"url": "/tr/net/programming-with-pdfsaveoptions/downsampling-images/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Görüntüleri Aşağı Örnekleme ile PDF Belge Boyutunu Azaltın

## giriiş

PDF'ler dijital dünyanın olmazsa olmazıdır ve belge paylaşımından e-kitap oluşturmaya kadar her şey için kullanılır. Ancak, boyutları bazen bir engel olabilir, özellikle de görsel zengin içeriklerle uğraşırken. Görüntüleri örneklemlemenin devreye girdiği yer burasıdır. PDF içindeki görüntülerin çözünürlüğünü düşürerek, kaliteyi çok fazla düşürmeden dosya boyutunu önemli ölçüde azaltabilirsiniz. Bu eğitimde, bunu .NET için Aspose.Words kullanarak başarmak için gereken adımları ele alacağız.

## Ön koşullar

Koda geçmeden önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1. Aspose.Words for .NET: Aspose.Words kütüphanesinin yüklü olduğundan emin olun. Değilse, indirebilirsiniz [Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio gibi herhangi bir .NET geliştirme ortamı.
3. Temel C# Bilgisi: C# programlamanın temellerini anlamak faydalı olacaktır.
4. Örnek Belge: Bir Word belgesi (örneğin, `Rendering.docx`) PDF'ye dönüştürülecek görsellerle.

## Ad Alanlarını İçe Aktar

İlk önce, gerekli ad alanlarını içe aktarmanız gerekir. Bunları kod dosyanızın en üstüne ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Şimdi süreci yönetilebilir adımlara bölelim.

## Adım 1: Belgeyi Yükleyin

İlk adım Word belgenizi yüklemektir. Burada belge dizininize giden yolu belirtirsiniz.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Bu adımda, Word belgesini belirtilen dizinden yüklüyoruz. Değiştirdiğinizden emin olun `"YOUR DOCUMENT DIRECTORY"` Belgenizin bulunduğu gerçek yol ile.

## Adım 2: Alt Örnekleme Seçeneklerini Yapılandırın

Sonra, alt örnekleme seçeneklerini yapılandırmamız gerekiyor. Bu, görüntüler için çözünürlüğü ve çözünürlük eşiğini ayarlamayı içerir.

```csharp
// Aşağı örnekleme için minimum bir eşik değeri belirleyebiliriz.
// Bu değer, giriş belgesindeki ikinci görüntünün küçültülmesini önleyecektir.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    DownsampleOptions = { Resolution = 36, ResolutionThreshold = 128 }
};
```

Burada, yeni bir örnek oluşturuyoruz `PdfSaveOptions` ve ayarlama `Resolution` 36 DPI'a ve `ResolutionThreshold` 128 DPI'a kadar. Bu, çözünürlüğü 128 DPI'dan yüksek olan herhangi bir görüntünün 36 DPI'a düşürüleceği anlamına gelir.

## Adım 3: Belgeyi PDF olarak kaydedin

Son olarak yapılandırdığımız seçeneklerle belgeyi PDF olarak kaydediyoruz.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DownsamplingImages.pdf", saveOptions);
```

Bu son adımda, belgeyi belirtilen alt örnekleme seçenekleriyle aynı dizine PDF olarak kaydediyoruz.

## Çözüm

Ve işte karşınızda! Aspose.Words for .NET kullanarak görüntüleri alt örnekleme yoluyla PDF'nizin boyutunu başarıyla küçülttünüz. Bu yalnızca PDF'lerinizi daha yönetilebilir hale getirmekle kalmaz, aynı zamanda daha hızlı yüklemelere, indirmelere ve daha akıcı görüntüleme deneyimlerine de yardımcı olur.

## SSS

### Aşağı örnekleme nedir?
Örneklemeyi azaltma, görüntülerin çözünürlüğünü azaltma işlemidir ve bu da söz konusu görüntüleri içeren belgelerin dosya boyutunun küçültülmesine yardımcı olur.

### Örneklemeyi azaltma işlemi görüntülerin kalitesini etkiler mi?
Evet, alt örnekleme görüntü kalitesini düşürecektir. Ancak, etkisi çözünürlük azaltma derecesine bağlıdır. Bu, dosya boyutu ve görüntü kalitesi arasındaki bir dengedir.

### Hangi görüntülerin küçültüleceğini seçebilir miyim?
Evet, ayarlayarak `ResolutionThreshold`, orijinal çözünürlüklerine göre hangi görüntülerin küçültüleceğini kontrol edebilirsiniz.

### Alt örnekleme için ideal çözünürlük nedir?
İdeal çözünürlük, özel ihtiyaçlarınıza bağlıdır. Genellikle, web görüntüleri için 72 DPI kullanılırken, daha yüksek çözünürlükler baskı kalitesi için kullanılır.

### Aspose.Words for .NET ücretsiz mi?
Aspose.Words for .NET ticari bir üründür, ancak ücretsiz deneme sürümünü indirebilirsiniz [Burada](https://releases.aspose.com/) veya başvuruda bulunun [geçici lisans](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}