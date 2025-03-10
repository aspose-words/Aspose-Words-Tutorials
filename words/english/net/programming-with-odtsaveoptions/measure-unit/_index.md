---
title: Measure Unit
linktitle: Measure Unit
second_title: Aspose.Words Document Processing API
description: Learn how to configure the unit of measurement feature in Aspose.Words for .NET to preserve document formatting during ODT conversion.
weight: 10
url: /net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Measure Unit

## Introduction

Have you ever had to convert your Word documents to different formats but needed a specific unit of measurement for your layout? Whether you're dealing with inches, centimeters, or points, ensuring your document maintains its integrity during the conversion process is crucial. In this tutorial, we’ll walk through how to configure the unit of measurement feature in Aspose.Words for .NET. This powerful feature ensures that your document's formatting is preserved exactly as you need it when converting to ODT (Open Document Text) format.

## Prerequisites

Before diving into the code, there are a few things you'll need to get started:

1. Aspose.Words for .NET: Make sure you have the latest version of Aspose.Words for .NET installed. If you don't have it yet, you can download it from [here](https://releases.aspose.com/words/net/).
2. Development Environment: An IDE like Visual Studio to write and execute your C# code.
3. Basic Knowledge of C#: Understanding the basics of C# will help you follow along with the tutorial.
4. A Word Document: Have a sample Word document ready that you can use for conversion.

## Import Namespaces

Before we start coding, let's make sure we have the necessary namespaces imported. Add these using directives at the top of your code file:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Step 1: Set Up Your Document Directory

First, you need to define the path to your document directory. This is where your Word document is located and where the converted file will be saved.

```csharp
// Path to your documents directory
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

Replace `"YOUR DOCUMENTS DIRECTORY"` with the actual path to your directory. This ensures your code knows where to find your Word document.

## Step 2: Load the Word Document

Next, you need to load the Word document that you want to convert. This is done using the `Document` class from Aspose.Words.

```csharp
// Load the Word document
Document doc = new Document(dataDir + "Document.docx");
```

Make sure your Word document, named "Document.docx", is present in the specified directory.

## Step 3: Configure the Unit of Measurement

Now, let's configure the unit of measurement for the ODT conversion. This is where the magic happens. We'll set up the `OdtSaveOptions` to use inches as the unit of measurement.

```csharp
// Configuration of backup options with the "Unit of measurement" feature
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

In this example, we are setting the unit of measurement to inches. You can also choose other units such as `OdtSaveMeasureUnit.Centimeters` or `OdtSaveMeasureUnit.Points` depending on your requirements.

## Step 4: Convert the Document to ODT

Finally, we'll convert the Word document to the ODT format using the configured `OdtSaveOptions`.

```csharp
// Convert the document to ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

This line of code saves the converted document in the specified directory with the new unit of measurement applied.

## Conclusion

And there you have it! By following these steps, you can easily configure the unit of measurement feature in Aspose.Words for .NET to ensure your document's layout is preserved during conversion. Whether you're working with inches, centimeters, or points, this tutorial has shown you how to take control of your document's formatting with ease.

## FAQs

### What is Aspose.Words for .NET?
Aspose.Words for .NET is a powerful library for working with Word documents programmatically. It allows developers to create, modify, convert, and process Word documents without requiring Microsoft Word.

### Can I use other units of measurement besides inches?
Yes, Aspose.Words for .NET supports other units of measurement such as centimeters and points. You can specify the desired unit using the `OdtSaveMeasureUnit` enumeration.

### Is there a free trial available for Aspose.Words for .NET?
Yes, you can download a free trial of Aspose.Words for .NET from [here](https://releases.aspose.com/).

### Where can I find documentation for Aspose.Words for .NET?
You can access comprehensive documentation for Aspose.Words for .NET at [this link](https://reference.aspose.com/words/net/).

### How can I get support for Aspose.Words for .NET?
For support, you can visit the Aspose.Words forum at [this link](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
