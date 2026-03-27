---
category: general
date: 2026-03-27
description: C# ile Word belgesi oluşturun ve şekil eklemeyi, şekle gölge uygulamayı
  ve gölge mesafesini ayarlamayı öğrenin. Aspose.Words için adım adım rehber.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: tr
og_description: C# ile bir dikdörtgen şekli ve özel gölge içeren Word belgesi oluşturun.
  Gölge mesafesini ve stilini ayarlamak için bu tam öğreticiyi izleyin.
og_title: C# ile Word Belgesi Oluştur – Gölgeli Şekil Ekle
tags:
- Aspose.Words
- C#
- Document Automation
title: Word Belgesi Oluştur C# – Gölgeli Şekil Ekle
url: /tr/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesi Oluştur C# – Gölgelikli Şekil Ekle

Hiç **create word document c#** gibi güzel stil verilmiş bir dikdörtgen içeren bir Word belgesi oluşturmanız gerekti mi? Belki bir rapor şablonu oluşturuyorsunuz ve düzeni öne çıkarmak için ince bir gölge eklemek istiyorsunuz. Bu öğreticide tam olarak bunu adım adım göstereceğiz – şekil ekleme, şekle gölge uygulama ve gölge mesafesini Aspose.Words kullanarak ayarlama.

Boş bir belgeyle başlayacağız, bir dikdörtgen ekleyeceğiz, ön tanımlı bir gölge vereceğiz ve dosyayı kaydederek bitireceğiz. Sonunda, Word’de açıp etkisini anında görebileceğiniz hazır bir .docx dosyanız olacak. Harici araç gerekmez, sadece saf C# kodu.

## Önkoşullar

- .NET 6 (veya herhangi bir yeni .NET Framework) yüklü.
- Visual Studio 2022 veya C# uzantılı VS Code.
- Aspose.Words for .NET NuGet paketi (`Aspose.Words` sürüm 23.12 veya daha yeni).  
  Paketi Package Manager Console üzerinden ekleyebilirsiniz:

  ```powershell
  Install-Package Aspose.Words
  ```

Hepsi bu – ekstra DLL veya COM interop gerekmez.

## Adım 1: Yeni Bir Belge ve Builder Başlatma – *create word document c#* Temelleri

İlk olarak Word dosyasını temsil eden bir `Document` nesnesine ve onu düzenlemek için bir `DocumentBuilder` nesnesine ihtiyacımız var.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why this step matters:** `Document` sınıfı tüm Word parçalarının (sayfalar, stiller, görseller) konteyneridir. Builder, düşük seviyeli düğüm manipülasyonunu soyutlayan yüksek‑seviye bir API olup, XML ile uğraşmadan **create word document c#** yapmayı kolaylaştırır.

## Adım 2: Dikdörtgen Şekli Ekle – *how to create rectangle*  

Şimdi sayfaya bir dikdörtgen yerleştireceğiz. Boyut, puan cinsinden ifade edilir (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Pro tip:** Farklı bir şekle ihtiyacınız varsa, sadece `ShapeType.Rectangle` yerine `ShapeType.Ellipse`, `ShapeType.Triangle` vb. kullanın. Aynı kod **how to add shape** için her türlü şekil ile çalışır.

## Adım 3: Ön Tanımlı Gölge Uygula ve İnce Ayar Yap – *apply shadow to shape*  

Aspose.Words birkaç ön tanımlı gölge formatı sunar. `Preset1` kullanacağız ve ardından mesafe, bulanıklık, şeffaflık ve rengi özelleştireceğiz.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Why customize the shadow?** `Distance` özelliği gölgenin dikdörtgenden ne kadar uzakta durduğunu kontrol eder – bunu bir 3‑D renderda gördüğünüz “kaldırma” olarak düşünebilirsiniz. `BlurRadius` kenarları yumuşatırken, `Transparency` daha ince, profesyonel bir görünüm sağlar. Bu, **set shadow distance** gereksinimini karşılar ve **apply shadow to shape** işlemini esnek bir şekilde yapmanızı gösterir.

## Adım 4: Belgeyi Kaydet – *create word document c#* Tamamlanması

Son olarak belgeyi diske yazalım. Yazma izniniz olan bir klasöre yolu ayarlayın.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Oluşan dosyayı Microsoft Word’de açın; 5 pt kaydırılmış, hafif gri bir gölgeye sahip açık mavi bir dikdörtgen göreceksiniz. Bu, stil verilmiş bir şekil ile **create word document c#** başarılı bir şekilde oluşturduğunuzun görsel kanıtıdır.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="create word document c# örneği, gölgeli dikdörtgen gösterimi"}

## İsteğe Bağlı Varyasyonlar ve Kenar Durumları

| Senaryo | Ne Değiştirilmeli | Neden Önemli |
|----------|-------------------|--------------|
| **Farklı gölge stili** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Ek kod yazmadan daha çarpıcı bir görünüm sağlar. |
| **Ön tanımlı yok – özel gölge** | `Format` özelliğini atlayıp `OffsetX`, `OffsetY` değerlerini manuel ayarlayın. | Yön ve derinlik üzerinde tam kontrol sağlar. |
| **Birden çok şekil** | Kaydetmeden önce `builder.InsertShape` komutunu tekrar çağırın. | İkon, logo gibi öğeler içeren karmaşık şablonlar için faydalıdır. |
| **Eski Aspose sürümleriyle uyumluluk** | `ShadowEffect` sınıfını kullanın (v20.x’te mevcut). | Kodunuzun eski projelerde çalışmasını garantiler. |
| **PDF olarak kaydetme** | `document.Save("ShadowShape.pdf");` | Aynı gölge renderı PDF çıktısında da görülür. |

> **Common question:** *What if the shadow doesn’t appear in Word?*  
> Aspose.Words’un (≥ 22.9) güncel bir sürümünü kullandığınızdan emin olun. Eski sürümlerde gölge desteği sınırlıydı. Ayrıca belgenin Word 2016+ gibi yeni bir sürümde açıldığını doğrulayın.

## Tam Çalışan Örnek

Aşağıda tamamen kopyala‑yapıştır hazır program yer alıyor. Tüm `using` yönergeleri, yorumlar ve sorunsuz bir deneyim için hata yönetimi içerir.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Programı çalıştırın, `C:\Temp\ShadowShape.docx` konumuna gidin ve yapılandırdığımız tam gölgeye sahip dikdörtgeni görün.

## Özet ve Sonraki Adımlar

- Artık **create word document c#**, bir dikdörtgen ekleme ve **apply shadow to shape** işlemini özel bir **set shadow distance** ile nasıl yapacağınızı biliyorsunuz.  
- Örnek, OpenXML karmaşıklıklarını soyutlayan ve Word sürümleri arasında tutarlı render garantileyen Aspose.Words kullanıyor.  
- Daha ileri gitmek ister misiniz? Birden çok şekli birleştirmeyi, dikdörtgenin içine metin eklemeyi veya aynı belgeyi PDF olarak dışa aktarmayı deneyin; gölgenin nasıl aktığını göreceksiniz.

### İlgili Konular

- **How to add shape** başlık/altbilgiye marka eklemek için.  
- **Aspose.Words** kullanarak programatik olarak grafik ve tablo eklemek.  
- Vektörel şekiller yerine resimlerde **shadow effects** özelleştirme.  
- Faturalar veya sertifikalar için toplu belge üretimini otomatikleştirme.

Deney yapmaktan, kodu kırmaktan ve ardından yeniden inşa etmekten çekinmeyin – bu, kavramları içselleştirmenin en hızlı yoludur. Bir sorunla karşılaşırsanız, aşağıya yorum bırakın veya daha derin API bilgileri için resmi Aspose.Words dokümantasyonuna bakın.

Kodlamanın tadını çıkarın ve Word dosyalarınızı biraz daha şık hâle getirin!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}