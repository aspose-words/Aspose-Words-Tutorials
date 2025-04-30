---
title: Shape Revision
linktitle: Shape Revision
second_title: Aspose.Words Document Processing API
description: Learn how to handle shape revisions in Word documents using Aspose.Words for .NET with this comprehensive guide. Master tracking changes, inserting shapes, and more.
weight: 10
url: /net/working-with-revisions/shape-revision/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Shape Revision

## Introduction

Editing Word documents programmatically can be a daunting task, especially when it comes to handling shapes. Whether you're creating reports, designing templates, or simply automating document creation, the ability to track and manage shape revisions is crucial. Aspose.Words for .NET offers a powerful API to make this process seamless and efficient. In this tutorial, we'll dive into the specifics of revising shapes in Word documents, ensuring you have the tools and knowledge to manage your documents with ease.

## Prerequisites

Before we dive into the code, let's ensure you have everything you need:

- Aspose.Words for .NET: Make sure you have the Aspose.Words library installed. You can [download it here](https://releases.aspose.com/words/net/).
- Development Environment: You should have a development environment set up, such as Visual Studio.
- Basic Understanding of C#: Familiarity with C# programming language and basic concepts of object-oriented programming.
- Word Document: A Word document to work with, or you can create one during the tutorial.

## Import Namespaces

First, let's import the necessary namespaces. These will provide us with access to the classes and methods required for handling Word documents and shapes.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Step 1: Setting Up Your Document Directory

Before we start working with shapes, we need to define the path to our document directory. This is where we'll save our modified documents.

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Step 2: Creating a New Document

Let's create a new Word document where we'll insert and revise shapes.

```csharp
Document doc = new Document();
```

## Step 3: Inserting an Inline Shape

We'll begin by inserting an inline shape into our document without tracking revisions. An inline shape is one that flows with the text.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Step 4: Starting to Track Revisions

To track changes in our document, we need to enable revision tracking. This is essential for identifying modifications made to shapes.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Step 5: Inserting Another Shape with Revisions

Now that revision tracking is enabled, let's insert another shape. This time, any changes will be tracked.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Step 6: Retrieving and Modifying Shapes

We can retrieve all shapes in the document and modify them as needed. Here, we'll get the shapes and remove the first one.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Step 7: Saving the Document

After making our changes, we need to save the document. This ensures all revisions and modifications are stored.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Step 8: Handling Shape Move Revisions

When a shape is moved, Aspose.Words tracks this as a revision. This means there will be two instances of the shape: one at its original location and one at its new location.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Conclusion

And there you have it! You've successfully learned how to handle shape revisions in Word documents using Aspose.Words for .NET. Whether you're managing document templates, automating reports, or simply keeping track of changes, these skills are invaluable. By following this step-by-step guide, you've not only mastered the basics but also gained insight into more advanced document handling techniques.

## FAQ's

### What is Aspose.Words for .NET?
Aspose.Words for .NET is a powerful library that allows developers to create, modify, and convert Word documents programmatically using C#.

### Can I track changes made to other elements in a Word document?
Yes, Aspose.Words for .NET supports tracking changes to various elements, including text, tables, and more.

### How can I get a free trial of Aspose.Words for .NET?
You can get a free trial of Aspose.Words for .NET [here](https://releases.aspose.com/).

### Is it possible to accept or reject revisions programmatically?
Yes, Aspose.Words for .NET provides methods to accept or reject revisions programmatically.

### Can I use Aspose.Words for .NET with other .NET languages besides C#?
Absolutely! Aspose.Words for .NET can be used with any .NET language, including VB.NET and F#.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
