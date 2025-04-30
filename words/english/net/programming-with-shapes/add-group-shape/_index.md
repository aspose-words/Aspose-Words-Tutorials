---
title: Add Group Shape
linktitle: Add Group Shape
second_title: Aspose.Words Document Processing API
description: Learn how to add group shapes to Word documents using Aspose.Words for .NET with this comprehensive, step-by-step tutorial.
weight: 10
url: /net/programming-with-shapes/add-group-shape/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Add Group Shape

## Introduction

Creating complex documents with rich visual elements can sometimes be a daunting task, especially when dealing with group shapes. But fear not! Aspose.Words for .NET simplifies this process, making it as easy as pie. In this tutorial, we'll walk you through the steps to add group shapes to your Word documents. Ready to dive in? Let's get started!

## Prerequisites

Before we begin, ensure you have the following:

1. Aspose.Words for .NET: You can download it from the [Aspose releases page](https://releases.aspose.com/words/net/).
2. Development Environment: Visual Studio or any other IDE compatible with .NET.
3. Basic Understanding of C#: Familiarity with C# programming is a plus.

## Import Namespaces

To start, we need to import the necessary namespaces in our project. These namespaces provide access to the classes and methods required for manipulating Word documents with Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Step 1: Initialize the Document

First things first, let's initialize a new Word document. Think of this as creating a blank canvas where we'll be adding our group shapes.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

Here, `EnsureMinimum()` adds a minimal set of nodes required for the document.

## Step 2: Create the GroupShape Object

Next, we need to create a `GroupShape` object. This object will serve as a container for other shapes, allowing us to group them together.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Step 3: Add Shapes to the GroupShape

Now, let's add individual shapes to our `GroupShape` container. We'll start with an accent border shape and then add an action button shape.

### Adding an Accent Border Shape

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

This code snippet creates an accent border shape with a width and height of 100 units and adds it to the `GroupShape`.

### Adding an Action Button Shape

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

Here, we create an action button shape, position it, and add it to our `GroupShape`.

## Step 4: Define the GroupShape Dimensions

To ensure our shapes fit well within the group, we need to set the dimensions of the `GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

This defines the width and height of the `GroupShape` as 200 units and sets the coordinate size accordingly.

## Step 5: Insert the GroupShape into the Document

Now, let's insert our `GroupShape` into the document using `DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` provides an easy way to add nodes, including shapes, to the document.

## Step 6: Save the Document

Finally, save the document to your specified directory.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

And there you have it! Your document with group shapes is ready.

## Conclusion

Adding group shapes to your Word documents doesn't have to be a complicated process. With Aspose.Words for .NET, you can create and manipulate shapes with ease, making your documents more visually appealing and functional. Follow the steps outlined in this tutorial, and you'll be a pro in no time!

## FAQ's

### Can I add more than two shapes to a GroupShape?
Yes, you can add as many shapes as you need to a `GroupShape`. Just use the `AppendChild` method for each shape.

### Is it possible to style the shapes within a GroupShape?
Absolutely! Each shape can be styled individually using the properties available in the `Shape` class.

### How do I position the GroupShape within the document?
You can position the `GroupShape` by setting its `Left` and `Top` properties.

### Can I add text to the shapes within the GroupShape?
Yes, you can add text to shapes using the `AppendChild` method to add a `Paragraph` containing `Run` nodes with text.

### Is it possible to group shapes dynamically based on user input?
Yes, you can dynamically create and group shapes based on user input by adjusting the properties and methods accordingly.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
