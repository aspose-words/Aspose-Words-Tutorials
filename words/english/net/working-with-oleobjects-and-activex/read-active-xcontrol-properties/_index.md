---
title: Read Active XControl Properties From Word File
linktitle: Read Active XControl Properties From Word File
second_title: Aspose.Words Document Processing API
description: Learn how to read ActiveX control properties from Word files using Aspose.Words for .NET in a step-by-step guide. Enhance your document automation skills.
weight: 10
url: /net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Read Active XControl Properties From Word File

## Introduction

In today's digital age, automation is key to enhancing productivity. If you're working with Word documents that contain ActiveX controls, you might need to read their properties for various purposes. ActiveX controls, such as checkboxes and buttons, can hold important data. Using Aspose.Words for .NET, you can efficiently extract and manipulate this data programmatically.

## Prerequisites

Before we begin, ensure you have the following:

1. Aspose.Words for .NET Library: You can download it from [here](https://releases.aspose.com/words/net/).
2. Visual Studio or any C# IDE: To write and execute your code.
3. A Word document with ActiveX controls: For example, "ActiveX controls.docx".
4. Basic knowledge of C#: Familiarity with C# programming is necessary to follow along.

## Import Namespaces

First, let's import the necessary namespaces to work with Aspose.Words for .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## Step 1: Load the Word Document

To start, you'll need to load the Word document that contains the ActiveX controls.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## Step 2: Initialize a String to Hold Properties

Next, initialize an empty string to store the properties of the ActiveX controls.

```csharp
string properties = "";
```

## Step 3: Iterate Through Shapes in the Document

We need to iterate through all shapes in the document to find the ActiveX controls.

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // Process the ActiveX control
    }
}
```

## Step 4: Extract Properties from ActiveX Controls

Within the loop, check if the control is a Forms2OleControl. If it is, cast it and extract the properties.

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## Step 5: Count Total ActiveX Controls

After iterating through all shapes, count the total number of ActiveX controls found.

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## Step 6: Display the Properties

Finally, print the extracted properties to the console.

```csharp
Console.WriteLine("\n" + properties);
```

## Conclusion

And there you have it! You've successfully learned how to read ActiveX control properties from a Word document using Aspose.Words for .NET. This tutorial covered loading a document, iterating through shapes, and extracting properties from ActiveX controls. By following these steps, you can automate the extraction of important data from your Word documents, enhancing your workflow efficiency.

## FAQ's

### What are ActiveX controls in Word documents?
ActiveX controls are interactive objects embedded in Word documents, such as checkboxes, buttons, and text fields, used to create forms and automate tasks.

### Can I modify the properties of ActiveX controls using Aspose.Words for .NET?
Yes, Aspose.Words for .NET allows you to modify the properties of ActiveX controls programmatically.

### Is Aspose.Words for .NET free to use?
Aspose.Words for .NET offers a free trial, but you'll need to purchase a license for continued use. You can get a free trial [here](https://releases.aspose.com/).

### Can I use Aspose.Words for .NET with other .NET languages besides C#?
Yes, Aspose.Words for .NET can be used with any .NET language, including VB.NET and F#.

### Where can I find more documentation on Aspose.Words for .NET?
You can find detailed documentation [here](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
