---
title: Specify Default Font When Rendering
linktitle: Specify Default Font When Rendering
second_title: Aspose.Words Document Processing API
description: Learn how to specify a default font when rendering Word documents using Aspose.Words for .NET. Ensure consistent document appearance across platforms.
weight: 10
url: /net/working-with-fonts/specify-default-font-when-rendering/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Specify Default Font When Rendering

## Introduction

Ensuring your Word documents render correctly across different platforms can be a challenge, especially when dealing with font compatibility. One way to maintain consistent appearance is by specifying a default font when rendering your documents to PDF or other formats. In this tutorial, we'll explore how to set a default font using Aspose.Words for .NET, so your documents look great no matter where they're viewed.

## Prerequisites

Before diving into the code, let's cover what you'll need to follow along with this tutorial:

- Aspose.Words for .NET: Ensure you have the latest version installed. You can download it [here](https://releases.aspose.com/words/net/).
- Development Environment: Visual Studio or any other .NET development environment.
- Basic Knowledge of C#: This tutorial assumes you're comfortable with C# programming.

## Import Namespaces

To get started, you need to import the necessary namespaces. These will allow you to access the classes and methods required for working with Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Now, let's break down the process of specifying a default font into easy-to-follow steps.

## Step 1: Set Up Your Document Directory

First, define the path to your document directory. This is where your input and output files will be stored.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Step 2: Load Your Document

Next, load the document you want to render. In this example, we'll use a file named "Rendering.docx".

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Step 3: Configure Font Settings

Create an instance of `FontSettings` and specify the default font. If the defined font cannot be found during rendering, Aspose.Words will use the closest available font on the machine.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";
```

## Step 4: Apply Font Settings to the Document

Assign the configured font settings to your document.

```csharp
doc.FontSettings = fontSettings;
```

## Step 5: Save the Document

Finally, save the document in the desired format. In this case, we'll save it as a PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## Conclusion

By following these steps, you can ensure that your Word documents render with a specified default font, maintaining consistency across different platforms. This can be particularly useful for documents shared widely or viewed on systems with varying font availability.


## FAQ's

### Why specify a default font in Aspose.Words?
Specifying a default font ensures your document appears consistent across different platforms, even if the original fonts are unavailable.

### What happens if the default font is not found during rendering?
Aspose.Words will use the closest available font on the machine to maintain the document's appearance as closely as possible.

### Can I specify multiple default fonts?
No, you can only specify one default font. However, you can handle font substitution for specific cases using the `FontSettings` class.

### Is Aspose.Words for .NET compatible with all versions of Word documents?
Yes, Aspose.Words for .NET supports a wide range of Word document formats, including DOC, DOCX, RTF, and more.

### Where can I get support if I encounter issues?
You can get support from the Aspose community and developers on the [Aspose.Words Support Forum](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
