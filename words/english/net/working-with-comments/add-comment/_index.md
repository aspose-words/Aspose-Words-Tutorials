---
title: Insert a Comment on a Specific Paragraph in a Word Document Using Aspose.Words for .NET
weight: 210
limit:
description: Step‑by‑step guide to add an author comment to a chosen paragraph in a Word document and save it as DOCX using Aspose.Words for .NET.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Step‑by‑step guide to add an author comment to a chosen paragraph in
    a Word document and save it as DOCX using Aspose.Words for .NET.
  headline: Insert a Comment on a Specific Paragraph in a Word Document Using Aspose.Words
    for .NET
  type: TechArticle
- description: Step‑by‑step guide to add an author comment to a chosen paragraph in
    a Word document and save it as DOCX using Aspose.Words for .NET.
  name: Insert a Comment on a Specific Paragraph in a Word Document Using Aspose.Words
    for .NET
  steps:
  - name: Instantiate a new Document and a DocumentBuilder to start building the Word
      file.
    text: Instantiate a new Document and a DocumentBuilder to start building the Word
      file.
  - name: Use DocumentBuilder.Writeln to add three separate paragraphs of text to
      the document.
    text: Use DocumentBuilder.Writeln to add three separate paragraphs of text to
      the document.
  - name: Retrieve the second paragraph safely, falling back to the first if the document
      has fewer than two paragraphs.
    text: Retrieve the second paragraph safely, falling back to the first if the document
      has fewer than two paragraphs.
  - name: Create a Comment with author details, set its text, and attach it to the
      selected paragraph.
    text: Create a Comment with author details, set its text, and attach it to the
      selected paragraph.
  - name: Save the modified document as a DOCX file named 'sample.docx' in the current
      folder.
    text: Save the modified document as a DOCX file named 'sample.docx' in the current
      folder.
  type: HowTo
- questions:
  - answer: The `if` block falls back to the first paragraph (`paraList[0]`) when
      `paraList.Count` is less than 2, so the comment will be attached to that single
      paragraph instead of the missing second one.
    question: What does the code do if the document contains only one paragraph?
  - answer: They are passed to the `Comment` constructor as the second and third arguments
      – `new Comment(wordDoc, "Jordan", "JH", DateTime.Now)` – where "Jordan" is the
      author name and "JH" is the initials.
    question: How are the comment author name and initials set in this example?
  - answer: In this snippet the comment is linked to the entire `Paragraph` via `AppendChild`,
      but to comment on a text range you would need to create a `CommentRangeStart`
      and `CommentRangeEnd` around the desired `Run` nodes and then add the `Comment`
      node between them.
    question: Can I attach a comment to a specific piece of text rather than the whole
      paragraph?
  - answer: '`AppendChild` adds the `Comment` node to the paragraph''s child collection,
      and Aspose.Words automatically generates the required comment start/end markers
      when the document is saved.'
    question: Do I need to manually insert comment markers, or does `AppendChild`
      handle that?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Insert a comment into a Word paragraph
og_description: Add an author comment to a specific paragraph and export the file as DOCX with Aspose.Words.
og_image_alt: Guide showing how to add a comment to a paragraph in a Word document using Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insert a Comment on a Specific Paragraph in a Word Document Using Aspose.Words
With Aspose.Words for .NET you can programmatically add comments to Word files. This tutorial walks through creating a new document, inserting three paragraphs, locating the second paragraph, and attaching a comment that includes author and date information. Finally, the document is saved as a DOCX file preserving the comment.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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

**Q: What does the code do if the document contains only one paragraph?**  
A: The `if` block falls back to the first paragraph (`paraList[0]`) when `paraList.Count` is less than 2, so the comment will be attached to that single paragraph instead of the missing second one.

**Q: How are the comment author name and initials set in this example?**  
A: They are passed to the `Comment` constructor as the second and third arguments – `new Comment(wordDoc, "Jordan", "JH", DateTime.Now)` – where "Jordan" is the author name and "JH" is the initials.

**Q: Can I attach a comment to a specific piece of text rather than the whole paragraph?**  
A: In this snippet the comment is linked to the entire `Paragraph` via `AppendChild`, but to comment on a text range you would need to create a `CommentRangeStart` and `CommentRangeEnd` around the desired `Run` nodes and then add the `Comment` node between them.

**Q: Do I need to manually insert comment markers, or does `AppendChild` handle that?**  
A: `AppendChild` adds the `Comment` node to the paragraph's child collection, and Aspose.Words automatically generates the required comment start/end markers when the document is saved.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}