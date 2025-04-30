---
title: Get Revision Types Of Words
linktitle: Get Revision Types Of Words
second_title: Aspose.Words Document Processing API
description: Learn how to get revision types of words in a Word document using Aspose.Words for .NET. This step-by-step guide helps you handle document revisions efficiently.
weight: 10
url: /net/working-with-revisions/get-revision-types/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Get Revision Types Of Words

## Introduction

Ever found yourself knee-deep in a sea of document revisions, wondering who moved what and when? You're not alone. Handling document revisions can be a tedious task, especially when dealing with extensive documents. But, fret not! With Aspose.Words for .NET, you can easily identify and manage these revisions. In this guide, we'll walk you through a step-by-step process on how to get revision types of words in a Word document using Aspose.Words for .NET. So, buckle up, and let's dive in!

## Prerequisites

Before we get our hands dirty with some code, there are a few things you'll need:

1. Aspose.Words for .NET Library: If you haven't already, download it from [here](https://releases.aspose.com/words/net/).
2. Development Environment: Visual Studio or any other .NET compatible IDE.
3. Basic Knowledge of C#: Understanding of C# programming language will be beneficial.
4. A Word Document with Revisions: Ensure you have a `.docx` file with tracked changes to test the code.

## Import Namespaces

To get started, you'll need to import the necessary namespaces in your C# project. This will allow you to access the functionalities provided by Aspose.Words for .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

Let's break down the example into multiple steps for better understanding and implementation.

## Step 1: Set Up Your Document Directory

First things first, you need to define the path to your documents directory. This is where your Word document with revisions will be located.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path to your documents folder.

## Step 2: Load Your Word Document

Next, you need to load the Word document into your project. This document should have the revisions that you want to analyze.

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

Ensure that the file `Revisions.docx` exists in the specified directory.

## Step 3: Access the Paragraph Collection

Now that your document is loaded, you need to access the paragraphs within the first section of the document's body. This will help you iterate through each paragraph to check for revisions.

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## Step 4: Iterate Through Paragraphs and Check for Revisions

Here's where the magic happens. You'll iterate through each paragraph and check if it has been moved (deleted or inserted).

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

This loop goes through each paragraph and uses the `IsMoveFromRevision` and `IsMoveToRevision` properties to determine if the paragraph was moved (deleted) or moved (inserted).

## Conclusion

And there you have it! With just a few lines of code, you can easily identify the types of revisions in your Word document using Aspose.Words for .NET. This powerful library makes handling document revisions a breeze, allowing you to focus on more important tasks. 

## FAQ's

### Can I use Aspose.Words for .NET to track changes made by specific users?

Yes, Aspose.Words for .NET provides functionality to access revision details, including the author of the changes.

### Is there a free trial available for Aspose.Words for .NET?

Absolutely! You can get a free trial [here](https://releases.aspose.com/).

### How can I apply a temporary license for Aspose.Words for .NET?

You can request and apply a temporary license from [here](https://purchase.aspose.com/temporary-license/).

### Where can I find more detailed documentation for Aspose.Words for .NET?

Detailed documentation is available on the [Aspose website](https://reference.aspose.com/words/net/).

### Can I use Aspose.Words for .NET in a non-commercial project?

Yes, Aspose.Words for .NET can be used in both commercial and non-commercial projects, but make sure to check the licensing terms.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
