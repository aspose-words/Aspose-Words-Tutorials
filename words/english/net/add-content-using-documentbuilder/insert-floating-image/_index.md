---
title: Insert Floating Image In Word Document
linktitle: Insert Floating Image In Word Document
second_title: Aspose.Words Document Processing API
description: Learn how to insert a floating image in a Word document using Aspose.Words for .NET with this detailed step-by-step guide. Perfect for enhancing your documents.
weight: 10
url: /net/add-content-using-documentbuilder/insert-floating-image/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert Floating Image In Word Document

## Introduction

Imagine creating a stunning report or proposal where images are perfectly positioned to complement your text. With Aspose.Words for .NET, you can achieve this effortlessly. This library provides powerful features for document manipulation, making it a go-to solution for developers. In this tutorial, we'll focus on inserting a floating image using the DocumentBuilder class. Whether you're a seasoned developer or just starting out, this guide will walk you through each step.

## Prerequisites

Before we dive in, let's ensure you have everything you need to get started:

1. Aspose.Words for .NET: You can download the library from the [Aspose releases page](https://releases.aspose.com/words/net/).
2. Visual Studio: Any version that supports .NET development.
3. Basic Knowledge of C#: Understanding the basics of C# programming will be helpful.
4. Image File: An image file you want to insert, such as a logo or picture.

## Import Namespaces

To use Aspose.Words in your project, you need to import the necessary namespaces. This is done by adding the following lines at the top of your C# file:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

With these prerequisites and namespaces in place, we're ready to start our tutorial.

Let's break down the process of inserting a floating image into a Word document into manageable steps. Each step will be explained in detail to ensure you can follow along without any hiccups.

## Step 1: Set Up Your Project

First, create a new C# project in Visual Studio. You can choose a Console App for simplicity.

1. Open Visual Studio and create a new project.
2. Select "Console App (.NET Core)" and click "Next."
3. Name your project and choose a location to save it. Click "Create."
4. Install Aspose.Words for .NET via NuGet Package Manager. Right-click on your project in the Solution Explorer, select "Manage NuGet Packages," and search for "Aspose.Words." Install the latest version.

## Step 2: Initialize Document and DocumentBuilder

Now that your project is set up, let's initialize the Document and DocumentBuilder objects.

1. Create a new instance of the `Document` class:

```csharp
Document doc = new Document();
```

2. Initialize a DocumentBuilder object:

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

The `Document` object represents the Word document, and the `DocumentBuilder` helps in adding content to it.

## Step 3: Define the Image Path

Next, specify the path to your image file. Ensure your image is accessible from your project's directory.

Define the image directory and image file name:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
string imagePath = dataDir + "Transparent background logo.png";
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path where your image is stored.

## Step 4: Insert the Floating Image

With everything set up, let's insert the floating image into the document.

Use the `InsertImage` method of the `DocumentBuilder` class to insert the image:

```csharp
builder.InsertImage(imagePath,
   RelativeHorizontalPosition.Margin,
   100,
   RelativeVerticalPosition.Margin,
   100,
   200,
   100,
   WrapType.Square);
```

Here's what each parameter means:
- `imagePath`: The path to your image file.
- `RelativeHorizontalPosition.Margin`: The horizontal position relative to the margin.
- `100`: The horizontal offset from the margin (in points).
- `RelativeVerticalPosition.Margin`: The vertical position relative to the margin.
- `100`: The vertical offset from the margin (in points).
- `200`: The width of the image (in points).
- `100`: The height of the image (in points).
- `WrapType.Square`: The text wrapping style around the image.

## Step 5: Save the Document

Finally, save the document to your desired location.

1. Specify the output file path:

```csharp
string outputPath = dataDir + "AddContentUsingDocumentBuilder.InsertFloatingImage.docx";
```

2. Save the document:

```csharp
doc.Save(outputPath);
```

Your Word document with the floating image is now ready!

## Conclusion

Inserting a floating image into a Word document using Aspose.Words for .NET is a straightforward process when broken down into manageable steps. By following this guide, you can add professional-looking images to your documents, enhancing their visual appeal. Aspose.Words provides a robust API that makes document manipulation a breeze, whether you're working on reports, proposals, or any other document type.

## FAQ's

### Can I insert multiple images using Aspose.Words for .NET?

Yes, you can insert multiple images by repeating the `InsertImage` method for each image with the desired parameters.

### How do I change the position of the image?

You can adjust the `RelativeHorizontalPosition`, `RelativeVerticalPosition`, and offset parameters to position the image as needed.

### What other wrap types are available for images?

Aspose.Words supports various wrap types such as `Inline`, `TopBottom`, `Tight`, `Through`, and more. You can choose the one that best fits your document layout.

### Can I use different image formats?

Yes, Aspose.Words supports a wide range of image formats including JPEG, PNG, BMP, and GIF.

### How do I get a free trial of Aspose.Words for .NET?

You can get a free trial from the [Aspose free trial page](https://releases.aspose.com/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
