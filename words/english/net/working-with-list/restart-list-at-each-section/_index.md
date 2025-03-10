---
title: Restart List At Each Section
linktitle: Restart List At Each Section
second_title: Aspose.Words Document Processing API
description: Learn how to restart lists at each section in Word documents using Aspose.Words for .NET. Follow our detailed step-by-step guide to manage lists effectively.
weight: 10
url: /net/working-with-list/restart-list-at-each-section/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Restart List At Each Section

## Introduction

Creating structured and well-organized documents can sometimes feel like solving a complex puzzle. One piece of that puzzle is managing lists effectively, especially when you want them to restart at each section. With Aspose.Words for .NET, you can accomplish this seamlessly. Let's dive into how you can restart lists at each section in your Word documents using Aspose.Words for .NET.

## Prerequisites

Before we get started, make sure you have the following:

1. Aspose.Words for .NET: Download and install the latest version from the [Aspose Releases](https://releases.aspose.com/words/net/) page.
2. .NET Environment: Set up your development environment with .NET installed.
3. Basic Understanding of C#: Familiarity with C# programming language is recommended.
4. Aspose License: You can opt for a [temporary license](https://purchase.aspose.com/temporary-license/) if you don't have one.

## Import Namespaces

Before writing the code, ensure you import the necessary namespaces:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Now, let's break down the process into multiple steps to make it easy to follow.

## Step 1: Initialize the Document

First, you'll need to create a new document instance.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
```

## Step 2: Add a Numbered List

Next, add a numbered list to the document. This list will follow a default numbering format.

```csharp
doc.Lists.Add(ListTemplate.NumberDefault);
```

## Step 3: Access the List and Set Restart Property

Retrieve the list you just created and set its `IsRestartAtEachSection` property to `true`. This ensures the list restarts numbering at each new section.

```csharp
List list = doc.Lists[0];
list.IsRestartAtEachSection = true;
```

## Step 4: Create a Document Builder and Associate the List

Create a `DocumentBuilder` to insert content into the document and associate it with the list.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.ListFormat.List = list;
```

## Step 5: Add List Items and Insert Section Break

Now, add items to the list. To illustrate the restart functionality, we'll insert a section break after a certain number of items.

```csharp
for (int i = 1; i < 45; i++)
{
    builder.Writeln($"List item {i}");

    if (i == 15)
        builder.InsertBreak(BreakType.SectionBreakNewPage);
}
```

## Step 6: Save the Document

Finally, save the document with the appropriate options to ensure compliance.

```csharp
OoxmlSaveOptions options = new OoxmlSaveOptions { Compliance = OoxmlCompliance.Iso29500_2008_Transitional };
doc.Save(dataDir + "WorkingWithList.RestartListAtEachSection.docx", options);		
```

## Conclusion

And there you have it! By following these steps, you can effortlessly restart lists at each section in your Word documents using Aspose.Words for .NET. This feature is incredibly useful for creating well-structured documents that require separate sections with their own list numbering. With Aspose.Words, handling such tasks becomes a breeze, allowing you to focus on crafting high-quality content.

## FAQ's

### Can I restart lists at each section for different list types?
Yes, Aspose.Words for .NET allows you to restart various list types, including bullet and numbered lists.

### What if I want to customize the numbering format?
You can customize the numbering format by modifying the `ListTemplate` property when creating the list.

### Is there a limit to the number of items in a list?
No, there is no specific limit to the number of items you can have in a list using Aspose.Words for .NET.

### Can I use this feature in other document formats like PDF?
Yes, you can use Aspose.Words to convert Word documents to other formats like PDF while retaining the list structure.

### How can I get a free trial of Aspose.Words for .NET?
You can get a free trial from the [Aspose Releases](https://releases.aspose.com/) page.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
