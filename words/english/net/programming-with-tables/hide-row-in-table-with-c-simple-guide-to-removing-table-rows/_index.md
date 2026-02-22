---
category: general
date: 2026-02-21
description: Hide row in table using C# and Aspose.Words. Learn how to hide row, how
  to hide row in Word, and remove row from table quickly and safely.
draft: false
keywords:
- hide row in table
- how to hide row
- remove row from table
- hide row in word
- hide row c#
language: en
og_description: Hide row in table using C# and Aspose.Words. This guide shows how
  to hide row, remove row from table, and hide row in Word documents.
og_title: Hide Row in Table with C# – Quick, Reliable Method
tags:
- C#
- Aspose.Words
- Word Automation
title: Hide Row in Table with C# – Simple Guide to Removing Table Rows
url: /net/programming-with-tables/hide-row-in-table-with-c-simple-guide-to-removing-table-rows/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hide Row in Table – Complete C# Tutorial

Ever needed to **hide row in table** while generating a Word document programmatically? You’re not the only one—developers constantly ask *how to hide row* without breaking the layout. The good news? With a few lines of C# and the powerful Aspose.Words library, you can hide a row, effectively removing it from the final output, and keep your code clean.

In this guide we’ll walk through the entire process: loading a `.docx`, picking the exact row, setting its `Hidden` property, and saving the result. By the end you’ll know exactly how to hide row in Word, how to remove row from table if you prefer deletion, and you’ll have a ready‑to‑run snippet you can drop into any .NET project. No external references required—just the code and clear explanations.

**What you’ll get**  
- A step‑by‑step walkthrough of the C# API.  
- Full, runnable code (including imports).  
- Tips for edge cases like hidden rows in merged cells.  
- Pro tips on when to *hide row* vs. *remove row from table*.

> **Prerequisite:** Visual Studio (or any C# IDE) and the Aspose.Words for .NET NuGet package (version 23.9 or later). If you’re new to Aspose.Words, the library is a pure‑managed solution—no Office installation needed.

---

## Hide Row in Table – Step‑by‑Step Implementation

Below is the complete, self‑contained example. It demonstrates the **primary** task—*hide row in table*—and also shows how you could *remove row from table* if you decide to delete it instead.

![Hide row in table example](hide-row-in-table.png "Screenshot showing a Word table with the third row hidden")

### 1. Load the Source Document  

First, we need to bring the Word file into memory. The `Document` class represents the whole file.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyDocs\input.docx");
```

*Why this matters:* Loading the document gives you access to sections, bodies, and tables. Without this step you can’t manipulate rows at all.

### 2. Locate the Desired Table  

For simplicity we grab the first table in the first section, but you can search by index, name, or even content.

```csharp
// Step 2: Get the first table in the document body
Table table = doc.FirstSection.Body.Tables[0];
```

> **Tip:** If your document has multiple tables, iterate `doc.GetChildNodes(NodeType.Table, true)` and pick the one you need.

### 3. Choose the Row You Want to Hide  

Here we target the third row (zero‑based index `2`). You could also use `Rows.Count` to verify the index exists.

```csharp
// Step 3: Choose the row you want to hide (third row, index 2)
Row rowToHide = table.Rows[2];
```

*Why this matters:* Selecting the correct row is the core of **how to hide row**. Mistaking the index will hide the wrong content.

### 4. Hide the Selected Row  

Setting `Hidden = true` tells Aspose.Words to omit the row when the document is saved. The row still exists in the object model, so you can un‑hide it later if needed.

```csharp
// Step 4: Hide the selected row – it will be omitted from the output
rowToHide.Hidden = true;
```

> **Pro tip:** If you truly want to *remove row from table* instead of hiding, call `table.Rows.Remove(rowToHide);`. Hiding preserves row metadata, which can be handy for conditional formatting.

### 5. Save the Updated Document  

Finally, write the changes back to disk.

```csharp
// Step 5: Save the document with the hidden row applied
doc.Save(@"C:\MyDocs\output.docx");
```

When you open `output.docx` in Word, the third row will be invisible—exactly what **hide row in word** means in practice.

---

## How to Hide Row – Common Variations & Edge Cases

### Hiding Multiple Rows  

If you need to hide several rows, loop through the collection:

```csharp
int[] rowsToHide = { 1, 3, 5 }; // zero‑based indexes
foreach (int i in rowsToHide)
{
    table.Rows[i].Hidden = true;
}
```

### Dealing with Merged Cells  

A hidden row that contains a vertically merged cell can cause layout warnings. The safe approach is to split the merge before hiding:

```csharp
Cell mergedCell = rowToHide.Cells[0];
if (mergedCell.CellFormat.VerticalMerge != CellMerge.None)
{
    // Break the merge to avoid Word warnings
    mergedCell.CellFormat.VerticalMerge = CellMerge.None;
}
rowToHide.Hidden = true;
```

### Compatibility with Older Word Versions  

Aspose.Words writes the `w:hideMark` attribute, which is understood by Word 2007+ and LibreOffice. If you target Word 97‑2003 (`.doc`), the hidden row will still be omitted, but complex tables may render differently. Stick to `.docx` for predictable results.

### When to *Hide Row* vs. *Remove Row from Table*  

- **Hide Row** – Keep the row for later un‑hide, preserve row height for page‑break calculations.  
- **Remove Row** – Reduce file size, permanently delete the data. Use `table.Rows.Remove(row)` if you’re sure the row isn’t needed again.

---

## Pro Tips & Gotchas

- **Pro tip:** Always check `table.Rows.Count` before accessing an index to avoid `ArgumentOutOfRangeException`.  
- **Watch out for:** Hidden rows still participate in table calculations like total height. If you notice unexpected spacing, consider setting `row.Height = 0` after hiding.  
- **Performance:** Hiding rows is cheap; removing rows triggers a re‑layout of the entire table, which can be slower on huge documents.  
- **Testing:** Open the saved file in Word and use **Reveal Formatting** (`Shift+F1`) to verify that the row’s `Hidden` flag is set.

---

## Complete Working Example (Copy‑Paste Ready)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;

class HideRowInTableDemo
{
    static void Main()
    {
        // Load the source document (ensure the path exists)
        Document doc = new Document(@"C:\MyDocs\input.docx");

        // Get the first table – adapt if you have multiple tables
        Table table = doc.FirstSection.Body.Tables[0];

        // Verify we have at least three rows
        if (table.Rows.Count < 3)
        {
            Console.WriteLine("The table doesn't have a third row to hide.");
            return;
        }

        // Choose the third row (index 2) and hide it
        Row rowToHide = table.Rows[2];
        rowToHide.Hidden = true; // This hides the row in the output document

        // Save the modified document
        doc.Save(@"C:\MyDocs\output.docx");
        Console.WriteLine("Row hidden successfully. Check output.docx.");
    }
}
```

**Expected result:** Open `output.docx` and you’ll see the table missing the third row, while the rest of the content stays untouched. The hidden row is still part of the document model, so you could later set `row.Hidden = false` to make it visible again.

---

## Conclusion

We’ve just covered **how to hide row** in a Word table using C#. By loading the document, locating the table, picking the target row, marking it as hidden, and saving, you achieve a clean *hide row in table* operation without deleting data. The same pattern lets you *remove row from table* if you need a permanent change, and the extra tips ensure you avoid common pitfalls when working with merged cells or older Word versions.

Ready for the next challenge? Try combining this technique with conditional logic—hide rows based on user input, or generate dynamic reports where certain sections disappear automatically. You might also explore **hide row in word** for headers, footers, or even entire sections.

Got questions about *hide row c#* or need help integrating this into a larger workflow? Drop a comment below or check out our related tutorials on **manipulating tables in Word with Aspose.Words**. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}