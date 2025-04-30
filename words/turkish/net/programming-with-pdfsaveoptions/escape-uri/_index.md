---
"description": "Aspose.Words for .NET kullanarak PDF'lerdeki URI'lerden nasıl kaçacağınızı öğrenin. Bu ayrıntılı kılavuz sizi adım adım süreçte yönlendirir."
"linktitle": "PDF Belgesinde URI'den Kaçış"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "PDF Belgesinde URI'den Kaçış"
"url": "/tr/net/programming-with-pdfsaveoptions/escape-uri/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# PDF Belgesinde URI'den Kaçış

## giriiş

Merhaba! Aspose.Words for .NET kullanarak bir Word belgesini PDF olarak kaydederken URI'lerin nasıl işleneceğini hiç merak ettiniz mi? Doğru yerdesiniz! Bugün, belgeniz dönüştürüldüğünde doğru şekilde çalışmasını sağlamak için PDF belgelerindeki URI'lerden kaçmayı derinlemesine inceleyeceğiz. Bu yolculuğa birlikte adım adım çıkalım ve yol boyunca her kavramı kavradığınızdan emin olalım.

## Ön koşullar

Başlamadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1. Aspose.Words for .NET: En son sürüme sahip olduğunuzdan emin olun. İndirebilirsiniz [Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio veya herhangi bir .NET geliştirme ortamı.
3. Temel C# Bilgisi: Bu eğitimde C# programlama hakkında temel bir anlayışa sahip olduğunuzu varsayıyoruz.

## Ad Alanlarını İçe Aktar

İlk önce, gerekli ad alanlarını içe aktarmanız gerekir. Bu, Aspose.Words işlevlerine erişmek için çok önemlidir.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Tamam, süreci sindirilebilir adımlara bölelim. Takip edin ve kısa sürede URI'lerden kaçmada uzman olacaksınız!

## Adım 1: Belge Dizininizi Ayarlayın

Koda dalmadan önce, belgeler dizininize giden yolu ayarlayın. Dosyalarınız buraya kaydedilecektir.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Yer değiştirmek `"YOUR DOCUMENT DIRECTORY"` PDF belgenizi kaydetmek istediğiniz gerçek yol ile.

## Adım 2: Yeni Bir Belge Oluşturun

Sonra, Aspose.Words kullanarak yeni bir belge oluşturacağız. Bu belge, köprü metinleri eklemek için tuvalimiz olarak hizmet edecek.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Burada, `Document` yeni Word belgeniz ve `DocumentBuilder` belge oluşturma sürecini basitleştiren bir yardımcı sınıftır.

## Adım 3: Bir Köprü Bağlantısı Ekleyin

Şimdi, belgeye bir köprü metni ekleyelim. Bu köprü metni, URI kaçış sürecimizin odak noktası olacak.

```csharp
builder.InsertHyperlink("Testlink", "https://www.google.com/search?q= aspose", false);
```

Bu satırda, `"Testlink"` köprü metni için görüntü metnidir ve `"https://www.google.com/search?q= aspose"` URL'dir. `false` parametresi, bağlantının bir köprü metni olarak biçimlendirilmemesi gerektiğini belirtir (yani, altı çizili ve mavi olmaz).

## Adım 4: Belgeyi PDF olarak kaydedin

Son olarak, belgeyi PDF olarak kaydedin. Aspose.Words'ün PDF çıktısında URI'yi kaçırmakla ilgilendiği yer burasıdır.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EscapeUri.pdf");
```

Bu satır, belgeyi belirtilen dizine dosya adıyla kaydeder `WorkingWithPdfSaveOptions.EscapeUri.pdf`.

## Çözüm

Ve işte oldu! Aspose.Words for .NET kullanarak bir Word belgesini PDF olarak kaydederken URI'lerden nasıl kaçacağınızı öğrendiniz. Bu işlem, köprülerinizin işlevsel kalmasını ve ortaya çıkan PDF'de düzgün biçimlendirilmesini sağlar. 

Unutmayın, bu küçük ama önemli tekniklerde ustalaşmak belgelerinizin kalitesini ve işlevselliğini büyük ölçüde artırabilir. Mutlu kodlama!

## SSS

### Aspose.Words for .NET nedir?

Aspose.Words for .NET, geliştiricilerin .NET uygulamalarında Word belgeleri oluşturmasına, düzenlemesine ve dönüştürmesine olanak tanıyan güçlü bir kütüphanedir.

### PDF'lerde URI kaçışının önemi nedir?

URI kaçışı, URL'lerdeki özel karakterlerin doğru yorumlanmasını sağlayarak, bozuk bağlantıları önler ve amaçlandığı gibi çalışmasını garantiler.

### Aspose.Words for .NET'te başka tür bağlantılar kullanabilir miyim?

Kesinlikle! Aspose.Words, dahili belge bağlantıları, yer imleri ve harici URL'ler dahil olmak üzere çeşitli bağlantı türlerini destekler.

### Aspose.Words for .NET'in ücretsiz deneme sürümünü nasıl edinebilirim?

Ücretsiz deneme alabilirsiniz [Burada](https://releases.aspose.com/).

### Aspose.Words for .NET hakkında daha detaylı dokümanları nerede bulabilirim?

Ayrıntılı dokümantasyonu bulabilirsiniz [Burada](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}