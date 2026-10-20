---
category: general
date: 2026-03-22
description: C#'ta dikdörtgen şekli oluşturun ve Aspose.Words ile şekle gölge ekleyin.
  Gölge eklemeyi, dikdörtgen oluşturmayı ve gölge özelliklerini ayarlamayı öğrenin.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: tr
og_description: C#'ta dikdörtgen şekli oluşturun ve Aspose.Words kullanarak şekle
  gölge ekleyin. Gölge ekleme, dikdörtgen oluşturma ve gölge ayarlama konularını kapsayan
  adım adım rehber.
og_title: C#'de gölgeli dikdörtgen şekli oluşturma – Tam Kılavuz
tags:
- Aspose.Words
- C#
- Document Automation
title: C#'de Aspose.Words kullanarak gölgeli dikdörtgen şekli oluştur
url: /tr/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Aspose.Words kullanarak gölgeli dikdörtgen şekli oluşturma

Bir Word belgesinde **create rectangle shape** oluşturmanız gerektiğinde ama ona ince bir gölge eklemenin nasıl yapılacağından emin olmadığınız oldu mu? Yalnız değilsiniz—birçok geliştirici belge otomasyonu ile ilk kez uğraşırken bu soruna takılıyor. Bu rehberde Aspose.Words kullanarak **add shadow to shape** nasıl yapılacağını adım adım göstereceğiz ve yol boyunca “**how to add shadow**”, “**how to create rectangle**” ve “**how to set shadow**” sorularını da yanıtlayacağız.

Temiz bir `Document` ile başlayacağız, bir dikdörtgen çizeceğiz, gölgesini açacağız, bulanıklık, mesafe, açı ve rengi ayarlayacağız ve sonunda dosyayı kaydedeceğiz. Sonunda sayfanın hemen üzerinde yüzen gri tonlu bir dikdörtgen gösteren hazır bir `.docx` dosyanız olacak. Hiçbir gizem yok, sadece herhangi bir .NET projesine kopyala‑yapıştır yapabileceğiniz basit bir kod.

## Gereksinimler

* **Aspose.Words for .NET** (Mart 2026 itibarıyla en son sürüm). NuGet üzerinden `Install-Package Aspose.Words` komutuyla edinebilirsiniz.
* .NET geliştirme ortamı – Visual Studio, Rider veya C# uzantılı VS Code bile işinizi görecektir.
* Temel C# bilgisi – karmaşık bir şey değil, sadece bir console ya da WinForms uygulaması oluşturabilme yeteneği.

Hepsi bu. Ekstra kütüphane yok, gizli adım yok. Hazır mısınız? Hadi başlayalım.

## Adım 1: Yeni boş bir belge başlatma

**create rectangle shape** oluşturmak için, önce Word dosyasını temsil eden bir `Document` nesnesi – bir konteyner – gerekir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

`Document` sınıfı, Aspose.Words'un yaptığı her şeyin giriş noktasıdır. Bunu boş bir tuval gibi düşünün; olmadan hiçbir şekil, tablo ya da metin ekleyemezsiniz.

## Adım 2: Gölgeyi tutacak dikdörtgeni oluşturma

Şimdi `Rectangle` tipinde bir `Shape` oluşturarak **how to create rectangle** yapacağız. Ayrıca boyutunu puan cinsinden ayarlıyoruz (1 point ≈ 1/72 inç).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Neden 200 × 100 point seçtik? Demo için makul bir boyut – gölgeyi net görebilecek kadar büyük, ama sayfayı boğacak kadar devasa değil. Bu sayıları düzeninize göre istediğiniz gibi ayarlayabilirsiniz.

## Adım 3: Gölge efektini etkinleştirme ve görünümünü yapılandırma

İşte öğreticinin kalbi: **how to add shadow** ve **how to set shadow** özellikleri. Aspose.Words, her şekil üzerinde bir `Shadow` nesnesi sunar; bu sayede efekti açıp kapatabilir ve görsel parametreleri ayarlayabilirsiniz.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** kenarları yumuşatır – daha yüksek değer gölgeyi daha dağınık gösterir.
* **Distance** gölgeyi dikdörtgenden daha uzakta konumlandırır.
* **Angle** ışığın nereden geldiğini belirler; 45° diyagonal, doğal bir görünüm verir.
* **Color** herhangi bir `System.Drawing.Color` seçmenizi sağlar. Gri güvenli bir varsayılan, ancak `Color.Black` ile cesur, `Color.LightGray` ile ince bir gölge seçebilirsiniz.

Pro ipucu: `Enabled = false` ayarlarsanız, diğer tüm gölge ayarları göz ardı edilir, bu yüzden bu bayrağı her zaman iki kez kontrol edin.

## Adım 4: Şekli belge gövdesine ekleme

Dikdörtgen hazır ve gölgesi yapılandırıldıktan sonra, belgeye yerleştirmemiz gerekir. En basit yol, ilk bölümün ilk paragrafına eklemektir.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Belgenizde zaten metin varsa, belirli bir `Paragraph` ya da bir `Table` hücresi bulup şekli oraya ekleyebilirsiniz. `AppendChild` yöntemi çok yönlüdür – herhangi bir `Node` tipiyle çalışır.

## Adım 5: Belgeyi kaydetme ve sonucu doğrulama

Son olarak, dosyayı diske yazıyoruz. Yolu istediğiniz yere değiştirin; klasör mevcut olmalı, aksi takdirde bir istisna alırsınız.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Oluşan `ShadowedRectangle.docx` dosyasını Microsoft Word (veya LibreOffice) ile açın; sağa aşağı doğru kayarak net, diyagonal bir gölgeye sahip gri bir dikdörtgen görmelisiniz. Gölge çok soluk görünüyorsa, `BlurRadius` veya `Distance` değerlerini artırıp kodu yeniden çalıştırın – deneme yanılma eğlencenin bir parçasıdır.

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="Gölge örneğiyle dikdörtgen şekli oluşturma"}

### Beklenen çıktı

* Tek sayfalık bir Word belgesi.
* Sayfanın sol‑üst köşesine konumlandırılmış 200 × 100 point boyutunda gri bir dikdörtgen.
* 45° açıyla, 8 piksel kaydırılmış ince bir gri gölge, 5 piksel bulanıklaştırılmış.

## Şekle gölge ekleme – derinlemesine inceleme

Şöyle bir sorunuz olabilir, *“Gölgeyi animasyonlu yapabilir miyim ya da kullanıcı girdisine göre değiştirebilir miyim?”* Aspose.Words kendisi animasyonu desteklemez, ancak kaydetmeden önce gölge özelliklerini programlı olarak ayarlayabilirsiniz; bu, aynı belgenin farklı görünümlerini oluşturur. Örneğin, renk koleksiyonunda döngü yapmak:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Bu küçük kod parçası, **how to set shadow**'ı dinamik olarak göstermektedir—temalı raporlar oluşturmak için harika.

## Dikdörtgen oluşturma – alternatif şekiller

Yuvarlatılmış bir dikdörtgene ihtiyacınız varsa, sadece `ShapeType`'ı değiştirin:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

Veya mükemmel bir kare için, `Width`'i `Height` ile aynı yapın. Aynı gölge özellikleri geçerli, böylece seçtiğiniz herhangi bir şekil için **how to add shadow** konusunda zaten hazırsınız.

## Yaygın tuzaklar ve sorun giderme

| Semptom | Muhtemel neden | Çözüm |
|---------|----------------|-------|
| Gölge görünmüyor | `Shadow.Enabled` `false` olarak bırakılmış | `rectangleShape.Shadow.Enabled = true;` olarak ayarlayın |
| Gölge çok keskin görünüyor | `BlurRadius` 0 olarak ayarlanmış | `BlurRadius` değerini en az 3'e yükseltin |
| Belge kaydedilirken `FileNotFoundException` hatası veriyor | Hedef klasör mevcut değil | Önce klasörü oluşturun ya da geçerli bir yol kullanın |
| Şekil görünmez | Width/Height 0 olarak ayarlanmış | Her iki boyutun da > 0 olduğundan emin olun |

Bu sorunlara dikkat etmek, klasik “şeklim neden görünmüyor?” anından sizi kurtarır.

## Özet – neler başardık

* **Create rectangle shape** yeni bir Word belgesinde Aspose.Words kullanarak oluşturma.  
* **Add shadow to shape** `Shadow.Enabled` bayrağını değiştirerek ve bulanıklık, mesafe, açı ve rengi ayarlayarak ekleme.  
* **how to add shadow**, **how to create rectangle**, ve **how to set shadow**'ı temiz, yeniden kullanılabilir bir kod parçacığında gösterdik.  
* Herhangi bir C# projesine yapıştırabileceğiniz eksiksiz, çalıştırmaya hazır bir örnek sağladık.

## Sıradaki adımlar

Temel konularda ustalaştığınıza göre, şunları keşfetmeyi düşünün:

* **How to add shadow to images** – aynı `Shadow` API'si `ShapeType.Image` için de çalışır.
* **Combining multiple shapes** – Word içinde doğrudan akış şemaları veya infografikler oluşturun.
* **Exporting to PDF** – gölgeler eklendikten sonra `document.Save("output.pdf")` çağırarak yazdırılabilir bir PDF elde edin.

Farklı renkler, açılar ya da hatta degrade doldurmalarla denemeler yapmaktan çekinmeyin. API, Word'ü manuel olarak açmadan bile profesyonel görünümlü belgeler oluşturmanıza yeterince esnek.

---

Kodlamanın tadını çıkarın! Herhangi bir sorunla karşılaşırsanız, aşağıya yorum bırakın ya da Aspose.Words forumlarına göz atın – topluluk hızlıca yardımcı olur.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}