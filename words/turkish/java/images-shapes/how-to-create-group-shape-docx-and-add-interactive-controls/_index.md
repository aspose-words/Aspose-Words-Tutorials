---
category: general
date: 2026-09-05
description: Tam bir C# örneğiyle grup şekilli docx oluşturmayı, ActiveX komut düğmesi
  eklemeyi ve bir Word belgesine Markdown yüklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: tr
lastmod: 2026-09-05
og_description: C# kullanarak grup şekilli bir docx oluşturun, ActiveX komut düğmesi
  ekleyin ve Markdown'ı bir Word belgesine yükleyin. Bu adım adım öğreticiyi izleyin.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Grup şekli docx oluşturun ve ActiveX kontrollerini gömün – C# rehberi
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: C#'ta grup şekilli docx nasıl oluşturulur ve etkileşimli kontroller nasıl eklenir
url: /tr/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#'ta grup şekilli docx nasıl oluşturulur ve etkileşimli kontroller eklenir

Programlı olarak **create group shape docx** dosyaları oluşturmanız gerekiyorsa, bu rehber tam olarak nasıl yapılacağını gösterir. Ayrıca **insert ActiveX command button** kontrollerini nasıl **Markdown'ı bir Word belgesine yükleyeceğinizi** alt çizgi biçimlendirmesini kaybetmeden göreceksiniz. Eğitimin sonunda, vektör grafikleri, etkileşimli UI öğeleri ve markdown tabanlı içeriği birleştiren tam işlevsel bir `.docx` dosyanız olacak.

Bu eğitim, temel bir C# geliştirme ortamına ve Aspose.Words for .NET kütüphanesinin yüklü olduğuna varsayar. Harici araçlar gerekmez—her şey standart bir .NET konsol veya masaüstü uygulaması içinde çalışır.

## Önkoşullar

- .NET 6.0 SDK veya daha yeni (kod .NET Framework 4.7+ ile de çalışır)
- Aspose.Words for .NET (NuGet paketi `Aspose.Words`)
- Geçerli bir X.509 sertifikası (`.pfx`) imzalama adımını test etmek istiyorsanız
- Bilinen bir klasöre yerleştirilmiş bir resim dosyası (ör. `logo.png`) ve bir markdown dosyası (`sample.md`)

> **Pro tip:** Tüm giriş dosyalarını tek bir *resources* klasöründe tutarak göreli yolları basitleştirin.

## Adım 1: Projeyi kurun ve ad alanlarını içe aktarın

Yeni bir konsol projesi oluşturun ve gerekli `using` yönergelerini ekleyin. Bu blok ayrıca daha sonra kullanacağınız Aspose.Words sınıflarına nasıl referans verileceğini gösterir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

`using` ifadeleri, eğitim boyunca kullanılan `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl` ve diğer tiplere doğrudan erişim sağlar.

## Adım 2: **Create group shape docx** – alt elemanlarla bir grup şekil ekleyin

*Group shape*, birden fazla çizim nesnesini tek bir birim gibi ele almanızı sağlar. Bu, ilişkili grafikleri birlikte taşıma veya yeniden boyutlandırma için kullanışlıdır.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Neden bir group shape?**  
Gruplama, kullanıcı Word içinde sürüklediğinde dikdörtgen ve elipsin hizalı kalmasını sağlar. Ayrıca ortak bir kenarlık uygulama veya tüm grafiği programlı olarak taşıma gibi sonraki işlemleri de basitleştirir.

## Adım 3: Düz metin içerik kontrolü ekleyin (kullanıcı girişi için yer tutucu)

İçerik kontrolleri, son kullanıcılara metin yazmaları için yapılandırılmış bir alan sağlar. Yer tutucu metin, kullanıcı yazmaya başladığında kaybolur.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

`PlaceholderName` özelliği, Word'ün açık gri bir ipucu olarak gösterdiği şeydir. Kullanıcılar bunu kendi metinleriyle değiştirebilir ve altındaki XML düzgün biçimde kalır.

## Adım 4: **Insert ActiveX command button** – belgeye etkileşimli UI ekleyin

ActiveX kontrolleri modern Word dosyalarında hâlâ desteklenir ve makroları ya da dış otomasyonu tetikleyebilir. Aşağıda bir *command button* ekliyor ve başlığını ayarlıyoruz.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**ActiveX düğmesi ne zaman kullanılmalı?**  
Eğer belgeyi VBA makrolarına dayanan bir kurumsal ortamda dağıtıyorsanız, bir ActiveX düğmesi bir makroyu başlatabilir veya harici bir uygulamayı çalıştırabilir. Saf HTML tabanlı etkileşim için, bunun yerine *content controls* ile *Office.js* kullanmayı düşünün.

## Adım 5: Markalaşma veya sonraki betik erişimi için gizli bir resim (ör. logo) ekleyin

Gizli şekiller, yazdırılmış belgede gösterilmez ancak XML içinde kalır, böylece daha sonra programlı olarak alınabilir.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Adım 6: **Load markdown into a Word document** – alt çizgi biçimlendirmesini koruyarak

Aspose.Words, Markdown'ı doğrudan içe aktarabilir. `ImportUnderlineFormatting` özelliğini etkinleştirmek, markdown alt çizgilerinin (`<u>` veya `__text__`) düz metin yerine Word alt çizgi stilleri olmasını sağlar.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Köşe durumu:** Markdown dosyası tablolar içeriyorsa, otomatik olarak Word tablolarına dönüştürülür. Özel tablo stiline ihtiyacınız varsa, eklemeden sonra bir `DocumentBuilder` uygulayın.

## Adım 7: Belgeyi XAdES‑EPES ile imzalayın (isteğe bağlı güvenlik adımı)

Dijital imzalar belge bütünlüğünü garanti eder. Aşağıdaki kod, **create group shape docx** dosyasını bir XAdES‑EPES profili kullanarak imzalar.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Güvenlik notu:** Sertifika şifresini kaynak kontrolünden uzak tutun. Üretimde ortam değişkenleri veya güvenli bir kasayı kullanın.

## Tam çalıştırılabilir örnek

Tüm adımları birleştirerek tek bir, bağımsız program elde edilir. Dosyayı `Program.cs` olarak kaydedin ve komut satırından çalıştırın.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Programı çalıştırmak, aşağıdakileri içeren `CompleteGroupShape.docx` dosyasını oluşturur:

- Gruplandırılmış bir dikdörtgen + elips (**create group shape docx** çekirdeği)
- Yer tutucu metinli düz metin içerik kontrolü
- “Click Me” etiketiyle bir **insert ActiveX command button**
- Gizli bir logo resmi
- Alt çizgileri korunmuş markdown içeriği
- (Sertifika sağlanırsa) bir XAdES‑EPES dijital imza

## Yaygın sorular ve sorun giderme

| Question | Answer |
|---|---|
| **ActiveX düğmesi macOS Word'de çalışır mı?** | macOS Word, ActiveX kontrollerini desteklemez. Düğme statik bir resim olarak görünecektir. Çapraz platform etkileşim için Office.js ile içerik kontrollerini kullanın. |
| **Markdown dosyası özel CSS içerirse ne olur?** | Aspose.Words CSS'yi yok sayar; yalnızca standart markdown sözdizimi işlenir. CSS ile stil verilen öğeleri içe aktarımdan sonra manuel olarak Word stillerine dönüştürün. |
| **Aynı gruba daha sonra daha fazla şekil ekleyebilir miyim?** | Evet. `GroupShape`'i adını veya indeksini kullanarak alın, ardından `AppendChild(newShape)` çağırın. Değişikliklerden sonra belgeyi yeniden kaydetmeyi unutmayın. |
| **İmza algoritmasını nasıl değiştiririm?** | `Sign` çağırmadan önce `signature.SignatureAlgorithm` ayarlayın. Varsayılan SHA‑256'dır ve çoğu uyumluluk gereksinimini karşılar. |
| **Gizli resim Word UI'da görünür mü?** | Hayır, ancak Word seçeneklerinde *Show hidden text* (Gizli metni göster) seçeneği açılarak görüntülenebilir. Bu, düzeni kirletmeden meta verileri saklamak için faydalıdır. |

## Sonraki adımlar

Artık **create group shape docx**, **insert ActiveX command button** ve **load markdown into a Word document** yapabildiğinize göre, şu konuları keşfedebilirsiniz:

- **Embedding VBA macros** that react to the ActiveX button click.
- **Applying custom styles** to the markdown‑generated paragraphs.
- **Generating PDFs** from the same document using `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **Automating batch processing** of multiple markdown files into a single compiled report.

Bu uzantılar, zengin grafikler, etkileşimli kontroller ve markdown tabanlı oluşturmayı birleştiren tamamen otomatik belge iş akışları oluşturmanızı sağlar—hepsi C#'tan.

---

*Kodlamanız keyifli olsun! Eğer bu öğreticiyi bulduysanız

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for .NET Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)
- [C# Kullanarak Word'de Dikdörtgen Şekli Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Word'den markdown oluşturma – Tam C# Kılavuzu](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}