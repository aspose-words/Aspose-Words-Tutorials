---
category: general
date: 2026-02-26
description: Aspose.Words kullanarak Word'de dikdörtgen şekil oluşturun ve dakikalar
  içinde şekli Word'e eklemeyi, şekle gölge uygulamayı ve şeklin şeffaflığını ayarlamayı
  öğrenin.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: tr
og_description: Aspose.Words kullanarak Word'de dikdörtgen şekli oluşturun. Şekli
  Word'e eklemeyi, şekle gölge uygulamayı ve şeklin şeffaflığını hızlıca ayarlamayı
  öğrenin.
og_title: Word'de Dikdörtgen Şekil Oluşturma – Tam Aspose.Words Rehberi
tags:
- Aspose.Words
- C#
- Word Automation
title: Word'de Dikdörtgen Şekil Oluşturma – Tam Aspose.Words Rehberi
url: /tr/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Dikdörtgen Şekil Oluşturma – Tam Aspose.Words Rehberi

Word belgesinde **create rectangle shape** oluşturmanız gerektiğinde nereden başlayacağınızı bilemediniz mi? Yalnız değilsiniz—birçok geliştirici raporlar veya faturalar otomatikleştirirken bu engelle karşılaşıyor. Bu öğreticide, **add shape to Word** nasıl yapılır, ince bir gölge nasıl uygulanır ve şeklin şeffaflığı nasıl kontrol edilir, hepsini Aspose.Words for .NET ile gösteren eksiksiz, çalıştırmaya hazır bir örnek üzerinden adım adım ilerleyeceğiz.

Kılavuzun sonunda, temiz bir gölgeye sahip bir dikdörtgen içeren bir `.docx` dosyanız olacak—markalaşma, vurgulamalar veya belgenizi biraz daha profesyonel göstermek için mükemmel. Harici araçlar gerekmez, sadece birkaç satır C#.

## İhtiyacınız Olanlar

- **Aspose.Words for .NET** (2026 başı itibarıyla en son sürüm). NuGet üzerinden alabilirsiniz (`Install-Package Aspose.Words`).
- Bir .NET geliştirme ortamı (Visual Studio, Rider veya C# uzantılı VS Code).
- C# sözdizimine temel aşinalık—fantezi bir şey yok, sadece yaygın `using` ifadeleri ve nesne oluşturma.

Eğer bunlara sahipseniz, harika—hadi başlayalım.

## Dikdörtgen Şekil Oluşturma – Temel Adımlar

Aşağıda tam kaynak kodu yer alıyor. Yeni bir konsol projesine kopyalayıp yapıştırın, **F5** tuşuna basın ve belirttiğiniz klasörde `ShadowDemo.docx` dosyasının oluştuğunu göreceksiniz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Neden Bu Çalışıyor

- **`Document`** giriş noktasıdır; tüm Word dosyasını temsil eder.
- **`Shape`**, `ShapeType.Rectangle` ile Aspose'a dikdörtgen bir çizim nesnesi istediğimizi söyler.
- **`Width`** ve **`Height`** ayarlamak şekle belirli bir boyut verir; aksi takdirde varsayılan olarak çok küçük bir yer tutucu olur.
- **`Shadow`** nesnesi, bulanıklık, mesafe, yön, renk, şeffaflık ve yayılma gibi tüm görsel özellikleri ince ayar yapmamızı sağlar. Bu, *apply shadow to shape* işleminin kalbidir.
- Son olarak, **`AppendChild`** şekli belgenin ilk paragrafına ekler; bu, *add shape to Word* işlemini tablo veya başlıklarla uğraşmadan yapmanın en basit yoludur.

`ShadowDemo.docx` dosyasını açtığınızda, belgede rahatça oturan gri bir dikdörtgen ve 45° açıyla aşağı‑sağa doğru eğimli bir gölge göreceksiniz. Gölge katı bir blok değildir; bulanıklık yarıçapı kenarları yumuşatır ve şeffaflık, sert bir kaplama yerine doğal bir düşen gölge gibi görünmesini sağlar.

![dikdörtgen şekil örneği](image.png "Aspose.Words kullanarak Word'de gölgeyle dikdörtgen şekil oluşturma")

*(Yukarıdaki görsel, kod parçacığının nihai sonucunu göstermektedir.)*

## Word Belgesine Şekil Ekleme – Yerleştirme Seçenekleri

Örnek, **ilk paragraf**ı kullanıyor çünkü ekranda bir şey görmek için en hızlı yol bu. Gerçek dünyada şu durumlar isteyebilirsiniz:

- Şekli belirli bir **section** veya **header/footer** içine ekleyin.
- Tablo verileriyle hizalama için **table cell** içine yerleştirin.
- Çevresindeki metnin dikdörtgenin etrafında akması için **text wrapping** seçenekleri (ör. `WrapType.Square`) ile sarın.

İşte şekli özel bir stil ile yeni bir paragrafta yerleştiren hızlı bir varyasyon:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Pro ipucu:* Şeklin özelliklerini yapılandırdıktan **sonra** ekleyin; aksi takdirde görsel görünümü yenilemek için `UpdateLayout` çağırmanız gerekebilir.

## Şekle Gölge Uygulama – Görünümü İnce Ayarlama

Gölge, bir belgenin estetiğini büyük ölçüde değiştirebilir. `Shadow` sınıfı çeşitli özellikler sunar:

| Property      | Kontrol Ettiği Şey                                   | Tipik Değerler |
|---------------|------------------------------------------------------|----------------|
| `BlurRadius`  | Gölge kenarlarının yumuşaklığı                      | 2.0 – 10.0      |
| `Distance`    | Gölgenin şekilden ne kadar uzakta olduğu            | 1.0 – 8.0       |
| `Direction`   | Derece cinsinden açı (0 = sol, 90 = yukarı)          | 0 – 360         |
| `Color`       | Gölge rengi (herhangi bir `System.Drawing.Color`)   | Gray, Black, Custom |
| `Transparency`| Opaklık (0 = tamamen opak, 1 = görünmez)            | 0.0 – 0.5       |
| `Spread`      | Bulanıklık uygulanmadan önce gölgenin genişlemesi    | 0.0 – 1.0       |

Eğer **hafif, profesyonel bir görünüm** istiyorsanız, `BlurRadius` değerini 4‑6 civarında ve `Transparency` değerini 0.2 yakınında tutun, tıpkı yukarıdaki kod gibi. **Dramatik bir etki** için ise `Distance` değerini 6'ya çıkarın, `Direction`'ı 135°'ye ayarlayın ve `Transparency`'ı 0.05'e düşürün.

## Şekil Şeffaflığını ve Gölge Yayılımını Ayarlama

Şeffaflık sadece gölgeyle ilgili değildir; aynı zamanda dikdörtgeni de kısmen saydam yapabilirsiniz:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

Yarı saydam bir dolgu ile yumuşak bir gölgeyi birleştirmek genellikle modern bir UI hissi verir—raporlara gömülü gösterge panelleri veya tasarım mock‑up'ları için harika.

### Dikkat Edilmesi Gereken Kenar Durumları

1. **Eski Word sürümleri** (2007 öncesi) bazı gölge özelliklerini desteklemez. `.doc` dosyalarını hedefliyorsanız, gölgeyi basitleştirmeyi düşünün (ör. `BlurRadius`'ı 0 yapın).
2. **Yüksek DPI ekranlar** gölgeyi biraz farklı render edebilir. Görsel doğruluk kritikse hedef ortamda test edin.
3. **Üst üste gelen şekiller**—Aspose gölgeleri eklenme sırasına göre render eder. İstenmeyen örtüşmeyi önlemek için şekilleri arka plandan öne doğru ekleyin.

## Sonucu Kaydet ve Doğrula

`Document.Save` yöntemi, dosya uzantısından çıkış formatını otomatik olarak algılar. **`.docx`** dosyası için Open XML formatı elde edersiniz; bu, çoğu modern Word işlemcisi tarafından anlaşılır. Aynı görsel stili koruyan bir **PDF** sürümüne ihtiyacınız varsa, sadece uzantıyı değiştirin:

```csharp
document.Save("ShadowDemo.pdf");
```

Oluşturulan `ShadowDemo.docx` (veya `ShadowDemo.pdf`) dosyasını açtığınızda temiz bir **gölgeli dikdörtgen** görmelisiniz; bu, Aspose.Words kullanarak *create rectangle shape* ve *apply shadow to shape* işlemlerini başarıyla gerçekleştirdiğinizi doğrular.

## Sık Sorulan Sorular

**S: Farklı bir şekil, örneğin bir elips kullanabilir miyim?**  
C: Kesinlikle. `ShapeType.Rectangle` yerine `ShapeType.Ellipse` (veya başka bir `ShapeType` enum) kullanın. Gölge özellikleri aynı kalır.

**S: Dikdörtgenin tıklanabilir olması gerekiyorsa ne yapmalıyım?**  
C: Şekle bir hiperlink atayabilirsiniz:

```csharp
rectangleShape.Href = "https://example.com";
```

**S: Bu .NET 6+ üzerinde çalışır mı?**  
C: Evet. Aspose.Words 23.11 ve sonrası .NET 6, .NET 7 ve .NET 8'i tam olarak destekler. Uygun NuGet paketini referans alın.

**S: Gölge rengini markama uygun şekilde nasıl değiştiririm?**  
C: İstediğiniz herhangi bir `System.Drawing.Color` kullanın:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Özet

Word belgesinde **create rectangle shape**, **add shape to Word**, **apply shadow to shape** ve **set shape transparency** işlemlerini nasıl yapacağınızı tamamen ele aldık. Tam ve çalıştırılabilir kod bu sayfanın üst kısmında yer alıyor ve açıklamalar, herhangi bir proje için boyutları, renkleri ve gölge parametrelerini ayarlamanız için yeterli güveni sağlamalı.

Bir sonraki adıma hazır mısınız? Şunları deneyin:

- Rozet efekti için birden fazla şekli üst üste katmanlamak.
- Belge içeriğine göre dinamik boyutlandırma (ör. bir tablo sütunundan genişliği hesaplamak).
- Gölgeyi koruyarak belgeyi PDF veya HTML'ye dışa aktarmak.

Herhangi bir sorunla karşılaşırsanız yorum bırakmaktan çekinmeyin, ya da “gölgeli dikdörtgen” temasıyla kendi varyasyonlarınızı paylaşın.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}