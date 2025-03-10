---
title: Get Substitution Without Suffixes
linktitle: Get Substitution Without Suffixes
second_title: Aspose.Words Document Processing API
description: Learn how to manage font substitution without suffixes in Aspose.Words for .NET. Follow our step-by-step guide to ensure your documents look perfect every time.
weight: 10
url: /net/working-with-fonts/get-substitution-without-suffixes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Get Substitution Without Suffixes

## Introduction

Welcome to this comprehensive guide on managing font substitution using Aspose.Words for .NET. If you've ever struggled with fonts not appearing correctly in your documents, you've come to the right place. This tutorial will take you through a step-by-step process to handle font substitution without suffixes efficiently.

## Prerequisites

Before diving into the tutorial, ensure you have the following:

- Basic Knowledge of C#: Understanding C# programming will make it easier to follow and implement the steps.
- Aspose.Words for .NET Library: Download and install the library from the [download link](https://releases.aspose.com/words/net/).
- Development Environment: Set up a development environment like Visual Studio to write and run your code.
- Sample Document: A sample document (e.g., `Rendering.docx`) to work with during this tutorial.

## Import Namespaces

First, we need to import the necessary namespaces to access the classes and methods provided by Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Step 1: Define the Document Directory

To start, specify the directory where your document is located. This helps in locating the document you want to work on.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Step 2: Set Up the Substitution Warning Handler

Next, we need to set up a warning handler that will notify us whenever a font substitution occurs during document processing. This is crucial for catching and handling any font issues.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Step 3: Add Custom Font Sources

In this step, we will add custom font sources to ensure that Aspose.Words can locate and use the correct fonts. This is particularly useful if you have specific fonts stored in custom directories.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

In this code:
- We retrieve the current font sources and add a new `FolderFontSource` pointing to our custom font directory (`C:\\MyFonts\\`).
- We then update the font sources with this new list.

## Step 4: Save the Document

Finally, save the document after applying the font substitution settings. For this tutorial, we'll save it as a PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Step 5: Create the Warning Handler Class

To handle warnings effectively, create a custom class that implements the `IWarningCallback` interface. This class will capture and log any font substitution warnings.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

In this class:
- The `Warning` method captures warnings related to font substitution.
- The `FontWarnings` collection stores these warnings for further inspection or logging.

## Conclusion

You've now mastered the process of handling font substitution without suffixes using Aspose.Words for .NET. This knowledge will ensure that your documents maintain their intended appearance, regardless of the fonts available on the system. Keep experimenting with different settings and sources to fully harness the power of Aspose.Words.

## FAQ's

### How can I use fonts from multiple custom directories?

You can add multiple `FolderFontSource` instances to the `fontSources` list and update the font sources accordingly.

### Where can I download a free trial of Aspose.Words for .NET?

You can download a free trial from the [Aspose free trial page](https://releases.aspose.com/).

### Can I handle multiple types of warnings using `IWarningCallback`?

Yes, the `IWarningCallback` interface allows you to handle various types of warnings, not just font substitution.

### Where can I get support for Aspose.Words?

For support, visit the [Aspose.Words support forum](https://forum.aspose.com/c/words/8).

### Is it possible to purchase a temporary license?

Yes, you can get a temporary license from the [temporary license page](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
