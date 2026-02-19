---
category: general
date: 2026-02-18
description: Aspose.Words kullanarak dikdörtgen şekil oluşturun ve gölge eklemeyi,
  şekil boyutunu ayarlamayı ve birkaç dakika içinde Word belgesini kaydetmeyi öğrenin.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: tr
og_description: Word dosyasında dikdörtgen şekil oluşturun, gölge eklemeyi öğrenin,
  şekil boyutunu ayarlayın ve belgeyi C# ile Aspose.Words kullanarak kaydedin.
og_title: Word’de dikdörtgen şekli oluşturma – Tam Aspose.Words Eğitimi
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words ile Word'de Dikdörtgen Şekli Oluşturma – Adım Adım Kılavuz
url: /tr/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Aspose.Words ile dikdörtgen şekli oluşturma – Adım Adım Kılavuz

Word dosyasında **dikdörtgen şekli oluşturma** ihtiyacı hiç duydunuz mu ama nereden başlayacağınızı bilemediniz mi? Tek başınıza değilsiniz—geliştiriciler sık sık “bir şekle gölge nasıl eklerim ve belge hâlâ düzenlenebilir kalır?” diye sorar. Bu öğreticide bu soruya yanıt verecek ve ayrıca **gölge ekleme**, **şekil boyutunu ayarlama** ve **Word belgesini kaydetme** konularını tek bir akıcı adımda göstereceğiz.

İhtiyacınız olan her şeyi adım adım göstereceğiz; yeni bir belge başlatmaktan (evet, bu **belge oluşturma** için ilk adımdır) final *.docx* dosyasını diske kaydetmeye kadar. Harici referanslar yok, sadece Visual Studio'ya kopyalayıp yapıştırabileceğiniz ve bugün çalıştırabileceğiniz bağımsız bir örnek.

---

## Önkoşullar

- .NET 6+ (veya .NET Framework 4.7+). Aspose.Words, herhangi bir yeni .NET çalışma zamanıyla çalışır.
- Geçerli bir Aspose.Words lisansı (veya ücretsiz değerlendirme anahtarı) – aksi takdirde filigran görürsünüz.
- Tercih ettiğiniz Visual Studio, Rider veya herhangi bir C# editörü.
- Temel C# bilgisi—fantezi bir şey yok, sadece bir konsol uygulaması çalıştırabilme yeteneği.

> **Pro ipucu:** Mac kullanıyorsanız, aynı kod .NET 6 altında VS Code ile çalışır—sadece `Aspose.Words` NuGet paketine referans verdiğinizden emin olun.

## 1. Adım: Belgeyi Başlatma – **belge oluşturma** temelini oluşturur

Herhangi bir şey çizmeye başlamadan önce boş bir tuvale ihtiyacımız var. Aspose.Words buna `Document` adını verir.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Neden önemli:** `Document` nesnesi tüm *.docx* dosyasını temsil eder. Eklediğiniz tüm şekiller, paragraflar ve bölümler bu nesnenin alt öğeleri olur. Temiz bir belgeyle başlamak, gizli stillerin dikdörtgeninizi etkilemesini önler.

## 2. Adım: Dikdörtgeni Tanımlama ve **şekil boyutunu ayarlama**

Dikdörtgen sadece `ShapeType.Rectangle` tipinde bir `Shape`'dır. Ona tam olarak istenen şekilde görünmesi için açık boyutlar vereceğiz.  

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **Sayıların anlamı:** Aspose.Words puan (point) birimini kullanır (1 pt = 1/72 in). Değerleri düzeninize göre ayarlayın; tipik bir A4 sayfası için 200 pt rahat bir genişliktir.

## 3. Adım: **Gölge ekleme** – şekli öne çıkarmak

Gölge, şeklin sayfadan “kaldırılmış” olduğunu görsel olarak belirtir. `Shadow` özelliği renk, mesafe, şeffaflık ve bulanıklık ayarlarını yapmanıza olanak tanır.  

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Neden şeffaflık kullanmalı?** Tamamen opak bir gölge sert görünebilir. 0.4 olarak ayarlamak efekti ince ve profesyonel kılar.

## 4. Adım: Dikdörtgeni Konumlandırma – çevredeki metinle satır içi akış

Şeklin bir paragrafta karakter gibi davranmasını istiyorsanız, `WrapType` özelliğini `Inline` olarak ayarlayın. Bu, özellikle belge daha sonra düzenlendiğinde, düzenin öngörülebilir kalmasını sağlar.  

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Köşe durum:** Dikdörtgenin metnin üzerinde (ör. bir filigran) yüzmesi gerekiyorsa, `WrapType`'ı `Square` veya `BehindText` olarak değiştirin.

## 5. Adım: Şekli belge gövdesine ekleme

Şimdi dikdörtgeni ilk paragraf içine yerleştiriyoruz. Belge henüz içeriğe sahip değilse, `FirstParagraph` otomatik olarak oluşturulur.  

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **İpucu:** Önce yeni bir paragraf oluşturup ardından şekli ekleyebilirsiniz—çevresinde metin gerektiğinde faydalıdır.

## 6. Adım: **Word belgesini kaydetme** – son adım

Her şey yerli yerinde olduğunda, dosyayı kaydetmek tek satırda yapılır. İstediğiniz yolu seçin; örnek, kendi dizininizle değiştirmeniz gereken bir yer tutucu kullanır.  

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Sonuç:** Oluşturulan *.docx* dosyasını Microsoft Word'de açın. İlk paragrafla satır içinde, 200 pt genişliğinde ve 100 pt yüksekliğinde, siyah gölgeli bir dikdörtgen göreceksiniz.

## Beklenen çıktı

**ShadowShape.docx** dosyasını açtığınızda, belge şu şekilde gösterir:

- Dikdörtgen şekli içeren tek bir paragraf.
- Dikdörtgen, 5 pt kaydırılmış ince bir siyah gölgeye sahiptir.
- Şekil boyutu, 2. Adımda ayarlanan boyutlarla eşleşir.
- Elle eklemediğiniz sürece ekstra metin görünmez.

Şekil görünmezse, doğru Aspose.Words sürümüne referans verdiğinizi ve lisansınızın (veya deneme sürümünün) aktif olduğunu iki kez kontrol edin.

## Yaygın Sorular & Varyasyonlar

| Soru | Cevap |
|----------|--------|
| *Gölge rengini siyah dışındaki bir renge değiştirebilir miyim?* | Kesinlikle—`rectangleShape.Shadow.Color = Color.Blue;` ya da herhangi bir `System.Drawing.Color` ayarlayın. |
| *Daha büyük bir dikdörtgene ihtiyacım olursa ne yapmalıyım?* | `Width` ve `Height` değerlerini ayarlayın. Bunların puan cinsinden olduğunu unutmayın; 72 pt = 1 in. |
| *Şekli mutlak bir konuma yerleştirmek mümkün mü?* | Evet—`WrapType = WrapType.Absolute` kullanın ve `Top`/`Left` özelliklerini ayarlayın. |
| *Bu .NET Core ile çalışır mı?* | Evet. Aspose.Words çapraz platformdur; sadece .NET Standard için NuGet paketini kurun. |
| *Dikdörtgenin içine metin ekleyebilir miyim?* | Doğrudan değil; düz bir dikdörtgen yerine bir `TextBox` şekli eklemeniz gerekir. |

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Programı çalıştırın, `C:\Temp\ShadowShape.docx` konumuna gidin ve açıklanan şekilde gölgeli bir dikdörtgen göreceksiniz.

## Sonuç

Artık Aspose.Words kullanarak bir Word dosyasında **dikdörtgen şekli oluşturma**, **şekil boyutunu ayarlama**, **gölge ekleme** ve sonunda **Word belgesini kaydetme** konularını biliyorsunuz. Tüm süreç—**belge oluşturma** adımından sonucu kalıcı hale getirmeye kadar—birkaç C# satırı içinde sığar ve daha karmaşık düzenler için genişletilebilir.

Bir sonraki meydan okumaya hazır mısınız? Dikdörtgeni yuvarlatılmış köşeli bir şekille değiştirin, farklı gölge renkleriyle deney yapın veya şekli bir tablo hücresine yerleştirin. Her ayar, burada ele aldığımız temel kavramları pekiştirir.

Bu kılavuzu faydalı bulduysanız, paylaşın, kendi varyasyonlarınızı yorum olarak bırakın veya Aspose.Words ile resim ekleme ya da tablo oluşturma gibi Word otomasyonu üzerine diğer öğreticilerimizi keşfedin. Kodlamanın tadını çıkarın!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}