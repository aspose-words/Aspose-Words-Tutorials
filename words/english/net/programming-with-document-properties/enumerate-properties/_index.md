---
title: Enumerate Properties
linktitle: Enumerate Properties
second_title: Aspose.Words Document Processing API
description: Learn how to enumerate properties in a Word document using Aspose.Words for .NET with this step-by-step guide. Perfect for developers of all skill levels.
weight: 10
url: /net/programming-with-document-properties/enumerate-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enumerate Properties

## Introduction

Looking to work with Word documents programmatically? Aspose.Words for .NET is a powerful tool that can help you achieve just that. Today, I'll walk you through how to enumerate properties of a Word document using Aspose.Words for .NET. Whether you're a beginner or have some experience, this guide will break it down step by step in a conversational and easy-to-follow manner.

## Prerequisites

Before we dive into the tutorial, there are a few things you'll need to get started:

- Aspose.Words for .NET: You can [download it here](https://releases.aspose.com/words/net/).
- Development Environment: Visual Studio is recommended, but you can use any C# IDE.
- Basic Knowledge of C#: A fundamental understanding of C# will help you follow along.

Now, let's jump right in!

## Step 1: Setting Up Your Project

First things first, you need to set up your project in Visual Studio.

1. Create a New Project: Open Visual Studio and create a new Console Application project.
2. Install Aspose.Words for .NET: Use NuGet Package Manager to install Aspose.Words for .NET. Right-click on your project in the Solution Explorer, select "Manage NuGet Packages," and search for "Aspose.Words". Install the package.

## Step 2: Import Namespaces

To work with Aspose.Words, you need to import the necessary namespaces. Add the following at the top of your Program.cs file:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Properties;
```

## Step 3: Load Your Document

Next, let's load the Word document you want to work with. For this example, we'll use a document named "Properties.docx" located in your project directory.

1. Define the Document Path: Specify the path to your document.
2. Load the Document: Use the Aspose.Words `Document` class to load the document.

Here's the code:

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

## Step 4: Display Document Name

Once your document is loaded, you might want to display its name. Aspose.Words provides a property for this:

```csharp
Console.WriteLine("1. Document name: {0}", doc.OriginalFileName);
```

## Step 5: Enumerate Built-in Properties

Built-in properties are metadata properties predefined by Microsoft Word. These include the title, author, and more.

1. Access Built-in Properties: Use the `BuiltInDocumentProperties` collection.
2. Loop Through Properties: Iterate through the properties and display their names and values.

Here's the code:

```csharp
Console.WriteLine("2. Built-in Properties");

foreach (DocumentProperty prop in doc.BuiltInDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## Step 6: Enumerate Custom Properties

Custom properties are user-defined metadata properties. These can be anything you want to add to your document.

1. Access Custom Properties: Use the `CustomDocumentProperties` collection.
2. Loop Through Properties: Iterate through the properties and display their names and values.

Here's the code:

```csharp
Console.WriteLine("3. Custom Properties");

foreach (DocumentProperty prop in doc.CustomDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## Conclusion

And there you have it! You've successfully enumerated both built-in and custom properties of a Word document using Aspose.Words for .NET. This is just the tip of the iceberg when it comes to what you can do with Aspose.Words. Whether you're automating document generation or manipulating complex documents, Aspose.Words provides a rich set of features to make your life easier.

## FAQ's

### Can I add new properties to a document?
Yes, you can add new custom properties using the `CustomDocumentProperties` collection.

### Is Aspose.Words free to use?
Aspose.Words offers a [free trial](https://releases.aspose.com/) and different [purchase options](https://purchase.aspose.com/buy).

### How do I get support for Aspose.Words?
You can get support from the Aspose community [here](https://forum.aspose.com/c/words/8).

### Can I use Aspose.Words with other .NET languages?
Yes, Aspose.Words supports multiple .NET languages including VB.NET.

### Where can I find more examples?
Check out the [Aspose.Words for .NET documentation](https://reference.aspose.com/words/net/) for more examples and detailed information.


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
