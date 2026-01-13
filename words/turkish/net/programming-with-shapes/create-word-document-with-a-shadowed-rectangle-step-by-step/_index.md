---
category: general
date: 2026-01-13
description: Aspose.Words kullanarak Word belgesi oluşturun ve C#'ta dikdörtgen şekil
  eklemeyi, gölge eklemeyi ve şekil gölgesi eklemeyi öğrenin. Tam örnek dahil.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: tr
og_description: Aspose.Words ile Word belgesi oluşturun, dikdörtgen şekli eklemeyi
  ve gölge eklemeyi görün. Tam C# örneğini izleyin.
og_title: Gölgelendirilmiş Dikdörtgenli Word Belgesi Oluşturma – Tam Kılavuz
tags:
- Aspose.Words
- C#
- Document Automation
title: Gölgeli Dikdörtgenle Word Belgesi Oluşturma – Adım Adım Rehber
url: /tr/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gölgelendirilmiş Dikdörtgenli Word Belgesi Oluşturma – Adım Adım Kılavuz

Hiç **create word document** içeren güzel gölgeli bir dikdörtgen oluşturmanız gerektiğinde, nereden başlayacağınızı bilemediniz mi? Tek başınıza değilsiniz—birçok geliştirici Aspose.Words ile ilk kez çalıştıklarında aynı duvara çarpar.  

Bu öğreticide, programlı olarak **create word document** oluşturmak, **insert rectangle shape** eklemek ve şeklin gerçekten öne çıkması için **how to add shadow** göstermeyi adım adım anlatacağız. Sonunda, herhangi bir .NET projesine ekleyebileceğiniz, çalıştırmaya hazır bir C# kod parçacığına sahip olacaksınız.

## Öğrenecekleriniz

- Bir Word dosyasına (dikdörtgen) **how to insert shape** için tam kod.  
- **add shape shadow** ayarlamanız gereken özellikler ve görünüm kontrolü.  
- Sonucu kaydetme ve gölgenin görünür olduğunu doğrulama.  
- Daha sonra baş ağrısı yaşamamanız için birkaç pratik ipucu ve kenar‑durum notu.

Harici bir dokümantasyona gerek yok—her şey burada.

## Önkoşullar

İlk olarak, aşağıdakilere sahip olduğunuzdan emin olun:

1. **.NET 6.0** (veya herhangi bir yeni .NET sürümü) yüklü.  
2. Aspose.Words for .NET için bir **license**, ya da test için ücretsiz değerlendirme modunu kullanabilirsiniz.  
3. Bir geliştirme ortamı—Visual Studio 2022 harika çalışır, ancak C# derleyebilen herhangi bir editör yeterlidir.

Hepsi bu. `Aspose.Words` dışındaki ekstra NuGet paketlerine gerek yok.

## Adım 1 – Projeyi Kurma ve Aspose.Words Referansını Ekleme

İlk olarak, yeni bir konsol uygulaması oluşturun ve Aspose.Words paketini ekleyin:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Ücretsiz deneme sürümünü kullanıyorsanız, lisans dosyanızla `License.SetLicense` çağırmayı unutmayın; aksi takdirde kütüphane bir filigran ekleyecektir.

## Adım 2 – Document Builder'ı Başlatma

Şimdi gerçek **create word document** sürecine başlayacağız. `Document` sınıfı bize boş bir tuval sağlar ve `DocumentBuilder` üzerine çizmemizi sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Neden bir builder'a ihtiyacımız var? Builder, düşük seviyeli OpenXML ayrıntılarını soyutlar, böylece dosyanın nasıl yapılandırıldığından ziyade *ne* istediğinize odaklanabilirsiniz. Bu, **how to insert shape**'i hızlıca yapmanın özüdür.

## Adım 3 – Dikdörtgen Şekli Ekleme

İşte **insert rectangle shape**'i gerçekten eklediğimiz yer. Dikdörtgen 150 × 100 puan (yaklaşık 2 in × 1.3 in) olacaktır.

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

`InsertShape` metodu bir `Shape` nesnesi döndürür; bunu daha da özelleştirebiliriz. Şu anda dikdörtgen sadece katı beyaz bir kutu—henüz gölge yok.

## Adım 4 – Gölge Ekleme (Add Shape Shadow)

Gölge eklemek, hangi özelliklere dokunmanız gerektiğini bildiğinizde şaşırtıcı derecede basittir. `ShadowFormat` nesnesi görünürlük, renk, bulanıklık, offset ve boyutu kontrol eder.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Bu blok, **how to add shadow** sorusunu sade bir dille yanıtlar: etkinleştirin, bir renk seçin, şeffaflığı, offset'i, bulanıklığı ve boyutu ayarlayın. Bu sayılarla deney yaparak yoğun bir gölge ya da çok ince bir gölge elde edebilirsiniz.

### Yaygın Varyasyonlar

- **Different colours:** Klasik bir gölge için `Color.Black`, stilize bir etki için `Color.BlueViolet` kullanın.  
- **Zero blur:** Keskin, net bir kenar için `BlurRadius = 0` ayarlayın.  
- **Larger offsets:** Gölgeyi şekilden daha uzağa itmek için `OffsetX`/`OffsetY` değerlerini artırın.

## Adım 5 – Belgeyi Kaydetme ve Doğrulama

Son olarak, belgeyi diske yazın. Dosya, modern bir Word işlemcisiyle açılabilen standart bir `.docx` olacaktır.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Ortaya çıkan *ShadowRectangle.docx* dosyasını Microsoft Word'de açın. Alt‑sağ köşeye hafif gri bir gölgeyle kaydırılmış bir dikdörtgen görmelisiniz—tam olarak kodun belirttiği gibi.

> **Beklenen çıktı:** 150 × 100 puanlık bir dikdörtgen, %30 şeffaf gri gölge, 5 pt offset, 4 pt bulanıklık ve şeklin %75 boyutunda bir tek sayfalık Word dosyası.

## Tam Çalışan Örnek

Her şeyi bir araya getirerek, işte tam, çalıştırmaya hazır program:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Programı (`dotnet run`) çalıştırın ve güzel gölgeli bir dikdörtgen içeren yeni bir Word dosyanız olacak—raporlar, sertifikalar veya ihtiyacınız olan herhangi bir görsel ipucu için mükemmel.

## Sıkça Sorulan Sorular (SSS)

**S: Diğer şekilleri (elips, yıldız) ekleyebilir ve aynı gölge kodunu kullanabilir miyim?**  
C: Kesinlikle. `InsertShape` metodu herhangi bir `ShapeType` enum değerini kabul eder. Bir `Shape` örneğine sahip olduğunuzda, `ShadowFormat` özellikleri aynı şekilde çalışır, bu yüzden **how to add shadow** şekle bağımlı değildir.

**S: Şeklin her iki tarafında da gölge ihtiyacım olursa?**  
C: Aspose.Words bir şekil başına yalnızca tek bir gölgeyi destekler. Çift taraflı bir etkiyi taklit etmek için şekli çoğaltın, her kopyayı farklı şekilde offsetleyin ve birinin `ShadowFormat.Visible` değerini `false` yapıp diğerinin gölgesini görünür tutun.

**S: Bu .NET Framework 4.8'de çalışır mı?**  
C: Evet. API sürüm bağımsızdır; hedef çerçeveniz için uygun Aspose.Words DLL'yi referans edin.

## İpuçları ve Tuzaklar

- **Visible = true` ayarlamayı unutmayın**—aksi takdirde gölge özellikleri yok sayılır.  
- **Şeffaflık değerleri 0.0 (opak) ile 1.0 (tamamen şeffaf) arasında değişir.** Yaygın bir hata `30` yerine `0.3` kullanmaktır.  
- **Salt okunur bir klasöre kaydetmek bir istisna fırlatır.** Çıktı dizininin yazılabilir olduğundan emin olun.

## Sonraki Adımlar

Şimdi **how to insert shape**, **add shape shadow** ve Aspose.Words ile **create word document** nasıl yapılacağını bildiğinize göre, aşağıdakileri keşfetmek isteyebilirsiniz:

- **text inside the rectangle** eklemek için şekli eklemeden önce `builder.InsertParagraph()` kullanın.  
- **gradient fills** veya **patterned borders** uygulayarak daha zengin görsel stil elde edin.  
- Dinamik raporlar oluşturmak için her biri farklı gölgeli bir şekle sahip birden fazla sayfa üretimini otomatikleştirin.

Deney yapmaktan çekinmeyin—gölgenin rengini, bulanıklığını veya boyutunu değiştirerek belgenizin görünümünü büyük ölçüde değiştirebilirsiniz.

---

*Bunu üretime koymaya hazır mısınız? Kodu alın, parametreleri ayarlayın ve Word dosyalarınızın saniyeler içinde profesyonel bir parlaklık kazanmasını izleyin.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}