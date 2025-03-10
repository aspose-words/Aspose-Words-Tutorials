---
title: Add Custom Document Properties
linktitle: Add Custom Document Properties
second_title: Aspose.Words Document Processing API
description: Learn how to add custom document properties in Word files using Aspose.Words for .NET. Follow our step-by-step guide to enhance your documents with additional metadata.
weight: 10
url: /net/programming-with-document-properties/add-custom-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Add Custom Document Properties

## Introduction

Hey there! Are you diving into the world of Aspose.Words for .NET and wondering how to add custom document properties to your Word files? Well, you’ve come to the right place! Custom properties can be incredibly useful for storing additional metadata that isn't covered by built-in properties. Whether it’s authorizing a document, adding a revision number, or even inserting specific dates, custom properties have got you covered. In this tutorial, we’ll walk you through the steps to seamlessly add these properties using Aspose.Words for .NET. Ready to get started? Let’s dive in!

## Prerequisites

Before we jump into the code, let’s make sure you’ve got everything you need:

1. Aspose.Words for .NET Library: Make sure you have the Aspose.Words for .NET library. You can download it [here](https://releases.aspose.com/words/net/).
2. Development Environment: An IDE like Visual Studio.
3. Basic Knowledge of C#: This tutorial assumes you have a basic understanding of C# and .NET.
4. Sample Document: Have a sample Word document ready, named `Properties.docx`, which you will modify.

## Import Namespaces

Before we can start coding, we need to import the necessary namespaces. This is a crucial step to ensure that your code has access to all the functionalities provided by Aspose.Words.

```csharp
using System;
using Aspose.Words;
```

## Step 1: Setting Up the Document Path

First things first, we need to set up the path to our document. This is where we’ll specify the location of our `Properties.docx` file.

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

In this snippet, replace `"YOUR DOCUMENT DIRECTORY"` with the actual path to your document. This step is crucial as it allows the program to locate and open your Word file.

## Step 2: Accessing Custom Document Properties

Next, let’s access the custom document properties of the Word document. This is where all your custom metadata will be stored.

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

By doing this, we get a handle on the custom properties collection, which we’ll be working with in the following steps.

## Step 3: Checking for Existing Properties

Before adding new properties, it’s a good idea to check if a particular property already exists. This avoids any unnecessary duplication.

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

This line checks if the property "Authorized" already exists. If it does, the program will exit the method early to prevent adding duplicate properties.

## Step 4: Adding a Boolean Property

Now, let’s add our first custom property—a boolean value to indicate if the document is authorized.

```csharp
customDocumentProperties.Add("Authorized", true);
```

This line adds a custom property named "Authorized" with a value of `true`. Simple and straightforward!

## Step 5: Adding a String Property

Next, we’ll add another custom property to specify who authorized the document.

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

Here, we’re adding a property called "Authorized By" with the value "John Smith". Feel free to replace "John Smith" with any other name you prefer.

## Step 6: Adding a Date Property

Let’s add a property to store the authorization date. This helps in keeping track of when the document was authorized.

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

This snippet adds a property named "Authorized Date" with the current date as its value. The `DateTime.Today` property automatically fetches today’s date.

## Step 7: Adding a Revision Number

We can also add a property to keep track of the document’s revision number. This is particularly useful for version control.

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

Here, we’re adding a property called "Authorized Revision" and assigning it the document’s current revision number.

## Step 8: Adding a Numeric Property

Lastly, let’s add a numeric property to store an authorized amount. This could be anything from a budget figure to a transaction amount.

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

This line adds a property named "Authorized Amount" with a value of `123.45`. Again, feel free to replace this with any number that suits your needs.

## Conclusion

And there you have it! You’ve successfully added custom document properties to a Word document using Aspose.Words for .NET. These properties can be incredibly useful for storing additional metadata that’s specific to your needs. Whether you’re tracking authorization details, revision numbers, or specific amounts, custom properties provide a flexible solution.

Remember, the key to mastering Aspose.Words for .NET is practice. So, keep experimenting with different properties and see how they can enhance your documents. Happy coding!

## FAQ's

### What are custom document properties?
Custom document properties are metadata that you can add to a Word document to store additional information that isn’t covered by built-in properties.

### Can I add properties other than strings and numbers?
Yes, you can add various types of properties, including boolean, date, and even custom objects.

### How can I access these properties in a Word document?
Custom properties can be accessed programmatically using Aspose.Words or viewed directly in Word through the document properties.

### Is it possible to edit or delete custom properties?
Yes, you can easily edit or delete custom properties using similar methods provided by Aspose.Words.

### Can custom properties be used for filtering documents?
Absolutely! Custom properties are excellent for categorizing and filtering documents based on specific metadata.


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
