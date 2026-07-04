---
category: general
date: 2026-05-26
description: C# ile Aspose.Words kullanarak Word belgesi oluşturun, dikdörtgen şekil
  ekleyin, dolgu rengini ayarlayın ve gölge efekti ekleyin – adım adım kılavuz.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: tr
og_description: Aspose.Words kullanarak C# ile Word belgesi oluşturun. Bir dikdörtgen
  şekli eklemeyi, dolgu rengini ayarlamayı ve gölge efekti eklemeyi öğrenin.
og_title: Word Belgesi Oluştur – C#'ta Dikdörtgen Şekil ve Gölge Ekle
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Word Belgesi Oluştur – C#'ta Dikdörtgen Şekil ve Gölge Ekle
url: /tr/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesi Oluştur – C#'ta Dikdörtgen Şekil ve Gölge Ekleme

Microsoft Word'ü açmadan **Word belgesi oluştur**mayı hiç merak ettiniz mi? Tek değilsiniz. Birçok otomasyon senaryosunda—faturalar, sözleşmeler ya da toplu rapor üretimi gibi—güvenilir bir şekilde .docx dosyası oluşturup içine bir şekil yerleştirip renk vermek ve hatta o profesyonel görünüm için gölge eklemek gerekir.

Bu öğreticide tam olarak bunu adım adım göstereceğiz: Aspose.Words for .NET kullanarak **Word belgesi oluştur**, **dikdörtgen şekil ekle**, doldurma uygula ve **gölge ekle**. Sonunda, herhangi bir sonraki iş akışına aktarabileceğiniz kaydedilebilir bir dosyanız olacak.

Ayrıca **şekil ekleme** yöntemine esnek bir bakış atacağız ve **doldurmayı ayarlama** nedeninin görsel tutarlılık açısından önemini anlatacağız. Gereksiz ayrıntı yok, sadece kopyalayıp çalıştırabileceğiniz kod.

## Önkoşullar

- .NET 6+ (veya .NET Framework 4.7+) yüklü.
- Geçerli bir Aspose.Words for .NET lisansı (veya geçici değerlendirme anahtarı).
- Visual Studio, Rider veya tercih ettiğiniz herhangi bir C# IDE.
- C# sözdizimi hakkında temel bir aşinalık—karmaşık bir şey gerekmez.

Bu koşullara sahipseniz, harika, başlayalım.

## 1. Adım – Word Belgesi Oluştur

İlk olarak boş bir belge nesnesine ihtiyacınız var. Bu, diğer her şeyin yer alacağı tuvaldir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` bellek içindeki .docx dosyasını temsil eder, `DocumentBuilder` ise metin, tablo ve şekil eklemek için kullanışlı bir API sağlar. **Word belgesi oluştur** bu şekilde anında gerçekleşir—UI yok, COM etkileşimi yok, sadece saf .NET.

## 2. Adım – Dikdörtgen Şekil Ekle

Şimdi bir belgemiz olduğuna göre, **dikdörtgen şekil ekle**. `InsertShape` metodu bir `ShapeType` enum değeri, genişlik ve yükseklik (puan cinsinden) alır. Yaklaşık 2 × 1 inç ölçüsüne denk gelen 150 × 80 puanlık bir dikdörtgen kullanacağız.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Arka planda Aspose bir `Shape` nesnesi oluşturur, mevcut paragrafın içine ekler ve stil verebileceğiniz bir referans döndürür. Bu, **şekil ekleme**nin özüdür—tek bir satır kod, ama son derece güçlü.

## 3. Adım – Doldurmayı Ayarlama

Dolgusu olmayan bir şekil beyaz sayfada görünmez. Ona hoş bir açık‑mavi arka plan verelim.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

Ayrıca degrade, doku ya da resim doldurması da kullanabilirsiniz, ancak tek renk örneği basit tutar. Bu, oluşturduğunuz herhangi bir şekil üzerinde **doldurmayı ayarlama**nın nasıl yapılacağını gösterir ve okuyucularınızın beklediği görsel ipucunu sağlar.

## 4. Adım – Gölge Ekle

Gölge derinlik katar ve şekli öne çıkarır. Aspose.Words bir `ShadowFormat` nesnesi sunar; burada görünürlüğü açıp kapatabilir, renk seçebilir ve bulanıklık, mesafe ve açı gibi değerleri ince ayar yapabilirsiniz.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Bu özel değerler neden? 45° açı, doğal bir sağ‑üst ışık kaynağı verir, hafif bir bulanıklık gölgeyi ince tutar ve kısa mesafe şeklin ayrı durmasını engeller. Denemekten çekinmeyin—örneğin açıyı 135°'ye değiştirirseniz gölge alt‑sola düşer.

## 5. Adım – Belgeyi Kaydet

Tüm işler bitti; şimdi dosyayı diske yazalım. İstediğiniz yolu seçin; klasörün var olduğundan emin olun.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

`ShadowShape.docx` dosyasını Microsoft Word'de açtığınızda, yumuşak gri bir gölgeye sahip açık mavi bir dikdörtgen göreceksiniz—tam da betimlediğimiz gibi.

## Tam Çalışan Örnek

Hepsini bir araya getirdiğimizde, kopyalayıp yapıştırmaya hazır tam program aşağıdadır:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Beklenen Sonuç

- Hedef klasörde **ShadowShape.docx** adlı bir dosya oluşur.
- Word'de açtığınızda ilk sayfanın ortasında açık mavi bir dikdörtgen görürsünüz.
- Dikdörtgen, 45° açıyla gri bir gölge atar ve hafif bir 3‑B etkisi verir.

## Yaygın Sorular & Kenar Durumlar

**Farklı bir şekle ihtiyacım olsaydı ne olur?**  
`ShapeType.Rectangle` ifadesini başka bir enum değeriyle (`Ellipse`, `Star`, `Arrow` vb.) değiştirin. Kodun geri kalanı aynı kalır.

**Şeklin içine metin ekleyebilir miyim?**  
Evet—şekli oluşturduktan sonra `shape.AppendChild(new Paragraph(doc))` çağırın ve ardından bir `Run` ile metninizi ekleyin. Metin sarma istiyorsanız `shape.TextBox` özelliklerini ayarlamayı unutmayın.

**DPI veya ölçü birimleri hakkında ne söyleyebilirsiniz?**  
Aspose puan cinsinden çalışır (1 pt = 1/72 inç). Santimetre tercih ediyorsanız, puanı 28.35 ile çarpın (çünkü 1 cm ≈ 28.35 pt).

**Bunun çalışması için lisansa ihtiyacım var mı?**  
Değerlendirme sürümü ilk sayfada bir filigran ekler. Geçerli bir lisans filigranı kaldırır ve tam API erişimini açar.

## İpuçları & Dikkat Edilmesi Gerekenler

- **Pro ipucu:** Şekli belge sonuna eklemek istiyorsanız `builder.MoveToDocumentEnd()` metodunu çağırın.
- **Dikkat:** Salt okunur bir klasöre kaydetmeye çalışmak `UnauthorizedAccessException` hatası verir. Uygulamanızın yazma iznine sahip olduğundan emin olun.
- **Performans notu:** Çok sayıda belge (yüzlerce) üretirken tek bir `Document` örneğini şablon olarak yeniden kullanın ve `doc.Clone(true)` ile klonlayın; böylece tekrar eden başlatma maliyetinden kaçınırsınız.

## Sonuç

Artık **Word belgesi oluştur**, **dikdörtgen şekil ekle**, **doldurmayı ayarla** ve **gölge ekle**yi Aspose.Words for .NET ile nasıl yapacağınızı biliyorsunuz. Yukarıdaki kod parçacığı, bir konsol uygulaması, bir web API veya arka plan servisi olsun, herhangi bir C# projesine kolayca entegre edebileceğiniz bağımsız bir çözümdür.

Bundan sonra şunları keşfedebilirsiniz:

- Farklı renklerde birden fazla şekil ekleme.
- Gradyanlar veya resim doldurmaları kullanma (`shape.FillColor = ...` → `shape.FillPattern`).
- Karmaşık rapor düzenleri için şekilleri tablolarla birleştirme.

Deneyin, parametreleri ayarlayın ve otomatik Word dosyalarınızın sadece birkaç satır kodla daha profesyonel göründüğünü izleyin. İyi kodlamalar!

## İlgili Öğreticiler

- [C# ile Word'te dikdörtgen şekil oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Şekil Gölge Öğreticisi – C#'ta Word Şekline Gölge Ekle](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Aspose.Words for .NET ile Word Belgesinde Grup Şekil Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}