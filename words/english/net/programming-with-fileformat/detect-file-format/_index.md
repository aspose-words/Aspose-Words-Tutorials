---
title: Detect Document File Format
linktitle: Detect Document File Format
second_title: Aspose.Words Document Processing API
description: Learn how to detect document file formats using Aspose.Words for .NET with this comprehensive, step-by-step guide.
weight: 10
url: /net/programming-with-fileformat/detect-file-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Detect Document File Format

## Introduction

In today's digital world, managing different document formats efficiently is crucial. Whether you are handling Word, PDF, HTML, or other formats, being able to detect and process these files correctly can save you a lot of time and effort. In this tutorial, we'll explore how to detect document file formats using Aspose.Words for .NET. This guide will walk you through everything you need to know, from prerequisites to a detailed step-by-step guide.

## Prerequisites

Before we dive into the code, let's make sure you have everything you need:

- Aspose.Words for .NET: You can download it from [here](https://releases.aspose.com/words/net/). Make sure you have a valid license. If not, you can get a [temporary license](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Any recent version will work fine.
- .NET Framework: Ensure you have the correct version installed.

## Import Namespaces

To get started, you'll need to import the necessary namespaces in your project:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Let's break down the example into multiple steps to make it easier to follow.

## Step 1: Set Up Directories

First, we need to set up directories where the files will be sorted based on their format.

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Create the directories if they do not already exist.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Step 2: Get the List of Files

Next, we'll get a list of files from the directory, excluding any corrupted documents.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Step 3: Detect File Formats

Now, we iterate through each file and detect its format using Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Display the document type
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## Conclusion

Detecting document file formats using Aspose.Words for .NET is a straightforward process. By setting up your directories, getting your list of files, and utilizing Aspose.Words to detect file formats, you can efficiently organize and manage your documents. This approach not only saves time but also ensures that you handle various document formats correctly.

## FAQ's

### What is Aspose.Words for .NET?
Aspose.Words for .NET is a powerful library for working with Word documents programmatically. It allows developers to create, modify, and convert documents in various formats.

### Can Aspose.Words detect encrypted documents?
Yes, Aspose.Words can detect if a document is encrypted and you can handle such documents accordingly.

### What formats can Aspose.Words detect?
Aspose.Words can detect a wide range of formats including DOC, DOCX, RTF, HTML, MHTML, ODT, and many more.

### How can I get a temporary license for Aspose.Words?
You can get a temporary license from the [Aspose Purchase](https://purchase.aspose.com/temporary-license/) page.

### Where can I find the documentation for Aspose.Words?
The documentation for Aspose.Words can be found [here](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
