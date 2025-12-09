---
category: general
date: 2025-12-08
description: Aspose.Words ile şekle hızlıca gölge ekleyin. Aspose kullanarak Word
  belgesi oluşturmayı, şekle gölge eklemeyi ve C#'ta gölge şeffaflığını uygulamayı
  öğrenin.
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: tr
og_description: Word dosyasında bir şekle gölge ekleyin Aspose.Words kullanarak. Bu
  adım adım kılavuz, bir belge oluşturmayı, bir şekil eklemeyi ve gölge şeffaflığını
  uygulamayı gösterir.
og_title: Şekle Gölge Ekle – Aspose.Words C# Öğreticisi
tags:
- Aspose.Words
- C#
- Word Automation
title: Word Belgesindeki Şekle Gölge Ekle – Tam Aspose.Words Rehberi
url: /turkish/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# Şekle Gölge Ekle – Tam Aspose.Words Rehberi

Bir Word dosyasında **şekle gölge ekleme** ihtiyacı duyup hangi API çağrılarını kullanacağınızdan emin olmadınız mı? Yalnız değilsiniz. Birçok geliştirici, özellikle Aspose.Words for .NET ile çalışırken, bir dikdörtgen ya da herhangi bir çizim öğesine doğru bir drop‑shadow vermeye çalıştıklarında bir engelle karşılaşıyor.

Bu öğreticide, bilmeniz gereken her şeyi adım adım inceleyeceğiz: **Aspose kullanarak Word belgesi oluşturma**'dan gölgeyi yapılandırmaya, bulanıklığını, mesafesini, açısını ayarlamaya ve hatta **gölge şeffaflığını uygulamaya** kadar. Sonunda, Word'de manuel ayarlama yapmadan güzel gölgeli bir dikdörtgen üreten, çalıştırmaya hazır bir C# programına sahip olacaksınız.

---

## Öğrenecekleriniz

- Visual Studio'da bir Aspose.Words projesi nasıl kurulur.  
- Aspose kullanarak **Word belgesi oluşturma** ve bir şekil ekleme adımları.  
- **Şekle gölge ekleme** ve bulanıklık, mesafe, açı ve şeffaflık üzerinde tam kontrol.  
- Yaygın sorunları giderme ipuçları (ör. eksik lisans, hatalı birimler).  
- Bugün çalıştırabileceğiniz eksiksiz, kopyala‑yapıştır kod örneği.

> **Önkoşullar:** .NET 6+ (veya .NET Framework 4.7.2+), geçerli bir Aspose.Words lisansı (veya ücretsiz deneme), ve C# hakkında temel bir aşinalık.

---

## Adım 1 – Projenizi Kurun ve Aspose.Words Ekleyin

İlk olarak, Visual Studio'yu açın, yeni bir **Console App (.NET Core)** oluşturun ve Aspose.Words NuGet paketini ekleyin:

```bash
dotnet add package Aspose.Words
```

> **Pro ipucu:** Eğer bir lisans dosyanız (`Aspose.Words.lic`) varsa, proje kök dizinine kopyalayın ve başlangıçta yükleyin. Bu, ücretsiz değerlendirme modunda görülen filigranı önler.

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

---

## Adım 2 – Yeni Boş Bir Belge Oluşturun

Şimdi gerçekten **Aspose kullanarak Word belgesi oluşturuyoruz**. Bu nesne, şeklimiz için bir tuval görevi görecek.

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

`Document` sınıfı, diğer her şeyin—paragraflar, bölümler ve tabii ki çizim nesneleri—giriş noktasıdır.

---

## Adım 3 – Bir Dikdörtgen Şekil Ekleyin

Belge hazır olduğunda bir şekil ekleyebiliriz. Burada basit bir dikdörtgen seçiyoruz, ancak aynı mantık daireler, çizgiler veya özel çokgenler için de çalışır.

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **Neden bir şekil?** Aspose.Words'ta bir `Shape` nesnesi metin, resim tutabilir ya da sadece dekoratif bir öğe olarak işlev görebilir. Bir şekle gölge eklemek, bir resim çerçevesini manipüle etmeye çalışmaktan çok daha kolaydır.

---

## Adım 4 – Gölgeyi Yapılandırın (Şekle Gölge Ekle)

Bu, öğreticinin kalbidir—**şekle gölge ekleme** ve görünümünü ince ayarlama. `ShadowFormat` özelliği size tam kontrol sağlar.

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### Her Özelliğin Ne İş Yaptığı

| Property | Effect | Typical Values |
|----------|--------|----------------|
| **Visible** | Gölgeyi açar/kapatır. | `true` / `false` |
| **Blur** | Gölge kenarlarını yumuşatır. | `0` (sert) to `10` (çok yumuşak) |
| **Distance** | Gölgeyi şekilden uzaklaştırır. | `1`–`5` nokta yaygındır |
| **Angle** | Ofset yönünü kontrol eder. | `0`–`360` derece |
| **Transparency** | Gölgeyi kısmen şeffaf yapar. | `0` (opak) to `1` (görünmez) |

> **Köşe durumu:** `Transparency` değerini `1` olarak ayarlarsanız, gölge tamamen kaybolur—programatik olarak geçiş yapmak için kullanışlıdır.

---

## Adım 5 – Şekli Belgeye Ekleyin

Şimdi şekli belgenin gövdesindeki ilk paragrafa ekliyoruz. Aspose, eğer paragraf yoksa otomatik olarak bir paragraf oluşturur.

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

Belgenizde zaten içerik varsa, şekli `InsertAfter` veya `InsertBefore` kullanarak istediğiniz herhangi bir düğüme ekleyebilirsiniz.

---

## Adım 6 – Belgeyi Kaydedin

Son olarak, dosyayı diske yazın. Herhangi bir desteklenen formatı (`.docx`, `.pdf`, `.odt`, vb.) seçebilirsiniz, ancak bu öğreticide yerel Word formatını kullanacağız.

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Oluşan `ShadowedShape.docx` dosyasını Microsoft Word'de açın ve 30 % şeffaf, 45 derece yumuşak bir gölgeye sahip bir dikdörtgen göreceksiniz—tam olarak yapılandırdığımız gibi.

---

## Tam Çalışan Örnek

Aşağıda, yukarıdaki tüm adımları içeren **tam, kopyala‑yapıştır hazır** program bulunmaktadır. `Program.cs` olarak kaydedin ve `dotnet run` ile çalıştırın.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**Beklenen çıktı:** `ShadowedShape.docx` adlı bir dosya, 45° açıyla hafif, yarı şeffaf bir drop shadow içeren tek bir dikdörtgen içerir.

---

## Varyasyonlar ve İleri Düzey İpuçları

### Gölge Rengini Değiştirme

Varsayılan olarak gölge, şeklin dolgu rengini devralır, ancak özel bir renk ayarlayabilirsiniz:

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Farklı Gölgelere Sahip Birden Çok Şekil

Birden fazla şekle ihtiyacınız varsa, oluşturma ve yapılandırma adımlarını tekrarlayın. Daha sonra referans vermeyi planlıyorsanız, her şekle benzersiz bir ad vermeyi unutmayın.

### Gölge Efektleri Korunarak PDF'ye Dışa Aktarma

Aspose.Words, PDF'ye kaydederken gölge efektlerini korur:

```csharp
doc.Save("ShadowedShape.pdf");
```

### Yaygın Tuzaklar

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| Gölge görünmüyor | `ShadowFormat.Visible` `false` olarak bırakılmış | `true` olarak ayarlayın. |
| Gölge çok sert görünüyor | `Blur` `0` olarak ayarlanmış | `Blur` değerini 3–6'ya artırın. |
| Gölge PDF'de kayboluyor | Eski bir Aspose.Words sürümü (< 22.9) kullanılıyor | En son kütüphaneye yükseltin. |

---

## Sonuç

Aspose.Words kullanarak **şekle gölge ekleme** konusunu, bir belge başlatmaktan bulanıklık, mesafe, açı ve **gölge şeffaflığını uygulamaya** kadar ele aldık. Tam örnek, herhangi bir şekil veya belge düzenine uyarlayabileceğiniz temiz, üretim‑hazır bir yaklaşımı gösteriyor.

**Aspose kullanarak Word belgesi oluşturma** gibi daha karmaşık senaryolar hakkında sorularınız mı var—örneğin gölgelere sahip tablolar veya dinamik veri‑tabanlı şekiller? Aşağıya bir yorum bırakın ya da Aspose.Words görüntü işleme ve paragraf biçimlendirme ile ilgili ilgili öğreticilere göz atın.

Kodlamaktan keyif alın ve Word belgelerinize ekstra görsel bir parlaklık katmanın tadını çıkarın! 

--- 

![şekle gölge ekleme örneği](shadowed_shape.png "şekle gölge ekleme örneği")

{{< layout-end >}}

{{< layout-end >}}