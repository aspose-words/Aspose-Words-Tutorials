---
category: general
date: 2025-12-25
description: C#'ta gölge ekleme, basit bir kod örneği ile. Gölge mesafesini nasıl
  ayarlayacağınızı, rengi nasıl özelleştireceğinizi ve grafiklerinizde derinlik oluşturmayı
  öğrenin.
draft: false
keywords:
- how to add shadow
- how to set shadow distance
language: tr
og_description: C#'ta gölge ekleme adım adım açıklanıyor. Profesyonel görünümlü şekiller
  için gölge mesafesini, rengini ve bulanıklığını ayarlamak üzere kılavuzu izleyin.
og_title: C#'de Gölge Ekleme – Tam Programlama Rehberi
tags:
- C#
- graphics
- Aspose.Words
- shadows
title: C#'de Gölge Nasıl Eklenir – Tam Programlama Rehberi
url: /tr/python/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta Gölge Ekleme – Tam Programlama Rehberi

C#'ta gölge eklemek, grafiklerinizin sayfadan çıkıyormuş gibi görünmesi istediğinizde yaygın bir ihtiyaçtır. Bu öğreticide, bir şeklin gölgesini ayarlamak için tam adımları, gölge mesafesini nasıl ayarlayacağınızı, bulanıklığı nasıl düzenleyeceğinizi ve doğru rengi nasıl seçeceğinizi göstereceğiz.  

Eğer bir düz dikdörtgene bakıp “burası biraz derinlik kazanmalı” diye düşündüyseniz, doğru yerdesiniz. Boş bir belgeden başlayıp bir şekil ekleyecek ve tasarımcı tarafından yerleştirilmiş gibi görünen cilalı bir gölgeyle bitireceğiz. Gereksiz ayrıntı yok, sadece bugün kopyalayıp yapıştırabileceğiniz uygulanabilir bir örnek.

## Öğrenecekleriniz

- Yeni bir belge oluşturma ve bir şekli programlı olarak ekleme.  
- Şeklin gölgesine yumuşak bir bulanıklık uygulama.  
- **Gölge mesafesini ayarlama** yöntemi, böylece gölge doğal bir offset ile görünür.  
- Her türlü arka plan üzerinde çalışan bir gölge rengi seçme.  
- Sonucu PDF (veya ihtiyacınız olan herhangi bir format) olarak kaydetme.  

### Önkoşullar

- .NET 6.0 veya üzeri (kod .NET Core ve .NET Framework ile de çalışır).  
- Aspose.Words for .NET (ücretsiz deneme veya lisanslı sürüm).  
- C# sözdizimi hakkında temel bir anlayış.  

Hepsi bu—ekstra kütüphane, sihir yok. Hadi başlayalım.

![Yumuşak siyah bir gölgeye sahip bir şeklin örneği – gölge ekleme](https://example.com/placeholder-shadow.png "gölge ekleme örneği")

## Adım 1: Projeyi Kurun ve Ad Alanlarını İçe Aktarın

İlk olarak yeni bir konsol uygulaması (veya herhangi bir C# projesi) oluşturun ve Aspose.Words NuGet paketini ekleyin:

```bash
dotnet new console -n ShadowDemo
cd ShadowDemo
dotnet add package Aspose.Words
```

Şimdi `Program.cs` dosyasını açın ve gerekli ad alanlarını kapsam içine alın:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;
```

> **İpucu:** Visual Studio kullanıyorsanız, IDE `Document` yazarken `using` ifadelerini sizin için önerecektir.

## Adım 2: Yeni Bir Belge Oluşturun ve Bir Şekil Ekleyin

Kütüphaneler hazır olduğunda, bir `Document` nesnesi oluşturup ilk sayfaya basit bir dikdörtgen bırakabiliriz.

```csharp
// Step 2: Initialize the document
Document doc = new Document();

// Add a blank page (Aspose.Words creates one automatically)
Section section = doc.FirstSection;

// Insert a rectangle shape – this will be the object we give a shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    // Size the shape (width, height) in points (1 point = 1/72 inch)
    Width = 200,
    Height = 100,
    
    // Position the shape 100 points from the left and 150 from the top
    Left = 100,
    Top = 150,
    
    // Fill the shape with a light gray so the shadow stands out
    FillColor = System.Drawing.Color.LightGray
};

// Add the shape to the document's first page
section.Body.FirstParagraph.AppendChild(rectangle);
```

Neden dikdörtgen? Gölgenin etkisinin dikkat dağıtmadan değerlendirilmesini sağlayan nötr bir kanvasdır. `ShapeType.Rectangle` yerine `Ellipse` ya da `Star` koyabilirsiniz—gölge mantığı aynı kalır.

## Adım 3: Gölge Ekleme – Bulanıklık, Mesafe ve Renk Uygulama

Şimdi öğreticinin kalbi geliyor: **gölge ekleme**. Aspose.Words her şekil üzerinde bir `Shadow` nesnesi sunar; bu nesneyle bulanıklık, mesafe ve rengi ayarlayabilirsiniz.

```csharp
// Step 3: Access the shape's shadow settings
Shadow shadow = rectangle.Shadow;

// 3a) Apply a soft blur – larger values make the shadow fuzzier
shadow.Blur = 5.0;          // 5 points blur gives a subtle, professional look

// 3b) Set the shadow's offset distance – this determines how far the shadow is displaced
shadow.Distance = 3.0;      // 3 points offset is enough to suggest depth without looking detached

// 3c) Choose a shadow color – black works on most backgrounds, but you can experiment
shadow.Color = Color.Black; // Solid black; you could use Color.FromArgb(128, 0, 0, 0) for semi‑transparent

// OPTIONAL: Rotate the shadow to match a light source direction (45 degrees works well)
shadow.Angle = 45.0;
```

Yorum satırına dikkat edin: `// 3b) Set the shadow's offset distance`. Bu satır doğrudan **gölge mesafesini nasıl ayarlayacağınızı** yanıtlar. `shadow.Distance` değerini değiştirerek şekil ile gölge arasındaki görsel boşluğu kontrol eder, belirli bir açıdan gelen ışık kaynağını taklit edersiniz.

### Bu Değerler Neden?

- **Blur = 5.0** – Hafif bir bulanıklık sert bir silueti önlerken hâlâ görünür kalmasını sağlar.  
- **Distance = 3.0** – Gölgeyi şekle yeterince yakın tutar, sanki şekil tarafından atılmış gibi görünür.  
- **Color = Black** – Hem açık hem koyu arka planlarda kontrast garantiler.  

Bu sayıları istediğiniz gibi ayarlayabilirsiniz; API herhangi bir `double` değeri kabul eder.

## Adım 4: Belgeyi Kaydedin ve Sonucu Doğrulayın

Gölge ayarlandıktan sonra dosyayı diske yazmamız yeterli. Aspose.Words birçok formatta çıktı verebilir; PDF paylaşım için yaygın bir tercihtir.

```csharp
// Step 4: Save the document as a PDF (you could also use .docx, .png, etc.)
string outputPath = "ShadowedShape.pdf";
doc.Save(outputPath, SaveFormat.Pdf);

Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
```

`ShadowedShape.pdf` dosyasını açtığınızda, hafif bir sağ‑alt offsetli yumuşak siyah gölgeye sahip gri bir dikdörtgen görmelisiniz. Gölge çok soluk görünüyorsa, `shadow.Blur` ya da `shadow.Distance` değerlerini artırıp yeniden çalıştırın.

## Yaygın Sorular & Kenar Durumları

### Şeffaf bir gölgeye ihtiyacım olursa?

Alfa kanalı 255'ten düşük bir ARGB rengi kullanın:

```csharp
shadow.Color = Color.FromArgb(80, 0, 0, 0); // 80/255 opacity = ~31% transparent
```

### Aynı gölgeyi birden fazla şekle uygulayabilir miyim?

Kesinlikle. Yardımcı bir metod oluşturun:

```csharp
static void ApplyStandardShadow(Shape shape)
{
    shape.Shadow.Blur = 5.0;
    shape.Shadow.Distance = 3.0;
    shape.Shadow.Color = Color.Black;
}
```

Her eklediğiniz şekil için `ApplyStandardShadow(rectangle);` çağrısını yapın.

### Bu, daha eski .NET Framework sürümleriyle çalışır mı?

Evet. Aspose.Words 22.9+ .NET Framework 4.5 ve üzeri sürümleri destekler. Proje dosyanızı buna göre ayarlamanız yeterlidir.

## Tam Çalışan Örnek

Aşağıda `Program.cs` içine kopyalayabileceğiniz, paket yüklü olduğu sürece doğrudan derlenip çalıştırılabilen tam program yer alıyor.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;

namespace ShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialize the document
            Document doc = new Document();
            Section section = doc.FirstSection;

            // Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 100,
                Top = 150,
                FillColor = System.Drawing.Color.LightGray
            };
            section.Body.FirstParagraph.AppendChild(rectangle);

            // Apply shadow – this is the core of "how to add shadow"
            Shadow shadow = rectangle.Shadow;
            shadow.Blur = 5.0;                // Soft blur
            shadow.Distance = 3.0;            // How to set shadow distance
            shadow.Color = Color.Black;       // Classic black shadow
            shadow.Angle = 45.0;              // Light source direction

            // Save as PDF
            string outputPath = "ShadowedShape.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
        }
    }
}
```

Programı çalıştırın:

```bash
dotnet run
```

Projede `ShadowedShape.pdf` dosyasını bulacaksınız. Herhangi bir PDF görüntüleyici ile açıp gölgenin tanımlandığı gibi göründüğünden emin olun.

## Sonuç

C#’ta bir şekle **gölge ekleme** sürecini baştan sona ele aldık ve **gölge mesafesini nasıl ayarlayacağınızı** bulanıklık ve renk ile birlikte gösterdik. Birkaç satır kodla grafiklerinize profesyonel, üç‑boyutlu bir his katabilirsiniz—harici tasarım araçlarına ihtiyaç duymadan.

Temel bilgileri kavradığınıza göre, şu deneyleri yapın:

- Daha soğuk bir hava için gölge rengini hafif bir maviye değiştirin.  
- Rüya gibi, dağınık bir etki için bulanıklığı artırın.  
- Aynı tekniği grafikler, resimler veya metin kutuları üzerine uygulayın.  

Her varyasyon aynı temel kavramları pekiştirir, böylece herhangi bir senaryoda gölgeleri özelleştirmeye alışırsınız.  

Başka sorularınız mı var? Yorum bırakın, iyi kodlamalar!  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}