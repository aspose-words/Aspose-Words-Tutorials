---
title: 在沒有文件產生器的情況下插入 ASKField
linktitle: 在沒有文件產生器的情況下插入 ASKField
second_title: Aspose.Words 文件處理 API
description: 了解如何在不使用 Aspose.Words for .NET 中的文件產生器的情況下插入 ASK 欄位。請按照本指南動態增強您的 Word 文件。
weight: 10
url: /zh-hant/net/working-with-fields/insert-askfield-with-out-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在沒有文件產生器的情況下插入 ASKField

## 介紹

您是否希望使用 Aspose.Words for .NET 掌握文件自動化？您來對地方了！今天，我們將引導您了解如何在不使用文件產生器的情況下插入 ASK 欄位。當您希望文件提示使用者進行特定輸入時，這是一個很棒的功能，可讓您的 Word 文件更具互動性和動態性。那麼，讓我們深入研究，讓您的文件變得更加聰明！

## 先決條件

在我們開始編寫一些程式碼之前，讓我們確保我們已經完成了所有設定：

1.  Aspose.Words for .NET：確保您已安裝此程式庫。如果沒有，您可以從以下位置下載[這裡](https://releases.aspose.com/words/net/).
2. 開發環境：合適的IDE，如Visual Studio。
3. .NET Framework：確保您已安裝 .NET Framework。

偉大的！現在我們已經準備好了，讓我們開始導入必要的命名空間。

## 導入命名空間

首先，我們需要匯入 Aspose.Words 命名空間來存取 Aspose.Words for .NET 的所有功能。操作方法如下：

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

## 第 1 步：建立一個新文檔

在插入 ASK 欄位之前，我們需要一個可以使用的文件。建立新文檔的方法如下：

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENTS DIRECTORY";

//文檔建立。
Document doc = new Document();
```

此程式碼片段設定一個新的 Word 文檔，我們將在其中新增 ASK 欄位。

## 第 2 步：訪問段落節點

在 Word 文件中，內容被組織成節點。我們需要存取第一個段落節點，我們將在其中插入 ASK 欄位：

```csharp
Paragraph para = (Paragraph)doc.GetChild(NodeType.Paragraph, 0, true);
```

這行程式碼檢索文件中的第一段，為我們的 ASK 欄位插入做好準備。

## 第 3 步：插入詢問字段

現在，讓我們進入主要事件 – 插入 ASK 欄位。開啟文件時，此欄位將提示使用者輸入。

```csharp
//插入詢問欄位。
FieldAsk field = (FieldAsk)para.AppendField(FieldType.FieldAsk, false);
```

在這裡，我們將 ASK 欄位附加到該段落。很簡單，對吧？

## 步驟 4：配置 ASK 字段

我們需要設定一些屬性來定義 ASK 欄位的行為方式。讓我們配置書籤名稱、提示文字、預設回應和郵件合併行為：

```csharp
field.BookmarkName = "Test1";
field.PromptText = "Please enter your response:";
field.DefaultResponse = "Default response";
field.PromptOnceOnMailMerge = true;
```

- BookmarkName：ASK 欄位的唯一識別碼。
- PromptText：提示使用者輸入的文字。
- DefaultResponse：使用者可以更改的預填充回應。
- PromptOnceOnMailMerge：確定提示在郵件合併期間是否僅出現一次。

## 第 5 步：更新字段

配置 ASK 欄位後，我們需要更新它以確保正確套用所有設定：

```csharp
field.Update();
```

此命令確保我們的 ASK 欄位已準備就緒並在文件中正確設定。

## 第 6 步：儲存文檔

最後，讓我們將文檔儲存到指定的目錄中：

```csharp
doc.Save(dataDir + "InsertionChampASKSansDocumentBuilder.docx");
```

此行保存帶有插入的 ASK 欄位的文件。現在您已經完成了 – 您的文件現在配備了動態 ASK 欄位！

## 結論

恭喜！您剛剛使用 Aspose.Words for .NET 在沒有文件產生器的情況下將 ASK 欄位新增至 Word 文件。此功能可顯著增強使用者與文件的交互，使文件更加靈活且使用者友好。不斷嘗試不同的字段和屬性，以釋放 Aspose.Words 的全部潛力。快樂編碼！

## 常見問題解答

### Aspose.Words 中的 ASK 欄位是什麼？
Aspose.Words 中的 ASK 字段是在開啟文件時提示使用者進行特定輸入的字段，從而允許動態資料輸入。

### 我可以在單一文件中使用多個 ASK 欄位嗎？
是的，您可以在文件中插入多個詢問字段，每個字段都有獨特的提示和回應。

### 目的是什麼`PromptOnceOnMailMerge` property?
這`PromptOnceOnMailMerge`屬性決定 ASK 提示是在郵件合併操作期間僅出現一次還是每次都出現。

### 設定屬性後是否需要更新 ASK 欄位？
是的，更新 ASK 欄位可確保正確套用所有屬性並且欄位如預期運作。

### 我可以自訂提示文字和預設回應嗎？
絕對地！您可以設定自訂提示文字和預設回應，以根據您的特定需求自訂詢問欄位。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
