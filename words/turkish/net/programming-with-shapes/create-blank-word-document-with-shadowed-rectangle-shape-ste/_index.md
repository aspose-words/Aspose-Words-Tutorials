---
category: general
date: 2026-01-08
description: Boş bir Word belgesi oluşturun ve bir dikdörtgen şekline gölge eklemeyi
  öğrenin. Şekil Word dosyalarını ekleyin ve Aspose.Words kullanarak C#'ta şekil gölgesi
  ekleyin.
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: tr
og_description: Boş bir Word belgesi oluşturun ve C# kullanarak bir dikdörtgen şekline
  gölge eklemeyi görün. Tam kod, açıklamalar ve ipuçları.
og_title: Boş Word Belgesi Oluştur – Gölgelendirilmiş Dikdörtgen Şekli Ekle
tags:
- Aspose.Words
- C#
- Document Automation
title: Gölgelendirilmiş Dikdörtgen Şekilli Boş Word Belgesi Oluşturma – Adım Adım
  Rehber
url: /tr/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş Word Belgesi Oluşturma ve Gölgelendirilmiş Dikdörtgen Şekli – Tam Kılavuz

Programatik olarak **boş Word** dosyaları oluşturup üzerine güzel bir gölgelendirilmiş dikdörtgen eklemeniz gerektiğinde hiç zorlandınız mı? Tek başınıza değilsiniz. Birçok geliştirici, şekil eklemenin ve efekt uygulamanın metin yazmak kadar basit olmadığını fark ettiğinde bir engelle karşılaşıyor.  

Bu rehberde, boş bir `.docx` dosyası oluşturma sürecinden **bir dikdörtgen şekline gölge ekleme** yöntemine ve sonunda **şekil ekleme** içeriğini şık bir **gölge ekleme** efektiyle belgeye yerleştirmeye kadar tüm adımları adım adım inceleyeceğiz. Sonunda, en yeni Aspose.Words for .NET ile çalışan, kullanıma hazır bir kod parçacığına sahip olacaksınız.

---

## Gereksinimler

- **Aspose.Words for .NET** (v24.10 veya daha yeni) – aşağıdaki tüm işlemleri sağlayan kütüphane.  
- Bir .NET geliştirme ortamı (Visual Studio, Rider veya `dotnet` CLI).  
- Temel C# bilgisi – “Hello World” yazabiliyorsanız yeterli.  

Ek bir NuGet paketi gerekmez; her şey `Aspose.Words` ve `System.Drawing` içinde bulunur.

---

## Adım 1: Boş Bir Word Belgesi Oluşturma

İlk yapmanız gereken, boş bir `Document` nesnesi oluşturmak. Bunu, yeni bir Word dosyasını manuel olarak açmaya benzetebilirsiniz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*Neden önemli:*  
`Document` örneği, bütün Word dosyasını temsil eder. Boş bir belgeyle başlamak, daha sonra ekleyeceğiniz paragraf, şekil vb. tüm öğeler üzerinde tam kontrol sağlar.

---

## Adım 2: Dikdörtgen Şekli Tanımlama (Rectangle Shape Word)

Şimdi üzerinde çalışacağımız bir şekle ihtiyacımız var. Dikdörtgen, en basit geometrik şekildir ve afiş, yer tutucu veya basit UI mock‑up’ları için idealdir.

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*Neden önemli:*  
`Width` ve `Height` ayarları, şeklin görsel alanını kontrol etmenizi sağlar. `ShapeType.Rectangle` Aspose’a klasik bir kutu çizmeyi söyler – **add shape shadow** işlemini göstermek için mükemmeldir.

---

## Adım 3: Şekle Gölge Uygulama (How to Add Shadow)

Gölge, derinlik katar ve düz bir dikdörtgeni fiziksel bir nesne gibi hissettirir. Aspose.Words, renk, mesafe, bulanıklık ve şeffaflık gibi ayarları yapabileceğiniz bir `Shadow` özelliği sunar.

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*Neden önemli:*  
Her bir özellik görsel ipucunu etkiler:

- **Enabled** – bu etkinleştirilmezse diğer ayarlar göz ardı edilir.  
- **Color** – belgenizin temasıyla uyumlu bir renk seçin.  
- **Distance** – yüksek değerler gölgeyi daha uzağa iter.  
- **BlurRadius** – büyük sayılar gölgeyi daha yumuşak yapar.  
- **Transparency** – opaklığı ayarlayarak gölgeyi ince ayarlayın.

Denemeler yapın; dramatik bir etki için `Distance` değerini `10` yapıp `Transparency`ı `0.5` olarak ayarlayabilirsiniz.

---

## Adım 4: Şekli Belgeye Ekleme (Insert Shape Word)

Dikdörtgen hazır, şimdi onu bir yere koymamız gerekiyor. En basit yer, belgenin gövdesindeki ilk paragraftır.

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*Neden önemli:*  
`FirstSection.Body.FirstParagraph` yeni bir `Document` içinde her zaman bulunur. Şekli buraya ekleyerek, şeklin dosyanın en üstünde görünmesini sağlarsınız – başlıklar veya afişler için kullanışlıdır.

Şekli başka bir konuma eklemek isterseniz, belirli bir `Paragraph` veya `Run` bulup `InsertAfter` ya da `InsertBefore` metodlarını kullanabilirsiniz.

---

## Adım 5: Word Dosyasını Kaydetme

Son adım, bellek içindeki belgeyi diske kalıcı olarak yazmaktır. Yazma izniniz olan bir klasör seçin ve dosyaya anlamlı bir ad verin.

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*Neden önemli:*  
`Save` çağrısı, tam uyumlu bir `.docx` dosyası oluşturur. Microsoft Word, LibreOffice veya herhangi bir görüntüleyicide açtığınızda, yumuşak gri bir gölgeye sahip bir dikdörtgen göreceksiniz – tam da ayarladığımız gibi.

---

## Tam Çalışan Örnek

Aşağıda, bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz tam program yer alıyor. Tüm `using` yönergeleri, şekil oluşturma, gölge yapılandırması, ekleme ve kaydetme adımları içerilir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Define a rectangle shape (rectangle shape word)
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
        {
            Width  = 200,
            Height = 100
        };

        // 3️⃣ How to add shadow – configure the shadow effect
        rectangleShape.Shadow.Enabled      = true;
        rectangleShape.Shadow.Color        = Color.Gray;
        rectangleShape.Shadow.Distance    = 5.0;
        rectangleShape.Shadow.BlurRadius  = 3.0;
        rectangleShape.Shadow.Transparency = 0.2;

        // 4️⃣ Insert shape word into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 5️⃣ Save the file (add shape shadow persisted)
        string outputPath = @"C:\Temp\ShadowedRectangle.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Beklenen çıktı:**  
`ShadowedRectangle.docx` dosyasını açtığınızda, sayfanın üst kısmının ortasında hafif gri bir dikdörtgen ve 5 pt kaydırılmış ince bir gölge göreceksiniz. Başka bir metin yok, sadece şekil – kodun ürettiği tam sonuç.

---

## Sık Sorulan Sorular & Özel Durumlar

### Farklı bir şekle ihtiyacım olursa ne yapmalıyım?

`ShapeType.Rectangle` ifadesini, istediğiniz başka bir `ShapeType` enum değeri (`Ellipse`, `Triangle`, `Star` vb.) ile değiştirin. Gölge özellikleri aynı şekilde çalışır.

### Birden fazla gölge ekleyebilir miyim?

Aspose.Words, bir şekil için yalnızca tek bir gölge destekler. Katmanlı efektler istiyorsanız, farklı gölge ayarlarına sahip iki üst üste gelen şekil oluşturun.

### .NET Core’da bu nasıl çalışır?

Aynı API, .NET 6/7/8 üzerinde de çalışır. **Aspose.Words.NETCore** paketini (veya artık çapraz platform olan standart paketi) referans ettiğinizden emin olun.

### Linux’da `System.Drawing` hâlâ destekleniyor mu?

`System.Drawing.Common`, .NET 6’dan itibaren sadece Windows’da çalışır. Çapraz platform projeler için `Aspose.Drawing` (ayrı bir NuGet) kullanın veya renkleri doğrudan `Aspose.Words` üzerinden tanımlayın.

### DPI ölçeklemesi nasıl yapılır?

Şekil boyutları puan cinsindendir (1 pt = 1/72 inç). Belirli bir DPI için piksel‑tam boyut istiyorsanız, puanı `pixels * 72 / dpi` formülüyle hesaplayın.

---

## Pro İpuçları & Dikkat Edilmesi Gerekenler

- **Pro ipucu:** Şeklin metin akışıyla birlikte hareket etmesini istiyorsanız `rectangleShape.WrapType = WrapType.Inline;` ayarlayın.  
- **Dikkat:** Gölgeyi etkinleştirmeyi (`Enabled = true`) unutmayın. Diğer ayarlar sessizce yok sayılır.  
- **Performans notu:** Çok sayıda şekli sık bir döngüde eklemek yavaş olabilir. Şekilleri tek bir `Section` içinde toplup, sonunda bir kez `document.UpdatePageLayout()` çağırın.  
- **Versiyon kontrolü:** Gölge API’si Aspose.Words 20.2’de tanıtıldı. Daha eski bir sürüm kullanıyorsanız, eksik özelliklerden kaçınmak için yükseltin.

---

## Sonuç

**Boş bir Word belgesi** oluşturduk, **dikdörtgen şekli word** ekledik, **gölge ekleme** yöntemini öğrendik ve sonunda **şekil ekleme** içeriğini şık bir **gölge ekleme** efektiyle belgeye yerleştirdik — tüm bunlar Aspose.Words for .NET ile.  

Kod parçacığı tamamen çalışır, Windows ve çapraz‑platform .NET üzerinde sorunsuz çalışır ve diğer şekiller, renkler veya hatta animasyonlu GIF’ler eklemek için genişletilebilir. Sonraki adım olarak, dikdörtgenin içine metin eklemeyi, degrade doldurmaları uygulamayı veya birden çok stilize şekil içeren bir rapor üretmeyi keşfedebilirsiniz.

Daha fazla fikriniz mi var? Gri gölgeyi mavi bir gölgeyle değiştirin, daha rüya gibi bir görünüm için bulanıklığı artırın veya birkaç şekli birleştirerek özel bir logo oluşturun. İmkânlar sınırsız ve artık bunu yapmanız için gerekli yapı taşlarına sahipsiniz.

Kodlamanın tadını çıkarın, belgeleriniz her zaman keskin (ve doğru miktarda gölge) görünsün!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}