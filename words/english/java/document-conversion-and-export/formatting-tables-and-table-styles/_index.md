---
title: How to Format Tables and Apply Table Styles with Aspose.Words for Java
linktitle: Formatting Tables and Table Styles
second_title: Aspose.Words Java Document Processing API
description: Learn how to format tables, apply table styles, set table borders, and auto fit tables using Aspose.Words for Java. This guide walks you through creating Word tables with professional styling.
weight: 17
url: /java/document-conversion-and-export/formatting-tables-and-table-styles/
date: 2026-02-01
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# How to Format Tables and Apply Table Styles with Aspose.Words for Java

## Introduction

When you need to **how to format tables** in a Word document, Aspose.Words for Java gives you a full set of tools to create, style, and fine‑tune tables programmatically. Whether you’re building a simple report or a complex invoice, mastering table formatting lets you present data clearly and professionally. In this tutorial you’ll learn how to set table borders, apply cell shading, use auto fit table features, and apply predefined table styles—all with easy‑to‑follow Java code.

## Quick Answers
- **What is the primary class for building tables?** `DocumentBuilder` is used to create and populate tables.  
- **How do I set borders for an entire table?** Use `table.setBorders(LineStyle.SINGLE, thickness, Color)`.  
- **Can I apply a built‑in style?** Yes, call `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **What method auto‑sizes columns?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Is conditional formatting possible?** You can programmatically change cell shading or borders based on any condition in your code.

## What is Table Formatting in Aspose.Words?

Table formatting refers to the process of defining visual attributes—borders, shading, cell margins, and overall style—so that a table looks polished and matches the document’s design language. With Aspose.Words you can control every aspect of a Word table from Java.

## Why Apply Table Styles?

Applying a table style saves you from manually setting each property. Styles such as **MEDIUM_SHADING_1_ACCENT_1** automatically format header rows, banded rows, and first columns, giving you a consistent look across multiple tables.

## Prerequisites

1. **Java Development Kit (JDK) 8+** – required to run Aspose.Words.  
2. **IDE** – IntelliJ IDEA, Eclipse, or any Java‑compatible editor.  
3. **Aspose.Words for Java library** – download the latest version from [here](https://releases.aspose.com/words/java/).  
4. **Basic Java knowledge** – to understand the code snippets below.

## Import Packages

To start, import the Aspose.Words namespace:

```java
import com.aspose.words.*;
```

This single import gives you access to all classes needed for creating and formatting tables.

## Step 1: Formatting Tables

### Load the Document

First, create an empty document and a `DocumentBuilder` that will help you insert content.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Create and Format the Table

Now we build a table, set borders for the whole table, and apply cell shading to illustrate how to **set table borders** and **create word table** cells with different background colors.

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### Customize Cell Borders

If you need to highlight a specific cell, you can clear previous formatting and apply thicker borders.

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### Explanation

- **Set Borders:** `table.setBorders` defines a single line border with a 2‑point thickness for the whole table.  
- **Cell Shading:** Background colors (red, green) make each cell stand out.  
- **Cell Borders:** The third cell receives a 4‑point border on all sides, demonstrating how to emphasize a particular cell.

## Step 2: Applying Table Styles

### Create the Document and Table

Before applying a style, you must have at least one row in the table.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Apply Table Style

Here we apply a built‑in style and enable specific style options such as banded rows and a highlighted first column.

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Add Table Data

Now fill the table with sample data. Notice the use of **auto fit table** to automatically adjust column widths.

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### Explanation

- **Set Table Style:** `MEDIUM_SHADING_1_ACCENT_1` provides a clean, shaded look.  
- **Style Options:** First column, row bands, and first row are automatically formatted.  
- **AutoFit:** `AUTO_FIT_TO_CONTENTS` ensures the table resizes based on the data it holds.

## Common Issues and Solutions

| Issue | Solution |
|-------|----------|
| Borders not showing | Ensure you call `table.setBorders` **before** adding rows, or refresh the builder after modifications. |
| Shading not applied to merged cells | Apply shading **after** merging cells, using `builder.getCellFormat().getShading()`. |
| Table width exceeds page margin | Use `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` or set explicit column widths. |
| Conditional formatting needed | Loop through rows/cells and apply shading or borders based on your business logic. |

## Frequently Asked Questions

**Q: Can I use custom table styles not included in the default options?**  
A: Yes, you can define and apply custom styles to your tables using Aspose.Words for Java. Check the [documentation](https://reference.aspose.com/words/java/) for more details on creating custom styles.

**Q: How can I apply conditional formatting to tables?**  
A: By evaluating your data in Java and calling formatting methods (e.g., `setBackgroundPatternColor`, `getBorders().setLineWidth`) inside conditional blocks, you can style cells dynamically.

**Q: Can I format merged cells in a table?**  
A: Absolutely. After merging cells with `Cell.merge`, apply shading or borders to the resulting cell to see the changes.

**Q: Is it possible to adjust the table layout dynamically?**  
A: Yes, you can modify cell widths, table width, and apply `autoFit` at runtime based on content or user input.

**Q: Where can I get more information on table formatting?**  
A: For deeper examples and API references, visit the [Aspose.Words API documentation](https://reference.aspose.com/words/java/).

---

**Last Updated:** 2026-02-01  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}