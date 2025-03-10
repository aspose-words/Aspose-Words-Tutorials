---
title: Set Fonts Folders
linktitle: Set Fonts Folders
second_title: Aspose.Words Document Processing API
description: Learn how to set custom font folders in Aspose.Words for .NET with this comprehensive, step-by-step guide. Perfect for developers looking to enhance document fonts.
weight: 10
url: /net/working-with-fonts/set-fonts-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Set Fonts Folders

## Introduction

Hey there! Ready to dive into the world of custom fonts in Aspose.Words for .NET? Let's get started. This tutorial will guide you through the process of setting custom font folders, ensuring your documents look just the way you want them to. Whether you’re a seasoned developer or just starting, this guide will walk you through every step. So, let's get those fonts looking fabulous!

## Prerequisites

Before we jump in, let's make sure you have everything you need:

- Aspose.Words for .NET: You can [download](https://releases.aspose.com/words/net/) it if you haven't already.
- Visual Studio: Any version will work, but the latest is always the best.
- A Document: We'll be using a Word document for this tutorial. You can create your own or use an existing one.
- Custom Fonts: Have some custom fonts ready. We'll be using these to demonstrate how to set font folders.

## Import Namespaces

First things first, let's import the necessary namespaces. This is essential for accessing the classes and methods we need from Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

With these namespaces imported, we're ready to start setting up our custom font folders.

## Step 1: Define Your Document Directory

Let's start by defining the path to your document directory. This is where your Word document is stored. We'll be using a variable called `dataDir` to store this path.

```csharp
// Path to your document directory 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path to your directory. This is crucial because Aspose.Words will need to know where to find your document.

## Step 2: Set Font Sources

Next, we need to set up the font sources. This is where we tell Aspose.Words where to find our custom fonts. We're going to use the `FontSettings.DefaultInstance.SetFontsSources` method to achieve this.

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

Here’s what we’re doing:

- SystemFontSource: This tells Aspose.Words to use the system's default fonts.
- FolderFontSource: This is where we specify the folder containing our custom fonts. Replace `"C:\\MyFonts\\"` with the path to your custom fonts directory. The `true` parameter indicates that subdirectories should also be included.

## Step 3: Load Your Document

Now that we’ve set up our font sources, it’s time to load the document we want to work with. We'll use the `Document` class from Aspose.Words for this.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Ensure that `"Rendering.docx"` is the name of your Word document. If your document has a different name, make sure to update this accordingly.

## Step 4: Save Your Document as PDF

Finally, let's save our document as a PDF to see the custom fonts in action. We'll use the `Save` method of the `Document` class.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

This will save your document as a PDF in the specified directory, using the custom fonts we set up earlier.

## Conclusion

And there you have it! You've successfully set up custom font folders in Aspose.Words for .NET and saved your document as a PDF with those custom fonts. Pretty cool, right? Customizing fonts can make a huge difference in the appearance of your documents, and now you know exactly how to do it. Happy coding!

## FAQ's

### How do I install Aspose.Words for .NET?

You can [download](https://releases.aspose.com/words/net/) the latest version of Aspose.Words for .NET from the website.

### Can I use multiple custom font folders?

Yes, you can add multiple `FolderFontSource` instances to the `SetFontsSources` method to use fonts from different directories.

### Is it necessary to include system fonts?

Including system fonts is optional but recommended to ensure all standard fonts are available.

### What file types are supported by Aspose.Words?

Aspose.Words supports a wide range of file formats, including DOCX, DOC, PDF, TXT, HTML, and many more.

### How can I get a temporary license for Aspose.Words?

You can obtain a [temporary license](https://purchase.aspose.com/temporary-license/) from the Aspose website to try out the full features of Aspose.Words.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
