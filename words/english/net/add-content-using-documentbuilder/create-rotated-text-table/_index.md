---
title: Create Rotated Text Table in Word Document Using Aspose.Words for .NET
weight: 110
limit:
description: Learn to build a Word table with fixed column widths, rotated text, precise row heights, and populated cells using Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Learn to build a Word table with fixed column widths, rotated text,
    precise row heights, and populated cells using Aspose.Words for .NET.
  headline: Create Rotated Text Table in Word Document Using Aspose.Words for .NET
  type: TechArticle
- description: Learn to build a Word table with fixed column widths, rotated text,
    precise row heights, and populated cells using Aspose.Words for .NET.
  name: Create Rotated Text Table in Word Document Using Aspose.Words for .NET
  steps:
  - name: Instantiate a new Document and a DocumentBuilder that will be used to construct
      the table.
    text: Instantiate a new Document and a DocumentBuilder that will be used to construct
      the table.
  - name: Start a new table, insert the first cell, and fix the column widths so they
      do not auto‑adjust.
    text: Start a new table, insert the first cell, and fix the column widths so they
      do not auto‑adjust.
  - name: Center‑align the content vertically in the current cell and write the first
      row's first cell text.
    text: Center‑align the content vertically in the current cell and write the first
      row's first cell text.
  - name: Insert the second cell of the first row and write its text.
    text: Insert the second cell of the first row and write its text.
  - name: Close the first row, finalizing its layout.
    text: Close the first row, finalizing its layout.
  - name: Start the first cell of the second row, set the row height to exactly 100
      points, rotate the text upward, and write the cell's text.
    text: Start the first cell of the second row, set the row height to exactly 100
      points, rotate the text upward, and write the cell's text.
  - name: Insert the second cell of the second row, rotate its text downward, and
      write the cell's text.
    text: Insert the second cell of the second row, rotate its text downward, and
      write the cell's text.
  - name: Close the second row, completing the table's second line.
    text: Close the second row, completing the table's second line.
  - name: Terminate the table construction, sealing the table structure.
    text: Terminate the table construction, sealing the table structure.
  - name: Save the completed document to a .docx file.
    text: Save the completed document to a .docx file.
  type: HowTo
- questions:
  - answer: After fixing the column widths, assign a width to each cell using `builder.CellFormat.Width
      = <valueInPoints>;` before inserting the next cell; the table will keep those
      exact widths.
    question: How can I set specific column widths after calling `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?
  - answer: '`builder.CellFormat.VerticalAlignment` is a cell‑level setting, so you
      need to set it again for the cells in the second row (e.g., `builder.CellFormat.VerticalAlignment
      = CellVerticalAlignment.Center;`) before writing their content.'
    question: Why does the vertical alignment only affect the first row and not the
      second row?
  - answer: Yes—set `builder.RowFormat.Height` and `builder.RowFormat.HeightRule =
      HeightRule.Exactly` before each `builder.EndRow();` call; the next row can have
      a different height value.
    question: Can I give each row a different exact height, and if so, how?
  - answer: Reset the orientation by assigning `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      before writing to the next cell.
    question: How do I revert the text orientation back to the default after using
      `TextOrientation.Upward` or `Downward`?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Create Rotated Text Table in Word with Aspose.Words
og_description: Step‑by‑step code to build a fixed‑width table with vertically rotated text and exact row heights.
og_image_alt: Screenshot showing a Word document with a table that has fixed column widths, rotated text in cells, and defined row heights, created using Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Create Rotated Text Table in Word Document Using Aspose.Words
This tutorial shows how to generate a Word document and add a table whose columns have fixed widths, rows have exact heights, and cell text is rotated vertically. You’ll learn to set vertical alignment, apply text orientation, fill each cell with content, and finally save the document—all with Aspose.Words for .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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

**Q: How can I set specific column widths after calling `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?**  
A: After fixing the column widths, assign a width to each cell using `builder.CellFormat.Width = <valueInPoints>;` before inserting the next cell; the table will keep those exact widths.

**Q: Why does the vertical alignment only affect the first row and not the second row?**  
A: `builder.CellFormat.VerticalAlignment` is a cell‑level setting, so you need to set it again for the cells in the second row (e.g., `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) before writing their content.

**Q: Can I give each row a different exact height, and if so, how?**  
A: Yes—set `builder.RowFormat.Height` and `builder.RowFormat.HeightRule = HeightRule.Exactly` before each `builder.EndRow();` call; the next row can have a different height value.

**Q: How do I revert the text orientation back to the default after using `TextOrientation.Upward` or `Downward`?**  
A: Reset the orientation by assigning `builder.CellFormat.Orientation = TextOrientation.Horizontal;` before writing to the next cell.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}