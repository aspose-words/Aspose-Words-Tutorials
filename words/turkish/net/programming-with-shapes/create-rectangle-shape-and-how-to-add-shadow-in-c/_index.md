---
category: general
date: 2026-04-04
description: C# ile Aspose.Words kullanarak dikdörtgen şekli oluşturun ve gölge eklemeyi,
  gölgeye bulanıklık uygulamayı ve gölgeyi şeffaf yapmayı öğrenin – adım adım rehber.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: tr
og_description: C# ile Aspose.Words kullanarak dikdörtgen şekli oluşturun. Gölge eklemeyi,
  gölgenin bulanıklığını uygulamayı ve gölgeyi şeffaf yapmayı kısa bir öğreticide
  öğrenin.
og_title: C#'ta dikdörtgen şekli oluşturma ve gölge ekleme
tags:
- Aspose.Words
- C#
- Document Automation
title: C#'ta dikdörtgen şekli oluşturma ve gölge ekleme
url: /tr/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta dikdörtgen şekli oluşturma ve gölge ekleme

Bir Word belgesinde **dikdörtgen şekli oluşturma** ihtiyacınız oldu ama ona ince bir gölge nasıl ekleyeceğinizi bilmiyor muydunuz? Yalnız değilsiniz. Birçok raporlama veya marka oluşturma senaryosunda, yumuşak, yarı saydam bir gölgeye sahip basit bir dikdörtgen, çok çaba harcamadan düzenin daha profesyonel görünmesini sağlar.

Bu öğreticide **Aspose.Words** kullanarak **belge oluşturmayı** adım adım gösterecek, ardından **gölge eklemeyi**, **gölgeye bulanıklaştırma uygulamayı** ve hatta **gölgeyi saydam yapmayı** anlatacağız. Sonunda, birkaç dakika içinde gölgeli bir dikdörtgen üreten, çalıştırılmaya hazır bir C# kod parçacığına sahip olacaksınız.

## Gereksinimler

- .NET 6 veya üzeri (API .NET Framework 4.6+ ile de çalışır)
- Aspose.Words for .NET (bu örnek için ücretsiz deneme sürümü çalışır)
- Bir kod editörü – Visual Studio, VS Code, Rider, tercihiniz ne olursa olsun
- Temel C# bilgisi – karmaşık bir şey değil, sadece bir konsol uygulaması çalıştırabilme

Bu gereksinimlere sahipseniz, doğrudan çözüme geçebiliriz.

## Adım 1 – Belgeyi oluşturma ve tuvali başlatma

İlk olarak bir boş `Document` nesnesine ihtiyacınız var. Bunu, Aspose.Words'ün daha sonra bir Word dosyasına dönüştüreceği boş bir kağıt parçası gibi düşünün.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

Neden bir şablon yüklemek yerine `Document` örneği oluşturuyoruz? Sıfırdan başlamak, gizli stillerin veya bölümlerin dikdörtgenimizi etkilemesini önler. Ayrıca dosya boyutunu küçültür – döngü içinde çok sayıda belge üretirken iyi bir alışkanlıktır.

## Adım 2 – Dikdörtgen şekli oluşturma (ana anahtar kelimemiz)

Şimdi **dikdörtgen şekli oluşturuyoruz**. `Shape` sınıfı esnektir; ona türünü (Rectangle), boyutunu ve çevresindeki metinle nasıl sarılacağını söylersiniz.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Nesne başlatıcı sözdiziminin kullanılmasına dikkat edin – bu, kodun daha öz ve sonradan bir özelliği unutma ihtimalini azaltır. Dikdörtgen, bir sonraki adımda ekleyeceğimiz ilk paragrafta yer alacak.

## Adım 3 – Gölge ekleme ve görünümünü özelleştirme

Gölge eklemek tek bir satırdan ibaret değildir; ayarlamanız gereken birkaç özellik vardır. İşte ikincil anahtar kelimeler **apply blur to shadow** ve **make shadow transparent** burada devreye girer.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

Sayılara kısa bir not: `BlurRadius` değeri 5 olduğunda hafif bir yumuşatma sağlar; daha yumuşak bir görünüm için 10’a, keskin bir kenar için 2’ye düşürebilirsiniz. `Transparency` değeri 0 (opak) ile 1 (görünmez) arasında değişir. Markanızın kontrast gereksinimlerine göre ayarlayın.

### Pro ipucu

Renkli bir gölgeye (örneğin kurumsal bir mavi) ihtiyacınız olursa, sadece `Color.DarkGray` yerine `Color.FromArgb(80, 0, 120, 215)` kullanın. İlk argüman alfa kanalını temsil eder – ince bir etki için düşük tutun.

## Adım 4 – Şekli belgeye ekleme

Dikdörtgen ve gölgesi hazır olduğunda, onu belgenin ilk paragrafına yerleştiriyoruz. Bu adım, şeklin dosyanın en üstünde görünmesini sağlar.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

Neden ilk paragraf? Belge tamamen boş olduğunda bile güvenli bir varsayılandır. Belirli bir konum (ör. bir başlıktan sonra) istiyorsanız, o düğümü bulup şekli oraya eklemeniz gerekir.

## Adım 5 – Dosyayı kaydetme ve sonucu doğrulama

Son olarak belgeyi diske kalıcı olarak kaydediyoruz. İstediğiniz herhangi bir yolu seçebilirsiniz; sadece klasörün var olduğundan emin olun.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

*ShadowRectangle.docx* dosyasını Microsoft Word’de açtığınızda, 200 × 100 puanlık bir dikdörtgenin, koyu gri, hafif bulanık, %30 saydam bir gölgeyle üç puan sağa ve aşağı kaydırılmış olarak göründüğünü fark edeceksiniz. Etki ince ama düz tasarımlara derinlik katıyor.

![create rectangle shape with shadow in Aspose.Words](https://example.com/placeholder-image.png "create rectangle shape with shadow in Aspose.Words")

*Görsel alt metni:* **Aspose.Words'te gölgeli dikdörtgen şekli oluşturma** – resim, gölgeli dikdörtgenin bulunduğu son belgeyi gösterir.

## Yaygın varyasyonlar ve kenar durumları

### Gölge rengini dinamik olarak değiştirme

Uygulamanız temaları destekliyorsa, gölge rengini bir yapılandırma dosyasından çekebilirsiniz:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### Şekli satır içi olmayan (non‑inline) hâle getirme

Bazen dikdörtgenin metnin üzerinde süzülmesini istersiniz. `WrapType` değerini `WrapType.Square` olarak değiştirin ve daha fazla kontrol için `RelativeHorizontalPosition` değerini `RelativeHorizontalPosition.Margin` olarak ayarlayın.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Çoklu sayfalarla başa çıkma

Her sayfada bir dikdörtgen ihtiyacınız varsa, `doc.Sections` içinde döngü yaparak her bölümün ilk paragrafına klonlanmış bir şekil ekleyin. Gölge ayarlarını da kopyalamak için `rect.Clone(true)` çağırmayı unutmayın.

## Özet – Neler başardık

- Aspose.Words kullanarak **dikdörtgen şekli oluşturduk**
- **Gölge ekleme** yöntemini renk, offset, bulanıklaştırma ve saydamlık ile gösterdik
- **apply blur to shadow** ve **make shadow transparent** kavramlarını uyguladık
- Anında açabileceğiniz bir Word dosyası kaydettik

Tüm bunlar sadece birkaç satır kodla gerçekleştirildi; bu da karmaşık görsel ayarların her zaman ağır grafik kütüphanelerine ihtiyaç duymadığını kanıtlıyor.

## Sıradaki adımlar

- Diğer `ShapeType` değerlerini (Ellipse, Cloud vb.) deneyin ve gölgelerin nasıl davrandığını görün.
- Dikdörtgeni metin kutuları ile birleştirerek etiketli açıklamalar oluşturun.
- **how to create document** şablonlarıyla şekiller için yer tutucular içeren şablonlar hazırlayın, ardından bunları programlı olarak doldurun.

Bulanıklaştırma yarıçapını, rengi ya da saydamlığı tasarım dilinize uygun olana kadar ayarlamaktan çekinmeyin. API affedicidir ve değişiklikler, konsol uygulamasını yeniden çalıştırdığınızda anında görülür.

Kodlamanın tadını çıkarın, belgeleriniz her zaman ekstra bir derinlik dokunuşuna sahip olsun!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}