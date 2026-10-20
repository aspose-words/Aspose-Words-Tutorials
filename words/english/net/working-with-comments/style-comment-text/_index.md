---
title: Apply Custom Style to Comment Text in Word Documents Using Aspose.Words for .NET
weight: 310
limit:
description: Learn how to add comments and apply a custom paragraph style to all comment text in a Word document with Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, style comment text, custom comment style, Word document comments, apply paragraph style, document branding]
url: /net/working-with-comments/style-comment-text/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add comments and apply a custom paragraph style to all
    comment text in a Word document with Aspose.Words for .NET.
  headline: Apply Custom Style to Comment Text in Word Documents Using Aspose.Words
    for .NET
  type: TechArticle
- description: Learn how to add comments and apply a custom paragraph style to all
    comment text in a Word document with Aspose.Words for .NET.
  name: Apply Custom Style to Comment Text in Word Documents Using Aspose.Words for
    .NET
  steps:
  - name: Create a new empty Document and a DocumentBuilder to edit it.
    text: Create a new empty Document and a DocumentBuilder to edit it.
  - name: Insert two example sentences into the document.
    text: Insert two example sentences into the document.
  - name: Create a comment by Carol, set its text, move to the start of the document,
      and attach the comment to the first paragraph.
    text: Create a comment by Carol, set its text, move to the start of the document,
      and attach the comment to the first paragraph.
  - name: Create a comment by Dave, set its text, move to the end of the document,
      and attach the comment to the last paragraph.
    text: Create a comment by Dave, set its text, move to the end of the document,
      and attach the comment to the last paragraph.
  - name: Define a custom paragraph style named "BrandComment" with Arial, 10 pt,
      dark blue, bold formatting to match the corporate brand.
    text: Define a custom paragraph style named "BrandComment" with Arial, 10 pt,
      dark blue, bold formatting to match the corporate brand.
  - name: Collect all Comment nodes in the document into a list.
    text: Collect all Comment nodes in the document into a list.
  - name: Iterate over each comment and apply the BrandComment style to every paragraph
      inside the comment.
    text: Iterate over each comment and apply the BrandComment style to every paragraph
      inside the comment.
  - name: Create a Results folder if needed and save the modified document as StyledCommentsDocument.docx.
    text: Create a Results folder if needed and save the modified document as StyledCommentsDocument.docx.
  type: HowTo
- questions:
  - answer: The code calls `commentNode.EnsureMinimum()` which creates a default paragraph
      if the comment is empty, so the subsequent style assignment always has a paragraph
      to work on.
    question: What happens if a comment node has no paragraphs when I run the style‑applying
      loop?
  - answer: Only the paragraphs inside the `Comment` object are styled; the anchor
      text in the main document retains its original formatting because the style
      is applied to `para.ParagraphFormat.Style` within each comment.
    question: Does the custom "BrandComment" style affect the comment anchor (the
      highlighted text in the main document) or only the comment’s text?
  - answer: Yes, retrieve the existing style with `document.Styles["ExistingStyleName"]`
      and assign it to `para.ParagraphFormat.Style` in the same loop, skipping the
      `document.Styles.Add` step.
    question: Can I apply an existing paragraph style instead of creating a new one
      for comments?
  - answer: It returns every `Comment` node in the document tree, including nested
      replies, because the `true` argument makes the search recursive.
    question: Will `document.GetChildNodes(NodeType.Comment, true)` also return replies
      to comments (nested comment nodes)?
  - answer: No, `document.Styles.Add` creates a style only if a style with that name
      does not already exist; subsequent runs will reuse the existing "BrandComment"
      style.
    question: If I run the code multiple times on the same document, will duplicate
      "BrandComment" styles be created?
  type: FAQPage
images:
- /net/working-with-comments/style-comment-text/og-image.png
og_title: Style All Comment Text in a Word Document
og_description: See how to programmatically add comments and give them a custom style with Aspose.Words for .NET.
og_image_alt: Screenshot showing a Word document with styled comment text created using Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Apply Custom Style to Comment Text in Word Documents Using Aspose.Words
This tutorial shows how to use Aspose.Words for .NET to programmatically add comments to a Word file and then apply a custom paragraph style to every comment paragraph. By styling comment text you can ensure that all remarks follow your corporate branding without manual formatting. The example covers creating comments, defining a style, and assigning that style to each comment block.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/style-comment-text" >}}


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

**Q: What happens if a comment node has no paragraphs when I run the style‑applying loop?**  
A: The code calls `commentNode.EnsureMinimum()` which creates a default paragraph if the comment is empty, so the subsequent style assignment always has a paragraph to work on.

**Q: Does the custom "BrandComment" style affect the comment anchor (the highlighted text in the main document) or only the comment’s text?**  
A: Only the paragraphs inside the `Comment` object are styled; the anchor text in the main document retains its original formatting because the style is applied to `para.ParagraphFormat.Style` within each comment.

**Q: Can I apply an existing paragraph style instead of creating a new one for comments?**  
A: Yes, retrieve the existing style with `document.Styles["ExistingStyleName"]` and assign it to `para.ParagraphFormat.Style` in the same loop, skipping the `document.Styles.Add` step.

**Q: Will `document.GetChildNodes(NodeType.Comment, true)` also return replies to comments (nested comment nodes)?**  
A: It returns every `Comment` node in the document tree, including nested replies, because the `true` argument makes the search recursive.

**Q: If I run the code multiple times on the same document, will duplicate "BrandComment" styles be created?**  
A: No, `document.Styles.Add` creates a style only if a style with that name does not already exist; subsequent runs will reuse the existing "BrandComment" style.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}