---
title: Format Number Of Data Label In A Chart
linktitle: Format Number Of Data Label In A Chart
second_title: Aspose.Words Document Processing API
description: Learn how to format data labels in charts using Aspose.Words for .NET with this step-by-step guide. Enhance your Word documents effortlessly.
weight: 10
url: /net/programming-with-charts/format-number-of-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Format Number Of Data Label In A Chart

## Introduction

Creating engaging and informative documents often involves including charts with well-formatted data labels. If you’re a .NET developer looking to enhance your Word documents with sophisticated charts, Aspose.Words for .NET is a fantastic library to help you achieve that. This tutorial will walk you through the process of formatting number labels in a chart using Aspose.Words for .NET, step by step.

## Prerequisites

Before diving into the code, there are a few prerequisites you need to have in place:

- Aspose.Words for .NET: Ensure you have the Aspose.Words for .NET library installed. If you haven't installed it yet, you can [download it here](https://releases.aspose.com/words/net/).
- Development Environment: You should have a .NET development environment set up. Visual Studio is highly recommended.
- Basic Knowledge of C#: Familiarity with C# programming is essential as this tutorial involves writing and understanding C# code.
- Temporary License: To use Aspose.Words without any limitations, you can get a [temporary license](https://purchase.aspose.com/temporary-license/).

Now, let’s dive into the step-by-step process of formatting number labels in a chart.

## Import Namespaces

First things first, we need to import the necessary namespaces to work with Aspose.Words for .NET. Add the following lines at the top of your C# file:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Step 1: Set Up Your Document Directory

Before you can start manipulating your Word document, you need to specify the directory where your document will be saved. This is essential for the save operation later on.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path to your document directory.

## Step 2: Initialize the Document and DocumentBuilder

The next step is to initialize a new `Document` and a `DocumentBuilder`. The `DocumentBuilder` is a helper class that allows us to construct the document content.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Step 3: Insert a Chart into the Document

Now, let's insert a chart into the document using the `DocumentBuilder`. In this tutorial, we'll use a Line chart as an example.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Here, we insert a Line chart with a specific width and height, and set the chart title.

## Step 4: Clear Default Series and Add New Series

By default, the chart will have some pre-generated series. We need to clear these and add our own series with specific data points.

```csharp
// Delete default generated series.
chart.Series.Clear();

// Add new series with custom data points.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Step 5: Enable Data Labels

To display the data labels on the chart, we need to enable them for our series.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Step 6: Format Data Labels

The core of this tutorial is formatting the data labels. We can apply different number formats to each data label individually.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Currency format
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Date format
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Percentage format
```

Additionally, you can link a data label's format to a source cell. When linked, the `NumberFormat` will be reset to general and inherited from the source cell.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Step 7: Save the Document

Finally, save the document to the specified directory.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

This saves your document with the specified name and ensures your chart with formatted data labels is preserved.

## Conclusion

Formatting data labels in a chart using Aspose.Words for .NET can greatly enhance the readability and professionalism of your Word documents. By following this step-by-step guide, you should now be able to create a chart, add data series, and format the data labels to meet your needs. Aspose.Words for .NET is a powerful tool that allows for extensive customization and automation of Word documents, making it an invaluable asset for .NET developers.

## FAQ's

### What is Aspose.Words for .NET?
Aspose.Words for .NET is a powerful library for creating, manipulating, and converting Word documents programmatically using C#.

### Can I format other types of charts with Aspose.Words for .NET?
Yes, Aspose.Words for .NET supports a variety of chart types, including bar, column, pie, and more.

### How do I get a temporary license for Aspose.Words for .NET?
You can obtain a temporary license [here](https://purchase.aspose.com/temporary-license/).

### Is it possible to link data labels to source cells in Excel?
Yes, you can link data labels to source cells, allowing the number format to be inherited from the source cell.

### Where can I find more detailed documentation for Aspose.Words for .NET?
You can find comprehensive documentation [here](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
