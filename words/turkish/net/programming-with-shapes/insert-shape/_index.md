---
"description": "Aspose.Words for .NET'i kullanarak Word belgelerine şekillerin nasıl ekleneceğini ve düzenleneceğini adım adım kılavuzumuzla öğrenin."
"linktitle": "Şekil Ekle"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Şekil Ekle"
"url": "/tr/net/programming-with-shapes/insert-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Şekil Ekle

## giriiş

Görsel olarak çekici ve iyi yapılandırılmış Word belgeleri oluşturmaya gelince, şekiller hayati bir rol oynayabilir. Oklar, kutular veya hatta karmaşık özel şekiller ekliyor olun, bu öğeleri programatik olarak düzenleme yeteneği benzersiz bir esneklik sunar. Bu eğitimde, .NET için Aspose.Words kullanarak Word belgelerine şekillerin nasıl ekleneceğini ve düzenleneceğini keşfedeceğiz.

## Ön koşullar

Eğitime başlamadan önce aşağıdaki ön koşullara sahip olduğunuzdan emin olun:

1. Aspose.Words for .NET: En son sürümü indirin ve yükleyin [Aspose sürüm sayfası](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio gibi uygun bir .NET geliştirme ortamı.
3. C# Temel Bilgisi: C# programlama dili ve temel kavramlara aşinalık.

## Ad Alanlarını İçe Aktar

Başlamak için, C# projenize gerekli ad alanlarını içe aktarmanız gerekir:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Adım 1: Projenizi Kurun

Şekil eklemeye başlamadan önce projenizi ayarlamanız ve Aspose.Words for .NET kütüphanesini eklemeniz gerekir.

1. Yeni Bir Proje Oluşturun: Visual Studio'yu açın ve yeni bir C# Konsol Uygulaması projesi oluşturun.
2. Aspose.Words for .NET'i ekleyin: Aspose.Words for .NET kitaplığını NuGet Paket Yöneticisi aracılığıyla yükleyin.

```bash
Install-Package Aspose.Words
```

## Adım 2: Belgeyi Başlatın

Öncelikle yeni bir belge ve belgenin oluşturulmasına yardımcı olacak bir belge oluşturucu başlatmanız gerekecek.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Yeni bir belge başlat
Document doc = new Document();

// Belgeyi oluşturmaya yardımcı olması için bir DocumentBuilder başlatın
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 3: Bir Şekil Ekle

Şimdi belgeye bir şekil ekleyelim. Basit bir metin kutusu ekleyerek başlayacağız.

```csharp
// Belgeye bir metin kutusu şekli ekleyin
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// Şekli döndür
shape.Rotation = 30.0;
```

Bu örnekte, (100, 100) konumuna her biri 50 birim genişlik ve yükseklikte bir metin kutusu ekliyoruz. Ayrıca şekli 30 derece döndürüyoruz.

## Adım 4: Başka Bir Şekil Ekleyin

Belgeye bir şekil daha ekleyelim, bu sefer konumunu belirtmeyelim.

```csharp
// Başka bir metin kutusu şekli ekle
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// Şekli döndür
secondShape.Rotation = 30.0;
```

Bu kod parçacığı, ilkiyle aynı boyutlara ve dönüşe sahip ancak konumunu belirtmeden başka bir metin kutusu ekler.

## Adım 5: Belgeyi Kaydedin

Şekilleri ekledikten sonra son adım belgeyi kaydetmektir. `OoxmlSaveOptions` kaydetme biçimini belirtmek için.

```csharp
// Uygunlukla kaydetme seçeneklerini tanımlayın
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// Belgeyi kaydet
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Çözüm

Ve işte oldu! Aspose.Words for .NET kullanarak bir Word belgesine şekilleri başarıyla eklediniz ve düzenlediniz. Bu eğitim temelleri kapsıyordu ancak Aspose.Words, özel stiller, bağlayıcılar ve grup şekilleri gibi şekillerle çalışmak için çok daha gelişmiş özellikler sunuyor.

Daha detaylı bilgi için şu adresi ziyaret edin: [Aspose.Words for .NET belgeleri](https://reference.aspose.com/words/net/).

## SSS

### Farklı şekil türlerini nasıl eklerim?
Değiştirebilirsiniz `ShapeType` içinde `InsertShape` Daire, dikdörtgen ve ok gibi farklı şekil türlerini ekleme yöntemi.

### Şekillerin içine metin ekleyebilir miyim?
Evet, kullanabilirsiniz `builder.Write` Şekilleri ekledikten sonra içlerine metin ekleme yöntemi.

### Şekilleri biçimlendirmek mümkün mü?
Evet, şekilleri şu şekilde özellikler ayarlayarak biçimlendirebilirsiniz: `FillColor`, `StrokeColor`, Ve `StrokeWeight`.

### Şekilleri diğer öğelere göre nasıl konumlandırabilirim?
Kullanın `RelativeHorizontalPosition` Ve `RelativeVerticalPosition` Şekilleri belgedeki diğer öğelere göre konumlandırmak için özellikler.

### Birden fazla şekli bir arada gruplayabilir miyim?
Evet, Aspose.Words for .NET, şekilleri gruplandırmanıza olanak tanır `GroupShape` sınıf.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}