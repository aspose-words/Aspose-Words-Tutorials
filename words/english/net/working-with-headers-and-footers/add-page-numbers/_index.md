---
title: Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET
weight: 210
limit:
description: Add automatically updating page numbers to a Word document’s primary footer using Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Add automatically updating page numbers to a Word document’s primary
    footer using Aspose.Words for .NET.
  headline: Add Page Numbers to the Footer of a Word Document Using Aspose.Words for
    .NET
  type: TechArticle
- description: Add automatically updating page numbers to a Word document’s primary
    footer using Aspose.Words for .NET.
  name: Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET
  steps:
  - name: Create a new Document object and a DocumentBuilder tied to it.
    text: Create a new Document object and a DocumentBuilder tied to it.
  - name: Move the builder's cursor to the primary footer of the first section.
    text: Move the builder's cursor to the primary footer of the first section.
  - name: Set the paragraph alignment to center so the footer text will be centered.
    text: Set the paragraph alignment to center so the footer text will be centered.
  - name: Write the label "Page " and insert a PAGE field that displays the current
      page number.
    text: Write the label "Page " and insert a PAGE field that displays the current
      page number.
  - name: Write " of " and insert a NUMPAGES field that shows the total page count.
    text: Write " of " and insert a NUMPAGES field that shows the total page count.
  - name: Save the document to a .docx file.
    text: Save the document to a .docx file.
  type: HowTo
- questions:
  - answer: No. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` moves the builder
      only to the primary footer of the *first* section, so the fields are inserted
      there alone.
    question: If the document has more than one section, will this code add page numbers
      to every section’s footer?
  - answer: Set `builder.ParagraphFormat.Alignment` to another `ParagraphAlignment`
      value (e.g., `ParagraphAlignment.Right`) before writing the fields.
    question: How can I change the alignment of the page‑number paragraph in the footer?
  - answer: '`InsertField` takes the field code and an optional field result; passing
      `null` tells Aspose.Words to let Word calculate the result at runtime.'
    question: What does the `null` argument in `InsertField("PAGE", null)` represent?
  - answer: Yes—replace `HeaderFooterType.FooterPrimary` with `HeaderFooterType.HeaderPrimary`
      (or another header type) before inserting the fields.
    question: Can I place the same "Page X of Y" fields in the header instead of the
      footer?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Insert Automatic Page Numbers in Word Footer
og_description: Step‑by‑step code to add live page numbers to a Word footer with Aspose.Words for .NET.
og_image_alt: Guide showing how to add automatic page numbers to a Word document footer using Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Add Page Numbers to the Footer of a Word Document Using Aspose.Words
This tutorial shows how to use Aspose.Words Document and DocumentBuilder to insert automatically updating page numbers into the primary footer of a Word document. By adding page numbers programmatically, you ensure consistent pagination across the entire file without manual editing. The example code is ready to run in a .NET environment.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: If the document has more than one section, will this code add page numbers to every section’s footer?**  
A: No. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` moves the builder only to the primary footer of the *first* section, so the fields are inserted there alone.

**Q: How can I change the alignment of the page‑number paragraph in the footer?**  
A: Set `builder.ParagraphFormat.Alignment` to another `ParagraphAlignment` value (e.g., `ParagraphAlignment.Right`) before writing the fields.

**Q: What does the `null` argument in `InsertField("PAGE", null)` represent?**  
A: `InsertField` takes the field code and an optional field result; passing `null` tells Aspose.Words to let Word calculate the result at runtime.

**Q: Can I place the same "Page X of Y" fields in the header instead of the footer?**  
A: Yes—replace `HeaderFooterType.FooterPrimary` with `HeaderFooterType.HeaderPrimary` (or another header type) before inserting the fields.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}