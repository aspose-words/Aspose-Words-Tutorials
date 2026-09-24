---
title: Add a Check Box Form Field to a Word Document with Aspose.Words for .NET
weight: 210
limit:
description: Learn how to programmatically add a check box form field to a new Word document using Aspose.Words for .NET and save the file.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Add a Check Box Form Field to a Word Document with Aspose.Words
This tutorial shows how to create a fresh Word document and use Aspose.Words for .NET's DocumentBuilder to insert a check box form field. By following the steps, you’ll see the exact code needed to add the interactive element and then save the document to a file. It’s a quick way to build simple form-enabled Word files programmatically.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: What does the fourth argument (0) in InsertCheckBox represent?**
A: It specifies the visual size of the check box in points; a value of 0 tells Aspose.Words to use the default size.

**Q: Can I insert more than one check box with the same name?**
A: No – each form field name must be unique; trying to insert another check box named "CheckBox" will throw an ArgumentException.

**Q: How do I add a check box to an existing document instead of a new one?**
A: Load the document first (e.g., `Document doc = new Document("Existing.docx");`) then create a DocumentBuilder for that document and call `InsertCheckBox` at the desired cursor position.

**Q: How can I read the state of the inserted check box after the document is saved?**
A: Retrieve the form field via `doc.Range.FormFields["CheckBox"]` and inspect its `Checked` property to see whether it was checked.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}