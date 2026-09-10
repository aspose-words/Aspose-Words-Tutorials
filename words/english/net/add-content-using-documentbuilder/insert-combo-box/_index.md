---
title: Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET
weight: 310
limit:
description: Learn how to add a combo box form field with predefined items to a Word document using Aspose.Words for .NET.
keywords: [combo box form field, Aspose.Words for .NET, documentbuilder combo box, add combo box word, word document form field]
url: /net/add-content-using-documentbuilder/insert-combo-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Add a Combo Box Form Field to a Word Document with Aspose.Words
This tutorial demonstrates how to use Aspose.Words for .NET's DocumentBuilder to create a new Word document and insert a combo box form field populated with predefined items. By following the step‑by‑step code, you’ll see how to configure the combo box options and then save the document for use in interactive forms.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-combo-box" >}}


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

**Q: What does the `items` array passed to `InsertComboBox` represent?**
A: It defines the list of strings that appear as selectable options in the combo box dropdown.

**Q: How can I change which item is selected by default when the document is opened?**
A: Set the third argument (`selectedIndex`) of `InsertComboBox` to the zero‑based index of the desired default item (e.g., `2` for "Three").

**Q: Is it possible to place the combo box at a specific location in the document?**
A: Yes—move the `DocumentBuilder` cursor to the desired spot using methods like `MoveToParagraph`, `InsertParagraph`, or `Write` before calling `InsertComboBox`.

**Q: What file format is created by this code and can it be opened in older versions of Word?**
A: The code saves a `.docx` file, which can be opened by Word 2007 and later, as well as any application that supports the OpenXML format.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}