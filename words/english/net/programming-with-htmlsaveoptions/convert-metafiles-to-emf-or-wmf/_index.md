---
title: Convert Metafiles To Emf Or Wmf
linktitle: Convert Metafiles To Emf Or Wmf
second_title: Aspose.Words Document Processing API
description: Step-by-step guide to converting metafiles to EMF or WMF formats when converting a document to HTML with Aspose.Words for .NET.
weight: 10
url: /net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert Metafiles To Emf Or Wmf

## Introduction

Welcome to another deep dive into the world of Aspose.Words for .NET. Today, we're tackling a neat trick: converting SVG images to EMF or WMF formats in your Word documents. This might sound a bit technical, but don't worry. By the end of this tutorial, you'll be a pro at it. Whether you're a seasoned developer or just getting started with Aspose.Words for .NET, this guide will walk you through everything you need to know, step by step.

## Prerequisites

Before we dive into the code, let's make sure we have everything set up. Here’s what you need:

1. Aspose.Words for .NET Library: Make sure you have the latest version. If you don’t have it, you can download it from [here](https://releases.aspose.com/words/net/).
2. .NET Framework: Ensure you have .NET Framework installed on your machine.
3. Development Environment: An IDE like Visual Studio will make your life easier.
4. Basic Knowledge of C#: You don’t need to be an expert, but a basic understanding will help.

Got everything? Great! Let’s get started.

## Import Namespaces

First things first, we need to import the necessary namespaces. This is crucial as it tells our program where to find the classes and methods we’ll be using.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

These namespaces cover everything from basic system functions to the specific Aspose.Words functionality we need for this tutorial.

## Step 1: Set Up Your Document Directory

Let's start by defining the path to your documents directory. This is where your Word document will be saved after we convert the metafiles.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path where you want to save your document.

## Step 2: Create the HTML String with SVG

Next, we need an HTML string that contains the SVG image we want to convert. Here's a simple example:

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg' width='500' height='40' viewBox='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

This HTML snippet includes a basic SVG that says "Hello world!".

## Step 3: Load HTML with ConvertSvgToEmf Option

Now, we use the `HtmlLoadOptions` to specify how we want to handle the SVG images in the HTML. Setting `ConvertSvgToEmf` to `true` ensures that SVG images are converted to EMF format.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

This code snippet creates a new `Document` object by loading the HTML string into it with the specified load options.

## Step 4: Set HtmlSaveOptions for Metafile Format

To save the document with the correct metafile format, we use `HtmlSaveOptions`. Here, we set `MetafileFormat` to `HtmlMetafileFormat.Png`, but you can change this to `Emf` or `Wmf` depending on your needs.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## Step 5: Save the Document

Finally, we save the document using the specified save options.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

This saves the document in the specified directory with the metafile format converted as defined.

## Conclusion

And there you have it! By following these steps, you’ve successfully converted SVG images to EMF or WMF formats in your Word documents using Aspose.Words for .NET. This method is handy for ensuring compatibility and maintaining the visual integrity of your documents across different platforms. Happy coding!

## FAQ's

### Can I convert other image formats using this method?
Yes, you can convert various image formats by adjusting the load and save options accordingly.

### Is it necessary to use a specific .NET Framework version?
Aspose.Words for .NET supports multiple .NET Framework versions, but it's always a good idea to use the latest version for the best compatibility and features.

### What is the advantage of converting SVG to EMF or WMF?
Converting SVG to EMF or WMF ensures that vector graphics are preserved and rendered correctly in environments that might not fully support SVG.

### Can I automate this process for multiple documents?
Absolutely! You can loop through multiple HTML files, applying the same process to automate the conversion for batch processing.

### Where can I find more resources and support for Aspose.Words for .NET?
You can find comprehensive documentation [here](https://reference.aspose.com/words/net/) and get support from the Aspose community [here](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
