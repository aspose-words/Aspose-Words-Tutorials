---
title: Insert Aligned HTML into Word Document Using Aspose.Words for .NET
weight: 210
limit:
description: Learn to insert raw HTML with left, center, or right alignment into a Word document using Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insert Aligned HTML into Word Document Using Aspose.Words
This interactive tutorial shows how to embed raw HTML into a Word document while controlling its alignment—left, center, or right—using Aspose.Words for .NET. By leveraging Document and DocumentBuilder, you can insert an HTML string and apply the desired paragraph alignment in just a few lines of code. The example is ideal when you need to preserve HTML formatting and place the content precisely within your document.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: What happens if the HTML string passed to DocumentBuilder.InsertHtml contains tags that Aspose.Words doesn't support, such as <script> or <iframe>?**
A: Unsupported tags are ignored; Aspose.Words parses only the subset of HTML it can render, so <script>, <iframe>, and similar elements are stripped out while the rest of the content is inserted.

**Q: Will inline CSS styles (e.g., <span style="color:red;">) be preserved when using InsertHtml?**
A: Yes, InsertHtml respects many inline CSS properties like color, font‑size, and background, converting them to the corresponding Word formatting.

**Q: Does InsertHtml automatically create a new paragraph for block‑level elements such as <div> or <h1>?**
A: Block‑level elements are mapped to Word paragraphs, so each <div>, <p>, <h1>, etc., becomes a separate paragraph in the document.

**Q: How can I insert HTML at a specific location in an existing document instead of at the beginning?**
A: Move the DocumentBuilder cursor to the desired node (e.g., builder.MoveToDocumentEnd() or builder.MoveToParagraph(index)) before calling InsertHtml; the HTML will be inserted at the current cursor position.

**Q: If the document already contains text, will calling InsertHtml overwrite existing content?**
A: No, InsertHtml inserts the parsed HTML at the builder's current position without deleting existing nodes unless you explicitly move the cursor into or delete those nodes beforehand.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}