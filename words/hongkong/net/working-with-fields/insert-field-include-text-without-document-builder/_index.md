---
title: 插入欄位包括文字而不使用文件產生器
linktitle: 在沒有文件產生器的情況下插入 FieldIncludeText
second_title: Aspose.Words 文件處理 API
description: 透過我們詳細的逐步指南，了解如何在不使用 Aspose.Words for .NET 中的 DocumentBuilder 的情況下插入 FieldIncludeText。
weight: 10
url: /zh-hant/net/working-with-fields/insert-field-include-text-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 插入欄位包括文字而不使用文件產生器

## 介紹

在文件自動化和操作領域，Aspose.Words for .NET 是一個強大的工具。今天，我們將深入研究如何在不使用 DocumentBuilder 的情況下插入 FieldIncludeText 的詳細指南。本教學將逐步引導您完成流程，確保您了解程式碼的每個部分及其用途。

## 先決條件

在我們深入研究程式碼之前，讓我們確保您擁有所需的一切：

1.  Aspose.Words for .NET：確保您安裝了最新版本。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/net/).
2. .NET 開發環境：任何與 .NET 相容的 IDE，例如 Visual Studio。
3. C# 基礎知識：熟悉 C# 程式設計將有助於您跟進。

## 導入命名空間

首先，我們需要導入必要的名稱空間。這些命名空間提供對操作 Word 文件所需的類別和方法的存取。

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

現在，讓我們將該範例分解為多個步驟。每個步驟都會詳細解釋以確保清晰。

## 第1步：設定目錄路徑

第一步是定義文檔目錄的路徑。這是您的 Word 文件的儲存和存取位置。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## 第 2 步：建立文件和段落

接下來，我們建立一個新文件以及該文件中的一個段落。該段落將包含 FieldIncludeText 欄位。

```csharp
//建立文件和段落。
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## 步驟 3：插入 FieldIncludeText 字段

現在，我們將 FieldIncludeText 欄位插入到段落中。此欄位允許您包含其他文件中的文字。

```csharp
//插入 FieldIncludeText 欄位。
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## 步驟 4：設定字段屬性

我們需要指定 FieldIncludeText 欄位的屬性。這包括設定書籤名和來源文件的完整路徑。

```csharp
fieldIncludeText.BookmarkName = "bookmark";
fieldIncludeText.SourceFullName = dataDir + "IncludeText.docx";
```

## 第 5 步：將段落附加到文檔

設定欄位後，我們將段落附加到文件的第一部分正文。

```csharp
doc.FirstSection.Body.AppendChild(para);
```

## 第 6 步：更新字段

在儲存文件之前，我們需要更新 FieldIncludeText 以確保它從來源文件中提取正確的內容。

```csharp
fieldIncludeText.Update();
```

## 步驟7：儲存文檔

最後，我們將文檔儲存到指定的目錄中。

```csharp
doc.Save(dataDir + "InsertionFieldFieldIncludeTextWithoutDocumentBuilder.docx");
```

## 結論

現在你就擁有了！透過執行以下步驟，您可以輕鬆插入 FieldIncludeText，而無需在 Aspose.Words for .NET 中使用 DocumentBuilder。這種方法提供了一種將一個文件中的內容包含到另一個文件中的簡化方法，使您的文件自動化任務更加簡單。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？  
Aspose.Words for .NET 是一個功能強大的程式庫，用於在 .NET 應用程式中處理 Word 文件。它允許以程式設計方式建立、編輯和轉換文件。

### 為什麼要使用 FieldIncludeText？  
FieldInincludeText 對於動態地將一個文件中的內容包含到另一個文件中非常有用，從而使文件更加模組化和可維護。

### 我可以使用此方法包含其他文件格式的文字嗎？  
FieldIncludeText 特別適用於 Word 文件。對於其他格式，您可能需要 Aspose.Words 提供的不同方法或類別。

### Aspose.Words for .NET 與 .NET Core 相容嗎？  
是的，Aspose.Words for .NET 支援 .NET Framework、.NET Core 和 .NET 5/6。

### 如何獲得 Aspose.Words for .NET 的免費試用版？  
您可以從以下位置獲得免費試用[這裡](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
