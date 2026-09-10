---
title: Insert TC Field in Word Document Using Aspose.Words for .NET
weight: 110
limit:
description: Learn how to insert a TC field with custom text into a Word document using Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insert TC Field in Word Document Using Aspose.Words
This tutorial shows how to use Aspose.Words for .NET to insert a TC (Table of Contents) field into a newly created Word document. By using DocumentBuilder you can add a TC field with custom entry text, which is useful for building a searchable index for a table of contents. The example also demonstrates saving the document to disk.

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

**Q: What does the "\f t" switch in the TC field code mean?**
A: The "\f t" switch tells Word to treat the entry as a table entry, which makes it appear in a Table of Contents generated with the \f switch.

**Q: How can I change the text that appears in the TC field?**
A: Replace "Entry Text" in the InsertField call with any string you want, e.g., builder.InsertField("TC \"Chapter 1\" \f t");

**Q: Can I insert multiple TC fields in the same document?**
A: Yes; just call builder.InsertField with different entry texts at the desired locations before saving the document.

**Q: Does this code work for formats other than .docx, such as .pdf?**
A: The document is saved as .docx in the example, but Aspose.Words can save to other formats (e.g., .pdf) by changing the file extension in doc.Save and ensuring the appropriate output format is supported.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}