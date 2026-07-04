---
category: general
date: 2026-05-01
description: C# kullanarak Aspose.Words'ta bir şeklin gölgesini nasıl hareket ettireceğinizi
  öğrenin. Şekle gölge eklemeyi, bulanıklığı değiştirmeyi, şeffaflığı ayarlamayı ve
  gölgeyi dakikalar içinde döndürmeyi keşfedin.
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: tr
og_description: C# kullanarak Aspose.Words'te bir şeklin gölgesini nasıl hareket ettireceğinizi
  öğrenin. Bu öğreticide, şekle gölge ekleme, bulanıklığı değiştirme, şeffaflığı ayarlama
  ve gölgeyi döndürme konuları gösterilmektedir.
og_title: Aspose.Words'ta Gölgeyi Nasıl Taşırsınız – Tam C# Rehberi
tags:
- Aspose.Words
- C#
- Document Automation
title: Aspose.Words'te Gölgeyi Nasıl Taşırsınız – Tam C# Kılavuzu
url: /tr/net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words'ta Gölge Nasıl Taşınır – Tam C# Kılavuzu

Hiç **gölgeyi nasıl taşıyacağınızı** bir Word belgesindeki şekil üzerinde, Word'ü manuel olarak açmadan merak ettiniz mi? Günlük işimde, şeklin gölgesini programatik olarak ayarlamam gerektiğinde sık sık karşılaştım—ister şık bir rapor, ister dinamik bir şablon olsun. İyi haber? Aspose.Words ile bunu birkaç satırda yapabilirsiniz ve aynı anda **şekle gölge ekleme**, **bulanıklığı nasıl değiştireceğinizi**, **saydamlığı nasıl ayarlayacağınızı** ve **gölgeyi nasıl döndüreceğinizi** de öğreneceksiniz.

Bu öğreticide gerçek bir senaryoyu adım adım inceleyeceğiz: zaten bir şekil içeren mevcut bir DOCX dosyasını yüklemek, gölgenin konumunu, yumuşaklığını, opaklığını ve yönünü ayarlamak ve sonunda sonucu kaydetmek. Sonunda, herhangi bir .NET projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız ve her özelliğin neden önemli olduğunu anlayacaksınız.

## Önkoşullar – Başlamadan Önce Neye İhtiyacınız Var

- **Aspose.Words for .NET** (sürüm 23.12 veya daha yeni). NuGet üzerinden `Install-Package Aspose.Words` komutuyla edinebilirsiniz.
- .NET 6+ geliştirme ortamı (Visual Studio, VS Code, Rider—ne tercih ederseniz).
- En az bir şekil (dikdörtgen, daire veya resim) içeren bir giriş Word dosyası (`input.docx`).
- C# sözdizimine temel aşinalık—özel bir şey gerekmez.

Eğer bunlardan birine sahip değilseniz, bir an durup kütüphaneyi kurun; rehberin geri kalanı paketin zaten referans alındığını varsayar.

## Adım 1: Belgeyi Yükleyin ve Hedef Şekli Alın – **Gölgeyi Nasıl Taşıyacağınız** Burada Başlıyor

İlk yaptığımız şey, kaynak belgeyi yüklemek ve değiştirmek istediğimiz şekli bulmaktır. Aspose.Words, her nesneyi (paragraflar, tablolar, şekiller) bir ağaçta düğüm olarak ele alır, bu yüzden doğrudan sorgulayabiliriz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **Bu neden önemli:** Belgeyi bir kez yükleyip aynı `Document` örneğini yeniden kullanmak verimlidir. `GetChild` çağrısı, indeks aralık dışındaysa `null` döndürdüğü için eksik şekilleri sorunsuz bir şekilde ele almamıza olanak tanır.

## Adım 2: Bulanıklık Yarıçapını Ayarlayın – **Bulanıklığı Nasıl Değiştireceğinizi** Öğrenin

Yumuşak bir gölge profesyonel görünürken, sert bir kenar ucuz durabilir. `BlurRadius` özelliği, yumuşaklığı puan cinsinden kontrol eder (1 pt ≈ 1/72 inç). Hadi bunu 8 pt'ye çıkaralım.

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **Pro ipucu:** Varsayılan bulanıklık 0.5 pt'dir. 5 pt üzerindeki değerler genellikle fark edilir, ancak çok büyük yapmaktan kaçının—şekil sayfadan kopmuş gibi görünebilir.

## Adım 3: Saydamlığı Ayarlayın – **Saydamlığı Nasıl Ayarlayacağınız** Sorunun Cevabı

Saydamlık, gölgenin ne kadar şeffaf olduğunu belirler. `0` değeri tamamen opak, `1` değeri tamamen görünmez demektir. İnce bir etki için `0.3` ( %30 şeffaf) kullanacağız.

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **Neden ilgilenebilirsiniz:** Şekil koyuysa, tamamen opak bir gölge alt metni boğabilir. Saydamlığı ayarlamak, belgeyi okunabilir tutarken derinlik kazandırır.

## Adım 4: Gölgeyi Taşıyın – **Gölgeyi Nasıl Taşıyacağınız**'ın Özeti

`Distance` özelliği, gölgenin şekilden ne kadar uzakta olduğunu puan cinsinden tanımlar. Daha büyük bir mesafe gölgeyi daha uzağa iter ve daha dramatik bir etki yaratır.

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **Küçük bir kaydırma gerekirse ne olur?** `Distance` değerini `0` yaparsanız gölge doğrudan şeklin arkasına oturur; bu, kabartma etkileri için faydalı olabilir.

## Adım 5: Işık Kaynağını Döndürün – **Gölgeyi Nasıl Döndüreceğinizi** Çözmek

Gölge sadece aşağı doğru düşmez; ışık kaynağının açısına göre yön alır. `Angle` özelliği (derece cinsinden) gölgeyi şeklin etrafında döndürür. Hadi 45° eğelim.

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **Hızlı deney:** Sağ tarafta bir gölge için `90`, sola eğik bir gölge için `-30` deneyin. Görsel değişim anında görülür.

## Adım 6: Belgeyi Kaydedin – **Şekle Gölge Ekle** Sonucunu Görmek

Gölgeyi ayarladığımıza göre belgeyi diske geri yazacağız. Orijinali üzerine yazabilir ya da yeni bir dosya oluşturabilirsiniz; örnek yeni bir çıktı dosyası kullanıyor.

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **Beklenen çıktı:** `output.docx` dosyasını açın. Şeklin gölgesi daha yumuşak, hafifçe kaydırılmış, yarı‑saydam ve 45° açıyla görünecek. `input.docx` ile yan yana karşılaştırırsanız fark hemen anlaşılır.

### Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

Aşağıda tüm program tek bir blokta verilmiştir. Yeni bir konsol projesine yapıştırın, `YOUR_DIRECTORY` ifadesini gerçek bir klasör yolu ile değiştirin ve çalıştırın.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## Yaygın Sorular ve Kenar Durumları

### Belge birden fazla şekle sahipse ne olur?

Tüm şekiller üzerinde döngü kurabilirsiniz:

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### Şu anda gölgesi olmayan bir şekle gölge ekleyebilir miyim?

Kesinlikle. `ShadowFormat` nesnesi her zaman mevcuttur; sadece etkinleştirmeniz yeterlidir:

```csharp
shape.ShadowFormat.Enabled = true;
```

### Bu, resimler ve SmartArt ile çalışır mı?

Evet. `Shape` sınıfından türetilen her düğüm—resimler, grafikler ve SmartArt dahil—`ShadowFormat` özelliğine sahiptir. Aynı özellikler geçerlidir.

### Gölge rengini nasıl kontrol ederim?

`Color` özelliğini kullanın:

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Uyumluluk Endişeleri?

Aspose.Words 23.12+ .NET 6, .NET Core 3.1 ve .NET Framework 4.6.2+ sürümlerini destekler. Gösterilen API bu sürümlerde kararlıdır.

## Sonuç

**gölgeyi nasıl taşıyacağınızı** bir şekil üzerinde Aspose.Words ile nasıl yapacağınızı yeni öğrendik ve aynı zamanda **şekle gölge ekleme**, **bulanıklığı nasıl değiştireceğinizi**, **saydamlığı nasıl ayarlayacağınızı** ve **gölgeyi nasıl döndüreceğinizi** de gösterdik. Tam, çalıştırılabilir örnek, herhangi bir şeklin gölgesini saniyeler içinde ayarlamanıza olanak tanır, belgelerinize Word'ü hiç açmadan şık ve profesyonel bir görünüm kazandırır.

Bir sonraki adıma hazır mısınız? Bu gölge ayarlarını **koşullu biçimlendirme** ile birleştirin—örneğin, yalnızca başlıklara veya belirli bir boyutu aşan grafiklere daha derin bir gölge uygulayın. Ya da şeklin kendisi için **gradient doldurmalar** keşfederek gerçekten göz alıcı bir tasarım yaratın.

Herhangi bir sorunla karşılaşırsanız, aşağıya yorum bırakın. İyi kodlamalar ve gölgeleriniz her zaman istediğiniz yerde kalsın!

![Bir şekil üzerindeki gölgenin hareket ettirilmesinin etkisini gösteren diyagram – gölgeyi nasıl taşıma örneği](https://example.com/images/shadow-demo.png "gölgeyi nasıl taşıma örneği")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}