---
"description": "了解如何使用 Aspose.Words for .NET 匯入文件並保留格式。帶有程式碼範例的分步指南。"
"linktitle": "保留源編號"
"second_title": "Aspose.Words文件處理API"
"title": "保留源編號"
"url": "/zh-hant/net/join-and-append-documents/keep-source-numbering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 保留源編號

## 介紹

使用 Aspose.Words for .NET 時，可以使用 `NodeImporter` 班級。本教學將引導您逐步完成整個過程。

## 先決條件

在開始之前，請確保您已準備好以下內容：
- 您的機器上安裝了 Visual Studio。
- 已安裝 Aspose.Words for .NET。如果沒有，請從以下位置下載 [這裡](https://releases。aspose.com/words/net/).
- 具有 C# 和 .NET 程式設計的基本知識。

## 導入命名空間

首先，在您的專案中包含必要的命名空間：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## 步驟 1：設定您的項目

首先在 Visual Studio 中建立一個新的 C# 項目，然後透過 NuGet 套件管理器安裝 Aspose.Words。

## 第 2 步：初始化文檔
建立來源的實例（`srcDoc`) 和目的地 (`dstDoc`) 文件。

```csharp
// 文檔目錄的路徑 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## 步驟 3：配置導入選項
設定匯入選項以維護來源格式，包括編號段落。

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## 步驟 4：導入段落
遍歷來源文件中的段落並將其匯入目標文件。

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## 步驟5：儲存文檔
將合併的文件儲存到您想要的位置。

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## 結論

總之，使用 Aspose.Words for .NET 匯入文件並保留格式非常簡單， `NodeImporter` 班級。此方法可確保您的文件無縫保持其原始外觀和結構。

## 常見問題解答

### 我可以匯入具有不同格式樣式的文件嗎？
是的， `NodeImporter` 類別支援匯入具有多種格式樣式的文件。

### 如果我的文件包含複雜的表格和圖像怎麼辦？
Aspose.Words for .NET 在導入作業期間處理表格和圖像等複雜結構。

### Aspose.Words 是否與所有版本的 .NET 相容？
Aspose.Words 支援 .NET Framework 和 .NET Core 版本，以實現無縫整合。

### 如何處理文件導入過程中的錯誤？
使用try-catch區塊來處理導入過程中可能發生的異常。

### 在哪裡可以找到有關 Aspose.Words for .NET 的更詳細文件？
訪問 [文件](https://reference.aspose.com/words/net/) 以獲得全面的指南和 API 參考。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}