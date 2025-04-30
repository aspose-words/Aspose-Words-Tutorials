---
title: Set Fonts Folders With Priority
linktitle: Set Fonts Folders With Priority
second_title: Aspose.Words Document Processing API
description: Learn how to set font folders with priority in Word documents using Aspose.Words for .NET. Our guide ensures your documents render perfectly every time.
weight: 10
url: /net/working-with-fonts/set-fonts-folders-with-priority/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Set Fonts Folders With Priority

## Introduction

In the world of document manipulation, setting custom font folders can make a world of difference in ensuring your documents render perfectly, no matter where they are viewed. Today, we’ll dive into how you can set font folders with priority in your Word documents using Aspose.Words for .NET. This comprehensive guide will walk you through each step, making the process as smooth as possible.

## Prerequisites

Before we get started, let's make sure we have everything we need. Here’s a quick checklist:

- Aspose.Words for .NET: You need to have this library installed. If you don’t have it yet, you can [download it here](https://releases.aspose.com/words/net/).
- Development Environment: Ensure you have a working .NET development environment, like Visual Studio.
- Document Directory: Make sure you have a directory for your documents. For our examples, we'll use `"YOUR DOCUMENT DIRECTORY"` as a placeholder for this path.

## Import Namespaces

First things first, we need to import the necessary namespaces. These namespaces are essential for accessing the classes and methods provided by Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Now, let's break down each step to set font folders with priority.

## Step 1: Set Up Your Font Sources

To begin, you'll want to define the font sources. This is where you tell Aspose.Words where to look for fonts. You can specify multiple font folders and even set their priority.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

In this example, we are setting two font sources:
- SystemFontSource: This is the default font source that includes all the fonts installed on your system.
- FolderFontSource: This is a custom font folder located at `C:\\MyFonts\\`. The `true` parameter specifies that this folder should be scanned recursively, and `1` sets its priority.

## Step 2: Load Your Document

Next, load the document you want to work with. Make sure the document is located in your specified directory.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

This line of code loads a document named `Rendering.docx` from your document directory.

## Step 3: Save Your Document with the New Font Settings

Finally, save your document. When you save the document, Aspose.Words will use the font settings you specified.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

This saves the document as a PDF in your document directory with the name `WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## Conclusion

And there you have it! You've successfully set up font folders with priority using Aspose.Words for .NET. By specifying custom font folders and priorities, you can ensure your documents render consistently, regardless of where they are viewed. This is especially useful in environments where specific fonts are not installed by default.

## FAQ's

### Why would I need to set custom font folders?
Setting custom font folders ensures that your documents render correctly, even if they use fonts not installed on the system where they are being viewed.

### Can I set multiple custom font folders?
Yes, you can specify multiple font folders. Aspose.Words allows you to set the priority for each folder, ensuring that the most important fonts are found first.

### What happens if a font is missing from all specified sources?
If a font is missing from all specified sources, Aspose.Words will use a fallback font to ensure the document is still readable.

### Can I change the priority of the system fonts?
The system fonts are always included by default, but you can set their priority relative to your custom font folders.

### Is it possible to use network paths for custom font folders?
Yes, you can specify network paths as custom font folders, allowing you to centralize font resources on a network location.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
