---
title: Ordered List
linktitle: Ordered List
second_title: Aspose.Words Document Processing API
description: Learn how to create ordered lists in Word documents using Aspose.Words for .NET with our step-by-step guide. Perfect for automating document creation.
weight: 10
url: /net/working-with-markdown/ordered-list/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ordered List

## Introduction

So, you've decided to dive into Aspose.Words for .NET to create amazing Word documents programmatically. Fantastic choice! Today, we're going to break down how to create an ordered list in a Word document. We'll take it step by step, so whether you're a coding newbie or a seasoned pro, you'll find this guide super helpful. Let's get started!

## Prerequisites

Before we dive into the code, there are a few things you'll need:

1. Aspose.Words for .NET: Make sure you have Aspose.Words for .NET installed. If you don't, you can download it [here](https://releases.aspose.com/words/net/).
2. Development Environment: Visual Studio or any other .NET compatible IDE.
3. Basic Knowledge of C#: You should be comfortable with C# basics to follow along easily.

## Import Namespaces

To use Aspose.Words in your project, you need to import the necessary namespaces. This is like setting up your toolbox before you start working.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

Let's break down the code into bite-sized steps and explain each part. Ready? Here we go!

## Step 1: Initialize the Document

First things first, you need to create a new document. Think of this as opening a blank Word document on your computer.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Here, we're initializing a new document and a DocumentBuilder object. The DocumentBuilder is like your pen, allowing you to write content into the document.

## Step 2: Apply Numbered List Format

Now, let's apply a default numbered list format. This is like setting your Word document to use numbered bullets.

```csharp
builder.ListFormat.ApplyNumberDefault();
```

This line of code sets up the numbering for your list. Easy, right?

## Step 3: Add List Items

Next, let's add some items to our list. Imagine you're jotting down a grocery list.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

With these lines, you're adding the first two items to your list.

## Step 4: Indent the List

What if you want to add sub-items under an item? Let's do that!

```csharp
builder.ListFormat.ListIndent();

builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
```

The `ListIndent` method indents the list, creating a sub-list. You're now creating a hierarchical list, much like a nested to-do list.

## Conclusion

Creating an ordered list in a Word document programmatically can seem daunting at first, but with Aspose.Words for .NET, it's a breeze. By following these simple steps, you can easily add and manage lists in your documents. Whether you're generating reports, creating structured documents, or just automating your workflows, Aspose.Words for .NET has got you covered. So, why wait? Start coding and see the magic unfold!

## FAQ's

### Can I customize the numbering style of the list?  
Yes, you can customize the numbering style using the `ListFormat` properties. You can set different numbering styles like Roman numerals, letters, etc.

### How do I add more levels of indentation?  
You can use the `ListIndent` method multiple times to create deeper levels of sub-lists. Each call to `ListIndent` adds one level of indentation.

### Can I mix bullet points and numbered lists?  
Absolutely! You can apply different list formats within the same document using the `ListFormat` property.

### Is it possible to continue numbering from a previous list?  
Yes, you can continue numbering by using the same list format. Aspose.Words allows you to control list numbering across different paragraphs.

### How can I remove the list format?  
You can remove the list format by calling `ListFormat.RemoveNumbers()`. This will turn the list items back into regular paragraphs.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
