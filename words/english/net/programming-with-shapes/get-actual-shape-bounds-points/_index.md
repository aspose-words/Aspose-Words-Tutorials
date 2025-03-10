---
title: Get Actual Shape Bounds Points
linktitle: Get Actual Shape Bounds Points
second_title: Aspose.Words Document Processing API
description: Discover how to get the actual shape bounds points in Word documents using Aspose.Words for .NET. Learn precise shape manipulation with this detailed guide.
weight: 10
url: /net/programming-with-shapes/get-actual-shape-bounds-points/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Get Actual Shape Bounds Points

## Introduction

Have you ever tried to manipulate shapes in your Word documents and wondered about their precise dimensions? Knowing the exact bounds of shapes can be crucial for various document editing and formatting tasks. Whether you're creating a detailed report, a fancy newsletter, or a sophisticated flyer, understanding shape dimensions ensures your design looks just right. In this guide, we'll dive into how to get the actual bounds of shapes in points using Aspose.Words for .NET. Ready to make your shapes picture-perfect? Let's get started!

## Prerequisites

Before we jump into the nitty-gritty, let's make sure you have everything you need:

1. Aspose.Words for .NET: Ensure you have the Aspose.Words for .NET library installed. If not, you can download it [here](https://releases.aspose.com/words/net/).
2. Development Environment: You should have a development environment set up, such as Visual Studio.
3. Basic Knowledge of C#: This guide assumes you have a basic understanding of C# programming.

## Import Namespaces

First, let's import the necessary namespaces. This is crucial as it allows us to access the classes and methods provided by Aspose.Words for .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Step 1: Create a New Document

To start, we need to create a new document. This document will be the canvas on which we insert and manipulate our shapes.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Here, we create an instance of the `Document` class and a `DocumentBuilder` to help us insert content into the document.

## Step 2: Insert an Image Shape

Next, let's insert an image into the document. This image will serve as our shape, and we will later retrieve its bounds.

```csharp
Shape shape = builder.InsertImage("YOUR DOCUMENT DIRECTORY/Transparent background logo.png");
```

Replace `"YOUR DOCUMENT DIRECTORY/Transparent background logo.png"` with the path to your image file. This line inserts the image into the document as a shape.

## Step 3: Unlock Aspect Ratio

For this example, we'll unlock the aspect ratio of the shape. This step is optional but useful if you plan to resize the shape.

```csharp
shape.AspectRatioLocked = false;
```

Unlocking the aspect ratio allows us to resize the shape freely without maintaining its original proportions.

## Step 4: Retrieve the Shape Bounds

Now comes the exciting part – retrieving the actual bounds of the shape in points. This information can be vital for precise positioning and layout.

```csharp
Console.Write("\nGets the actual bounds of the shape in points: ");
Console.WriteLine(shape.GetShapeRenderer().BoundsInPoints);
```

The `GetShapeRenderer` method provides a renderer for the shape, and `BoundsInPoints` gives us the exact dimensions.

## Conclusion

And there you have it! You've successfully retrieved the actual bounds of a shape in points using Aspose.Words for .NET. This knowledge empowers you to manipulate and position shapes with precision, ensuring your documents look exactly how you envision them. Whether you're designing complex layouts or simply need to tweak an element, understanding shape bounds is a game-changer.

## FAQ's

### Why is it important to know the bounds of a shape?
Knowing the bounds helps in precise positioning and alignment of shapes within your document, ensuring a professional look.

### Can I use other types of shapes besides images?
Absolutely! You can use any shape, such as rectangles, circles, and custom drawings.

### What if my image doesn't appear in the document?
Ensure the file path is correct and the image exists at that location. Double-check for typos or incorrect directory references.

### How can I maintain the aspect ratio of my shape?
Set `shape.AspectRatioLocked = true;` to maintain the original proportions when resizing.

### Is it possible to get bounds in units other than points?
Yes, you can convert points to other units such as inches or centimeters using appropriate conversion factors.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
