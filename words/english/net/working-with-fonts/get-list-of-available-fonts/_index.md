---
title: Get List Of Available Fonts
linktitle: Get List Of Available Fonts
second_title: Aspose.Words Document Processing API
description: Discover how to get a list of available fonts using Aspose.Words for .NET in this detailed step-by-step tutorial. Boost your font management skills.
weight: 10
url: /net/working-with-fonts/get-list-of-available-fonts/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Get List Of Available Fonts

## Introduction

Ever found yourself struggling to manage fonts in your Word documents? If you're a .NET developer, Aspose.Words for .NET is here to rescue you! This powerful library not only helps you create and manipulate Word documents programmatically but also offers extensive font management capabilities. In this guide, we'll walk you through a step-by-step tutorial on how to get a list of available fonts using Aspose.Words for .NET. We'll break it down into digestible steps to ensure you can follow along with ease. So, let's dive in and make font management a breeze!

## Prerequisites

Before we get started, there are a few things you'll need:

- Aspose.Words for .NET: Make sure you have the Aspose.Words for .NET library installed. You can download it from [here](https://releases.aspose.com/words/net/).
- Visual Studio: This example uses Visual Studio as the development environment.
- .NET Framework: Ensure you have .NET Framework installed on your machine.
- Document Directory: A directory path where your documents are stored.

## Import Namespaces

First, import the necessary namespaces into your project:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Step 1: Initialize Font Settings

The first step is to initialize the font settings. This will allow you to manage the font sources for your documents.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: This class is used to specify the settings for font substitution and font sources.
- fontSources: We create a list of existing font sources from the current font settings.

## Step 2: Define Document Directory

Next, specify the path to your document directory. This is where Aspose.Words will search for fonts.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

- dataDir: This string variable holds the path to the directory where your fonts are located. Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path.

## Step 3: Add Custom Font Folder

Now, add a new folder source to instruct Aspose.Words to search this folder for fonts.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: This class represents a folder font source. The second parameter (`true`) indicates whether to search for fonts recursively in subfolders.

## Step 4: Update Font Sources

Add the custom font folder to the list of existing font sources and update the font settings.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): Adds the custom font folder to the existing font sources.
- updatedFontSources: Converts the list of font sources to an array.

## Step 5: Retrieve and Display Fonts

Finally, retrieve the available fonts and display their details.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): Retrieves the list of available fonts from the first font source in the updated list.
- fontInfo: An instance of `PhysicalFontInfo` containing details about each font.

## Conclusion

Congratulations! You've successfully retrieved a list of available fonts using Aspose.Words for .NET. This tutorial has walked you through each step, from initializing font settings to displaying font details. With this knowledge, you can now manage fonts in your Word documents with ease. Remember, Aspose.Words for .NET is a powerful tool that can significantly enhance your document processing capabilities. So, go ahead and explore more features to make your development process even more efficient.

## FAQ's

### Can I use Aspose.Words for .NET with other .NET frameworks?
Yes, Aspose.Words for .NET is compatible with various .NET frameworks including .NET Core and .NET 5+.

### How do I install Aspose.Words for .NET?
You can install it via NuGet Package Manager in Visual Studio by searching for "Aspose.Words".

### Is it possible to add multiple custom font folders?
Yes, you can add multiple custom font folders by creating multiple `FolderFontSource` instances and adding them to the font sources list.

### Can I retrieve font details from a specific font source?
Yes, you can retrieve font details from any font source by specifying the index of the font source in the `updatedFontSources` array.

### Does Aspose.Words for .NET support font substitution?
Yes, it supports font substitution to ensure that text is rendered correctly even if the original font is not available.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
