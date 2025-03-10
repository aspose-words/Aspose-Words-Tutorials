---
title: Biçim 1Bpp Dizinli
linktitle: Biçim 1Bpp Dizinli
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak bir Word belgesini 1Bpp dizinli bir görüntüye nasıl dönüştüreceğinizi öğrenin. Kolay dönüşüm için adım adım kılavuzumuzu izleyin.
weight: 10
url: /tr/net/programming-with-imagesaveoptions/format-1bpp-indexed/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Biçim 1Bpp Dizinli

## giriiş

Hiç Word belgesini sadece birkaç satır kodla siyah beyaz bir resim olarak nasıl kaydedeceğinizi merak ettiniz mi? Şanslısınız! Bugün, belgelerinizi 1Bpp dizinli resimlere dönüştürmenizi sağlayan Aspose.Words for .NET'i kullanarak şık bir küçük numaraya dalacağız. Bu format, belirli dijital arşivleme, yazdırma veya yerden tasarruf etmeniz gerektiğinde mükemmeldir. Her adımı, çocuk oyuncağı haline getirmek için parçalara ayıracağız. Başlamaya hazır mısınız? Hadi başlayalım!

## Ön koşullar

Ellerimizi kirletmeden önce, yerinde olması gereken birkaç şey var:

-  Aspose.Words for .NET: Kütüphanenin kurulu olduğundan emin olun.[buradan indirin](https://releases.aspose.com/words/net/).
- .NET Geliştirme Ortamı: Visual Studio iyi bir seçenektir, ancak kendinizi rahat hissettiğiniz herhangi bir ortamı kullanabilirsiniz.
- Temel C# Bilgisi: Merak etmeyin, basit tutacağız ancak C# konusunda biraz bilgi sahibi olmak faydalı olacaktır.
- Word Belgesi: Dönüştürülmeye hazır bir örnek Word belgesi bulundurun.

## Ad Alanlarını İçe Aktar

İlk önce gerekli ad alanlarını içe aktarmamız gerekiyor. Bu önemlidir çünkü Aspose.Words'den ihtiyaç duyduğumuz sınıflara ve yöntemlere erişmemizi sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Adım 1: Belge Dizininizi Ayarlayın

Belge dizininize giden yolu belirtmeniz gerekecektir. Word belgenizin saklandığı ve dönüştürülen görüntünün kaydedileceği yer burasıdır.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Adım 2: Word Belgesini Yükleyin

 Şimdi Word belgesini bir Aspose.Words'e yükleyelim`Document` nesne. Bu nesne Word dosyanızı temsil eder ve onu düzenlemenize olanak tanır.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Adım 3: Görüntü Kaydetme Seçeneklerini Yapılandırın

 Daha sonra, şunu ayarlamamız gerekiyor:`ImageSaveOptions`Sihir burada gerçekleşir. Görüntüyü 1Bpp dizinli renk moduyla PNG formatında kaydedecek şekilde yapılandıracağız.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: Bu, belgeyi PNG resmi olarak kaydetmek istediğimizi belirtir.
- PageSet(1): Bu yalnızca ilk sayfayı dönüştürdüğümüzü gösterir.
- ImageColorMode.BlackAndWhite: Bu, görüntüyü siyah beyaza ayarlar.
- ImagePixelFormat.Format1bppIndexed: Bu, görüntü formatını 1Bpp indeksli olarak ayarlar.

## Adım 4: Belgeyi Görüntü Olarak Kaydedin

 Son olarak, belgeyi bir resim olarak kaydediyoruz`Save` yöntemi`Document` nesne.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Çözüm

Ve işte karşınızda! Sadece birkaç satır kodla, Word belgenizi Aspose.Words for .NET kullanarak 1Bpp dizinli bir görüntüye dönüştürdünüz. Bu yöntem, belgelerinizden yüksek kontrastlı, alandan tasarruf sağlayan görüntüler oluşturmak için inanılmaz derecede kullanışlıdır. Şimdi, bunu projelerinize ve iş akışlarınıza kolayca entegre edebilirsiniz. İyi kodlamalar!

## SSS

### 1Bpp indeksli görüntü nedir?
1Bpp (Piksel Başına 1 Bit) dizinli görüntü, her pikselin 0 veya 1 olmak üzere tek bir bit ile temsil edildiği siyah beyaz bir görüntü biçimidir. Bu biçim oldukça yer tasarrufu sağlar.

### Bir Word belgesinin birden fazla sayfasını aynı anda dönüştürebilir miyim?
 Evet, yapabilirsiniz. Değiştirebilirsiniz.`PageSet` mülk`ImageSaveOptions` birden fazla sayfayı veya tüm belgeyi içermek.

### Aspose.Words for .NET'i kullanmak için lisansa ihtiyacım var mı?
 Evet, Aspose.Words for .NET tam işlevsellik için bir lisans gerektirir. Bir tane alabilirsiniz[burada geçici lisans](https://purchase.aspose.com/temporary-license/).

### Word belgemi hangi diğer görüntü biçimlerine dönüştürebilirim?
 Aspose.Words, JPEG, BMP ve TIFF dahil olmak üzere çeşitli resim formatlarını destekler. Basitçe`SaveFormat` içinde`ImageSaveOptions`.

### Aspose.Words for .NET hakkında daha fazla dokümanı nerede bulabilirim?
 Ayrıntılı belgeleri şu adreste bulabilirsiniz:[Aspose.Words for .NET dokümantasyon sayfası](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
