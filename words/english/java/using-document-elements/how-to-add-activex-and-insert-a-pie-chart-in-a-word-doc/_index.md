---
category: general
date: 2026-08-17
description: How to add ActiveX controls and insert a pie chart in a Word doc using
  Aspose.Words. Explode a slice and save as DOCX in a few steps.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: en
lastmod: 2026-08-17
og_description: How to add ActiveX controls, insert a pie chart, explode a slice,
  and save as DOCX with Aspose.Words – complete step‑by‑step guide.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: How to add ActiveX and insert a pie chart in a Word doc
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: How to add ActiveX and insert a pie chart in a Word doc
url: /java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to add ActiveX and insert a pie chart in a Word doc

If you need to **how to add ActiveX** controls and embed a chart in a Word document, this tutorial shows you a complete, runnable solution. Using Aspose.Words you can place an ActiveX CommandButton, create a pie chart, explode a slice for emphasis, and finally **save as DOCX** in just a few lines of C#.

In the sections below you’ll see every required import, a full code listing, and explanations of why each step matters. By the end you’ll be able to integrate interactive controls and visual data into any .docx file you generate programmatically.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 or later (the code also works with .NET Framework 4.7+)
* Aspose.Words for .NET package (available via NuGet)
* A development environment such as Visual Studio 2022 or VS Code
* Basic familiarity with C# and the Word object model

No additional third‑party chart libraries are required—Aspose.Words provides built‑in chart creation.

## How to add ActiveX controls with Aspose.Words

ActiveX controls let you embed interactive UI elements directly in a Word file. In this guide we add a **CommandButton** that can later be wired to VBA code.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Why this works:**  
`InsertForms2OleControl` creates an OLE container that the Word UI recognises as an ActiveX control. Setting the control type to `CommandButton` and giving it a caption makes it behave like a standard button when the user opens the file in Word.

## Insert pie chart and explode a slice

Charts are useful for visualizing data without leaving the document. The following steps demonstrate **how to insert chart** and specifically a **pie chart** whose first slice is exploded.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Why explode the slice:**  
Calling `SetExplode(0, true)` tells Aspose.Words to offset the first data point, drawing the viewer’s eye to that segment. This is a common technique in presentations to highlight a key value.

## Save as DOCX

After adding the ActiveX button and the chart, persist the document to disk. This step demonstrates **save as DOCX** using the standard method.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

The file `Output.docx` now contains an interactive button, a pie chart with an exploded slice, and can be opened in Microsoft Word without additional plugins.

## Full runnable example

Putting everything together, here is a self‑contained program you can copy into a console application and run immediately.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Expected result:**  
Opening `Output.docx` in Word shows a button labeled *Click Me* and a pie chart where the first slice (January) is offset from the rest. The button is ready for VBA event handling, and the chart can be edited using Word’s built‑in chart tools.

## Common questions and edge cases

* **Can I add other ActiveX types?**  
  Yes. Replace `Forms2OleControlType.CommandButton` with any value from the `Forms2OleControlType` enum (e.g., `CheckBox`, `OptionButton`). The same insertion pattern applies.

* **What if I need a different chart type?**  
  Use `ChartType.Bar`, `ChartType.Line`, etc., in the `InsertChart` call. The **how to insert chart** step stays identical; only the enum value changes.

* **How to control the size of the exploded slice?**  
  Aspose.Words currently supports a binary explode flag (true/false). For finer control (e.g., offset distance) you would need to edit the underlying OOXML after saving.

* **Is the document compatible with older Word versions?**  
  Saving as DOCX ensures compatibility with Word 2007 and later. For Word 2003 you could change `SaveFormat.Doc` but ActiveX support is limited in that format.

* **Do I need to reference `System.Drawing`?**  
  No. All drawing objects are provided by Aspose.Words, so the only required NuGet package is `Aspose.Words`.

## Conclusion

You now know **how to add ActiveX**, **insert a pie chart**, **explode a pie slice**, and **save as DOCX** using Aspose.Words for .NET. The complete example covers every step from document creation to final persistence, and it explains the reasoning behind each API call.

Next, you might explore:

* Adding VBA macros that respond to the CommandButton click (**how to insert chart** and automate data updates)
* Customizing chart appearance (colors, data labels) to match corporate branding
* Embedding additional ActiveX controls such as **ComboBox** or **ListBox** for richer forms

Feel free to experiment with the code, replace the sample data, and integrate the solution into your own document‑generation pipelines. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}