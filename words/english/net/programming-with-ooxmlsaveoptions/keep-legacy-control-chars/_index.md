---
title: Keep Legacy Control Chars
linktitle: Keep Legacy Control Chars
second_title: Aspose.Words Document Processing API
description: Learn how to preserve legacy control characters in Word documents using Aspose.Words for .NET with this step-by-step guide.
weight: 10
url: /net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Keep Legacy Control Chars

## Introduction

Ever been puzzled by those strange, invisible control characters in your Word documents? They're like tiny, hidden gremlins that can mess up formatting and functionality. Luckily, Aspose.Words for .NET provides a handy feature to keep these legacy control characters intact when saving documents. In this tutorial, we'll dive deep into how to manage these control characters using Aspose.Words for .NET. We'll break it down step-by-step, ensuring you grasp every detail along the way. Ready to get started? Let's dive in!

## Prerequisites

Before we start, make sure you have the following:

1. Aspose.Words for .NET: Download and install from [here](https://releases.aspose.com/words/net/).
2. A valid Aspose license: You can obtain a temporary license [here](https://purchase.aspose.com/temporary-license/).
3. Development Environment: Visual Studio or any other IDE that supports .NET.
4. Basic Knowledge of C#: Familiarity with C# programming language will be helpful.

## Import Namespaces

Before writing your code, you need to import the necessary namespaces. Add the following lines to the top of your C# file:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Step 1: Setting Up Your Project

First, you'll need to set up your project in Visual Studio (or your preferred IDE). 

1. Create a new C# project: Open Visual Studio and create a new C# Console Application project.
2. Install Aspose.Words for .NET: Use NuGet Package Manager to install Aspose.Words for .NET. Right-click on your project in Solution Explorer, select "Manage NuGet Packages," search for "Aspose.Words," and install it.

## Step 2: Load Your Document

Next, you'll load the Word document that contains the legacy control characters.

1. Specify the document path: Set the path to your document directory.
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2. Load the document: Use the `Document` class to load your document.

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## Step 3: Configure Save Options

Now, let's configure the save options to keep the legacy control characters intact.

1. Create Save Options: Initialize an instance of `OoxmlSaveOptions` and set the `KeepLegacyControlChars` property to `true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## Step 4: Save the Document

Finally, save the document with the configured save options.

1. Save the document: Use the `Save` method of the `Document` class to save the document with the specified save options.

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## Conclusion

And there you have it! By following these steps, you can ensure that your legacy control characters are preserved when working with Word documents in Aspose.Words for .NET. This feature can be a lifesaver, especially when dealing with complex documents where control characters play a crucial role. 

## FAQ's

### What are legacy control characters?

Legacy control characters are non-printing characters used in older documents to control formatting and layout.

### Can I remove these control characters instead of keeping them?

Yes, you can use Aspose.Words for .NET to remove or replace these characters if needed.

### Is this feature available in all versions of Aspose.Words for .NET?

This feature is available in recent versions. Make sure to use the latest version to access all functionalities.

### Do I need a license to use Aspose.Words for .NET?

Yes, you need a valid license. You can get a temporary license for evaluation purposes [here](https://purchase.aspose.com/temporary-license/).

### Where can I find more documentation on Aspose.Words for .NET?

You can find detailed documentation [here](https://reference.aspose.com/words/net/).
 


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
