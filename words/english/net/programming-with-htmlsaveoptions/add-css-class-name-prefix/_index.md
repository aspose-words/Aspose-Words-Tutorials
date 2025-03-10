---
title: Add Css Class Name Prefix
linktitle: Add Css Class Name Prefix
second_title: Aspose.Words Document Processing API
description: Learn how to add a CSS class name prefix when saving Word documents as HTML using Aspose.Words for .NET. Step-by-step guide, code snippets, and FAQs included.
weight: 10
url: /net/programming-with-htmlsaveoptions/add-css-class-name-prefix/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Add Css Class Name Prefix

## Introduction

Welcome! If you're diving into the world of Aspose.Words for .NET, you're in for a treat. Today, we’ll explore how to add a CSS class name prefix when saving a Word document as HTML using Aspose.Words for .NET. This feature is super handy when you want to avoid class name conflicts in your HTML files.

## Prerequisites

Before we get started, make sure you have the following:

- Aspose.Words for .NET: If you haven’t installed it yet, [download it here](https://releases.aspose.com/words/net/).
- Development Environment: Visual Studio or any other C# IDE.
- A Word Document: We'll be using a document named `Rendering.docx`. Place it in your project directory.

## Import Namespaces

First, ensure you have the necessary namespaces imported into your C# project. Add these at the top of your code file:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Now, let's dive into the step-by-step guide!

## Step 1: Set Up Your Project

Before we can start adding a CSS class name prefix, let's set up our project.

### Step 1.1: Create a New Project

Fire up your Visual Studio and create a new Console App project. Name it something catchy like `AsposeCssPrefixExample`.

### Step 1.2: Add Aspose.Words for .NET

If you haven’t already, add Aspose.Words for .NET to your project via NuGet. Simply open the NuGet Package Manager Console and run:

```bash
Install-Package Aspose.Words
```

Great! Now, we’re ready to start coding.

## Step 2: Load Your Document

The first thing we need to do is load the Word document we want to convert to HTML.

### Step 2.1: Define the Document Path

Set up the path to your document directory. For the sake of this tutorial, let's assume your document is in a folder named `Documents` within your project directory.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Step 2.2: Load the Document

Now, let's load the document using Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Step 3: Configure HTML Save Options

Next, we need to configure the HTML save options to include a CSS class name prefix.

### Step 3.1: Create HTML Save Options

Instantiate the `HtmlSaveOptions` object and set the CSS style sheet type to `External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Step 3.2: Set CSS Class Name Prefix

Now, let’s set the `CssClassNamePrefix` property to your desired prefix. For this example, we'll use `"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Step 4: Save the Document as HTML

Finally, let's save the document as an HTML file with our configured options.


Specify the output HTML file path and save the document.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Step 5: Verify the Output

After running your project, navigate to your `Documents` folder. You should find an HTML file named `WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`. Open this file in a text editor or browser to verify that the CSS classes have the prefix `pfx_`.

## Conclusion

And there you have it! By following these steps, you've successfully added a CSS class name prefix to your HTML output using Aspose.Words for .NET. This simple yet powerful feature can help you maintain clean and conflict-free styles in your HTML documents.

## FAQ's

### Can I use a different prefix for each save operation?
Yes, you can customize the prefix each time you save a document by changing the `CssClassNamePrefix` property.

### Does this method support inline CSS?
The `CssClassNamePrefix` property works with external CSS. For inline CSS, you'll need a different approach.

### How can I include other HTML save options?
You can configure various properties of `HtmlSaveOptions` to customize your HTML output. Check the [documentation](https://reference.aspose.com/words/net/) for more details.

### Is it possible to save the HTML to a stream?
Absolutely! You can save the document to a stream by passing the stream object to the `Save` method.

### How do I get support if I run into issues?
You can get support from the [Aspose forum](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
