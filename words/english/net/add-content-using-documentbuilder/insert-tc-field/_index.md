---
title: Add a TC Field to a Word Document with Aspose.Words for .NET
weight: 310
limit:
description: Learn to insert a TC field into a new Word document with Aspose.Words for .NET using DocumentBuilder.
keywords: [Aspose.Words for .NET, insert TC field, DocumentBuilder TC field, Word document indexing, add TC field programmatically, TC field tutorial]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Add a TC Field to a Word Document with Aspose.Words
In this interactive tutorial you’ll learn how to programmatically add a TC field—a hidden marker used by Word’s indexing and table‑of‑contents features—to a freshly created document using Aspose.Words for .NET. By using DocumentBuilder you can place the field exactly where you need it and then save the file, ready for further processing.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


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

**Q: What does the "TC" field inserted by `builder.InsertField("TC \"Entry Text\" \\f t")` actually do in the Word document?**
A: It creates a Table of Contents entry with the visible text "Entry Text" and marks it as a TC (Table of Contents) entry, which Word can later use when generating a TOC.

**Q: What is the purpose of the `\f t` switch in the TC field string?**
A: The `\f t` switch tells Word to treat the entry as a normal text entry (as opposed to a heading) and to include it in the Table of Contents when the TOC is built.

**Q: Can I insert multiple TC fields with different entry texts using the same `DocumentBuilder` instance?**
A: Yes; just call `builder.InsertField` again with a different string, e.g., `builder.InsertField("TC \"Another Entry\" \\f t")`, and each call inserts a new TC field at the current cursor position.

**Q: If I need the entry text to be dynamic (e.g., from a variable), how should I format the `InsertField` call?**
A: Build the field string with string interpolation or `String.Format`, for example: `string entry = "Chapter 1"; builder.InsertField($"TC \"{entry}\" \\f t");`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}