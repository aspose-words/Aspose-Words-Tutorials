---
title: 在沒有文件產生器的情況下插入 TOA 字段
linktitle: 在沒有文件產生器的情況下插入 TOA 字段
second_title: Aspose.Words 文件處理 API
description: 了解如何在不使用 Aspose.Words for .NET 中的文件產生器的情況下插入 TOA 欄位。按照我們的逐步指南有效管理法律引文。
weight: 10
url: /zh-hant/net/working-with-fields/insert-toafield-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在沒有文件產生器的情況下插入 TOA 字段

## 介紹

在 Word 文件中建立權限表 (TOA) 欄位就像拼湊一個複雜的謎題。然而，在 Aspose.Words for .NET 的幫助下，這個過程變得順利且簡單。在本文中，我們將引導您在不使用文件產生器的情況下插入 TOA 欄位的步驟，讓您可以輕鬆管理 Word 文件中的引文和法律參考文獻。

## 先決條件

在深入學習本教程之前，我們先介紹一下您需要的基本知識：

-  Aspose.Words for .NET：確保您安裝了最新版本。您可以從[阿斯普斯網站](https://releases.aspose.com/words/net/).
- 開發環境：與 .NET 相容的 IDE，例如 Visual Studio。
- 基本 C# 知識：了解基本 C# 文法和概念將會有所幫助。
- 範例 Word 文件：在要插入 TOA 欄位的位置建立或準備好範例文件。

## 導入命名空間

首先，您需要從 Aspose.Words 庫匯入必要的命名空間。此設定可確保您可以存取文件操作所需的所有類別和方法。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

讓我們將這個過程分解為簡單、易於遵循的步驟。我們將引導您完成每個階段，解釋每段程式碼的作用以及它如何有助於建立 TOA 欄位。

## 步驟1：初始化文檔

首先，您需要建立一個實例`Document`班級。該物件代表您正在處理的 Word 文件。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

此程式碼初始化一個新的 Word 文件。您可以將其視為創建一個空白畫布，您可以在其中添加內容。

## 步驟2：建立並配置TA字段

接下來，我們將新增 TA（權限表）欄位。此欄位標記將出現在 TOA 中的條目。

```csharp
Paragraph para = new Paragraph(doc);

//我們想要像這樣插入 TA 和 TOA 欄位：
// { TA \c 1 \l "值 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

這是一個細分：
- Paragraph para = new Paragraph(doc);：在文件中建立一個新段落。
-  FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);：在段落中新增 TA 欄位。這`FieldType.FieldTOAEntry`指定這是一個 TOA 輸入欄位。
- fieldTA.EntryCategory = "1";：設定條目類別。這對於對不同類型的條目進行分類非常有用。
- fieldTA.LongCitation = "Value 0";：指定長引文文字。這是將出現在 TOA 中的文字。
- doc.FirstSection.Body.AppendChild(para);：將帶有 TA 欄位的段落附加到文件正文。

## 步驟 3：新增 TOA 字段

現在，我們將插入將所有 TA 條目編譯到表中的實際 TOA 欄位。

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

在這一步中：
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);：將 TOA 欄位新增至段落。
- fieldToa.EntryCategory = "1";：過濾條目以僅包含那些標記為類別「1」的條目。

## 第 4 步：更新 TOA 字段

插入 TOA 欄位後，您需要更新它以確保它反映最新的條目。

```csharp
fieldToa.Update();
```

此命令會刷新 TOA 字段，確保所有標記的條目正確顯示在表中。

## 第 5 步：儲存文檔

最後，使用新新增的 TOA 欄位儲存文件。

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

這行程式碼將文件儲存到指定目錄。確保更換`"YOUR DOCUMENT DIRECTORY"`與您要儲存檔案的實際路徑。

## 結論

現在你就擁有了！您已成功將 TOA 欄位新增至 Word 文檔，而無需使用文檔產生器。透過執行這些步驟，您可以有效地管理引文並在法律文件中建立全面的授權表。 Aspose.Words for .NET 讓這個過程變得順暢和高效，為您提供了輕鬆處理複雜文件任務的工具。

## 常見問題解答

### 我可以新增多個不同類別的 TA 欄位嗎？
是的，您可以透過設定來新增多個不同類別的TA字段`EntryCategory`相應的財產。

### 如何自訂 TOA 的外觀？
您可以透過修改 TOA 欄位的屬性（例如條目格式和類別標籤）來自訂 TOA 的外觀。

### 是否可以自動更新TOA欄位？
雖然您可以使用以下命令手動更新 TOA 字段`Update`方法，Aspose.Words 目前不支援文件變更的自動更新。

### 我可以在文件的特定部分以程式設計方式新增 TA 欄位嗎？
是的，您可以透過將 TA 欄位插入所需的段落或部分中來在特定位置新增 TA 欄位。

### 如何處理單一文件中的多個 TOA 欄位？
您可以透過指派不同的TOA字段來管理多個TOA字段`EntryCategory`值並確保每個 TOA 欄位根據其類別過濾條目。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
