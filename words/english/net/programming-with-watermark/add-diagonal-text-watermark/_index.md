---
title: Create a Diagonal Text Watermark with Custom Font in a Word Document Using Aspose.Words for .NET
weight: 210
limit:
description: Step‑by‑step code to add a diagonal text watermark with custom font to a Word .docx using Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Step‑by‑step code to add a diagonal text watermark with custom font
    to a Word .docx using Aspose.Words for .NET.
  headline: Create a Diagonal Text Watermark with Custom Font in a Word Document Using
    Aspose.Words for .NET
  type: TechArticle
- description: Step‑by‑step code to add a diagonal text watermark with custom font
    to a Word .docx using Aspose.Words for .NET.
  name: Create a Diagonal Text Watermark with Custom Font in a Word Document Using
    Aspose.Words for .NET
  steps:
  - name: Create a new empty Word document instance named `document`.
    text: Create a new empty Word document instance named `document`.
  - name: Configure `watermarkSettings` with Arial 48‑pt gray font, diagonal layout,
      and opaque rendering.
    text: Configure `watermarkSettings` with Arial 48‑pt gray font, diagonal layout,
      and opaque rendering.
  - name: Apply the text watermark "Private" to `document` using the previously defined
      settings.
    text: Apply the text watermark "Private" to `document` using the previously defined
      settings.
  - name: Define the file path where the watermarked document will be saved.
    text: Define the file path where the watermarked document will be saved.
  - name: Save the modified `document` to the specified path as a .docx file.
    text: Save the modified `document` to the specified path as a .docx file.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` determines whether the watermark is rendered with
      partial opacity; setting it to `false` makes the watermark fully opaque, while
      `true` applies a default semi‑transparent effect.'
    question: What does the **IsSemitrasparent** flag control in `TextWatermarkOptions`?
  - answer: Yes—set the `Layout` property to `WatermarkLayout.Horizontal` (or another
      enum value) before calling `document.Watermark.SetText`.
    question: Can I change the watermark orientation to horizontal instead of diagonal?
  - answer: Word will fall back to its default font for the watermark, so the text
      still appears but may look different from the intended style.
    question: What happens if the specified `FontFamily` (e.g., "Arial") is not installed
      on the target machine?
  - answer: Load the existing file with `Document document = new Document("Existing.docx");`
      then configure `TextWatermarkOptions` and call `document.Watermark.SetText`
      as shown.
    question: Is it possible to add a watermark to an existing `.docx` file instead
      of creating a new one?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Add a Diagonal Text Watermark with Custom Font
og_description: Learn to embed a slanted text watermark with your own font into a Word file in minutes.
og_image_alt: Guide showing how to add a diagonal text watermark with custom font to a Word document using Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Create a Diagonal Text Watermark with Custom Font in a Word Document Using Aspose.Words
This tutorial walks you through creating a fresh Word document, configuring a diagonal text watermark with your chosen font settings, applying it via the Document.Watermark.SetText API, and saving the result as a .docx file. By the end you’ll have a professionally watermarked document that showcases your branding or ownership. The step‑by‑step code is ready to copy into any .NET project.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: What does the **IsSemitrasparent** flag control in `TextWatermarkOptions`?**  
A: `IsSemitrasparent` determines whether the watermark is rendered with partial opacity; setting it to `false` makes the watermark fully opaque, while `true` applies a default semi‑transparent effect.

**Q: Can I change the watermark orientation to horizontal instead of diagonal?**  
A: Yes—set the `Layout` property to `WatermarkLayout.Horizontal` (or another enum value) before calling `document.Watermark.SetText`.

**Q: What happens if the specified `FontFamily` (e.g., "Arial") is not installed on the target machine?**  
A: Word will fall back to its default font for the watermark, so the text still appears but may look different from the intended style.

**Q: Is it possible to add a watermark to an existing `.docx` file instead of creating a new one?**  
A: Load the existing file with `Document document = new Document("Existing.docx");` then configure `TextWatermarkOptions` and call `document.Watermark.SetText` as shown.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}