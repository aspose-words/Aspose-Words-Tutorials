---
title: Aspect Ratio Locked
linktitle: Aspect Ratio Locked
second_title: Aspose.Words Document Processing API
description: Learn how to lock the aspect ratio of shapes in Word documents using Aspose.Words for .NET. Follow this step-by-step guide to keep your images and shapes proportionate.
weight: 10
url: /net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspect Ratio Locked

## Introduction

Have you ever wondered how to maintain the perfect proportions of images and shapes in your Word documents? Sometimes, you need to ensure that your images and shapes don't get distorted when resized. This is where locking the aspect ratio comes in handy. In this tutorial, we'll explore how to set the aspect ratio for shapes in Word documents using Aspose.Words for .NET. We'll break it down into easy-to-follow steps, making sure you can apply these skills to your projects with confidence.

## Prerequisites

Before we dive into the code, let's go over what you need to get started:

- Aspose.Words for .NET Library: You need to have Aspose.Words for .NET installed. If you haven't already, you can [download it here](https://releases.aspose.com/words/net/).
- Development Environment: Ensure you have a .NET development environment set up. Visual Studio is a popular choice.
- Basic Knowledge of C#: Some familiarity with C# programming will be helpful.

## Import Namespaces

First things first, let's import the necessary namespaces. These namespaces will give us access to the classes and methods we need to work with Word documents and shapes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Step 1: Set Up Your Document Directory

Before we start manipulating shapes, we need to set up a directory where our documents will be stored. For the sake of simplicity, we'll use a placeholder `YOUR DOCUMENT DIRECTORY`. Replace this with the actual path to your document directory.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Step 2: Create a New Document

Next, we'll create a new Word document using Aspose.Words. This document will serve as our canvas for adding shapes and images.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Here, we create an instance of the `Document` class and use a `DocumentBuilder` to help us build the document content.

## Step 3: Insert an Image

Now, let's insert an image into our document. We'll use the `InsertImage` method of the `DocumentBuilder` class. Ensure you have an image in your specified directory.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

Replace `dataDir + "Transparent background logo.png"` with the path to your image file.

## Step 4: Lock the Aspect Ratio

Once the image is inserted, we can lock its aspect ratio. Locking the aspect ratio ensures that the proportions of the image remain constant when resizing.

```csharp
shape.AspectRatioLocked = true;
```

Setting `AspectRatioLocked` to `true` ensures that the image maintains its original aspect ratio.

## Step 5: Save the Document

Finally, we'll save the document to the specified directory. This step writes all the changes we've made to the document file.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Conclusion

Congratulations! You've successfully learned how to set the aspect ratio for shapes in Word documents using Aspose.Words for .NET. By following these steps, you can ensure that your images and shapes retain their proportions, making your documents look professional and polished. Feel free to experiment with different images and shapes to see how the aspect ratio locking feature works in various scenarios.

## FAQ's

### Can I unlock the aspect ratio after locking it?
Yes, you can unlock the aspect ratio by setting `shape.AspectRatioLocked = false`.

### What happens if I resize an image with a locked aspect ratio?
The image will resize proportionally, maintaining its original width-to-height ratio.

### Can I apply this to other shapes besides images?
Absolutely! The aspect ratio locking feature can be applied to any shape, including rectangles, circles, and more.

### Is Aspose.Words for .NET compatible with .NET Core?
Yes, Aspose.Words for .NET supports both .NET Framework and .NET Core.

### Where can I find more documentation on Aspose.Words for .NET?
You can find comprehensive documentation [here](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
