---
category: general
date: 2026-09-27
description: Aspose.Words kullanarak C#'ta grup şekilli bir Word belgesini programlı
  olarak oluşturun. Dosyayı oluşturmak ve faydalı ipuçlarını öğrenmek için bu adım
  adım kılavuzu izleyin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: tr
lastmod: 2026-09-27
og_description: Aspose.Words kullanarak programlı bir şekilde grup şekilli bir Word
  belgesi oluşturun. Bu öğretici, tam C# kodunu adım adım gösterir, her adımı açıklar
  ve nihai çıktıyı gösterir.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Programatik olarak grup şekilli bir Word belgesi oluşturma – C# rehberi
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Programatik olarak grup şekilli bir Word belgesi oluşturma
url: /tr/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programmatically create a Word document with a group shape

Eğer **programmatically create a Word document** içinde gruplanmış bir çizim oluşturmanız gerekiyorsa, bu kılavuz Aspose.Words for .NET ile bunu tam olarak nasıl yapacağınızı gösterir. Bir sözleşme oluşturucu, rapor oluşturucu ya da form‑doldurma aracı geliştiriyor olun, eksiksiz C# kodunu, her API çağrısının neden önemli olduğunu ve yaygın kenar durumlarını nasıl ele alacağınızı öğreneceksiniz.

Word'de bir grup şekil oluşturmak, Word nesne modelinin grup şekillerini diğer çizim nesneleri için kapsayıcılar olarak ele alması nedeniyle zorlayıcı görünebilir. Bu öğretici yalnızca **how to create group shape word** belgelerinin nasıl oluşturulacağını yanıtlamakla kalmaz, aynı zamanda şeklin içinde düzenlenebilir içerik tutabilmesi için düz‑metin StructuredDocumentTag (SDT) nasıl gömülür de gösterir.

## What you’ll accomplish

- `Document` ve `DocumentBuilder` ile yeni bir boş Word belgesi başlatın.
- Mevcut imleç konumuna bir `GroupShape` ekleyin.
- Grup şekline düz‑metin bir `StructuredDocumentTag` (SDT) ekleyin.
- Dosyayı Microsoft Word'de açılabilecek bir `.docx` olarak kaydedin.
- Gelecek uzantılar için `GroupShape` ve `StructuredDocumentTag` ana özelliklerini anlayın.

### Prerequisites

- .NET 6.0 veya üzeri (kod .NET Framework 4.7+ ile de çalışır).
- Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`).
- Visual Studio 2022 veya C# uzantılı VS Code gibi bir C# IDE'si.

---

## Programmatically create a Word document – set up the project

1. **Create a new console project**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Open the project in your IDE** and replace the content of `Program.cs` with the code shown in the next sections.

> **Pro tip:** Proje klasörünüzü temiz tutun; Aspose.Words çıktı dosyasını çalışma dizinine yazar, mutlak bir yol belirtmezseniz.

## Step 1: Initialize the document and builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Why this matters:**  
`Document` bütün Word dosyasını temsil ederken, `DocumentBuilder` yeni öğeleri düğüm ağacını manuel olarak dolaşmadan konumlandırmanızı sağlar. Sayfa boyutlarını erken ayarlamak, grup şeklinin sayfayı aşmasını önler.

## Step 2: Insert a GroupShape at the current cursor location

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Explanation:**  
`GroupShape`, diğer şekiller, resimler veya metin kutuları tutabilen bir çizim nesnesidir. `Width`, `Height`, `Left` ve `Top` değerlerini ayarlayarak sayfadaki kesin konumunu kontrol edersiniz. `InsertNode` yöntemi şekli ana belge akışına ekler ve yüzen bir nesne gibi davranır.

## Step 3: Add a plain‑text StructuredDocumentTag (SDT) inside the group

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Why use an SDT?**  
StructuredDocumentTag'ler Word'ün yerel içerik denetimleridir. Kullanıcıların kaydedilmiş belgede metni doğrudan düzenlemesine izin verir ve daha sonra veri çıkarımı için programatik olarak erişilebilir. Bir SDT'yi grup şeklinin içine yerleştirerek görsel gruplamayı düzenlenebilir içerikle birleştirebilirsiniz.

## Step 4: Save the document

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Result:**  
`GroupShapeDemo.docx` dosyasını Microsoft Word'de açtığınızda, içinde “Enter text here” metin yer tutucusunu gösteren yüzen bir dikdörtgen (grup şekli) görürsünüz. Kullanıcılar şeklin içine tıklayıp doğrudan yazabilir.

### Expected output screenshot (conceptual)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

Dış kutu `GroupShape`; içindeki gri alan `StructuredDocumentTag`'i temsil eder.

---

## How to create group shape word – additional considerations

### Adding more child shapes

Grubu, resimler veya metin kutuları gibi ek çizim nesneleri ekleyerek zenginleştirebilirsiniz:

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Controlling wrapping style

Grup şeklinin metnin arkasında kalmasını veya sıkı sarma (tight wrapping) olmasını istiyorsanız, `WrapType` özelliğini ayarlayın:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Edge case: Empty group shape

Çocuk nesne içermeyen bir `GroupShape`, görünmez bir yer tutucu olarak render edilir. En az bir çocuk (ör. bir SDT veya resim) eklediğinizden emin olun; aksi takdirde Word kaydetme sırasında grup şekli atabilir.

### Compatibility note

Aspose.Words 23.10+ `GroupShape` ve `StructuredDocumentTag`'i tam olarak destekler. Daha eski sürümleri hedefliyorsanız, `AppendChild` yöntemi farklı davranabilir ve kaydetme sonrası `UpdatePageLayout` çağırmanız gerekebilir.

---

## Complete runnable example

Aşağıdaki tüm kod parçacığını `Program.cs` dosyanıza kopyalayın ve projeyi çalıştırın. Kod, yukarıdaki adımları tek bir, bağımsız programda birleştirir.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.PageSetup.PageWidth = 595;
        builder.PageSetup.PageHeight = 842;

        // 2️⃣ Create and insert a GroupShape.
        GroupShape groupShape = new GroupShape(doc)
        {
            Width = 300,
            Height = 150,
            Left = 100,
            Top = 100
        };
        builder.InsertNode(groupShape);

        // 3️⃣ Add a plain‑text StructuredDocumentTag (SDT) inside the group.
        StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
        {
            Title = "GroupShapeText",
            PlaceholderName = "Enter text here"
        };
        groupShape.AppendChild(sdtTag);

        // 4️⃣ Optional: add a picture to demonstrate multiple children.
        // Uncomment and adjust the path if you want to test this.
        /*
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            ImageData = ImageData.FromFile("logo.png"),
            Width = 100,
            Height = 50,
            Left


## What Should You Learn Next?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakın ilişkili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım‑adım açıklamalarla tam çalışan kod örnekleri içerir.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}