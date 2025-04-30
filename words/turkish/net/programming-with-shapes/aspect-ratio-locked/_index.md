---
"description": "Aspose.Words for .NET kullanarak Word belgelerindeki şekillerin en boy oranını nasıl kilitleyeceğinizi öğrenin. Görüntülerinizi ve şekillerinizi orantılı tutmak için bu adım adım kılavuzu izleyin."
"linktitle": "En Boy Oranı Kilitli"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "En Boy Oranı Kilitli"
"url": "/tr/net/programming-with-shapes/aspect-ratio-locked/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# En Boy Oranı Kilitli

## giriiş

Word belgelerinizdeki resimlerin ve şekillerin mükemmel oranlarını nasıl koruyacağınızı hiç merak ettiniz mi? Bazen, resimlerinizin ve şekillerinizin yeniden boyutlandırıldığında bozulmamasını sağlamanız gerekir. İşte en boy oranını kilitlemenin işe yaradığı yer burasıdır. Bu eğitimde, .NET için Aspose.Words kullanarak Word belgelerindeki şekiller için en boy oranının nasıl ayarlanacağını inceleyeceğiz. Bunu, kolayca takip edilebilen adımlara bölerek bu becerileri projelerinize güvenle uygulayabilmenizi sağlayacağız.

## Ön koşullar

Koda dalmadan önce, başlamak için neye ihtiyacınız olduğunu gözden geçirelim:

- Aspose.Words for .NET Kütüphanesi: Aspose.Words for .NET'in yüklü olması gerekir. Henüz yüklü değilse, şunları yapabilirsiniz: [buradan indirin](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: .NET geliştirme ortamınızın kurulu olduğundan emin olun. Visual Studio popüler bir seçimdir.
- Temel C# Bilgisi: C# programlama konusunda biraz bilgi sahibi olmak faydalı olacaktır.

## Ad Alanlarını İçe Aktar

İlk önce gerekli ad alanlarını içe aktaralım. Bu ad alanları bize Word belgeleri ve şekilleriyle çalışmak için ihtiyaç duyduğumuz sınıflara ve yöntemlere erişim sağlayacak.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Adım 1: Belge Dizininizi Ayarlayın

Şekilleri düzenlemeye başlamadan önce, belgelerimizin depolanacağı bir dizin ayarlamamız gerekir. Basitlik adına, bir yer tutucu kullanacağız `YOUR DOCUMENT DIRECTORY`. Bunu belge dizininize giden gerçek yol ile değiştirin.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Adım 2: Yeni Bir Belge Oluşturun

Sonra, Aspose.Words kullanarak yeni bir Word belgesi oluşturacağız. Bu belge, şekil ve resim eklemek için tuvalimiz olarak hizmet edecek.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Burada, bir örnek oluşturuyoruz `Document` sınıf ve kullan `DocumentBuilder` Belgenin içeriğini oluşturmamıza yardımcı olmak için.

## Adım 3: Bir Resim Ekle

Şimdi, belgemize bir resim ekleyelim. Bunu kullanacağız `InsertImage` yöntemi `DocumentBuilder` sınıf. Belirtilen dizinde bir görüntünüz olduğundan emin olun.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

Yer değiştirmek `dataDir + "Transparent background logo.png"` resim dosyanızın yolunu da ekleyin.

## Adım 4: En Boy Oranını Kilitleyin

Resim eklendikten sonra, en boy oranını kilitleyebiliriz. En boy oranını kilitlemek, yeniden boyutlandırılırken resmin oranlarının sabit kalmasını sağlar.

```csharp
shape.AspectRatioLocked = true;
```

Ayar `AspectRatioLocked` ile `true` görüntünün orijinal en boy oranını korumasını sağlar.

## Adım 5: Belgeyi Kaydedin

Son olarak, belgeyi belirtilen dizine kaydedeceğiz. Bu adım, yaptığımız tüm değişiklikleri belge dosyasına yazar.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Çözüm

Tebrikler! Aspose.Words for .NET kullanarak Word belgelerindeki şekiller için en boy oranını nasıl ayarlayacağınızı başarıyla öğrendiniz. Bu adımları izleyerek, görüntülerinizin ve şekillerinizin oranlarını koruyarak belgelerinizin profesyonel ve cilalı görünmesini sağlayabilirsiniz. En boy oranı kilitleme özelliğinin çeşitli senaryolarda nasıl çalıştığını görmek için farklı görüntüler ve şekillerle denemeler yapmaktan çekinmeyin.

## SSS

### En boy oranını kilitledikten sonra tekrar açabilir miyim?
Evet, en boy oranını ayarlayarak kilidini açabilirsiniz `shape.AspectRatioLocked = false`.

### Kilitli en boy oranına sahip bir resmi yeniden boyutlandırırsam ne olur?
Resim, orijinal genişlik-yükseklik oranını koruyarak orantılı bir şekilde yeniden boyutlandırılacaktır.

### Bunu resimlerin dışında başka şekillere de uygulayabilir miyim?
Kesinlikle! En boy oranı kilitleme özelliği dikdörtgenler, daireler ve daha fazlası dahil olmak üzere her şekle uygulanabilir.

### Aspose.Words for .NET, .NET Core ile uyumlu mudur?
Evet, Aspose.Words for .NET hem .NET Framework'ü hem de .NET Core'u destekler.

### Aspose.Words for .NET hakkında daha fazla dokümanı nerede bulabilirim?
Kapsamlı dokümanları bulabilirsiniz [Burada](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}