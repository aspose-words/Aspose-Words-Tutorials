---
title: Insert Horizontal Rule Shape in Word Document Using Aspose.Words for .NET
weight: 110
limit:
description: Learn to add a horizontal rule shape to a Word document with Aspose.Words for .NET using DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insert Horizontal Rule Shape in Word Document Using Aspose.Words
In this tutorial you’ll learn how to programmatically insert a horizontal rule shape into a Word document with Aspose.Words for .NET. Using the Document and DocumentBuilder classes we create a new document, add a paragraph of text, and then place a horizontal line shape at the desired location. The horizontal rule provides a visual separator that can be useful for section breaks or visual emphasis.

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

**Q: Where exactly does `builder.InsertHorizontalRule()` place the line in the document?**
A: `InsertHorizontalRule` inserts a horizontal rule shape at the current cursor position of the `DocumentBuilder`; if you want it on its own line, call `builder.Writeln()` before the insert.

**Q: Can I change the thickness, color, or width of the inserted horizontal rule?**
A: `InsertHorizontalRule` adds a default‑styled rule and does not expose formatting options; to customize those properties you need to insert a `Shape` manually (e.g., `builder.InsertShape(ShapeType.HorizontalLine)`) and then set its `LineFormat` properties.

**Q: Is it possible to add more than one horizontal rule in the same document?**
A: Yes—simply call `builder.InsertHorizontalRule()` each time you need a new rule; each call creates a separate shape at the builder’s current location.

**Q: Will the horizontal rule be visible when the saved .docx is opened in Microsoft Word?**
A: Absolutely; the rule is saved as a shape inside the .docx file, so Word displays it exactly as it appears in the generated document.

**Q: What happens if the `dataDir` folder does not exist before calling `doc.Save(...)`?**
A: `doc.Save` will throw a `DirectoryNotFoundException`; ensure the target directory exists or create it programmatically before saving.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}