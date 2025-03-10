---
title: Move Node In Tracked Document
linktitle: Move Node In Tracked Document
second_title: Aspose.Words Document Processing API
description: Learn how to move nodes in a tracked Word document using Aspose.Words for .NET with our detailed, step-by-step guide. Perfect for developers.
weight: 10
url: /net/working-with-revisions/move-node-in-tracked-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Move Node In Tracked Document

## Introduction

Hey there, Aspose.Words enthusiasts! If you've ever needed to move a node in a Word document while tracking revisions, you're in the right place. Today, we're diving into how to achieve this using Aspose.Words for .NET. Not only will you learn the step-by-step process, but you'll also pick up some tips and tricks to make your document manipulation smooth and efficient.

## Prerequisites

Before we get our hands dirty with some code, let's make sure you've got everything you need:

- Aspose.Words for .NET: Download it [here](https://releases.aspose.com/words/net/).
- .NET Environment: Ensure you have a compatible .NET development environment set up.
- Basic C# Knowledge: This tutorial assumes you have a basic understanding of C#.

Got everything? Great! Let's move on to the namespaces we need to import.

## Import Namespaces

First things first, we need to import the necessary namespaces. These are essential for working with Aspose.Words and handling document nodes.

```csharp
using Aspose.Words;
using System;
```

Alright, let's break down the process into manageable steps. Each step will be explained in detail to ensure you understand what’s happening at every point.

## Step 1: Initialize the Document

To begin, we need to initialize a new document and use a `DocumentBuilder` to add some paragraphs.

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Adding some paragraphs
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// Check the initial paragraph count
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Step 2: Start Tracking Revisions

Next, we need to start tracking revisions. This is crucial as it allows us to see the changes made to the document.

```csharp
// Start tracking revisions
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## Step 3: Move Nodes

Now comes the core part of our task: moving a node from one location to another. We'll be moving the third paragraph and placing it before the first paragraph.

```csharp
// Define the node to be moved and its end range
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// Move the nodes within the defined range
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## Step 4: Stop Tracking Revisions

Once we’ve moved the nodes, we need to stop tracking revisions.

```csharp
// Stop tracking revisions
doc.StopTrackRevisions();
```

## Step 5: Save the Document

Finally, let's save our modified document to the specified directory.

```csharp
// Save the modified document
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// Output the final paragraph count
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Conclusion

And there you have it! You've successfully moved a node in a tracked document using Aspose.Words for .NET. This powerful library makes it easy to manipulate Word documents programmatically. Whether you're creating, editing, or tracking changes, Aspose.Words has got you covered. So, go ahead and give it a try. Happy coding!

## FAQ's

### What is Aspose.Words for .NET?

Aspose.Words for .NET is a class library for working with Word documents programmatically. It allows developers to create, edit, convert, and print Word documents within .NET applications.

### How do I track revisions in a Word document using Aspose.Words?

To track revisions, use the `StartTrackRevisions` method on the `Document` object. This will enable revision tracking, showing any changes made to the document.

### Can I move multiple nodes in Aspose.Words?

Yes, you can move multiple nodes by iterating over them and using methods like `InsertBefore` or `InsertAfter` to place them at the desired location.

### How do I stop tracking revisions in Aspose.Words?

Use the `StopTrackRevisions` method on the `Document` object to stop tracking revisions.

### Where can I find more documentation on Aspose.Words for .NET?

You can find detailed documentation [here](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
