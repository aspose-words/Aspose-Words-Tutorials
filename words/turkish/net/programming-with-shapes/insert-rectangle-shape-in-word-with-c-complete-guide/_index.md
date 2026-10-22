---
category: general
date: 2026-08-10
description: C# kullanarak Word'e dikdörtgen şekil ekleyin. Şekli nasıl gizleyeceğinizi,
  Word’de şekli nasıl gizleyeceğinizi öğrenin ve Aspose.Words ile gizli şekil oluşturun.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: tr
lastmod: 2026-08-10
og_description: C# kullanarak Word'e dikdörtgen şekil ekleyin. Bu öğreticide şekli
  nasıl gizleyeceğiniz, Word'de şekli nasıl gizleyeceğiniz ve tam kod örnekleriyle
  gizli şekil oluşturmayı açıklıyoruz.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: C# ile Word'e dikdörtgen şekli ekleme – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C# ile Word'e dikdörtgen şekli ekleme – tam kılavuz
url: /tr/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Word belgesine dikdörtgen şekli ekleme – tam kılavuz

Bir Word belgesine **dikdörtgen şekli eklemeniz** gerektiğinde, bu kılavuz size adım adım gereken işlemleri gösterir. Ayrıca **şekli gizleme** yöntemini öğrenerek şeklin son dosyada görünmemesini sağlayabilir, yaygın olarak sorulan **hide shape in Word** sorusuna yanıt bulabilir ve **create hidden shape** işlemini programatik olarak nasıl yapacağınızı görebilirsiniz.

Bu öğreticide Aspose.Words SDK'sının kurulumu, şeklin gizli olduğunun doğrulanması gibi tüm konular ele alınmaktadır. Makalenin sonunda, herhangi bir .NET projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığı elde edeceksiniz.

## Prerequisites

Başlamadan önce şunların yüklü olduğundan emin olun:

- .NET 6.0 veya daha yeni bir sürüm (kod .NET Framework 4.6+ ile de çalışır)
- Geçerli bir Aspose.Words for .NET lisansı veya geçici bir değerlendirme anahtarı
- Visual Studio 2022 (veya C# destekleyen herhangi bir IDE)
- C# sözdizimi ve Word dosyalarının Document Object Model (DOM) yapısına temel aşinalık

`Aspose.Words` dışındaki ek NuGet paketlerine ihtiyaç yoktur.

## Step 1: Create a new blank document and a DocumentBuilder

İlk işlem bir `Document` nesnesi oluşturmaktır. `DocumentBuilder`, şekil, paragraf ve tablo gibi içerikleri eklemek için kullanışlı bir API sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document`, .docx dosyasının tamamını temsil ederken, `DocumentBuilder` bir imleç tutar ve bir sonraki öğenin nereye yerleştirileceğini izler. Her iki nesnenin de başlatılması, herhangi bir Word otomasyon görevinin temelini oluşturur.

## Step 2: Insert rectangle shape

Şimdi dikdörtgeni ekleyin. `InsertShape` metodu, şekil tipini ve boyutlarını puan (point) cinsinden ister (1 point ≈ 1/72 inç). **200 × 100 point** boyutu, yaklaşık 2.78 × 1.39 inçlik bir dikdörtgen oluşturur.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Why this matters:** Aldığınız `Shape` nesnesi tamamen yapılandırılabilir—renk, kenarlık, metin ve görünürlük, belge kaydedilmeden önce değiştirilebilir.

## Step 3: Hide the shape

Dikdörtgenin görüntülenmesini veya yazdırılmasını engellemek için `Hidden` özelliğini `true` yapın. Bu özellik, Word’ün hem görüntüleme hem de yazdırma modlarında saygı gösterdiği “Hidden” niteliğine doğrudan karşılık gelir.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Why this matters:** `Hidden` ayarı, şekli belge yapısından kaldırmadan **hide shape in Word** işleminin standart yoludur. Şekil, kod tarafından erişilebilir olmaya devam eder; bu sayede koşullu biçimlendirme veya veri odaklı görünürlük değişiklikleri gibi sonraki işlemler yapılabilir.

## Step 4: Save the document

Son olarak belgeyi diske kaydedin. İstediğiniz bir klasörü seçin; örnek, gerçek bir yolla değiştirilmesi gereken bir yer tutucu yol kullanır.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Why this matters:** Kaydetme işlemi dosyayı sonlandırır ve gizli bayrağını alttaki Open XML’e yazar. Microsoft Word’de belgeyi açtığınızda dikdörtgen görünmez ve **created hidden shape** işleminin başarılı olduğunu doğrular.

## Step 5: Verify the hidden shape

Oluşturulan `HiddenShape.docx` dosyasını Microsoft Word’de açın:

1. **File → Options → Display** menüsüne gidin ve *“Show hidden text”* seçeneğinin **unchecked** olduğundan emin olun.  
2. Dikdörtgen hiçbir sayfada görünmemelidir.  
3. Çift kontrol için *“Show hidden text”* seçeneğini etkinleştirin; dikdörtgen hafif noktalı bir konturla görünecek ve şeklin var olduğunu, ancak gizli olduğunu gösterecektir.

Dikdörtgen hâlâ görünüyorsa, `Hidden = true` ayarını yaptıktan sonra dosyayı kaydettiğinizden ve doğru dosyayı açtığınızdan emin olun.

## Full runnable example

Aşağıda doğrudan kopyalayıp çalıştırabileceğiniz tam program yer almaktadır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Expected output:** Konsol, dosya yolunu ve kısa bir hatırlatmayı yazdırır. Dosya Word’de açıldığında, gizli metin etkinleştirilmediği sürece dikdörtgen görünmez.

## Common questions and edge cases

### Can I hide only the outline but keep the fill visible?

Evet. `Hidden = true` yerine `rectangle.LineFormat.Visible = false` ayarlayarak kenarlığı gizleyebilir, dolgu rengini görünür tutabilirsiniz. Bu, **how to hide shape** sorusunun görselin bir kısmını koruyan bir varyasyonudur.

### Does the hidden flag work in older Word versions (2003, 2007)?

Gizli niteliği, Word 2007 ile tanıtılan Open XML spesifikasyonunun bir parçasıdır. Eski ikili `.doc` formatında kaydedilen belgeler bu bayrağı koruyamaz. Eski formatları desteklemek için belgeyi `.docx` olarak kaydedin ve gerekirse Aspose.Words’ün `SaveFormat.Doc` özelliğiyle daha sonra dönüştürün.

### What if I need to hide multiple shapes at once?

`Document.GetChildNodes(NodeType.Shape, true)` koleksiyonunu döngüye alıp, kriterlerinize (ör. belirli bir `ShapeType` veya özel bir `AlternativeText` değeri) uyan her şeklin `Hidden = true` özelliğini ayarlayın.

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Is there a performance impact when hiding shapes?

Gizli bayrağı sadece küçük bir XML özniteliği ekler; render hızını etkilemez. Ancak çok büyük sayıda gizli nesne dosya boyutunu hafifçe artırabilir. Gerekmeyen şekilleri kaldırarak belgenin hafif kalmasını sağlayın.

## Tips and best practices

- **Give the shape a meaningful name** using `rectangle.Name = "MyHiddenRectangle"`; this helps when you later search for the shape in the DOM.  
- **Set `AlternativeText`** to a custom tag (e.g., `"HiddenShape"`). This allows you to locate the shape without relying on its index.  
- **Wrap the code in a try‑catch block** to handle licensing errors or I/O exceptions gracefully.  
- **Dispose of the Document** after saving if you are processing many files in a loop to free unmanaged resources: `document.Dispose();`.

## Conclusion

Artık C# ile bir Word belgesine **dikdörtgen şekli ekleme**, **hide shape in Word** ve **create hidden shape** konularını biliyorsunuz; şekil belge yapısının bir parçası olarak kalır ancak son kullanıcılar için görünmez. Tam ve çalıştırılabilir örnek, belge oluşturulmasından doğrulamaya kadar tüm süreci göstermektedir.

Sonraki adımda, **how to hide shape** işlemini kullanıcı girdisine göre uygulayabilir veya dinamik belge üretimi için gizli şekilleri içerik denetimleriyle birleştirebilirsiniz. Aynı tekniği elips, ok veya özel çizimler gibi diğer şekil türlerine de uygulayabilirsiniz.

Farklı boyutlar, renkler ve görünürlük ayarlarıyla denemeler yapmaktan çekinmeyin. Sorunla karşılaşırsanız, yukarıdaki adımlara geri dönün veya daha derin API detayları için Aspose.Words dokümantasyonuna göz atın. İyi kodlamalar!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}