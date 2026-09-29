---
title: Add Red Diagonal Text Watermark to Word Documents Using Aspose.Words for .NET
weight: 110
limit:
description: Automatically apply a red diagonal text watermark to every Word file generated in a batch using Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Automatically apply a red diagonal text watermark to every Word file
    generated in a batch using Aspose.Words for .NET.
  headline: Add Red Diagonal Text Watermark to Word Documents Using Aspose.Words for
    .NET
  type: TechArticle
- description: Automatically apply a red diagonal text watermark to every Word file
    generated in a batch using Aspose.Words for .NET.
  name: Add Red Diagonal Text Watermark to Word Documents Using Aspose.Words for .NET
  steps:
  - name: Create the "GeneratedReports" folder where the output files will be saved.
    text: Create the "GeneratedReports" folder where the output files will be saved.
  - name: Start a loop that will generate three separate documents.
    text: Start a loop that will generate three separate documents.
  - name: Create a new empty Word document object.
    text: Create a new empty Word document object.
  - name: Use DocumentBuilder to write a title line and a description into the document.
    text: Use DocumentBuilder to write a title line and a description into the document.
  - name: Define the appearance of the watermark, including font, size, color, and
      diagonal layout.
    text: Define the appearance of the watermark, including font, size, color, and
      diagonal layout.
  - name: Apply the configured red diagonal watermark with the text "PROTECTED" to
      the document.
    text: Apply the configured red diagonal watermark with the text "PROTECTED" to
      the document.
  - name: Save the watermarked document to the "GeneratedReports" folder with a unique
      filename.
    text: Save the watermarked document to the "GeneratedReports" folder with a unique
      filename.
  - name: Close the loop after processing the current document.
    text: Close the loop after processing the current document.
  type: HowTo
- questions:
  - answer: IsSemitrasparent determines whether the watermark is rendered with partial
      opacity; setting it to **true** makes the text semi‑transparent so underlying
      content remains more readable.
    question: What does the **IsSemitrasparent** option control and what effect does
      setting it to **true** have?
  - answer: Yes—set the **Layout** property to **WatermarkLayout.Horizontal** in the
      **TextWatermarkOptions** before calling **document.Watermark.SetText**.
    question: Can I change the watermark orientation to horizontal instead of diagonal?
  - answer: The snippet creates a fresh **Document** instance, but you can open any
      existing file (e.g., `new Document("Existing.docx")`) and then call **document.Watermark.SetText**
      to apply the same watermark.
    question: Will this code add a watermark to an existing Word file, or only to
      newly created documents?
  - answer: Assign a custom color with **Color.FromArgb(red, green, blue)** to the
      **Color** property of **TextWatermarkOptions**, e.g., `Color = Color.FromArgb(128,
      0, 128)` for purple.
    question: How can I use a custom RGB color for the watermark instead of the predefined
      **Color.Red**?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Add a Red Diagonal Text Watermark to Word Docs
og_description: See how to auto‑apply a red diagonal watermark to each Word document in a batch with Aspose.Words.
og_image_alt: Guide showing how to add a red diagonal text watermark to Word documents using Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Add Red Diagonal Text Watermark to Word Documents Using Aspose.Words
This tutorial demonstrates how to automatically embed a red diagonal text watermark into each Word document created during a batch report generation. Using Aspose.Words for .NET's Document and DocumentBuilder classes, the watermark is applied programmatically as the files are produced, ensuring every document carries the same branding or confidentiality notice without manual effort.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: What does the **IsSemitrasparent** option control and what effect does setting it to **true** have?**  
A: IsSemitrasparent determines whether the watermark is rendered with partial opacity; setting it to **true** makes the text semi‑transparent so underlying content remains more readable.

**Q: Can I change the watermark orientation to horizontal instead of diagonal?**  
A: Yes—set the **Layout** property to **WatermarkLayout.Horizontal** in the **TextWatermarkOptions** before calling **document.Watermark.SetText**.

**Q: Will this code add a watermark to an existing Word file, or only to newly created documents?**  
A: The snippet creates a fresh **Document** instance, but you can open any existing file (e.g., `new Document("Existing.docx")`) and then call **document.Watermark.SetText** to apply the same watermark.

**Q: How can I use a custom RGB color for the watermark instead of the predefined **Color.Red**?**  
A: Assign a custom color with **Color.FromArgb(red, green, blue)** to the **Color** property of **TextWatermarkOptions**, e.g., `Color = Color.FromArgb(128, 0, 128)` for purple.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}