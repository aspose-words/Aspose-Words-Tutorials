---
"description": "透過逐步指南了解如何使用 Aspose.Words for .NET 從 Word 檔案中讀取 ActiveX 控制項屬性。增強您的文件自動化技能。"
"linktitle": "從 Word 檔案讀取 Active XControl 屬性"
"second_title": "Aspose.Words文件處理API"
"title": "從 Word 檔案讀取 Active XControl 屬性"
"url": "/zh-hant/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 從 Word 檔案讀取 Active XControl 屬性

## 介紹

在當今數位時代，自動化是提高生產力的關鍵。如果您正在使用包含 ActiveX 控制項的 Word 文檔，則可能需要讀取它們的屬性以用於各種目的。 ActiveX 控制項（例如複選框和按鈕）可以儲存重要資料。使用 Aspose.Words for .NET，您可以以程式設計方式有效地提取和操作這些資料。

## 先決條件

在開始之前，請確保您具備以下條件：

1. Aspose.Words for .NET Library：您可以從 [這裡](https://releases。aspose.com/words/net/).
2. Visual Studio 或任何 C# IDE：編寫和執行程式碼。
3. 帶有 ActiveX 控制項的 Word 文件：例如「ActiveX 控制項.docx」。
4. C# 基礎知識：需要熟悉 C# 程式設計才能繼續學習。

## 導入命名空間

首先，讓我們匯入使用 Aspose.Words for .NET 所需的命名空間。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## 步驟 1：載入 Word 文檔

首先，您需要載入包含 ActiveX 控制項的 Word 文件。

```csharp
// 文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## 步驟 2：初始化字串以保存屬性

接下來，初始化一個空字串來儲存ActiveX控制項的屬性。

```csharp
string properties = "";
```

## 步驟 3：遍歷文件中的形狀

我們需要遍歷文件中的所有形狀來找到 ActiveX 控制項。

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // 處理 ActiveX 控件
    }
}
```

## 步驟 4：從 ActiveX 控制項中擷取屬性

在循環中，檢查控制項是否為 Forms2OleControl。如果是，則對其進行轉換並提取屬性。

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## 步驟 5：統計 ActiveX 控制項總數

遍歷所有形狀後，計算找到的 ActiveX 控制項總數。

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## 步驟 6：顯示屬性

最後，將提取的屬性列印到控制台。

```csharp
Console.WriteLine("\n" + properties);
```

## 結論

就是這樣！您已成功學習如何使用 Aspose.Words for .NET 從 Word 文件讀取 ActiveX 控制項屬性。本教學涵蓋了載入文件、遍歷形狀以及從 ActiveX 控制項中提取屬性。透過遵循這些步驟，您可以自動從 Word 文件中提取重要數據，從而提高工作流程效率。

## 常見問題解答

### Word 文件中的 ActiveX 控制項是什麼？
ActiveX 控制項是嵌入在 Word 文件中的互動式對象，例如核取方塊、按鈕和文字字段，用於建立表單和自動執行任務。

### 我可以使用 Aspose.Words for .NET 修改 ActiveX 控制項的屬性嗎？
是的，Aspose.Words for .NET 允許您以程式設計方式修改 ActiveX 控制項的屬性。

### Aspose.Words for .NET 可以免費使用嗎？
Aspose.Words for .NET 提供免費試用，但您需要購買授權才能繼續使用。您可以免費試用 [這裡](https://releases。aspose.com/).

### 除了 C# 之外，我可以將 Aspose.Words for .NET 與其他 .NET 語言一起使用嗎？
是的，Aspose.Words for .NET 可以與任何 .NET 語言一起使用，包括 VB.NET 和 F#。

### 在哪裡可以找到有關 Aspose.Words for .NET 的更多文件？
您可以找到詳細的文檔 [這裡](https://reference。aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}