---
"description": "透過本全面的逐步指南了解如何使用 Aspose.Words for .NET 偵測文件檔案格式。"
"linktitle": "檢測文件文件格式"
"second_title": "Aspose.Words文件處理API"
"title": "檢測文件文件格式"
"url": "/zh-hant/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 檢測文件文件格式

## 介紹

在當今的數位世界中，有效管理不同的文件格式至關重要。無論您處理的是 Word、PDF、HTML 或其他格式，能夠正確檢測和處理這些文件可以為您節省大量時間和精力。在本教學中，我們將探討如何使用 Aspose.Words for .NET 偵測文件檔案格式。本指南將引導您了解您需要知道的所有內容，從先決條件到詳細的逐步指南。

## 先決條件

在深入研究程式碼之前，請確保您擁有所需的一切：

- Aspose.Words for .NET：您可以從 [這裡](https://releases.aspose.com/words/net/)。確保您擁有有效的許可證。如果沒有，你可以得到 [臨時執照](https://purchase。aspose.com/temporary-license/).
- Visual Studio：任何最新版本都可以正常運作。
- .NET Framework：確保您安裝了正確的版本。

## 導入命名空間

首先，您需要在專案中匯入必要的命名空間：

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

我們將範例分解為多個步驟，以便於理解。

## 步驟 1：設定目錄

首先，我們需要設定目錄，以便根據文件的格式對其進行排序。

```csharp
// 文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// 如果目錄不存在，則建立目錄。
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## 第 2 步：取得文件列表

接下來，我們將從目錄中取得文件列表，排除任何損壞的文件。

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## 步驟3：檢測文件格式

現在，我們遍歷每個檔案並使用 Aspose.Words 偵測其格式。

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // 顯示文檔類型
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

## 結論

使用 Aspose.Words for .NET 偵測文件檔案格式是一個簡單的過程。透過設定目錄、取得文件清單以及利用 Aspose.Words 偵測文件格式，您可以有效地組織和管理文件。這種方法不僅節省時間，還能確保您正確處理各種文件格式。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的函式庫，可以透過程式處理 Word 文件。它允許開發人員創建、修改和轉換各種格式的文件。

### Aspose.Words 可以偵測加密文件嗎？
是的，Aspose.Words 可以偵測文件是否已加密，您可以相應地處理此類文件。

### Aspose.Words 可以偵測哪些格式？
Aspose.Words 可以偵測多種格式，包括 DOC、DOCX、RTF、HTML、MHTML、ODT 等。

### 如何取得 Aspose.Words 的臨時授權？
您可以從 [Aspose 購買](https://purchase.aspose.com/temporary-license/) 頁。

### 在哪裡可以找到 Aspose.Words 的文檔？
Aspose.Words 的文檔可以在 [這裡](https://reference。aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}