---
title: Set Fonts Folders System And Custom Folder
linktitle: Set Fonts Folders System And Custom Folder
second_title: Aspose.Words Document Processing API
description: Learn how to set system and custom font folders in Word documents using Aspose.Words for .NET, ensuring your documents display correctly across different environments.
weight: 10
url: /net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Set Fonts Folders System And Custom Folder

## Introduction

Imagine you’re crafting a document with a unique font style, only to find out that the fonts don’t display correctly on another machine. Frustrating, right? This is where configuring font folders comes into play. With Aspose.Words for .NET, you can define system and custom font folders to ensure your documents always look as intended. Let's dive into how you can achieve this.

## Prerequisites

Before we start, make sure you have the following:

- Aspose.Words for .NET Library: If you haven't already, download it [here](https://releases.aspose.com/words/net/).
- Development Environment: An IDE like Visual Studio.
- Basic Knowledge of C#: Familiarity with C# will help you follow along with the code examples.

## Import Namespaces

First, import the necessary namespaces in your project:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Now, let's break down the process into simple steps.

## Step 1: Load the Document

To begin, load your Word document into an Aspose.Words `Document` object. This document will be the one where you want to set the font folders.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Step 2: Initialize Font Settings

Create a new instance of `FontSettings`. This object will allow you to manage font sources.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Step 3: Retrieve System Font Sources

Retrieve the default system font sources. On a Windows machine, this typically includes the "Windows\Fonts\" directory.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Step 4: Add a Custom Font Folder

Add a custom folder that contains your additional fonts. This is useful if you have specific fonts not installed in the system fonts directory.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Step 5: Update Font Sources

Convert the list of font sources back to an array and set it to the `FontSettings` object.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Step 6: Apply Font Settings to Document

Finally, apply the configured `FontSettings` to your document and save it in your desired format, such as PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Conclusion

And there you have it! By following these steps, you can ensure that your Word documents use the correct fonts, whether they are system fonts or custom ones stored in a specific directory. This setup helps maintain the integrity of your document's appearance across different environments.

## FAQ's

### What happens if a font is missing in both system and custom folders?

Aspose.Words will use a default font to substitute the missing font, ensuring the document remains readable.

### Can I add multiple custom font folders?

Yes, you can add multiple custom font folders by repeating the process of creating `FolderFontSource` objects and adding them to the font sources list.

### Is it possible to use network paths for custom font folders?

Yes, you can specify a network path in the `FolderFontSource` constructor.

### What file formats does Aspose.Words support for saving documents?

Aspose.Words supports various formats, including DOCX, PDF, HTML, and more.

### How do I handle font substitution notifications?

You can handle font substitution notifications by using the `FontSettings` class’s `FontSubstitutionWarning` event.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
