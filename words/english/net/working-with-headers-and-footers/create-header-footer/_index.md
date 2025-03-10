---
title: Create Header Footer
linktitle: Create Header Footer
second_title: Aspose.Words Document Processing API
description: Learn how to add and customize headers and footers in Word documents using Aspose.Words for .NET. This step-by-step guide ensures professional document formatting.
weight: 10
url: /net/working-with-headers-and-footers/create-header-footer/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Header Footer

## Introduction

Adding headers and footers to your documents can enhance their professionalism and readability. With Aspose.Words for .NET, you can easily create and customize headers and footers for your Word documents. In this tutorial, we'll walk you through the process step by step, ensuring you can implement these features seamlessly.

## Prerequisites

Before you begin, make sure you have the following:

- Aspose.Words for .NET: Download and install from the [download link](https://releases.aspose.com/words/net/).
- Development Environment: Such as Visual Studio, to write and run your code.
- Basic Knowledge of C#: Understanding of C# and .NET framework.
- Sample Document: A sample document to apply the headers and footers, or create a new one as shown in the tutorial.

## Import Namespaces

First, you need to import the necessary namespaces to access the Aspose.Words classes and methods.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Step 1: Define the Document Directory

Define the directory where your document will be saved. This helps in managing the path effectively.

```csharp
// The path to the documents directory
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Step 2: Create a New Document

Create a new document and a `DocumentBuilder` to facilitate the addition of content.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Step 3: Configure Page Setup

Set up the page settings, including whether the first page will have a different header/footer.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Step 4: Add a Header to the First Page

Move to the header section for the first page and configure the header text.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Step 5: Add a Primary Header

Move to the primary header section and insert an image and text.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Insert an image into the header
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Step 6: Add a Primary Footer

Move to the primary footer section and create a table to format the footer content.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Add page numbering
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## Step 7: Add Content and Page Breaks

Move to the end of the document, add a page break, and create a new section with different page settings.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## Step 8: Copy Headers and Footers from the Previous Section

If you want to reuse headers and footers from a previous section, copy them and apply necessary modifications.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Conclusion

By following these steps, you can effectively add and customize headers and footers in your Word documents using Aspose.Words for .NET. This enhances your document's appearance and professionalism, making it more readable and engaging.

## FAQ's

### What is Aspose.Words for .NET?

Aspose.Words for .NET is a library that enables developers to create, edit, and convert Word documents programmatically within .NET applications.

### Can I add images to the header or footer?

Yes, you can easily add images to the header or footer using the `DocumentBuilder.InsertImage` method.

### How do I set different headers and footers for the first page?

You can set different headers and footers for the first page by using the `DifferentFirstPageHeaderFooter` property of the `PageSetup` class.

### Where can I find more documentation on Aspose.Words?

You can find comprehensive documentation on the [Aspose.Words API documentation page](https://reference.aspose.com/words/net/).

### Is there support available for Aspose.Words?

Yes, Aspose offers support through their [support forum](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
