---
title: Export Resources
linktitle: Export Resources
second_title: Aspose.Words Document Processing API
description: Learn how to export resources like CSS and fonts while saving Word documents as HTML using Aspose.Words for .NET. Follow our step-by-step guide.
weight: 10
url: /net/programming-with-htmlsaveoptions/export-resources/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Export Resources

## Introduction

Hey there, fellow tech enthusiast! If you've ever found yourself needing to convert Word documents to HTML, you're in the right place. Today, we're diving into the wonderful world of Aspose.Words for .NET. This powerful library makes it a breeze to work with Word documents programmatically. In this tutorial, we'll walk through the steps to export resources, such as fonts and CSS, when saving a Word document as HTML using Aspose.Words for .NET. Buckle up for a fun, informative ride!

## Prerequisites

Before we dive into the code, let's make sure you've got everything you need to get started. Here's a quick checklist:

1. Visual Studio: Ensure you have Visual Studio installed on your machine. You can download it from the [Visual Studio website](https://visualstudio.microsoft.com/).
2. Aspose.Words for .NET: You'll need the Aspose.Words for .NET library. If you haven't got it yet, grab a free trial from [Aspose Releases](https://releases.aspose.com/words/net/) or purchase it from the [Aspose Store](https://purchase.aspose.com/buy).
3. Basic Knowledge of C#: A fundamental understanding of C# will help you follow along with the code examples.

Got all that? Great! Let's move on to importing the necessary namespaces.

## Import Namespaces

To use Aspose.Words for .NET, you need to include the relevant namespaces in your project. Here's how you do it:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

These namespaces are crucial for accessing the Aspose.Words classes and methods we'll be using in our tutorial.

Let's break down the process of exporting resources when saving a Word document as HTML. We'll take it step by step, so it's easy to follow.

## Step 1: Set Up Your Document Directory

First things first, you need to specify the path to your documents directory. This is where your Word document is located and where the HTML file will be saved.

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path to your directory.

## Step 2: Load the Word Document

Next, let's load the Word document you want to convert to HTML. For this tutorial, we'll use a document named `Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

This line of code loads the document from the specified directory.

## Step 3: Configure HTML Save Options

To export resources such as CSS and fonts, you need to configure the `HtmlSaveOptions`. This step is crucial for ensuring your HTML output is well-structured and includes the necessary resources.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/resources"
};
```

Let's break down what each option does:
- `CssStyleSheetType = CssStyleSheetType.External`: This option specifies that CSS styles should be saved in an external stylesheet.
- `ExportFontResources = true`: This enables the export of font resources.
- `ResourceFolder = dataDir + "Resources"`: Specifies the local folder where resources (like fonts and CSS files) will be saved.
- `ResourceFolderAlias = "http://example.com/resources"`: Sets an alias for the resource folder, which will be used in the HTML file.

## Step 4: Save the Document as HTML

With the save options configured, the final step is to save the document as an HTML file. Here's how you do it:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

This line of code saves the document in HTML format, along with the exported resources.

## Conclusion

And there you have it! You've successfully exported resources while saving a Word document as HTML using Aspose.Words for .NET. With this powerful library, handling Word documents programmatically becomes a piece of cake. Whether you're working on a web application or just need to convert documents for offline use, Aspose.Words has got you covered.

## FAQ's

### Can I export images along with fonts and CSS?
Yes, you can! Aspose.Words for .NET supports exporting images as well. Just make sure to configure the `HtmlSaveOptions` accordingly.

### Is there a way to embed CSS instead of using an external stylesheet?
Absolutely. You can set `CssStyleSheetType` to `CssStyleSheetType.Embedded` if you prefer embedded styles.

### How can I customize the output HTML file's name?
You can specify any file name you like in the `doc.Save` method. For example, `doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Does Aspose.Words support other formats besides HTML?
Yes, it supports various formats including PDF, DOCX, TXT, and more. Check out the [documentation](https://reference.aspose.com/words/net/) for a full list.

### Where can I get more support and resources?
For more help, visit the [Aspose.Words Support Forum](https://forum.aspose.com/c/words/8). You can also find detailed documentation and examples on the [Aspose website](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
