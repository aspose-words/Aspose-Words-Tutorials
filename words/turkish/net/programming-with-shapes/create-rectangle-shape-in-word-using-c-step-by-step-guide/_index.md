---
category: general
date: 2026-01-03
description: C# ile Word’de dikdörtgen şekil oluşturun ve şekle gölge ekleyin. Word’e
  şekil eklemeyi, şekle gölge eklemeyi ve Word belgelerini programlı olarak oluşturmayı
  öğrenin.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: tr
og_description: C# ile Word’de dikdörtgen şekil oluşturun ve şekle gölge ekleyin.
  Bu kılavuzu izleyerek Word’e şekil ekleyin, gölgeleri yapılandırın ve belgeleri
  programlı olarak oluşturun.
og_title: C# kullanarak Word'de dikdörtgen şekli oluşturma – Tam Kılavuz
tags:
- C#
- Word Automation
- Aspose.Words
title: C# kullanarak Word'de dikdörtgen şekli oluşturma – Adım adım rehber
url: /tr/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Word’te Dikdörtgen Şekil Oluşturma – Tam Kılavuz

Bir Word belgesinde **dikdörtgen şekil** oluşturmanız gerektiğinde nereden başlayacağınızı bilemediniz mi? Yalnız değilsiniz—birçok geliştirici, **şekle gölge eklemek** istediğinde aynı sorunla karşılaşıyor. Bu öğreticide **Word’e şekil ekleme**, hafif bir gölge uygulama ve sonunda **c# generate word document** dosyalarını kullanıcılarınıza sunma adımlarını adım adım göstereceğiz.

Projeyi kurmaktan gölge özelliklerini ayarlamaya kadar her şeyi ele alacağız ve çalıştırmaya hazır bir kod örneğiyle bitireceğiz. Gereksiz ayrıntılar yok, sadece işi halledecek pratik bilgiler.

## Öğrenecekleriniz

- C# ile Aspose.Words (veya Open XML) kullanarak **dikdörtgen şekil** oluşturma  
- Derinlik katmak için **şekle gölge ekleme** için gerekli tam özellikler  
- `DocumentBuilder` ile şeklin nerede konumlandırılacağı  
- Dosyanın Microsoft Word’de doğru şekilde açılması için kaydetme  
- Gerçek dünya senaryoları için ipuçları, tuzaklar ve varyasyonlar  

### Önkoşullar

- .NET 6.0 veya üzeri (kod .NET Core ve .NET Framework’te çalışır)  
- Word dosyalarını manipüle edebilen bir NuGet paketi – **Aspose.Words for .NET** kullanacağız çünkü API’si özlü. Open XML SDK tercih ederseniz, kavramlar aynı, sadece sınıflar farklı.  
- Visual Studio, VS Code veya sevdiğiniz herhangi bir C# IDE  

> **Pro tip:** Bütçeniz kısıtlıysa, Aspose öğrenme amaçlı ücretsiz bir deneme sunar. Test ederken lisans satırını yorum satırı haline getirmeyi unutmayın.

## Adım 1: Word İşleme Kütüphanesini Yükleyin

İlk olarak kütüphaneyi projenize ekleyin. Çözüm klasörünüzde bir terminal açın ve şu komutu çalıştırın:

```bash
dotnet add package Aspose.Words
```

Open XML SDK kullanıyorsanız komut `dotnet add package DocumentFormat.OpenXml` olur. Bu rehberin geri kalan kısmı Aspose.Words varsayımıyla ilerliyor, ancak API çağrılarını değiştirmek oldukça basit.

## Adım 2: Yeni Boş Bir Belge Oluşturun

Kütüphane hazır olduğuna göre, temiz bir `Document` nesnesiyle **dikdörtgen şekil** oluşturabiliriz. Bunu yeni bir tuval gibi düşünün.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder`, düşük seviyeli düğüm ağaçlarına dalmadan içerik eklemenin yüksek seviyeli bir yolunu sunar.

## Adım 3: Dikdörtgen Şekli Ekleyin

Builder elinizdeyken **Word’e şekil ekleyebilir**iz. `InsertShape` metodu şekil tipini ve boyutlarını (genişlik, yükseklik) puan cinsinden alır.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Bu noktada dikdörtgen belgeye eklenir, ancak biraz düz görünür. Bir sonraki adım burada devreye girer.

## Adım 4: Şekle Gölge Ekleyin

Gölge, şekle derinlik hissi verir. `Shadow` nesnesi bulanıklık, mesafe, açı, renk ve şeffaflığı ince ayar yapmamıza olanak tanır. Aşağıda çoğu rapor için iyi çalışan tam bir yapılandırma yer alıyor.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**Bu değerler neden?**  
- `5.0` **BlurRadius**, kenarı pürüzsüz tutar ve bulanık görünmez.  
- `4.0` **Distance**, gölgeyi fark edilebilir bir şekilde kaydırır.  
- `45` **Angle**, üst‑sol köşeden gelen doğal ışığı taklit eder, yaygın bir UI kuralıdır.  
- `0.3` **Transparency**, gölgenin şeklin dolgusunu bastırmasını önler.

Daha dramatik bir etki isterseniz `BlurRadius` değerini artırın ve `Transparency` değerini düşürün. Neredeyse görünmez bir kaldırma için ise tam tersini yapın.

## Adım 5: Belgeyi Kaydedin

Son olarak dosyayı diske yazın. `Save` metodu dosya uzantısından formatı algılar, bu yüzden `.docx` modern Word formatını verir.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

`ShadowRectangle.docx` dosyasını Microsoft Word’de açın; yumuşak bir gölgeye sahip net bir dikdörtgen göreceksiniz—tam da “**şekle nasıl eklenir**” sorusuna profesyonel bir yanıt.

![Create rectangle shape with shadow in Word](placeholder-image.png "Create rectangle shape with shadow in Word")

*Görsel alt metni: Word’te gölgeli dikdörtgen şekil oluşturma*

## Tam Çalışan Örnek

Hepsini bir araya getirdiğimizde, çalıştırmaya hazır tam program aşağıdadır. Konsol uygulamasına kopyalayıp **F5** tuşuna basın.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Beklenen Sonuç

- Oluşturulan `ShadowRectangle.docx` dosyası, imleç konumunda **bir dikdörtgen şekil** içerir.  
- Dikdörtgen, **%30 şeffaf siyah bir gölge** ile 45° açıda hafifçe kaydırılmış şekilde gösterilir.  
- Başka bir içerik eklenmez, böylece dosya hafif ve büyük raporlara gömülmesi kolay olur.

## Yaygın Sorular & Kenar Durumları

### Farklı bir şekle ihtiyacım olursa?

`ShapeType.Rectangle` ifadesini istediğiniz başka bir `ShapeType` enum değeriyle (ör. `Ellipse`, `Triangle`) değiştirin. Gölge API’si aynı şekilde çalışır, yapılandırmayı yeniden kullanabilirsiniz.

### Dolgu rengini nasıl değiştiririm?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Şekli belirli bir paragrafta ekleyebilir miyim?

Evet. `InsertShape` çağrısından önce `DocumentBuilder`’ı hedef paragrafına `builder.MoveToParagraph(index)` ile taşıyın. Böylece şekil tam istediğiniz yerde görünür.

### Eski Word formatları (.doc) hakkında ne söyleyebilirsiniz?

Sadece uzantıyı değiştirin:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

Gölge özelliği Word 2003 ve sonrası sürümlerde desteklenir, bu yüzden etki hâlâ görülür.

### Aspose yerine Open XML SDK kullanmak?

Adımlar aynı kalır: bir `WordprocessingDocument` oluşturun, bir `Drawing` öğesi ekleyin, `<a:shadow>` özelliklerini ayarlayın. XML daha ayrıntılıdır, ancak aynı kavramlar (boyut, bulanıklık, mesafe, açı) geçerlidir.

## Tuzaklardan Kaçınma İpuçları

- Ücretli bir Aspose sürümü kullanıyorsanız **lisansı eklemeyi unutmayın**; aksi takdirde filigran alırsınız.  
- **Birimler puandır**, piksel değil. Ortalama bir ekran pikseli ≈ 0.75 pt olduğundan boyutları buna göre ayarlayın.  
- Şeklin `WrapType` özelliği `Inline` ise **gölge özellikleri göz ardı edilir**. Yüzen şekillerde gölgeyi göstermek için `WrapType = WrapType.Square` kullanın.  
- **Ağ paylaşımına kaydetmek** izin sorunlarına yol açabilir; yolu önceden test edin.

## Sonuç

Artık C# kullanarak bir Word belgesinde **dikdörtgen şekil** oluşturmayı, **şekle gölge eklemeyi** ve kutudan çıktığı gibi şık görünen **c# generate word document** dosyaları üretmeyi biliyorsunuz. Temel adımlar—kütüphaneyi kurmak, `Document` nesnesini oluşturmak, şekli eklemek, gölgeyi yapılandırmak ve kaydetmek—akılda kalıcı ve diğer şekiller, renkler ya da dinamik veriler için kolayca uyarlanabilir.

Sırada ne var? Birden fazla şekil katmanlamayı, resim eklemeyi ya da tablolar ve grafiklerle tam bir rapor üretmeyi deneyin. Ayrıca veri değerlerine göre gölge yoğunluğunu değiştiren koşullu biçimlendirmeler keşfedebilirsiniz; böylece belgeleriniz sadece işlevsel değil, aynı zamanda görsel olarak da çekici olur.

Denemekten çekinmeyin, bir sorunla karşılaşırsanız aşağıya yorum bırakın. İyi kodlamalar, ve Word belgeleriniz her zaman mükemmel bir drop shadow’a sahip olsun!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}