---
category: general
date: 2026-03-06
description: Word'de dikdörtgen şekli oluşturun ve Aspose.Words ile şekle gölge ekleyin.
  Word'de dikdörtgen eklemeyi ve C#'ta şekle gölge eklemeyi öğrenin.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: tr
og_description: Word'de dikdörtgen şekli oluşturun ve Aspose.Words ile şekil gölgesi
  ekleyin. Word'de dikdörtgen ekleme ve şekle gölge ekleme adım adım rehberi.
og_title: Aspose.Words ile Word'de gölgeli dikdörtgen şekli oluştur
tags:
- Aspose.Words
- C#
- Word Automation
title: Aspose.Words ile Word'de gölgeli dikdörtgen şekli oluştur
url: /tr/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Aspose.Words kullanarak gölge ile dikdörtgen şekil oluşturma

Word belgesinde **create rectangle shape** oluşturmanız gerektiğinde, ona o cilalı görünümü nasıl vereceğinizden emin olmadınız mı? Yalnız değilsiniz—çoğu geliştirici, otomatik belgelerine görsel bir dokunuş eklemeye çalıştığında aynı sorunu yaşar. İyi haber? Aspose.Words for .NET ile sadece birkaç C# satırıyla **create rectangle shape** ve **add shape shadow** yapabilirsiniz.

Bu öğreticide, **how to insert rectangle in Word** adımını tam olarak gösterecek, ardından **how to add shadow to shape** göstererek şeklin sayfadan çıkmasını sağlayacağız. Sonunda, Word'de açabileceğiniz ve yumuşak bir gölgeye sahip gri tonlu bir dikdörtgen göreceğiniz, kaydetmeye hazır `Shadow.docx` dosyanız olacak. Ekstra resim dosyası yok, manuel ayarlama yok—sadece kod.

## Neler Öğreneceksiniz

- Aspose.Words ile **create rectangle shape** oluşturmak için gereken tam C# ifadeleri.  
- `Shadow` nesnesini kullanarak gölgeyi nasıl etkinleştirip yapılandıracağınız.  
- Her özelliğin neden önemli olduğu (ör. `Transparency`, `Blur`, `Angle`).  
- Yaygın tuzaklar (birimler, sürüm uyumluluğu) ve hızlı çözümler.  
- Bugün çalıştırabileceğiniz eksiksiz, kopyala‑yapıştır hazır bir program.

### Önkoşullar

- .NET 6+ (veya .NET Framework 4.7+).  
- Aspose.Words for .NET 23.10 veya daha yeni sürüm (NuGet paketi `Aspose.Words`).  
- C# ve Visual Studio (veya tercih ettiğiniz herhangi bir IDE) hakkında temel bir anlayış.  

Bunlara sahipseniz, doğrudan başlayalım.

---

## Adım 1: Projeyi kurun ve ad alanlarını içe aktarın

İlk olarak, yeni bir konsol uygulaması oluşturun (veya mevcut birini yeniden kullanın) ve Aspose.Words NuGet paketini ekleyin:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Şimdi gerekli ad alanlarını `Program.cs` dosyanıza ekleyin:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Pro tip:** .NET 6+ hedefliyorsanız, bu satırları her dosyada tekrarlamamak için global `using` yönergelerini etkinleştirebilirsiniz.

## Adım 2: Boş bir Word belgesinde **Create rectangle shape**

Yeni bir `Document` nesnesi ve onu manipüle etmek için bir `DocumentBuilder` ile başlayacağız. Builder'ın `InsertShape` metodu sihrin gerçekleştiği yerdir.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Neden 200 × 100 point? Word'de bir point, inçin 1/72'sine eşittir, bu yüzden dikdörtgen yaklaşık 2.8 × 1.4 inç olur—gözle görülür ama çok büyük değil. Bu sayıları düzeninize göre değiştirebilirsiniz; sadece **points** cinsinden ölçüldüklerini, piksel olmadığını unutmayın.

## Adım 3: **Add shape shadow** – görünümü yapılandırma

Artık bir dikdörtgenimiz olduğuna göre, ona hafif bir gri gölge ekleyelim. `Shadow` nesnesi `Shape` üzerinde bulunur ve birkaç kullanışlı özelliği ortaya çıkarır.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Her özelliğin ne yaptığı

| Özellik | Etkisi | Tipik değerler |
|----------|--------|----------------|
| **Enabled** | Gölgeyi açar/kapatır | `true` veya `false` |
| **Color** | Gölgenin temel rengi | Any `System.Drawing.Color` |
| **Transparency** | Opaklık (0 = katı, 1 = görünmez) | 0.0 – 1.0 |
| **Blur** | Kenar yumuşaklığı | 0 – 10 (yüksek = daha yumuşak) |
| **Distance** | Şekil ile gölge arasındaki boşluk | 0 – 20 point |
| **Angle** | Işığın geldiği yön | 0 – 360 derece |
| **Size** | Gölgenin şekle göre ölçeği | 0 – 200 % |

> **Neden bu ayarlarla uğraşasınız?**  
> Gölgeyi ince ayar yapmak, kurumsal marka yönergelerine (ör. profesyonel bir görünüm için hafif %20 şeffaflık) uymanızı sağlar ve harici görüntü düzenleyicilere başvurmanıza gerek kalmaz.

## Adım 4: Belgeyi kaydedin ve sonucu doğrulayın

Son olarak, dosyayı diske yazın. İstediğiniz herhangi bir klasörü seçebilirsiniz; sadece `YOUR_DIRECTORY` ifadesini gerçek bir yol ile değiştirin.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

`Shadow.docx` dosyasını Microsoft Word'de açın ve 45° açıyla hafif bir gölgeye sahip gri bir dikdörtgen görmelisiniz. Bu görsel ipucu, şeklin sayfadan “kaldırılmış” hissetmesini sağlar—cilalı bir rapor veya faturadan bekleyeceğiniz tam şey.

## Tam Çalışan Örnek

Aşağıda, `Program.cs` içine kopyala‑yapıştır yapabileceğiniz eksiksiz program yer alıyor. Hiçbir parça eksik değil; olduğu gibi derlenir ve çalışır.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Beklenen Çıktı

- **Dosya:** `Shadow.docx` proje çalışma klasörüne yerleştirilir.  
- **Görsel:** Sayfanın ortasında tek bir dikdörtgen, varsayılan beyaz ile doldurulmuş ve gri gölge 4 point aşağı‑sağa kaydırılmış, doğal bir görünüm için hafif bulanıklaştırılmış.

## Sık Sorulan Sorular & Kenar Durumları

### 1. Farklı bir birime (ör. santimetre) ihtiyacım olsaydı ne olur?

Aspose.Words point biriminde çalışır, ancak santimetreyi point'e basit bir formülle dönüştürebilirsiniz:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Bu, eski Aspose.Words sürümleriyle çalışır mı?

`Shadow` API'si version 14.0'da tanıtıldı. Daha eski bir sürüm kullanıyorsanız, NuGet üzerinden yükseltmeniz gerekir. Kodun geri kalan kısmı (şekil oluşturma) yıllardır stabil olduğu için kırılma hatalarıyla karşılaşmazsınız.

### 3. Diğer şekillere (ör. daireler) gölge ekleyebilir miyim?

Kesinlikle—her `Shape` nesnesi bir `Shadow` özelliği sunar. `ShapeType.Rectangle` yerine `ShapeType.Ellipse` veya `ShapeType.Cloud` kullanın, ardından aynı gölge ayarlarını uygulayın.

### 4. Renkli bir gölgeye (ör. marka için mavi) ihtiyacım olsaydı ne yapmalıyım?

`Color.Gray` ifadesini istediğiniz herhangi bir `Color` ile değiştirin:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

`Transparency` değerini ayarlamayı unutmayın, böylece renk çok baskın olmaz.

## 🎨 Görsel Özet

![Word'de Aspose.Words kullanarak gölge ile dikdörtgen şekil oluşturma](image-placeholder.png "Word'de Aspose.Words kullanarak gölge ile dikdörtgen şekil oluşturma")

*Alt text: Word'de Aspose.Words kullanarak gölge ile dikdörtgen şekil oluşturma*

Ekran görüntüsü (yer tutucu) son belgeyi gösterir—sadece dikdörtgen ve yumuşak gri gölgesi.

## Sonuç

Artık bir Word dosyasında **create rectangle shape** nasıl yapılacağını, **add shape shadow** nasıl ekleneceğini ve Aspose.Words for .NET kullanarak her görsel öğeyi nasıl ince ayar yapacağınızı biliyorsunuz. Oluşturduğumuz kısa program tüm iş akışını kapsar—  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}