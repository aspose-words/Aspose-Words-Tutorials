---
"description": "了解如何使用 Aspose.Words for .NET 偵測純文字文件中帶有空格的編號並確保正確識別您的清單。"
"linktitle": "檢測帶有空格的數字"
"second_title": "Aspose.Words文件處理API"
"title": "檢測帶有空格的數字"
"url": "/zh-hant/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 檢測帶有空格的數字

## 介紹

Aspose.Words 適合 .NET 愛好者！今天，我們將深入研究一項令人著迷的功能，它可以輕鬆處理純文字文件中的清單。您是否曾經處理過這樣的文字檔案：其中某些行應該是列表，但是當載入到 Word 文件中時它們看起來不太正確？好吧，我們有一個巧妙的技巧：偵測帶有空格的數字。本教學將指導您如何使用 `DetectNumberingWithWhitespaces` Aspose.Words for .NET 中的選項可確保您的清單已正確識別，即使數字和文字之間存在空格。

## 先決條件

在開始之前，請確保您具備以下條件：

- Aspose.Words for .NET：您可以從 [Aspose 版本](https://releases.aspose.com/words/net/) 頁。
- 開發環境：Visual Studio 或任何其他 C# IDE。
- 您的機器上安裝了 .NET Framework。
- C# 基礎知識：了解基礎知識將幫助您理解範例。

## 導入命名空間

在進入程式碼之前，請確保已在專案中匯入必要的命名空間。以下是幫助您入門的簡短程式碼片段：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

讓我們將這個過程分解為簡單、易於管理的步驟。每個步驟都會引導您完成必要的程式碼並解釋正在發生的事情。

## 步驟 1：定義文件目錄

首先，讓我們設定文檔目錄的路徑。這是儲存您的輸入和輸出檔案的地方。

```csharp
// 文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步驟2：建立純文字文檔

接下來，我們將建立一個純文字文件作為字串。本文檔將包含可能被解釋為清單的部分。

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## 步驟 3：配置 LoadOptions

為了偵測帶有空格的數字，我們需要設定 `DetectNumberingWithWhitespaces` 選擇 `true` 在一個 `TxtLoadOptions` 目的。

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## 步驟 4：載入文檔

現在，讓我們使用 `TxtLoadOptions` 作為參數。這確保第四個清單（帶有空格）被正確檢測。

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## 步驟5：儲存文檔

最後，將文件儲存到您指定的目錄。這將輸出一個包含正確檢測清單的 Word 文件。

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## 結論

就是這樣！只需幾行程式碼，您就掌握了使用 Aspose.Words for .NET 偵測純文字文件中帶有空格的編號的技術。在處理各種文字格式並確保清單在 Word 文件中準確顯示時，此功能非常方便。因此，下次您遇到這些棘手的清單時，您就會確切地知道該怎麼做。

## 常見問題解答

### 什麼是 `DetectNumberingWithWhitespaces` 在 Aspose.Words for .NET 中？
`DetectNumberingWithWhitespaces` 是一個選項 `TxtLoadOptions` 即使編號和清單項目文字之間存在空格，Aspose.Words 也能夠辨識清單。

### 我可以將此功能用於其他分隔符號（例如項目符號和括號）嗎？
是的，Aspose.Words 會自動偵測具有常見分隔符號（如項目符號和括號）的清單。這 `DetectNumberingWithWhitespaces` 特別有助於處理帶有空格的清單。

### 如果我不使用會發生什麼 `DetectNumberingWithWhitespaces`？
如果沒有此選項，編號和文字之間帶有空格的列表可能不會被識別為列表，並且項目可能會顯示為普通段落。

### 其他 Aspose 產品中是否有此功能？
此特定功能是為 Aspose.Words for .NET 量身定制的，旨在處理 Word 文件。

### 如何取得 Aspose.Words for .NET 的臨時授權？
您可以從 [Aspose臨時許可證](https://purchase.aspose.com/temporary-license/) 頁。




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}