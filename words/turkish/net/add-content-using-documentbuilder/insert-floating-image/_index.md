---
"description": "Bu ayrıntılı adım adım kılavuzla Aspose.Words for .NET kullanarak Word belgesine yüzen bir resmin nasıl ekleneceğini öğrenin. Belgelerinizi geliştirmek için mükemmeldir."
"linktitle": "Word Belgesine Yüzen Resim Ekleme"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Word Belgesine Yüzen Resim Ekleme"
"url": "/tr/net/add-content-using-documentbuilder/insert-floating-image/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesine Yüzen Resim Ekleme

## giriiş

Metninizi tamamlamak için görsellerin mükemmel bir şekilde konumlandırıldığı çarpıcı bir rapor veya teklif oluşturduğunuzu hayal edin. Aspose.Words for .NET ile bunu zahmetsizce başarabilirsiniz. Bu kitaplık, belge düzenleme için güçlü özellikler sunarak onu geliştiriciler için vazgeçilmez bir çözüm haline getirir. Bu eğitimde, DocumentBuilder sınıfını kullanarak yüzen bir görsel eklemeye odaklanacağız. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, bu kılavuz sizi her adımda yönlendirecektir.

## Ön koşullar

Başlamadan önce, başlamak için ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1. Aspose.Words for .NET: Kütüphaneyi şu adresten indirebilirsiniz: [Aspose sürüm sayfası](https://releases.aspose.com/words/net/).
2. Visual Studio: .NET geliştirmeyi destekleyen herhangi bir sürüm.
3. Temel C# Bilgisi: C# programlamanın temellerini anlamak faydalı olacaktır.
4. Resim Dosyası: Logo veya resim gibi eklemek istediğiniz bir resim dosyası.

## Ad Alanlarını İçe Aktar

Projenizde Aspose.Words kullanmak için gerekli ad alanlarını içe aktarmanız gerekir. Bu, C# dosyanızın en üstüne aşağıdaki satırları ekleyerek yapılır:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Bu ön koşullar ve ad alanları sağlandıktan sonra eğitimimize başlamaya hazırız.

Yüzen bir resmi Word belgesine ekleme sürecini yönetilebilir adımlara bölelim. Her adım, herhangi bir aksama olmadan takip edebilmeniz için ayrıntılı olarak açıklanacaktır.

## Adım 1: Projenizi Kurun

Öncelikle Visual Studio'da yeni bir C# projesi oluşturun. Basitlik için bir Konsol Uygulaması seçebilirsiniz.

1. Visual Studio’yu açın ve yeni bir proje oluşturun.
2. "Konsol Uygulaması (.NET Core)" seçeneğini seçin ve "İleri"ye tıklayın.
3. Projenize bir isim verin ve kaydetmek için bir konum seçin. "Oluştur"a tıklayın.
4. NuGet Paket Yöneticisi aracılığıyla .NET için Aspose.Words'ü yükleyin. Çözüm Gezgini'nde projenize sağ tıklayın, "NuGet Paketlerini Yönet"i seçin ve "Aspose.Words"ü arayın. En son sürümü yükleyin.

## Adım 2: Belgeyi ve DocumentBuilder'ı Başlatın

Artık projeniz kurulduğuna göre, Document ve DocumentBuilder nesnelerini başlatalım.

1. Yeni bir örnek oluşturun `Document` sınıf:

```csharp
Document doc = new Document();
```

2. Bir DocumentBuilder nesnesi başlatın:

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

The `Document` nesne Word belgesini temsil eder ve `DocumentBuilder` içerik eklenmesine yardımcı olur.

## Adım 3: Görüntü Yolunu Tanımlayın

Sonra, görüntü dosyanızın yolunu belirtin. Görüntünüzün projenizin dizininden erişilebilir olduğundan emin olun.

Görüntü dizinini ve görüntü dosyası adını tanımlayın:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
string imagePath = dataDir + "Transparent background logo.png";
```

Yer değiştirmek `"YOUR DOCUMENT DIRECTORY"` Resminizin saklandığı gerçek yol ile.

## Adım 4: Yüzen Görüntüyü Ekle

Her şey ayarlandıktan sonra, yüzen resmi belgeye ekleyelim.

Kullanın `InsertImage` yöntemi `DocumentBuilder` resmi eklemek için sınıf:

```csharp
builder.InsertImage(imagePath,
   RelativeHorizontalPosition.Margin,
   100,
   RelativeVerticalPosition.Margin,
   100,
   200,
   100,
   WrapType.Square);
```

Her parametrenin anlamı şöyle:
- `imagePath`: Resim dosyanızın yolu.
- `RelativeHorizontalPosition.Margin`: Kenar boşluğuna göre yatay konum.
- `100`: Kenar boşluğundan yatay uzaklık (nokta cinsinden).
- `RelativeVerticalPosition.Margin`: Kenar boşluğuna göre dikey konum.
- `100`: Kenar boşluğundan dikey uzaklık (nokta cinsinden).
- `200`: Görüntünün genişliği (nokta cinsinden).
- `100`: Görüntünün yüksekliği (nokta cinsinden).
- `WrapType.Square`: Resmin etrafındaki metnin sarılma stili.

## Adım 5: Belgeyi Kaydedin

Son olarak belgeyi istediğiniz yere kaydedin.

1. Çıktı dosya yolunu belirtin:

```csharp
string outputPath = dataDir + "AddContentUsingDocumentBuilder.InsertFloatingImage.docx";
```

2. Belgeyi kaydedin:

```csharp
doc.Save(outputPath);
```

Kayan görselin bulunduğu Word belgeniz artık hazır!

## Çözüm

Aspose.Words for .NET kullanarak bir Word belgesine yüzen bir resim eklemek, yönetilebilir adımlara bölündüğünde basit bir işlemdir. Bu kılavuzu izleyerek, belgelerinize profesyonel görünümlü resimler ekleyebilir ve görsel çekiciliklerini artırabilirsiniz. Aspose.Words, raporlar, teklifler veya başka herhangi bir belge türü üzerinde çalışıyor olun, belge düzenlemeyi kolaylaştıran sağlam bir API sağlar.

## SSS

### Aspose.Words for .NET kullanarak birden fazla resim ekleyebilir miyim?

Evet, işlemi tekrarlayarak birden fazla resim ekleyebilirsiniz. `InsertImage` Her görüntü için istenilen parametrelere sahip bir yöntem.

### Resmin pozisyonunu nasıl değiştirebilirim?

Ayarlayabilirsiniz `RelativeHorizontalPosition`, `RelativeVerticalPosition`ve görüntüyü gerektiği gibi konumlandırmak için ofset parametreleri.

### Görseller için başka hangi sarma türleri mevcuttur?

Aspose.Words, aşağıdaki gibi çeşitli sarma türlerini destekler: `Inline`, `TopBottom`, `Tight`, `Through`ve daha fazlası. Belge düzeninize en uygun olanı seçebilirsiniz.

### Farklı resim formatlarını kullanabilir miyim?

Evet, Aspose.Words JPEG, PNG, BMP ve GIF dahil olmak üzere çok çeşitli resim formatlarını destekler.

### Aspose.Words for .NET'in ücretsiz deneme sürümünü nasıl edinebilirim?

Ücretsiz deneme sürümünü şuradan alabilirsiniz: [Aspose ücretsiz deneme sayfası](https://releases.aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}