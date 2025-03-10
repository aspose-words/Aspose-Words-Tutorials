---
title: Restart List Number
linktitle: Restart List Number
second_title: Aspose.Words Document Processing API
description: Learn how to restart list numbers in Word documents using Aspose.Words for .NET. This detailed, 2000-word guide covers everything you need to know, from setup to advanced customization.
weight: 10
url: /net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Restart List Number

## Introduction

Are you looking to master the art of list manipulation in your Word documents using Aspose.Words for .NET? Well, you're in the right place! In this tutorial, we're going to dive deep into restarting list numbers, a nifty feature that will take your document automation skills to the next level. Buckle up, and let's get started!

## Prerequisites

Before we jump into the code, let's make sure you have everything you need:

1. Aspose.Words for .NET: You need to have Aspose.Words for .NET installed. If you haven't installed it yet, you can [download it here](https://releases.aspose.com/words/net/).
2. Development Environment: Ensure you have a suitable development environment like Visual Studio.
3. Basic Knowledge of C#: A basic understanding of C# will help you follow along with the tutorial.

## Import Namespaces

First things first, let's import the necessary namespaces. These are crucial for accessing the Aspose.Words features.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Now, let's break down the process into easy-to-follow steps. We'll cover everything from creating a list to restarting its numbering.

## Step 1: Set Up Your Document and Builder

Before you can start manipulating lists, you need a document and a DocumentBuilder. The DocumentBuilder is your go-to tool for adding content to your document.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Step 2: Create and Customize Your First List

Next, we'll create a list based on a template and customize its appearance. In this example, we're using the Arabic number format with parentheses.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Here, we've set the font color to red and aligned the text to the right.

## Step 3: Add Items to Your First List

With your list ready, it's time to add some items. The DocumentBuilder's `ListFormat.List` property helps in applying the list format to the text.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Step 4: Restart List Numbering

To reuse the list and restart its numbering, you need to create a copy of the original list. This allows you to modify the new list independently.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

In this example, the new list starts at number 10.

## Step 5: Add Items to the New List

Just like before, add items to your new list. This demonstrates the list restarting at the specified number.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Step 6: Save Your Document

Finally, save your document to your specified directory.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Conclusion

Restarting list numbers in Word documents using Aspose.Words for .NET is straightforward and incredibly useful. Whether you're generating reports, creating structured documents, or just need better control over your lists, this technique has you covered.

## FAQ's

### Can I use other list templates besides NumberArabicParenthesis?

Absolutely! Aspose.Words offers various list templates such as bullets, letters, Roman numerals, and more. You can choose the one that best fits your needs.

### How do I change the list level?

You can change the list level by modifying the `ListLevels` property. For example, `list1.ListLevels[1]` would refer to the second level of the list.

### Can I restart numbering at any number?

Yes, you can set the starting number to any integer value using the `StartAt` property of the list level.

### Is it possible to have different formatting for different list levels?

Indeed! Each list level can have its own formatting settings, such as font, alignment, and numbering style.

### What if I want to continue numbering from a previous list instead of restarting?

If you want to continue numbering, you don't need to create a copy of the list. Simply continue adding items to the original list.




{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
