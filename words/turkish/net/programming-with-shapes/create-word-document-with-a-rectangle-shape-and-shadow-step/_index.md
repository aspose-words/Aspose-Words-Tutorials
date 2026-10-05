---
category: general
date: 2026-03-01
description: Aspose.Words kullanarak bir Word belgesi oluşturun ve dikdörtgen şekli
  eklemeyi, gölge eklemeyi, şeffaflığı ayarlamayı ve şekil oluşturmayı öğrenin—hepsi
  C# ile.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: tr
og_description: C# ile Aspose.Words kullanarak Word belgesi oluşturun. Birkaç adımda
  dikdörtgen şekli eklemeyi, dış gölge uygulamayı ve şeffaflık ayarlamayı öğrenin.
og_title: Dikdörtgen Şekli ve Gölgesiyle Word Belgesi Oluşturma – Rehber
tags:
- Aspose.Words
- C#
- Document Generation
title: Dikdörtgen Şekilli ve Gölge ile Word Belgesi Oluşturma – Adım Adım Kılavuz
url: /tr/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesi Oluşturma: Dikdörtgen Şekil ve Gölge – Adım Adım Kılavuz

Hiç **Word belgesi oluşturma** içeren özel‑stil bir dikdörtgen oluşturmanız gerekti mi? Belki bir rapor şablonu oluşturuyorsunuz ve düzeni öne çıkarmak için ince bir gölge istiyorsunuz. Tek başınıza değilsiniz—geliştiriciler sürekli olarak “Dikdörtgen şekli ve gölgeyi programlı olarak nasıl ekleyebilirim?” sorusunu soruyor. İyi haber, Aspose.Words ile bunu birkaç satırda yapabilirsiniz.

Bu öğreticide tüm süreci adım adım inceleyeceğiz: boş bir Word dosyası oluşturmak, dikdörtgen şekli eklemek ve şeffaflık içeren dış gölgeyi yapılandırmak. Sonunda, Word'de açıp etkisini anında görebileceğiniz hazır bir `Shadow.docx` dosyanız olacak. Harici araçlar yok, karmaşık XML yok—sadece temiz C# kodu ve net açıklamalar.

## Öğrenecekleriniz

- **Şekil oluşturmayı** Aspose.Words kullanarak bir Word belgesinde nesneler olarak nasıl yapacağınızı.
- **Dikdörtgen şekli eklemeyi** bir paragrafta mevcut içeriği bozmadan nasıl yapacağınızı.
- **Gölge eklemeyi** (dış gölge) ve rengini, ofsetini, bulanıklığını ve şeffaflığını nasıl kontrol edeceğinizi.
- **Şeffaflığı ayarlamayı** gölgede profesyonel görünmesi için nasıl yapacağınızı.
- İpuçları, tuzaklar ve gerçek dünya projelerinde ihtiyaç duyabileceğiniz varyasyonlar.

### Önkoşullar

- .NET 6.0 veya üzeri (API, .NET Framework 4.6+ ile de çalışır).
- NuGet üzerinden Aspose.Words for .NET kurulumu (`Install-Package Aspose.Words`).
- C# sözdizimi hakkında temel bir anlayış—fantezi bir şey yok, sadece standart `using` ifadeleri ve nesne oluşturma.

> **Pro tip:** Visual Studio kullanıyorsanız, olası null‑referans hatalarını erken yakalamak için “nullable reference types” özelliğini etkinleştirin.

## 1. Adım – Boş Bir Word Belgesi Oluşturma

`Document` sınıfı ile **Word belgesi oluşturmak** için başlarız. Bunu boş bir tuval gibi düşünün; daha sonra bölümler, paragraflar, tablolar veya şekiller ekleyebilirsiniz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

Temiz bir `Document` örneğine neden ihtiyacımız var? Çünkü her şekil, paragraf veya stil bir belge nesne modeli (DOM) içinde yaşar. Temiz bir belgeyle başlamak, eklediğiniz dikdörtgenin mevcut içerikle çakışmayacağını garanti eder.

## 2. Adım – Dikdörtgen Şekli Tanımlama

Şimdi bir dikdörtgen **şekil oluşturmayı** yapıyoruz. `Shape` yapıcı metodu, belgeyi ve şekil tipini alır. Ayrıca genişlik ve yüksekliğini puan cinsinden ayarlarız (1 pt ≈ 1/72 in).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Şunu merak edebilirsiniz: “Puan yerine santimetre kullanabilir miyim?” API sadece puan kabul eder, ancak dönüştürebilirsiniz: `points = centimeters * 28.35`. Bu küçük dönüşüm, şekilleri sayfa kenar boşluklarına hizalarken kullanışlıdır.

## 3. Adım – Dış Gölge Ekleme ve Şeffaflığı Ayarlama

İşte sihrin gerçekleştiği yer: **gölge eklemeyi** ve bu gölgeye **şeffaflık ayarlamayı**. `ShadowFormat` özelliği size tam kontrol sağlar.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Neden bu ayarlar?**  
- **Transparency** (Şeffaflık) alt sayfa dokusunun görünmesine izin verir, gölgenin çok ağır görünmesini önler.  
- **OffsetX/Y** şeklin sayfadan kaldırılmış gibi bir illüzyon yaratır.  
- **BlurRadius** kenarları yumuşatır—olmasaydı gölge sert bir dikdörtgen olur, bu da doğal olmaz.

Daha dramatik bir etki isterseniz, `OffsetX/Y` değerlerini 10'a yükseltin ve `BlurRadius`'ı 8'e artırın. Tam tersine, ince bir ipucu için her ikisini de sırasıyla 2 tutun.

## 4. Adım – Şekli Belgeye Ekleme

Şimdi belge içindeki ilk paragrafa **dikdörtgen şekli ekliyoruz**. Belgenin içeriği yoksa, `FirstParagraph` sizin için otomatik olarak oluşturulur.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Şekli belirli bir tablo hücresi içinde ya da daha sonraki bir paragrafta istiyorsanız ne yapmalısınız? O düğümü (`doc.GetChild(NodeType.Paragraph, index, true)`) bulun ve `AppendChild` metodunu çağırın. Aynı şekil nesnesi, birden fazla kopya gerektiğinde klonlanabilir.

## 5. Adım – Belgeyi Kaydetme

Son olarak, diske **Word belgesi oluşturma** dosyasını kaydediyoruz. Ortamınıza uygun bir yol kullanın; örnek bir yer tutucu kullanır.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

`Shadow.docx` dosyasını Microsoft Word'de açtığınızda, sağ alt köşeye kaydırılmış yumuşak bir dış gölgeye sahip açık gri bir dikdörtgen göreceksiniz. Gölgenin %30 şeffaflığı, sayfayı domine etmemesini sağlar.

![Gölgelendirilmiş dikdörtgen şekilli Word belgesi oluşturma](image.png "Gölgelendirilmiş dikdörtgen şekilli Word belgesi oluşturma")

*Resim alt metni: gölgelendirilmiş dikdörtgen şekilli Word belgesi oluşturma*

## Tam, Çalıştırmaya Hazır Kod

Aşağıda, bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz tam program yer alıyor. Eksik parça yok, “daha fazla bilgi için belgelere bakın” gibi bir şey yok.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Beklenen Sonuç

- Hedef klasörde **Shadow.docx** adlı bir dosya oluşur.
- Word'de açtığınızda, koyu gri bir dış gölgeye sahip (200 × 100 pt) bir dikdörtgen gösterilir.
- Gölge, yatay ve dikey olarak 5 pt kaydırılmış, bulanık ve %30 şeffaftır.

## Yaygın Sorular ve Kenar Durumları

| Soru | Cevap |
|----------|--------|
| **Gölge rengini markama uygun şekilde değiştirebilir miyim?** | Kesinlikle—`System.Drawing.Color.DarkGray` ifadesini istediğiniz herhangi bir `Color` ile değiştirin, örneğin mavi bir vurgu için `Color.FromArgb(255, 0, 120, 215)`. |
| **Dış gölge yerine iç gölgeye ihtiyacım olsaydı ne yapmalıyım?** | `ShadowFormat.Style = ShadowStyle.InnerShadow` olarak ayarlayın. Diğer özellikler aynı şekilde çalışır. |
| **Şeffaflık eski Word sürümlerinde destekleniyor mu?** | Evet. Aspose.Words, Word 2007+ tarafından anlaşılan uygun XML'i yazar. Eski sürümler şeffaflık değerini görmezden gelebilir ancak gölgeyi yine de gösterir. |
| **Farklı gölgeli birden fazla şekil ekleyebilir miyim?** | Tabii—yeni `Shape` örnekleri oluşturun, her gölgeyi bağımsız olarak yapılandırın ve istediğiniz düğümlere ekleyin. |
| **Yüzlerce şekil için performans nasıl etkilenir?** | Çok sayıda şekil oluşturmak bellek kullanımını artırabilir. Tek bir `Document` örneğini yeniden kullanın ve şekilleri bir döngüde ekleyin; eğer bellek baskısı yaşarsanız geçici nesneleri serbest bırakın. |

## Gerçek Dünya Projeleri İçin İpuçları

- **Batch generation:** Birçok kullanıcı için rapor oluştururken, tek bir `Document` şablonu örneği oluşturup her yineleme için klonlayın. Şekilleri eklemeden önce yer tutucuları değiştirin.
- **Dynamic sizing:** Sayfa boyutlarını (`document.FirstSection.PageSetup.PageWidth`) kullanarak şekil boyutunu sayfaya göre hesaplayın, böylece farklı kağıt boyutlarında tutarlı bir düzen sağlanır.
- **Testing:** Gölge parametrelerinde bir değişiklik yaptıktan sonra her zaman oluşturulan `.docx` dosyasını Word'de açın. Görsel geri bildirim, sayı tahmininden daha hızlıdır.

## Sonraki Adımlar

Artık **dikdörtgen şekli eklemeyi**, **gölge eklemeyi** ve **şeffaflık ayarlamayı** bildiğinize göre, aşağıdakileri keşfetmeyi düşünün:

- Şekillere **gradient doldurmalar** eklemek (`Shape.FillFormat`).
- Şekillerin içine **resimler** gömerek watermark etkisi oluşturmak.
- **Tablolar** kullanarak bir ızgarada birden fazla gölgeli şekli hizalamak.
- Aynı belgeyi PDF olarak dışa aktarmak (`document.Save("output.pdf")`) ve gölgeleri korumak.

Bu maddelerin her biri aynı temel kavramlar üzerine inşa edildiği için, kodu genişletirken rahat hissedeceksiniz.

### Özet

Aspose.Words ile **Word belgesi oluşturma** ile başladık, ardından bir dikdörtgen **şekil oluşturmayı**, **gölge eklemeyi**, **şeffaflık ayarlamayı** uyguladık ve sonucu kaydettik. Tüm süreç, herhangi bir otomasyon senaryosuna uyarlayabileceğiniz kompakt ve yeniden kullanılabilir bir modele sığar.

Denemeler yapmaktan çekinmeyin—renkleri değiştirin, ofsetlerle oynayın veya birkaç şekli üst üste koyun. Bir sorunla karşılaştığınızda, yukarıdaki bölümlere geri dönün; bunlar hızlı bir referans olacak şekilde tasarlandı. Kodlamanın tadını çıkarın ve belgeleriniz her zaman şık görünsün!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}