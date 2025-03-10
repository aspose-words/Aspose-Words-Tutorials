---
title: 列舉屬性
linktitle: 列舉屬性
second_title: Aspose.Words 文件處理 API
description: 透過此逐步指南，了解如何使用 Aspose.Words for .NET 列舉 Word 文件中的屬性。非常適合所有技能水平的開發人員。
weight: 10
url: /zh-hant/net/programming-with-document-properties/enumerate-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 列舉屬性

## 介紹

希望以程式方式處理 Word 文件？ Aspose.Words for .NET 是一個功能強大的工具，可以幫助您實現這一目標。今天，我將向您介紹如何使用 Aspose.Words for .NET 列舉 Word 文件的屬性。無論您是初學者還是有一定經驗，本指南都會以對話式且易於理解的方式逐步分解。

## 先決條件

在我們深入學習本教程之前，您需要先完成一些準備：

-  Aspose.Words for .NET：您可以[在這裡下載](https://releases.aspose.com/words/net/).
- 開發環境：建議使用Visual Studio，但您可以使用任何C# IDE。
- C# 基礎知識：對 C# 的基本了解將幫助您跟進。

現在，讓我們開始吧！

## 第 1 步：設定您的項目

首先，您需要在 Visual Studio 中設定專案。

1. 建立新專案：開啟 Visual Studio 並建立一個新的控制台應用程式專案。
2. 安裝 Aspose.Words for .NET：使用 NuGet Package Manager 安裝 Aspose.Words for .NET。在解決方案資源管理器中右鍵單擊您的項目，選擇“管理 NuGet 套件”，然後搜尋“Aspose.Words”。安裝軟體包。

## 第 2 步：導入命名空間

若要使用 Aspose.Words，您需要匯入必要的命名空間。在 Program.cs 檔案頂部新增以下內容：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Properties;
```

## 第 3 步：載入您的文檔

接下來，讓我們載入您要使用的 Word 文件。對於此範例，我們將使用位於專案目錄中名為「Properties.docx」的文件。

1. 定義文檔路徑：指定文檔的路徑。
2. 載入文檔：使用Aspose.Words`Document`類別來載入文檔。

這是代碼：

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

## 步驟4：顯示文檔名稱

載入文件後，您可能希望顯示其名稱。 Aspose.Words 為此提供了一個屬性：

```csharp
Console.WriteLine("1. Document name: {0}", doc.OriginalFileName);
```

## 第 5 步：枚舉內建屬性

內建屬性是 Microsoft Word 預先定義的元資料屬性。其中包括標題、作者等。

1. 存取內建屬性：使用`BuiltInDocumentProperties`收藏。
2. 循環遍歷屬性：循環遍歷屬性並顯示它們的名稱和值。

這是代碼：

```csharp
Console.WriteLine("2. Built-in Properties");

foreach (DocumentProperty prop in doc.BuiltInDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## 第 6 步：枚舉自訂屬性

自訂屬性是使用者定義的元資料屬性。這些可以是您想要新增到文件中的任何內容。

1. 存取自訂屬性：使用`CustomDocumentProperties`收藏。
2. 循環遍歷屬性：循環遍歷屬性並顯示它們的名稱和值。

這是代碼：

```csharp
Console.WriteLine("3. Custom Properties");

foreach (DocumentProperty prop in doc.CustomDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 成功地列舉了 Word 文件的內建屬性和自訂屬性。這只是 Aspose.Words 功能的冰山一角。無論您是自動產生文檔還是操作複雜文檔，Aspose.Words 都提供了一組豐富的功能，讓您的生活更輕鬆。

## 常見問題解答

### 我可以向文件添加新屬性嗎？
是的，您可以使用以下命令新增新的自訂屬性`CustomDocumentProperties`收藏。

### Aspose.Words 可以免費使用嗎？
 Aspose.Words 提供了[免費試用](https://releases.aspose.com/)和不同的[購買選項](https://purchase.aspose.com/buy).

### 如何獲得 Aspose.Words 支援？
您可以從 Aspose 社區獲得支持[這裡](https://forum.aspose.com/c/words/8).

### 我可以將 Aspose.Words 與其他 .NET 語言一起使用嗎？
是的，Aspose.Words 支援多種 .NET 語言，包括 VB.NET。

### 我在哪裡可以找到更多範例？
查看[Aspose.Words for .NET 文檔](https://reference.aspose.com/words/net/)了解更多範例和詳細資訊。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
