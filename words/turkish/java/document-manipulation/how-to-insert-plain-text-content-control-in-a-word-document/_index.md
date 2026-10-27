---
category: general
date: 2026-10-26
description: Aspose.Words kullanarak C#'te düz metin içerik denetimi eklemeyi öğrenin.
  StructuredDocumentTag, başlıklar ve etiket kimliklerini kapsayan adım adım bir rehber.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: tr
lastmod: 2026-10-26
og_description: Aspose.Words kullanarak C#'de düz metin içerik denetimi ekleyin. Başlıklar,
  etiket kimlikleri eklemek ve görünümü özelleştirmek için bu kılavuzu izleyin.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: C# ile Word'e Düz Metin İçerik Denetimi Ekleme – Tam Kılavuz
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C# ile bir Word belgesine düz metin içerik denetimi ekleme
url: /tr/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile bir Word belgesine düz metin içerik denetimi ekleme

Eğer bir Word dosyasına **düz metin içerik denetimi** eklemeniz gerekiyorsa, bu öğretici Aspose.Words for .NET kullanarak bunu nasıl yapacağınızı adım adım gösterir. Bir belge‑oluşturma hizmeti geliştiriyor ya da form oluşturmayı otomatikleştiriyorsanız, aşağıdaki adımlar son kullanıcıların doldurabileceği yeniden kullanılabilir, düzenlenebilir bir bölge eklemenizi sağlar.

`Document` oluşturmayı, `DocumentBuilder` ile bir düz‑metin Structured Document Tag (SDT) yerleştirmeyi, dostça bir başlık ayarlamayı ve benzersiz bir etiket tanımlayıcısı atamayı öğreneceksiniz. Rehber ayrıca görünümü değiştirme ya da denetimleri iç içe yerleştirme gibi yaygın varyasyonları da açıklar; böylece çözümü herhangi bir projeye uyarlayabilirsiniz.

## Önkoşullar

Başlamadan önce şunların kurulu olduğundan emin olun:

- .NET 6.0 veya üzeri (kod .NET Framework 4.6+ ile de çalışır)
- Geçerli bir Aspose.Words for .NET lisansı (veya ücretsiz deneme anahtarı)
- Visual Studio 2022 veya C# uyumlu herhangi bir IDE
- C# sözdizimi hakkında temel bilgi

> **Pro ipucu:** Ücretsiz deneme sürümünü kullanıyorsanız, çıktı belgesinin bir filigran içereceğini unutmayın. Lisanslı bir sürüm bunu otomatik olarak kaldırır.

## Aspose.Words kullanarak düz metin içerik denetimi ekleme

Çözümün temeli üç adımlı bir süreçtir:

1. **`Document` ve `DocumentBuilder` oluşturun.**  
2. **Varsayılan görünüme sahip bir düz‑metin Structured Document Tag (SDT) ekleyin.**  
3. **SDT’ye bir başlık ve bir etiket tanımlayıcısı atayın.**  

Her adım aşağıda, tam ve çalıştırılabilir kod örnekleriyle açıklanmıştır.

### Adım 1: Belgeyi ve builder’ı başlatma

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document`, tüm Word dosyasını temsil ederken, `DocumentBuilder` `InsertParagraph`, `InsertImage` ve bu öğreticide kritik olan `InsertStructuredDocumentTag` gibi yöntemler sunar. İlk olarak bunları başlatmak, **düz metin içerik denetimi** yerleştireceğiniz bir tuval oluşturur.

### Adım 2: Düz‑metin içerik denetimini (SDT) ekleme

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText`, Aspose.Words’e **düz metin içerik denetimi** oluşturmasını söyler; bu, kullanıcıların düzenleyebileceği basit bir metin kutusu gibi davranır. `SdtAppearance.Default` denetimi hafif bir arka planla render eder ve bölgenin belgede düzenlenebilir olduğunu belirgin kılar.

> **Neden `SdtAppearance.Default` kullanılır?**  
> Varsayılan görünüm, Word sürümleri arasında en evrensel uyumlu stildir. Kenarlık‑sız bir görünüm isterseniz, daha sonra `SdtAppearance.Hidden`’a geçebilirsiniz.

### Adım 3: Başlık ve etiket tanımlayıcısı ayarlama

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Başlık** (`sdt.Title`) Word’ün *Content Controls* panelinde görünür ve son kullanıcıların alanın amacını anlamasına yardımcı olur.  
- **Etiket** (`sdt.Tag`) geliştirici‑odaklı bir tanımlayıcıdır; daha sonra `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` ile sorgulanabilir.  
- **PlaceholderName**, gri renkte rehber metni sağlar ve kullanıcı deneyimini iyileştirir.

Yukarıdaki tam kod parçacığı, derleyip çalıştırabileceğiniz bağımsız bir program oluşturur. Çalıştırdıktan sonra `output.docx`, başlığı *MyTag* ve etiketi *TagId* olan tek bir düz‑metin içerik denetimi içerir.

![Diagram showing insert plain text content control in a Word document](image.png){alt="insert plain text content control"}

## StructuredDocumentTag (SDT) ve özelliklerini anlama

Bir **Structured Document Tag** (SDT), Word içerik denetimlerinin temel nesne modelidir. Düz metin denetimi eklemek için en ilgili özellikler şunlardır:

| Özellik | Amaç | Tipik değerler |
|----------|------|----------------|
| `SdtType` | Denetim tipini belirler (düz metin, zengin metin, resim vb.) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | Denetimin görsel stili | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | *Content Controls* panelinde gösterilen insan‑okunur ad | Herhangi kısa metin |
| `Tag` | Kod içinde kullanılan makine‑okunur tanımlayıcı | Alfanümerik dize |
| `PlaceholderName` | Denetim boşken gösterilen metin | Özel ipucu metni |

`SdtType.PlainText` ayarlandığında, Word içeriği sadece düz karakterlerle sınırlayarak zengin biçimlendirmeyi engeller. Bu, *İsim*, *E‑posta* veya *Telefon Numarası* gibi basit form alanları için denetimi ideal kılar.

### İhtiyacınız olabilecek varyasyonlar

| Senaryo | Kod değişikliği |
|----------|-----------------|
| **Görsel gölgelendirme yok** (kenarlık‑sız) | `Default` yerine `SdtAppearance.Hidden` kullanın. |
| **Salt‑okunur alan** | Eklemeden sonra `sdt.LockContentControl = true` ayarlayın. |
| **Veri ile ön‑doldurma** | Etiketi oluşturduktan sonra `sdt.Text = "John Doe";` atayın. |
| **Tablodaki birden fazla denetim** | `InsertStructuredDocumentTag` çağrısından önce `builder.InsertCell();` kullanarak SDT’yi tablo hücresine ekleyin. |

## Yaygın hatalar ve nasıl önlenir

1. **Başlık atamayı unutmak** – Word denetimi oluşturur, ancak kullanıcılar *Content Controls* panelinde anlamlı bir açıklama görmez. Her zaman `sdt.Title` atayın.  
2. **Yanlış `SdtType` kullanmak** – Düz metin ihtiyacınız varken yanlışlıkla `RichText` seçerseniz, denetim biçimlendirmeye izin verir ve sonraki işlemleri bozabilir. Enum değerini iki kez kontrol edin.  
3. **Salt‑okunur bir klasöre kaydetmek** – `doc.Save` çağrısı `UnauthorizedAccessException` fırlatır. Hedef dizinin yazılabilir olduğundan emin olun veya test için `Path.GetTempPath()` kullanın.  
4. **Lisans uygulanmadı** – Geçerli bir lisans olmadan, çıktı belge bir değerlendirme filigranı içerir. Lisansı programınızın başında uygulayın:  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## Tam, çalıştırılabilir örnek

Aşağıda yeni bir konsol projesine kopyalayıp yapıştırabileceğiniz tüm program yer almaktadır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Beklenen çıktı:** `output.docx` dosyasını Microsoft Word’de açtığınızda, *“Please fill in the following field:”* satırının ardından hafif gri bir kutu içinde *MyTag* etiketi görünür. *Enter your text here* yer tutucu metni, kullanıcı yazana kadar açık gri renkte gösterilir.

## Sonuç

Artık Aspose.Words for .NET kullanarak bir Word belgesine **düz metin içerik denetimi** eklemeyi biliyorsunuz. Öğreticide `Document` başlatma, `PlainText` tipinde bir `StructuredDocumentTag` ekleme ve başlık, etiket ve yer tutucu özelleştirme konuları ele alındı. `SdtAppearance` seçeneklerini ve yaygın hataları anladığınızda, düzenlenebilir içerik denetimlerine dayalı formlar, şablonlar ve otomatik raporlar oluşturabilirsiniz.

### Sıradaki adımlar

- Açılır menüler için `RichText` veya `ComboBox` gibi diğer SDT tiplerini keşfedin.  
- Tablolar içinde birden çok içerik denetimini birleştirin veya `RepeatingSection` ile tekrarlayın.  
- `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` kullanarak denetim değerlerini programatik olarak okuyun veya değiştirin.

Varyasyonları deneyin, desenleri daha büyük belge‑oluşturma hatlarınıza entegre edin. Kodlamanın tadını çıkarın!

## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanıza ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [How to create content control in C# with Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}