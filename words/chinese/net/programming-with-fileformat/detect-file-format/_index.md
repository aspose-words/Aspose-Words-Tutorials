---
"description": "通过本全面的分步指南了解如何使用 Aspose.Words for .NET 检测文档文件格式。"
"linktitle": "检测文档文件格式"
"second_title": "Aspose.Words文档处理API"
"title": "检测文档文件格式"
"url": "/zh/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 检测文档文件格式

## 介绍

在当今的数字世界中，高效管理各种文档格式至关重要。无论您处理的是 Word、PDF、HTML 还是其他格式，能够正确检测和处理这些文件可以节省大量时间和精力。在本教程中，我们将探索如何使用 Aspose.Words for .NET 检测文档文件格式。本指南将引导您了解所有需要了解的内容，从先决条件到详细的分步指南。

## 先决条件

在深入研究代码之前，请确保您拥有所需的一切：

- Aspose.Words for .NET：您可以从 [这里](https://releases.aspose.com/words/net/)确保您持有有效驾照。如果没有，您可以申请 [临时执照](https://purchase。aspose.com/temporary-license/).
- Visual Studio：任何最新版本都可以正常工作。
- .NET Framework：确保您安装了正确的版本。

## 导入命名空间

首先，您需要在项目中导入必要的命名空间：

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

我们将示例分解为多个步骤，以便于理解。

## 步骤 1：设置目录

首先，我们需要设置目录，以便根据文件的格式对其进行排序。

```csharp
// 文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// 如果目录不存在，则创建目录。
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## 第 2 步：获取文件列表

接下来，我们将从目录中获取文件列表，排除任何损坏的文档。

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## 步骤3：检测文件格式

现在，我们遍历每个文件并使用 Aspose.Words 检测其格式。

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // 显示文档类型
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

## 结论

使用 Aspose.Words for .NET 检测文档文件格式非常简单。通过设置目录、获取文件列表并利用 Aspose.Words 检测文件格式，您可以高效地组织和管理文档。这种方法不仅节省时间，还能确保您正确处理各种文档格式。

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个功能强大的库，用于以编程方式处理 Word 文档。它允许开发人员创建、修改和转换各种格式的文档。

### Aspose.Words 可以检测加密文档吗？
是的，Aspose.Words 可以检测文档是否加密，您可以相应地处理此类文档。

### Aspose.Words 可以检测哪些格式？
Aspose.Words 可以检测多种格式，包括 DOC、DOCX、RTF、HTML、MHTML、ODT 等。

### 如何获得 Aspose.Words 的临时许可证？
您可以从 [Aspose 购买](https://purchase.aspose.com/temporary-license/) 页。

### 在哪里可以找到 Aspose.Words 的文档？
Aspose.Words 的文档可以在 [这里](https://reference。aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}