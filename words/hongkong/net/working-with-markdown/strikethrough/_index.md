---
title: 刪除線
linktitle: 刪除線
second_title: Aspose.Words 文件處理 API
description: 透過我們的逐步指南，了解如何使用 Aspose.Words for .NET 將刪除線格式套用至文字。提升您的文件處理技能。
weight: 10
url: /zh-hant/net/working-with-markdown/strikethrough/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 刪除線

## 介紹

歡迎閱讀本詳細指南，以了解如何使用 Aspose.Words for .NET 將刪除線格式套用至文字。如果您希望提高文件處理技能並為文字添加獨特的風格，那麼您來對地方了。讓我們深入了解吧！

## 先決條件

在我們開始之前，請確保您具備以下條件：

-  Aspose.Words for .NET：下載[這裡](https://releases.aspose.com/words/net/).
- .NET Framework：確保您的系統上安裝了 .NET Framework。
- 開發環境：像Visual Studio這樣的IDE。
- C# 基礎知識：熟悉 C# 程式設計是必要的。

## 導入命名空間

首先，您需要匯入必要的命名空間。這些對於存取 Aspose.Words 程式庫及其功能至關重要。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 第 1 步：初始化 DocumentBuilder

這`DocumentBuilder` class 是 Aspose.Words 中的強大工具，可讓您輕鬆地將內容新增至文件。

```csharp
//初始化一個 DocumentBuilder。
DocumentBuilder builder = new DocumentBuilder();
```

## 步驟2：設定刪除線屬性

現在，讓我們將刪除線屬性應用到我們的文字中。這涉及到設置`StrikeThrough`的財產`Font`反對`true`.

```csharp
//將文字新增刪除線。
builder.Font.StrikeThrough = true;
```

## 步驟 3： 用刪除線書寫文本

設定刪除線屬性後，我們現在可以新增文字。這`Writeln`方法會將文字加入文件中。

```csharp
//用刪除線書寫文字。
builder.Writeln("This text will be StrikeThrough");
```

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 成功為文字新增刪除線格式。這個強大的庫為文檔處理和定制打開了一個充滿可能性的世界。無論您是建立報告、信件或任何其他類型的文檔，掌握這些功能無疑將提高您的工作效率和輸出品質。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的文件處理庫，可讓開發人員以程式設計方式建立、操作和轉換 Word 文件。

### 我可以在商業專案中使用 Aspose.Words for .NET 嗎？
是的，您可以在商業專案中使用 Aspose.Words for .NET。有關購買選項，請訪問[購買頁面](https://purchase.aspose.com/buy).

### Aspose.Words for .NET 有沒有免費試用版？
是的，您可以下載免費試用版[這裡](https://releases.aspose.com/).

### 如何獲得 Aspose.Words for .NET 支援？
您可以獲得 Aspose 社群和專家的支持[支援論壇](https://forum.aspose.com/c/words/8).

### 我可以使用 Aspose.Words for .NET 套用其他文字格式選項嗎？
絕對地！ Aspose.Words for .NET 支援多種文字格式選項，包括粗體、斜體、底線等。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
