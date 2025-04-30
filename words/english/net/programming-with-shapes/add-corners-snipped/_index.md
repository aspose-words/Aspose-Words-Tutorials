---
title: Add Corners Snipped
linktitle: Add Corners Snipped
second_title: Aspose.Words Document Processing API
description: Learn how to add a corners snipped shape to your Word documents using Aspose.Words for .NET. This step-by-step guide ensures you can enhance your documents easily.
weight: 10
url: /net/programming-with-shapes/add-corners-snipped/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Add Corners Snipped

## Introduction

Adding custom shapes to your Word documents can be a fun and visually appealing way to highlight important information or add a bit of flair to your content. In this tutorial, we're going to dive into how you can insert "Corners Snipped" shapes into your Word documents using Aspose.Words for .NET. This guide will walk you through every step, ensuring you can effortlessly add these shapes and customize your documents like a pro.

## Prerequisites

Before we jump into the code, let's make sure you have everything you need to get started:

1. Aspose.Words for .NET: If you haven't already, download the latest version from the [Aspose releases page](https://releases.aspose.com/words/net/).
2. Development Environment: Set up your development environment. Visual Studio is a popular choice, but you can use any IDE that supports .NET.
3. License: If you’re just experimenting, you can use a [free trial](https://releases.aspose.com/) or get a [temporary license](https://purchase.aspose.com/temporary-license/) to unlock full functionality.
4. Basic Understanding of C#: Familiarity with C# programming will help you follow along with the examples.

## Import Namespaces

Before we can start working with Aspose.Words for .NET, we need to import the necessary namespaces. Add these at the top of your C# file:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Now, let’s break down the process of adding a "Corners Snipped" shape into multiple steps. Follow these steps closely to ensure everything works smoothly.

## Step 1: Initialize the Document and DocumentBuilder

The first thing we need to do is create a new document and initialize a `DocumentBuilder` object. This builder will help us add content to our document.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

In this step, we’ve set up our document and builder. Think of the `DocumentBuilder` as your digital pen, ready to write and draw in your Word document.

## Step 2: Insert the Corners Snipped Shape

Next, we will use the `DocumentBuilder` to insert a "Corners Snipped" shape. This shape type is predefined in Aspose.Words and can be easily inserted with a single line of code.

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

Here, we’re specifying the shape type and its dimensions (50x50). Imagine you're placing a small, perfectly snipped corner sticker on your document. 

## Step 3: Define Save Options with Compliance

Before saving our document, we need to define the save options to ensure our document complies with specific standards. We’ll use the `OoxmlSaveOptions` class for this.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

These save options ensure that our document adheres to the ISO/IEC 29500:2008 standard, which is crucial for compatibility and document longevity.

## Step 4: Save the Document

Finally, we save our document to the specified directory using the save options we defined earlier.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

And just like that, your document now contains a custom "Corners Snipped" shape, saved with the necessary compliance options.

## Conclusion

There you have it! Adding custom shapes to your Word documents using Aspose.Words for .NET is straightforward and can greatly enhance the visual appeal of your documents. By following these steps, you can easily insert a "Corners Snipped" shape and ensure your document meets the required standards. Happy coding!

## FAQ's

### Can I customize the size of the "Corners Snipped" shape?
Yes, you can adjust the size by changing the dimensions in the `InsertShape` method.

### Is it possible to add other types of shapes?
Absolutely! Aspose.Words supports various shapes. Just change the `ShapeType` to your desired shape.

### Do I need a license to use Aspose.Words?
While you can use a free trial or temporary license, a full license is required for unrestricted use.

### How can I style the shapes further?
You can use additional properties and methods provided by Aspose.Words to customize the appearance and behavior of shapes.

### Is Aspose.Words compatible with other formats?
Yes, Aspose.Words supports multiple document formats including DOCX, PDF, HTML, and more.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
