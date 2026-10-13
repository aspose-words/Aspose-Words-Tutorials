---
category: general
date: 2026-03-19
description: Aspose.Words ile C#'ta Word belgesi oluşturun, şekil eklemeyi, dikdörtgen
  şekli eklemeyi, gölge uygulamayı öğrenin ve belgeyi dakikalar içinde docx olarak
  kaydedin.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: tr
og_description: Aspose.Words ile Word belgesi oluşturun, dikdörtgen şekil ekleyin,
  dış gölge uygulayın ve belgeyi docx olarak kaydedin. Adım adım kılavuz.
og_title: Word Belgesi Oluştur – Dikdörtgen Şekil ve Gölge Ekle
tags:
- Aspose.Words
- C#
- Document Automation
title: Word Belgesi Oluştur – Dikdörtgen Şekil ve Gölge Nasıl Eklenir
url: /tr/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesi Oluşturma – Dikdörtgen Şekil ve Gölge Ekleme

Programatik olarak **create word document** ihtiyacı hiç duydunuz mu ve nereden başlayacağınızı merak ettiniz mi? Yalnız değilsiniz. Birçok geliştirici, özel grafikler içeren bir .docx dosyası oluşturmaya ilk kez çalıştıklarında aynı duvara çarpar. Bu öğreticide, sürecin tamamını adım adım göstereceğiz—şekil ekleme, özellikle bir **add rectangle shape**, ona şık bir **add shadow to shape**, ve sonunda **save document as docx**.

Kılavuzun sonunda, herhangi bir .NET projesine ekleyebileceğiniz hazır bir C# kod parçacığına sahip olacaksınız. Belirsiz referanslar yok, sadece eksiksiz, çalıştırılabilir bir örnek.

## Önkoşullar

- .NET 6.0 veya üzeri (kod .NET Framework ile de çalışır).  
- Aspose.Words for .NET yüklü (NuGet paketi `Aspose.Words`).  
- C# sözdizimi hakkında temel bir anlayış—özel bir şey gerekmez.  

Kütüphane eksikse, şu komutu çalıştırın:

```bash
dotnet add package Aspose.Words
```

Hepsi bu—ek SDK'lar, COM interop yok, sadece tek bir NuGet referansı.

## Adım 1: Word Belgesi Oluşturma (Ana Hedef)

İlk ihtiyacımız temiz bir tuval. `Document` sınıfını Microsoft Word'te yeni bir sayfa gibi düşünün; bölümler, paragraflar ve daha sonra ekleyeceğiniz her şeyi tutar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Neden boş bir `Document` ile başlıyoruz? Çünkü bir şablondan gizli biçimlendirmelerin sızmasını engeller. Benim deneyimime göre, sıfırdan başlamak, daha sonra şekil eklediğinizde ortaya çıkan gizemli düzen kaymalarını önler.

## Adım 2: Dikdörtgen Şekil Ekleme – Görsel Öğeyi Eklemek

Şimdi bir belgemiz olduğuna göre, ilk paragrafına **add rectangle shape** ekleyelim. `Shape` nesnesi çok yönlü; `ShapeType.Rectangle`, `Ellipse` veya hatta özel çizimler seçebilirsiniz. İşte en temel kod:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**Altında ne oluyor?**  
- `ShapeType.Rectangle` Aspose'a basit bir kutu istediğimizi söyler.  
- `WrapType.Inline` dikdörtgenin metin akışıyla birlikte hareket etmesini sağlar; bu genellikle bir kelime işlem senaryosunda beklediğiniz şeydir.  
- `FirstParagraph`'a ekleyerek yeni bir paragraf manuel ekleme ihtiyacını ortadan kaldırırız; belge gerçekten boşsa Aspose bizim için bir tane oluşturur.

> **Pro tip:** Şeklin metnin *arkasında* durması gerekiyorsa, `WrapType`'ı `WrapType.Transparent` olarak değiştirin. Bu küçük değişiklik büyük bir görsel fark yaratabilir.

## Adım 3: Dış Gölge Uygulama – Görünümü Geliştirme

Düz bir dikdörtgen… yani, düzdür. **add shadow to shape** eklemek, ekstra görüntü olmadan derinlik kazandırır. Aspose'un `ShadowFormat`'ı bunu tek satırda yapar.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Bu belirli değerlerle neden uğraşıyoruz?  
- `5.0` **Blur**, çoğu monitörde profesyonel görünen hafif tüylü bir kenar verir.  
- `3.0` **Distance** ve `45` **Angle**, üst‑sol köşeden doğal bir ışık kaynağı oluşturur, yaygın bir tasarım kuralıdır.  
- **Color.Gray**, hem açık hem koyu temalarda çalışır; daha güçlü bir kontrast gerekiyorsa `Color.Black` ile değiştirebilirsiniz.

Eğer bir *iç* gölgeye ihtiyacınız olursa (örneğin gömülü bir düğme), sadece `ShadowType.OuterShadow`'ı `ShadowType.InnerShadow` olarak değiştirin. Aynı özellikler hâlâ geçerlidir.

## Adım 4: Belgeyi DOCX Olarak Kaydetme – Çalışmanızı Kalıcı Hale Getirme

Tüm eğlence güzel, ama sonunda diskte bir dosya isteyeceksiniz. **save document as docx** adımı basittir:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Birkaç not:  
- `SaveFormat.Docx` enum'u modern Office Open XML formatını garantiler; bu, Word 2007+ ile uyumludur.  
- Dosyayı doğrudan bir web yanıtına akıtmanız gerekiyorsa, dosya yolunu bir `MemoryStream` ile değiştirin ve HTTP yanıtına yazın.

Kodu çalıştırdıktan sonra, `ShadowedRectangle.docx` dosyasını Microsoft Word'de açın. İlk paragrafla satır içinde duran, yumuşak bir gölgeye sahip gri bir dikdörtgen görmelisiniz—tam da ulaşmak istediğimiz şey.

## Şekil Ekleme – Alternatif Yaklaşımlar

Yukarıdaki örnek *inline* yaklaşımını kullanıyor, ancak bazen metnin üzerinde süzülen bir şekil istersiniz. İşte farklı sarma seçenekleriyle **how to add shape** devreye girer.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Burada `WrapType`'ı `Square` olarak değiştirdik ve şekli sayfanın ortasına yerleştirdik. Bu desen kapak sayfaları veya dekoratif afişler için faydalıdır. Unutmayın: yüzen şekiller, Word ek konumlandırma verileri sakladığı için dosya boyutunu biraz artırır.

## Beklenen Çıktı ve Doğrulama

Oluşturulan dosyayı açtığınızda şunları görmelisiniz:

- Gri bir dikdörtgen içeren tek bir paragraf.  
- Dikdörtgen yaklaşık 2.8 × 1.4 inç ölçülerinde.  
- Alt‑sağ köşeye doğru hafif bir dış gölge.  

Şekil paragrafın *dışında* görünüyorsa, `WrapType`'ı tekrar kontrol edin. Gölge çok sert görünüyorsa, `Blur` değerini düşürün veya `Color`'ı daha açık bir tona değiştirin.

## Yaygın Tuzaklar ve Nasıl Önlenir

| Sorun | Neden Olur | Çözüm |
|-------|------------|------|
| Kaydedildikten sonra şekil kaybolur | `WrapType` `Inline` olarak ayarlandı ancak paragraf kaldırıldı | Paragrafın var olduğundan emin olun; bunu sağlamak için `doc.FirstSection.Body.FirstParagraph` kullanın. |
| Gölge pikselli görünüyor | Çok düşük bir `Blur` değeri kullanmak | Kenarların pürüzsüz olması için `Blur` değerini en az `3.0`'a yükseltin. |
| Dosya boyutu şişiyor | Şekillerin yanında birçok yüksek çözünürlüklü görüntü eklemek | Görüntü eklediyseniz kaydetmeden önce `doc.RemoveUnusedResources()` kullanın. |
| Renk karanlık modda görünmüyor | Şeklin kendisi için koyu bir `Color` kullanmak | Daha iyi görünürlük için zıt bir renk seçin (ör. `Color.White`). |

## Tam Çalışan Örnek

Aşağıda, konuştuğumuz her şeyi içeren eksiksiz, kopyala‑yapıştır‑hazır kod bulunmaktadır. Konsol uygulaması olarak çalıştırabilirsiniz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Açıklama** her blok için yorum satırları içinde verilmiştir, hem SEO okuyucularını hem de kendi kendine yanıt veren AI asistanlarını memnun eder.

## Sonuç

Sıfırdan **create word document** oluşturduk, **how to add shape** öğrettik, özellikle bir **add rectangle shape**, ona bir **add shadow to shape** ekledik ve sonunda **save document as docx** yaptık. Adımlar basit, kod kompakt ve sonuç şık görünüyor.

Daha ileri gitmeye hazırsanız, dikdörtgeni özel bir görüntüyle değiştirin, farklı gölge renkleriyle deney yapın veya birden fazla şekilli bölümlerle tam bir rapor oluşturun. Aspose.Words API'si, faturadan pazarlama broşürlerine kadar her şeyi yönetebilecek kadar esnektir.

Diğer şekil tipleri hakkında sorularınız mı var ya da bunu bir ASP.NET Core servisine entegre etme konusunda yardıma mı ihtiyacınız var? Aşağıya yorum bırakın, iyi kodlamalar!

![create word document with rectangle shape and shadow](placeholder-image.png "create word document with rectangle shape and shadow

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}