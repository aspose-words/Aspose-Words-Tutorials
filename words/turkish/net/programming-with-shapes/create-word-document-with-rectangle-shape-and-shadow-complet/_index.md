---
category: general
date: 2026-01-02
description: Aspose.Words kullanarak bir dikdörtgen şekilli Word belgesi oluşturun,
  şeklin dolgu rengini ayarlayın ve docx dosyasını kaydedin. Dakikalar içinde gölgelikli
  dikdörtgen oluşturmayı öğrenin.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: tr
og_description: Özel bir dikdörtgenle Word belgesi oluşturun, dolgu rengini ayarlayın,
  gölge ekleyin ve DOCX olarak kaydedin. Tam kod ve açıklamalar.
og_title: Dikdörtgen Şekilli Word Belgesi Oluştur – Adım Adım
tags:
- Aspose.Words
- C#
- Document Generation
title: Dikdörtgen Şekil ve Gölge ile Word Belgesi Oluşturma – Tam Rehber
url: /tr/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dikdörtgen Şekil ve Gölge ile Word Belgesi Oluşturma – Tam Kılavuz

Hiç **Word belgesi oluşturmanın** içinde şık bir dikdörtgen nasıl eklenir diye merak ettiniz mi? Belki bir logo için yer tutucu, renkli bir başlık ya da raporda sadece görsel bir ipucu ihtiyacınız var. Bu öğreticide **dikdörtgen şekil ekleyecek**, ona dolgu rengi verecek, hafif bir gölge uygulayacak ve sonunda **docx dosyasını kaydedeceğiz** – hepsi Aspose.Words for .NET ile.

Hazır‑çalıştır C# kod parçacığı, her satırın net açıklaması ve kendi projelerinizde yeniden kullanabileceğiniz bir dizi ipucu elde edeceksiniz. Gereksiz şey yok, sadece kopyala‑yapıştır yapabileceğiniz pratik bir çözüm.

## Gereksinimler

- .NET 6 veya üzeri (kod .NET Framework'te de çalışır)  
- Visual Studio 2022 (veya tercih ettiğiniz herhangi bir editör)  
- **Aspose.Words** NuGet paketi (`Install-Package Aspose.Words`)  

Eğer bunlara sahipseniz, harika – hemen başlayalım.

## 1. Adım – Yeni Bir Belge Başlatma (Word belgesi nasıl oluşturulur)

İlk yapmanız gereken şey, bellekte **Word belgesi oluşturmak**. Bunu, daha sonra dikdörtgeninizi çizeceğiniz boş bir tuval açmak gibi düşünün.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Neden önemli:** `Document` tüm DOCX dosyasını temsil eder, `DocumentBuilder` ise metin, tablo, resim ve şekil eklemenizi sağlayan, alt düğüm ağacını manuel olarak yönetmenize gerek kalmayan kullanışlı bir yardımcıdır.

## 2. Adım – Dikdörtgen Şekil Ekleme (Dikdörtgen şekil ekle)

Şimdi belgeye **dikdörtgen şekil ekleyeceğiz**. `InsertShape` yöntemi şekil tipini ve boyutlarını puan cinsinden alır (1 point = 1/72 inç).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Pro ipucu:** Farklı bir geometri (elips, üçgen vb.) oluşturmanız gerektiğinde, sadece `ShapeType.Rectangle` değerini istediğiniz enum değeriyle değiştirin.

## 3. Adım – Gölgeyi Yapılandırma (Şekil dolgu rengi ve gölge ayarla)

Gölge, düz bir şekli daha üç boyutlu hissettirebilir. Burada gölgeyi etkinleştirip görünümünü ayarlıyoruz.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **Bu değerler neden?** Makul bir bulanıklık yarıçapı ve 5‑puan mesafe, gölgenin şekli bastırmasını önler, 45° ise ışık kaynağının sol üstten gelmesini taklit eder – yaygın bir UI kuralıdır.

## 4. Adım – Belgeyi Kaydetme (docx dosyasını kaydet)

Son olarak, **docx dosyasını** diske **kaydediyoruz**. Ortamınıza uygun olacak şekilde yolu ayarlayın.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

`ShadowDemo.docx` dosyasını Word'de açtığınızda, aşağıdaki ekran görüntüsü gibi hafif mavi bir dikdörtgen ve yumuşak gri bir gölge görmelisiniz.

![Dikdörtgen şekil ve gölge ile Word Belgesi Oluşturma](https://example.com/images/rectangle-shadow.png "Dikdörtgen şekil ve gölge ile Word Belgesi Oluşturma")

*Görsel alt metni:* **Word Belgesi Oluşturma** gösteren bir dikdörtgen şekil ve gölge.

## Tam, Çalıştırılabilir Örnek (Dikdörtgen oluşturma ve kaydetme)

Her şeyi bir araya getirerek, bir konsol uygulamasına kopyalayabileceğiniz tam program aşağıdadır:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### Beklenen Sonuç

- Hedef klasörde **ShadowDemo.docx** adlı bir dosya oluşur.  
- Microsoft Word'de açtığınızda “Shadow Demo” metni ve ardından hafif mavi bir dikdörtgen gösterilir.  
- Dikdörtgen, 45° açıyla yumuşak gri bir gölge atar ve hafif bir 3‑B hissi verir.

## Yaygın Sorular ve Kenar Durumları

### Farklı bir boyuta ihtiyacım olursa?

`InsertShape` içindeki `200, 100` argümanlarını değiştirin. Bu sayılar genişlik ve yükseklik değerlerini puan cinsindendir. Kare için aynı değerleri kullanın.

### Gölgeyi daha belirgin yapabilir miyim?

`BlurRadius` değerini artırarak daha yumuşak bir kenar, `Distance` değerini yükselterek daha büyük bir kaydırma, ya da `Transparency` değerini (ör. `0.1`) düşürerek gölgeyi daha koyu yapabilirsiniz.

### Dikdörtgenin etrafına kenarlık eklemek nasıl yapılır?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### Bu, Aspose.Words'ın eski sürümleriyle uyumlu mu?

Evet. `ShadowFormat` sınıfı 2020'nin erken sürümlerinden beri mevcuttur. Çok eski bir sürüm kullanıyorsanız, tüm özelliklere erişmek için yükseltmeniz gerekebilir.

## İpuçları ve Tuzaklar

- **Pro ipucu:** İşiniz bittiğinde büyük belgeleri (`doc.Dispose()`) her zaman serbest bırakın, özellikle web uygulamalarında, yerel kaynakları serbest bırakmak için.  
- **Dikkat:** Uygun izinler olmadan göreli bir yol kullanmak `UnauthorizedAccessException` hatasına yol açabilir. Mutlak yolları tercih edin veya uygulama havuzunun yazma izni olduğundan emin olun.  
- **Unutmayın:** `FillColor` özelliği herhangi bir `System.Drawing.Color` değerini kabul eder. Özel bir pastel ton için `Color.FromArgb(255, 173, 216, 230)` kullanabilirsiniz.

## Sonraki Adımlar

Artık **Word belgesi oluşturmayı**, **dikdörtgen şekil eklemeyi**, **şekil dolgu rengini ayarlamayı** ve **docx dosyasını kaydetmeyi** bildiğinize göre, daha fazla deney yapabilirsiniz:

- Birden fazla şekil ekleyip `RelativeHorizontalPosition` ve `RelativeVerticalPosition` ile konumlandırın.  
- Dikdörtgeni `Shape.TextBox` kullanarak başlıklar için metinle birleştirin.  
- Aynı belgeyi dağıtım için PDF olarak dışa aktarın (`doc.Save("output.pdf")`).

Daha gelişmiş grafikler hakkında meraklıysanız, Aspose.Words'ın **WordArt**, **grafikler** ve **satır içi görüntüler** desteğine göz atın. Hepsi aynı desen izler: bir düğüm oluşturun, özelliklerini yapılandırın ve kaydedin.

---

### TL;DR

- `Document` ve `DocumentBuilder` kullanarak **Word belgesi oluşturun**.  
- `InsertShape(ShapeType.Rectangle, …)` çağırarak **dikdörtgen şekil ekleyin**.  
- İstediğiniz arka plan için `FillColor` ayarlayın.  
- `ShadowFormat`'ı etkinleştirip özelliklerini ayarlayarak şık bir görünüm elde edin.  
- `document.Save("yourPath.docx")` ile **docx dosyasını kaydedin**.

Kodlamaktan keyif alın ve Word dosyalarınızı biraz daha şık hale getirin!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}