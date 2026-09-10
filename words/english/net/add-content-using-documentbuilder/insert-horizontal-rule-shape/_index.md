---
title: Insert Horizontal Rule Shape in Word Document Using Aspose.Words for .NET
weight: 110
limit:
description: Step‑by‑step guide to insert a horizontal rule shape into a Word document with Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insert Horizontal Rule Shape in Word Document Using Aspose.Words
Learn how to use Aspose.Words for .NET to insert a horizontal rule shape into a Word document. This tutorial walks you through creating a new document, adding a line of text, placing a horizontal rule shape with DocumentBuilder, and saving the file. The horizontal rule provides a simple visual separator for your content.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: Can I change the appearance (color, thickness) of the horizontal rule inserted with DocumentBuilder.InsertHorizontalRule()?**
A: InsertHorizontalRule creates a built‑in horizontal line shape with default formatting; to modify its appearance you must retrieve the inserted Shape object (builder.CurrentParagraph.LastChild) and adjust its LineFormat properties.

**Q: What happens if I call InsertHorizontalRule() after a paragraph that already ends with a line break?**
A: The method inserts the rule as a separate paragraph, so any preceding line break simply creates an empty paragraph before the rule; the rule will still appear on its own line.

**Q: Is it possible to insert more than one horizontal rule in the same document using DocumentBuilder?**
A: Yes, each call to builder.InsertHorizontalRule() adds a new horizontal rule shape at the current cursor position, allowing multiple rules throughout the document.

**Q: Does InsertHorizontalRule() work when saving the document to formats other than DOCX, such as PDF?**
A: The horizontal rule is stored as a shape in the document model, so when you save to PDF, XPS, or other supported formats the rule is rendered correctly in the output.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}