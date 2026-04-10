---
category: general
date: 2026-04-10
description: C#'ta bir şekle gölge ayarlama – gölge eklemeyi, şeffaflığı değiştirmeyi,
  bulanıklığı ayarlamayı ve Aspose.Words kullanarak şekil gölgesi eklemeyi öğrenin.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: tr
og_description: C#'ta bir şekle gölge ayarlama – bu öğretici, düşey gölge uygulamayı,
  şeffaflığı değiştirmeyi, bulanıklığı ayarlamayı ve net kod örnekleriyle şekil gölgesi
  eklemeyi gösterir.
og_title: C#'ta bir şekle gölge ekleme – Tam Kılavuz
tags:
- Aspose.Words
- C#
- Document Automation
title: C#'ta bir şekle gölge ayarlama – adım adım rehber
url: /tr/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta bir şekle gölge nasıl eklenir – Tam Kılavuz

Bir Word belgesini programlı olarak oluştururken bir şekle **gölge nasıl eklenir** diye merak ettiniz mi? Yalnız değilsiniz. Birçok geliştirici, bir metin kutusu, logo veya açıklama kutusu için ince bir gölgeye ihtiyaç duyduğunda zorlanıyor ve API belgeleri yetersiz kalıyor.  

Bu öğreticide tüm süreci adım adım inceleyeceğiz: bir `.docx` dosyasını yüklemek, ilk `Shape` nesnesini almak, gölge eklemek, şeffaflığını ayarlamak, bulanıklık yarıçapını düzenlemek ve sonunda konumunu tam olarak ayarlamak. Sonunda Aspose.Words .NET 2023 ve üzeriyle çalışan yeniden kullanılabilir bir kod parçacığına sahip olacaksınız ve *her bir özelliğin neden önemli* olduğunu anlayacaksınız.

## İhtiyacınız Olanlar

- **Aspose.Words for .NET** (NuGet paketi `Aspose.Words`) – `Document`, `Shape` ve `ShadowFormat` sınıflarını sağlayan kütüphane.  
- **.NET 6+** (veya .NET Framework 4.7.2) – herhangi bir yeni çalışma zamanı yeterli.  
- En az bir şekil (ör. metin kutusu) içeren basit bir Word dosyası (`input.docx`).  
- Visual Studio, VS Code veya tercih ettiğiniz IDE.

Hepsi bu. Ek üçüncü‑taraf araçları, COM interop yok, sadece saf C#.

![how to set shadow example](image-placeholder.png){:alt="Word belgesinde bir şekle gölge nasıl eklenir"}

## Gölge Ayarlama – Genel Bakış

**gölge nasıl eklenir** sorusunun temel fikri, bir `Shape` üzerinde bulunan `ShadowFormat` nesnesini manipüle etmektir. `ShadowFormat`ı gölgenin kendisi için mini bir “stil sayfası” gibi düşünün: renderlayıcıya gölgenin görünür olup olmadığını, hangi renkte olacağını, ne kadar şeffaf olacağını, ne kadar bulanık olacağını ve şekle göre nerede konumlanacağını söyler.  

Aşağıda *tam* çalıştırılabilir bir program bulunuyor. Konsol uygulamasına kopyalayıp **F5** tuşuna basın, kaydedilen `output.docx` içinde gölgenin belirdiğini izleyin.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Bu Ayarların Önemi

- **Visible** – Bu bayrak açılmadan diğer tüm özellikler yok sayılır.  
- **Color** – Koyu gri, tipik bir UI gölgesi taklit eder; istediğiniz herhangi bir `Color` ile değiştirebilirsiniz.  
- **Transparency** – 0.3, şekli okunabilir tutarken *yumuşak* bir görünüm verir.  
- **Size** – Bulanıklığı kontrol eder; 6 değeri genellikle profesyonel bir his için yeterlidir.  
- **Distance & Angle** – Birlikte *offset*i tanımlar; 2 pt ve 45° hafif çapraz bir gölge oluşturur.

Bu, **gölge nasıl eklenir** konusunun özüdür. Şimdi her bir parçayı ayrıntılı inceleyecek, **drop shadow uygulama**, **şeffaflığı değiştirme**, **bulanıklığı ayarlama** ve **şekil gölgesi ekleme** işlemlerini tek tek yapabileceksiniz.

---

## Bir Şekle Drop Shadow Uygulama

İnsanlar “C#’ta **drop shadow nasıl uygulanır**?” diye sorduğunda genellikle sadece görünürlük anahtarı ve bir renk gerekir. Aşağıdaki kod parçacığı bu iki satırı izole eder:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Pro tip:** Daha eski Word sürümlerini (2003‑2007) hedefliyorsanız standart renkleri kullanın. Bazı egzotik ARGB değerleri eski renderlayıcı tarafından göz ardı edilebilir.

---

## Gölgenin Şeffaflığını Değiştirme

Şeffaflık, **0 ile 1 arasında bir float** olarak ifade edilir. **0** değeri tamamen opak bir gölge, **1** değeri ise gölgenin görünmez olmasını sağlar. Çoğu tasarımcı doğal bir görünüm için **0.2‑0.4** arasında bir değer tercih eder.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Kenar Durumları

- **Negatif değerler** – Aspose.Words bunları 0’a kısıtlar, ancak girdi doğrulaması yapmak daha iyidir.  
- **1’den büyük değerler** – 1’e kısıtlanır, gölge etkili bir şekilde gizlenir.  

Kullanıcıların yüzde seçebilmesi gerekiyorsa, önce dönüştürün:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Gölgenin Bulanıklığını (Size) Ayarlama

**Size** özelliği bulanıklık yarıçapını kontrol eder. Daha büyük sayılar daha yumuşak, daha dağınık bir gölge üretir. Ölçü birimi nokta (pt) olup piksel değildir.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Küçük vs. Büyük Bulanıklık Ne Zaman Kullanılır

- **Small blur (2‑4 pt)** – Kenarı net istediğiniz UI‑stil çağrı kutuları için iyidir.  
- **Large blur (8‑12 pt)** – Baskı raporları veya şekil arka plandan uzakta olduğunda iyi çalışır.

---

## Şekil Gölgesi Ekleme – Konumlandırma ve Yön

**add shape shadow** konusunun son parçası offsettir. İki özellik birlikte çalışır:

| Özellik | Anlam |
|----------|---------|
| **Distance** | Gölgenin şekilden ne kadar uzakta durduğunu (puan cinsinden). |
| **Angle**    | Ofsetin yönü (0° = sağ, 90° = aşağı, 180° = sol, 270° = yukarı). |

Alt‑sağ köşeye hafif bir gölge oluşturan örnek:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Farklı ışık kaynaklarını taklit etmek için açıları deneyebilirsiniz. Yaygın bir hile, kullanıcının bir “ışık kaynağı”nı açılır menüden seçmesine izin vermek ve bunu bir açı değerine eşlemek.

---

## Tam Çalışan Örnek (Tüm Adımlar Birleşti)

Aşağıda önceki program aynı, ancak mantığı kristal‑net yapan **ekstra yorumlar** eklenmiştir. Bunu `Program.cs` içine kopyalayın ve çalıştırın; çıktı dosyası mükemmel ayarlanmış bir gölgeye sahip bir metin kutusu içerecek.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Beklenen sonuç:** `output.docx` dosyasını açın. İlk metin kutusu, %30 şeffaf, koyu gri bir gölge gösterecek; hafif bulanık (size = 6) ve 2 pt, 45° açıyla offsetlenmiş olacaktır. Etki ince ama fark edilir—çoğu UI tasarımcısının hedeflediği tam o şey.

---

## Sık Sorulan Sorular & Dikkat Edilmesi Gerekenler

- **“Bu, görseller için de çalışır mı?”**  
  Evet. Herhangi bir `Shape`—metin kutusu, resim veya otomatik şekil olsun—`ShadowFormat` sunar. Sadece şekil alma mantığını uygun indeks veya isimle değiştirin.

- **“Belgede birden fazla şekil olursa ne olur?”**  
  `doc.GetChildNodes(NodeType.Shape, true)` üzerinden döngü kurarak aynı ayarları her birine uygulayın. Ayrıca `shape.Name` veya `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}