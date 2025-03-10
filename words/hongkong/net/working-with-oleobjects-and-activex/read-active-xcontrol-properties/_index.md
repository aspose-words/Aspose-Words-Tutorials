---
title: 從 Word 檔案讀取 Active XControl 屬性
linktitle: 從 Word 檔案讀取 Active XControl 屬性
second_title: Aspose.Words 文件處理 API
description: 透過逐步指南了解如何使用 Aspose.Words for .NET 從 Word 檔案讀取 ActiveX 控制項屬性。提高您的文件自動化技能。
weight: 10
url: /zh-hant/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 從 Word 檔案讀取 Active XControl 屬性

## 介紹

在當今的數位時代，自動化是提高生產力的關鍵。如果您正在使用包含 ActiveX 控制項的 Word 文檔，則可能需要出於各種目的讀取它們的屬性。 ActiveX 控制項（例如複選框和按鈕）可以儲存重要資料。使用 Aspose.Words for .NET，您可以以程式設計方式有效地提取和操作這些資料。

## 先決條件

在我們開始之前，請確保您具備以下條件：

1.  Aspose.Words for .NET Library：您可以從以下位置下載它[這裡](https://releases.aspose.com/words/net/).
2. Visual Studio 或任何 C# IDE：編寫和執行程式碼。
3. 帶有 ActiveX 控制項的 Word 文件：例如「ActiveXcontrols.docx」。
4. C# 基礎知識：需要熟悉 C# 程式設計才能進行後續操作。

## 導入命名空間

首先，讓我們匯入必要的命名空間以使用 Aspose.Words for .NET。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## 第 1 步：載入 Word 文檔

首先，您需要載入包含 ActiveX 控制項的 Word 文件。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## 第 2 步：初始化一個字串來保存屬性

接下來，初始化一個空字串來儲存 ActiveX 控制項的屬性。

```csharp
string properties = "";
```

## 第 3 步：迭代文檔中的形狀

我們需要遍歷文件中的所有形狀來尋找 ActiveX 控制項。

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        //處理ActiveX控件
    }
}
```

## 步驟 4：從 ActiveX 控制項中擷取屬性

在循環中，檢查控制項是否為 Forms2OleControl。如果是，則鑄造它並提取屬性。

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

## 步驟 5：計算 ActiveX 控制項總數

遍歷所有形狀後，計算找到的 ActiveX 控制項的總數。

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## 第 6 步：顯示屬性

最後，將提取的屬性列印到控制台。

```csharp
Console.WriteLine("\n" + properties);
```

## 結論

現在你就擁有了！您已成功學習如何使用 Aspose.Words for .NET 從 Word 文件讀取 ActiveX 控制項屬性。本教學介紹了載入文件、迭代形狀以及從 ActiveX 控制項中提取屬性。透過執行以下步驟，您可以自動從 Word 文件中提取重要數據，從而提高工作流程效率。

## 常見問題解答

### Word 文件中的 ActiveX 控制項是什麼？
ActiveX 控制項是嵌入在 Word 文件中的互動式對象，例如核取方塊、按鈕和文字字段，用於建立表單和自動執行任務。

### 我可以使用 Aspose.Words for .NET 修改 ActiveX 控制項的屬性嗎？
是的，Aspose.Words for .NET 允許您以程式設計方式修改 ActiveX 控制項的屬性。

### Aspose.Words for .NET 可以免費使用嗎？
 Aspose.Words for .NET 提供免費試用版，但您需要購買授權才能繼續使用。您可以獲得免費試用[這裡](https://releases.aspose.com/).

### 我可以將 Aspose.Words for .NET 與 C# 以外的其他 .NET 語言一起使用嗎？
是的，Aspose.Words for .NET 可以與任何 .NET 語言一起使用，包括 VB.NET 和 F#。

### 在哪裡可以找到有關 Aspose.Words for .NET 的更多文件？
你可以找到詳細的文檔[這裡](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
