---
title: Insert TOA Field Without Document Builder
linktitle: Insert TOA Field Without Document Builder
second_title: Aspose.Words Document Processing API
description: Learn how to insert a TOA field without using a document builder in Aspose.Words for .NET. Follow our step-by-step guide to efficiently manage legal citations.
weight: 10
url: /net/working-with-fields/insert-toafield-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert TOA Field Without Document Builder

## Introduction

Creating a Table of Authorities (TOA) field in a Word document can feel like piecing together a complex puzzle. However, with the help of Aspose.Words for .NET, the process becomes smooth and straightforward. In this article, we'll guide you through the steps to insert a TOA field without using a document builder, making it easy for you to manage your citations and legal references within your Word documents.

## Prerequisites

Before diving into the tutorial, let's cover the essentials you'll need:

- Aspose.Words for .NET: Ensure you have the latest version installed. You can download it from the [Aspose website](https://releases.aspose.com/words/net/).
- Development Environment: A .NET-compatible IDE like Visual Studio.
- Basic C# Knowledge: Understanding basic C# syntax and concepts will be helpful.
- Sample Word Document: Create or have a sample document ready where you want to insert the TOA field.

## Import Namespaces

To get started, you'll need to import the necessary namespaces from the Aspose.Words library. This setup ensures that you have access to all the classes and methods required for document manipulation.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Let's break down the process into simple, easy-to-follow steps. We'll guide you through each stage, explaining what each piece of code does and how it contributes to creating the TOA field.

## Step 1: Initialize the Document

First, you need to create an instance of the `Document` class. This object represents the Word document you're working on.

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

This code initializes a new Word document. You can think of it as creating a blank canvas to which you'll add your content.

## Step 2: Create and Configure the TA Field

Next, we'll add a TA (Table of Authorities) field. This field marks the entries that will appear in the TOA.

```csharp
Paragraph para = new Paragraph(doc);

// We want to insert TA and TOA fields like this:
// { TA \c 1 \l "Value 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Here's a breakdown:
- Paragraph para = new Paragraph(doc);: Creates a new paragraph within the document.
- FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: Adds a TA field to the paragraph. The `FieldType.FieldTOAEntry` specifies that this is a TOA entry field.
- fieldTA.EntryCategory = "1";: Sets the entry category. This is useful for categorizing different types of entries.
- fieldTA.LongCitation = "Value 0";: Specifies the long citation text. This is the text that will appear in the TOA.
- doc.FirstSection.Body.AppendChild(para);: Appends the paragraph with the TA field to the document's body.

## Step 3: Add the TOA Field

Now, we'll insert the actual TOA field that compiles all the TA entries into a table.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

In this step:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: Adds a TOA field to the paragraph.
- fieldToa.EntryCategory = "1";: Filters the entries to include only those marked with category "1".

## Step 4: Update the TOA Field

After inserting the TOA field, you need to update it to ensure it reflects the latest entries.

```csharp
fieldToa.Update();
```

This command refreshes the TOA field, ensuring that all marked entries are correctly displayed in the table.

## Step 5: Save the Document

Finally, save your document with the newly added TOA field.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

This line of code saves the document to the specified directory. Make sure to replace `"YOUR DOCUMENT DIRECTORY"` with the actual path where you want to save your file.

## Conclusion

And there you have it! You've successfully added a TOA field to a Word document without using a document builder. By following these steps, you can efficiently manage citations and create comprehensive tables of authorities in your legal documents. Aspose.Words for .NET makes this process smooth and efficient, giving you the tools to handle complex document tasks with ease.

## FAQ's

### Can I add multiple TA fields with different categories?
Yes, you can add multiple TA fields with different categories by setting the `EntryCategory` property accordingly.

### How can I customize the appearance of the TOA?
You can customize the TOA's appearance by modifying the TOA field's properties, such as entry formatting and category labels.

### Is it possible to update the TOA field automatically?
While you can manually update the TOA field using the `Update` method, Aspose.Words doesn't currently support automatic updates on document changes.

### Can I add TA fields programmatically in specific parts of the document?
Yes, you can add TA fields at specific locations by inserting them into the desired paragraphs or sections.

### How do I handle multiple TOA fields in a single document?
You can manage multiple TOA fields by assigning different `EntryCategory` values and ensuring each TOA field filters entries based on its category.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
