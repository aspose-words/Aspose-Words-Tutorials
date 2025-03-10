---
title: Insert Shape
linktitle: Insert Shape
second_title: Aspose.Words Document Processing API
description: Learn how to insert and manipulate shapes in Word documents using Aspose.Words for .NET with our step-by-step guide.
weight: 10
url: /net/programming-with-shapes/insert-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert Shape

## Introduction

When it comes to creating visually appealing and well-structured Word documents, shapes can play a vital role. Whether you're adding arrows, boxes, or even complex custom shapes, the ability to manipulate these elements programmatically offers unparalleled flexibility. In this tutorial, we'll explore how to insert and manipulate shapes in Word documents using Aspose.Words for .NET.

## Prerequisites

Before diving into the tutorial, ensure you have the following prerequisites:

1. Aspose.Words for .NET: Download and install the latest version from the [Aspose releases page](https://releases.aspose.com/words/net/).
2. Development Environment: A suitable .NET development environment such as Visual Studio.
3. Basic Knowledge of C#: Familiarity with C# programming language and basic concepts.

## Import Namespaces

To get started, you'll need to import the necessary namespaces in your C# project:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Step 1: Set Up Your Project

Before you can start inserting shapes, you need to set up your project and add the Aspose.Words for .NET library.

1. Create a New Project: Open Visual Studio and create a new C# Console Application project.
2. Add Aspose.Words for .NET: Install the Aspose.Words for .NET library via NuGet Package Manager.

```bash
Install-Package Aspose.Words
```

## Step 2: Initialize the Document

First, you'll need to initialize a new document and a document builder, which will help in constructing the document.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Initialize a new document
Document doc = new Document();

// Initialize a DocumentBuilder to help build the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Step 3: Insert a Shape

Now, let's insert a shape into the document. We'll start by adding a simple text box.

```csharp
// Insert a text box shape into the document
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// Rotate the shape
shape.Rotation = 30.0;
```

In this example, we insert a text box at the position (100, 100) with a width and height of 50 units each. We also rotate the shape by 30 degrees.

## Step 4: Add Another Shape

Let's add another shape to the document, this time without specifying the position.

```csharp
// Add another text box shape
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// Rotate the shape
secondShape.Rotation = 30.0;
```

This code snippet inserts another text box with the same dimensions and rotation as the first one but without specifying its position.

## Step 5: Save the Document

After adding the shapes, the final step is to save the document. We'll use the `OoxmlSaveOptions` to specify the save format.

```csharp
// Define save options with compliance
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// Save the document
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Conclusion

And there you have it! You've successfully inserted and manipulated shapes in a Word document using Aspose.Words for .NET. This tutorial covered the basics, but Aspose.Words offers many more advanced features for working with shapes, such as custom styles, connectors, and group shapes.

For more detailed information, visit the [Aspose.Words for .NET documentation](https://reference.aspose.com/words/net/).

## FAQ's

### How do I insert different types of shapes?
You can change the `ShapeType` in the `InsertShape` method to insert different types of shapes such as circles, rectangles, and arrows.

### Can I add text inside the shapes?
Yes, you can use the `builder.Write` method to add text inside the shapes after inserting them.

### Is it possible to style the shapes?
Yes, you can style the shapes by setting properties like `FillColor`, `StrokeColor`, and `StrokeWeight`.

### How do I position shapes relative to other elements?
Use the `RelativeHorizontalPosition` and `RelativeVerticalPosition` properties to position shapes relative to other elements in the document.

### Can I group multiple shapes together?
Yes, Aspose.Words for .NET allows you to group shapes using the `GroupShape` class.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
