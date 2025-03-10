---
title: Enable Disable Font Substitution
linktitle: Enable Disable Font Substitution
second_title: Aspose.Words Document Processing API
description: Learn how to enable or disable font substitution in Word documents using Aspose.Words for .NET. Ensure your documents look consistent across all platforms.
weight: 10
url: /net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enable Disable Font Substitution

## Introduction

Ever found yourself in a situation where your meticulously chosen fonts in a Word document are replaced when viewed on another computer? Annoying, right? This happens due to font substitution, a process where the system replaces a missing font with an available one. But worry not! With Aspose.Words for .NET, you can easily manage and control font substitution. In this tutorial, we’ll walk you through the steps to enable or disable font substitution in your Word documents, ensuring your documents always look just the way you want them to.

## Prerequisites

Before diving into the steps, let's ensure you have everything you need:

- Aspose.Words for .NET: Download the latest version [here](https://releases.aspose.com/words/net/).
- Visual Studio: Any version supporting .NET.
- Basic knowledge of C#: This will help you follow along with the coding examples.

## Import Namespaces

To get started, ensure you have the necessary namespaces imported in your project. Add these at the top of your C# file:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Now, let’s break down the process into simple, manageable steps.

## Step 1: Set Up Your Project

First, set up a new project in Visual Studio and add a reference to the Aspose.Words for .NET library. If you haven’t already, download it from the [Aspose website](https://releases.aspose.com/words/net/).

## Step 2: Load Your Document

Next, load the document you want to work with. Here’s how you do it:

```csharp
// Path to your document directory 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path to your document directory. This code loads the document into memory so you can manipulate it.

## Step 3: Configure Font Settings

Now, let’s create a `FontSettings` object to manage the font substitution settings:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Step 4: Set Default Font Substitution

Set the default font substitution to a font of your choice. This font will be used if the original font is not available:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

In this example, we’re using Arial as the default font.

## Step 5: Disable Font Info Substitution

To disable font info substitution, which stops the system from replacing missing fonts with available ones, use the following code:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Step 6: Apply Font Settings to the Document

Now, apply these settings to your document:

```csharp
doc.FontSettings = fontSettings;
```

## Step 7: Save Your Document

Finally, save your modified document. You can save it in any format you like. For this tutorial, we’ll save it as a PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Conclusion

And there you have it! By following these steps, you can easily control font substitution in your Word documents using Aspose.Words for .NET. This ensures your documents maintain their intended look and feel, no matter where they are viewed.

## FAQ's

### Can I use fonts other than Arial for substitution?

Absolutely! You can specify any font available on your system by changing the font name in the `DefaultFontName` property.

### What happens if the specified default font is not available?

If the default font is not available, Aspose.Words will use a system fallback mechanism to find an appropriate replacement.

### Can I enable font substitution again after disabling it?

Yes, you can toggle the `Enabled` property of `FontInfoSubstitution` back to `true` if you want to enable font substitution again.

### Is there a way to check which fonts are being substituted?

Yes, Aspose.Words provides methods to log and track font substitution, allowing you to see which fonts are being replaced.

### Can I use this method for other document formats besides DOCX?

Definitely! Aspose.Words supports various formats, and you can apply these font settings to any supported format.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
