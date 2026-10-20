---
title: Add Hyperlink Comment and Export as PDF Annotation Using Aspose.Words for .NET
weight: 110
limit:
description: Learn to add a hyperlink comment in a Word file and export it as a PDF annotation with Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn to add a hyperlink comment in a Word file and export it as a
    PDF annotation with Aspose.Words for .NET.
  headline: Add Hyperlink Comment and Export as PDF Annotation Using Aspose.Words
    for .NET
  type: TechArticle
- description: Learn to add a hyperlink comment in a Word file and export it as a
    PDF annotation with Aspose.Words for .NET.
  name: Add Hyperlink Comment and Export as PDF Annotation Using Aspose.Words for
    .NET
  steps:
  - name: Create a new empty Document object and a DocumentBuilder to work with it.
    text: Create a new empty Document object and a DocumentBuilder to work with it.
  - name: Write a line of visible text that will host the upcoming comment.
    text: Write a line of visible text that will host the upcoming comment.
  - name: Create a Comment authored by Jane Doe and attach it to the first paragraph
      of the document.
    text: Create a Comment authored by Jane Doe and attach it to the first paragraph
      of the document.
  - name: Inside the comment, add a paragraph and insert a blue, underlined hyperlink
      to the Aspose.Words Library website.
    text: Inside the comment, add a paragraph and insert a blue, underlined hyperlink
      to the Aspose.Words Library website.
  - name: Configure the document to render comments as PDF annotations and refresh
      the layout.
    text: Configure the document to render comments as PDF annotations and refresh
      the layout.
  - name: Create an "Output" folder in the current directory to store the generated
      PDF.
    text: Create an "Output" folder in the current directory to store the generated
      PDF.
  - name: Save the prepared document as a PDF file using PdfSaveOptions.
    text: Save the prepared document as a PDF file using PdfSaveOptions.
  - name: Check that the PDF file exists and contains data, then output the result
      to the console.
    text: Check that the PDF file exists and contains data, then output the result
      to the console.
  type: HowTo
- questions:
  - answer: '`InsertHyperlink`’s third parameter specifies whether the link should
      be treated as a field; setting it to `false` inserts a plain hyperlink that
      works in the PDF annotation without needing a field code.'
    question: What does the third argument (`false`) in `InsertHyperlink` control?
  - answer: Set `myDocument.LayoutOptions.CommentDisplayMode` to `CommentDisplayMode.ShowInBalloons`
      before calling `Save`; the PDF will then contain the comment as a regular Word
      comment rather than an annotation.
    question: How can I make the comment appear as a balloon in the Word document
      instead of a PDF annotation?
  - answer: Yes—each `Comment` you append to a paragraph can contain its own `InsertHyperlink`
      call, and all hyperlinks will be preserved as separate PDF annotations when
      the document is saved.
    question: If I add more than one comment, will each hyperlink work in the exported
      PDF?
  - answer: Open the generated PDF, locate the comment annotation (usually shown as
      a note icon), click it to reveal the comment text, and then click the blue underlined
      link; it should open the target URL in a web browser.
    question: How do I verify that the hyperlink inside the comment actually works
      after the PDF is generated?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Insert Hyperlink Comment & Export to PDF
og_description: Learn to embed a clickable link in a Word comment and turn it into a PDF annotation.
og_image_alt: Guide showing how to add a comment with a clickable hyperlink to a Word document and export it as a PDF annotation using Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Add Hyperlink Comment and Export as PDF Annotation Using Aspose.Words
In this tutorial you’ll see how to create a Word document, insert a comment that contains a clickable hyperlink to an external website, configure that comment to appear as a PDF annotation, export the document to PDF, and verify the resulting PDF file. The step‑by‑step code lets you add rich, link‑enabled comments and preserve them when converting to PDF, making it easy to share interactive notes with readers.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: What does the third argument (`false`) in `InsertHyperlink` control?**  
A: `InsertHyperlink`’s third parameter specifies whether the link should be treated as a field; setting it to `false` inserts a plain hyperlink that works in the PDF annotation without needing a field code.

**Q: How can I make the comment appear as a balloon in the Word document instead of a PDF annotation?**  
A: Set `myDocument.LayoutOptions.CommentDisplayMode` to `CommentDisplayMode.ShowInBalloons` before calling `Save`; the PDF will then contain the comment as a regular Word comment rather than an annotation.

**Q: If I add more than one comment, will each hyperlink work in the exported PDF?**  
A: Yes—each `Comment` you append to a paragraph can contain its own `InsertHyperlink` call, and all hyperlinks will be preserved as separate PDF annotations when the document is saved.

**Q: How do I verify that the hyperlink inside the comment actually works after the PDF is generated?**  
A: Open the generated PDF, locate the comment annotation (usually shown as a note icon), click it to reveal the comment text, and then click the blue underlined link; it should open the target URL in a web browser.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}